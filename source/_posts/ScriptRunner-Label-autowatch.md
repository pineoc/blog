---
title: ScriptRunner Jira Issue Label 추가시 자동으로 watcher 추가
toc: true
date: 2019-12-01 23:11:27
categories:
  - PM
  - System
tags:
  - Jira
  - ScriptRunner
thumbnail: https://marketplace-cdn.atlassian.com/files/images/396d3521-7734-4137-9a47-d7afedf1ea18.png
---

스크립트러너에서 Jira 이슈의 Label 추가에 따라 자동으로 특정 사람들을 와쳐(watcher)에 추가하는 방법을 다뤄봅니다.

## 시스템 테스트 환경

- Jira: Jira Software 8.3.2
- ScriptRunner: 5.6.1.1-jira8

## 참고 포스트

- Listener에 대한 내용 참고 포스트: {% post_link scriptrunner2 %}
- Label 관련 내용을 다룬 포스트: {% post_link ScriptRunner-Label %}

## 사용 시나리오

적용하는 방법 전에 제가 사용하고 있는 시나리오를 공유드립니다.
특정 이벤트에 따라 와쳐를 추가할 수 있으니 이벤트만 잘 고려해서 `와쳐 추가 코드`만 사용하셔도 괜찮습니다.

1. 특정 레이블(Label)이 이슈에 추가됨
2. 레이블이 추가된 이슈에 원하는 인원을 와쳐 필드에 입력함
3. 와쳐 인원 입력은 복수의 인원이 가능해야함

여기서 특정 이벤트는 `레이블 추가` 입니다.
다른 이벤트의 예시로는 `컴포넌트 추가`, `특정 커스텀 필드 값의 변경` 등 다양하게 조건을 변경해볼 수 있을 것 같네요.

## 적용

앞서 설명드린 시나리오대로 적용해보겠습니다.
바로 적용해보고 싶으신 분들을 위해 먼저 코드와 설정 화면을 보여드리겠습니다.

