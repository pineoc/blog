---
title: Jira Field & Screen 살펴보기
toc: true
date: 2019-12-28 17:35:13
categories:
- PM
- System
tags:
- Jira
thumbnail: https://wac-cdn.atlassian.com/dam/jcr:fa01756d-6dcc-45d1-83ab-696fbfeb074f/Jira-icon-blue.svg?cdnVersion=696
---

## Intro - Jira에서 필드(Field)와 스크린(Screen)

지난 포스트에서 Jira에서 스킴(Scheme)을 이야기해보았는데요. ({% post_link What-is-Jira-Schemes1 %})
이때 필드 스킴, 스크린 스킴에 대해서 이야기를 하다가 필드와 스크린도 따로 이야기해보는 것이 좋을 것 같아 정리해보려고 합니다!

## 지난번에도 보았던 스크린과 스킴, 필드에 대한 구조도

[Project screens, schemes and fields (EN)](https://confluence.atlassian.com/adminjiraserver/project-screens-schemes-and-fields-938847220.html)
![](https://confluence.atlassian.com/adminjiraserver/files/938847220/938847221/1/1507216023026/fields_diagram.png)

지난 포스트에서도 한번 보았던 다이어그램입니다.
다이어그램을 보면 대략 알 수 있지만 정리해보면 다음과 같을 수 있겠네요.

### 필드 구조 특징

- **필드**는 **스크린**에 들어갑니다.
- **필드 설정**에 따라 필드를 안보이게 하거나, 필수 입력 값으로 설정할 수 있습니다.
  - 특정 필드가 필요하지 않다면 Hide 설정하여 보이지 않게 할 수 있습니다.
  - 특정 필드가 입력이 필요하다면 Required 설정하여 입력을 강제할 수 있습니다.
- **필드 설정**은 **필드 설정 스킴**에서 이슈 타입에 따라 맵핑하여 사용할 수 있습니다.
  - **이슈 타입에 따라 필드 설정을 각각 다르게 설정**할 수 있습니다.
  - **모든 이슈 타입에 대해 같은 필드 설정**을 할 수 있습니다.
- **필드 설정 스킴**은 **프로젝트**에 종속적입니다.

### 스크린 구조 특징

- **스크린**은 **필드**를 가집니다.
- **스크린 스킴**은 이슈의 조작(Operation)에 맞춰 설정할 수 있습니다.
  - 이슈 생성(Create)/수정(Edit)/보기(View)에 따라 각각의 스크린을 만들어 적용할 수 있습니다.
  - **각각의 스크린에 다른 필드들을 설정 가능**하다는 것을 의미합니다.
- **스크린 스킴**은 **이슈 타입 스크린 스킴**에서 이슈 타입에 따라 맵핑하여 사용할 수 있습니다.
  - **이슈 타입에 따라 스크린 스킴을 각각 다르게 설정**할 수 있습니다.
- **이슈 타입 스크린 스킴**은 **프로젝트**에 종속적입니다.

### 워크플로우(Workflow, 흐름) 구조 특징

필드와 스크린 내용에는 설명할 예정은 없었지만 구조도에 있기에 정리해봅니다.

- **워크플로우**에서 상태 간의 트랜지션(이동)에 **스크린**을 맵핑할 수 있습니다.
  - 상태 변경 중에 스크린이 나타나고 특정 값을 변경하는 방식으로 설정이 가능합니다.
- **워크플로우**는 **워크플로우 스킴**에서 이슈 타입에 따라 맵핑하여 사용할 수 있습니다.
  - **이슈 타입에 따라 워크플로우를 각각 다르게 설정**할 수 있습니다.
- **워크플로우 스킴**은 **프로젝트**에 종속적입니다.

구조도에 나온 내용은 이쯤에서 마무리하고 필드와 스크린 설명으로 넘어가겠습니다. :)

## 필드 (Field)

Jira에서 필드란 무엇일까요?
간단하게 생각해보면 이슈에서 필요한 정보를 담기 위한 `변수`라고 볼 수 있을 것 같습니다.
Jira 시스템 상에는 기본적으로 있는 `시스템 필드`가 있고 사용자가 필요시 만들어서 사용할 수 있는 `커스텀 필드`가 있습니다.

### 시스템 필드 (System Field)

Jira에서 기본적으로 제공하는 필드를 의미합니다. 어떻게 보면 시스템 필드라고 부르는게 정확한지는 모르겠네요.
필드들을 볼 수 있는 곳은 Jira 소프트웨어 서포트 페이지 링크로 [Advanced searching - fields reference](https://confluence.atlassian.com/jirasoftwareserver/advanced-searching-fields-reference-939938743.html) 여기서 볼 수 있습니다.
약 38개쯤 되는데요, 하나하나 보기 보다는 위 링크에서 보시면 좋을 것 같습니다. 우리가 주로 보는 필드 몇개만 소개를 해볼게요.

- **Affected version**: 반영된 버전의 의미로 사용할 수 있는 필드입니다. 프로젝트의 Releases에 있는 버전들을 입력할 수 있습니다.
- **Assignee**: 이슈의 담당자를 입력할 수 있는 필드입니다.
- **Component**: 프로젝트에 있는 컴포넌트를 입력할 수 있는 필드입니다.
- **Summary**: 이슈의 제목 필드입니다. [Jira의 텍스트 검색 신텍스](https://confluence.atlassian.com/jirasoftwareserver/search-syntax-for-text-fields-939938747.html)를 사용하여 검색할 수 있습니다.
- **Description**: 이슈의 설명 필드입니다.

이 외에도 많은 필드들이 있는데 각 필드마다 사용할 수 있는 기능(operation) 다릅니다.
예를 들면, Assignee 같은 경우 `WAS` `WAS NOT` `CHANGED` 등을 JQL에서 사용할 수 있습니다.
내가 담당했던 이슈를 찾을때는 `WAS`를 이용해서 찾아볼 수 있겠죠.
`CHANGED`는 변경이 언제 이뤄졌는지, 누가 변경했는지에 대해 쿼리해볼 수 있습니다.

자세한 내용은 [Advanced searching - fields reference](https://confluence.atlassian.com/jirasoftwareserver/advanced-searching-fields-reference-939938743.html) 이 페이지에서 참고하시면 좋을 것 같습니다. :)

### 커스텀 필드 (Custom Field)

커스텀 필드는 말그대로 사용자가 커스텀하게 만들 수 있는 필드를 뜻합니다.
만들 수 있는 필드의 타입은 여러가지가 있겠죠? 텍스트 형식부터 시작해서 사용자를 입력할 수 있거나, 텍스트 박스 등 여러 타입이 있습니다.

**기본 타입(Standard type)**

- **Checkboxes**: 체크박스 필드
- **Date Picker**: 날짜 설정 필드
- **Date Time Picker**: 날짜 + 시간 필드
- **Labels**: 레이블 필드 (입력시 자동완성 기능이 있음)
- **Number Field**: 숫자 입력 필드
- **Radio Buttons**: 라디오 버튼 필드 (하나만 선택 가능한 필드)
- **Select List (cascading)**: 2개로 나눠진 드롭다운 선택 리스트 필드
- **Select List (multiple choices)**: 여러개를 선택할 수 있는 드롭다운 선택 리스트 필드
- **Select List (single choices)**: 한개만 선택할 수 있는 드롭다운 선택 리스트 필드
- **Text Field (multi-line)**: 여러줄 입력할 수 있는 텍스트 필드
- **Text Field (single line)**: 한줄 입력할 수 있는 텍스트 필드
- **URL Field**: URL을 입력할 수 있는 필드 (URL 클릭 가능)
- **User Picker (single user)**: 사용자를 입력할 수 있는 필드

기본 타입 외에도 그룹을 입력할 수 있는 picker, 버전을 입력할 수 있는 picker, 읽을 수만 있는 read only text 필드도 있습니다.
필요한 커스텀 필드를 생성하여 필드 설정(Field Configuration)에 반영한다면 사용할 수 있겠죠?

**주의(Warning)!**
커스텀 필드는 기본적으로 생성될 때 모든 프로젝트의 필드 설정에 추가됩니다.
다른 프로젝트에서는 사용하지 않고 현재 관리하고 있는 프로젝트에서만 사용하고자할 경우 추가 설정해주셔야 합니다.
커스텀 필드 설정 -> Edit Configuration -> Choose applicable context -> Apply to issue under selected projects 옵션으로
생성한 커스텀 필드가 필요한 프로젝트에 반영될 수 있습니다. (다른 프로젝트에 의도하지 않게 필드가 추가되면 프로젝트에 영향을 주기 때문입니다.)

## 스크린 (Screen)

Jira에서 스크린은 이슈를 생성, 수정, 조회하는 모든 화면들을 이야기합니다.
Jira 서포트 문서([Defining a screen](https://confluence.atlassian.com/adminjiraserver/defining-a-screen-938847288.html))에서는 아래와 같이 표현하고 있습니다.

> Screens group all available fields (or a subset of all available fields) defined in Jira applications, and organize them for presentation to a user.

> 스크린은 Jira에 정의된 사용 가능한 모든 필드(또는 사용 가능한 모든 필드의 하위 집합)를 그룹화하고 사용자에게 보여주기 위해 이를 구성한다.

위 내용 정도로 정리해볼 수 있겠네요.
스크린은 앞서 말씀드렸던 이슈 생성/수정/조회에서 사용할 수 있을 뿐만 아니라 워크플로우에서 상태 변경시에도 사용할 수 있도록 설정할 수 있습니다.
추가로 스크린에 탭으로 입력하고자하는 정보들을 정리해서 입력할 수 있도록 설정할 수 있죠.

### 이슈와 스크린

앞서 스크린을 설명할 때에 이슈 생성/수정/조회에서 사용할 수 있다고 말씀드렸었습니다.
스크린 스킴에서 각 동작에 따라 스크린을 설정하는 화면을 보시면 이해가 빠를 것 같습니다.

![Project - Screens](https://user-images.githubusercontent.com/5077086/70859786-2ff10b80-1f5c-11ea-94ac-07b2c451eb01.png)

위 화면 처럼 이슈 마다, 각 **Create issue** / **Edit issue** / **View issue**에 따라 스크린을 따로 만들어서 적용한 것을 볼 수 있습니다.
각 스크린은 다르게 설정할 수도 있고 다를 필요가 없다면 따로 설정할 필요 없이 같은 스크린을 사용해도 됩니다.

![Create issue Screen](https://user-images.githubusercontent.com/5077086/70859936-3ed8bd80-1f5e-11ea-9f9d-edf125bfc2de.png)

필드의 순서 설정도 가능하고, 탭을 추가해서 탭마다 입력하고자 하는 필드를 나눠서 둘 수도 있습니다.

![이렇게도 가능하겠네요 :)](https://confluence.atlassian.com/jirakb/files/874785568/874787137/1/1488529470182/image2017-3-3+16%3A24%3A21.png)

### 워크플로우와 스크린

워크플로우에서도 스크린을 사용할 수 있다고 말씀드렸었습니다. [참고 jira 서포트 페이지:Map a screen to a workflow transition in Jira server](https://confluence.atlassian.com/jirakb/map-a-screen-to-a-workflow-transition-in-jira-server-720634253.html)
아래 그림처럼 상태 변경시에 스크린이 나올 수 있도록 설정할 수 있습니다.

![](https://confluence.atlassian.com/jirakb/files/720634253/720634279/1/1425969251461/resolution_screen_transition.png)

자세한 내용은 위 서포트 페이지에 가보시면 **Solution**에 더 자세하게 나와있으니 참고해보세요!

## 마무리

Jira에서 빼놓을 수 없는 필드와 스크린을 알아보았습니다.
지금 작성해놓고 보니까 스크린의 내용이 약간 부족해보인다는 느낌이 있지만 어느 부분을 추가해야할지 모르겠네요. 향후 추가할 내용이 생긴다면 따로 포스트 추가해보겠습니다.
추후에 현재 프로젝트에서는 어떤 필드를 사용하고 있고 어떻게 스크린을 구성해서 사용하고 있는지 보여드리겠습니다.
긴 글 읽어주셔서 감사합니다. :)
