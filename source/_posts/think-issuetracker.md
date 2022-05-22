---
title: "이슈 트래커(Issue Tracker Jira)에 잘 접근하는 방법 고민 #1"
toc: true
date: 2022-05-21 15:30:17
categories:
- PM
- Work
tags:
- Jira
- PM
- Issue Tracker
thumbnail: https://user-images.githubusercontent.com/5077086/169641123-77d65747-5d29-4a50-ac01-f5c5e9cf8375.jpg
---

![](https://user-images.githubusercontent.com/5077086/169641123-77d65747-5d29-4a50-ac01-f5c5e9cf8375.jpg)

## 방법 연구 목적

Jira에 접근해서 자신이 해야하는 일이 무엇인지 확인하기 어려워하는 분들이나 더 편하게 접근할 수 있는 방법이 있을까 하는 생각이 들었습니다. (갑자기?)
궁극적인 목적은 작업자들이 자신이 해야하는 일을 잘, 빠르고 편리하게 확인하고 일할 수 있는 것이죠.
나에게 할당된 일을 바로 알 수 있는 방법이 있다면 제일 좋을 것 같아 각 작업자의 작업 흐름, 작업 프로그램 등을 확인해봅니다.

### (TMI) 이 글을 정리하게된 계기

[https://youtu.be/xlV82Q-ZmAA](https://youtu.be/xlV82Q-ZmAA)

2021년에 OKKYCON에서 김영재님이 발표해주셨던 **프로덕트 조직의 생산성 높이기** 내용에 감명을 받아서 정리하게되었습니다.
(작년에 본 영상인데 왜 이제야? 라는 생각도 들지만 최근에 동료분들이 내가 어떤 일을 해야하는지에 대해 편하게 접근할 수 있다면 Jira와 친해지고 더 잘 쓸 수 있게되지 않을까했습니다. 😁)

영상에서는 “개발자가 이슈 트래커를 잘 쓴다는 기준”에 대해 다뤄주셨는데요.

- 이슈 트래커 웹에서 적게 열어볼 수록 잘쓰는 것
- 절대 상태를 손으로 바꾸지 않는 것 → (핵심) 커밋 메세지로 상태 변화가 가능한 것

## 작업

게임 개발(PUBG 기준)에 있어서 작업자 카테고리 및 작업 프로그램을 분류해보겠습니다.
일단 PUBG 개발은 Unreal Engine Editor, Perforce/Git 으로 작업하고 소스를 관리하고 있습니다. 

### 엔지니어 Engineer

(코딩 + 블루프린트 작업) Visual Studio (Visual Studio Code), **Unreal Engine Editor**

- 코딩 후 Git 히스토리 정리를 위해 SourceTree, Fork, GitKraken 등 Git GUI를 사용하는 경우도 있음
- PUBG는 소스 컨트롤 시스템을 Perforce와 Gitlab(Git)을 쓰고 있음

### 아티스트 Artist

(애셋 작업) Maya, 3D Max ..., **Unreal Engine Editor**

- 컨셉 아티스트...의 경우 어도비 포토샵 또는 일러스트레이터?
- 어쨌든 실제 게임에 적용되는 애셋들은 언리얼 에디터 통해서 반영되어야하니 커밋 내용을 작성하고 푸시하는 곳은 언리얼 에디터? Perforce?
- (어디가 편할지는 인터뷰와 고민이 필요합니다.)

### 기획자 Designer

(데이터 작업 + 블루프린트 작업 등) Excel, **Unreal Engine Editor**

- 데이터 작업을 엑셀로만 하지는 않고 언리얼 에디터에서 그래프를 수정하는 등 여러 작업이 있음
- 블루프린트에 입력해야하는 데이터, 코드에서 가져다 쓰는 데이터 등 에디터와 에디터 밖에서 작업 가능함

## 작업 프로그램과 Jira 연결

각 작업자분들이 작업을 하는 프로그램에서 Jira 이슈를 볼 수 있는 방법이 있는지부터 확인을 해봐야겠죠?
작업 프로그램 하나하나 관련 플러그인이 있는지 확인해보겠습니다.

| 작업 프로그램 | Jira 연결 프로그램 | 특징/코멘트 |
| --- | --- | --- |
| Visual Studio | [VSJira](https://marketplace.visualstudio.com/items?itemName=farmas.VSJira&ssr=false#overview) | ⚠️ VSJira<br/>- VS 2019에서 동작하지 않는다는 평가가 많네요. (동작하는지 확인 필요) |
| Visual Studio | [CodeStream-vs](https://marketplace.visualstudio.com/items?itemName=CodeStream.codestream-vs) | ✅ CodeStream-vs<br/>- New Relic에서 만든 플러그인으로 VS 2019 버전에서 동작 가능하고 지금도 유지보수가 이뤄지고 있는 플러그인<br/>- 내 이슈를 확인하고 이슈를 바로 만들 수도 있습니다.<br/>- Jira 외에도 다른 서비스 연결이 강력하네요. (슬랙, 팀즈, 트렐로 등)  |
| Visual Studio Code | [Jira and Bitbucket](https://marketplace.visualstudio.com/items?itemName=Atlassian.atlascode) | ✅ Jira and Bitbucket<br/>- 아틀라시안에서 만든 플러그인으로 유지보수 및 여러가지 Jira 기능이 보장되어있습니다.<br/>- 플러그인의 형태로 VS Code에 설치 후 서버 설정 및 계정 설정<br/>- VS Code에서 바로 이슈 내용을 바로 볼 수 있습니다<br/>- VS Code 내에서 필터를 구성해서 내가 보려는 이슈만 골라서 볼 수도 있고요 |
| Unreal Engine Editor | ❌ [Bug-reporter](https://www.unrealengine.com/marketplace/ko/product/bug-reporter)<br>❌ [Bug tracker](https://www.unrealengine.com/marketplace/ko/product/bug-tracker) | ❓ 언리얼 엔진 플러그인으로 있는 것을 찾기 어렵네요<br/>- ❌ Bug-reporter 플러그인은 있는데 $30로 비용이... <br/>- ❌ Bug Tracker 플러그인은 ₩73590... 꽤 비싸네요. 다만 Trello만 지원해서 패스.<br/>없어서 플러그인 만들어서 써야하는 것 같습니다. (다른 회사들도 그냥 만들어쓰는걸까요..?) |
| Perforce(P4V) | ❌ / ⚠️ [jira-perforce 연결](https://www.perforce.com/integrations/jira-and-perforce-integration) | ❌ <br>- P4V에서 바로 Jira 연결하는 플러그인은 따로 없고 커스텀 툴을 개발해서 넣어야합니다.<br>- HTML Tool 또는 Custom Tool을 따로 만들어서 적용해야합니다.<br>- 다른 서비스들에 연결은 할 수 있는데 추가로 구매하고 설정해야하는게 큰일이네요. |

## 고민 1차 정리

일단 각 작업 프로그램별로 Jira 연결 프로그램을 확인해보았는데요.
Visual Studio쪽은 있는데 언리얼 에디터, 퍼포스 쪽은 제대로된 플러그인을 확인할 수 없었네요.

공교롭게도 게임 개발 관련 프로그램에는 Jira 연결 플러그인을 찾기 어려웠... (게임 개발과 이슈 트래커 툴은 친하지 않은 관계일까 싶기도했지만 아니겠죠..?)
물론 언리얼 에디터 쪽에 관련 플러그인이 있지만 Jira를 딱 잘 쓸 수 있게 만들어진 것은 아니어서 애매하다고 생각했습니다.

내부 동료 개발자분들은 어떻게 Jira를 사용하고 있는지, 어떤 방법으로 커밋(submit)할때 jira 이슈를 찾아서 보고 있는지 인터뷰해보고 개선 각을 봐야겠습니다.
개선 방식은 #2 포스트로 찾아올게요 😃
