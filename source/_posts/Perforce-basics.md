---
title: Perforce Client(P4V) basics
toc: true
date: 2020-01-23 18:53:03
categories:
- Tech
tags:
- Perforce
thumbnail: https://user-images.githubusercontent.com/5077086/72974765-f17c2580-3e12-11ea-8812-98dfb5840866.png
---

## P4V 가이드 #1

갑자기 PM이 Perforce 프로그램인 P4V 가이드를 작성하게 되었는데요. 사실 저는 Git, SVN 정도를 사용해본 경험만 있고 이번에 Perforce를 처음 사용하게 되었습니다.

제가 P4V를 볼 일은 많지 않지만 다른 사용자분들의 P4V 사용을 돕기 위해서 가이드 문서를 작성하다가 한국쪽 가이드 문서가 많지 않아 이렇게 블로그로 정리해보게 되었습니다.

툴 설명이라 엄청나게 큰 팁이 있다기 보다 이런 기능도 있구나, 이런 화면에 이런 기능도 있구나 하는 것을 조금씩 정리해보고 공유해보려 합니다. :)

이번 포스트에서는 접속화면 부터 메인메뉴 화면을 중심으로 다뤄보고 다음 포스트에는 P4V에서 자랑하는 기능들을 중심으로 설명해보려합니다. 시작하겠습니다!

## 접속 화면

P4V를 켜게되면 아래와 같은 화면을 볼 수 있습니다.

