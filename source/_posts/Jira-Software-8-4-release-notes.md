---
title: Jira Software 8.4 릴리스 노트
toc: true
date: 2019-10-09 16:10:20
categories:
- PM
- System
tags:
- Jira
---

## Jira Software 8.4 릴리스 노트

Jira Software 8.4.x 릴리스 노트: <https://confluence.atlassian.com/jirasoftware/jira-software-8-4-x-release-notes-975017507.html>

2019년 9월에 릴리스된 Jira Software 8.4 기능에 대해 살펴보는 포스트입니다.
위 릴리스 노트에서 자세한 내용을 보실 수 있으며, 이 포스트는 주관적인 생각을 담고 있습니다.

### 하이라이트 (Highlights)

- Archived issues taken to the next level (Data Center)
- **Better email notifications, right from the start**
- **Filters in Multi User picker Custom field**
- **External links open in a new tab**
- Jira becomes more accessible
- A large number of versions is OK for boards
- **Time tracking in bulk edit**
- Open links in your mobile app
- **Jira Docker**
- New supported databases

이번 8.4 릴리스는 하이라이트 리스트만 봐도 내용이 많긴하네요.
몇가지는 시스템 설정 관련 내용이긴 하지만 한번 보겠습니다.

### Better email notifications, right from the start

8.0 버전에 들어갔던 Batch 이메일 알림에 대한 추가 개선 내용했고, 이 내용이 기본 설정으로 변경되었습니다.
기본 템플릿이 있지만 추가적으로 커스텀하게 알림 받고 싶은 것에 대해 설정할 수 있게되었기도 합니다.

- [customizing-email-content-batched-notifications](https://confluence.atlassian.com/adminjiraserver/customizing-email-content-batched-notifications-976770772.html)
- [adding-custom-fields-to-emails-batched-notifications](https://confluence.atlassian.com/adminjiraserver/adding-custom-fields-to-emails-batched-notifications-968669988.html)

다만 시스템 설정 상에서 쉽게 변경할 수는 없고 Velocity template이라는 것을 수정해야한다고 합니다.
나중에 관련해서 세팅하는 방법을 따로 포스트해봐야겠습니다.
(저도 아직 사용해보지 않아서 얼마나 힘들지 모르겠네요.)

### Filters in Multi User picker Custom field

릴리스 노트에 있는 내용 그대로 들고와보았습니다. 유저 요청에 따라 추가된 기능이라고 하네요.
> In response to user requests, we've made it possible to limit the multi user picker custom field to hold only specific set of users.
> This is to prevent sending notifications to random users as a result of mistyping user names.
> This adds to the overall security of issues.

![](https://confluence.atlassian.com/jirasoftware/files/975017507/975017552/1/1563959636990/Screen+Shot+2019-07-24+at+11.04.16.png)

추가된 기능은 필터에 멀티 유저 피커 커스텀 필드 내용을 추가하여 사용할 수 있는 기능입니다.
필터에 다른 유저를 잘못 입력하는 것을 방지할 수 있는 기능 같네요.

### External links open in a new tab

YourUserProfile > Profile > Preferences > External links 메뉴에서
외부 링크를 항상 새로운 탭에서 볼 수 있는 옵션을 제공합니다.

### Time tracking in bulk edit

![](https://confluence.atlassian.com/jirasoftware/files/975017507/976163716/1/1566286925646/image__6___1_.png)
Time tracking 필드의 벌크(bulk) 수정이 가능한 기능이 추가되었습니다.
일괄적으로 추정 시간, 남은 시간을 변경하는 데에 좋을 것 같습니다.

### Jira Docker

Jira 서버 버전 및 데이터 센터 버전을 Docker 컨테이너로 사용할 수 있도록 공식 지원한다고 합니다.
자세한 내용은 링크에서 보실 수 있습니다. <https://hub.docker.com/u/atlassian>
Jira 외에 컨플루언스, 파이프라인 등 다른 이미지들도 있어서 시스템 구성시 사용해볼 수 있을 것 같습니다.

- Jira Software: <https://hub.docker.com/r/atlassian/jira-software>
- Jira Core: <https://hub.docker.com/r/atlassian/jira-core>

## 마무리

8.4 릴리스는 8.5 릴리스 전에 많이 개선된 느낌이 있네요.
Docker 이미지가 추가된 것도 좋은 업데이트 사항이었고 향후 있을 8.5 릴리스 내용도 기대가됩니다.
