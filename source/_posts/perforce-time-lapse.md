---
title: Perforce(P4V) Time lapse 기능
toc: true
date: 2021-04-30 00:31:40
categories:
- Tech
- Program&Service
tags:
- Perforce
---

## Time-lapse(타입 랩스) 기능?

P4V에는 파일의 변경 내역을 Slider를 이용해서 리비전, 체인지리스트 단위로 볼 수 있는 타입 랩스 기능이 있습니다.

- [Perforce Video Guide: Time lapse view](https://www.perforce.com/video-tutorials/vcs/using-time-lapse-view)
- https://www.perforce.com/manuals/p4v/Content/P4V/advanced_files.timelapse.html

![](https://user-images.githubusercontent.com/5077086/116579937-dbcaa980-a94d-11eb-8d5f-e4413ba2478b.png)

타임랩스 기능을 보는 방법은 간단합니다. 파일에서 오른쪽 버튼을 누르고 Time-lapse View를 누르면 확인하실 수 있습니다.
위 화면은 Time-lapse view의 Single revision 모드의 화면입니다. 파일 리비전 단위로 슬라이드를 움직여 히스토리가 변경되는 것을 볼 수 있습니다.

아래에 있는 내용은 가이드 문서에 있는 Toolbar 설명 테이블 내용을 간단히 정리해보았습니다.

### 타임랩스 뷰 메뉴 설명

| Functions                                                    | Descriptions                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Mode**                                                     | 얼마나 많은 리비전을 보여줄지 결정하는 옵션입니다.<br />- **Single revision**: 한번에 하나의 리비전을 보여줍니다. <br />- **Incremental diffs**: 2개의 인접한 리비전의 변경된 것을 강조해서 보여줍니다. <br />- **Multiple revisions**: 특정 범위 리비전의 변경된 것을 강조해서 보여줍니다. |
| **Content range**                                            | 시작과 끝 리비전을 정의합니다.                               |
| **Scale**                                                    | 시점 단위를 체인지리스트로 볼 것인지, 날짜, 리비전으로 볼 것인지 정의합니다. |
| **User** ![](https://www.perforce.com/manuals/p4v/Content/Images/p4v-tlv-user_12x15.png) | 수정한 유저를 보여줍니다.                                    |
| **Aging** ![](https://www.perforce.com/manuals/p4v/Content/Images/p4v-tlv_aging_16x15.png) | 수정 사항이 얼마나 오래되었는지 색으로 보여줍니다.           |
| **Line numbers** ![](https://www.perforce.com/manuals/p4v/Content/Images/p4v-tlv_linenumbers_15x15.png) | 줄 번호를 보여줍니다.                                        |
| **Lifetimes** ![](https://www.perforce.com/manuals/p4v/Content/Images/p4v-tlv-lifetimes_15x15.png) | 파일에 인접한 텍스트 청크가 얼마나 오래 같이 있었는지 그래픽 너비(width)를 통해 수명을 보여줍니다. |
| **Direct history** ![](https://www.perforce.com/manuals/p4v/Content/Images/p4v-p4v_timelapse_direct_15x15.png) | 브랜치 히스토리를 제외하고 파일 리비전 히스토리를 보여줍니다. |
| **Branch history** ![](https://www.perforce.com/manuals/p4v/Content/Images/p4v-branchhistory_15x15.png) | 브랜치 히스토리(머지, 인테그레이션)를 보여줍니다. 브랜치 정보는 타임라인 밑에 나타납니다. |
| **Originating changelist** ![](https://www.perforce.com/manuals/p4v/Content/Images/p4v-p4v_timelapse_originating_15x15.png) | 각 리비전의 원래 체인지리스트에 대한 정보를 보여줍니다.      |
| **Find** ![](https://www.perforce.com/manuals/p4v/Content/Images/p4merge-find_15x15.png) | 파일에서 텍스트 기반으로 검색한 결과를 보여줍니다.           |
| **Go to line number** ![](https://www.perforce.com/manuals/p4v/Content/Images/p4merge-gotoline_15x15.png) | 지금 보이는 코드 라인을 지정해서 봅니다.                     |
| **Go to Next diff** ![](https://www.perforce.com/manuals/p4v/Content/Images/p4merge-nextdiff_15x15.png) | 다음 변경 사항                                               |
| **Go to Previous diff** ![](https://www.perforce.com/manuals/p4v/Content/Resources/Images/p4merge-prevdiff_15x15.png) | 이전 변경 사항                                               |
| **Line ending** ![](https://www.perforce.com/manuals/p4v/Content/Images/p4merge-lineend_17x15.png) | 줄바꿈 관련 설정                                             |

### Incremental diffs mode

![](https://user-images.githubusercontent.com/5077086/116579933-db321300-a94d-11eb-8a7b-245b677007f2.png)

Incremental diffs 모드는 인접해있는 2개의 리비전의 변화를 볼 수 있는 모드입니다.
현재 리비전과 직전의 리비전의 차이와 어떤 것이 변경되었는지 빠르게 볼 수 있을 것 같네요.
2개의 리비전 정보도 같이 볼 수 있어서 변경 사항을 파악하는데 유용해보입니다.

### Multiple revisions mode

![](https://user-images.githubusercontent.com/5077086/116579918-d79e8c00-a94d-11eb-8ef6-0f0ad90ebe9d.png)

이 모드는 설정한 범위 내의 리비전 변화를 볼 수 있습니다.
특정 범위 내에서 변경 사항을 확인하고 어떤 사람이 어떤 변경을 했는지 집중해서 확인하기에 좋을 것 같네요.

### 이미지 타임랩스 뷰

![](https://user-images.githubusercontent.com/5077086/116586528-8a71e880-a954-11eb-904a-cea3ddf48efe.png)

이미지의 경우 타임랩스 뷰를 통해 변화되는 것을 볼 수 있습니다.

https://www.perforce.com/manuals/p4v/Content/P4V/advanced_files.timelapse_image.html

가이드 문서나 비디오에서도 기능에 대한 스크린샷이 없네요. 😂 
실제 테스트 해보니 이미지 변화를 페이드인/아웃해서 보여줍니다. (이미지가 크면 메모리 많이 먹겠다는 생각이 드네요 ㅎㅎ)
어지간한 이미지 파일 형식은 다 지원하는 것 같습니다.

## 타입랩스 뷰 소개 마무리

타임랩스 뷰 기능에 대해 간단히 살펴보았습니다.
코드 변경된 내용을 확인하는 데에는 좋은 것 같은데 언어에 따라 포맷팅해주지는 못하는 것 같아 아쉽긴하네요. (P4V 기능 대부분 그런 것 같긴하지만 말이죠 😂)

이만 포스트 마칩니다.