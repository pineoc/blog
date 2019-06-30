---
title: OpenGL ES 버전 2.0과 3.0 차이
date: 2019-06-30 15:22:35
categories:
  - Tech
tags:
---

![](https://3.bp.blogspot.com/-c_SkNvG1Vr8/WRhwNJUMi5I/AAAAAAAAH7E/IBNjjCt97uYbo9oewA7yQNQxG_NP4IaFgCK4B/s640/opengl.png)

## OpenGL ES(Embeded System)

Cocos2d-x 버전 차이에 대해서 공부하던 중에 그 기반이 되는 OpenGL ES의 버전에도
큰 차이가 있지 않을까하여 공부해봤습니다.

우선 OpenGL ES란, ([Wikipedia-ko](https://ko.wikipedia.org/wiki/OpenGL_ES))

> OpenGL ES (임베디드 단말을 위한 OpenGL)는 크로노스 그룹이 정의한 3차원 컴퓨터 그래픽스 API인 OpenGL의 서브셋으로, 휴대전화, PDA 등과 같은 임베디드 단말을 위한 API이다.

한글로 작성된 위키는 짧군요. 영어로 작성된 위키를 더 보겠습니다. ([Wikipedia-en](https://en.wikipedia.org/wiki/OpenGL_ES))

> OpenGL for Embedded Systems (OpenGL ES or GLES) is a subset of the OpenGL computer graphics rendering application programming interface (API) for rendering 2D and 3D computer graphics such as those used by video games, typically hardware-accelerated using a graphics processing unit (GPU). It is designed for embedded systems like smartphones, computer tablets, video game consoles and PDAs. OpenGL ES is the "most widely deployed 3D graphics API in history". The API is cross-language and multi-platform. The libraries GLUT and GLU are not available for OpenGL ES. OpenGL ES is managed by the non-profit technology consortium Khronos Group. Vulkan, a next-generation API from Khronos, is made for simpler high performance drivers for mobile and desktop devices.

설명에 큰 차이는 없지만, API에 대한 설명에는 크로스 랭귀지, 멀티 플랫폼이 포함되어 있네요.
OpenGL에서 사용할 수 있는 `GLUT`, `GLU`는 OpenGL ES에서는 사용할 수 없다는 것 정도를 추가로 알 수 있었습니다.

각 버전별 설명도 잘 나와있는 영문 위키를 보면,

### OpenGL ES 2.0 - (EN)

OpenGL ES 2.0 was publicly released in March 2007.[[6]](https://en.wikipedia.org/wiki/OpenGL_ES#cite_note-6) It is based roughly on OpenGL 2.0, but it eliminates most of the fixed-function rendering pipeline in favor of a programmable one in a move similar to transition from OpenGL 3.0 to 3.1.[[7]](https://en.wikipedia.org/wiki/OpenGL_ES#cite_note-7) Control flow in shaders is generally limited to forward branching and to loops where the maximum number of iterations can easily be determined at compile time.[[8]](https://en.wikipedia.org/wiki/OpenGL_ES#cite_note-8) Almost all rendering features of the transform and lighting stage, such as the specification of materials and light parameters formerly specified by the fixed-function API, are replaced by [shaders](https://en.wikipedia.org/wiki/Shader) written by the graphics programmer. As a result, OpenGL ES 2.0 is not [backward compatible](https://en.wikipedia.org/wiki/Backward_compatibility) with OpenGL ES 1.1. Some incompatibilities between the desktop version of OpenGL and OpenGL ES 2.0 persisted until OpenGL 4.1, which added the `GL_ARB_ES2_compatibility` extension.[[9]](https://en.wikipedia.org/wiki/OpenGL_ES#cite_note-9)

### OpenGL ES 3.0 - (EN)

The OpenGL ES 3.0 specification[[10]](https://en.wikipedia.org/wiki/OpenGL_ES#cite_note-10) was publicly released in August 2012.[[11]](https://en.wikipedia.org/wiki/OpenGL_ES#cite_note-11) OpenGL ES 3.0 is backwards compatible with OpenGL ES 2.0, enabling applications to incrementally add new visual features to applications. OpenGL 4.3 provides full compatibility with OpenGL ES 3.0. Version 3.0 is also base of [WebGL](https://en.wikipedia.org/wiki/WebGL) 2.0.[[12]](https://en.wikipedia.org/wiki/OpenGL_ES#cite_note-12)

New functionality in the OpenGL ES 3.0 specification includes:

- multiple enhancements to the [rendering pipeline](https://en.wikipedia.org/wiki/Rendering_pipeline) to enable acceleration of advanced visual effects including: [occlusion queries](https://en.wikipedia.org/wiki/Occlusion_queries), [transform feedback](https://en.wikipedia.org/wiki/Transform_feedback), [instanced rendering](https://en.wikipedia.org/wiki/Geometry_instancing) and support for four or more [rendering targets](https://en.wikipedia.org/wiki/Render_Target),
- high quality [ETC2 / EAC](https://en.wikipedia.org/wiki/Ericsson_Texture_Compression#ETC2_and_EAC) [texture compression](https://en.wikipedia.org/wiki/Texture_compression) as a standard feature, eliminating the need for a different set of [textures](https://en.wikipedia.org/wiki/Texture_mapping) for each platform,
- a new version of the GLSL ES [shading language](https://en.wikipedia.org/wiki/Shading_language) with full support for integer and [32-bit](https://en.wikipedia.org/wiki/32-bit) [floating point](https://en.wikipedia.org/wiki/Floating_point) operations;[[13]](https://en.wikipedia.org/wiki/OpenGL_ES#cite_note-13)

- greatly enhanced [texturing](https://en.wikipedia.org/wiki/Texture_mapping) functionality including guaranteed support for [floating point](https://en.wikipedia.org/wiki/Floating_point) textures, 3D textures, depth textures, vertex textures, NPOT textures, R/RG textures, immutable textures, 2D array textures, [swizzles](https://en.wikipedia.org/wiki/Swizzling_(computer_graphics)), [LOD](https://en.wikipedia.org/wiki/Level_of_detail) and [mip level](https://en.wikipedia.org/wiki/Mipmap) clamps, seamless [cube maps](https://en.wikipedia.org/wiki/Cube_mapping) and sampler objects,
- an extensive set of required, explicitly sized [texture](https://en.wikipedia.org/wiki/Texture_mapping) and render-buffer formats, reducing implementation variability and making it much easier to write portable applications.

(참고, [http://www.informit.com/articles/article.aspx?p=2181697&amp;seqNum=2](http://www.informit.com/articles/article.aspx?p=2181697&seqNum=2))

음, 내용이 많아 번역한 내용으로 각각 살펴보고 정리해보겠습니다.

### OpenGL ES 2.0

OpenGL ES 2.0는 2007년 3월에 출시되었습니다. OpenGL 2.0을 기반으로 하지만 OpenGL 3.0에서 3.1로 업데이트 될 때와 비슷하게 고정 렌더링 파이프라인을 제거하였습니다. 셰이더의 제어 흐름은 컴파일할 때에 쉽게 결정할 수 있는 순방향 분기, 루프로 제한됩니다.

이전에 고정 함수 API에 의해 지정된 재질 및 조명 매개 변수와 같은 변형 및 조명 스테이지의 거의 모든 렌더링 기능은 그래픽 프로그래머가 작성한 쉐이더로 대체되었습니다. 따라서 OpenGL ES 2.0은 OpenGL ES 1.1과 호환되지 않습니다. OpenGL과 OpenGL ES 2.0 데스크톱 버전 간의 일부 비 호환성은 GL_ARB_ES2_compatibility 확장을 추가한 OpenGL 4.1까지 지속됩니다.

### OpenGL ES 3.0

OpenGL ES 3.0 사양은 2012년 8월에 공개되었습니다.
OpenGL ES 3.0은 OpenGL ES 2.0과 하위 호환되므로 응용 프로그램이 응용 프로그램에 점진적으로 새로운 시각적 기능을 추가할 수 있습니다.

OpenGL 4.3은 OpenGL ES 3.0과 완벽한 호환성을 제공합니다.
OpenGL ES 3.0은 WebGL 2.0의 기반이기도합니다.

새로운 기능은 아래와 같습니다.

- 오클루전 쿼리, 변환 피드백, 인스턴스 렌더링 및 4개 이상의 렌더링 대상에 대한 지원을 비롯하여 고급 시각 효과를 가속화할 수 있도록 렌더링 파이프 라인에 대한 여러 가지 향상된 기능을 제공합니다.
- 고품질 ETC2/EAC 텍스처 압축을 표준 기능으로 지원하여 각 플랫폼에 다른 텍스처 세트가 필요하지 않습니다.
- 부동 소수점 텍스처, 3D 텍스처, 깊이 텍스처, 정점 텍스처, NPOT 텍스처, R/RG 텍스처, 불변 텍스처, 2D 배열 텍스처, 스위즐, LOD 및 밉(Mip) 레벨 클램프, 매끄러운 큐브 맵 및 샘플러 객체에 대한 보장된 지원을 포함하여 크게 향상된 텍스처링 기능을 포함합니다.
- 명시적으로 크기가 필요한 텍스처 및 렌더링 버퍼 형식의 광범위한 세트로, 구현 변동성을 줄이고 모바일 앱을 훨씬 쉽게 개발할 수 있습니다.

구글 번역기의 도움을 받아 해석해보았습니다.
내용 상으로는 전반적으로 기능 추가, 성능 향상이 있어보입니다.
(버전이 올라가면 늘 있는 성능 향상인 것 같지만요)
2.0과 하위 호환이 된다는 것이 큰 것으로 보이며 더 깊게 봐야겠지만 렌더링 대상 지원 추가, 렌더링 파이프 라인 기능 향상 등이 눈에 띄네요.
텍스쳐링 기능도 지원 범위가 넓어진 것도 큰 것 같습니다.

성능 테스트 자료가 있으면 좋겠는데.. 없네요.
주로 OpenGL ES와 Vulkan 성능 분석이 많아서 OpenGL ES 2.0과 3.0은 성능 자료는 찾기 힘드네요.
성능 분석에 큰 의미가 없어서 그런 것일 수도 있겠습니다.
(기기에 따라 성능 차이가 많이 나서)

OpenGL ES 버전 차이가 어떤가에 대해 개괄적인 내용을 살펴보았습니다.
렌더링 방식, 텍스처 처리방식, 버퍼 크기등에 대한 차이가 있었네요.

그래픽 엔지니어는 아니어서 자세한 내용은 더 정리하기 힘들지만
다른 좋은 레퍼런스가 있다면 추가해서 들고 오겠습니다.
