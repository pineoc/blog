---
title: Jira Schemes은 무엇일까? (2)
toc: true
date: 2019-12-28 14:15:08
categories:
- PM
- System
tags:
- Jira
thumbnail: https://wac-cdn.atlassian.com/dam/jcr:fa01756d-6dcc-45d1-83ab-696fbfeb074f/Jira-icon-blue.svg?cdnVersion=696
---

## Jira Scheme 시리즈

- {% post_link What-is-Jira-Schemes1 %}
- **{% post_link What-is-Jira-Schemes2 %}**

앞선 1편의 내용 뒤로 남은 스킴들에 대해 알아보는 포스트입니다.
1편에서는 Jira 프로젝트에서 주로 이슈와 관련하여 설정하곤하는 스킴에 대해 이야기해보았습니다.

2편에서는 프로젝트에서는 많이 변경하지 않지만 알아두면 프로젝트 관리에 도움이 될만한 스킴을 이야기해보겠습니다.

## 남은 스킴은 뭐가 남았나요?

- Issue Security Scheme(이슈 보안 스킴)
- Project Permission Scheme(프로젝트 권한 스킴)
- Notification Scheme(노티피케이션/알림 스킴)

남은 스킴은 이렇게 3개 정도가 되겠습니다.
(더 봐야하는 스킴이 남아있을 수 있지만 제가 알고 있는 스킴을 중심으로 정리해보았습니다.)
프로젝트 이슈에 대한 내용보다는 프로젝트 외적인 부분에 대한 내용으로 생각하고 보시면 될 것 같습니다.

## Issue Security Scheme(이슈 보안 스킴)

이슈 보안 스킴은 이슈들에 대해 특정 인원에게 보여주거나 할당할 수 있도록 제한할 수 있는 스킴입니다.
스킴에 있는 보안 레벨(Security level)을 통해 사용자를 제한할 수 있습니다.

프로젝트에 설정되어있는 보안 레벨 스킴은 아래 경로에서 확인할 수 있습니다.
프로젝트 설정 -> Issue Security
대부분은 스킴이 설정되어있지 않을 겁니다. 프로젝트 안에서 특정 티켓들을 안보이게 하거나 할당되지 않게할 수 있는 설정이어서
외부인과 협업 또는 보안상 특별한 이슈가 없다면 사용할 일이 많지 않은 스킴이긴 합니다.

참고 문서: [JIRA Security Level 설정하기 (Reporter와 Assignee만 해당 이슈 보기)](http://confluence.augkorea.org/pages/viewpage.action?pageId=10977319)
위 참고 문서에 잘 설명되어있네요. :)

## Project Permission Scheme(프로젝트 권한 스킴)

프로젝트에서 프로젝트 역할(project role)이나 사용자에 따라 권한을 설정할 수 있는 스킴입니다.

![프로젝트 권한 스킴 화면](https://user-images.githubusercontent.com/5077086/71538752-e9e07280-2973-11ea-9e72-76c43d5c59d1.png)

위 페이지 화면 처럼, 퍼미션이 있고 각 권한을 프로젝트 역할, 그룹, 특정 사용자 등으로 설정할 수 있습니다.
설정에 따라 권한을 가지고 있는 사용자만 프로젝트를 접근하거나 댓글을 달 수 있도록 할 수 있습니다.
설정 가능한 옵션을 좀 더 본다면 아래와 같습니다.

![프로젝트 권한 스킴 수정 화면](https://user-images.githubusercontent.com/5077086/71538779-7c811180-2974-11ea-80a2-56c6ad078d12.png)

위 화면에서도 보실 수 있겠지만 한번 정리해봅니다.

- **프로젝트 역할 (Project Role)**: 현재 Jira에 있는 프로젝트 역할 리스트를 추가할 수 있습니다.
- **응용프로그램 엑세스(Application access)**: 로그인한 사용자 또는 Jira 소프트웨어 사용자 그룹으로 추가할 수 있습니다.
- **그룹(Group)**: Jira에 있는 그룹으로 추가할 수 있습니다.
- **보고자(Reporter)**: 이슈를 생성한 사용자를 추가합니다.
- **단일 사용자(Single user)**: 특정 사용자를 추가합니다.
- **프로젝트 책임자(Project lead)**: 프로젝트 책임자를 추가합니다.
- **현재 담당자(Current assignee)**: 이슈의 담당자를 추가합니다.
- **사용자 정의 필드 값(User custom field value)**: 사용자 타입의 커스텀 필드에 있는 사용자를 추가합니다.
- **그룹 사용자 정의 필드 값(Group custom field value)**: 그룹 사용자 타입의 커스텀 필드에 있는 사용자를 추가합니다.

권한을 추가할 수 있는 사용자 옵션도 많고, 권한 종류도 많습니다.
수정할 수 있는 권한 카테고리는 아래와 같이 정리해볼 수 있을 것 같네요.

- 프로젝트 권한
- 이슈 권한
- 투표자(Vote), 지켜보기(Watch) 권한
- 댓글(Comment) 권한
- 첨부파일(Attachments) 권한
- 시간 추적(Worklog) 권한

## Notification Scheme(노티피케이션/알림 스킴)

알림 스킴은 이슈에서 발생하는 이벤트에 대한 알림 중 어떤 것을 누구에게 보낼 것인지를 설정할 수 있는 스킴입니다.
이슈가 생성되고 변경되었을 때 알림 메일을 받을 것인지 등을 설정할 수 있습니다.

![알림 스킴 화면](https://user-images.githubusercontent.com/5077086/71539130-409d7a80-297b-11ea-879f-1f81cacd3e6c.png)

각 이벤트에 따라 알림을 받을 사용자, 사용자 그룹을 설정할 수 있습니다.
프로젝트 권한 스킴 설정과 비슷하게 알림을 받을 사용자들을 추가할 수 있습니다.
각 알림 항목에 알림을 받을 사용자를 추가할 수 있는 옵션은 다음과 같습니다.

- Current Assignee
- Reporter
- Current User
- Project Lead
- Component Lead
- Single User
- Group
- Project Role
- All Watchers
- User Custom Field Value
- Group Custom Field Value

알림 이벤트는 이슈 생성, 이슈 수정, 이슈 할당, 이슈 해결 부터 댓글 추가, 댓글 업데이트 등이 있어서
필요한 이벤트에 대해 알림이 필요한 사용자들을 추가할 수 있습니다.

## 마무리

스킴 관련한 내용은 2개의 포스트로 마무리할 수 있었네요.
저도 이번에 정리하면서 Jira에 있는 스킴들을 공부할 수 있었어서 좋았고 나중에 활용할 수 있는 방법을 고민할 수 있게된 계기가 되어 좋았습니다.

긴 글 읽어주셔서 감사합니다. :)
