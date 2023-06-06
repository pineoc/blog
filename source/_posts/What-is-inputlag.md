---
title: 인풋랙(Input Lag)? 그게 뭔데?
toc: true
date: 2023-06-06 13:00:00
categories:
- Tech
- Game
tags:
- Game
- Study
---

## 인풋랙(Input lag)?

![참고 이미지: BenQ 인풋랙](https://image.benq.com/is/content/benqco/input-lag-gif?$ResponsivePreset$)

[https://en.wikipedia.org/wiki/Input_lag](https://en.wikipedia.org/wiki/Input_lag)

인풋랙은 말 그대로 인풋(마우스, 키보드 등) → 연산장치(컴퓨터) → 디스플레이(모니터)까지 사용자의 인풋에 따른 디스플레이까지의 지연을 의미합니다.
인풋랙이라고 부르긴하지만 시스템 지연 시간으로 볼 수 있어요.

이번 포스트에서는 게임에서 주로 느끼는 인풋랙에 대해서만 다뤄보겠습니다.
(주로 인풋랙에 민감하게 반응하는 영역이 게임이기 때문에)

> 중간에 인풋랙을 찾다가 디스플레이 랙(Display Lag)으로 잘못 빠졌었는데 Latency(지연 시간, 응답 속도) 측면에서 완전히 분리할 수는 없지만 인풋랙과는 다른 영역이었네요.
디스플레이 랙 = 디스플레이 장치(예: 모니터, TV)에서 입력 신호를 받아 처리하여 화면에 표시되는 시간
참고: [https://en.wikipedia.org/wiki/Display_lag](https://en.wikipedia.org/wiki/Display_lag)

## 인풋랙 깊게 살펴보기

![](https://www.nvidia.com/content/dam/en-zz/Solutions/geforce/news/reflex-low-latency-platform/nvidia-reflex-end-to-end-system-latency-terminology.png)

![](https://images.nvidia.com/content/images/article/system-latency-optimization-guide/nvidia-latency-optimization-guide-peripheral-latency.png)

엔비디아에서 좋은 글, 좋은 영상이 있어서 들고왔습니다.
(엔비디아 Reflex에 대한 소개가 있긴하지만요 😅)

- [https://www.youtube.com/watch?v=h69JR51pZbU](https://www.youtube.com/watch?v=h69JR51pZbU)
- [https://www.nvidia.com/en-us/geforce/guides/system-latency-optimization-guide/](https://www.nvidia.com/en-us/geforce/guides/system-latency-optimization-guide/)

게임에서 인풋랙은 많은 요소들이 영향을 준다고 볼 수 있습니다. 적당히 풀어서 정리해볼게요.

- 주변기기 지연 - 인풋 기기의 폴링 레이트(Polling Rate)에 맞춰 컴퓨터에서 신호 처리가 되는데 그 처리에서 지연 시간이 있습니다. (USB 신호 처리, CPU 처리 등)
- PC 지연 - 입력을 받고 PC에서 처리되는 동안 발생하는 지연
  - CPU - 게임 내에서 일어나는 애니메이션, 물리 엔진 연산 등에 사용되는 시간
  - Render Queue - CPU 연산 뒤 렌더링을 위해 렌더링 명령들을 Queue에 적재하고 대기하는 시간
  - GPU - Render Queue에 있는 명령들을 렌더링하는 시간
- 디스플레이 지연 - PC로 부터 받은 신호들을 보이도록 처리하는 시간

우리가 게임에서 말하는 인풋랙은 이렇게 크게 3가지 지연 시간을 합해서 계산해볼 수 있습니다.
물론 네트워크를 이용한 멀티플레이 게임의 경우, 네트워크 레이턴시도 포함해서 봐야하지만 그건 PC 지연에 포함한다고 가정하고 넘어가겠습니다

## 게임과 인풋랙

주로 인풋랙에 영향을 많이 받는 게임은 FPS(Shooter), 격투 게임, 리듬 게임이 작은 지연에도 큰 영향을 받는 게임 장르로 볼 수 있습니다.

- FPS, Shooter: 인풋랙에 따라 상대방을 조준, 사격하는데에 있어서 인풋랙의 영향을 받습니다.
  - 추가로 네트워크 레이턴시도 추가되어 흔히 이야기하는 핑(ping) 차이가 발생하기도 합니다
  - 핑이 높으면 피커스 어드벤티지(Peeker’s advantage) 현상이 더 크게 발생할 수 있습니다
    - 피커스 어드벤티지: 네트워크 지연, 차이 등에 따른 공격자가 상대를 먼저 인지할 수 있는 이득을 보는 것
    - (참고) [피커스 어드벤티지, 발로란트 포스트](https://playvalorant.com/ko-kr/news/game-updates/04-on-peeker-s-advantage-ranked/)
- 격투 게임: 인풋랙에 따라 콤보를 넣을 수 있느냐, 상대의 공격을 인식해서 방어, 회피할 수 있냐가 달라지기에 크게 영향을 받는다고 볼 수 있습니다.
  - 한 사례로 콘솔 기기와 PC 설정 환경 차이로 인해 인풋렉의 차이가 발생해서 PC로 대회를 열 수 밖에 없었다는 사례도 있었네요. (스트리트파이터5 [참고 사례](https://www.fmkorea.com/4082074751), [참고 사례 링크2](https://gigglehd.com/gg/game/13668209))
- 리듬 게임: 인풋랙에 따라 노트를 정확하게 맞출 수 있냐 없냐가 달라지니 크게 영향을 받는다고 볼 수 있습니다.
  - 게임이 얼마나 세세하게 판정하냐에 따라 영향도는 달라질 수는 있지만 게임 자체 이슈, 모니터, 컨트롤러의 지연 요소에 따라 인풋랙이 크게 발생할 수 있습니다

## 인풋랙 측정 방법

![](https://www.nvidia.com/content/dam/en-zz/Solutions/geforce/news/nvidia-reviewer-toolkit/nvidia-reviewer-toolkit-ldat-testing-photo.jpg)

퀘이사존: 모니터 인풋랙은 무엇이고, 어떻게 측정할까? [https://quasarzone.com/bbs/qn_report/views/113059](https://quasarzone.com/bbs/qn_report/views/113059)

상세한 내용은 퀘이사존에서 자세히 설명해주고 있어서 위 글을 참고해보시면 좋을 것 같습니다.

요약해보면 마우스 입력 → 화면 반응까지 시간을 [LDAT(Latency Display Analysis Tool)](https://developer.nvidia.com/nvidia-latency-display-analysis-tool)이라는 장치를 이용해서 측정합니다.
LDAT이 없을때는 화면 반응을 카메라를 이용해서 촬영, 측정했다고 하네요. 🤩

## 인풋랙 개선 방법

엔비디아 글에서 여러가지 인풋랙 개선 방법들이 있어 간단히 남겨보겠습니다.

[https://www.nvidia.com/en-us/geforce/guides/system-latency-optimization-guide/](https://www.nvidia.com/en-us/geforce/guides/system-latency-optimization-guide/)

1. **Turn on NVIDIA Reflex (게임 설정): 게임에서 Reflex 기능 On**
2. **Turn on Ultra Low Latency Mode (엔비디아 설정): Low Latency를 Ultra로 설정**
3. **Turn on Exclusive Fullscreen (게임 설정): 게임에서 “전체화면” 설정**
4. **Turn off VSYNC (엔비디아 설정): Vsync 기능 off**
5. **Turn on “Game Mode” in Windows(OS 설정)**
  1.  **설정 > 게임 > 게임 모드 >게임모드 On 설정**
6. **Overclocking (PC 하드웨어 설정): CPU, GPU, Ram 오버클럭**
7. **Consider Faster Hardware: 하드웨어 업그레이드** 😂
8. **Reduce settings (게임 설정):**
  1. 하위 옵션으로 반응성을 올려라
9. **Enable your maximum refresh rate: 디스플레이의 주사율을 최대로 설정**
10. **Turn on G-SYNC Esports mode (엔비디아 설정)**
11. **Turn on *some* overdrive: 모니터에서 오버드라이드 모드 설정**

## 마무리

요렇게 인풋랙에 대해서 짧게 알아보았는데요. 정리해보고나니 일상적으로 게임에서 이야기하는 인풋랙은 시스템 레이턴시(시스템 지연 시간) 정도로 볼 수 있을 것 같습니다.

인풋랙은 워낙 많은 요소들이 영향을 주는 것이다 보니 하나만으로는 개선이 어렵고 이것저것 다 최적화해야하는 느낌이네요.

개인의 입장에서는 하드웨어 업그레이드, 게임 설정으로 개선할 수 있고
게임 입장에서는 게임 최적화, 하드웨어 기능 호환 등을 지원하는 것이 개선 방법이 될 수 있겠습니다.

## 참고

- [https://quasarzone.com/bbs/qn_hardware/views/474933](https://quasarzone.com/bbs/qn_hardware/views/474933)
  - 원문: [https://videocardz.com/newz/nvidia-reviewer-kit-ldatpcat-will-make-gpu-testing-more-accurate](https://videocardz.com/newz/nvidia-reviewer-kit-ldatpcat-will-make-gpu-testing-more-accurate)
- Nvidia
  - ****What is System Latency:**** [https://www.youtube.com/watch?v=h69JR51pZbU](https://www.youtube.com/watch?v=h69JR51pZbU)
  - [https://www.nvidia.com/en-us/geforce/guides/system-latency-optimization-guide/](https://www.nvidia.com/en-us/geforce/guides/system-latency-optimization-guide/)