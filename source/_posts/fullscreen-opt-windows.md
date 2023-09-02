---
title: "Windows에서 전체화면(Fullscreen) 최적화의 이해 on Microsoft Blog"
toc: true
date: 2023-09-02 18:30:17
categories:
- Life
- Study
tags:
- Study
- Windows
---

## 원본

[DirectX Dev Blog: Demystifying Fullscreen Optimizations](https://devblogs.microsoft.com/directx/demystifying-full-screen-optimizations/)

## 요약: 전체화면 모드(FullScreen Mode) vs 창 모드(Windowed Mode)

- Windows 10 출시와 함께 전체화면 전용 게임을 전체 화면을 차지하는 고도로 최적화된 `전체 창 모드(Borderless) 형식`으로 실행하는 `전체화면 최적화`가 추가되었음
- 이 최적화로 전체 창 모드로 프로그램(게임)을 실행해도 시각 경험과 성능이 전체화면 모드와 거의 동일하게 개선되었음
- 다만 전체화면 모드와 창 모드의 이점을 갖는 대신 진짜 전체화면 모드와 비교했을 때 성능 부하가 있기에 완전히 성능이 동일하다고 볼 수는 없음
  - (참고) 전체화면 모드 + 다른 프로그램의 오버레이 케이스에서는 전체화면 모드에서도 성능 저하가 있을 수 있음
- 전체화면 최적화 기능을 끄고 싶다면 (전체화면, Fullscreen Exclusive) 아래처럼 설정
  - 프로그램 파일(.exe 파일) 오른쪽 클릭 > 속성(Properties) 선택
  - 호환성(Compatibility) 탭 선택
  - 전체 화면 최적화 사용 중지 선택 > 적용

## 마무리

원본 글을 보시면 알 수 있지만 저희가 게임에서 전체화면 모드라고 생각했지만 실제로 OS단에서 전체 창 모드로 보여주고 있을 가능성이 있네요.
실제 게임에서 전체화면 모드를 지원하더라도 OS에서 최적화를 통해 창모드로 실행되고 있을 수 있겠습니다. 😂
최근 게임 성능 테스트하면서 전체화면 모드 vs 전체 창 모드를 테스트해보았었는데 FPS가 비슷했어서 의아했는데 이제 알게되었습니다.
이 최적화는 Windows 10 특정 업데이트부터 적용된 것 같긴하네요. (2019년 글이니 그 전에 반영되었다고 볼 수 있겠습니다.)

