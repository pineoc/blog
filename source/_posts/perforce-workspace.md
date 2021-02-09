---
title: Perforce(P4) Workspace(작업공간)
toc: true
date: 2021-02-10 00:37:45
categories:
- Tech
- Program&Service
tags:
- Perforce
---

## Workspace(작업 공간)?

P4는 workspace을 만들고 그 공간에서 작업(checkout, submit 등)을 합니다.
(말 그대로 작업 공간이니 당연한 말을 하고 있었네요. 🙈)

Perforce 가이드 문서에는 workspace를 아래와 같이 설명하고 있습니다.

> **Workspace**: Helix Core server에서 관리하는 파일의 개정판을 작업하는 워크스테이션의 폴더 또는 디렉토리입니다.

단순하게 보면 작업 공간이긴하나 git과 다른 점은 p4 서버가 내 작업 공간 정보를 가지고 있다는 것 입니다.

![여러 컴퓨터에서 생성한 workspace 리스트](https://user-images.githubusercontent.com/5077086/107389843-7b8c4e80-6b3a-11eb-848d-c839303d098c.png)

위의 화면은 서버에 등록된 workspace를 선택하여 사용할 수 있는 화면입니다.
`Show only workspace available for use on this computer` 옵션을 통해서 현재 컴퓨터에서 만든 workspace를 필터링해서 보고 선택하여 사용할 수 있습니다.

## Workspace를 만들어봅시다

작업을 시작하기 위해 workspace를 만들어보죠. p4v를 실행하면 제일 먼저 아래화면을 보실겁니다.

![](https://user-images.githubusercontent.com/5077086/107391578-2a7d5a00-6b3c-11eb-86c1-396108cf6aa8.png)

이 화면에서 Worspace에 있는 New 버튼을 눌러보면 아래와 같은 화면을 볼 수 있습니다.

![](https://user-images.githubusercontent.com/5077086/107391910-82b45c00-6b3c-11eb-90f0-1cc14dd0651d.png)

이 글을 보는 모든 분들이 같은 화면을 보지는 않겠지만, Workspace name, Stream에 텍스트를 입력해줍니다.
Workspace name은 workspace의 이름이고 Stream은 해당 workspace에 어떤 스트림을 매핑할지 고르는 거에요.
Stream은 Browse해서 찾을 수도 있고, 입력칸에 검색해서 입력할 수 있습니다.
(직접 입력하면 Stream이 정확하게 입력되지 않을 수 있습니다.)