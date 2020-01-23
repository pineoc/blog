---
title: 'ScriptRunner: Custom Field 다루기'
toc: true
date: 2019-10-12 16:08:45
categories:
  - PM
  - System
tags:
  - Jira
  - ScriptRunner
thumbnail: https://user-images.githubusercontent.com/5077086/72972150-3fdaf580-3e0e-11ea-998a-108879c7874c.png
---

스크립트러너에서 Jira 이슈의 커스텀 필드를 다루는 경우가 많습니다.
저는 어떻게 스크립트러너에서 커스텀 필드의 값을 가져오고, 수정하고 있는지 다뤄보겠습니다.

## ScriptRunner란? (복습)

기존에 있는 포스트를 보시면 좋을 것 같습니다.
그중에 2번째 포스트에서 설명했던 `Script Console`에서 실습해보겠습니다.

- {% post_link scriptrunner1 %}
- **{% post_link scriptrunner2 %}**
- {% post_link scriptrunner3 %}
- {% post_link scriptrunner4 %}

## 시스템 테스트 환경

스크립트러너는 jira 버전에 영향을 좀 받아서 환경도 미리 알고 계셔야합니다.
(버전에 따라 내부 함수들이 변경됨에 따라 실제 코드도 조금씩 변경됩니다)

- Jira: Jira Software 8.3.2
- ScriptRunner: 5.6.1.1-jira8

## 커스텀 필드(Custom Field) 값 가져오기

간단하게 `커스텀 필드` 값을 가져오는 코드를 보면서 설명하겠습니다.
코드는 groovy로 작성하며 Script Console에서 테스트해보았습니다.

```groovy
// import
import com.atlassian.jira.component.ComponentAccessor;
import com.atlassian.jira.issue.MutableIssue;

// functions
String getCustomFieldValue(MutableIssue issue, String cfName) {
  def customFieldManager = ComponentAccessor.getCustomFieldManager();
  def cfObj = customFieldManager.getCustomFieldObjectsByName(cfName)[0];
  String cfValue = issue.getCustomFieldValue(cfObj);
  return cfValue;
}

def issueMgr = ComponentAccessor.getIssueManager();
MutableIssue issue = issueMgr.getIssueObject("PUBGTEST-169");
getCustomFieldValue(issue, "Translation");
```

복사 & 붙여넣기 하시고 `이슈 키`, `커스텀 필드 이름`만 바꿔서 입력해주시면
해당 이슈의 커스텀 필드 값을 가져올 수 있는 코드입니다.
코드에서 중요한 부분만 간단하게 보고 커스텀 필드 값 수정으로 넘어가겠습니다.

### getCustomFieldValue(issue, cfName) 함수

`이슈 오브젝트`와 `커스텀 필드 이름`을 받아 커스텀 필드 값을 반환하는 함수입니다.

1. CustomFieldManager를 사용하여 커스텀 필드 오브젝트를 가져옵니다.
  - 배열로 가져오는 함수(`getCustomFieldObjectsByName()`)를 사용하였습니다.
  - `getCustomFieldObjectByName()`도 있지만 배열로 가져오는 함수를 권장하고 있습니다.
  - 같은 이름의 커스텀 필드가 있을 수 있기에 배열로 가져오는 함수를 권장하는 것 같네요.
2. issue에 있는 함수 `getCustomFieldValue()`로 커스텀 필드 오브젝트를 이용해 커스텀 필드 값을 가져옵니다.
3. 커스텀 필드 값을 리턴합니다.

### 코드 실행 결과

Script Console 실행 결과도 보여드리겠습니다.

