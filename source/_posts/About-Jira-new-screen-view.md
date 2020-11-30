---
title: About Jira new screen view
toc: true
date: 2020-11-29 15:03:07
categories:
- PM
- System
tags:
- Jira
---

## 새로운 Jira 이슈 뷰 소개

- [What is the new Jira issue view?](https://support.atlassian.com/jira-core-cloud/docs/what-is-the-new-jira-issue-view/)
- [🎥 Jira Software: New Issue View - Demo Den - Nov 2020](https://www.youtube.com/watch?v=KjrY20C2yjI)

2021년 3월 31부터 변경될 Jira Cloud 이슈 뷰의 소개 글을 번역, 정리해보는 글입니다.
새로운 뷰에서는 어떤 것들이 달라지는지, 쓱 살펴보겠습니다.

### 뭐가 바뀌나요?

![새로운 issue view](https://images.ctfassets.net/zsv3d0ugroxu/JTMuqOq0jyvL7IjcZJ1UK/f49f36bbe0188726082beb65853c1905/bento_annotated__1_.png)

1. **Quick-add buttons**: subtasks, 첨부 파일을 추가하거나 이슈 링크 등 퀵 버튼이 추가되었습니다.
2. **Transition issues**: 워크플로우 버튼이 하나로 통합되어 드롭다운으로 한눈에 보여질 수 있도록 변경되었습니다.
3. **Watch, vote, and more actions**: 지켜보기, 투표, 좋아요 등 액션 버튼이 위로 모이게되었습니다.
4. **Pinned fields**: 자신에게 중요한 필드를 모아서 볼 수 있는 핀(먼저보기) 필드를 설정할 수 있게되었습니다.
5. **More fields**: "Show more" 버튼을 통해 다른 필드를 볼 수 있도록 변경되었습니다. (담당자, 레이블 등)
6. **Configure issue layout**: 필드를 이동하거나 숨기거나 설정할 수 있습니다.
7. **Activity section**: 댓글 창이 항상 떠있게 변경되어 언제든지 댓글을 입력할 수 있게되었습니다.
8. **Attachments**: 첨부 파일 목록을 한번에 받을 수 있게되었네요.
9. **Flexible layout**: 필드를 오른쪽/왼쪽에 놓을지 설정할 수 있게되었습니다.

### 핵심 기능

#### 한 스크린에서 확인하고 수정

![](https://images.ctfassets.net/zsv3d0ugroxu/3MYUATd5pvAxuIyLqE0JIC/1fc26864b61eb8213f83f9af8796f836/JSD_Cloud_-_Inline_edit_fields_in_issue_view)

새로운 이슈 뷰에서는 view 스크린과 edit 스크린이 통합되어 한 화면에서 정보를 확인, 수정, 트랜지션 모두 가능하게되었습니다.

#### 중요한 필드는 핀(Pin)!

![](https://images.ctfassets.net/zsv3d0ugroxu/6PajiA56E9L0WOdyqo7lkY/579a0cbd598fd1081d341db682cd71c5/bento_pinnedfields__3_.png)

이슈 필드 중 중요한 필드를 Pin하여 이슈 정보 화면 상단에서 볼 수 있게되었습니다.

#### 이슈에 빠르게 연관 컨텐츠 추가

![](https://images.ctfassets.net/zsv3d0ugroxu/3MMLf96TbBwRPUoefh8s7n/6103c6989662ead69e39e469708d1477/bento_weblinks)

첨부 파일을 추가하거나 서브태스크 추가, 링크 추가 등을 할 수 있는 퀵 버튼이 생겼습니다.

#### 트랜지션 단순화

![](https://images.ctfassets.net/zsv3d0ugroxu/6sNxS4aguSE4rFM1Sz4f9F/9a5ace815bfd1dc0b47d3cff8db1c5e7/Workflow_status_dropdown_when_a_status_is_selected)

워크플로우 스탭에 따라 버튼이 여러개 생기는 방식이 아닌 하나의 드롭다운에서 트랜지션 할 수 있도록 변경되었습니다.

> 이 변화가 좋은지는 모르겠지만 변경되면서 다음 상태 버튼이 바로 보이지 않아 약간의 불편함이 있을 것 같긴하네요.

#### 어디서든 댓글 작성 가능!

![](https://images.ctfassets.net/zsv3d0ugroxu/3WfysutrGuQnLMSb9noFOa/02649a20491206d5f9a611330771a061/screenshot_Comment_bar)

댓글 창이 아래에 항상 보이게되어 스크롤을 내리지 않고 댓글을 바로 작성할 수 있도록 변경되었네요. 👍

#### 첨부 파일 기능 개선

![](https://images.ctfassets.net/zsv3d0ugroxu/1GLDQ5ChrmLmXAwdi2vam0/28889c8e338b5077069049533b592182/bento_attachmentslistview__1_)

첨부 파일을 리스트로 보는 것, 미리보기 리스트(strip view) 화면이 개선되었습니다.

#### 댓글/워크로그 링크 복사

![](https://images.ctfassets.net/zsv3d0ugroxu/1g4wqhRO88xgHhZ4M0y92D/86973cfc61f72226997d963f4b9d4b8a/bento_permalinks)

댓글이나 워크로그 내용을 바로 복사 붙여넣기 할 수 있는 기능이 추가되었네요.

#### New Atlassian editor (with markdown)

![](https://images.ctfassets.net/zsv3d0ugroxu/1LrLSHewnNbCwtU4s8JBzM/ad0d08745ac9375101f5363b271dd61d/screenshot_TextEditor_Core_JSW)

기존에는 h1, h2와 같은 매크로를 이용해서 렌더링 되었는데 마크다운 형식이 보일 수 있도록 변경된다고 합니다.

#### Show more

![](https://images.ctfassets.net/zsv3d0ugroxu/3C2LlpFC9tzR1L6WyLOXrK/c8bd081d6539a01d7342bab52170683c/screenshot_issueShowMoreAndConfigure)

Show more 버튼을 눌러야 보이는 필드들에 대해 설정할 수 있게되었습니다.

> 많은 필드들이 show more 항목으로 들어가서 바로 보기 어려워질 수도 있겠다는 생각이 들지만...
> 버튼 하나 누르면 보이긴해서 약간의 불편함이 추가되지 않을까 싶긴하네요.

### 향후 개선

향후 개선할 내용은 아래와 같습니다.

- **Issue layout**: 필드를 찾기 쉽고 보기 쉽게 이슈 레이아웃을 개선합니다.
- **Performance**: 새로운 이슈 뷰의 성능이 이전 뷰에 도달하고 능가하도록 개선합니다.
- **Additional features**: 기존 뷰에 있던 기능들을 가져옵니다. 투표, 서브태스크 시간 추정, 남은 시간 필드 업데이트 등

## 새로운 이슈 뷰 내용 정리 소감

새로운 이슈 뷰에 대해 정리해보면서 느낀점은... 차세대 프로젝트로 다 넘기고 싶어하는 것 같다는 느낌을 받았습니다.
저는 개인 공부나 일을 정리하는데 차세대 프로젝트를 사용하고 있는데 새로운 이슈 뷰가 낯설지 않았는데요.
변경되는 방향을 보았는데 차세대 프로젝트 이슈 뷰와 같아서 흐으으으음 했습니다. 😂

Atlassian 소프트웨어 개발 방식이 점차 클라우드, 단일 UX 개발 방향으로 가는 것 같네요.
(지난번에 {% post_link Atlassian-Jira-Clound %} 포스트와 연관이 있어보입니다.)

뭐 차세대 프로젝트 사용하면서 별다른 불편함은 없었는데 개인 혼자 사용하는 것과 많은 팀원들과 사용할 때는 어떤 어려움이 있을지 모르겠네요. 🤔

차차 개선되는 것을 지켜봐야겠습니다. 다음 포스트에서 뵈어요! 🙏
