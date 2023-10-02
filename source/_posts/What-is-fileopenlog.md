---
title: "FileOpenLog, FileOpenOrder란?"
date: 2023-10-02 17:00:35
categories:
  - Tech
  - Game
tags:
  - Unreal Engine
  - FileOpenLog
toc: true
thumbnail: 
---
## FileOpenLog, FileOpenOrder

참고 문서: https://docs.unrealengine.com/4.27/ko/Basics/Projects/Packaging/

언리얼 엔진에서 패키지 생성 및 로딩하는 것과 연관이 있는 내용입니다.

참고 문서에서 언급한 내용으로는 아래와 같습니다.

“로드 시간 단축을 위해서는 `.pak 파일` 순서를 잘 지정하는 것이 중요합니다. `.pak 파일` 최적의 순서를 지정하는 데 도움을 드리기 위해, UE4 에서는 데이터 애셋의 필요 순서를 알아내어 더욱 빠른 로딩 패키지를 제작하기 위한 툴 세트가 제공됩니다. 개념적으로, 이 프로세스는 프로파일 주도형 최적화와 비슷합니다.”

언리얼 서밋 세션도 있어서 참고해보면,
https://youtu.be/KJUVH_KzLj8?si=QRG7h2Mim5f0KGOD&t=2135

![](https://user-images.githubusercontent.com/5077086/271898897-068df3eb-ccab-4ae8-8800-0a1d92d20453.png)

테스트 빌드를 실행할 때에 -fileopenlog 파라미터를 적용해서 실행하고 로그 파일을 빌드시 사용하는 것 입니다. (파일은 {project}/Build/WindowsNoEditor/FileOpenOrder/ 에 위치함)

이 최적화는 Disk보다는 Flash Drive에서 효과적이라고 하네요.
(예시: Disk=HDD, Flash Drive=SSD, USB 드라이브)

언리얼 서밋 세션에서 공유한 예시 수치로는 5.9s → 4.6s, 약 23%가 감소한 수치를 보여줬습니다.
로그를 얻기 위해 실제 유저가 플레이하는 것 처럼 플레이하더라도 많은 게임 데이터를 포함해서 플레이를 하기는 어렵기에 어느정도 감안하고 최적화한다고 봐야할 것 같네요.

## 마무리

FileOpenLog라는 용어가 일반적인 용어일 줄 알았는데 실제로 사용하는 곳은 언리얼엔진 정도인 것 같습니다.
파일오픈로그(오더) 용어 그대로 파일이 열리는 순서를 최적화해서 로딩 시간을 개선하는 방법, 방법을 위한 파일 정도로 이해하면 좋을 것 같네요.
