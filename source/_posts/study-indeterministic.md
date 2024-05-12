---
title: "(Game Dev Study) Deterministic packaging"
date: 2024-05-12 15:00:35
categories:
  - Tech
  - Game
tags:
  - Packaging
toc: true
---

## 짧은 개발 공부 - 디터미니스틱 패키징, 디터미니스틱 쿠킹

언리얼 한정 이슈인지는 모르겠으나 빌드를 생성한 뒤에 패치할 때 변경된 내역에 따라 발생하는 업데이트/패치 사이즈와 연관된 내용입니다.

빌드 생성시 패키징할 때마다 애셋이 변경되지 않아도 패키지가 변경되는 경우가 있습니다.

이런 경우에 패키지가 In-deterministic(인디터미니스틱, 해석: 비결정론적)하다고 표현하고 Deterministic(해석: 결정론적)할 수 있도록 패키징 중에 어떤 일이 일어나는지 분석, 수정합니다.

**패키지가 Deterministic하다면 매 업데이트 마다 빌드의 변경 내역이 줄어들고 패치 사이즈가 줄어들겠죠.**

디터미니스틱(결정론적이라는 표현보다는 이렇게 표현하는게 더 좋은 것 같네요) 패키징이 안되는 이유, 인디터미니스틱하게 패키징이 되는 원인은 주로 어떤 것이 있을지 살짝 살펴보면..

**(주요 원인) 매 빌드, 패키징마다 애셋, 애셋과 연관된 데이터들이 변경된다**

- 레퍼런스가 변경되었으나 패키징 과정에서 경로 해석에 따라 변경
- 데이터테이블 데이터 중 파일 경로를 사용하는 경우, 입력된 파일 경로와 실제 파일 경로가 다르지만 대소문자 정도의 차이일 경우 해석에 따라 패키징 타임에 해석되어 패키징될 경우 변경

## 언리얼 커뮤니티 아티클

https://dev.epicgames.com/community/learning/knowledge-base/oDGP/unreal-engine-deterministic-builds-and-cooking

아티클에서는 Non deterministic이라는 표현을 쓰고 있는데 동일하게 패키지를 하면서 바뀌는 것의 설명이라 동일하다고 볼 수 있을 것 같네요.

에픽 게임즈가 해결해야하는 부분과 개발사가 해결해야하는 문제를 나눠서 볼 수 있는데 개발사 해결해야하는 내용 중심으로 보겠습니다.

One issue we have seen in the past is that some third party tools can cause deterministic cooking errors. One example was a code integration from a third party that added a globally unique identifier (GUID) to Primitive Components, but regenerated it each time. This caused level files to have deterministic cooking problems, and patch sizes to increase dramatically.

> 써드 파티 툴에 의해서 컴포넌트에 ID가 변경되는 케이스가 있었고 그에 따라 패키지가 변경되는 케이스가 있었다고 하네요. 
> 툴, 플러그인을 사용할 경우 주의해야하는 영역이겠네요.

다른 하나가 더 있는데 항목이 길어서 요약해보면..

프로젝트 측 로직으로 인해 비결정적 쿠킹 문제가 발생할 수 있습니다. 예를 들어, C++에서 직렬화된 변수에 결과가 저장되는 비결정적 행동을 가진 블루프린트 노드를 정의하고, 이를 블루프린트 구성 스크립트에서 호출하는 경우가 있습니다. 이러한 스크립트는 쿠킹 과정 중에 실행되므로, 주의를 기울이지 않으면 각 쿠킹마다 행동이 달라질 수 있고, 결과적으로 자산이 달라지며 패치 크기가 인위적으로 증가할 수 있습니다. 이를 피하기 위해, 구성 스크립트에서 호출할 필요가 없는 블루프린트 노드를 구성 스크립트에 배치하지 않도록 표시할 수 있습니다. C++에서 구성 스크립트 호출 가능 노드를 정의할 때는 신중하게 접근해야 합니다.

> 요약해도 긴 내용이네요. 스크립트에 랜덤한 로직이 있을 경우 패키징하는 과정에서 달라질 수 있으니 주의해야한다는 내용이겠습니다.
> (랜덤 seed를 사용하는 스크립트라거나 패키징 과정에서 변경될 수 있는 값을 참조하는 변수가 있거나..)

## 짧은 공부 정리

- 디터미니스틱한 패키지, 빌드를 만들고 싶다면 빌드 과정에서 랜덤 요소나 변경될 요소를 없애야 한다.
- 패키지 변경 사항은 패키지를 만들고 비교하고 변경된 패키지에서 어떤 부분에 변경이 있었는지 분석, 수정한다.
- 프로젝트 에셋에 대부분 문제 원인이 있겠지만 엔진이나 툴에도 원인이 있을 수 있다. (플러그인 GUID 변경 케이스)
