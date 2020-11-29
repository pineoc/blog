---
title: 우리에게 1ms의 의미란 (FPS vs Frame time)
toc: true
date: 2020-11-03 00:31:15
categories:
- Tech
tags:
- General Engineering
thumbnail: https://user-images.githubusercontent.com/5077086/100539406-9bb9aa80-3279-11eb-8ee0-88e94e38085b.jpg
---

## Intro

이 글은 최적화 관점에서 FPS(Frame Per Second) 대신 Frame time(1ms)을 어떤 의미로 어떻게 볼 수 있는지에 대해 간단히 이야기해봅니다.

## FPS? Frame time?

**FPS**는 다들 많이 들어보았을 것 같습니다. 말 그대로 Frame Per Second, 프레임 당 초(시간)을 의미하며 Frame rate(프레임률)이라고도 말합니다.

위키 참고: [https://ko.wikipedia.org/wiki/프레임_레이트](https://ko.wikipedia.org/wiki/%ED%94%84%EB%A0%88%EC%9E%84_%EB%A0%88%EC%9D%B4%ED%8A%B8)

> 1초 동안 보여주는 화면(프레임)의 수

예를 들면, FPS 60 == 1초당 60 프레임을 그린다고 볼 수 있겠습니다.

**Frame time(프레임 시간)**은 FPS에 비해서 생소할 수 있지만 간단히 말하면 화면(프레임)이 그려지는데 걸리는 시간입니다. (한 프레임을 그리는데 사용할 수 있는 버퍼 시간으로도 볼 수 있습니다.)

<div style='position:relative; padding-bottom:calc(56.25% + 44px)'><iframe src='https://gfycat.com/ifr/SardonicSociableLeafbird' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>

FPS와 동일하게 예를 들면, frame time 16ms == 화면 1개 그리는데 16ms 소요된다고 볼 수 있습니다.
FPS와 Frame time을 엮어서 보면 아래와 같겠죠

|FPS|Frame time|Frame time(ms)|
|:-:|:-:|:-:|
|20|1/20|50ms|
|30|1/30|33.33ms|
|60|1/60|16.67ms|
|100|1/100|10ms|
|144|1/144|6.9ms|

이렇게 보니 FPS와 Frame time이 연관이 있는 것은 알았습니다. 최적화 관점에서 이 두 값을 어떤 의미로 볼 수 있을까요?

## 최적화 후 1ms 차이

게임을 개발하면서 FPS가 안정적일 수 있도록, 더 높은 FPS로 플레이할 수 있도록 최적화를 하는데요. 이 때 최적화 결과 Frame time이 1ms 줄었을 때 FPS 변화는 어떻게될까요?

FPS와 Frame time 관계를 보았을 때 60 FPS 기준으로 Frame time은 16.67ms 였는데요.

Frame time이 16.67ms → 15.57ms가 될 경우, 60 FPS → 63.8 FPS. 약 3.8 FPS 상승합니다.

더 높은 FPS에서는 어떨까요? 10ms → 9ms가 되면 100 FPS → 111.11 FPS. 약 11.11 FPS 상승합니다.

## 최적화 후에는 FPS를 보는 것 보다 Frame time을 보는게 더 명확하다

60 FPS 고정인 상태 또는 게임에서의 부하(stress), 여러가지 하드웨어 환경에 따라 측정 결과가 다를 수 있긴합니다.

다만 최적화 후 개선된 항목(function 또는 Operation)이 얼마나 게임 환경(성능)에 영향을 주었는지를 Frame time 변화를 통해서 조금 더 명확하게 볼 수 있습니다.

물론 FPS 보다는 바로 이해가 가지 않을 수는 있지만 다른 요소에 영향을 받지 않는 수치로 볼 수 있는 것이죠.

## Fin

일반인(?)의 시선으로 Frame time을 최적화 관점에서 정리를 해보았습니다.

항상 최적화 이후에 1ms, 0.5ms 개선했다는 내용이 큰 개선인가? 하는 의문이 있었고 그런 참에 계산해보고 정리해보면서 개선의 크기와 영향도를 알게되어서 즐거운 공부였네요.

틀린 내용이 있다면 편하게 댓글 남겨주세요. 
고맙습니다. :)

### 참고 영상

[https://www.youtube.com/watch?v=GpYyjb5mz48](https://www.youtube.com/watch?v=GpYyjb5mz48)
