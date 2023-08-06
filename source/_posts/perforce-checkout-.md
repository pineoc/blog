---
title: Perforce(P4V) 체크아웃, 체크아웃 해제
toc: true
date: 2023-08-06 22:00:45
categories:
- Tech
- Program&Service
tags:
- Perforce
- Tips
---

## 체크아웃(Check Out), 체크아웃 해제(Check out file Revert)

{% post_link Perforce-basics %}

### 체크아웃 방법

<div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666159-55aeb2cd-ee7e-492e-a0c7-c76e7012064c.png" alt="체크아웃 후 파일 오픈!"/>
  </div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666162-0ea18653-ecc6-4849-8e7c-da9b03f0f644.png" alt="체크아웃 후 파일이 열린 모습">
  </div>
</div>

- 체크아웃하려는 파일을 워크스페이스 파일 트리에서 파일을 선택, 오른쪽 버튼으로 체크아웃합니다.
- Check Out, Check Out and Open 메뉴를 통해서 체크아웃할 수 있습니다.

**체크아웃 참고**

![작업할 이미지 파일이 Lock된 상태"](https://user-images.githubusercontent.com/5077086/146666192-f895452b-7bcb-40a3-a2ec-8f4fff278024.png)
![이미 누군가 파일을 체크아웃했다고 합니다](https://user-images.githubusercontent.com/5077086/146666195-61885ec1-2baf-4038-8f17-7ea0d28cb937.png)

- 이미지, 에셋 등 Exclusive file을 체크아웃할 때 다른 작업자가 체크아웃하고 있을 경우 체크아웃할 수 없습니다.
- 작업을 하고자할 경우 현재 진행중인 작업이 마무리되고 체크아웃하여 작업할 수 있습니다.

### 체크아웃 해제

![파일 체크아웃 해제: Revert](https://user-images.githubusercontent.com/5077086/258645362-1454f547-3b34-4d64-88af-58dc54392242.png)

- 체크아웃한 파일들을 더 이상 수정하지 않는다면 **Revert**를 이용하여 체크아웃을 해제할 수 있습니다.
- Changelist에서 마우스 오른쪽 버튼 -> Revert Files 또는 Revert Unchanged Files로 리버트할 수 있습니다.
  - `Revert Files` : Changelist에 있는 모든 파일의 수정을 취소합니다.(리버트합니다)
  - `Revert Unchanged Files` : Changelist에 있는 수정되지 않은 파일을 pending list를 제외합니다. (이것도 리버트라고 볼 수 있겠네요)
- 파일 각각 선택하여 리버트할 수도 있습니다.

![Revert시 변경한 내역이 있는 파일이 있는 경우](https://user-images.githubusercontent.com/5077086/258648658-444d6bc5-6333-4f89-8c3c-d9cbf3e788cf.png)

- 다른 옵션 설정 없이 그냥 리버트해도 상관 없습니다.
- 두번째 옵션(Get the latest revision and then check out all files that were reverted)의 경우 리버트 후 파일들을 최신 데이터로 업데이트한 뒤 체크아웃해줍니다.

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
