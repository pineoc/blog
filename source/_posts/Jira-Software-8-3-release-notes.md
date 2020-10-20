---
title: Jira Software 8.3 릴리스 노트
toc: true
date: 2019-10-06 18:15:03
categories:
- PM
- System
tags:
- Jira
- ReleaseNotes
thumbnail: https://wac-cdn.atlassian.com/dam/jcr:fa01756d-6dcc-45d1-83ab-696fbfeb074f/Jira-icon-blue.svg?cdnVersion=696
---

## Jira Software 8.3 릴리스 노트

Jira Software 8.3.x 릴리스 노트: <https://confluence.atlassian.com/jirasoftware/jira-software-8-3-x-release-notes-972326971.html>

2019년 7월에 릴리스된 Jira Software 8.3 기능에 대해 살펴보는 포스트입니다.
위 릴리스 노트에서 자세한 내용을 보실 수 있으며, 이 포스트는 주관적인 생각을 담고 있습니다.

### 하이라이트 (Highlights)

- **Jira Server mobile app**
- Content Delivery Network (CDN) for Jira Data Center
- AdoptOpenJDK JRE bundled with JIRA
- List of custom changes after upgrade
- **New filters to search for custom fields**
- Browsing projects is faster now
- **Improvements to batching emails**
- Cluster lock mechanism improved in Data Center
- **Re-indexing made better**

### Jira Server mobile app

8.0 버전에서 베타로 있었던 Jira 모바일 앱이 8.3 버전에서 부터 정식 버전으로 오픈되었습니다!
자세한 사항은 따로 페이지가 만들어져 있네요. ([링크](https://confluence.atlassian.com/jirasoftwareserver/jira-server-mobile-app-966063511.html))

- Android: <https://play.google.com/store/apps/details?id=com.atlassian.jira.server>
- iOS: <https://apps.apple.com/us/app/id1405353949>

모바일 웹뷰보다는 잘 보이는 것들이 많습니다.
저는 모바일 폰 보다 패드에서는 시원하게 보이는 것들이 많아서 편하게 사용하고 있습니다.
실제로 컴퓨터로 보는게 더 편한 것들이 많은 것은 넘어가겠습니다. :)

### New filters to search for custom fields

![](https://confluence.atlassian.com/jirasoftware/files/972326971/972352770/2/1567587244325/Screenshot+2019-06-04+at+10.26.15.png)

시스템 설정 > 이슈의 커스텀 필드를 검색하는데에 편의를 위해 필터가 생겼습니다.
이 기능으로 커스텀 필드를 골라서 보는 데에 조금 더 빠르고 편리하게 수정할 수 있게되었습니다.

- 특정 프로젝트가 사용하는 커스텀 필드
- 커스텀 필드 타입
- 특정 스크린이 사용하는 커스텀 필드

### Re-indexing made better

커스텀 필드 추가나 이슈 필드 수정이 있으면 항상 따라오는 리인덱싱!
이 내용은 데이터 센터 버전에 해당하는 내용이라고 하네요.
리인덱싱을 진행할 때, 데이터 센터 노드 별로 진행하는 사항 등에 대한 경고로 실수를 막을 수 있도록 했다고 합니다.

## 마무리

이번 8.3 릴리스는 데이터 센터 업데이트 스펙이 많은 것 같습니다.
서버 버전 사용자 측면에서는 큰 변화는 없으나 시스템 관리자가 편해진 내용도 있었습니다.
큰 스펙으로는 서버 버전의 모바일 앱을 정식으로 지원하게 되었다는 것!

다음 버전에는 어떤 기능들이 추가될지 기대하며 포스트 마치겠습니다.
