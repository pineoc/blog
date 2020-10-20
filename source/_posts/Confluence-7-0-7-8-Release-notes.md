---
title: Confluence 7.0~7.8 Release notes
toc: true
date: 2020-10-18 15:09:59
categories:
- PM
- System
tags:
- Confluence
- ReleaseNotes
thumbnail: https://user-images.githubusercontent.com/5077086/96360171-853a1280-1155-11eb-9895-cd15add31f09.png
---

## Confluence Release Notes

- [All Release Notes](https://confluence.atlassian.com/doc/confluence-release-notes-327.html)

## Confluence 7.0 - 7.8 릴리스 노트

지난 **{% post_link Confluence-6-12-6-15 %}** 포스트에서 컨플루언스 버전 6에 대한 릴리스 노트를 소개하고 한동안 정리를 안했더니 버전 7이 어느새 7.8까지 나왔네요.
모든 내용을 다루기는 힘들 것 같아 하이라이트 기능만 짚고 넘어가보고자 합니다. 😀
(하이라이트 항목은 없지만 사용자 입장에서 알아두면 좋을만한 내용들을 정리해본다고 생각해주시면 될 것 같습니다.)

## 7.0 Release notes

- [7.0 Release notes](https://confluence.atlassian.com/doc/confluence-7-0-release-notes-973479448.html)

버전 7의 첫 버전 업데이트는 2019년 9월이었네요.
7.0 버전 업데이트에는 사용자 측면에서는 큰 변경사항은 없습니다. 다만 버전 7에서는 어떤 것을 해나갈지 릴리스 노트 앞에 이야기를 해두었네요.

### Welcome to Confluence 7

In Confluence 7.0 we're continuing to invest in the future of Confluence, providing solutions for geo-performance challenges, better upgrade planning tools, and new admin tools to help meet your organization's needs for years to come.

> 컨플루언스 7에서는 컨플루언스의 미래에 투자하는 것을 지속한다고 합니다. geo-performance(지역, 리전별 성능. 예를 들면 다른 나라에서 페이지를 로딩할 때의 성능 같은 것) 도전과 플래닝 툴 개선, 새로운 어드민 툴을 만들 것이라고 하네요.
> 현 시점에서 얼마나 지켜졌는지도 한번 확인해보면서 릴리스 노트 소개해보겠습니다. 😂

### Be better prepared for upgrades

![General Configuration > Plan your upgrade](https://confluence.atlassian.com/doc/files/973479448/975032620/3/1593140959919/plan-your-upgrade.png)

Jira에 업데이트 되었던 pre-upgrade 플래닝 기능이 추가되었네요.
버전 업데이트를 더 안정적으로 할 수 있도록 하는 툴의 추가는 좋은 것 같습니다.

### Move your site to the Cloud

![Cloud Migration Assistant for Confluence](https://confluence.atlassian.com/doc/files/973479448/975032621/3/1593140960222/5_Review.png)

버전 업데이트와 더불어 클라우드로 마이그레이션 할 수 있도록 마이그레이션 툴이 추가되었습니다.
최근에 클라우드 버전으로 완전히 변경하기 위한 기반 작업이 아니었을까 싶네요

7.0은 별다른 업데이트 내용이 없어 마치고 다음 릴리스 노트로 가보겠습니다.

## 7.1 Release notes

- [7.1 Release notes](https://confluence.atlassian.com/doc/confluence-7-1-release-notes-976776964.html)

2019년 11월에 업데이트되었던 릴리스 노트입니다.
7.1 업데이트에도 크게 소개할만한 내용은 없네요.
매크로 관련 기능 개선 및 페이지 복사할 때에 첨부 파일도 같이 복사할지에 대한 옵션이 추가되었습니다.
Java 11 지원 및 컨플루언스 내에서 엑셀이나 워드 파일 등 Office 파일들을 Office 앱으로 바로 연결해서 수정할 수 있는 기능을 컴패니언 앱에서도 사용할 수 있도록 지원한다고 합니다.

그 외에는 더 소개할만한 내용이 없네요.

## 7.2 Release notes

- [7.2 Release notes](https://confluence.atlassian.com/doc/confluence-7-2-release-notes-979421828.html)

2019년 12월에 업데이트되었던 릴리스 노트입니다.
데이터 센터 쪽 업데이트 한개가 있네요. 인프라에 있는 서버들을 관리하기 위해 클러스터 모드를 이용해서 관리할 수 있도록 업데이트가 되었네요.
인프라에서 관리되는 서버들의 설정 등을 관리할 수 있도록 업데이트 되었습니다.
요거 하나 업데이트 있는 7.2 버전이었네요.

## 7.3 Release notes

- [7.3 Release notes](https://confluence.atlassian.com/doc/confluence-7-3-release-notes-983794557.html)

2020년 2월에 업데이트되었던 릴리스 노트입니다.
파일 수정 컨트롤과 관련한 내용 및 권한 등에 대해 업데이트가 되었네요.

### Advanced permissions management for easier administration

권한과 관련한 업데이트 내용은 공간 권한 관리를 관리자가 쉽게할 수 있도록 하는 기능들이었습니다.
(사용자 권한이 올바른지 확인하거나 한번에 권한을 변경하거나하는 등의 기능이 추가되었습니다.)
자세한 내용은 여기서 볼 수 있습니다. [Inspect permissions](https://confluence.atlassian.com/doc/inspect-permissions-992678939.html)

### Safeguarding performance & rate limiting

페이지 트리를 로딩할 때, 많은 페이지를 로딩하면서 권한에 따라 보여주는 것이 달라집니다.
이에따라 성능에도 영향을 주는데 이를 피할 수 있도록 트리 단계당 최대 200페이지까지만 보이도록 하고 이후 내용은 Show all로 볼 수 있도록 변경했다고 합니다.
(페이지가 많고 한 단계에 많은 페이지가 있다면 유용하긴 할 것 같네요.)

![Self-protect and sleep easy with rate limiting](https://confluence.atlassian.com/doc/files/983794557/987144818/1/1579213681219/rate-limiting.png)

rate limiting은 간단하게 컨플루언스 시스템에 요청을 제한하여 안정적으로 동작할 수 있도록 하는 기능입니다.
주로 REST API 요청이 많은 것을 예로 들고 있고 그에 대한 제한을 이야기하고 있습니다.
자세한 내용은 여기서 볼 수 있습니다. [Improving instance stability with rate limiting](https://confluence.atlassian.com/doc/improving-instance-stability-with-rate-limiting-992679004.html)

## 7.4 Release notes

- [7.4 Release notes](https://confluence.atlassian.com/doc/confluence-7-4-release-notes-994312218.html)

2020년 4월에 업데이트되었던 릴리스 노트입니다.
이번 7.4버전은 LTS(Long Term Support) 업데이트 버전으로 설정되어 진행된다고 합니다.
그 외의 업데이트 내용은 특별히 공유할만한 내용은 없고 컨플루언스 서버 앱을 Mobile Device Management (MDM) 솔루션을 이용해서 디바이스 관리를 할 수 있다고 합니다.

## 7.5 Release notes

- [7.5 Release notes](https://confluence.atlassian.com/doc/confluence-7-5-release-notes-1001823832.html)

2020년 5월에 업데이트되었던 릴리스 노트입니다.
7.5 버전 업데이트에는 audit log, 테이블 색상 추가, 위젯 커넥터 업데이트 등이 있습니다.

### Audit like a pro with our new Audit log

![Audit log](https://confluence.atlassian.com/doc/files/1001823832/1005784961/1/1588909259958/audit-log-RNs.png)

audit log와 관련해서 어떤 내용을 저장할 것인지 설정화면이 사용성이 개선되었습니다.
얼마나 저장할 것인지, 어떤 내용을 저장할 것인지 등 관리할 수 있게되었다고 하네요.

### Bring some colour to your tables

![table colour](https://confluence.atlassian.com/doc/files/1001823832/1005784963/1/1588909319988/table-cell-colours.png)

원래는 색이 몇개 안되었었는데 많이 추가되었네요. (색이 많이 추가되어서 하트도 그릴 수 있네요 😸)

### Widget connector gets a modern makeover

페이지 매크로에 여러가지 위젯 커넥터를 이용해서 페이지를 작성할 수 있도록 위젯이 추가되거나 업데이트되었습니다
페이스북, Figma, LinkedIn, Microsoft Stream, Frezi, Spotify를 사용할 수 있다네요.
구글 캘린더, 맵, 구글 docs, 트위터도 위젯이 개선되었다고 합니다.

### ETC

추가로 OpenID 커넥트 프로토콜을 사용할 수 있게된 내용이나 컴패니언 프로그램 언어 지원 등에 대한 내용도 있습니다.

## 7.6 Release notes

- [7.6 Release notes](https://confluence.atlassian.com/doc/confluence-7-6-release-notes-1004945745.html)

2020년 6월에 업데이트되었던 릴리스 노트입니다.
사용자 입장에서는 볼만한 내용은 없고 관리자 입장에서는 audit log 관련 기능이 눈에 띄겠네요.

![Capture more end-user activity in the audit log](https://confluence.atlassian.com/doc/files/1004945745/1013842995/1/1592796851298/audit-new-events.png)

사용자들의 액션 중 페이지나 블로그 포스트를 옮기거나 공유, 권한 요청, 권한 생성 등을 볼 수 있게되었습니다.

## 7.7 Release notes

- [7.7 Release notes](https://confluence.atlassian.com/doc/confluence-7-7-release-notes-1004960930.html)

2020년 8월 업데이트되었던 릴리스 노트입니다.
웹훅, 에디팅 기능 개선, 접근성 개선, 성능 개선 등 이번 업데이트에는 변경사항이 많네요.
Audit log에서는 필터를 할 수 있는 것이 많아져서 더 보기 편해질 것 같습니다.

### Take Confluence to the next level with webhooks

기존에 컨플루언스에 웹훅이 없다가 7.7 버전에 웹훅이 추가되었다고 합니다.

![Webhooks](https://confluence.atlassian.com/doc/files/1004960930/1018771477/1/1597377701819/webhooks.png)

- 유저 또는 그룹이 추가되거나 삭제되었을 때
- 컨텐츠가 추가되거나 업데이트되었을 때
- 컨텐츠가 삭제되거나 복원되거나 휴지통에서 제거할 때

이런 이벤트가 발생할 경우 웹훅이 동작할 수 있게 설정할 수 있다고 합니다.
관련한 자세한 내용은 [Managing Webhooks](https://confluence.atlassian.com/doc/managing-webhooks-1021225606.html) 페이지에서 볼 수 있습니다.

### Seamless editing experience & Accessibility improvements

에디팅할 때 여러가지 이슈들을 수정하고 개선했다고 합니다. (끝나지 않는 에디터 기능 개선..)
부디 많은 개선이 이뤄졌기를 🙏

추가로 접근성 개선도 함께 이뤄졌네요.
버튼에 이름이 빠진 것, 키보드 네비게이션 버그 수정 등이 이뤄졌습니다.

### Reindex your cluster without downtime

클러스터에 리인덱스를 다운타임(점검) 없이 할 수 있도록 개선되었다고 합니다.

![Content Indexing](https://confluence.atlassian.com/doc/files/1004960930/1018272539/1/1595989774107/reindex-cluster.png)

### More control of your audit log

![filter by category](https://confluence.atlassian.com/doc/files/1004960930/1013858084/1/1594971600827/audit-category-filter.png)

카테고리, 제목 별로 필터를 할 수 있도록 audit log가 개선되었네요.
많은 로그를 봐야하는 관리자 입장에서 로그 관련한 기능이 또 추가되어 사용성이 올라간 느낌입니다. :)

### Page Properties Report macro performance improvements

페이지 속성 보고서 매크로의 성능 개선이 이뤄졌습니다.
보고서를 500개 까지만 제한하여 로드하는 것을 통해 3000 페이지까지 보여줄 수 있도록 개선이 되었다고 하네요.
이 제한 값은 시스템 값으로 변경할 수 있다고 합니다.

## 7.8 Release notes

- [7.8 Release notes](https://confluence.atlassian.com/doc/confluence-7-8-release-notes-1018778133.html)

2020년 9월에 업데이트되었던 릴리스 노트입니다.
audit log에서 유저 활동 관련 내용 추가와 페이지 속성 보고서 매크로 레이블 제한 수 증가, 중지된 매크로 보여주기 등이 업데이트되었습니다.
(추가로 allowlist, blocklist 변경건도 있네요 💃🏿)

## 마무리

7.0 버전부터 7.8 버전까지 살펴보았습니다.
하나하나 모든 기능을 설명해보려고 했으나 내용이 너무 많아서 생략하거나 압축한 버전도 있네요.
사실 컨플루언스는 지라보다는 문서 에디팅 기능에 초점이 있다보니 다른 기능에는 눈이 가지 않네요. 😂

이 글이 컨플루언스 업데이트 시 작은 도움이 되었으면 좋겠네요. 감사합니다.
다음 포스트에는 "아틀라시안 앞으로 클라우드로 서비스한다?!"는 내용을 가져와보겠습니다.