![Listener - Custom Listener 선택](https://user-images.githubusercontent.com/5077086/69915509-1dbe9a00-1493-11ea-854a-66226c3ff935.png)

![Custom Listener field 입력](https://user-images.githubusercontent.com/5077086/69915636-a0942480-1494-11ea-8598-844dc87e5c8d.png)

```groovy
import com.atlassian.jira.component.ComponentAccessor;
import java.util.List;

def watcherManager = ComponentAccessor.getWatcherManager();
def userManager = ComponentAccessor.getUserManager();
// Add users to watcher field
def watchUsers = {usernames ->
  usernames.each {
    def user = userManager.getUserByKey(it.toString());
    watcherManager.startWatching(user, event.issue);
  }
}
// Remove users on watcher field
def unwatchUsers = {usernames ->
  usernames.each {
    def user = userManager.getUserByKey(it.toString());
    watcherManager.stopWatching(user, event.issue);
  }
}
def labelWatch = {String label, List users, String[] oldArr, String[] newArr, boolean isCaseSensitive ->
  String[] tmpOldArr = oldArr.collect {String i ->
    if (isCaseSensitive)
      return i;
    else
      return i.toLowerCase();
  };
  String[] tmpNewArr = newArr.collect {String i ->
    if (isCaseSensitive)
      return i;
    else
      return i.toLowerCase();
  }
  String tmpLabel = isCaseSensitive ? label : label.toLowerCase();
  if (tmpOldArr.contains(tmpLabel) == false && tmpNewArr.contains(tmpLabel) == true) {
    watchUsers(users);
  }
  if (tmpOldArr.contains(tmpLabel) == true && tmpNewArr.contains(tmpLabel) == false) {
    unwatchUsers(users);
  }
}
def labelWatchCreated = {String label, List users, boolean isCaseSensitive ->
  String[] labels = event.issue.labels as String[];
  String[] tmpLabels = labels.collect {String i ->
    if (isCaseSensitive)
      return i;
    else
      return i.toLowerCase();
  }
  String tmpLabel = isCaseSensitive ? label : label.toLowerCase();
  if (tmpLabels.contains(tmpLabel)) {
    watchUsers(users);
  }
}

def change = event?.getChangeLog()?.getRelated("ChildChangeItem")?.find {it.field == "labels"};

if (change) {
  // Issue Updated case
  String[] oldArr = change.oldstring.toString().tokenize();
  String[] newArr = change.newstring.toString().tokenize();

  labelWatch("m", ["m1", "m2", "m3"], oldArr, newArr, false);
  labelWatch("b", ["b1", "b2", "b3", "b4", "b5"], oldArr, newArr, true);
} else {
  // Issue Created case: ${event.issue} ${event.issue.labels}
  labelWatchCreated("m", ["m1", "m2", "m3"], false);
  labelWatchCreated("b", ["b1", "b2", "b3", "b4", "b5"], true);
}

```

### 참고

위와 같이 설정하고 Update 버튼을 눌러주시면 적용됩니다.
코드가 깔끔하지는 않으나 동작하고 있는 코드입니다. (코드 개선은 향후 조금씩 진행해보겠습니다.)
다만 적용 전에 각자에 맞게 설정해야하는 값은 아래와 같습니다.

1. `labelWatch()`를 호출시 "m"은 레이블 이름을, []안에는 와쳐 필드에 추가하고자 하는 유저의 아이디들을 입력해주세요.
2. `labelWatchCreated()`를 호출시 1번 항목과 동일하게 입력해주세요.
  - 이 함수를 추가하는 이유는 이슈 생성시 이벤트가 다르게 처리되기 때문입니다.
  - 이슈 생성시 이벤트를 실행시키지 않고자 한다면 해당 코드를 지워도 괜찮습니다.
3. `labelWatch()`, `labelWatchCreated()` 함수 마지막 인자는 레이블의 대소문자를 구분할 것인지에 대한 변수입니다.
  - 레이블 값의 대소문자를 구분하고자한다면 `true`, 아니라면 `false` 값을 넣고 호출해주세요.

## 코드 설명

코드에 대한 설명 내용이 많지않지만 각 함수별로 짧게 설명드리겠습니다.

### watchUsers(usernames) / unwatchUsers(usernames)

변수로 전달받은 유저들을 이벤트가 발생한 이슈의 와쳐 필드에 입력/삭제합니다.

```groovy
def watcherManager = ComponentAccessor.getWatcherManager();
def userManager = ComponentAccessor.getUserManager();
// Add users to watcher field
def watchUsers = {usernames ->
  usernames.each {
    def user = userManager.getUserByKey(it.toString());
    watcherManager.startWatching(user, event.issue);
  }
}
// Remove users on watcher field
def unwatchUsers = {usernames ->
  usernames.each {
    def user = userManager.getUserByKey(it.toString());
    watcherManager.stopWatching(user, event.issue);
  }
}
```

- 유저를 의미하는 `usernames`이라는 string 배열 인수를 받아 처리합니다.
- `watcherManager`에 있는 `startWatching()`, `stopWatching()` 함수로 와쳐를 추가하고 삭제합니다.

### labelWatch (label, users, oldArr, newArr, isCaseSensitive)

레이블과 변경전 레이블 배열, 변경후 레이블 배열을 받아 레이블이 변경되었는지 확인합니다. 추가적으로 `isCaseSensitive` 인수를 통해 레이블의 대소문자를 구분하여 확인합니다.
확인 후, 받은 유저들을 이슈의 와쳐 필드에 추가 또는 삭제합니다.
(watchUsers(), unwatchUsers() 함수로)
이슈가 업데이트될 경우에만 호출되는 함수입니다. 생성시에는 아래에 있는 `labelWatchCreated()` 함수가 호출됩니다.

### labelWatchCreated(label, users, isCaseSensitive)

이슈 생성시에는 변경된 사항이 없기에 issue Created 이벤트를 받아 처리해야했습니다.
추가 함수를 통해 이슈 생성시에도 와쳐가 추가될 수 있도록 만든 함수입니다.

`labelWatch()` 함수처럼 레이블과 유저를 받고 받은 레이블이 값에 있을 경우 유저를 이슈의 와쳐 필드에 추가합니다.

### 실행 코드

실행 코드는 위에서 설명한 함수를 사용하여 와쳐 추가를 실행합니다.

```groovy
def change = event?.getChangeLog()?.getRelated("ChildChangeItem")?.find {it.field == "labels"};

if (change) {
  // Issue Updated case
  String[] oldArr = change.oldstring.toString().tokenize();
  String[] newArr = change.newstring.toString().tokenize();

  labelWatch("m", ["m1", "m2", "m3"], oldArr, newArr, false);
  labelWatch("b", ["b1", "b2", "b3", "b4", "b5"], oldArr, newArr, true);
} else {
  // Issue Created case: ${event.issue} ${event.issue.labels}
  labelWatchCreated("m", ["m1", "m2", "m3"], false);
  labelWatchCreated("b", ["b1", "b2", "b3", "b4", "b5"], true);
}
```

## 마무리

실제로 빠르게 적용해보고 사용해본 코드라 깔끔하지 않을 수 있지만
다른분들도 사용해볼 수 있도록 포스트해보았습니다.

업무에 도움이 될 수 있기를 바라며 다른 방법도 추후에 올려보겠습니다.
감사합니다.
