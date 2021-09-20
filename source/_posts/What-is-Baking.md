---
title: 베이킹(Baking)이란 무엇일까?
toc: true
date: 2021-09-19 19:02:37
categories:
- Tech
tags:
- Computer Graphics
- Study
thumbnail: https://user-images.githubusercontent.com/5077086/133923617-fd0c286d-7c47-40ee-a426-07b814fdb06d.png
---

## Baking이 뭐죠? 🍞 🥖 🍩

> ⚠️ 기술적으로 깊게 다루는 글이 아닌 그래픽스, 렌더링과 관련한 공부 중에 정리한 내용입니다.
> 일부 기술적인 내용은 오류가 있을 수 있습니다.

### 사전적 의미의 Baking

- 굽다, 구워지다, 굽기
- 빵을 굽다 / 햇볕에 피부를 태운다는 뜻으로 쓴다(?)

### CG(Computer Graphics)에서의 Baking은?

위키에서 설명하는 Baking을 찾아보았습니다. (번역을 돌려보겠습니다. 🤖)

<details>
  <summary><a href="https://en.wikipedia.org/wiki/Texture_mapping#Baking">https://en.wikipedia.org/wiki/Texture_mapping#Baking</a></summary>
  As an optimization, it is possible to render detail from a complex, high-resolution model or expensive process (such as global illumination) into a surface texture (possibly on a low-resolution model). Baking is also known as render mapping. This technique is most commonly used for light maps, but may also be used to generate normal maps and displacement maps. Some computer games (e.g. Messiah) have used this technique. The original Quake software engine used on-the-fly baking to combine light maps and colour maps ("surface caching"). Baking can be used as a form of level of detail generation, where a complex scene with many different elements and materials may be approximated by a single element with a single texture, which is then algorithmically reduced for lower rendering cost and fewer drawcalls. It is also used to take high-detail models from 3D sculpting software and point cloud scanning and approximate them with meshes more suitable for realtime rendering.
</details>

> 베이킹은 최적화로 복잡한 고해상도 모델 또는 비싼 프로세스(예: GI, Global Illumination)의 세부 정보를 표면 텍스처(저해상도 모델에서 가능)로 렌더링하는 것이 가능합니다. 베이킹은 렌더 매핑이라고도 합니다. 이 기술은 라이트 맵에 가장 일반적으로 사용되지만 노멀 맵과 변위 맵을 생성하는 데에도 사용할 수 있습니다. 일부 컴퓨터 게임(예: Messiah)은 이 기술을 사용했습니다. 원래 Quake 소프트웨어 엔진은 즉석 베이킹을 사용하여 라이트 맵과 컬러 맵("표면 캐싱")을 결합했습니다. **베이킹은 LOD(Level Of Detail) 생성의 한 형태로 사용할 수 있습니다. 여기에서 다양한 요소와 재질이 포함된 복잡한 장면은 단일 텍스처가 있는 단일 요소로 근사화될 수 있으며, 그런 다음 알고리즘을 통해 렌더링 비용을 낮추고 드로콜을 줄일 수 있습니다.** 또한 3D 조각 소프트웨어 및 포인트 클라우드 스캐닝에서 세부 모델을 가져와 실시간 렌더링에 더 적합한 메시로 근사하는 데 사용됩니다.