![Login](https://user-images.githubusercontent.com/5077086/73133444-030c3a00-406c-11ea-8116-024cd0caa5a2.png)

- 서버 주소, 이름, 워크스페이스를 설치하면서 설정한대로 또는 추가 설정하여 진행할 수 있습니다.
- 워크스페이스(Workspace)는 내가 앞으로 로컬에서 작업할 공간을 의미합니다.
  - 특정 스트림과 맞춰 설정해두고 그 스트림에 수정사항을 제출할 수 있는 공간으로 이해하시면 됩니다.
- Show dialog at startup 옵션을 체크해두면 시작할 때마다 이 창을 볼 수 있습니다.
  - 똑같은 값인데 항상 뜨는 창이 귀찮다면 해당 옵션을 끄고 시작하면됩니다.

## Setting

처음 접속 시에 아래와 같은 화면이 나와 설정이 필요할 경우 참고하세요.
(갑작스러운 윈도우 화면이지만 정보와 버튼 UI 레이아웃은 맥과 동일합니다)

![SSL fingerprint trust](https://user-images.githubusercontent.com/5077086/72976825-a8c66b80-3e16-11ea-8dc9-bdb3c4f50aeb.jpg)

![Encoding check](https://user-images.githubusercontent.com/5077086/72976830-ab28c580-3e16-11ea-91bf-ea0f6155b115.png)

- Trust this fingerprint 체크! → Connect
  - p4 서버 연결시 SSL이 설정되어있을 경우, 확인 절차로 나옵니다. 아닌 경우에는 설정창이 뜨지 않습니다.
  - 이 컴퓨터에서 보안 연결하는 것을 설정하는 작업입니다.
- 드롭다운을 눌러서 서버에 설정된 인코딩에 맞춰 설정합니다.
  - CPC949 또는 UTF-8, UTF-8 (no bom) 등이 있습니다. 자신의 서버에 맞게 설정해주세요.

## 메인 화면

![Main view](https://user-images.githubusercontent.com/5077086/72977344-af091780-3e17-11ea-8fba-5df8378a19a1.png)

- 메인 화면은 처음 실행한 화면과 예시 화면이 다를 수 있습니다.
- 현재 히스토리(History)를 보여주는 영역을 메인 영역으로 정의하고 설명드리겠습니다.
  - 화면 상단에 뷰(**View)** 메뉴를 눌러보면 많은 뷰 메뉴가 있습니다.
  - 모든 뷰 메뉴에 대한 자세한 설명이 필요하다면 [이 링크](https://www.perforce.com/manuals/p4v/Content/P4V/using.navigating.html#Navigating_P4V)를 참고해주세요. (영어 주의)
- 현재 보이는 화면에서 자주보는 메뉴는 다음과 같습니다.
  - History: 왼쪽 트리에서 선택한 디팟(Depot), 스트림, 파일의 히스토리를 볼 수 있습니다.
  - Files: 왼쪽 트리에서 Workspace 탭으로 갔을 때, 각 폴더에 있는 파일 목록을 볼 수 있습니다.
  - Pending: 현재 작업하고자 Checkout한 파일리스트 또는 제출(서밋, Submit)하기 위해 만든 체인지리스트(Changelist)를 관리할 수 있습니다.
  - Submitted: 내가 제출한 체인지리스트의 목록을 볼 수 있습니다.

### History

![History view](https://user-images.githubusercontent.com/5077086/73132469-1238bb00-405f-11ea-8287-7702993a5de6.png)

- 왼쪽 메뉴에서 선택한 항목(디팟, 스트림, 파일)의 히스토리를 볼 수 있습니다.
- Revision / Date Submitted / Submitted By / Description 각 컬럼별로 정렬하여 볼 수 있습니다.
- 브랜치(스트림)에 상관없이 디팟의 히스토리를 보고 싶다면 stream 항목을 눌러서 히스토리를 볼 수 있습니다.
- 왼쪽 메뉴 상단의 필터 버튼을 통해 스트림을 타입별로 골라서 볼 수 있습니다.
  - **mainline 스트림만** 보고 싶다면, **필터 버튼 > Tree Restricted to Stream Type > Mainline**
  - **Development 스트림만** 보고 싶다면, **필터 버튼 > Tree Restricted to Stream Type > Development**
  - **Release 스트림만** 보고 싶다면, **필터 버튼 > Tree Restricted to Stream Type > Release**
  - 필터를 사용하지 않고 모든 스트림을 보는 옵션은 **No Filter** 또는 **All Types** 입니다.
- 저장소의 히스토리만 보고자 한다면, 로컬에 소스를 받을 필요없이 리모트의 히스토리만 볼 수 있습니다.

### Files

![Files view](https://user-images.githubusercontent.com/5077086/73132651-47460d00-4061-11ea-864b-c7318c6e98af.png)

- 왼쪽 메뉴에서 선택한 항목의 하위에 있는 파일들을 볼 수 있습니다.
  - 폴더를 선택할 경우 해당 폴더안에 있는 파일들을 볼 수 있습니다.
  - 파일을 선택하더라도 같은 폴더안에 있는 파일들도 볼 수 있습니다.
- 각 파일 항목 별로 마우스 오른쪽 버튼을 누르면 기능들이 많습니다.
  - Check Out, Mark for Delete, File History 등 사용하고자하는 기능을 사용할 수 있습니다.

### Pending

![Pending view](https://user-images.githubusercontent.com/5077086/73132738-31851780-4062-11ea-8d9f-75b0d0127175.png)

- 현재 보여지는 화면과 가이드를 보고 있는 여러분의 화면은 다를 수 있습니다.
  - 메뉴 상단에 필터가 어떻게 적용되어있냐에 따라 다릅니다.
  - 필터를 어떻게 적용하냐에 따라 다른 사람의 Pending changelist(작업 내용)을 볼 수 있습니다.
- 체크아웃을 하여 작업한 내용을 넣거나 체크아웃 하기 전 미리 체인지리스트를 만들 수 있는 화면입니다.

### Submitted

![Submitted view](https://user-images.githubusercontent.com/5077086/73132781-ee777400-4062-11ea-9e78-b3ddf8e77924.png)

- 기본 필터로는 현재 사용자가 제출한 체인지리스트를 볼 수 있습니다.
  - 필터를 어떻게 적용하냐에 따라 다른 사용자가 제출한 내용도 볼 수 있습니다.
- 각 항목은 마우스 오른쪽 버튼을 클릭하면 상세 내용을 볼 수 있는 메뉴들을 볼 수 있습니다.

# Filter 기능

![Filter](https://user-images.githubusercontent.com/5077086/73132881-7447ef00-4064-11ea-8f15-534bc05b013d.png)

- 내가 원하는 조건에 따른 결과를 볼 수 있도록 하는 필터 기능입니다.
- 위에 메인메뉴에서 있던 Pending, Submitted 등의 메뉴에서 사용할 수 있습니다.
- -/+ 버튼으로 조건을 추가할 수 있습니다.
  - User, Workspace, Files를 조건으로 검색할 수 있습니다.
- **필터 기능은 슬프게도 히스토리(History) 메뉴에는 없습니다. :(**
- 각 필터 항목에 OR / AND 연산을 할 수 있는 쿼리가 지원되지 않습니다.
  - 혹시나 해서 && 나 || AND OR 등 지원되는 것이 없네요. :(
- 자주사용하는 필터는 저장해서 사용할 수 있습니다.
  - 메뉴 상단 필터 버튼 > Save Filter... > 필터 이름입력 > OK

## 검색(Search)

각 메뉴에서 Ctrl + f (Cmd + f)를 누르면 검색할 수 있습니다. 다만 제한조건이 있습니다.

- 히스토리 메뉴에서는 Revision, Submitted By, Description 항목에 있는 내용으로 검색할 수 있습니다.
- 각 Pending, Submitted에서는 설명 메세지, 체인지리스트 값으로 검색할 수 있습니다.
- **다만 한계점은, 지금 리스트에 보이는 만큼에서만 검색됩니다.**
  - 퍼포스는 전체 체인지리스트를 한번에 받아오지 않게 되어있기 때문입니다.
  - 검색 기능은 다소 불편하지만 스크롤을 쭉 내려서 검색하는 것도 방법입니다.

추가적으로 할 수 있는 방법은 HTML Tools를 사용해서 검색 툴을 만드는 것 정도가 있을 수 있겠습니다.

- [https://www.perforce.com/.../enable-html-tools.html](https://www.perforce.com/manuals/p4vjs-ug/Content/P4VJS-UG/enable-html-tools.html)
- 예시 중에 Demo Run Queries 를 참고하면 전체 체인지리스트에서 검색할 수는 있어보입니다.
- 나중에 다른분들도 사용해볼 수 있도록 만든 뒤에 공유해보겠습니다.

# 마무리

회사에서 SVN을 사용하다가 Perforce로 마이그레이션하면서 빠르고 편한 것도 있지만 여러 어려움을 겪고 있는데요. 기존에 검색되던 것들이 쉽게 검색되지 않는 것과 종종 발생하는 대규모 lock 사태 등..

조금씩 사내 시스템에 개선해나가면 Perforce도 쓸만해지지 않을까라는 생각을 하며 다른 사용자분들도 잘 사용하고 계신지 궁금하네요. 다음 포스트에서 더 유익한 정보 가져오겠습니다.

감사합니다.