---
title: Perforce(P4V) bookmark(북마크)
toc: true
date: 2021-02-19 21:49:21
categories:
- Tech
- Program&Service
tags:
- Perforce
---

## Bookmark(북마크)

[P4V Guide: Bookmarks](https://www.perforce.com/manuals/p4v/Content/P4V/using.bookmarks.html#Bookmarking_files)

P4V에는 폴더나 파일에 빠르게 접근할 수 있는 기능인 북마크 기능이 있습니다.
Tools > Bookmarks 메뉴에서 볼 수 있는데요.
(웹 브라우저에서 사용하는 북마크라고 생각하시면 될 것 같네요. 😸)

![](https://www.perforce.com/manuals/p4v/Content/Resources/Images/p4v-add-bookmark-dialog.png)

Name에는 북마크 이름, Location에는 파일이나 폴더의 경로를 입력하고 OK를 누르면 저장됩니다.
shortcut도 저장할 수 있네요. (맥에서는 ^+shift+[1~9 숫자]) 최대 9개의 숏컷을 저장할 수 있습니다.

북마크는 Tools > Bookmarks에서 리스트를 볼 수 있고 Manage Bookmarks 메뉴에서 관리할 수 있습니다.

![](https://www.perforce.com/manuals/p4v/Content/Resources/Images/p4v-manage-bookmarks-dialog.png)

## 짧은 소개 마무리

자주 찾는 폴더 경로나 파일을 빠르게 접근할 수 있는 북마크 기능을 알아보았습니다.
mainline과 특정 스트림을 이동하는 작업이 많을 경우 북마크를 등록하고 숏컷을 이용하여 편하게 이동할 수 있을 것 같아요.
다만, 북마크에는 타입에 따라 이동에 약간의 제한이 있습니다.

- folder: Workspace folder / Depot folder
- file: Workspace file / Depot file

`Workspace folder, file`의 경우 현재 workspace와 맞는 북마크만 보여지고 숏컷을 이용하더라도 `workspace가 일치하지 않으면 이동하지 못합니다.`
이와 달리 `Depot folder, file`은 `현재 workspace와는 상관없이 이동`할 수 있구요.

북마크 기능이 workspace까지 변경되면서 이동하지는 않으나 숏컷만으로도 유용한 기능이긴 한 것 같습니다.
이미 잘알고 사용하시는 분도 있겠지만 사용하고 있지 않다면 한번 사용해보시는 것도 좋겠네요. 😸
