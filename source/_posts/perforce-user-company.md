---
title: 'Perforce를 사용하는 회사, 사용자는 얼마나 될까?'
toc: true
date: 2021-12-28 22:04:50
categories:
- Life
- Think
tags:
- PM
- Think
- Perforce
---

## 시작하며: 회사에서 Perforce Helix core를 사용하면서 드는 생각들

21년에 퍼포스 기능에 대한 포스트를 한 10개 안되게 만들어보면서 회사 내에도 그렇고 외부에도 그렇고 참 자료가 없다는 것을 느낍니다.
다들 퍼포스를 알게 모르게 쓰고 있는 것일까? 아니면 내부 자료로만 정리되고 있는걸까 하기도 하구요.

이참에 퍼포스를 사용하는 곳과 검색 트렌드를 좀 확인해보고 자료가 없다면 정리해서 조금씩 만들어보고자 합니다.
(이 글에서 말하는 퍼포스는 버전 관리 프로그램인 Perforce Helix Core를 의미합니다.)

## 퍼포스 사용하는 회사들

저는 주로 퍼포스는 게임 개발 회사에서 사용한다고 알고 있었습니다. 에픽에서 사용하는 것으로 알고있긴해요.
(엔진 코드가 github에는 올라가 있지만 Perforce를 사용하고 있다고 들었습니다.)

퍼포스를 사용하고 있는 회사는 여기서 확인할 수 있었습니다.
<https://www.perforce.com/customers>

