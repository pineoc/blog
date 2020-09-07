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

- Improved user picker
- More control over your Advanced Audit log
- Support for MySQL 8.0
- Less app impact on indexing
- Users created automatically with Just-in-time user provisioning
- Small improvements to make your day

### Improved user picker

![유저 피커 개선!](https://confluence.atlassian.com/jirasoftware/files/1019380834/1019380843/1/1595492968913/Screen+Shot+2020-07-14+at+11.14.13.png)

커스텀 필드에서 유저 피커 필드의 경우 리포터, 담당자와 같은 시스템 필드처럼 사용자 이미지 및 이름을 볼 수 있도록 개선되었습니다.

> 싱글 유저 피커만 개선된 것 같고 멀티 유저 피커는 나중에 개선될지 봐야할 것 같네요.

### More control over your Advanced Audit log

(데이터 센터)

![데이터 센터-Audit log 컨트롤 개선](https://confluence.atlassian.com/jirasoftware/files/1019380834/1018761801/1/1595576728949/Screenshot+2020-07-24+at+09.43.41.png)

데이터 센터를 위한 기능들이 지속적으로 개선되고 있네요. 이번에도 Audit log 개선사항입니다.
카테고리, 제목을 필터해서 볼 수 있게되었네요. 추가로 로그 파일을 어떻게 저장할 것인지도 옵션화되었습니다.
그 외에 우선순위 수정, 시큐어 어드민 로그인, 이슈 익스포트, OAuth 2.0 설정에 대한 이벤트도 Audit log에서 볼 수 있도록 이벤트가 추가되었습니다.

### Support for MySQL 8.0

말 그대로 MySQL 8.0 지원으로 추가된 내용입니다.

### Less app impact on Jira indexing

(데이터 센터)

인덱싱 진행시 시간이 오래걸리는 이슈를 개선하고자 하는 기능입니다.
`Document-Based Replication` 기능을 기반으로 인덱싱시 앱에 영향이 크지 않도록 한다고 하네요.
[Document-based replication in Jira Data Center](https://confluence.atlassian.com/enterprise/document-based-replication-in-jira-data-center-1021214730.html)와 관련한 내용은 여기서 자세히 보실 수 있습니다.

> **Document-based replication**을 DBR이라고 부르고 소개하고 있네요.
> 링크의 문서에 보면 bad state를 완전히 없앤 기술이라고 하는데요. 정보를 리플리케이션하는 방식에 대한 개선 같습니다.
> 자세한 것은 링크를 참고해보셔요!

### Users created automatically with Just-in-time user provisioning

(데이터 센터)


### Small improvements to make your day

작은 개선이라고 소개했지만 너무나 큰 선물! 이번에도 좋은 개선 사항이 추가되었네요.

#### Order of statuses on boards

board > Configure에서 보드에서 보이는 이슈를 상태 순서대로 볼 수 있도록 설정할 수 있게 되었습니다.

> todo를 맨 밑에서 보고 싶다면 순서를 상태 컬럼에서 todo 상태를 맨 밑으로 보내면 됩니다.

#### Accessibility: Background in subtle buttons

이 기능은 단순히 마우스 오버시에 표시되는 회색을 기본 상태가 회색으로 보일 수 있도록 설정하는 기능입니다.
기존에 버튼이 잘 안보였다면 이 개인 설정을 켜보는 것이 좋겠군요. 😄

## 마무리

8.10 ~ 8.12 Jira 기능을 살펴보았습니다.
생각보다 많은 업데이트가 있었네요. (작성하면서 절반이 데이터 센터 전용 기능이었던 것 같은데 기분탓이겠죠 😂)
다음 업데이트인 8.13도 준비되고 있는 것 같지만 아마 LTS 릴리스라서 큰 변경사항은 없을 것 같네요.
8.13 업데이트 이후에 8.14를 기대하면서 다음 포스트를 준비해보겠습니다.
다음에 만나요! 감사합니다! 👋
