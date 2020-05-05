---
title: Jira Software 8.6 ~ 8.8 release note
toc: true
date: 2020-05-04 18:06:55
categories:
- PM
- System
tags:
- Jira
thumbnail: https://wac-cdn.atlassian.com/dam/jcr:fa01756d-6dcc-45d1-83ab-696fbfeb074f/Jira-icon-blue.svg?cdnVersion=696
---

## Jira Software 8.6 ~ 8.8 릴리스 노트

Jira Software 8.6 ~ 8.8 릴리스 노트:

- 8.6 Release Notes: <https://confluence.atlassian.com/jirasoftware/jira-software-8-6-x-release-notes-978220007.html>
- 8.7 Release Notes: <https://confluence.atlassian.com/jirasoftware/jira-software-8-7-x-release-notes-990550432.html>
- 8.8 Release Notes: <https://confluence.atlassian.com/jirasoftware/jira-software-8-8-x-release-notes-994314852.html>

이번 포스트는 Jira Software 8.6 ~ 8.8 버전 릴리스들을 모아서 보겠습니다.
(사실 8.6 릴리스에 추가된 기능이 많고 8.7, 8.8 릴리스에는 크게 소개할만한 내용은 없습니다.)

## Jira 8.6

2019년 12월에 릴리스한 버전입니다.

### 하이라이트 (Highlights)

- Jira copies over changes files on upgrade
- New JVM code cache check
- Replying to JIRA notifications in Outlook made way better
- Users and roles made better
- PostgreSQL 10 comes to Jira
- Several older platforms get deprecated
- Prefix and suffix search
- Accessible dropdown menus
- Configurable scheme parameters in Jira REST API for projects creation
- Burnup charts in Jira Software
- Self-protect and sleep easy with rate limiting
- New information in the audit log
- Cluster monitoring

8.6 릴리스는 앞선 8.5 엔터프라이즈 릴리스 후에 나온 버전이라 업데이트된 기능들이 많습니다.
시스템 관리자가 알아야 하는 내용보다 태스크 관리 및 프로젝트 관리 측면의 기능 내용을 중점으로 살펴보겠습니다.

### Replying to JIRA notifications in Outlook made way better

많은 사용자들의 요청에 의해 추가된 기능입니다.
Outlook에서 Jira 이슈 알림 메일에 댓글을 남길 수 있도록 하는 기능을 세팅할 수 있게 되었네요.
설명 상으로는 2개의 기능을 deprecate 했다고 하네요.

- Add a comment from the non-quoted email body
- Create a new issue or add a comment to an existing issue

설정과 관련한 내용은 [이 링크](https://confluence.atlassian.com/jirakb/how-to-set-up-replying-to-jira-notifications-via-outlook-975017386.html)에서 확인할 수 있습니다.
참고차 설정 링크에는 기능을 어떻게 설정할 수 있는 방법보다는 개론과 같은 내용이 있습니다.
(Jira 어드민이 대충 이런 느낌으로 사용하면 될 것이다의 느낌이에요.)

### Users and roles made better

![변경된 Users & Roles 관리 메뉴](https://confluence.atlassian.com/jirasoftware/files/978220007/980460545/2/1576573636455/usersandroles.jpg)

기존에는 하나하나 role 그룹에 유저들을 추가해줘야 했다면 이제는 체크박스를 이용해서 더 간편하게 수정할 수 있도록 변경되었습니다.
다만 그전에는 롤에 따라서 어떤 유저가 있는지 한분에 볼 수 있었는데 지금은 roles 메뉴를 눌러서 볼 수 있도록 변경되었습니다.
(지금 상태가 조금 더 잘 정리되어 보이는 것 같긴 합니다. ㅎㅎ)

### Prefix and suffix search

지난 8.0 릴리스에는 Prefix 검색에 대해서 지원을 시작했는데 이번 8.6부터 suffix 검색도 추가되었다고 합니다. 👏

| Prefix 검색 | Suffix 검색 |
|-------------|-------------|
|text ~ "work*"| text ~ "*box"|

검색 기능이 조금씩 개선되는 것 같아 좋네요! :)

### Accessible dropdown menus

![](https://confluence.atlassian.com/jirasoftware/files/978220007/983795015/1/1576576915707/Screen+Shot+2019-12-17+at+11.01.23.png)

드롭다운 메뉴에 대해서 스크롤이 추가되었다는 내용입니다.
기존에는 메인화면을 내려야 했다면 드롭메뉴 자체에 스크롤이 생겨서 편하게 메뉴를 볼 수 있게 되었네요.

### Burnup charts in Jira Software

![](https://confluence.atlassian.com/jirasoftware/files/978220007/980470562/2/1576573635567/Screen+Shot+2019-11-28+at+11.12.52.png)

번업(Burnup) 차트 기능이 Jira Server에도 추가되었습니다.
앞으로 애자일 보드 -> 리포트에서 새로운 번업 차트를 볼 수 있게 되었네요.

### More granular sprint permissions

하이라이트에는 없는 내용이지만 언급이 필요해 보여서 넣었습니다.
스프린트 관리 권한에 대해 몇 가지가 분리되어 추가되었습니다. 이에 따라 스프린트 관리를 사용자 권한에 맞게 부여할 수 있게 되었습니다.
기존에 있던 `Manage Sprint` 권한은 있으나 `Start/Complete sprints`, `Edit sprints` 두 가지 권한이 추가되었네요.
앞으로는 스프린트를 시작, 완료하는 사용자와 삭제도 할 수 있는 사용자 등으로 나눠서 관리할 수 있겠습니다.

그 외의 데이터 센터 내용은 스킵합니다.
(관리자 기능이기도 하고 크게 소개할 내용은 없어 보여서 스킵합니다.)

## Jira 8.7

2020년 2월에 릴리스한 버전입니다.

### 하이라이트 (Highlights)

- Anonymizing users for GDPR compliance
- PostgreSQL 11 support
- OpenID Connect comes to Jira

GDPR 관련 내용, DB 시스템, OpenID(데이터 센터) 등에 대한 릴리스로 일반 유저를 위한 기능 업데이트는 없네요.
8.6 버전에 많이 업데이트하고 나서 안정화하는 버전이었는지 기능 추가는 없었네요.
다음 8.8 버전으로 넘어가겠습니다~

## Jira 8.8

2020년 3월에 릴리스한 버전입니다.

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

감사합니다. :)
