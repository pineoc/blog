---
title: Perforce(P4V) Stream(스트림)
toc: true
date: 2021-06-21 22:30:00
categories:
- Tech
- Program&Service
tags:
- Perforce
---

## Perforce Stream(스트림)?

지난 포스트에서 작업공간(workspace)를 살펴보았는데요. {% post_link perforce-workspace %}
이번에는 작업공간과 연결되는 서버 쪽 작업공간, 스트림을 살펴보겠습니다.
(작업공간보다는 브랜치가 더 익숙한 것 같긴합니다 😸)

가이드 문서: [perforce - about streams](https://www.perforce.com/manuals/p4v/Content/P4V/streams.about.html#About_streams)

### Stream Depot

Git에서 저장소(Repository)와 같은 역할을 하는 Depot입니다.
Depot 내에는 많은 스트림들이 있고 여러 유형의 스트림이 있습니다. 

### 스트림 유형(Stream types)

- Mainline: 최상위 스트림으로 메인 브랜치로 볼 수 있습니다.
- Release: 안정적인 소스 상태로 관리하기 위한 스트림으로 주로 안정적인 릴리스를 준비하기 위해 사용하는 스트림입니다.
- Development: 개발이 이뤄지는 피쳐 스트림입니다.
- Task: 작은 단위의 작업을 할 때 사용할 수 있는 특수한 스트림입니다. 자세한 내용은 [링크](https://www.perforce.com/manuals/p4v/Content/P4V/streams.task.html)를 참고하세요.
- Virtual: 특정 인원에게 제한된 뷰를 제공하기 위한 스트림입니다. 자세한 내용은 [링크](https://www.perforce.com/manuals/p4v/Content/P4V/streams.virtual.html)를 참고하세요.

## 스트림 그래프(Stream Graph)

![](https://www.perforce.com/manuals/p4v/Content/Resources/Images/p4v-streamgraph-noinherit.png)

스트림 그래프를 보면 스트림간의 부모-자식(Parent-child) 관계를 설정할 수 있다는 것을 알 수 있습니다.
이 관계에 따라 코드의 변경 사항을 전파할 수 있습니다. (rebase, merge할 수 있다는 이야기입니다.)

그래프 방향에 맞춰서 머지 다운(merge down), 카피 업(copy up)이라는 액션을 통해 소스를 머지, 리베이스합니다.
가이드 문서에서는 Propagation(전파)라고 표현하고 있습니다.

> 이 전파 방식의 목표는 안정적이지 않은 스트림을 보다 안정적인 부모 또는 자식으로 최신 상태를 유지하여
> 변경 사항이 덜 안정적인 스트림에서 보다 안정적인 스트림으로 전파될 때 덮어쓰지 않도록 하는 것입니다.

가이드 문서에 있는 내용을 가져왔더니 좀 어렵게 설명이 되었네요. 😢
"**스트림을 안정적으로 만들고 유지하는 것**을 계층으로 전파하는 방식을 통해 이뤄질 수 있도록 했다" 정도로 이해하면 될 것 같습니다.

그래프에 있는 이미지를 짧게 살펴보면,

* rel1 : 릴리스 타입의 스트림으로 main1을 통해 머지 다운, 카피업 (전파)합니다
* main1 : 메인라인 타입의 스트림으로 rel1과 전파할 수 있으며 dev1, dev2과 통신(전파)할 수 있습니다.
* dev1, dev2 : 각각 개발 타입의 스트림으로 main1과 전파하며 각자 dev11, dev22와 전파할 수 있습니다.
* dev11, dev22 : 개발 스트림의 개발 스트림으로 main1에는 직접 전파하지 못하고 dev1, dev2를 통해 전파할 수 있습니다.

여기서 각 스트림 노드에 회색이냐, 파란띠가 둘러져있냐는 부모 스트림 상속(Inherit) 유무를 뜻합니다.
파란띠는 noinherit 으로 상속하지 않았다는 표시, 회색 노드는 상속했다는 표시입니다.

상속한 경우 부모 파일을 공유하거나 다른 경로에 맵핑할 수 있습니다. 자세한 내용은 [스트림 뷰 설정](https://www.perforce.com/manuals/p4v/Content/P4V/streams.views.html#Stream_view_configuration)에서 확인할 수 있습니다.
(스트림 뷰 설정도 내용이 많아서 따로 정리해서 공유하겠습니다.)

## 스트림 정리!

짧게 살펴본 스트림 정리해보겠습니다.

1. Perforce에는 Depot(저장소) 하위에 스트림들이 있습니다.
2. **스트림**은 git에서 **브랜치** 와 비슷한 친구로 이해할 수 있습니다.
3. 스트림은 계층 구조를 가질 수 있고 여러가지 타입으로 설정할 수 있습니다.
4. 스트림 간의 코드 전파는 git 브랜치와 다르게 **머지 다운, 카피 업**과 같은 액션으로 코드를 머지하고 싱크합니다.

스트림 정리는 이만 마치고 다음 포스트에서 스트림 뷰 설정과 상속에 대해 공부하고 정리해보겠습니다. 😸

## 다른 Perforce 가이드 문서들

- {% post_link P4V-User-Guide %}
- {% post_link Perforce-basics %}
- {% post_link perforce-bookmark %}
- {% post_link perforce-revision-graph %}
- {% post_link perforce-search %}
- {% post_link perforce-workspace %}
- {% post_link perforce-streams %}
- {% post_link perforce-streams-task %}
- {% post_link perforce-time-lapse %}
