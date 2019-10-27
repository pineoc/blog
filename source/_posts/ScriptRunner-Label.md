---
title: ScriptRunner Label 다루기
toc: true
date: 2019-10-27 15:21:10
categories:
  - PM
  - System
tags:
  - Jira
  - ScriptRunner
thumbnail: https://marketplace-cdn.atlassian.com/files/images/396d3521-7734-4137-9a47-d7afedf1ea18.png
---

스크립트러너에서 Jira 이슈의 Label 값을 수정하는 경우가 종종 있는데 어떻게 추가/수정하는지
이번 포스트에서 다뤄보겠습니다.

이번에도 Script Console에서 코드를 실행시켜보고 저는 어떤 케이스에서 사용하는지 설명드리겠습니다.

## 시스템 테스트 환경

스크립트러너는 Jira 버전에 영향을 좀 받아서 환경도 미리 알고 계셔야합니다.
(버전에 따라 내부 함수들이 변경됨에 따라 실제 코드도 조금씩 변경됩니다)

- Jira: Jira Software 8.3.2
- ScriptRunner: 5.6.1.1-jira8

## Label 값 가져오기

Label 값을 가져오는 것은 쉽습니다.
이슈에서 기본적으로 사용하는 필드라서 다루기 쉬운 것이 장점입니다.

```groovy
import com.atlassian.jira.component.ComponentAccessor;
import com.atlassian.jira.issue.label.LabelManager;
import com.atlassian.jira.issue.MutableIssue;

LabelManager labelManager = ComponentAccessor.getComponent(LabelManager);
def issueMgr = ComponentAccessor.getIssueManager();
MutableIssue issue = issueMgr.getIssueObject("PUBGTEST-169");

labelManager.getLabels(issue.getId());
```

### getLabels(Long issueId)

getLabels() 함수는 issueId 값을 받아 이슈의 label 값을 가져옵니다.
함수의 리턴 값은 label들을 포함한 배열로 리턴합니다.
(아래 결과 값은 이슈에 테스트로 Label 값을 입력한 것을 기반으로 스크립트 결과가 나온 것입니다.)

**Result**
> [Promotion, art]

## Label 값 추가하기

Label 값을 가져오는 것보다는 한가지 더 고려가 필요한 `추가` 입니다.
Label 값을 추가할 때에는 어떤 사용자가 값을 추가할 것인지 결정이 필요합니다.
먼저 코드를 보면서 설명을 드리겠습니다.

```groovy
import com.atlassian.jira.component.ComponentAccessor;
import com.atlassian.jira.issue.label.LabelManager;
import com.atlassian.jira.issue.MutableIssue;
  
def user = ComponentAccessor.getUserManager().getUserByKey("pubg-helper");
LabelManager labelManager = ComponentAccessor.getComponent(LabelManager);
def issueMgr = ComponentAccessor.getIssueManager();
MutableIssue issue = issueMgr.getIssueObject("PUBGTEST-169");

labelManager.addLabel(user, issue.getId(), 'test', false);
labelManager.getLabels(issue.getId());
```

### 코드 설명

앞서 Label 값을 가져오는 것과 비교해서 달라진 것은 아래 코드와 `addLabel()` 함수 입니다.
`def user = ComponentAccessor.getUserManager().getUserByKey("pubg-helper");`
위 코드는 Label을 추가할 사용자를 결정하기 위해 사용자 객체를 아이디로 가져온 것입니다.

ScriptRunner의 Listener 기능에서 Label 수정/추가 기능을 사용할 때,
위 코드를 통해 업데이트하는 사용자를 동적으로 변경할 수 있습니다.

addLabel(User remoteUser, Long issueId, String label, boolean sendNotification) 함수는 이슈에 Label을 하나 추가할 수 있는 함수입니다.
함수 레퍼런스: [docs.atlassian.com/.../LabelManager/addLabel](https://docs.atlassian.com/DAC/javadoc/jira/reference/com/atlassian/jira/issue/label/LabelManager.html#addLabel(com.atlassian.crowd.embedded.api.User,%20java.lang.Long,%20java.lang.String,%20boolean))

**Result**
> [Promotion, art, test]

## Label 값 변경

앞서 Label 추가의 경우 하나씩 추가했던 것에 비해 Label 값을 변경하는 것은 LabelManager의 setLabels() 함수를 사용합니다.

```groovy
import com.atlassian.jira.component.ComponentAccessor;
import com.atlassian.jira.issue.label.LabelManager;
import com.atlassian.jira.issue.MutableIssue;
  
def user = ComponentAccessor.getUserManager().getUserByKey("pubg-helper");
LabelManager labelManager = ComponentAccessor.getComponent(LabelManager);
def issueMgr = ComponentAccessor.getIssueManager();
MutableIssue issue = issueMgr.getIssueObject("PUBGTEST-169");

labelManager.setLabels(user, issue.getId(), ['test'] as Set, false, true);
labelManager.getLabels(issue.getId());
```

### labelManager.setLabels()

labelManager.setLabels() 함수는 Label 값을 추가, 삭제한다기보다는
새로운 값으로 `재설정`한다는 것으로 이해하시면 될 것 같습니다.

`public Set<Label> setLabels (User remoteUser, Long issueId, Set<String> labels, boolean sendNotification, boolean causeChangeNotification)`

여기서 중간에 labels 값에 Set으로 되어있는데 그냥 [] 배열로 넣을 경우 List 객체로 인식하는 문제가 생깁니다.
그래서 `as Set`으로 변경해준 것으로 이해해주시면 됩니다. (혹은 변수를 따로 Set으로 두고 입력하면 됩니다)

labelManager.setLabels() 함수 레퍼런스: [docs.atlassian.com/.../LabelManager/setLabels](https://docs.atlassian.com/DAC/javadoc/jira/reference/com/atlassian/jira/issue/label/LabelManager.html#setLabels(com.atlassian.crowd.embedded.api.User,%20java.lang.Long,%20java.util.Set%3Cjava.lang.String%3E,%20boolean,%20boolean))

**Result**
> [test]

## 마무리

Label 값을 가져오고 추가/설정하는 것은 어렵지 않은 것 같습니다. (커스텀 필드 수정에 비해서요)
다만 골라서 삭제하는 기능은 없어 setLabels와 기존에 있는 값을 비교해서 삭제하는 것으로 삭제할 수는 있어 보이네요. (그렇게 어려워 보이지는 않을 것 같긴 하네요.)

저는 특정 이벤트가 발생할 경우 Label을 추가하는 정도로만 Listener에 Custom Listener를 추가하여 사용하고 있습니다. 이 Label을 사용하여 보드를 만들어 사용하시는 분이 있는데 잘 사용하고 있다고 하네요. :)

다음에 다른 기능을 소개하는 포스트로 찾아뵙겠습니다.
감사합니다!