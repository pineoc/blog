---
title: Perforce Trigger로 jira key → jira url로 변경해보기
toc: true
date: 2022-07-31 15:31:40
categories:
- Tech
- Program&Service
tags:
- Perforce
---

## 이전 글 돌아보기

P4 trigger 설정하기: [https://pineoc.github.io/blog/2022/01/31/perforce-trigger/](https://pineoc.github.io/blog/2022/01/31/perforce-trigger/)

## 계기

이슈 트래커 연결: [https://pineoc.github.io/blog/2022/05/21/think-issuetracker/](https://pineoc.github.io/blog/2022/05/21/think-issuetracker/)

최근 이슈 트래커(Jira)랑 Perforce를 연결해보려는 고민을 했었습니다.
내부 엔지니어 피드백으로 “P4V에서 History탭을 볼 때, Changelist에 Jira Key가 있다면 Jira 링크로 연결되었으면 좋겠다”고 말씀해주셨어요.

업무할 때 큰 도움이 될 것 같다는 생각에 간단하게 할 수 있는 방법이 있지 않을까 싶어서 방법을 찾아보기 시작했습니다.

제가 생각한 방법은 2가지 정도였습니다.

1. Perforce에 Submit할 때 **P4 Trigger를 이용**해서 Changelist를 서밋할 때, Description을 받아서 Jira Key → Jira URL로 변경해주는 방법
2. **P4 custom HTML Tool을 이용**해서 P4 changelist을 볼 때 Description을 받아 Jira Key → Jira URL로 변경해서 보여주는 방법
3. P4에서 Job 기능을 이용해서 Jira - P4 Job을 연결, Perforce와 Jira 정보 체계를 엮는 방법

이번 글에서는 1번 방법을 고민한 흔적을 공유해보려 합니다.

> 실제로 설정해보시려면 스크립트 구성 ~ 트리거 설정까지 참고하여 따라 진행해보시면 될 것 같습니다. 👍

## 1. P4 submit, populate 할 때 URL 변경해보기

[https://www.perforce.com/manuals/p4sag/Content/P4SAG/scripting.triggers.submits.html](https://www.perforce.com/manuals/p4sag/Content/P4SAG/scripting.triggers.submits.html)

우리의 목적은 Changelist를 서밋할 때, Description을 변경하는 것이니 submit할 때 Perforce가 어떻게 동작하는지 알아야합니다.

![https://www.perforce.com/manuals/p4sag/Content/Resources/Images/p4sag-triggers.png](https://www.perforce.com/manuals/p4sag/Content/Resources/Images/p4sag-triggers.png)

내부 동작을 보니 이벤트는 change-submit → change-content → change-commit로 우리는 change-submit 쯤 Description 정보를 가져와서 변경하면되지 않을까 싶습니다.

각 이벤트 상세는 가이드 문서에 있네요.

- **change-submit**: 변경 목록 생성 후 파일 전송 전에 제출 트리거를 실행합니다. 트리거가 파일 내용에 액세스할 수 없습니다.
- **change-content**: 변경 목록 생성 및 파일 전송 후, 그러나 파일 커밋 전에 제출 트리거를 실행합니다.
- **change-commit**: 변경 목록 생성, 파일 전송 및 변경 목록 커밋 후에 제출 트리거를 실행합니다.

트리거 설정 작업해봅니다.

> 참고: change-submit시 볼 수 있는 changelist는 아직 commit된 CL이 아니기에 pending changelist를 받게됩니다.
[https://www.perforce.com/manuals/p4sag/Content/P4SAG/scripting.triggers.variables.html](https://www.perforce.com/manuals/p4sag/Content/P4SAG/scripting.triggers.variables.html)
A **`change-submit`** trigger is passed the pending changelist number; a **`change-commit`** trigger receives the committed changelist number.

### **스크립트 구성**

스크립트의 실행 순서를 대충 정리해보면 아래와 같겠습니다.

1. change-commit 이벤트를 받아 스크립트를 실행
2. 이벤트와 함께 받은 Changelist에서 Description을 가져온다.
3. Description에서 Jira key를 확인, Description 마지막에 JIRA 항목으로 링크들을 만들어 추가
4. p4 --field Description="3 단계 Description" change -o changelistNum | p4 change -if
5. 끝

### 스크립트 트리거 설정 전 환경 설정

아래 트러블 슈팅 쪽을 보시면 상세내용을 아실 수 있겠지만 Perforce 서버(P4D)쪽 환경 이슈가 있어서 사전 설정이 필요합니다.

- P4D 환경 p4 client 설정
- P4D 환경의 p4 user 권한 확인하여 admin 이상의 권한으로 설정

### 스크립트

<script src="https://gist.github.com/pineoc/1d3696a9a83419821b42cb6100a03901.js"></script>

### 트리거 설정

- admin 권한을 가지고 있는 계정으로 p4 triggers 명령어 실행

```bash
Triggers:
	submit_data_hook_Test change-commit //Test/... "C:\Program Files (x86)\Python38-32\python %//Test/mainline/Tool/P4Triggers/submit_data_hooks.py% %change%"
```

- P4D 환경에 맞춰서 파이썬 경로 설정
- 참고
    - 필요한 파라미터는 [trigger variable](https://www.perforce.com/manuals/p4sag/Content/P4SAG/scripting.triggers.variables.html) 에서 각 이벤트별 사용할 수 있는 파라미터를 확인할 수 있습니다.

## Trouble shootings

### encoding(P4CHARSET) 이슈

python 스크립트에서 p4 description을 가져오는 라인에서 에러가 발생

`'utf-8' codec can't decode byte 0xc0` 에러가 발생했는데 왜 발생했나 봤더니 p4 client charset이 cp949(euc-kr)로 되었는 것으로 확인

→ **✨ `p4 set P4CHARSET=utf8` 로 설정 후 해결!**

### P4 trigger 설정 후 Submit해도 Description 바뀌지 않는 이슈

**Try 1: change-submit 트리거로 스크립트를 실행함**

→ Description이 바뀌지 않았음
→ p4 --field Description … | p4 change -i -u 명령어와 -f 옵션 모두 해보았으나 안됨

**Try 2: change-commit 트리거로 변경하고 스크립트 -f 옵션을 넣음**

→ Description이 바뀌지 않았음

**Try 3: stackoverflow에 물어보자**

→ [https://stackoverflow.com/questions/72506774/p4-triggers-edit-changelist-description-after-submit-on-client](https://stackoverflow.com/questions/72506774/p4-triggers-edit-changelist-description-after-submit-on-client)
→ 방법은 대략 알았지만 에러가 있다! 스크립트 외에 다른 문제가 있을 것 같아 에러 메세지를 더 분석해보았습니다.

### dm-UpdateChangeSpecF 에러

```python
CompletedProcess(args=['p4', 'change', '-if'], returncode=1, stdout=b'', stderr=b"Operation 'dm-UpdateChangeSpecF' failed.\r\nRequired parameter 'data' not set!\r\n")
```

위와 같은 에러가 나는데 가만히 보니 영어만 있는 CL에서는 에러가 발생하지 않음.
한국어, 중국어, 일본어와 같이 아시아권 언어에 또 문제가 있는가보다 😂

관련 이슈 리포트 링크: [https://youtrack.jetbrains.com/issue/IDEA-102104](https://youtrack.jetbrains.com/issue/IDEA-102104)

→ **✨ 스크립트쪽 input 값에 .decode('cp949').encode('utf-8') 해서 강제로 utf8로 변환해주었음. 해결!**

### Client 'test' unknown - use 'client' command to create it. 에러

실제로 P4D(퍼포스 서버)가 동작하는 곳에 트리거 설정 후 테스트 해보았더니
`Client 'test' unknown - use 'client' command to create it.` 라는 에러가 발생함

대충봐도 client가 설정되지 않았으니 client 즉 workspace를 설정해야 CL을 수정할 수 있다는 것으로 보입니다.

→ **✨ P4D 동작하는 환경에 client 설정 후 트리거 동작. 해결!
→ 추가로 P4D 동작하는 환경에 유저 권한도 admin 또는 super 권한을 설정해줘야합니다.**

## 마무리

이번에 트리거 설정하면서 P4D 환경에 설정할 것들도 많고, 스크립트에서도 신경써야할 것이 많은 점을 배웠네요.
사실 파일 검사나 Description 검사정도만 한다면 권한 문제는 없었을텐데 다른 사람이 작업한 설명을 수정하는 것이니 권한이 필요한 트리거 작업이었네요.
실제로 설정해보시려면 스크립트 구성 ~ 트리거 설정까지 따라 진행해보시면 될 것 같습니다.
어렵거나 모호한 부분이 있다면 편하게 질문해주세요! 💪