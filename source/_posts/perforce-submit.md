---
title: Perforce(P4V) 파일 수정부터 submit까지
toc: true
date: 2021-12-19 15:30:45
categories:
- Tech
- Program&Service
tags:
- Perforce
---

## 들어가며

[https://pineoc.github.io/blog/2020/01/23/Perforce-basics/](https://pineoc.github.io/blog/2020/01/23/Perforce-basics/)

앞선 Perforce 베이직 포스트에서는 P4V 클라이언트에서 기본적인 뷰의 구성이나 기능들을 확인해보았습니다.
이번 포스트에서는 워크스페이스를 구성하고 파일을 Submit하고 Depot에 잘 반영되었는지 확인하는 과정을 살펴보려해요.

## 준비 사항

파일 수정 및 submit 전에 작업할 워크스페이스를 설정해주세요.
우선 P4V를 실행합니다.
<div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/73133444-030c3a00-406c-11ea-8116-024cd0caa5a2.png" alt="P4V 실행시 맨처음에 나오는 Open Connection 화면"/>
  </div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666119-84af7925-cf57-43c9-993b-b6badb39a81b.png" alt="계정 생성 팝업">
  </div>
</div>

1. Server는 사용하고자하는 Perforce 서버 주소를 입력합니다.
2. User는 로그인하고자하는 사용자 ID를 입력합니다.
    1. 사용자 ID는 Open Connection 창에서도 새로 만들 수 있을 수 있지만,
    2. 사내 계정 서비스 또는 LDAP 등으로 계정 관리가 되고 있다는 가정하에 ID를 입력하겠습니다.
3. Workspace는 New를 눌러서 새로운 워크스페이스를 만들어보겠습니다.

### Workspace 만들기

<div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666134-0d583e2d-3c1f-4752-9d4d-ff2b99574418.png" alt="Workspace New"/>
  </div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666127-3fe8b229-2d29-425d-83c2-f106a66c8bec.png" alt="Stream Browse 팝업">
  </div>
</div>

1. 앞선 Open Connection 화면에서 Workspace New 버튼을 클릭합니다.
2. Workspace 만드는 화면에서 아래의 값들을 입력, 선택합니다.
    1. Workspace name: 워크스페이스 이름을 입력해주세요. 입력한 값에 따라 Workspace root(경로) 값이 맞춰서 변경됩니다.
    2. Workspace root: 워크스페이스 경로입니다. 경로 변경이 필요할 경우 Browse를 통해 경로를 확인하고 변경할 수 있습니다.
    3. Stream: 워크스페이스와 연결할 Stream을 입력합니다. Browse를 통해 스트림을 찾을 수 있고 입력창에서도 자동완성으로 찾을 수 있습니다.
3. 모두 입력한 뒤에 OK를 누르면 워크스페이스가 생성됩니다.
4. 다른 워크스페이스를 사용하고자할 경우에는 Workspace Browse를 통해 워크스페이스 리스트를 확인할 수 있습니다.
5. 워크스페이스가 생성이 완료되었습니다! 🎉

## Workspace로 가서 작업을 시작해보죠!

이제 워크스페이스도 만들었으니 작업하러 들어가보겠습니다.
처음에 들어가면 아래와 같은 화면을 볼 수 있을거에요. (상세한 탭 구성은 저와 살짝 다를 수 있습니다 😈 )

<div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666149-38d86cfa-6804-4377-b7d6-245418e72fd7.png" alt="Workspace 만들자마자의 상태"/>
  </div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666152-2ead0c8d-211d-45d0-8fa7-8bc8b00c2bdb.png" alt="Get Latest 후의 상태">
  </div>
</div>

왼쪽에 있는 Depot, Workspace 뷰에 작업할 파일 목록이 보여야하는데 처음에는 보이지 않을겁니다.
아직 워크스페이스와 연결된 depot 스트림에서 데이터를 동기화하지 않았기 때문이죠.
**Get Latest**를 눌러서 최신화를 해보면 파일들이 최신 데이터 상태로 동기화될겁니다.

Get Latest를 하면 오른쪽 이미지 처럼 폴더 내에 파일이 생긴 것을 확인하실 수 있습니다.
(설마 Get Latest를 하고 있는데 Perforce 서버가 죽거나 다른 분이 파일을 다 삭제하지 않았다면요 🤡 )

파일 작업을 하려면 Perforce에서는 Check Out하고 작업을 시작해야합니다.
(Check Out을 하지 않고 작업을 시작할 경우 각 OS 파일 시스템에서는 파일 잠금을 해제하라고 경고창이 나올거에요.)

### Code 파일(Non Exclusive File) 작업

<div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666159-55aeb2cd-ee7e-492e-a0c7-c76e7012064c.png" alt="체크아웃 후 파일 오픈!"/>
  </div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666162-0ea18653-ecc6-4849-8e7c-da9b03f0f644.png" alt="체크아웃 후 파일이 열린 모습">
  </div>
</div>

코드, 텍스트 파일 혹은 Non Exclusive 파일 작업의 경우, Check Out 후 바로 작업할 수 있습니다.
Check Out and Open을 눌러주시고 중간에 Select Pending Changelist 창에서 Changelist를 생성합니다.
(이미 작업중인 Changelist에도 추가할 수 있으나 처음 작업한다는 가정하에 Changelist 생성해보겠습니다.)

default Changelist 생성 후 파일이 열립니다. 파일을 수정하고 저장해보았습니다.
Pending 탭에 있는 빨간색 세모 아이콘이 있는 default Changelist에 파일이 있을거에요.

<div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666174-a0f21b05-40f6-4165-8ab3-cfd7462c1b0d.png" alt="그전에 작업된 리비전과 비교하기"/>
  </div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666172-95360d4f-843b-486e-b96b-c75cb42d3d52.png" alt="P4Merge에서 변경된 사항 확인하기">
  </div>
</div>

파일 항목에서 마우스 오른쪽 클릭 후 "Diff against have revision"을 해보면 현재 가지고 Revision과 아직 반영하지 않은 수정한 내역의 변경 사항을 확인할 수 있습니다.
(P4V와 함께 사용되는 P4Merge가 실행될겁니다. P4Merge가 없다면 설치하거나 다른 IDE를 통해서 볼 수 있어요.)

수정한 파일 내용이 문제가 없는 것을 확인했다면 실제 스트림에 반영하기 위해 Changelist를 Submit 합니다.

<div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666177-e1031030-0535-41e0-8b3d-d440b5660684.png" alt="Submit!"/>
  </div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666181-447eb91a-533e-4989-832d-410cd0692610.png" alt="Description을 채워주세요">
  </div>
</div>

1. Pending Changelist 항목에서 마우스 오른쪽 클릭 후 Submit을 선택합니다.
2. Submit Changelist 창에서 Changelist 설명(Description) 항목에 값을 입력합니다.
    1. 설명에는 작업에 대한 상세 내용과 ITS(jira, redmine 등)를 사용한다면 issue 키를 입력합니다.
    2. Perforce job을 사용한다면 job을 입력하기도합니다.
3. 모든 값이 잘 입력되어있다면 Submit!
4. 변경사항(Changelist)이 잘 제출되었는지는 History 또는 Submitted 탭에서 확인할 수 있습니다.

### Asset 파일(Exclusive File) 작업

앞서 코드, 텍스트 파일은 Non Exclusive 파일이어서 체크아웃 후 바로 작업가능한 것으로 말씀드렸습니다.
주로 이미지 파일이나 게임 개발시 사용하는 머터리얼 애셋 등은 대부분의 경우 Exclusive로 설정되어있습니다.

Exclusive로 설정되어있을 경우 내가 작업하고자 A.png 파일을 체크아웃 할 경우,
다른 사람은 내가 체크아웃을 해제할 때까지 A.png 파일을 사용할 수 없습니다.

이미지 파일 또는 애셋 파일들은 여러 사람이 동시 작업할 경우 변경 사항의 컨플릭트를 해결하기 어렵기에
동시 작업을 할 수 없도록 약속을 만들었다고 이해하시면 좋을 것 같습니다.
(SVN, Git lfs에도 있는 파일 Lock 기능입니다.)

<div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666192-f895452b-7bcb-40a3-a2ec-8f4fff278024.png" alt="작업할 이미지 파일이 Lock된 상태"/>
  </div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666195-61885ec1-2baf-4038-8f17-7ea0d28cb937.png" alt="이미 누군가 파일을 체크아웃했다고 합니다">
  </div>
</div>

- pineoc_main3(user1)에서 test1.png 파일을 수정하기 위해 test1.png를 체크아웃합니다.
- pineoc_main(user2)에서도 test1.png 파일을 수정하려고했더니 이미 Lock이 되어있어서 체크아웃할 수 없습니다.
- pineoc_main3(user1)에서 작업이 끝나고 Lock이 풀려야 pineoc_main(user2)에서 작업이 가능합니다.

위 경우는 동일한 사용자의 워크스페이스 뿐만 아니라 다른 사용자의 워크스페이스에서도 체크아웃이 이뤄지면 파일은 잠기게됩니다 (Lock).

이후 작업을 완료하고 Submit하는 과정은 텍스트 수정 작업과 동일합니다.

## 작업된 Changelist 확인하기

워크스페이스에서 체크아웃, 파일 수정, 서밋까지 했으니 잘 반영되었는지 확인해보겠습니다.
보통은 작업 후 잘 반영되었는지 History탭에서 Revision을 확인해봅니다.

왼쪽은 워크스페이스에서의 History, 오른쪽은 리모트 depot 스트림의 History입니다.

<div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666205-ed91e802-521e-4bb8-ac46-f0cb50b9e95f.png" alt="Workspace History"/>
  </div>
  <div style="width: 50%; float: left;">
    <img src="https://user-images.githubusercontent.com/5077086/146666209-af70cf1e-4b35-43d4-867d-aa68bfd88d82.png" alt="Remote Depot History">
  </div>
</div>

서밋한 내용이 정확히 반영되었는지 보고 싶다면 해당 리비전에 마우스 오른쪽 클릭 후 diff를 이용해 확인해볼 수 있습니다.
(이미지도 어떤 변경이 있었는지 알 수 있지만 다른 바이너리 파일들은 안됩니다.)

## 마무리

이렇게 워크스페이스 생성부터 파일 서밋까지 간단하게 정리해보았습니다.
Perforce를 사용하는 곳이 많지 않다보니 하나하나 가이드 문서가 소중한 느낌이긴하네요. 조금조금 팁이 생길 때 마다 포스트 남겨보겠습니다.
이 문서가 하시는 업무에 도움이 되기를 바랍니다. 🙇‍♂️
