---
title: "(Game Dev Study) Grahpics - nsight-graphics"
date: 2024-09-19 15:00:35
categories:
  - Tech
  - Game
tags:
  - Graphics
  - nsight-graphics
  - Profiling
toc: true
thumbnail: 
---

## nsight-graphics 란?

![](https://private-user-images.githubusercontent.com/5077086/368835823-b3d1a1b5-2948-447d-b258-c345a7c19de1.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MjY3MTg2NDEsIm5iZiI6MTcyNjcxODM0MSwicGF0aCI6Ii81MDc3MDg2LzM2ODgzNTgyMy1iM2QxYTFiNS0yOTQ4LTQ0N2QtYjI1OC1jMzQ1YTdjMTlkZTEucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MDkxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDA5MTlUMDM1OTAxWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MmM5YTU4MjcwNWY3YjZiMjJjMDJlYzBmNzg5MmUxNmIxZDUxOWY1MDgzNWM2M2FmY2M3N2NlYTM0NTEyN2VlYSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmYWN0b3JfaWQ9MCZrZXlfaWQ9MCZyZXBvX2lkPTAifQ.kcQfEVW_6jMzXuDY2yw5Ikh-noTr9Xwrr4uea2Zvrmk)

![](https://private-user-images.githubusercontent.com/5077086/368835470-b0f09b62-63f1-4689-ab50-a0f94dbe9a01.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MjY3MTg1NTcsIm5iZiI6MTcyNjcxODI1NywicGF0aCI6Ii81MDc3MDg2LzM2ODgzNTQ3MC1iMGYwOWI2Mi02M2YxLTQ2ODktYWI1MC1hMGY5NGRiZTlhMDEucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MDkxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDA5MTlUMDM1NzM3WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9NWQwYzk1YjkwZjVjZGVmNzk2ZDYzNzNhOWVkOTI2YTRmOTUxNTc1MGRkZGIzNmYzZTk1MzdkYjdlZTExYTVmOSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmYWN0b3JfaWQ9MCZrZXlfaWQ9MCZyZXBvX2lkPTAifQ.MOAZRD5dM8rq2mGe9BGwbqeE-XE1lG_hT5rKvP0ymPo)

https://developer.nvidia.com/nsight-graphics

Nsight Graphics는 NVIDIA에서 제공하는 그래픽 디버깅 및 프로파일링 툴로, 게임 개발이나 그래픽 애플리케이션 개발에서 성능 최적화와 문제 해결을 돕는 도구입니다.

- **프레임 분석**: 개별 프레임을 세밀하게 분석하여 렌더링 파이프라인의 각 단계에서 발생하는 성능 병목을 파악할 수 있습니다.
- **셰이더 디버깅**: 셰이더 코드를 실시간으로 디버깅하고 성능을 분석할 수 있어, 비효율적인 셰이더나 그래픽 문제를 빠르게 찾아 해결할 수 있습니다.
- **GPU 성능 분석**: GPU 사용량과 자원 분배를 분석해 성능 병목을 파악하고, 멀티스레딩 및 CPU와 GPU 간의 효율적인 작업 분배를 돕습니다.
- **메모리 분석**: GPU 메모리와 VRAM 사용을 추적하여 메모리 누수나 과도한 사용을 발견하고, 리소스 최적화를 지원합니다.
- **API 호출 추적**: DirectX, Vulkan, OpenGL 등 다양한 그래픽 API 호출을 추적하여 비효율적인 패턴을 찾고 수정할 수 있습니다.
- **프레임 리플레이**: 문제가 있는 프레임을 저장하고 나중에 재생하여, 렌더링 오류나 크래시 문제를 효과적으로 디버깅할 수 있습니다.
- **실시간 성능 모니터링**: 게임 실행 중 HUD와 성능 그래프를 통해 성능 상태를 실시간으로 확인하고 최적화 포인트를 찾을 수 있습니다.

## nsight-graphics으로 분석할 수 있는 것

홈페이지에서 소개하고 있는 내용을 먼저 살펴보겠습니다.

**Track GPU Performance**
최소한의 오버헤드로 GPU 처리량과 사용률을 분석하여 편향되지 않은 활동 데이터를 수집합니다. 
캡처된 타임라인에서 중요한 성능 마커를 세부적으로 분석하고, 하드웨어 유닛의 처리량, 캐시 적중률, 메모리 처리량 등을 검사할 수 있습니다.

**Analyze GPU Traces**
Nsight Graphics는 캡처된 GPU 추적에 대한 자동 성능 분석을 지원합니다. 
스트리밍 멀티프로세서(SM) 성능에 대한 심층 프로파일링은 여러 프레임에 걸친 셰이더 실행을 자동으로 추적하여 이루어집니다.

**Debug Ray-Tracing and Shaders**
레이 트레이싱 API 호출을 디버깅하고 상태를 검사할 수 있습니다. Ray Tracing Inspector는 가속 구조를 노출하여 씬의 지오메트리와 레이의 교차를 최적화하는 데 도움을 줍니다. 
또한 레이 트레이싱의 효율성을 확인하여 레이 탐색 속도가 높은지 확인할 수 있습니다.

Vulkan 셰이더 디버거를 통해 셰이더 코드를 디버깅할 수 있으며, 이를 통해 렌더 파이프라인에서 실시간으로 셰이더 소스를 확인하고 직접 수정할 수 있습니다.

**Profile Ray-Tracing Shaders**
Nsight Graphics의 셰이더 프로파일러는 셰이더 데이터를 노출하여, 정체 현상과 그 원인을 파악할 수 있게 합니다. 
실시간 셰이더 프로파일러는 실시간으로 가장 비용이 많이 드는 셰이더를 확인할 수 있습니다. 
셰이더 타이밍 히트맵은 픽셀별로 셰이더 처리 시간 지연이 발생한 부분을 씬에 겹쳐 시각화합니다.

레이 트레이싱 셰이더의 프로파일링은 GPU에 대한 광범위한 지식을 요구하는 복잡한 작업이지만, 이러한 기능을 통해 프로파일링 과정을 간소화하고 직관적으로 만들 수 있습니다.

**Export C++ Capture**
CPU 부하가 적은 환경에서 프레임 분석을 수행할 수 있는 독립된 C++ 프로젝트를 생성합니다. 
이를 통해 원래의 애플리케이션에 구속되지 않고 반복 가능한 고립된 분석을 수행할 수 있으며, 최적화 실험을 안전하게 진행할 수 있는 보호된 환경을 제공합니다.

요약해보면... 아래 정도겠군요.
**"GPU 성능 분석, 셰이더 및 레이 트레이싱 디버깅, 실시간 프로파일링을 통해 게임 및 그래픽 애플리케이션 개발에서 최적화와 문제 해결을 돕는 도구"**

## 살짝 사용해본 경험

![](https://github.com/user-attachments/assets/b09ecbb5-2684-4319-9cce-43c983b9fd39)

* 테스트해볼 테스트 프로그램을 찾고 실행하는데 까지 뭔가 어렵다는 느낌은 있었습니다만 실행은 해보았어요.
* Nsight Graphics를 실행 -> Start Activity 할때 사용할 프로그램을 선택하고 실행하면 알아서 프로파일링 툴이 프로그램에 붙습니다.
* 프레임 디버깅을 실행했을 때, 렌더링 이벤트에 따라 어떤 API들이 호출되는지 디버깅할 수 있네요. (사실 봐도 어떤 내용인지 모르겠음)
* Draw, Command 실행 등 눈에 띄는 이벤트나 API들을 확인할 수 있었습니다.

![](https://d29g4g2dyqv443.cloudfront.net/sites/default/files/akamai/track-gpu-performance-630x354.jpg)
Nvidia 예시로는 이렇게도 다 볼 수 있다는데... 툴 창에서 이것저것 더 만져봤어야하나봅니다 😂

> Nvidia 그래픽카드에서 동작할 경우 그래픽스 디버깅에 사용할 수 있는 툴로 사용해볼 수 있겠네요.
> (AMD 그래픽카드에서 사용할 수 있는지는 모르겠군요)
> 엔비디아가 하드웨어 레이 트레이싱을 밀고 있어서 이 툴에도 레이 트레이싱 디버깅과 관련한 기능이 좀 있다는 생각도 들었습니다.

짧게 살펴보고 이만 마치겠습니다 😁

## 가이드 문서, 자료

- NVIDIA Nsight videos: https://www.nvidia.com/en-us/on-demand/playlist/playList-c9450de5-2ffd-4ea9-8a1b-24aeeaf49d4e/

## 다른 그래픽스 분석 툴

- RenderDoc: https://renderdoc.org/
- Intel Graphics Performance Analyzers: [https://www.intel.com/content/www/us/en/developer/tools/graphics-performance-analyzers/overview.html](https://www.intel.com/content/www/us/en/developer/tools/graphics-performance-analyzers/overview.html)
