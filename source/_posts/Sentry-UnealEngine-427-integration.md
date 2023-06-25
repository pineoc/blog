---
title: "Sentry - Uneal Engine 4.27 integration"
toc: true
date: 2023-06-25 11:30:17
categories:
- Tech
- Game
tags:
- Unreal Engine
- Sentry
---

## 준비 사항

⚠️ 프로젝트가 C++ 클래스를 빌드할 수 있는 상태여야 합니다.

> (가이드 문서 내용) Currently, this method is available only for C++ UE projects. Blueprint projects can be converted to a C++ one by adding an empty class using the editor.
> → 현재 이 메서드는 C++ UE 프로젝트에서만 사용할 수 있습니다. 블루프린트 프로젝트는 에디터를 사용하여 빈 클래스를 추가하여 C++ 프로젝트로 변환할 수 있습니다.

C++ 클래스 빌드를 위해서는 Visual Studio 설치가 필요합니다.
관련 구성요소를 설치해야하는데 설치해야하는 것은 다음과 같습니다.

![](https://user-images.githubusercontent.com/5077086/248500526-69a886bc-17c8-4619-923e-6d645afa1121.png)

- .Net 데스크톱 개발, C++를 사용한 데스크톱 개발, 유니버설 Windows 플랫폼 개발

## 설치, 설정 방법

[https://docs.sentry.io/platforms/unreal/](https://docs.sentry.io/platforms/unreal/)
[https://github.com/getsentry/sentry-unreal](https://github.com/getsentry/sentry-unreal)

설치 방법은 간단합니다.

1. Github에서 Sentry-unreal 소스를 받는다.
    1. 4.27 버전 엔진의 경우 [0.5.0 버전](https://github.com/getsentry/sentry-unreal/releases/tag/0.5.0)을 받아야함. 
    2. 5.0 이상 엔진의 경우 최신 버전을 사용할 수 있음 (현재는 0.7.0)
2. 받은 소스를 프로젝트 폴더/Plugins 폴더 하위에 옮긴다.
3. 프로젝트를 실행한다.
    1. 프로젝트 실행시 플러그인을 빌드하겠냐는 팝업이 실행되면 빌드한다
4. 이후 문서 가이드를 참고하여 설정한다
    1. [https://docs.sentry.io/platforms/unreal/#configure](https://docs.sentry.io/platforms/unreal/#configure)

## 설치중 에러 참고

### ERROR: Could not find NetFxSDK install dir; this will prevent SwarmInterface from installing. Install a version of .NET Framework SDK at 4.6.0 or higher.

- Visual Studio에서 빌드에 필요한 컴포넌트가 설치되어 있지 않아 발생하는 문제.
- .Net 데스크톱 개발, C++를 사용한 데스크톱 개발, 유니버설 Windows 플랫폼 개발 설치

### Plugin build fail

- 플러그인이 소스코드만 포함되어있는 상태라면 Visual Studio 설치가 필요합니다.
- Visual Studio를 설치해주세요.
