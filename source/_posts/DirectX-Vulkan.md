---
title: "(Game Dev Study) DirectX, Vulkan 정리"
date: 2021-07-31 16:15:35
categories:
  - Tech
  - Game
tags:
  - Graphics
  - DirectX
toc: true
thumbnail: 
---

## Low level Graphics API (저수준 그래픽스 API)

DirectX, Vulkan을 소개하기에 앞서 저수준 그래픽스 API는 뭔지 알아봐야겠죠?

https://en.wikipedia.org/wiki/List_of_3D_graphics_libraries

위키에서는 3D 그래픽스 라이브러리로 이야기하고 있지만 그래픽스 API로 이해하고 보시면될 것 같습니다.
말 그대로 컴퓨터에서 3D를 볼 수 있게하는 그래픽스 엔진, 라이브러리로 이해하시면 편하겠네요.

이런 API를 통해서 언리얼 엔진이나 각종 게임 엔진에서 오브젝트들을 렌더링하고 그래픽 결과물들을 보여주고 있습니다.

## DirectX, Vulkan 소개

 ### DirectX

https://ko.wikipedia.org/wiki/DirectX

마이크로소프트에서 만든 주로 게임 개발에 널리 쓰이고 있는 API입니다. (멀티미디어를 위한 API)
DirectX에는 2D, 3D 등 그래픽 렌더링을 위한 API가 포함되어있습니다. 

DirectX는 마이크로소프트 플랫폼(Windows, Xbox)에서 동작하는 그래픽스 API로 많은 게임에서 사용되는 API입니다.
현재 최신 버전은 12버전으로 Dx12, D3D12로 많이 부르기도합니다.

관련 자료들은 마이크로소프트 페이지에서도 확인하실 수 있으니 참고해보세요!

* https://docs.microsoft.com/en-us/windows/win32/direct3d12/direct3d-12-graphics
* Youtube Videos: https://www.youtube.com/channel/UCiaX2B8XiXR70jaN7NK-FpA

### Vulkan

https://ko.wikipedia.org/wiki/%EB%B2%8C%EC%BB%A8_(API)

Vulkan은 크로스 플랫폼 3D 그래픽스 API입니다. 모바일, 리눅스, 마이크로소프트 플랫폼 등에 사용될 수 있다는 뜻이죠.
크로노스 그룹에서 OpenGL의 차세대 버전으로 준비하다가 Vulkan이라는 이름으로 릴리스되었습니다.

OpenGL처럼 게임이나 미디어 처럼 고성능 실시간 3D 그래픽스 앱을
모든 플랫폼에서 고성능으로 CPU를 적게 사용하도록 개발하는 것을 목표로 만들어진 API입니다.

<iframe width="560" height="315" src="https://www.youtube.com/embed/rvCD9FaTKCA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

영상에서는 기존 OpenGL 보다 Vulkan이 CPU 코어 활용성이 좋고 에너지를 덜 쓰는 것을 비교해서 보여주고 있네요.

## DirectX 11, DirectX 12, Vulkan 뭘 써서 개발해야할까?

요즘 게임 개발을 하는데 바로 저수준 그래픽 API를 사용해서 개발하는 경우는 별로 없을겁니다.
언리얼 엔진이나 유니티 등 상용 엔진들을 사용해서 게임 컨텐츠를 개발하고 있죠.

컨텐츠 개발 이후 최적화에 있어서 어떤 것을 중점으로 최적화를 할지, 어떤 플랫폼에 런칭을 할지에 따라 위 질문에 있는 모든 것을 사용해야할 수도 있습니다.
Dx11이 Dx12 보다 버전이 낮지만 현재 개발된 환경에 따라 11 버전을 사용해야할 수도 있겠죠.
API에 맞게 최적화도 필요한 것이 있어 각 개발 환경에 맞춰 개발해야한다 정도로 이야기할 수 있을 것 같습니다. (너무 정론이네요 😂)

## DirectX vs Vulkan?

<iframe width="560" height="315" src="https://www.youtube.com/embed/bHCzfq0jAfg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

2개의 API를 확인해보았으니 비교를 안해볼 수 없죠! 사실 Youtube에서 2개의 API를 치면 많이 나오는 것이 비교내용입니다.
게이머 입장에서는 그래픽 품질은 좋고 FPS가 잘나오면 최고이니까요. 게임 개발 엔진들에서도 각 API를 사용하여 개발할 수 있도록 지원하고 있기도하구요.

영상만 보았을 때는 Dx11은 Dx12, Vulkan에 비해 안좋은 버전으로 보이지만 사실 버전에 맞춰 게임 코드도 최적화가 필요하기에 버전만 12로 올리기는 어렵습니다.

다른 블로그 글이나 아티클들을 보면 두 API를 비교한 것은 대부분 성능상의 비교가 대부분인데요.
이건 사실 하드웨어 + 게임(앱) 마다 천차만별이라서 뭐가 더 좋고 나쁘다를 판별하기는 어렵다고 생각합니다.

## 마무리

사실 2개의 API를 비교하고 차이점을 정리하기에는 어려움이 있네요.

각각 그래픽을 렌더링하기 위해 다른 동작을 사용하고 있는 것도 있고 기본 개념이 같은 것들도 있었습니다.

이번 포스팅을 위해 공부를 얕고 짧게했지만 누가 우위에 있냐는 크게 중요하지 않은 것으로 결론을 내렸습니다.

아마 다음에는 하나하나 조금 더 깊게 공부할만한 주제로 찾아올 수 있지 않을까 싶네요.

다음에는 게임 개발에 필요한 그래픽스에 대해 조금이나마 더 알 수 있는 지식으로 찾아오겠습니다. 감사합니다. 😈
