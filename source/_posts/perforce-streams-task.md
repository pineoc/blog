---
title: Perforce Stream, task stream / 태스크 스트림
toc: true
date: 2023-05-02 22:30:00
categories:
- Tech
- Program&Service
tags:
- Perforce
---

## Perforce stream: Task stream

예전 포스트에서 스트림을 살펴보았는데요. {% post_link perforce-streams %}
각 스트림 타입별 내용을 한번 정리해보고자 합니다. 😃
이번 포스트에서는 Task stream, 태스크 스트림을 공부해보겠습니다.

가이드 문서: [Working with task streams](https://www.perforce.com/manuals/p4v/Content/P4V/streams.task.html)

## 참고: 스트림 유형(Stream types)

- Mainline: 최상위 스트림으로 메인 브랜치로 볼 수 있습니다.
- Release: 안정적인 소스 상태로 관리하기 위한 스트림으로 주로 안정적인 릴리스를 준비하기 위해 사용하는 스트림입니다.
- Development: 개발이 이뤄지는 피쳐 스트림입니다.
- **Task: 작은 단위의 작업을 할 때 사용할 수 있는 특수한 스트림입니다. 자세한 내용은 [링크](https://www.perforce.com/manuals/p4v/Content/P4V/streams.task.html)를 참고하세요.**
- Virtual: 특정 인원에게 제한된 뷰를 제공하기 위한 스트림입니다. 자세한 내용은 [링크](https://www.perforce.com/manuals/p4v/Content/P4V/streams.virtual.html)를 참고하세요.

## Task stream overview(요약)

먼저 가이드 문서에 있는 내용들을 요약해보겠습니다.

- 태스크 스트림은 `버그 수정`이나 `작은 기능 개발`과 같이 제한된 작업에 적합합니다. 
- 태스크 스트림은 브랜치의 총 파일 수에 비해 적은 수의 파일에 영향을 주는 `가벼운 브랜치`입니다.
- 태스크 스트림은 대개 일시적인 경우가 많으며 변경 사항이 통합되면 삭제되거나 언로드됩니다.
- 태스크 스트림은 리포지토리 메타데이터의 양을 최소한으로 유지하여 `Helix Core Server 성능에 도움`이 될 수 있습니다.
- ⭐각 태스크 스트림에는 고유한 이름이 필요하며, 이 이름은 태스크 스트림이 삭제된 후에도 재사용할 수 없습니다.
  - 따라서 사이트에 사용자-날짜-작업 번호와 같은 명명 규칙이 있는지 관리자에게 문의하세요.
  - 여기서 작업 번호는 이슈 추적 애플리케이션에서 식별자 또는 '작업(job)'을 나타냅니다.

## 다른 스트림들과 다른 태스크 스트림의 예외 사항

- **태스크 스트림에는 상위(부모) 스트림이 필요하지 않습니다.**
  - 따라서 스트림 depot에서 작업하지 않는 사용자도 태스크 스트림을 만들 수 있습니다.
  - 태스크 스트림은 스트림 저장소에 있어야 하지만, 해당 저장소는 태스크 스트림의 보류 장소일 뿐입니다.
  - 사용할 스트림 보관소에 대한 정보는 관리자나 프로젝트 리드에게 문의하세요.
  - 자세한 내용은 [상위 스트림 없이 태스크 스트림 만들기](https://www.perforce.com/manuals/p4v/Content/P4V/streams.task.html#streams.task.create_noparent)를 참조하세요.
- **상위 스트림은 다른 depot에 있을 수 있습니다.**
  - 태스크 스트림은 삭제되거나 언로드될 때까지 디포에 빠르게 누적될 수 있습니다.
  - 프로젝트 보관함을 태스크 스트림으로 어수선하게 만들지 않으려면 관리자나 프로젝트 리더가 특정 스트림 보관함을 태스크 스트림의 전용 보관 장소로 설정할 수 있습니다.
  - 이 경우, 태스크 스트림 저장소에 스트림을 프로젝트 저장소에 있는 상위 스트림의 하위 스트림으로 만들면 됩니다.
  - 태스크 스트림이 다른 디포에 있더라도 부모 디포의 스트림 그래프 보기에 스트림이 표시되는 것을 볼 수 있습니다.
  - 자세한 내용은 [다른 저장소에 태스크 스트림 만들기](https://www.perforce.com/manuals/p4v/Content/P4V/streams.task.html#streams.task.create_diff)를 참조하세요.
- **태스크 스트림은 자식 스트림을 가질 수 없습니다.**
  - 태스크 스트림은 상위 스트림을 다시 지정할 수 없습니다.
  - 하지만 태스크 스트림을 일반 스트림으로 변환하면 해당 일반 스트림에 상위 스트림을 다시 지정할 수 있습니다.

> **💡 태스크 스트림이 다른 스트림과 다른점 💡**
> P4V나 가이드 문서를 확인해보니 태스크 스트림만 unload 할 수 있네요.
> mainline, development, release 스트림은 삭제만 가능하고 Virtual 스트림은 다른 유형의 스트림이니 제외하고 나면 태스크 스트림만 가능합니다.
> 스트림이 많을수록 서버 성능에 영향이 있을 수 있으니 사용하지 않는 스트림의 정보를 unload하고 데이터를 로딩하지 않는 형태로 서버 성능을 관리할 수 있는 형태인 것 같네요.
> 추가로 Unload할 수 있는 것은 워크스페이스인데 퍼포스 서버 쪽에서 관리하는 데이터를 unload해서 서버 성능 관리를 좀 해야하나 봅니다.
> (저희도 workspace, stream 전체 현황 검토해서 정리가 필요하겠네요 ㅎㅎ 😂)

## 정리

정리해보면, 태스크 스트림은 작은 작업, 버그 수정 등을 위한 피쳐 브랜치로 사용할 수 있는 스트림이라고 할 수 있네요.
다른 스트림들에 비해 스위칭 속도가 더 빠르거나 그런 것은 아닌 것 같지만 어떻게 스트림을 생성했냐에 따라 다를 수 있을 것 같습니다.
(스트림 생성시 부모 스트림의 데이터를 그대로 사용하는 설정 등..?)

가이드 문서와 다른 메뉴얼들만 보았을때는 퍼포스 서버 성능 관리를 위한 기능 같아서 작업자들 입장에서 어떤 것들이 좋은지는 더 살펴봐야겠네요.
실제로 스트림간 스위치 성능이 다른지 확인해보고 추가 내용으로 포스트해보겠습니다.

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
