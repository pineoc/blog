---
title: Jira Software 8.10~8.12 release notes
toc: true
date: 2020-09-06 20:53:57
categories:
- PM
- System
tags:
- Jira
thumbnail: https://wac-cdn.atlassian.com/dam/jcr:fa01756d-6dcc-45d1-83ab-696fbfeb074f/Jira-icon-blue.svg?cdnVersion=696
---

## Jira Software 8.10 ~ 8.12 릴리스 노트

Jira Software 8.10 ~ 8.12 릴리스 노트:

- [8.10 Release Notes](https://confluence.atlassian.com/jirasoftware/jira-software-8-10-x-release-notes-1004948108.html)
- [8.11 Release Notes](https://confluence.atlassian.com/jirasoftware/jira-software-8-11-x-release-notes-1013852753.html)
- [8.12 Release Notes](https://confluence.atlassian.com/jirasoftware/jira-software-8-12-x-release-notes-1019380834.html)

Jira Software 8.10 ~ 8.12 버전 릴리스들을 모아서 보겠습니다.
3개의 버전을 모아서 보아도 큰 업데이트는 없네요. 다만 QoL(Quality of Life) 개선 내용이 있어서 좋네요. 👍

## Jira 8.10

2020년 6월(June)에 릴리스한 버전입니다. - [8.10 Release Notes](https://confluence.atlassian.com/jirasoftware/jira-software-8-10-x-release-notes-1004948108.html)

### 하이라이트 (Highlights)

- OAuth 2.0 for your incoming mail
- User anonymization (GDPR) improvements
- More insight into your custom fields
- Stale nodes automatically removed
- Optimized custom fields

> 8.10 릴리스는 커스텀 필드 관리 측면에서의 개선과 OAuth 2.0 추가된 것이 주 포인트입니다.
> 다만 커스텀 필드 관리 측면의 내용은 모두 데이터 센터 한정한 내용이긴 합니다. 자세한 내용은 아래에서 더 자세하게 보시죠.

### OAuth 2.0 for your incoming mail

구글과 마이크로소프트에서 Basic Authnication을 사용하지 않을 것에 대한 대응 업데이트입니다.
기존에 메일에서 사용할 수 있는 기능을 계속 사용할 수 있도록 OAuth 2.0을 추가했네요.
gmail, Microsoft Exchange에서 비밀번호를 사용하지 않고 기능을 사용할 수 있게 되었습니다.
(물론 OAuth 2.0과 관련한 설정을 해줘야겠죠 😀)

![Add OAuth 2.0 Integration](https://confluence.atlassian.com/jirasoftware/files/1004948108/1004948141/1/1590047864061/localhost_8443_jira_plugins_servlet_oauth2+%282%29.png)

자세한 내용은 [Integration with OAuth 2.0](https://confluence.atlassian.com/adminjiraserver0810/integrating-with-oauth-2-0-1014674403.html) 문서를 참고해주세요.

> 저도 봇 개발을 하고있는 입장에서 OAuth 2.0 추가는 좋네요.
> 다만 Https 설정이 기본이고 URL도 잘 설정해둬야 잘 동작한다네요.
> 문서를 꼼꼼히 읽어보고 나중에 설정하는 방법도 포스팅해보겠습니다.

### User anonymization (GDPR) improvements

GDPR과 관련하여 유저의 익명화 기능에 대한 개선 내용입니다. 익명화 기능의 범위를 늘렸다고 하네요.

- 이슈 검색에서 Reporter, Creator 익명화
- 이슈 히스토리에 있는 이름 익명화 (Assignee, Reporter, Single- and Multi-user picker fields)
- 이미 삭제된 유저에 대해 익명화할 수 있는 기능 추가

더 자세한 내용은 [Anonymizing users](https://confluence.atlassian.com/adminjiraserver/anonymizing-users-992677655.html)에서 더 볼 수 있습니다.

> GDPR과 관련한 내용은 많이 와닿지 않는 내용이긴하지만 사용자의 정보를 지키고 관리하는 것은 필요하니 알아둘 필요는 있는 것 같습니다.

### More insight into your custom fields

(데이터 센터)

![Custom field indexing](https://confluence.atlassian.com/jirasoftware/files/1004948108/1004948140/1/1590047714056/Field+indexers+one+table+-+ideal+formatting+%282%29.png)

"Jira Administration > System > Clustering > Actions > Custom field indexing" 경로에서 커스텀 필드가 어떻게 인덱싱되고 있는지 볼 수 있도록 기능이 추가되었네요.

> 데이터 센터와 관련해서 관리자 역할을 하고 있지는 않아서 모르긴하지만 커스텀 필드의 값의 인덱싱 관리가 어려운 경우에는 좋을 것 같긴하네요. 😀

### Stale nodes automatically removed

(데이터 센터)
지난번에 클러스터 관리와 관련한 자동화를 소개했었는데 자동으로 오래된 노드를 지워주는 기능이 추가되었네요.
자세한 내용은 [Jira cluster monitoring](https://confluence.atlassian.com/adminjiraserver/jira-cluster-monitoring-983794905.html)에서 볼 수 있습니다.

### Optimized custom fields

(데이터 센터)
많은 양의 커스텀 필드는 성능에 영향도 주고 인덱싱할 때에도 시간이 오래 걸리는 요인이기도 합니다.
이런 상황을 개선하기 위해 필요한 상황에서만 커스텀 필드를 보여주거나 관리하도록 변경했네요.
자세한 내용은 [Optimizing custom fields](https://confluence.atlassian.com/enterprise/optimizing-custom-fields-1005343684.html)에서 볼 수 있습니다.

## Jira 8.11

2020년 7월(July)에 릴리스한 버전입니다. - [8.11 Release Notes](https://confluence.atlassian.com/jirasoftware/jira-software-8-11-x-release-notes-1013852753.html)

### 하이라이트 (Highlights)

- Managing private filters and dashboards
- Issue detail view is now optional
- Improved email notifications about mentions
- Embedded Crowd upgrade
- More stability in the Favorite Filters gadget
- Restricting sprint selection
- Configure how fast stale nodes are moved offline

하이라이트만 봤을 때는 몇 가지 마음에 드는 기능들이 보이네요.
프라이빗 필터, 대시보드 관리 가능해지는 점과 Jira에서 멘션시 메일 오는 것에 대한 개선이 눈에 띕니다.
한번 각각 자세히 볼까요?

### Managing private filters and dashboards

![드디어 private filter, dashboard를 수정할 수 있게 되었습니다!](https://confluence.atlassian.com/jirasoftware/files/1013852753/1014671282/1/1593813265040/filters_rn_light.jpg)

이번 8.11 업데이트 부터 private 필터, 대시보드를 수정할 수 있게 되었습니다.
주로 탈퇴한 사용자/유효하지 않은 사용자가 만든 필터, 대시보드를 관리하기 어려운 상황이 있는데 이런 상황을 해결할 수 있게되었네요. 👏
(대시보드에 연결되어있는 필터 등 문제가 있을만한 내용을 관리자가 수정할 수 있게된 것은 좋은 것 같습니다.)

### Issue detail view is now optional

![보드에서 이슈 상세보기 화면 옵션화](https://confluence.atlassian.com/jirasoftware/files/1013852753/1014671283/1/1593813282592/detailview_rn_light.jpg)

보드에서 이슈 카드를 누를 경우에 나오는 이슈 상세보기 화면을 보이지 않도록 설정할 수 있는 옵션이 추가되었습니다.
칸반/스프린트 보드에서 Board > Hide detail view로 설정할 수 있네요.
이 옵션을 설정하고나면 이슈를 한번 클릭해도 상세보기 화면이 나오지 않습니다.

### Improved email notifications about mentions

![멘션시 이메일 알림 개선](https://confluence.atlassian.com/jirasoftware/files/1013852753/1014671285/1/1593813300068/mentions_rn_light.jpg)

이번 개선 기능도 그동안 메일 알림 읽는데에 어려움을 주었던 것을 해소해주는 기능이네요.
8.0에 적용되었던 알림을 묶어서 메일로 전송해주는 기능이 있었는데요.
멘션시 알려주는 알림과 별개의 흐름(기능)이라서 멘션 알림 따로 묶음 알림 메일이 따로 전송되고 있었습니다.
이번 업데이트로 묶음 알림과 멘션 알림 메일이 같이 전송되도록 개선되었네요.
참고할 점은 멘션 알림은 바로 알려질 필요가 있는 경우가 많으니 멘션시 묶어서 보낼 내용을 같이 보내준다고 합니다.

> 이 업데이트로 멘션 알림 따로 묶음 알림 따로 받지 않아도 되서 즐겁습니다. 😀

### Embedded Crowd upgrade

Crowd라는 라이브러리 2.0 -> 4.0 업데이트가 있었다고 합니다.
성능 향상과 클러스터링 지원, 디렉토리 페일오버, 버그 수정 등이 적용되었다고 하네요.
(사용자 측면에서는 딱히 뭐가 달라졌는지 알 수 있을만한 내용은 없네요.)

> API 문서를 보아하니 유저 계정 싱크나 계정 관리 쪽 업데이트로 성능 향상이 된 것 같습니다.
> LDAP 싱크에 성능향상이 있을까 궁금하네요. (성능 향상이 있으면 벤치마크를 보여주지...)

### More stability in the Favorite Filters gadget

![favorite 필터 가젯 안정성 강화!](https://confluence.atlassian.com/jirasoftware/files/1013852753/1013853274/1/1593772424022/dashboardgadget_rn.jpg)

대시보드에서 가끔 favorit filters 가젯이 오류가 나서 안나오는 경우가 있습니다.
필터에 문제가 발생했거나 시스템 상 필터에 있는 이슈를 가져오지 못하는 경우가 있어서 그런 것 인데요.
문제가 있는 필터만 보이지 않도록 따로 에러 처리를 한 것으로 보입니다.
(종종 쓰는 기능이긴한데, 느릴 때가 있긴해도 실제로 보지는 못했습니다. 물론 타임아웃을 겪은 적은 좀 있지만요.)

### Restricting sprint selection

![스프린트 제한 설정](https://confluence.atlassian.com/jirasoftware/files/1013852753/1013852713/1/1593697844335/Screen+Shot+2020-04-29+at+10.46.30.png)

스프린트 설정의 오류를 개선하기 위해 관리자 옵션에서 `Relevant sprints` 라는 옵션이 추가되었네요.
옵션을 설정할 경우 프로젝트에 속한 스프린트만 볼 수 있게됩니다. (다른 스프린트를 보고 싶다면 Show all로 볼 수 있긴하지만요.)

### Configure how fast stale nodes are moved offline

(데이터 센터)

앞서 8.10에서 소개했던 오래된 노드를 자동으로 삭제해주는 기능이 있었는데요.
이번에 업데이트된 것은 오래된 노드를 오프라인으로 바꿔주는 시간을 설정할 수 있는 기능입니다.
jira.not.alive.active.nodes.retention.period.in.hours 설정 값으로 오프라인으로 변경되는 데에 시간을 설정할 수 있다고하네요.

## Jira 8.12

2020년 8월에 릴리스한 버전입니다. - [8.12 Release Notes](https://confluence.atlassian.com/jirasoftware/jira-software-8-12-x-release-notes-1019380834.html)

### 하이라이트 (Highlights)

- Revamped Audit log
- Dates for future sprints
- Jira loves accessibility
- Access Data Center features on Server infrastructure

### Revamped Audit log

![](https://confluence.atlassian.com/jirasoftware/files/994314852/998879194/2/1587581320827/Screen+Shot+2020-03-19+at+20.53.54.png)

데이터 센터 버전과 몇 가지 기능이 다를 수는 있겠지만 서비스 로그에 대해서 추가적으로 볼 수 있도록 기능이 개선되었습니다.

- 어떤 로그를 어느 기간 동안 보관할 것 인지를 설정할 수 있습니다. (you can decide which events are logged and how long you want to keep them)
- 로그들에 대해 더 자세히 알 수 있습니다. (you can filter the events, expand each for further details, and export the audit log if necessary)
- 카테고리로 정리된 로그를 통해 로그 확인이 개선되었습니다. (by getting an audit log that’s clear and categorized, you don’t need to spend time browsing through piles of events.)
- 나머지는 데이터 센터 내용이라서 스킵합니다.
  - 인스턴스와 관련한 로그를 확인할 수 있다는 내용과 3rd 파티 툴 연동 등에 대한 내용이 포함되어있습니다.

위 개선 사항들은 `Administration> System > Audit log` 에서 확인하실 수 있습니다.

### Dates for future sprints

![](https://confluence.atlassian.com/jirasoftware/files/994314852/994314857/3/1587581322091/Screenshot+2020-02-07+at+10.08.16.png)

미래 스프린트를 위해 날짜 입력을 할 수 있도록 업데이트되었네요.
기존에는 스프린트에 날짜를 입력하도록 Required(필수 입력) 설정되어있었는데 미래 스프린트 계획을 위해 추가된 기능으로 보입니다.

### Jira loves accessibility

![](https://confluence.atlassian.com/jirasoftware/files/994314852/993924584/2/1587581321481/accessibility_relnotes.jpg)

<https://confluence.atlassian.com/jirasoftwareserver/accessibility-998878998.html>
개인 설정을 통해서 상태(Status)의 색/무늬를 변경할 수 있도록 할 수 있게 되었네요.
관련한 자세한 내용은 위 링크에서 보실 수 있습니다.

## 마무리

8.6 ~ 8.8 버전을 모두 살펴보았습니다.
8.6 버전에는 추가/수정된 기능들이 많았네요. 8.7, 8.8 버전은 안정화 업데이트 같은 느낌을 받았습니다.
한 달마다 버전 업데이트를 하고 있는데 버그 내용도 하나하나 보고 싶지만 이번 포스트에서는 스킵하고 다음 버전에서는 코멘트할 내용이 있을지 보겠습니다.
