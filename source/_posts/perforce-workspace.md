---
title: Perforce(P4V) Workspace(작업공간) 관리
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

## Workspace 만들기

### 시작 화면에서 Workspace 만들기

작업을 시작하기 위해 workspace를 만들어보죠. p4v를 실행하면 제일 먼저 아래화면을 보실겁니다.

![](https://user-images.githubusercontent.com/5077086/107391578-2a7d5a00-6b3c-11eb-86c1-396108cf6aa8.png)

이 화면에서 Workspace에 있는 New 버튼을 눌러보면 아래와 같은 화면을 볼 수 있습니다.

![](https://user-images.githubusercontent.com/5077086/107391910-82b45c00-6b3c-11eb-90f0-1cc14dd0651d.png)

이 글을 보는 모든 분들이 같은 화면을 보지는 않겠지만, Workspace name, Stream에 텍스트를 입력해줍니다.
Workspace name은 workspace의 이름이고 Stream은 해당 workspace에 어떤 스트림을 매핑할지 고르는 거에요.
Stream은 `Browse`해서 찾을 수도 있고, 입력칸에 검색해서 입력할 수 있습니다.
(직접 입력하면 Stream이 정확하게 입력되지 않을 수 있으니 직접입력하고 자동완성되는 항목을 선택하는 것을 추천합니다.)

이렇게 workspace를 만들고 Open Connection 화면에서 접속을 진행합니다.

### 현재 Workspace에 접속한 상태에서 다른 Workspace 만들기

`시작 화면에서 Workspace 만들기` 방법과 같지만 현재 접속한 화면에서 다른 workspace를 만드는 방법도 있습니다.

* 상단에 있는 메뉴에서 `Connection > New Workspace​`를 선택합니다.
* `Streams tab (오른쪽 탭)`에서 workspace를 만들고자하는 스트림에 `마우스 오른쪽 클릭` 후 `New Workspace`를 선택합니다​.
* `Workspaces tab (오른쪽 탭)` 상단에 `드롭박스 메뉴`를 선택한 뒤에 `New Workspace`를 선택합니다.

위에서 각 New Workspace 메뉴 선택한 뒤에 workspace 만드는 방법은 동일합니다.

## Workspace에서 작업하기

workspace를 만들었으니 작업을 위해 소스들을 가져와야겠죠?
다만, 이 포스트에서는 Get Latest 내용만 간단히 보고 넘어가겠습니다.
(workspace와 관련한 내용을 다루기 위한 포스트니까요 😸)

현재 workspace에 연결된 스트림에 있는 `모든 파일을 싱크(Sync)하고자 한다면` 현재 폴더에서 `Get Latest`를 선택해주시면 됩니다.

![](https://user-images.githubusercontent.com/5077086/107872112-15f9e280-6eeb-11eb-88cc-390eea133176.png)

또는 특별히 필요한 폴더만 싱크하고자 한다면,
오른쪽 탭에서 Depot에 스트림 하위에 필요한 폴더에서 `마우스 오른쪽 클릭`으로 `Get Latest Revision`을 선택하여 원하는 것만 싱크할 수 있습니다.

이후에 수정이 필요한 소스를 Checkout하고 작업한 뒤에 Changelist를 만들고 Submit하면 커밋이 완료됩니다. 👍

> 나중에 changelist, submit까지 흐름을 간단하게 정리해보면 좋겠네요.

## Workspace 이동(Switch)

작업을 하다보면 브랜치를 이동해야하는 경우가 있습니다.
퍼포스에서는 workspace가 곧 스트림에 연결되어있으니 workspace를 이동하여 작업합니다.

![드롭다운 메뉴에서 바로 이동!](https://user-images.githubusercontent.com/5077086/107881071-d69cb780-6f25-11eb-9219-6d426952d2d0.png)

![Switch to Workspace 메뉴를 통해 이동](https://user-images.githubusercontent.com/5077086/107881442-b837bb80-6f27-11eb-80b3-6af3e682bffc.png)

위 예시 스크린샷은 같은 스트림을 보고있는 workspace이지만, 다른 스트림을 바라보는 workspace로도 이동할 수 있습니다.

## Workspace 삭제(delete)

[P4 Guide: Workspace Delete & Unload](https://www.perforce.com/manuals/p4v/Content/P4V/using.workspaces.html#Delete_and_unload_workspaces)

workspace를 삭제하는 방법은 간단합니다.

![](https://user-images.githubusercontent.com/5077086/107891686-93613980-6f63-11eb-895a-e0056196bdc3.png)

1. 삭제하고자 하는 workspace에 작업중인 내용이 있다면 리버트합니다. (pending changelist, shelve가 있다면 revert해줍니다.)
2. View > Workspaces 메뉴에서 Workspaces 탭을 열어줍니다. (이미 열려있다면 해당 탭으로 갑니다)
3. 마우스 오른쪽 클릭을 누른 뒤 삭제합니다.

삭제하고자하는 workspace에 작업중인 내용이 있다면 아래와 같은 오류가 발생할 수 있으니 작업중인 내용이 있는지 확인해보세요.

`Client 'pineoc-feature1' has files opened. To delete the client, revert any opened files and delete any pending changes first. An administrator may specify -f to force the delete of another user's client.`
예시로 삭제해보려했는데 파일 하나가 checkout 되어있어 위와 같은 오류를 볼 수 있었습니다.

> 가이드 문서에 있는 언로드는 제가 테스트하는 workspace에서는 나오지 않아 넘어가겠습니다.

## Workspace 관리 마무리

이렇게 Perforce에서 workspace를 생성하고 이동, 삭제하는 것까지 살펴보았습니다.
사실 더 자세하게 정리하면 이야기할 내용이 많지만 use case 별로 정리를 하고 포스팅을 해봐야겠네요. 😎
