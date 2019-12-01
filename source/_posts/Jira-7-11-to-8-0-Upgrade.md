---
title: Jira 7.11 to 8.0 Upgrade
date: 2019-07-13 11:15:50
categories:
- PM
- System
tags:
- Jira
toc: true
thumbnail: https://wac-cdn.atlassian.com/dam/jcr:fa01756d-6dcc-45d1-83ab-696fbfeb074f/Jira-icon-blue.svg?cdnVersion=696
---

## Jira 7.11 to 8.0 Upgrade Specs

Jira Software(서버 설치버전)을 사용하면서 7.11에서 8.0으로 버전 업그레이드될 때
정리해보았던 내용을 포스트해봅니다.

## 사전 참고 링크

- Jira 릴리즈 노트: [Jira Software release notes](https://confluence.atlassian.com/jirasoftware/jira-software-release-notes-776821069.html)
  - 각 버전별 릴리즈 노트를 볼 수 있으며 버전별 업그레이드 문서도 함께 있습니다
- Jira 버전별 업그레이드 매트릭스: [Upgrade matrix](https://confluence.atlassian.com/adminjiraserver/upgrade-matrix-966063322.html)
  - 각 업그레이드 버전 항목 별로 간단하게 내용이 정리되어있는 표가 있습니다

# 각 버전 별 변경 사항

사내에서 기존에 사용했던 Jira 버전은 7.11 버전이었는데 8.0으로 업그레이드했습니다
이 업그레이드에는 7.12, 7.13, 8.0 수정사항이 모두 반영되어서 변경 사항에 대해 정리해보았습니다
각 변경 내용은 릴리즈 노트에 기반하여 정리하였습니다

## 7.12 변경 내용

[jira-software-7-12-x-release-notes](https://confluence.atlassian.com/jirasoftware/jira-software-7-12-x-release-notes-953676636.html)

### New look and feel of the Custom fields page

![custom field](https://confluence.atlassian.com/jirasoftware/files/953676636/955184240/3/1534154413740/custom.png)
- 어드민 기능 수정 내용으로 `설정 > Fields > Custom fields` 간략하게 볼 수 있는 내용
- 커스텀 필드가 적용된 프로젝트, 스크린을 한가득 보던 화면을 최적화해서 어드민 QoL 기능

### Share edit rights for filters and dashboards

![filter editors](https://confluence.atlassian.com/jirasoftware/files/953676636/955176570/3/1533817120715/filters_relnotes.png)
- 필터 수정 권한을 추가로 설정할 수 있는 기능 추가
- 필터를 다른 사람도 수정할 수 있게 된 것이 매우매우 좋다!

### More search power

- Development 관련 검색 기능 추가 (Open PR, Merged PR, Failling builds, Passed builds 등등)
- 작업이 어떻게 진행되고 있는지 파악하기 좋을 것으로 보임

### Boost Jira performance

- 보드에 있는 이슈의 수를 보여주는 것이 느리게 만드는 데 그 숫자를 안보이게하면 빠르게 할 수 있음
- 컬럼에서 얼마나 머물러 있었는지 볼 수 있는 내용도 끌 수 있는데 끄면 성능을 개선할 수 있음
- 다만 이 기능을 사용할 경우 보드에서 이슈가 얼마나 있는지, 얼마나 그 상태에 머물러 있었는지 알 수 없어서 불편할 것으로 예상됨

### 그 외의 버그 수정 다수

## 7.13 변경 내용

[jira-software-7-13-x-release-notes](https://confluence.atlassian.com/jirasoftware/jira-software-7-13-x-release-notes-957981568.html)

- AdoptOpenJDK 8 comes to Jira
  - 내부 개발 플랫폼 내용이라 자세히 알 필요는 없음
- End of year Enterprise release roundup
  - 공식 릴리즈에 대한 이야기
- Enterprise releases, performance-wise
  - 성능 향상 - [performance-and-scale-testing-966063698.html](https://confluence.atlassian.com/adminjiraserver0713/performance-and-scale-testing-966063698.html)
  - 7.12와 비교했을때 눈에 띄는 성능 향상은 아니지만 7.6 버전에 비하면 성능 향상이 이뤄졌음
  - (하지만 기존에 사용하고 있던 버전도 낮은 버전은 아니어서 큰 성능 차이를 느끼지 못했습니다)

## 8.0 변경 내용

[jira-software-8-0-x-release-notes](https://confluence.atlassian.com/jirasoftware/jira-software-8-0-x-release-notes-957981626.html)

### Look and feel: Scrum and Kanban

![Look and feel: Scrum and Kanban](https://confluence.atlassian.com/jirasoftware/files/957981626/964981997/3/1550749827559/boards.png)
- 보드의 외형이 바뀌었음
- 카드 정보를 어떻게 설정하여 보여줄 수 있을지 봐야할 것

### Better email notifications

![Better email notifications](https://confluence.atlassian.com/jirasoftware/files/957981626/964981972/3/1550749827217/email.png)
- 이메일이 너무 많이 와서 압도되는 것을 줄여보고자 했음
- 예시로는 10분간의 알림 사항을 모아서 메일주는 것을 보여줌
- 설정 > System > Batching email notifications 에서 설정 가능
  - 상세 내용: [configuring-email-notifications](https://confluence.atlassian.com/adminjiraserver/configuring-email-notifications-938847633.html)
- 댓글의 수정 내용이 계속 오는 것이 아닌 정리되서 와서 좋았던 기능

### Significant backlogs load faster

![Significant backlogs load faster](https://confluence.atlassian.com/jirasoftware/files/957981626/960698183/3/1550749826625/Screen+Shot+2018-10-29+at+11.41.27.png)
- 백로그 로딩 시간이 줄어들었음
- 몇개를 샘플링해서 보여주고 추가적으로 로딩할 수 있도록 하여 로딩 속도 개선한 것으로 보임

### Dropping Linked pages count to boost performance

- 이슈에 링크되어있는 페이지의 숫자를 보여주지 않는 것으로 성능 향상

### New priority icons

- 새로운 priority 아이콘 추가 (리뉴얼 되었음)

### New options in advanced search

- Find authors (updatedBy)
  - [UpdatedBy() guide](https://confluence.atlassian.com/jirasoftwareserver/advanced-searching-functions-reference-939938746.html#Advancedsearching-functionsreference-approverupdatedBy())
  - 어떤 사용자가 업데이트했는지 알 수 있음. 추가로 특정 시간부터 또는 특정 시간 동안 수정했는지 알 수 있음.
- Find link types (issueLinkType)
  - [issueLinkType guide](https://confluence.atlassian.com/jirasoftwareserver/advanced-searching-fields-reference-939938743.html#Advancedsearching-fieldsreference-issuelinktypeIssuelinktype)
  - 링크된 타입에 따라 이슈를 검색해볼 수 있음

### Massive performance improvements

- 보드, 백로그가 보이는데 걸리는 시간이 62%, 87%까지 빨라졌음
- JQL 프로세싱 과정은 33% 빨라졌음
- 보드 브라우징은 16% 빨라졌음

### Faster indexing

- 리인덱싱 속도가 71% 빨라졌음
- 인덱스의 크기가 줄어들어 인덱싱에 부담을 덜었음
- 인덱싱 관련 최적화가 되었음
- (실제로도 각 프로젝트에서 인덱싱할 때에 다른 프로젝트에서 영향 받지 않고 빠르게 된 것을 확인했습니다)

### REST API for issue type schemes

- 이슈 타입 스킴(Scheme)을 REST API로 수정할 수 있게 되었습니다.
- [jira/docs/api/REST/8.1.0/#api/2/issuetypescheme](https://docs.atlassian.com/software/jira/docs/api/REST/8.1.0/#api/2/issuetypescheme)

### Misc(Bonus resources)

- Small improvements to make your day
  - 4 Byte characters 지원
  - add-ons → apps 이름 변경
  - Using sprints when your backlog isn't sorted by rank (백로그가 rank로 정렬되지 않아도 스프린트 사용 가능)
- 성능 및 스케일 테스트
  - [performance-and-scaling](https://confluence.atlassian.com/adminjiraserver/performance-and-scaling-965568705.html)
- 보안 관련 페이지
- JIRA Server mobile App 지원 (베타 앱으로 지원되고 있어서 베타로 깔아야 함)
  - Android: [https://play.google.com/apps/testing/com.atlassian.jira.server](https://play.google.com/apps/testing/com.atlassian.jira.server)
  - iOS: [https://testflight.apple.com/join/6JbjYbSY](https://testflight.apple.com/join/6JbjYbSY)
  - Pre-upgrade planning page 추가
    - 설정 > Applications > Plan your upgrade 기능으로 볼 수 있음
- 그 외의 버그 수정 다수

## 업그레이드 버전 별 정리 후기

PM 업무를 하면서 Jira를 어떻게하면 더 잘 사용할 수 있을지, 개발 프로세스에 어떻게 잘 녹여낼지
고민하다보니 Jira 시스템도 많이 보게되어 정리하게 되었네요.
8.0 업그레이드를 했으니 곧 8.1, 8.2 업그레이드 릴리즈 노트도 정리해서 포스트 해보겠습니다.
