---
title: ScriptRunner 소개 4
date: 2019-05-11 10:30:46
categories:
  - PM
  - System
tags:
  - Jira
  - ScriptRunner
toc: true
thumbnail: https://marketplace-cdn.atlassian.com/files/images/396d3521-7734-4137-9a47-d7afedf1ea18.png
---

## ScriptRunner 소개 #4

- {% post_link scriptrunner1 %}
- {% post_link scriptrunner2 %}
- {% post_link scriptrunner3 %}
- **{% post_link scriptrunner4 %}**

지난 #3 소개 글에서는 Script Fragments 기능까지 보았습니다.
얼마 남지 않았지만 너무 길어져서 #4로 나눴습니다.

- Escalation Services
- Script JQL Functions

길고 길었던 ScriptRunner 소개를 마무리하러 가보겠습니다! :)

## Escalation Services

<https://scriptrunner.adaptavist.com/latest/jira/escalation-service.html>
설명은 아래와 같이 나와있는데 요약해보겠습니다.

> Automate issue escalation with escalation services. Use a JQL query to define processes for modifying issues based on elapsed time. Specify actions (such as transitions) to occur at defined intervals after a specified time has passed.

> 에스컬레이션 서비스를 통해 문제 에스컬레이션 자동화 JQL 쿼리를 사용하여 경과된 시간을 기준으로 문제를 수정하는 프로세스를 정의하십시오. 지정된 시간이 경과한 후 정의된 간격으로 발생할 작업(예: 전환)을 지정하십시오. - with Papago

JQL로 검색한 쿼리들을 일정 시간마다 특정 값을 설정하거나 transition(전환) 할 수 있는 기능입니다.
예를 들면, 2주 동안 변경이 없는 이슈들의 상태를 변경할 수 있겠죠. (혹은 특정 필드를 수정하거나)

![](https://user-images.githubusercontent.com/5077086/57563668-59045900-73db-11e9-89fc-0eaf749e1ac4.png)
입력해야하는 항목은 아래와 같이 많지 않습니다.

- Description: 설정에 대한 설명을 적습니다.
- JQL Query: 변경하고자하는 이슈를 가져오기 위해 JQL을 작성합니다.
- AS User: 어떤 유저로 변경할 것인지 설정합니다.
- Interval/CRON Expression: 얼마나 자주 실행할 것인지 설정합니다. 기본적으로 분 단위로 설정할 수 있습니다.
  - CRON Expression에 대한 것은 [링크](https://crontab.guru/)에서 참고하여 작성해볼 수 있습니다.
- Action: Transition을 설정할 수 있습니다. 반드시 설정해야하는 항목은 아닙니다.
- Additional issue actions: 댓글을 달거나 Resolution을 설정할 수 있습니다. groovy 코드로 작성해야합니다.
  - Show examples를 보고 작성해보는 것을 추천합니다.
- Transition Options: Permissions, Validators, Conditions 확인하는 것을 건너뛸 것인지 설정합니다.

수시로 확인해서 상태를 업데이트하거나 이슈의 항목을 수정해야하는 일이 있다면 사용하기 좋을 것 같습니다.
다만 As User로 설정한 유저의 권한을 잘 확인하여 transition할 수 있는 권한이 있는지 확인해주세요.
(방금 테스트해보았는데 권한없는 동작을 하려할 경우 아예 변경이 진행되지 않습니다.)

## Script JQL Functions

<https://scriptrunner.adaptavist.com/latest/jira/jql-functions.html>
이 항목은 커스텀한 JQL 함수를 추가할 수 있다기 보다 현재 사용할 수 있는 JQL Function들을 보여줍니다.

커스텀한 함수를 추가할 수는 있지만 JIRA 페이지에서 바로 추가할 수 있지는 않습니다.
<https://scriptrunner.adaptavist.com/latest/jira/custom-jql-functions.html>

![](https://user-images.githubusercontent.com/5077086/57564512-c6b68200-73e7-11e9-8d67-b31c30b00467.png)
쭉 내려보면 많은 함수들을 볼 수 있습니다.
함수에 대한 더 자세한 내용을 보려면 위에 있는 jql-functions 링크를 참고하세요.

## ScriptRunner 소개 마무리

4개의 포스트로 소개 문서를 마무리하고자 합니다.
많은 내용들을 찾아보고 테스트 삼아 만들어보느라 시간이 오래걸리기도 했네요.
설정하면서 많이 배웠고 실제 프로젝트에서도 적용해볼만한 내용들이 많았습니다.
다른 JIRA를 사용하는 분들께도 필요한 내용이 있으면 다른 포스트에서 짧게 사용할만한 것들
남겨두겠습니다. :)

긴 글 읽어주셔서 감사합니다. (_ _)
