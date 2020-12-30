---
title: P4V 소개 - 기본 개념 및 Cheat Sheet
toc: true
date: 2020-12-30 13:33:55
categories:
- Tech
- Program&Service
tags:
- Perforce
thumbnail: https://user-images.githubusercontent.com/5077086/72974765-f17c2580-3e12-11ea-8812-98dfb5840866.png
---

## P4V, Helix Visual Client 소개

전에 작성했던 P4V 가이드 글 외에도 Perforce를 참고할만한 내용이 많지 않아 가이드 문서를 번역해보고 알아보는 포스트를 작성해보고자 합니다.

> 전에 작성했던 기본 가이드: {% post_link Perforce-basics %}

그중에 P4V, Helix(Perforce) 비주얼 클라이언트 소개 글을 정리해보고자 합니다.
각 기능에 대한 번역 및 소개들도 차차 포스팅해보겠습니다.
(대부분의 사람들이 주로 쓰는 프로그램이 비주얼 클라이언트일테니까요. 😸)

## Basic concepts (기본 개념)

<!-- The Helix Core server is an enterprise version management tool that you can use to manage source files and other documents, such as multiple revisions of a manual, web pages, or operating system administration files. The files managed by the Helix Core server reside in a depot. To work on files, you open the files and edit them in your workspace. When you’re done, you submit changed files to the depot using a changelist. The depot keeps track of all of the current and previous revisions of a file. -->

Helix Core 서버는 여러 버전의 매뉴얼, 웹 페이지 또는 운영 체제 관리 파일과 같은 소스 파일 및 기타 문서를 관리하는 데 사용할 수 있는 엔터프라이즈 버전 관리 도구입니다.
Helix Core 서버에서 관리하는 파일은 `저장소(depot)`에 있습니다.
파일 작업을 하려면 파일을 열고 `작업 공간(workspace)`에서 편집합니다.
완료되면 `변경 목록(changelist)`을 사용하여 변경된 파일을 저장소에 `제출(submit)`합니다.
저장소는 파일의 모든 현재 및 이전 개정을 추적합니다.

![P4V Diagram](https://www.perforce.com/manuals/p4v/Content/Resources/Images/p4v-diagram-1-v2.png)

<!-- - Workspace: folders or directories on your workstation where you work on revisions of files that are managed by the Helix Core server.
- Helix Core app: P4V (or another Helix Core application, like the command-line client or P4VS, the Helix Plugin for Visual Studio), running on your workstation, which makes requests from the Helix Core server and delivers the results of those requests (files, status information, and so on) to you.
- Helix Core server or Helix server: the program that responds to requests from Helix Core applications, maintains depot files, and tracks the state of workspaces.
- Depot: a file repository hosted by the Helix server. It contains all existing versions of all files ever submitted. The Helix server can host multiple depots, but the examples in this guide show a single depot. -->

> 각 용어는 번역하지 않고 그대로 두겠습니다.

- **Workspace**: Helix Core server에서 관리하는 파일의 개정판을 작업하는 워크스테이션의 폴더 또는 디렉토리입니다.
- **Helix Core app**: 워크스테이션에서 실행되는 P4V (또는 명령 줄 클라이언트 또는 P4VS, Visual Studio 용 Helix 플러그인과 같은 다른 Helix Core 애플리케이션)는 Helix Core 서버로 요청하고 해당 요청의 결과 (파일, 상태 정보 등)를 제공합니다.
- **Helix Core server or Helix server**: Helix Core app의 요청에 응답하고, Depot 파일을 유지하고, Workspace의 상태를 추적하는 프로그램입니다.
- **Depot**: Helix server에서 호스팅하는 파일 저장소입니다. 여기에는 제출된 모든 파일의 모든 기존 버전이 포함됩니다. Helix server는 여러 저장소를 호스팅 할 수 있지만 이 가이드의 예에서는 단일 저장소를 보여줍니다.

## P4V Cheat Sheet

P4V 치트 시트가 있긴한데 많이 유용한지는 모르겠습니다.
프린트해놓고 옆에 두고 쓰거나하면 좋을지는 모르겠네요. 😂

Cheat Sheet 원본: [P4V Cheat Sheet (EN)](https://www.perforce.com/sites/default/files/files/2017-10/perforce-helix-cheatsheet.pdf)

![](https://user-images.githubusercontent.com/5077086/103333204-6ee2f800-4ab0-11eb-8a53-9eef85846525.png)

아이콘 모양이나 파일 상태, 스트림 타입에 대해서는 옆에두고 보면 좋을 것 같긴합니다. 😸
(익숙해지기 전까지는요)
치트 시트를 번역해보고 싶었는데 PDF다 보니 이미지를 추출하기도 힘들어서 나중에 기회가 된다면 번역해보겠습니다.

다음 포스트는 스트림과 관련한 내용을 쓸까 싶습니다.
정리되는대로 포스팅해보겠습니다.

감사합니다.
