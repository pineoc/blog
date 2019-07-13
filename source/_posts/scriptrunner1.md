---
title: ScriptRunner 소개 1
categories:
  - PM
  - System
date: 2019-04-21 15:45:00
tags:
  - Jira
  - ScriptRunner
toc: true
thumbnail: https://marketplace-cdn.atlassian.com/files/images/396d3521-7734-4137-9a47-d7afedf1ea18.png
---

## ScriptRunner 소개 #1

- **{% post_link scriptrunner1 %}**
- {% post_link scriptrunner2 %}
- {% post_link scriptrunner3 %}
- {% post_link scriptrunner4 %}

업무에서 요즘 많이 사용하는 'ScriptRunner' 라는 플러그인을 소개하려 합니다.
이 포스트에서 다루는 내용은 JIRA 환경을 기준으로 작성되었습니다.
(한국 문서로는 많이 볼 수 없어서 공부 및 소개 겸 포스트 작성합니다.)

## ScriptRunner란

![Adaptavist ScriptRunner](https://scriptrunner.adaptavist.com/latest/images/SR-web-logo.png)

- 메인 페이지: <https://scriptrunner.adaptavist.com/latest/index.html>
- Adaptavist 라는 회사에서 만든 스크립트 플러그인
  - Adaptavist inc: <https://www.adaptavist.com/>
  - ScriptRunner, Test Management, SmartDraw 등 Atlassian 소프트웨어 플러그인 개발사
- JIRA, Confluence, Bitbucket에서 커스텀 스크립트를 사용할 수 있는 플러그인
- 플러그인 설치 시 기본적으로 스크립트 함수, 필드 지원
- 스크립트 언어는 Groovy를 사용

## ScriptRunner 가이드

가이드 문서는 모두 영어로 되어있으며, JIRA Server, JIRA Cloud로 나눠져있습니다.
Server 설치 버전과 Cloud 버전이 달라 기능도 약간씩 다르니 그 부분은 참고하여 사용해야합니다.

- 메인 페이지: <https://scriptrunner.adaptavist.com/latest/index.html>
- Server 버전: <https://scriptrunner.adaptavist.com/latest/jira/quickstart.html>
- Cloud 버전: <http://scriptrunner-docs.connect.adaptavist.com/jiracloud/quickstart.html>

ScriptRunner 플러그인을 처음 시작한다면 다음 자료들을 보면 좋습니다.

- 기본 컨셉: <https://scriptrunner.adaptavist.com/latest/jira/>
- tutorialspoint/Groovy: <https://www.tutorialspoint.com/groovy/index.htm>
- webinar: <https://www.youtube.com/watch?v=ufNACtDxyD8>
- ScriptRunner 소개 영상: <https://www.youtube.com/watch?v=sJa_bFmPoLU>

Adaptavist에서는 따로 교육과정도 있으니 참고하세요.

- <https://learn.adaptavist.com/course-library/getting-started-with-sr4js>
  - 4시간짜리 강좌로 JQL, Built-in Script, Behaviours 등을 배울 수 있습니다.
  - ScriptRunner 강좌는 이 강좌 밖에 없습니다.
- 전체 강좌: <https://learn.adaptavist.com/course-library>
- 가격은 개인 결제시 350$ 이며 러닝 사이트 내에 있는 모든 강좌를 들을 수 있습니다.
  - 결제를 위해 카드 정보까지 다 입력시 계정이 생성되는 것으로 보입니다.
    (포스팅 시 결제까지 진행하지 않아 모르겠습니다.)

## ScriptRunner 스크립트 작성

ScriptRunner 플러그인으로 스크립트를 작성할 수 있는 곳은 JIRA 기준으로 다음과 같습니다.

- Administration &gt; Add-ons &gt; Behaviours
- Administration &gt; Add-ons &gt; ScriptRunner
  - Script Console
  - Built-in Scripts
  - Script Listeners
  - Script Fields
  - REST Endpoints
  - Script Fragments
  - Escalation Services
  - Script JQL Functions

각 메뉴에서 할 수 있는 일을 정리해보겠습니다.

### Behaviours

- <https://scriptrunner.adaptavist.com/5.5.0/jira/behaviours-overview.html>
- 위의 링크를 참고하면 예제를 따라하면서 어떻게 사용해야할지 알 수 있습니다.
- 설명은 다음과 같이 나와있습니다.

behaviours 기능을 통해 관리자는 하나 이상의 behaviours를 만들 수 있습니다. **behaviours**는 주어진 프로젝트 또는 이슈에서 **이슈에 대한 필드가 동작하는 방식**을 정의합니다. 아래는 예시입니다.

#### 예시

- 이슈 화면에 입력된 다른 데이터(즉, 이슈 생성 또는 이슈 전환 중)에 따라 필드를 필수 항목으로 지정.
- 사용자 역할 또는 그룹에 따라 필드를 읽기 전용으로 설정
- 이슈 화면(스크린)이 제출되기 전에 필드 데이터를 서버 측이 검증 수행
- 다른 이슈 화면(스크린) 데이터에 따라 필드 값 설정

<https://scriptrunner.adaptavist.com/5.5.0/jira/behaviours-overview.html#_examples>
링크에서는 예시로 좋은 설명이 1, 2 항목에 있습니다.

1. 이슈 생성 시 기본 Description(설명) 포맷 값 설정
2. Resolved 처리 시 Resolution이 Fixed 일 경우, Fix Version 입력을 꼭 할 수 있도록 스크린 설정
3. Live Editing (실시간 코드 작성)

작성하다보니 내용이 많아졌네요.
ScriptRunner 소개 #2 포스트에서 다음 내용들을 다루겠습니다.
