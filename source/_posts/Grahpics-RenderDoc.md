---
title: "(Game Dev Study) Grahpics - RenderDoc"
date: 2023-08-13 18:00:35
categories:
  - Tech
  - Game
tags:
  - Graphics
  - RenderDoc
  - Profiling
toc: true
thumbnail: 
---

## RenderDoc이란?

<div style="width: 100px;">
    <img src="https://renderdoc.org/fp/logo.svg"/>
  </div>

[https://renderdoc.org/](https://renderdoc.org/)

그래픽 작업, 렌더링 최적화를 위한 프로파일링으로 사용할 수 있는 디버거 툴로 사이트에서 설명하는 내용을 가져와보면 다음과 같습니다.

> RenderDoc is a free MIT licensed stand-alone graphics debugger that allows quick and easy single-frame capture and detailed introspection of any application using Vulkan, D3D11, OpenGL & OpenGL ES or D3D12 across Windows, Linux, Android, or Nintendo Switch™.
> → 요약해보면 오픈소스 그래픽 디버거로 쉬운 프레임 캡처와 상세 분석(검사)을 할 수 있는 툴입니다.

RenderDoc은 Github에서 소스를 공개하고 있으며 빌드는 홈페이지에서 다운로드 받을 수 있습니다.

Source: [https://github.com/baldurk/renderdoc](https://github.com/baldurk/renderdoc)
Download: [https://renderdoc.org/builds](https://renderdoc.org/builds)

## RenderDoc으로 분석할 수 있는 것

언리얼 서밋 2019에서 다룬 내용을 중심으로 정리해보려합니다.

영상에서는 언리얼 엔진에서 RenderDoc 플러그인을 설정하고 보여주고 있어서 언리얼 엔진의 렌더링 파이프라인에 맞춰 정리해보겠습니다.

![](https://user-images.githubusercontent.com/5077086/260287512-60791fb0-1023-43fd-9c44-c6d0120e9f3f.png)

![](https://user-images.githubusercontent.com/5077086/260288120-f17985d1-fea0-4920-be50-80b89ec9eb5c.png)

위 파이프라인은 추상화한 내용으로 더 자세한 내용은 참고 자료 링크로 남겨두겠습니다.
쉬운 이해를 위해 추상화를 하면서 그림을 그리는 단계와 비교해서 쉽게 설명해주셨어요.

> 밑그림 - 밑그림 색칠 - 다듬기 - 그리기 - 마무리
각 단계별로 어떤 내용들을 볼 수 있는지 알 수 있었습니다.

### ⭐ 요약 ⭐

- PrePass - BasePass - Lighting - Translucency 각 단계에서 일어나는 일을 분석할 수 있음
- Event Browser 에서 각 단계의 이벤트를 확인하고 Texture Viewer, Mesh Viewer, Pixel History 등의 기능을 통해 분석, 프로파일링할 수 있다

### PrePass - 밑그림

![](https://user-images.githubusercontent.com/5077086/260288255-51c14e72-e449-4684-a79e-f2113e6bcb33.png)

![](https://user-images.githubusercontent.com/5077086/260289146-60b96657-79d5-4459-999b-bfbb43f70889.png)

RenderDoc에서 렌더링 파이프라인에 따라 이벤트가 발생하고 그 시점에 따라 분석할 수 있게 되어있네요. (화면 왼쪽에 Event Browser에서 확인할 수 있음)

위에서 보고 있는 event는 **PrePass(PrePass DDM_AllOpaque …)입니다.**

이 단계에서는 하위 이벤트에서 각 에셋들의 메쉬들을 Mesh Viewer를 통해 확인하고 과도하게 메쉬를 복잡하게 만들지 않았는지를 확인할 수 있습니다.
(폴리곤을 과도하게 사용하지는 않았는지 = 너무 디테일하게 메쉬를 만들었는지)

### BasePass - 밑그림 색칠

![](https://user-images.githubusercontent.com/5077086/260289735-815644da-8792-411c-9acd-f70ff90cb6ef.png)

BasePass는 PrePass와 동일하게 모델을 화면에 맞게 변형합니다. 그 후에 PrePass과 대조해서 필요한 곳에만 색칠하는 작업을 반복합니다. PrePass를 이용하여 필요한 곳만 색칠할 수 있습니다.
이 단계에서는 Texture Viewer에서 각 에셋을 텍스쳐로 색칠하는데에 필요하지 않은 텍스쳐가 사용되거나 잘못된 경우를 찾아볼 수 있습니다.

> 영상 예시로는 범용 머터리얼을 사용해서 발생한 이슈로 필요한 텍스쳐만 사용하는 머터리얼로 수정하고 해결하는 것을 볼 수 있었습니다.

### Lighting - 다듬기

![](https://user-images.githubusercontent.com/5077086/260290183-394803cb-40bf-418c-95d9-6083e1e3d4cf.png)

Lighting 단계에서는 에셋들이 빛의 영향을 잘 받는지 비효율적으로 빛의 범위가 크게 설정되어있지는 않은지 확인할 수 있습니다.

라이팅 각 이벤트를 눌러보고 Texture Viewer의 Outputs를 보면 어떻게 라이트가 적용되어 렌더링 씬이 바뀌어가는지 알 수 있어요.

> ![](https://user-images.githubusercontent.com/5077086/260290389-e3044c50-ef5c-4bda-b571-d9096f42c16f.png)
> 영상에서는 불필요한 큰 라이트 범위를 조정해서 라이팅 렌더링 비용을 개선했습니다. 👍

### Translucency - 그리기

![](https://user-images.githubusercontent.com/5077086/260290878-49f6ea55-81ba-44e6-9816-5b9b9e4f39c8.png)

이 단계는 대략 그림이 완성되었으니 마지막 마무리로 계속 이미지를 겹쳐서 그리는 단계입니다.
이 때에 추가로 그리는 범위가 커질수록, 겹쳐서 그릴수록 어려워지게됩니다. (비용이 커짐)

이 부분에 대한 프로파일링, 최적화는 언리얼 엔진 에디터에서도 쿼드 오버드로(Quad Overdraw)나 셰이더 복잡도(Shader Complexity) 뷰를 통해서 보고 개선해볼 수 있습니다.

RenderDoc에는 **Pixel History** 기능을 통해서 픽셀이 어떻게 변화했는지 볼 수 있는 편리한 기능이 있습니다.

1. Texture Viewer → Outputs → 이미지에서 확인하고자하는 픽셀 영역을 오른쪽 버튼을 누릅니다
2. Outputs 하단에 History를 누릅니다 → 픽셀이 변화한 히스토리를 확인합니다

> 영상에서는 확인한 곳의 픽셀은 안개에 의해 색이 변해야하는 곳인데 변하지 않는 것을 픽셀 히스토리를 통해서 확인 → 개선!

### PostProcess - 마무리

PostProcess 단계는 포토샵의 필터 적용과 같은 단계로 볼 수 있는데요. RenderDoc에서 언리얼 엔진의 PostProcess를 보기는 쉽지 않다고 합니다.
어떤 기능에 의해 합쳐진 효과들이 적용되고 보이게되어서 RenderDoc에서는 한계가 있다고 합니다.

> 나중에 엔지니어나 TA 분에게 물어보고 공부해보는 것으로 해야겠군요 😃

## 마무리

오랜만에 최적화 부분을 이것저것 들여다보니 재미있었네요. 😎
찾다보니 RenderDoc은 오픈소스로 알려져있는 툴이고 Nvidia나 Intel에서도 분석툴이 있어서 나중에 한번 슬쩍보는 것도 재미있겠다 싶습니다.
나중에 시간나는대로 Nvidia 부터 살펴보고 포스트해보겠습니다. 👋

## 가이드 문서, 자료

- [https://youtu.be/EF0YpKHfbAw](https://youtu.be/EF0YpKHfbAw)
    - 언리얼 서밋 2019 아티스트를 위한 흥나는 프로파일링!: RenderDoc
    - 추가적인 내용은 위 영상을 참고하면 좋을 것 같습니다
- 가이드 문서-튜토리얼: [https://renderdoc.org/docs/getting_started/quick_start.html](https://renderdoc.org/docs/getting_started/quick_start.html)
- 가이드 영상 모임: [https://www.youtube.com/user/baldurkarlsson](https://www.youtube.com/user/baldurkarlsson)
- 언리얼 파이프라인: [https://unrealcommunity.wiki/unreal-schematics-2d6859](https://unrealcommunity.wiki/unreal-schematics-2d6859)
- 언리얼 엔진 RenderDoc: [https://docs.unrealengine.com/4.26/ko/TestingAndOptimization/PerformanceAndProfiling/RenderDoc/](https://docs.unrealengine.com/4.26/ko/TestingAndOptimization/PerformanceAndProfiling/RenderDoc/)

## 다른 그래픽스 분석 툴

- Nvidia Nsight Graphics: [https://developer.nvidia.com/nsight-graphics](https://developer.nvidia.com/nsight-graphics)
- Intel Graphics Performance Analyzers: [https://www.intel.com/content/www/us/en/developer/tools/graphics-performance-analyzers/overview.html](https://www.intel.com/content/www/us/en/developer/tools/graphics-performance-analyzers/overview.html)