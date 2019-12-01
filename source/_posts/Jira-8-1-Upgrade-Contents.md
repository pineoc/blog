---
title: Jira Software 8.1 릴리스 노트
date: 2019-09-02 00:05:55
categories:
- PM
- System
tags:
- Jira
toc: true
thumbnail: https://wac-cdn.atlassian.com/dam/jcr:fa01756d-6dcc-45d1-83ab-696fbfeb074f/Jira-icon-blue.svg?cdnVersion=696
---

## Jira Software 8.1 릴리스 노트

Jira Software 8.1.x 릴리스 노트: <https://confluence.atlassian.com/jirasoftware/jira-software-8-1-x-release-notes-966669112.html>

지난 4월에 릴리스된 Jira Software 8.1 기능에 대해 살펴보는 포스트입니다.
위 릴리스 노트에서 자세한 내용을 보실 수 있으며, 이 포스트는 주관적인 생각을 담고 있습니다.

### 하이라이트

하이라이트 기능으로는 아래 리스트와 같습니다. 하나하나 살펴보겠습니다!

- Issue archiving (Jira Data Center)
- Managing old components
- Development info on issue cards
- Flexible boards
- More performance improvements
- Jira Data Center on Microsoft Azure
- New JMX metrics
- Small improvements to make your day
- Resolved issues

### Issue archiving (Jira Data Center)

![Issue archiving](https://confluence.atlassian.com/jirasoftware/files/966669112/968658741/1/1553854467925/issuearchiving.png)

위 이미지 처럼 이슈를 아카이브 할 수 있는 기능입니다. 다만 Data center만 가능한 기능입니다.
자세한 내용은 아래 링크를 참고하세요.
<https://confluence.atlassian.com/adminjiraserver/archiving-an-issue-968669980.html>

### Managing old components

![Managing old components](https://confluence.atlassian.com/jirasoftware/files/966669112/967343327/1/1552057157649/image-20190213-122213.png)

기존에는 컴포넌트를 삭제하는 방식으로 컴포넌트를 관리할 수 있었는데 한가지 추가 옵션이 생겼습니다.
아카이브하여 해당 컴포넌트는 아카이브되었다는 것을 보여줄 수 있게 되었네요.
입력된 컴포넌트가 아카이브될 경우, 선택 옵션에서는 선택할 수 없으나 이미 입력된 것은 유지됩니다.

![](https://user-images.githubusercontent.com/5077086/64077887-a81a2500-cd0f-11e9-9f2f-45e920523a4a.png)

### Development info on issue cards

![](https://confluence.atlassian.com/jirasoftware/files/966669112/966669129/2/1553854539622/devinfo.png)

이제 칸반, 스프린트 보드에서 이슈 카드에서 커밋되었거나 브랜치가 생성된 내역을 볼 수 있습니다.
이 기능은 커밋 내역을 트래킹하여 보여주는 서비스가 연결되어 있을 경우 볼 수 있겠군요.
(예: Fisheye, Crucible, Bitbucket)

이미지 상으로는 커밋 내역과 브랜치, 리뷰가 완료되었는지 진행 중인지 알 수 있겠네요.
배포 관련 내용은 bitbucket과 관련 내용인지 봐야할 것 같기는 합니다.
(정확한 것은 모르겠지만 아틀라시안 제품과 연동이 잘 되어 있을 것으로 예상합니다)

### Flexible boards

![](https://confluence.atlassian.com/jirasoftware/files/966669112/967894226/1/1553509436159/issue_resize.gif)

보드에서 오른쪽에 이슈 카드의 디테일 내용을 볼 때 가로의 크기가 정해져 있어 보기 힘들었던 것을
옆으로 늘려서 볼 수 있도록 개선한 내용입니다. (QoL 내용 같네요. ㅎㅎ)

### More performance improvements

항상 열심히 성능 개선에 힘쓰고 있는 아틀라시안!
이번에도 성능 개선 소식이 있네요.

#### 보드 피커 개선

보드 페이지를 열 때 마다 모든 보드 리스트를 가져왔는데 그렇게 하지 않도록 개선했다고 합니다.
보드를 고를 때는 차이가 나지 않지만, 다른 페이지에서는 성능 상 효과가 있을 것이라고 하네요. :)

#### 이슈 카드 색깔 설정 속도 개선

보드에서 JQL에 따라 카드에 색깔을 넣을 수 있는 기능을 개선했다는 내용입니다.
내부 로직을 개선한 내용으로 색깔을 입히는데에 더 효율적으로 계산한다고 하네요.

### Jira Data Center on Microsoft Azure

Jira Data Center 버전-MS Azure 배포 템플릿을 개선했다고 합니다.
(사실 데이터 센터 버전을 사용하지 않아서 잘 모르겠지만 8.1 버전 외에 다 적용되는 사항이라고 합니다.)

### New JMX metrics

Jira 성능을 보기 위해서 JMX라는 매트릭스를 도입했다고 합니다.
자세한 것은 이 링크([Live monitoring using the JMX interface](https://confluence.atlassian.com/adminjiraserver/live-monitoring-using-the-jmx-interface-939707304.html))에 있네요.
다만 이 기능은 모니티링도 성능에 영향을 줄 수 있으니 1초에 한번정도만 새로고침하라고 경고하네요. :)
기능을 켜면 Administration > System > System info 밑에 `Instrumentation`이라는 메뉴가 나타납니다.

![Instrumentation: 많은 성능 관련 내용을 볼 수 있습니다.](https://user-images.githubusercontent.com/5077086/64078257-40fe6f80-cd13-11e9-9bb3-b5bc36e45439.png)

### Small improvements to make your day

작은 개선 사항이지만 우리에게는 꿀맛같은 개선사항입니다.
(이번에는 그렇게 많지는 않군요.)

#### Sorting projects by columns

![](https://confluence.atlassian.com/jirasoftware/files/966669112/968661924/1/1554109939974/sortprojects.png)

이미지 처럼 각 컬럼 별로 여러 프로젝트를 소팅해서 볼 수 있습니다.
프로젝트가 많지 않으면 와닿지 않겠지만 프로젝트가 많을 경우에는 좋을 것 같네요!

#### Additional custom fields in batched email notifications

특정 커스텀 필드를 이메일 알림에 포함하는 것을 조정할 수 있는 기능이 추가되었다고 합니다.
기능은 심플한데 설정하기에는 까다로운 것 같네요. [참고 링크](https://confluence.atlassian.com/adminjiraserver/adding-custom-fields-to-emails-batched-notifications-968669988.html)
나중에 한번 해보고 정리해서 따로 포스트 작성해보겠습니다.

그 외에는 계정 로그인, 로그아웃 시간을 볼 수 있는 기능과 아바타 이미지가 추가된 것이 있네요.
버그 수정 사항은 따로 다루지 않겠습니다.

## 마무리

8.0에도 변경사항이 많았는데 8.1도 변경 사항이 많았네요.
글을 작성하면서 QoL이 되었으면 하는 것 중 `프로젝트 별 이슈 필드 리스트 개선`이 언젠가는 생기겠지하는 생각을 했네요.
잡생각을 마무리하며, 포스트 마치겠습니다.