![Perforce customers](https://user-images.githubusercontent.com/5077086/147757884-e936aaa4-782e-4562-befb-fc557f9cd7cd.png)

Industry를 보니 당연히 게임 개발이 있고 다른 카테고리로는 이커머스, 자동차 회사, 우주항공 쪽도 있습니다.
(NASA, 포르쉐도 있네요. 😈)
각 회사에서 사용하는 프로그램은 조금씩 다르긴합니다. 각 회사에서 사용하는 프로그램을 보면,
Helix Core / Hansoft / Helix QAC 요렇게 나눠서 보여주고 있습니다.

- Helix Core: 버전 관리 프로그램 <https://www.perforce.com/products/helix-core>
- Hansoft: 애자일 툴 <https://www.perforce.com/products/hansoft>
- Helix QAC: C, C++ 정적 코드 분석 프로그램 <https://www.perforce.com/products/helix-qac>

각 프로그램에 대한 자세한 내용은 따로 다루지 않고 넘어가겠습니다.
저는 Helix Core를 어디서 얼마나 어떻게 쓰고 있는지가 궁금해서요. 😸

### 유비소프트(Ubisoft)

Featured Customer로 되어있는 유비소프트 케이스 스터디를 좀 보겠습니다.
<https://www.perforce.com/case-studies/vcs/ubisoft>

- 2000명 이상의 개발자가 소스코드와 작업 애셋들(그래픽, 애니메이션 등)을 저장하고 있음
- API 용이성, 유연성 / 이상적인 브랜치 방식 / 프록시 서버 효율성
- 개발 환경
  - 개발자: 2000명
  - 파일 수: 5TB(24,070,195개 파일)
  - 변경 수: 166,642,479 리비전 (337GB 메타데이터)
- 아티스트와 모델러는 P4V와 P4GT 그래픽 도구용 플러그인을 이용하여 작업하기도 했음
- P4Report를 사용해서 애셋과 코드에 대한 리포트 생성을 단순화했음
  - 따로 확인해보니 p4 report 명령어는 없고 p4 files, p4 changes 등의 명령어로 정보를 관리한 것으로 보입니다
- 개발 속도를 높이기 위해 자주 사용하는 파일 캐시를 제공하고자 Perforce Proxy(P4P) 활용
- 많은 사내 도구가 개발되면서 소스 제어와 상호작용할 수 있는 유연한 API가 필요했음
- API가 유연해서 유비소프트 내부 도구와 통합할 수 있어서 생산성이 향상되었음

여기도 오래동안 게임을 개발한 곳이어서 개발자 수, 파일 수가 어마어마하네요.
퍼포스를 사용한 이유는 브랜치 방식도 방식인데 내부 개발 도구와 API 연동도 몫을 했나봅니다.
내부 생산성을 위해 툴 개발 및 시스템 구축했다는 것이 인상깊었습니다.

### CD Projekt Red

다른 게임사인 CD Projekt Red 포스트도 한번 보겠습니다.
<https://www.perforce.com/case-studies/vcs/cd-projekt-red>

위쳐 개발하면서 사용했던 이야기를 써두었네요. (사이버펑크 개발할때도 썼겠죠 😸)

- 개발환경
  - 개발자: 450명 이상
  - 데이터베이스 크기: 205GB
  - 저장소 크기: 10TB
  - 파일 수: 1500만개
- 매일 최대 50-60GB 대용량 데이터 작업 진행
  - 큰 파일을 작업하고 동기화하는데에 적합하다고 보고 있음
- 빌드 자동화: Helix Core와 빌드 시스템을 통합하여 변경 사항을 모니터링하고 테스트, 컴파일함
  - 수정된 내역이 포함된 빌드가 완료되면 버그를 자동으로 닫음

앞서 보았던 유비소프트보다는 개발자 수가 적지만 저장소 크기와 파일 수는 꽤나 큽니다.
파일수에 비해 저장소 크기가 큰 것을 보니 글에 있는 내용대로 파일이 큰 작업들을 다 저장소에 올리는 것으로 보입니다.
작업물에 대한 공유를 모두 퍼포스를 통해서 하는 것 같네요.
(다른 클라우드 서비스보다 퍼포스를 사용하는게 아닐까 싶기도하구요.)

### 그외의 회사들

Helix Core 외에 다른 게임 회사들은 어떤 것을 쓰고 있나 보았습니다.

- EA, Capcom은 Hansoft를 이용해서 작업을 관리하고 있는 것 같습니다
- Epic Games는 Helix Core를 사용하고 있긴하지만 따로 포스트를 올리지는 않았네요
- 영상으로 사례를 올린 곳은 영상의 길이가 짧아서 딱히 알 수 있는 것이 별로 없었습니다

## 구글 검색 트렌드

퍼포스에서 소개한 회사의 이야기는 들어보았으니 구글에서 사용자들이 얼마나 검색하는지를 알아보겠습니다.
Perforce, SVN, Git으로 확인해보니..

<script type="text/javascript" src="https://ssl.gstatic.com/trends_nrtr/2790_RC04/embed_loader.js"></script> <script type="text/javascript"> trends.embed.renderExploreWidget("TIMESERIES", {"comparisonItem":[{"keyword":"perforce","geo":"","time":"today 12-m"},{"keyword":"SVN","geo":"","time":"today 12-m"},{"keyword":"git","geo":"","time":"today 12-m"}],"category":0,"property":""}, {"exploreQuery":"q=perforce,SVN,git&date=today 12-m,today 12-m,today 12-m","guestPath":"https://trends.google.com:443/trends/embed/"}); </script>

<script type="text/javascript"> trends.embed.renderExploreWidget("RELATED_QUERIES_0", {"comparisonItem":[{"keyword":"perforce","geo":"","time":"today 12-m"},{"keyword":"SVN","geo":"","time":"today 12-m"},{"keyword":"git","geo":"","time":"today 12-m"}],"category":0,"property":""}, {"exploreQuery":"q=perforce,SVN,git&date=today 12-m,today 12-m,today 12-m","guestPath":"https://trends.google.com:443/trends/embed/"}); </script>


Git이 압도적이어서 Perforce가 아예 바닥에 있어서 보이지를 않네요. Perforce만 두고 기간을 늘려서 보겠습니다.


<script type="text/javascript"> trends.embed.renderExploreWidget("TIMESERIES", {"comparisonItem":[{"keyword":"perforce","geo":"","time":"2004-01-01 2021-12-28"}],"category":0,"property":""}, {"exploreQuery":"date=all&q=perforce","guestPath":"https://trends.google.com:443/trends/embed/"}); </script>

2000년 초반까지만해도 꽤 많은 검색량이 있었는데 2010년들어서는 많이 떨어졌네요.
나라별로는 세인트헬레나, 대한민국, 이스라엘, 중국, 캐나다, 미국 순으로 많이 검색했네요.

검색량만 봤을때, 지금은 대부분의 회사에서는 소스관리 프로그램 Git을 주로 쓰는 것 같고
Perforce는 게임 개발 회사에서는 몇몇 큰 회사에서 쓰고 있는 것 같습니다.

## 생각 마무리

어디 퍼포스 쓰는 회사 얼마나 되는지 살짝 맛을 보았습니다. 아무래도 게임 개발에 있어서 큰 애셋 파일들의 동기화가 시간이 걸리는데 그것에 대한 강점이 있고 작업물의 통합에도 편리함이 있으니 사용하는 것 같습니다.
슬쩍 확인해보니 국내 게임 회사들도 꽤나 쓰고 있는 것 같네요. (N사, S사, P사 등)
<https://www.perforce.com/support/self-service-resources/documentation> 퍼포스 가이드 문서도 이것저것 있는데 아무래도 영어이기도하고 활용하기 어렵게 작성되어있기도해서 조금씩 공부하면서 포스트 해볼 것 같습니다.
가이드 문서가 부족해도 회사에서 쓰고 있는 시스템이니 생산성을 올릴 수 있는 방법도 고민해야하고 가이드 문서들도 좀 챙겨보고 그래야겠죠. ㅎㅎ
이만 생각 포스트 마치겠습니다.
