---
title: Jira Cloud Next Gen project (차세대 프로젝트) 둘러보기
toc: true
date: 2020-06-30 22:55:41
categories:
- PM
- System
tags:
- Jira
- Jira Cloud
thumbnail: https://user-images.githubusercontent.com/5077086/86138645-b13f7280-bb29-11ea-9eae-8d41336ecff4.png
---

## Jira 클라우드(Cloud)

지난 포스트에서는 Jira 클라우드를 무료로 사용해볼 수 있는 방법을 소개해드렸었습니다.
참고: **{% post_link Jira-Cloud-Free-Plan %}**
이어서 제가 개인 공부 겸, 사용해보고 있는 "차세대 프로젝트(Next Gen)"를 한번 둘러보고 소개드리고자 합니다.

## Jira Next Gen?

현재 Jira에서 개발 진행중인 프로젝트 유형으로 기존 템플릿보다 심플한 유형입니다.
이름도 차세대 프로젝트로 기존의 프로젝트 형태와는 다른 모습인데 자세한 내용은 둘러보면서 설명하겠습니다.
(기본적인 기능들은 동일하지만, 다른 느낌정도로 이해해주시면 될 것 같습니다.)

## 차세대 프로젝트 둘러보기

![프로젝트 생성 - 클래식 vs 차세대](https://user-images.githubusercontent.com/5077086/86138660-b43a6300-bb29-11ea-8d0f-c132d62423ed.png)

Jira 프로젝트를 생성할 때 어떤 프로젝트 유형을 사용할지 고를 수 있습니다.
클래식 프로젝트는 기존에 사용하던 유형이구요. **차세대 프로젝트**가 우리가 살펴볼 프로젝트 유형입니다.

### 클래식 프로젝트 / 차세대 프로젝트 차이

프로젝트 생성할 때 설명되어 있는 것을 정리해보았습니다.
Classic, Next Gen 기능 상 차이점이 각 프로젝트 별 성격을 잘 보여주는 것 같네요.

| Type      | Classic              | Next Gen                   |
|-----------|----------------------|---------------------------|
| Team      | 여러 팀 간의 일관성 제어  | 민첩하고 독립적인 팀에 가장 적합함 |
| Customize | 전체 기능 집합, 고급 구성 | 제한된 기능 집합, 더 쉬운 설정    |
| Admin     | 관리자가 설정 및 유지관리  | 누구든지 설정 및 유지 관리 가능   |
| 로드맵      | x                   | o                          |
| advanced 로드맵 | o | x   |
| 카드 레이아웃 사용자 지정</br>(카드 레이아웃 커스텀) | o          | x      |
| 보고서(report) | 20개 이상의 종류 | 4개 종류 |
| 예상치 | o | o (스토리 포인트만) |
| 워크플로우 편집기 | o | x |
| 병렬 스프린트 | o | x |
| 세부 권한 | o | x |
| 교차 프로젝트 설정 | o | x |
| 빠른 필터(Quick Filter) | o | x |

위 테이블 내용 중 차세대 프로젝트 기능은 현재 기준으로 기능이 정리되어있으며 아직 개발중인 것들이 많습니다.
자세한 내용은 아래 링크에서 보실 수 있습니다.
<https://www.atlassian.com/ko/software/jira/whats-new/next-gen#overview>

> 한 가지 다행인 것은, 워크플로우(Workflow) 편집기가 사라진 것은 아니며 아직 개발중인 상태로 2020년에 제공될 예정이라고 하네요.

프로젝트 유형 별로 기능에 대한 기본적인 소개 내용은 Jira 가이드 문서에도 잘 정리가 되어있었습니다.
[Jira Software 시작하기 가이드 문서](https://www.atlassian.com/ko/software/jira/guides/getting-started/basics)

기본적인 기능, 차이점들을 보았으니 실제 모습을 한번 둘러보겠습니다.

### 프로젝트 보드

![차세대 프로젝트 - 칸반 보드](https://user-images.githubusercontent.com/5077086/86142896-b3f09680-bb2e-11ea-98bf-3ac3ca04cf54.png)

저는 우선 개인 작업을 관리하기 위해서 만든 것이어서 스크럼(Scrum)까지는 필요하지 않아 칸반(Kanban) 타입으로 보드를 만들었습니다.
기본적인 컬럼 레이아웃, 기능은 클래식 유형과 거의 동일합니다. 다만 차이점에서 살펴보았듯이 몇가지 기능들이 없거나 간소화되었습니다.
**차세대 프로젝트**에서의 기능을 기준으로 살펴보면 다음과 같습니다.

- 이슈의 그룹화 기준, 곧 **스윔레인(swimlane)**은 담당자, 에픽, 하위작업 정도로 나눌 수 있습니다.
  - Classic에 있던 jql에 따라 스윔레인을 나누는 기능은 없습니다. 😂
- 보드 상단에 있던 빠른 필터(퀵 필터)가 없어서 보드 안에서 특정 조건의 이슈들을 골라서 보기 어렵습니다.
  - 보드에서 제목으로 이슈를 검색할 수 있습니다. jql은 안되는 것 같네요.
- 보드 컬럼을 바로바로 만들 수 있습니다.
  - 각 컬럼의 이름이 곧 상태 이름이 됩니다. workflow가 아직 없어서 이슈의 상태 변환이 굉장히 자유롭습니다.
  - 맨 오른쪽에 있는 컬럼이 완료 컬럼입니다. 이슈가 맨 오른쪽 컬럼으로 움직였다면 그 이슈는 완료된 상태가 되며 보고서에서도 완료된 이슈로 계산될 것 입니다.
- 보드에 있는 이슈 카드 레이아웃을 설정할 수 없습니다.
  - 제목, 우선순위(priority), 스토리 포인트 정도를 볼 수 있네요.

차세대 프로젝트 보드는 기존보다 기능이 간소화되었다는 느낌을 받았습니다. 이렇게 보니 민첩하고 독립적인 팀에 적합하다고 한 것 같네요. 😀

### 프로젝트 기능 설정

![프로젝트 기능 설정](https://user-images.githubusercontent.com/5077086/86144957-50b43380-bb31-11ea-834e-bfcda52cb349.png)

프로젝트에서 사용할 수 있는 기능들을 On/Off 할 수 있도록 되어있는데 처음에는 대부분 꺼져있는 상태입니다.
프로젝트 기능 설정은 **프로젝트 설정 > 기능**에서 살펴볼 수 있으며 On/Off 할 수 있습니다.

저는 로드맵, 백로그, 보고서, 예측, 페이지, 릴리스 및 버전 관리, 이슈 이렇게 기능을 켜서 사용하고 있는데요.
간단히 각각 기능들을 짚어보겠습니다.

### 로드맵(Roadmap)

![이슈들을 한눈에 볼 수 있는 로드맵 from Atlassian](https://wac-cdn.atlassian.com/dam/jcr:f60a6df0-c521-45e6-ae03-16a868744d63/NG-roadmap-issues-big-picture.png?cdnVersion=1100)

![pineoc 개인 로드맵](https://user-images.githubusercontent.com/5077086/86257440-7eae7c00-bbf4-11ea-9fa6-3523ea0b0376.png)

로드맵은 에픽을 기준으로 하위에 있는 이슈들을 계층 구조로 볼 수 있는 기능입니다.
모든 작업이 에픽을 기준으로 묶이는 것으로 단순화하여 로드맵이 단순화 되었습니다.
> 피쳐 작업 또는 단위 기능 기준으로 에픽을 만들고 하위에 태스크 구성하면 한눈에 보기 좋을 것 같습니다.
> (물론 하위 태스크가 30개 이상이 되어버리면 보기 어려운 것은 기존과 마찬가지겠지만요. 😂)

![작업자 또는 상태 기준으로 필터링](https://wac-cdn.atlassian.com/dam/jcr:88ea37d3-b61b-469e-a867-095d39dd7df8/NG-roadmap-filters.png?cdnVersion=1100)

![로드맵 내보내기 - 이미지 내보내기](https://user-images.githubusercontent.com/5077086/86258430-c97cc380-bbf5-11ea-8a05-244b387eb029.png)

필터링, 내보내기 기능 등 로드맵 쪽에 기능이 몇 가지 있네요.
> 이미지 내보내기 기능이 쓸모가 크게 있을 것 같지는 않지만, 이미지 공유로 가능하다는 점에서 좋은 것 같네요.

### 백로그(Backlog)

![pineoc 프로젝트 백로그](https://user-images.githubusercontent.com/5077086/86259465-02696800-bbf7-11ea-8a3a-4296199a1dbb.png)

저는 개인 공부/작업의 백로그를 두고 관리하기 위해 사용하고 있습니다.
차세대 프로젝트 백로그는 에픽, 버전 별로 필터를 적용하여 볼 수 있습니다.
패널도 옆에 켜서 볼 수 있어서 에픽, 버전 별로 하위 작업의 프로그레션을 볼 수 있습니다.

백로그 중간에 있는 드래그 가능한 바(bar)는 보드 / 백로그 티켓을 바 기준으로 옮길 수 있도록 하는 기능을 합니다.

> 백로그는 사실 보드 보다는 많이 보지 않지만 필터 기능이 있어서 편하긴 한 것 같습니다. 👍

### 보고서(Report)

![보고서 종류](https://user-images.githubusercontent.com/5077086/86260394-2da08700-bbf8-11ea-99fa-56f93bd6c070.png)

기존 클래식 타입의 프로젝트에는 많은 보고서 타입이 있는데 차세대 프로젝트에는 4개 정도 밖에 없습니다.
그와중에 저는 칸반을 사용하고 스프린트를 사용하지 않아서 3개의 보고서는 보지 못하네요. 😂

![스프린트 번다운 차트 from Atlassian](https://wac-cdn.atlassian.com/dam/jcr:d45d24e3-35da-4671-950b-901d11493b4e/NG-burndown-report-2.png?cdnVersion=1100)
기능 소개 참고 커뮤니티 포스트: [We are reinventing the Sprint burndown for next-gen projects!](https://community.atlassian.com/t5/Next-gen-articles/We-are-reinventing-the-Sprint-burndown-for-next-gen-projects/ba-p/1192403)
스프린트 번다운 차트는 소개 문서에 있는 내용을 가져왔습니다.

- 스프린트 보고서와 번다운 차트를 차세대 제품에서는 단일 보고서로 통합했습니다.
- 스프린트 번다운 차트에는 스프린트에서 완료된 작업량과 남은 총 작업량이 표시됩니다.
- 또한 과도한 범위 증가를 파악하고 스프린트 회고 시 요약을 제공하는 데에도 유용합니다.

> 기존보다 세련되었다 정도 밖에 의견을 못남기겠네요.
> 프로젝트 리포트를 현업에서 잘 사용해보지 못해서 그런 것도 있습니다. 😅
> 현업에서도 잘 사용해보고 싶다는 생각을 하며 보고서 기능 소개를 마무리 합니다.
> (번다운 차트 외, 다른 리포트은 설명 링크 달아두겠습니다.)

- 번업 차트(Burnup Chart): [View and understand the burnup chart](https://support.atlassian.com/jira-software-cloud/docs/view-and-understand-the-burnup-chart/)
- 속도 차트(Velocity Chart): [View and understand the velocity chart](https://support.atlassian.com/jira-software-cloud/docs/view-and-understand-the-velocity-chart/)

> 위 2개 보고서는 따로 클래식, 차세대 나눠서 볼 필요는 없어서 클래식에 있는 내용을 공유드립니다.

### 예측(Estimation)

예측이라고 적어두니까 특별한 기능이 있는 것 처럼 보이지만 사실은 **스토리 포인트** 기능을 의미합니다.
클래식과 차세대에서 예측(estimation) 기능의 큰 차이는 없습니다.
클래식에서는 스토리 포인트 외에 다른 필드 값을 사용할 수 있다는 점 정도가 다릅니다.
(스토리 포인트, Original time estimate, 이슈 수, 커스텀 필드를 사용할 수 있습니다)

> 예측 설정으로 스토리 포인트를 통해 번다운 차트나 속도 차트를 볼 수 있습니다.

### 페이지(Page)

![](https://user-images.githubusercontent.com/5077086/86265863-524c2d00-bbff-11ea-929c-e42b09aacb3e.png)

이 기능은 사실 컨플루언스와 연동해서 사용할 수 있는 기능입니다.
Jira 프로젝트와 연결되어 관련 문서를 바로 볼 수 있다는 점은 좋은 것 같습니다.
(사실 그냥 컨플루언스 기능을 연결한 정도여서 따로 살펴볼 내용은 없네요.)

> 저는 Jira 무료 사용자인데 페이지 기능을 사용하려면 Confluence는 Jira와 다른 제품이라서 사용하려면 추가 구매해야합니다.
> 저는 테스트를 위해 30일 무료 테스트(free trial)를 해보고 있습니다.
> UI가 세련되서 좋긴한데 개인적으로는 차세대 프로젝트에 꼭 필요한 기능으로는 생각되지 않네요.
> 접근성을 높혔다는 점이 좋은 것 같습니다.

### 릴리스 및 버전 관리(Release and Version)

![](https://wac-cdn.atlassian.com/dam/jcr:ea56a241-8746-44cd-89ce-20c39a7570f1/NG-versions.png?cdnVersion=1102)

작업한 버그나 태스크들을 버전에 맞게 플래닝, 정리할 수 있는 버전 관리입니다.
버전별로 출시할 내용들을 릴리스 버전을 통해 관리하는 것이죠.
기존 클래식 버전과 다른 점은 각 릴리스 버전을 누르면 버전이 입력된 이슈들을 보여주는 릴리스 페이지가 보이는 것이 아닌 이슈 검색 화면으로 이동한다는 점입니다.

![클래식 프로젝트 - 릴리스](https://user-images.githubusercontent.com/5077086/86487455-1baa1a00-bd99-11ea-9c2d-69c9841d4f30.png)

![차세대 프로젝트 - 릴리스/이슈 검색 화면으로 이동한 모습](https://user-images.githubusercontent.com/5077086/86487613-8e1afa00-bd99-11ea-8bdd-91cee0029a59.png)

> 기존 사용방법과 달라서 잠시 혼란이 있었지만 굳이 버전 페이지가 따로 있어야하는지는 한번 더 생각해보게 되었네요.
> 사실 저는 클래식 버전의 릴리스 버전 화면이 마음에 듭니다. 😀

### 이슈(Issue)

![차세대 프로젝트 - 이슈 탐색기](https://wac-cdn.atlassian.com/dam/jcr:3e0dcd34-6686-46fd-be7b-3ed6a5a0465d/All%20issues%20in%20project-april.png?cdnVersion=1109)

<https://community.atlassian.com/t5/Next-gen-articles/Introducing-issue-navigator-in-next-gen-projects/ba-p/1339049>
"프로젝트 이슈 탐색기로 차세대 탐색 및 검색이 훨씬 더 간편해집니다. 텍스트 검색을 사용하거나 담당자, 보고자, 상태별로 필터링하여 프로젝트에서 이슈를 검색하세요. 다양한 기준으로 목록을 정렬하여 해당 목록에서 이슈를 바로 수정할 수 있습니다."

기존 클래식 프로젝트의 경우 "이슈" 메뉴를 누르면 바로 필터 메뉴로 넘어가서 검색할 수 있도록 되는데요.
차세대 프로젝트에서는 담당자, 보고자, 상태, 유형 별로 정렬해볼 수 있어서 좋은 것 같습니다.
하나하나 검색하는 것 보다 접근성이 좋아졌네요.

> 이슈 기능은 바로 필터링해서 볼 수 있는 기능이 생겨서 사용성은 좋아진 것 같습니다.
> 이슈의 수가 많아지면 빠르게 동작할 수 있을지 모르겠지만요. 올해 프로젝트 사용해보면서 더 정리해봐야겠네요.

## 차세대 프로젝트 정리

지금까지 차세대 프로젝트에 어떤 기능들이 있는지, 어떻게 달라졌는지 살펴보았는데요.
충분한 설명이 되었는지 모르겠습니다.
저도 프로젝트를 생성해서 테스트한지 한달 정도 되어서 더 사용해봐야 유용한 정보들을 소개드릴 수 있을 것 같네요.
향후 추가될 기능들도 기대가 되서 업데이트될 때마다 공유드리면 좋을 것 같네요.
긴 글 읽어주셔서 감사합니다. 🙇‍♂️
