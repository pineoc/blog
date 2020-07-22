---
title: What is Buildbot
toc: true
date: 2020-07-12 01:02:37
categories:
- Tech
- Program&Service
tags:
- Tool
thumbnail: https://buildbot.net/img/full_logo.svg
---

## 빌드봇(Buildbot)

<https://buildbot.net/>
"The Continuous Integration Framework"
"Python-based continuous integration testing framework"
Jenkins, Circle CI와 같은 CI 프레임워크로 지속적인 통합을 위한 프로그램입니다.

![Buildbot in Action](https://buildbot.net/img/overview.png)

![Buildbot Home - https://buildbot.buildbot.net/#/](https://user-images.githubusercontent.com/5077086/87241980-81666800-c463-11ea-9953-53aa5a7770de.png)

## 빌드봇 기본 설명

기본적으로 Buildbot은 작업 예약 시스템입니다. 작업을 대기하고 필요한 리소스를 사용할 수 있을 때 작업을 실행하며 결과를 보고합니다.
소스 저장소에서 소스를 받아 마스터(master)가 워커(worker)에게 빌드를 요청합니다.

사실 다른 CI 서비스들과 크게 다른 점은 없지만 현재 사용하고 있는 CI 서비스라서 공부 및 소개하는 차원에서 정리해봅니다.
> 다른 자료들을 보면서 어떤 장, 단점이 있는지 참고하면서 공부하려고 했는데 자료가 거의 없네요. 😂
> 빌드봇 공식 문서를 보면서 정리해보고자 합니다. :)

## 빌드봇 Docs 살펴보기

### Introductions

<http://docs.buildbot.net/current/manual/introduction.html>

빌드봇 소개는 기능 소개로 시작되네요.

- run builds on a variety of worker platforms
- arbitrary build process: handles projects using C, Python, whatever
- minimal host requirements: Python and Twisted
- workers can be behind a firewall if they can still do checkout
- status delivery through web page, email, IRC, other protocols
- track builds in progress, provide estimated completion time
- flexible configuration by subclassing generic build process classes
- debug tools to force a new build, submit fake Changes, query worker status
- released under the GPL

> 정리해보면 다음과 같습니다.
> - 다양한 워커 플랫폼으로 빌드할 수 있고, 다양한 언어 프로젝트를 빌드 가능
> - Python, Twisted로 설치 요구사항이 적음
> - 빌드 상태 추적 및 예상 완료 시간 제공
> - 빌드 프로세스 설정과 관련하여 유연하게 설정 가능

현재 빌드봇을 사용하는 이유가 빌드 프로세스 설정을 커스텀하게 할 수 있어서이긴 합니다.
<https://stackshare.io/buildbot>
Stackshare 서비스에서 투표된 내용을 기반으로 보면, 장점으로 "Highly configurable builds"가 1순위네요.
추가로는 "Beautiful waterfall(이쁜 워터폴)", "Hosted internally(내부 설치)"가 있었습니다.

![시스템 구조 오버뷰](http://docs.buildbot.net/current/_images/overview.svg)

앞서 첨부했던 이미지에 있는 내용과 동일한 이미지를 시작으로 시스템 아키텍쳐(구조)에 대한 이야기가 나옵니다.
소스코드 저장소에서 변경사항이 있을 경우 빌드마스터가 이벤트를 받아 워커에 빌드를 요청하고 빌드 상황을 이메일, 웹, 등에서 볼 수 있다는 기본적인 구조를 설명합니다.

워커는 빌드마스터에게 명령을 받고 빌드를 진행하며, 빌드마스터가 코드를 제공하지는 않고 저장소에서 코드를 받아 빌드를 진행합니다.

### Buildmaster Architecture

![buildmaster architecture](http://docs.buildbot.net/current/_images/master.svg)

빌드마스터 구조라고 소개해두었지만, 빌드마스터가 어떻게 워커에게 일을 주는 지에 대해 알 수 있는 그림이네요.
문서 상에 설명되어있는 내용을 기준으로 정리해보겠습니다.

**Change Sources(변경사항들)**
VCS 저장소 내에서 무엇인가 수정될 때마다 변경사항 오브젝트를 생성합니다.
대부분의 `ChangeSource`는 어떤 종류의 후크 스크립트에서 메시지를 받습니다.
일부 소스들은 정기적으로 저장소를 적극적으로 폴링합니다. 모든 `변경사항`은 스케줄러에게 제공됩니다.

**Schedulers(스케쥴러)**
빌드 수행 시기를 결정합니다.
스케쥴러는 `BuildRequest`에 대한 `변경사항`을 수집하고, 이 변경사항은 워커를 사용할 수 있을 때까지 `빌더들`에 전달하기 위해 대기열에 있습니다.

**Builders(빌더)**
각 빌드의 수행 방법을 정확하게 제어합니다(`BuildFactory`에서 구성된 일련의 `BuildSteps`). 각 `빌드`는 단일 워커에서 실행됩니다.

**Status plugins(상태 플러그인)**
HTTP, 메일 및 IRC와 같은 프로토콜을 통해 빌드 결과에 대한 정보를 제공합니다.

> Each Builder is configured with a list of Workers that it will use for its builds. These workers are expected to behave identically: the only reason to use multiple Workers for a single Builder is to provide a measure of load-balancing.

각 `빌더`는 빌드에 사용할 `워커`들의 목록으로 구성됩니다.
이 워커들은 동일하게 작동해야합니다: 단일 `빌더`에 여러 `워커`들을 사용하는 유일한 이유는 로드 밸런싱을 제공하는 것 때문입니다.

### Status Delivery Architecture(상태 전달 아키텍쳐)

![Status](http://docs.buildbot.net/current/_images/status.svg)

가이드 문서상에 있는 내용을 그대로 번역하면서 정리해보겠습니다.

> The buildmaster maintains a central `Status` object, to which various status plugins are connected. Through this `Status` object, a full hierarchy of build status objects can be obtained.

빌드 마스터는 다양한 상태 플러그인이 연결된 중앙 `상태(Status)` 객체를 유지합니다. 이 `상태` 객체를 통해 빌드 상태 객체의 전체 계층을 얻을 수 있습니다.

configuration(구성, 설정) 파일은 활성화된 상태 플러그인을 제어합니다. 각 상태 플러그인은 최상위 상태 객체에 대한 참조를 가져옵니다. 여기에서 각 빌더, 빌드, 단계 및 로그 파일에 대한 정보를 요청할 수 있습니다.
이 on-demand 쿼리 인터페이스는 `html.Waterfall` 플러그인에서 웹 브라우저가 기본 URL에 도달 할 때마다 기본 상태 페이지를 작성하는 데 사용됩니다.

상태 플러그인은 또한 새로운 빌드가 발생할 때 이 상태를 확인(hear)하기 위해 구독(subscribe)할 수 있습니다.
`MailNotifier`는 이를 사용하여 최근에 완료된 각 빌드에 대해 새 이메일 메시지를 작성합니다.

`상태` 객체는 빌드 마스터의 기본 디렉토리에 있는 디스크의 기존 빌드 상태를 기록합니다. 이를 통해 히스토리 빌드에 대한 정보를 리턴할 수 있습니다.

`스케줄러` 및 `빌더`에 해당하는 상태 객체도 있습니다. 이를 통해 상태 플러그인은 예정된 빌드 및 각 워커의 온라인 / 오프라인 상태에 대한 정보를 보고 할 수 있습니다.

이미지를 보면서 정리해보면, 상태 객체 - 빌더 상태 - 빌드 상태 - 단계(step) 상태 - 로그 파일 구조로 상태를 볼 수 있게 구조화되어있습니다.
최상위 상태 객체는 상태 플러그인이 메일로 상태를 알릴 것인지, IRC로 상태를 알릴 것인지 등 정보를 제공합니다.

### Control Flow

가이드 문서에는 "빌드봇에서의 하루" 느낌으로 플로우를 설명합니다.

- 개발자는 일부 소스 코드 변경 사항을 저장소에 커밋합니다. 일종의 훅(hook) 스크립트 또는 커밋 트리거는 구성된 변경 소스 중 하나를 통해 이 변경에 대한 정보를 빌드 마스터에게 보냅니다. 이 알림은 이메일 또는 네트워크 연결을 통해 도착할 수 있습니다 (빌드마스터가 변경 사항을 구독 할 때 시작되거나 커밋 트리거가 `변경 사항`을 빌드마스터에게 푸시 할 때 시작됨). `변경 사항`에는 변경한 사람, 수정된 파일, 변경 사항이 포함된 리비전 및 체크인 코멘트(주석)에 대한 정보가 포함됩니다.
- 빌드마스터는 이 변경 사항을 구성된 모든 스케줄러에 분배합니다. **중요한** 변경 사항으로 인해 "tree-stable-timer"가 시작되고 `변경 사항`이 새 `빌드`로 들어갈 목록에 추가됩니다. 타이머가 만료되면 구성된 각 빌더 세트에서 `빌드`가 시작되어 모두 동일한 소스 코드를 컴파일 / 테스트합니다. 달리 구성하지 않는 한, 모든 `빌드`는 여러 워커에서 병렬로 실행됩니다.
- The Build consists of a series of Steps. Each Step causes some number of commands to be invoked on the remote worker associated with that Builder. The first step is almost always to perform a checkout of the appropriate revision from the same VC system that produced the Change. The rest generally perform a compile and run unit tests. As each Step runs, the worker reports back command output and return status to the buildmaster.
- As the Build runs, status messages like “Build Started”, “Step Started”, “Build Finished”, etc, are published to a collection of Status Targets. One of these targets is usually the HTML Waterfall display, which shows a chronological list of events, and summarizes the results of the most recent build at the top of each column. Developers can periodically check this page to see how their changes have fared. If they see red, they know that they’ve made a mistake and need to fix it. If they see green, they know that they’ve done their duty and don’t need to worry about their change breaking anything.
- If a MailNotifier status target is active, the completion of a build will cause email to be sent to any developers whose Changes were incorporated into this Build. The MailNotifier can be configured to only send mail upon failing builds, or for builds which have just transitioned from passing to failing. Other status targets can provide similar real-time notification via different communication channels, like IRC.