![](https://user-images.githubusercontent.com/5077086/66697493-18559680-ed11-11e9-944b-86f4686b1e63.png)

콘솔에서는 코드 실행 후 마지막에 있는 오브젝트의 값을 보여줍니다.
log에서 출력한 내용은 logs 탭에서 볼 수 있습니다.

## 커스텀 필드(Custom Field) 값 수정하기

커스텀 필드의 값을 확인했으니 수정도 해볼 수 있어야겠죠?!
값을 가져오는 것보다 코드가 조금 더 추가됩니다.

```groovy
// import
import com.atlassian.jira.event.type.EventDispatchOption
import com.atlassian.jira.component.ComponentAccessor;
import com.atlassian.jira.issue.MutableIssue;

// functions
String getCustomFieldValue(MutableIssue issue, String cfName) {
  def customFieldManager = ComponentAccessor.getCustomFieldManager();
  def cfObj = customFieldManager.getCustomFieldObjectsByName(cfName)[0];
  String cfValue = issue.getCustomFieldValue(cfObj);
  return cfValue;
}
def setCustomFieldValue(MutableIssue issue, String cfName, String str) {
  def issueMgr = ComponentAccessor.getIssueManager();
  def customFieldManager = ComponentAccessor.getCustomFieldManager();
  def user = ComponentAccessor.getJiraAuthenticationContext().getLoggedInUser();
  def cfObj = customFieldManager.getCustomFieldObjectsByName(cfName)[0];
  issue.setCustomFieldValue(cfObj, str);
  issueMgr.updateIssue(user, issue, EventDispatchOption.DO_NOT_DISPATCH, false);
}

def issueMgr = ComponentAccessor.getIssueManager();
MutableIssue issue = issueMgr.getIssueObject("PUBGTEST-169");
setCustomFieldValue(issue, "Translation", "TEST");
getCustomFieldValue(issue, "Translation");
```

앞서 값을 가져오는 코드와 마찬가지로 "TEST"에 있는 값을 바꾸면 적용해보실 수 있습니다.
다만 주의하실 점은 커스텀 필드의 타입이 텍스트 타입이어야합니다.
Label, Checkbox 등 다른 타입일 경우에는 **동작하지 않는** 코드입니다.

### setCustomFieldValue(issue, cfName, str)

값을 가져오는 코드와 다른 부분만 설명드리겠습니다.

- issueMgr: 이슈 매니저로 이슈 업데이트를 위해 함수 내에 선언합니다.
- usr: 이슈 업데이트를 하려면 업데이트하는 사용자 오브젝트가 필요하여 선언합니다.
- issue.setCustomFieldValue(cfObj, str);
  - 이 함수를 통해 커스텀 필드 값이 변경됩니다.
  - 이 코드만 실행할 경우, 실제 반영은 되지 않습니다. (함수 동작시에만 변경됨)
- issueMgr.updateIssue()
  - 이 함수를 통해 앞에서 setCustomFieldValue()에서 변경된 내용이 반영됩니다.

커스텀 필드 수정과 관련한 질문은 Google에 검색만 하더라도 많이 나옵니다.
(첫번째 글을 보시는 것을 추천합니다.)

- [community.atlassian.com/Set-custom-field-value-Script-Runner](https://community.atlassian.com/t5/Jira-questions/Set-custom-field-value-Script-Runner/qaq-p/1042485)
- [community.atlassian.com/Basic-method-to-update-a-custom-field-with-Scriptrunner](https://community.atlassian.com/t5/Marketplace-Apps-Integrations/Basic-method-to-update-a-custom-field-with-Scriptrunner/qaq-p/362875)

### 코드 실행 결과

![](https://user-images.githubusercontent.com/5077086/66698085-edba0c80-ed15-11e9-9199-5ea5e16afde5.png)

실제로 TEST로 변경된 것을 볼 수 있습니다.

## 마무리

이렇게 스크립트러너로 Jira 이슈의 커스텀 필드를 다뤄보았습니다.
처음에는 어려울 수 있지만 조금씩 다뤄보면 그렇게 어렵지 않습니다.
쉽게 따라하고 적용해보실 수 있는 내용으로 추가 포스트해보겠습니다.

감사합니다. :)