---
title: Perforce Trigger 설정
toc: true
date: 2022-01-31 00:31:40
categories:
- Tech
- Program&Service
tags:
- Perforce
---

## Perforce Trigger?

퍼포스 시스템에서 변경사항을 서밋하거나 changelist가 생성될 때 등
이벤트에 따라 스크립트를 실행시켜 여러가지 커스터마이즈할 수 있는 기능입니다.

[https://www.perforce.com/manuals/p4sag/Content/P4SAG/chapter.scripting.triggers.html](https://www.perforce.com/manuals/p4sag/Content/P4SAG/chapter.scripting.triggers.html)

가이드 문서는 서버 관리자 가이드 문서로 써있는데 개발환경 개선을 해볼 수 있는 여지가 많은 시스템입니다.
한국어 문서가 많지 않아 이번에 포스트를 작성해보게 되었어요. 😎

## 준비물 / Pre-requisite

- 당연하지만 Perforce(P4V)가 설치되어있어야합니다.
- Perforce 관리자 계정(Admin)이 있어야합니다.
    - 관리자 계정이 아니면 ‘You don't have permission for this operation.’ 라는 오류를 만납니다.
- Perforce 서버(P4D)가 동작하고 있는 환경에 실행하고자하는 스크립트 프로그램이 설치되어있어야합니다.
    - Python, Node, Perl, Ruby 등

## 트리거 설정하기

Trigger 설정을 시작하는 방법은 간단합니다.
p4 로그인이 된 상태에서 cmd(또는 터미널)에서 p4 triggers 커맨드로 트리거 관리 파일을 수정합니다.
수정 후 저장하면 트리거 설정 완료! 자세한 것은 아래에서 더 다뤄볼게요.

### p4 triggers 실행

p4 triggers를 실행하면 컴퓨터에 설정한 텍스트 수정 프로그램으로 트리거 설정 파일이 열립니다.
아래와 같은 내용을 보실 수 있을거에요.

```makefile
# Perforce Submit and Form Validating Trigger Specifications.
#
#  Triggers:	a list of triggers; one per line. Each trigger line must be
#	indented with spaces or tabs in the form. Each line has four
#	elements:
#
#  	Name:   The name of the trigger.
#
# Type:   'archive'	  external archive access triggers
#   'bgtask    '      server-side user processes
#   'auth-check'      check authentication trigger
#   'auth-check-sso'  sso check authentication trigger
#   'auth-set'        set authentication trigger
#   'change-submit'   pre-submit triggers
#   'change-content'  modify content submit triggers
#   'change-commit'   post-submit triggers
# ...
#
#  For example,
#
#   Triggers:
#       cscheck change-submit //depot/... "cmd %changelist%"
#       no-oblits command pre-user-obliterate fail
#       mkspec form-out client "%quote%//trig/scr.pl%quote%"
#       daily_verify bgtask unset "verify.pl"
#
# See 'p4 help triggers' for more information about triggers.

Triggers:
    submit_data_hook_Test change-commit //Test/... "C:\Program Files (x86)\Python38-32\python %//Test/mainline/Tool/P4Triggers/submit_data_hooks.py% %change%"
```

파일에는 트리거에 대한 설명 주석과 이벤트 타입, 트리거 예시가 있습니다.
제가 설정한 트리거는 아래 4개 정도를 사용하고 있고 모두 change-commit 이벤트를 트리거하고 있습니다.

### 설정할 트리거 이벤트 고르기

앞서 파일에서 보실 수 있듯이 트리거할 수 있는 이벤트가 많습니다.
하나하나 알아보기에는 많아서 저는 어떤 것들을 사용하는지 + 가이드 문서를 공유해드릴게요.

가이드 문서: [https://www.perforce.com/manuals/p4sag/Content/P4SAG/chapter.scripting.triggers.html](https://www.perforce.com/manuals/p4sag/Content/P4SAG/chapter.scripting.triggers.html)

포스트 시작할때에도 공유드렸던 가이드 문서인데 하위에 submit, populate, push, fetch 등의 이벤트에 대한 정의를 보실 수 있습니다. 예시도 같이 있으니 참고하면 좋을 것 같습니다.

제가 설정한 트리거를 설명드리면, 주로 `change-commit` 이벤트를 트리거에 사용하고 있습니다.
**change-commit은 changelist가 서버에 커밋되어 저장될 경우 트리거되는 이벤트입니다.**

> 상세 설명: change-commit trigger guide [Perforce guide docs](https://www.perforce.com/manuals/p4sag/Content/P4SAG/scripting.triggers.submits.commit.html)

`change-commit` 이벤트 외에도 changelist 만들때 description 템플릿 폼 적용을 위해 `form-out` 이벤트를 사용해서 만들 수도 있습니다.

> form-out trigger guide: [Perforce guide docs](https://www.perforce.com/manuals/p4sag/Content/P4SAG/scripting.triggers.forms.out.html)
가이드 문서에서는 기본 클라이언트 워크스페이스 뷰를 설정하는 스크립트를 다뤘네요.

### 스크립트 작성

[Submit event trigger 문서](https://www.perforce.com/manuals/p4sag/Content/P4SAG/scripting.triggers.submits.commit.html) 가이드 문서 예시로는 쉘스크립트로 “체인지리스트가 서밋될 경우 파일을 수정했던 사용자들에게 이메일로 수정 사항을 공유”하는 스크립트를 보여주고 있네요.

python, node, perl 등 그 외의 스크립트를 사용하고자할 경우, 프로그램 경로를 잘 맞춰서 설정할 수 있습니다.
제가 사용하고 있는 스크립트는 요렇게 생겼습니다.
스크립트 목적은 작업된 changelist 내역이 슬랙 채널 통해서 공유되도록 하는 것입니다.

<script src="[https://gist.github.com/pineoc/588537cef8dba9902205e5c1cc334c51.js](https://gist.github.com/pineoc/588537cef8dba9902205e5c1cc334c51.js)"></script>

자세한 내용은 위 스크립트를 참고해보세요 😁

### 이벤트에 맞는 스크립트 설정

change-commit(서밋 완료) 이벤트에 맞춰 스크립트가 실행되도록 트리거를 설정해보았습니다.
이벤트 트리거가 발생되어 스크립트를 실행할 수 있도록 `프로그램 경로 + 스크립트 + 파라미터` 를 아래와 같이 입력합니다.

1. 프로그램 경로는 P4D 실행되고 있는 경로에서 프로그램이 설치된 경로를 입력
2. 스크립트 경로는 보통 Perforce에서 스크립트를 관리하니 경로에 맞춰 입력
3. 필요한 파라미터를 입력해줍니다.
    1. 필요한 파라미터는 [trigger variable](https://www.perforce.com/manuals/p4sag/Content/P4SAG/scripting.triggers.variables.html) 에서 각 이벤트별 사용할 수 있는 파라미터를 확인할 수 있습니다.

```makefile
# p4 triggers comments ...
Triggers:
	submit_data_hook_Test change-commit //Test/... "C:\Program Files (x86)\Python38-32\python %//Test/mainline/Tool/P4Triggers/submit_data_hooks.py% %change%"
```

### 설정 완료!

위와 같이 트리거 설정 파일을 수정, 저장하고나면 트리거 설정을 완료됩니다.

## 트리거 설정 소개 마무리

설정과 관련해서 간단하게 소개해보았고 제가 설정해서 사용하고 있는 스크립트도 공유드려보았습니다. 간단하게 수정된 사항이 발생할 경우 슬랙으로 정보를 공유하는 방식은 응용할 것이 많아보이니 참고해서 설정해보시면 좋을 것 같네요. 💪