[https://en.m.wikipedia.org/wiki/Glossary_of_computer_graphics#baking](https://en.m.wikipedia.org/wiki/Glossary_of_computer_graphics#baking)

Performing an expensive calculation offline, and caching the results in a Texture map or Vertex attributes. Typically used for generating lightmaps, normal maps, or low level of detail models.

> 오프라인에서 값비싼 계산을 수행하고 결과를 텍스처 맵 또는 버텍스(Vertex) 속성으로 캐싱합니다. 
일반적으로 라이트맵, 노말 맵 또는 낮은 수준의 LOD(Level of Detail)을 생성하는 데 사용됩니다.

Texture baking, Light baking 등이 있으며 텍스쳐나 빛을 렌더링할 때 미리 만들어둔 결과물로 빠르게 효율적으로(저렴한 비용으로) 렌더링할 수 있도록 미리 만들어두는 것으로 굳이 비유하자면..

> 빵을 먹을때 밀가루 반죽하고 휴지하고 틀에 넣고 굽고 먹는 것이 아니라
미리 반죽 준비해두고 오븐도 예열해두고 바로 구워먹을 수 있게 준비해두는 것
(혹은 다 구워두고 먹기만하는 것) 정도로 비유할 수 있겠네요.

## 왜 Baking 하나요?

오브젝트를 렌더링하기 전에 미리 준비할 수 있는 것들을 준비해서 실제 렌더링할 때 가져다가 효율적으로 렌더링하는 것이 좋잖아요.
왜 효율적으로 렌더링해야하죠? 더 많은 오브젝트를 부드럽고 높은 품질로(이쁘게) 렌더링할 수 있으니까요.

![출처: https://barista7.tistory.com/429](https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcSOUWU6Cq-IfeG1d3hw1jW0icOst98vNsLeV9HkbTOEYGbcOFgk)

미션임파서블 - 고스트 프로토콜 복도씬 [https://youtu.be/k9HGylRFS-U?t=27](https://youtu.be/k9HGylRFS-U?t=27)
<p align="center">
<img src="https://mblogthumb-phinf.pstatic.net/MjAxODA4MzBfMTc4/MDAxNTM1NjA2MTM3Mjk5.jpSHJahUYH_fJNeYbQR5XirterdL9T54pVdDsxcjfl8g.swZcJY0OV-lBludFy4oHbZcoBvqt7N_waH_ipW3AXFEg.GIF.itsno/KakaoTalk_20180830_141339834.gif?type=w800"/>
<p align="center">조금 다른 예시지만 미리 만들어두고 다른 것을 할 수도 있죠. 😈</p>
</p>


빛과 텍스쳐 변화에 맞춰 실시간 연산 처리가 가능한 하드웨어 스펙과 기술이 늘어나고 있지만
베이킹된 텍스쳐 맵, 노멀 맵, 라이트 맵 등을 사용하면 렌더링할 때 비용을 크게 절약할 수 있습니다.

### 맵(Map)? 매핑(Mapping)?

텍스쳐를 이쁘고 효율적으로 렌더링하기 위해서 많은 기술들이 들어갑니다.
실제로 오브젝트의 매시(mesh)를 상세하게 만들어서 렌더링할 수 있겠지만 매시를 상세하게 만들수록 렌더링 비용이 증가하게 됩니다. 렌더링시 실제로 보이는 결과물이 거의 동일하지만 매시는 덜 자세하게 만들고 매핑 기술들을 적용하여 렌더링 비용을 줄일 수 있죠.

주로 언급되는 매핑 기술들은 범프 매핑, 법선 매핑(노말 매핑), 시차 매핑(Parallax Mapping), 변위 매핑(Displacement Mapping), 라이트 매핑(Light Mapping, Lightmap), 쉐도우 매핑(Shadow Mapping) 등이 있고 이외에도 많은 기술들이 있습니다.

> 사실 매핑과 관련한 내용들이 많아서 그래픽스 엔지니어, TA나 아티스트가 아니라면 다 상세하게 알기는 쉽지 않을 것 같네요.
이런 기술들이 우리가 렌더링된 영상을 볼때 적용되어있다 정도만 알아주세요. 😸

- [https://ko.m.wikipedia.org/wiki/텍스처_매핑](https://ko.m.wikipedia.org/wiki/%ED%85%8D%EC%8A%A4%EC%B2%98_%EB%A7%A4%ED%95%91)
- [https://en.m.wikipedia.org/wiki/Bump_mapping](https://en.m.wikipedia.org/wiki/Bump_mapping)
    - [https://en.m.wikipedia.org/wiki/Normal_mapping](https://en.m.wikipedia.org/wiki/Normal_mapping)
    - [https://en.m.wikipedia.org/wiki/Parallax_mapping](https://en.m.wikipedia.org/wiki/Parallax_mapping)
- [https://en.m.wikipedia.org/wiki/Displacement_mapping](https://en.m.wikipedia.org/wiki/Displacement_mapping)
- [https://en.m.wikipedia.org/wiki/Lightmap](https://en.m.wikipedia.org/wiki/Lightmap)

![https://spiderlili.com/2020/03/01/tech-art-tips-tricks-all-about-displacement-normal-bump-maps/](https://spiderlilystudio.files.wordpress.com/2020/03/maps.jpg)

![https://docs.unrealengine.com/4.27/Images/RenderingAndGraphics/Materials/HowTo/DetailTexturing/DT_Hooked_Up_Textures.jpg](https://docs.unrealengine.com/4.27/Images/RenderingAndGraphics/Materials/HowTo/DetailTexturing/DT_Hooked_Up_Textures.jpg)

언리얼 엔진에서는 텍스쳐를 이런식으로 데이터들을 연결해서 머터리얼 + 매시로 물체들을 렌더링합니다.
언리얼 엔진뿐만 아니라 최신 게임 엔진에서는 위와 같은 PBR(Physically Based Rendering)을 이용하여 렌더링합니다. (표면의 재질에 따른 빛의 반사가 물리적으로 어떻게 이루어지는지를 시뮬레이션해서 그래픽을 표현하는 기법으로 [https://namu.wiki/w/물리 기반 렌더링](https://namu.wiki/w/%EB%AC%BC%EB%A6%AC%20%EA%B8%B0%EB%B0%98%20%EB%A0%8C%EB%8D%94%EB%A7%81) 자세한 내용은 나무위키를 참고해보세요.)

## Baking할 때 주로 어떤 것을 굽나요?

앞서 살펴보았던 내용을 다시 가져왔습니다.

- [https://en.m.wikipedia.org/wiki/Glossary_of_computer_graphics#baking](https://en.m.wikipedia.org/wiki/Glossary_of_computer_graphics#baking)

    Performing an expensive calculation offline, and caching the results in a Texture map or Vertex attributes. Typically used for generating lightmaps, normal maps, or low level of detail models.

> 오프라인에서 값비싼 계산을 수행하고 결과를 텍스처 맵 또는 버텍스(Vertex) 속성으로 캐싱합니다. 
**일반적으로 라이트맵, 노말 맵 또는 낮은 수준의 LOD(Level of Detail)을 생성하는 데 사용됩니다.**

여기서 오프라인의 의미는 실제 렌더링이 이뤄지지 않는 환경을 의미합니다.
실시간으로 렌더링하기에 비용이 큰 라이트맵, 노말 맵, LOD를 미리 만들어두는 것이죠.
앞서 위키 링크를 첨부해두었지만 각각 항목에 대해 살펴보겠습니다.

### 라이트맵(LightMap)

[https://en.m.wikipedia.org/wiki/Lightmap](https://en.m.wikipedia.org/wiki/Lightmap)

![LightMap](https://upload.wikimedia.org/wikipedia/commons/thumb/1/15/Lightmapped_Scene_with_Lightmap.png/2880px-Lightmapped_Scene_with_Lightmap.png)

위와 같은 화면(Scene)에 설정되어있는 빛(해, 조명 등 빛 오브젝트)에 따라 보이는 빛나는 부분과 어두운 부분에 대해 맵을 만든 것을 라이트맵(LightMap)이라고 합니다.

간단하게 라이트맵은 빛에 따라 보이는 것을 텍스처로 만들었다고 볼 수 있습니다.
실시간으로 빛을 계산해서 보여줄 필요없이 텍스처를 보여주어 렌더링시 비용을 절약합니다.

다만 라이트맵은 정적인 물체, 환경에 대해 생성할 수 있다는 제한이 있습니다.
물론 최신 게임 엔진에서 지원하는 기능 중에는 움직이는 물체에 대해 라이트맵을 생성 및 적용할 수 있는 기능을 지원할 수도 있습니다만.. 아마 빛 자체를 실시간 렌더링하는 기술이지 않을까 싶습니다.

Unity에서는 [Light Prove(라이트 프로브)](https://docs.unity3d.com/kr/530/Manual/LightProbes.html)를 이용해서 빛의 실시간 렌더링을 일부 지원하고 있고,
Unreal Engine 5에서는 [루멘(Lumen) 시스템](https://docs.unrealengine.com/5.0/ko/RenderingFeatures/Lumen/)을 이용해서 빛의 실시간 렌더링을 모두 지원한다고 하네요. (강력하다..)

> 잠시 딴길로 갔지만 정리해보면,
라이트맵은 빛에 따라 표현되는 것을 텍스처(이미지)로 만들어서 렌더링할 때 비용을 줄일 수 있는 친구입니다.

### **노말 맵(Normal Map)**

[https://en.m.wikipedia.org/wiki/Normal_mapping](https://en.m.wikipedia.org/wiki/Normal_mapping)

링크는 노말 매핑이지만 노말 매핑에 사용되는 것이 노말 맵이니 참고할 수 있겠습니다.
노말 매핑은 **튀어나온 곳, 움푹 들어간 곳의 빛을 왜곡하는 기법**입니다. 노말 매핑을 사용하면 많은 폴리곤을 사용하지 않고 세세한 부분을 표현할 수 있습니다.

![Normal Mapping](https://upload.wikimedia.org/wikipedia/commons/3/36/Normal_map_example.png)

위와 같이 매시의 폴리곤 수를 줄이고 노말 매핑을 적용하면 폴리곤이 많은 매시의 효과를 볼 수 있습니다.

![Normal map & texture](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2e/Normal_map_example_with_scene_and_result.png/2880px-Normal_map_example_with_scene_and_result.png)

- 왼쪽 이미지: 평평한 텍스처 이미지입니다.
- 중간 이미지: 노말 맵으로 빛의 XYZ를 RGB로 표현한 맵 이미지입니다.
- 오른쪽 이미지: 왼쪽 이미지에 중간 이미지의 노말 맵을 노말 매핑한 최종 렌더링된 모습입니다.

> 정리해보면 노말 맵은 오브젝트의 굴곡을 표현할 수 있는 빛의 벡터 정보를 갖는 데이터입니다.

### LOD(Level Of Detail)

[https://en.m.wikipedia.org/wiki/Level_of_detail_(computer_graphics)](https://en.m.wikipedia.org/wiki/Level_of_detail_(computer_graphics))

직역하면 세부 수준(...)이지만 **오브젝트의 세부 표현을 레벨(또는 거리)에 따라 표현한다** 정도로 이해하면될 것 같습니다.

![거리에 따라 토끼를 세부 표현 - LOD](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQwNcQAvaM-7KQ25GS2fBOdAGveoiJ5Vh7Xvw&usqp=CAU)

LOD를 적용하면 아래와 같은 장점이 있습니다.

- 멀리있는 오브젝트를 자세하게 표현하지 않아 비용을 줄일 수 있습니다.
- 멀리있는 오브젝트를 덜 자세하게 표현하여 자연스럽게 표현할 수 있습니다.
(실제 멀리 있는 물체를 보았을 때 작고 흐릿하게 보이는 것처럼 표현되어야 자연스럽기 때문이죠.)

언리얼 엔진에서는 LOD 0가 가장 자세하게 표현하고 LOD 1, LOD 2 이렇게 점차 덜 자세하게 표현합니다.

![플랫폼 별 LOD 표현](https://docs.unrealengine.com/4.27/Images/WorkingWithContent/Types/StaticMeshes/PerPlatformLOD/PPlatformLOD_07.webp)

위 이미지는 각 플랫폼 별로 표현할 LOD 기준을 정하고 상황에 맞춰 렌더링 될 수 있도록 설정한 것을 보여주고 있네요.

LOD는 밉맵(MipMap)을 이용하여 적용할 수도 있고 언리얼 엔진처럼 LOD 레벨별로 매시&텍스쳐를 설정할 수도 있습니다.
여기서 밉맵은 렌더링 속도를 향상시키기 위한 목적으로 기본 텍스처와 이를 연속적으로 미리 축소시킨 텍스처들로 이루어진 비트맵 이미지의 집합입니다. (자세한 내용은 [위키](https://ko.m.wikipedia.org/wiki/%EB%B0%89%EB%A7%B5)를 참고해주세요.)

> 정리해보면 LOD는 가까울수록 자세하게 보이게하는 방식입니다.
(구현에 따라 다르게 보이게 설정할 수도 있지만 일반적인 정의로 이해해주세요)

### Baking 결과물로 뭘하죠?

베이킹 결과물인 라이트 맵, 노말 맵, LOD로 오브젝트들을 렌더링할 때에 사용합니다.
매시의 상세(디테일)를 줄이고 여러 매핑 기술을 적용해서 렌더링 비용을 줄이고 빠르게 표현할 수 있죠.

## 마무리: 이제 Baking이 뭔지 이해하셨나요?

저는 처음에는 Bake, Baking이 그냥 빵을 굽는 정도의 뭔가 미리 컴파일 같은 것을 해두고 사용한 것인가 싶었는데요.
이번에 정리하면서 베이킹을 하고 반영하기 위해 많은 기술들이 들어간 것을 공부할 수 있었습니다.

주로 위키를 통해서 베이킹이나 그래픽스와 관련한 내용들을 알아볼 수 있었는데 조금 더 깊게 그래픽스 엔지니어링과 관련한 일반적인 지식도 공부하고 싶어졌네요.

https://gabrielgambetta.com/computer-graphics-from-scratch/

컴퓨터 그래픽스를 한번 쓱 훑어보기 좋을 것 같아 한번 읽어보고 포스트 남겨보겠습니다. 😄