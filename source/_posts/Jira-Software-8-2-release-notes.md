---
title: Jira Software 8.2 릴리스 노트
toc: true
date: 2019-10-06 14:54:49
categories:
- PM
- System
tags:
- Jira
thumbnail: https://wac-cdn.atlassian.com/dam/jcr:fa01756d-6dcc-45d1-83ab-696fbfeb074f/Jira-icon-blue.svg?cdnVersion=696
---

## Jira Software 8.2 릴리스 노트

Jira Software 8.2.x 릴리스 노트: <https://confluence.atlassian.com/jirasoftware/jira-software-8-2-x-release-notes-968676271.html>

2019년 5월에 릴리스된 Jira Software 8.2 기능에 대해 살펴보는 포스트입니다.
위 릴리스 노트에서 자세한 내용을 보실 수 있으며, 이 포스트는 주관적인 생각을 담고 있습니다.

### 하이라이트 (Highlights)

- **Filters on the Export archived issues page**
- **Color updates for issue statuses**
- Support for Java 11
- Support for Microsoft SQL Server 2017
- Updating apps has never been easier
- **Exporting all the issues you need**

하이라이트 내용에서는 Jira 서비스를 사용하는 사람 입장에서 주요한 기능들만 강조해보았습니다.
(그 외의 내용은 시스템 관리자가 봐야할 내용이라서 건너뛰겠습니다. :))

### Filters to limit the number of archived issues you export

데이터 센터 버전에서 사용할 수 있는 기능입니다.
익스포트하려는 아카이브된 이슈의 수를 제한할 수 있는 기능입니다.
(저는 서버 설치 버전을 사용하고 있어 해당 기능이 정확히 어떤 기능을 하는지 모르겠습니다.)
자세한 내용은 [아카이빙 이슈](https://confluence.atlassian.com/adminjiraserver/archiving-an-issue-968669980.html)에서 참고해주세요.

### Color updates for issue statuses

간단하게 설명하면 이슈들의 상태 카테고리 색깔이 변경되었습니다.
서버 버전과 클라우드 버전의 일관성을 맞추기 위해서 바꾸었다고 하네요.
![전, 후](https://confluence.atlassian.com/jirasoftware/files/968676271/974366138/1/1562355537865/new+statuses+for+documentation.png)

노란색은 사라지고 파란색이 더 강조된 느낌입니다.

### Exporting all the issues you need

기존에는 1000개까지 밖에 안되었던 이슈 익스포트가 최적화를 통해 더 많은 양을 익스포트할 수 있게되었습니다.
다만 이 제한 설정은 시스템 관리자가 설정할 수 있습니다.
System > Advanced Settings > `jira.search.views.max.limit`

![](https://user-images.githubusercontent.com/5077086/66265123-d9749c00-e84b-11e9-8083-24cfe7475e12.png)

## 마무리

8.2 릴리스는 변경사항이 그렇게 많지 않네요.
그 외에 버그 수정사항도 약간 있으니 자세한 내용인 실제 릴리스 노트 링크를 참고해보세요!
