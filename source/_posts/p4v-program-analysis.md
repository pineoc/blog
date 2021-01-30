---
title: P4V(Perforce Client) 프로그램 분석기
toc: true
date: 2021-01-26 01:27:20
categories:
- Tech
- Program&Service
tags:
- Perforce
thumbnail: https://user-images.githubusercontent.com/5077086/106361347-ca7afc80-6360-11eb-8afd-d4be861338f8.png
---

## P4V, Perforce 클라이언트

<https://www.perforce.com/products/helix-core-apps/helix-visual-client-p4v>
<https://www.perforce.com/downloads/helix-visual-client-p4v>

![P4V main view](https://www.perforce.com/sites/default/files/image/2017-06/screenshot-p4v-horiz-tab-1.jpg)

앞선 포스트에서 기본 내용을 소개한 것과 연관해서 P4V는 어떻게 만들어졌는지 궁금해져서 확인해보았습니다.

> 사실 git 클라이언트 프로그램은 많은데 "왜 Perforce는 다양한 클라이언트가 없을까?"하는 궁금함이 있었고 프로그램에 뭔가 있지 않을까해서 확인해보게되었네요. 🙈

## 앱(프로그램) 파일 구조 확인 on Mac

![](https://user-images.githubusercontent.com/5077086/106361347-ca7afc80-6360-11eb-8afd-d4be861338f8.png)

Mac에서 p4v를 설치하고 내부 패키지가 어떻게 구성되었는지 확인해보았습니다.
Frameworks에 Qt관련 폴더가 가득한 것을 보니 Qt를 사용해서 개발한 것 같네요.

실제로 패치노트에서도 Qt를 언급하고 있긴합니다. Qt 5버전을 쓰고 있네요.
<https://www.perforce.com/perforce/doc.current/user/p4vnotes.txt>

```
--------------------------------------------------------------------------
Supporting Libraries for 2020.3.1/2059355
    Qt 5.15.1
    OpenSSL1.1.1
    ICU 65.1
    Helix Core C/C++ API 2020.2
--------------------------------------------------------------------------
```

### Qt 프레임워크?

<https://www.qt.io/>

Qt 프레임워크를 간단하게 설명하면, C++로 개발한 프로그램(GUI 포함)을 다양한 플랫폼에서 사용할 수 있도록 개발할 수 있는 프레임워크입니다. 크로스 플랫폼 프레임워크죠 (React Native나 Ionic, Flutter 같은 프레임워크)
다시 P4V 분석으로 돌아가봅니다.

### Qt Webkit, WebEngine을 사용한 웹 렌더링

P4V에는 p4vjs를 통해 웹페이지를 보여주거나 커스텀 HTML을 통해 p4v에서 기본적으로 보여주는 것 외의 것들을 제공할 수 있는데요.

참고 데모: <https://www.perforce.com/manuals/p4vjs-ug/Content/P4VJS-UG/run-demo-mode.html>

Qt에서는 크로미움(Chromium)을 사용한 웹킷으로 HTML을 보여줄 수 있도록 지원하고 있습니다.
이를 이용해서 P4V도 HTML을 보여줄 수 있는 방법을 열어준 것 같네요.

### 더 분석할만한 프로그램 내용

딱 파일 구조랑 사용한 프레임워크 외에는 더 분석할 만한 내용은 보이지 않네요. CLI 정도까지만 간단하게 보겠습니다.
(리버스 엔지니어링까지 할만한 프로그램은 아니라고 생각이 들기도하구요. 😸)

## P4V 외의 P4 CLI(Command Line Interface)

<https://www.perforce.com/manuals/cmdref/Content/CmdRef/Home-cmdref.html>

p4도 당연히 CLI가 존재하고 커맨드라인으로 p4v에서 할 수 있는 것들을 할 수 있습니다.
(커맨드를 잘 다룰 수 있다면, 더 많은 것들을 할 수도 있겠죠)

* [커맨드 리스트](https://www.perforce.com/manuals/cmdref/Content/CmdRef/commands.html)
* [p4 환경 변수](https://www.perforce.com/manuals/cmdref/Content/CmdRef/envars.html)

## 짧은 분석, 공부 마무리

사실 p4v를 사용하면서 뭘로 만들어졌길래 뭔가 안이쁘지? 하고 확인, 정리해보았는데요.
개발툴이라고 생각하고 보면 git 관리툴들이 다 이쁘게 만들어진게 아닐까하는 생각도 들었습니다.

이번에 정리하면서 기본적인 UI 외에 p4vjs로도 뭔가 더 커스텀하게 만들어볼 수 있으니 그걸 쓰면 더 이쁘게 쓸 수 있지 않을까하는 생각도 들었어요. 🤔

p4v를 사용하면서 더 공유할만한 내용이 있다면 또 들고 오겠습니다.
다음 포스트에서 보아요! 😎
