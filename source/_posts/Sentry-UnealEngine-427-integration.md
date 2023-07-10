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

## 설정 상세

- Project Settings > 프로젝트-패키징 > 패키징 > 크래시 리포터 포함에 체크해줍니다. 
- Project Settings > Plugins > Sentry 에서 DSN 값을 설정해줍니다.
    - 가이드 문서에서 Text 블록에 있는 텍스트를 클릭하면 현재 생성해둔 프로젝트들의 DSN 값을 골라서 볼 수 있습니다.
- DSN 설정 후 하단에 있는 Crash Reporter Endpoint도 설정해줍니다.
    - 크래시 리포터를 통해 크래시 덤프 업로드하는 곳을 설정해주는 것입니다.

> DSN, Crash Reporter Endpoint URL은 Sentry 웹페이지에서 프로젝트 > 프로젝트 설정 > SDK SETUP - Client Keys(DSN)에 있습니다

## 설정 후 크래시 테스트

저는 크래시 테스트를 위해 기본 프로젝트 생성 후 아래와 같이 진행했습니다.

1. 기본 프로젝트 생성
2. 파일 > 새로운 C++ 클래스 추가 > Game Mode Base 선택 > Game Mode 클래스(ex. MyGameModeBase class) 추가
3. MyGameModeBase에 콘솔 명령어 함수 작성
4. 에디터에서 월드 세팅 > Game Mode > 게임 모드 오버라이드에서 MyGameModeBase 설정
5. 컴파일 후 프로젝트 패키지하여 프로그램 실행 테스트

### 코드

<script src="https://gist.github.com/pineoc/448834555138ae140775b10611002889.js"></script>

## 크래시 센트리 업로드 확인

프로젝트 패키지로 만들어진 바이너리 실행 후 크래시를 발생시킵니다.
저는 크래시 발생시키는 명령어 이름을 `crashMe`로 지어두었고 콘솔 명령어로 실행하면 아래와 같이 크래시 리포터가 뜨게됩니다.

![크래시 리포터](https://user-images.githubusercontent.com/5077086/250354005-5cde418e-4cc5-4fe8-b14c-bbeb24459f76.png)

"Send and Close"로 크래시 정보를 보내면 센트리에서 크래시 정보를 볼 수 있게됩니다.

![Sentry-이슈 대시보드](https://user-images.githubusercontent.com/5077086/250353644-ffb91ecf-e07e-4923-b7df-5e995c0703ce.png)
![Sentry-이슈 상세](https://user-images.githubusercontent.com/5077086/250353907-2c9740e5-5013-4c92-a736-8c96cb3abcd5.jpg)

## 마무리

이번 포스트에서는 간단히 센트리-언리얼 엔진 설정을 다뤄봤는데 글은 간단했지만..
실제로 크래시를 일으키기 위해 어떻게 해야할지 여러가지 난관이 있었네요.
(언리얼 엔진 에디터에서 처음 빌드해보고 Visual Studio로 연결하는 것도 처음이다보니 좀 걸렸습니다. 😅)
다음 포스트에는 다른 크래시 분석 툴을 설정해보고 포스트 남겨보겠습니다. 감사합니다. 🙏


## 설치중 에러 참고

### ERROR: Could not find NetFxSDK install dir; this will prevent SwarmInterface from installing. Install a version of .NET Framework SDK at 4.6.0 or higher.

- Visual Studio에서 빌드에 필요한 컴포넌트가 설치되어 있지 않아 발생하는 문제.
- .Net 데스크톱 개발, C++를 사용한 데스크톱 개발, 유니버설 Windows 플랫폼 개발 설치

### Plugin build fail

- 플러그인이 소스코드만 포함되어있는 상태라면 Visual Studio 설치가 필요합니다.
- Visual Studio를 설치해주세요.
