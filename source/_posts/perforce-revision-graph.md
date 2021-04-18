---
title: Perforce(P4V) Revision Graph(리비전 그래프) 기능
toc: true
date: 2021-04-18 23:40:50
categories:
- Tech
- Program&Service
tags:
- Perforce
---

## P4V 리비전 그래프 기능

[P4V User Guide: Viewing codeline history in the revision graph](https://www.perforce.com/manuals/p4v/Content/P4V/advanced_files.revgraph.html#Viewing_codeline_history_in_the_revision_graph)

![](https://user-images.githubusercontent.com/5077086/115149985-6c2d0280-a0a1-11eb-81f9-737d5ae911d3.png)

P4V의 리비전 그래프 기능은 파일이 어떻게 변경되어왔는지 한눈에 볼 수 있는 기능입니다.
리비전 그래프 기능은 파일이나 폴더를 선택하고 오른쪽 버튼으로 Revision graph를 선택하면 볼 수 있습니다.
단축키는 Mac은 `Cmd + Shift + r` / Windows는 `Ctrl + Shift + r` 입니다.

### 리비전 그래프에서 그래프 선의 의미

리비전 그래프에서 각 리비전 블록과 화살표를 보실 수 있을텐데요.
각 화살표의 의미는 리비전 그래프 오른쪽 하단의 Legend에서 확인하실 수 있습니다.

![](https://user-images.githubusercontent.com/5077086/115150328-cd090a80-a0a2-11eb-8981-bd550dc644c3.png)

Legend에서 보실 수 있듯이 색과 선의 형태에 따라 의미하는 것이 다르네요.

> 저도 정리하면서 어렴풋이 알던 내용을 정리한 느낌이라 좋군요. 😸

Branch, Merge, Edit 등 내용은 이름만 봐도 알 수 있을 것 같으니 이런 것이 있다 정도로 보고 넘어가겠습니다.

### 리비전 그래프 기능 상세

리비전 그래프에서는 리비전 상세 내용에서 어떤 Integration에 의해 생성된 리비전인지, Label이 있는지, 코드 수정 사항이라면 짧게 Preview도 볼 수 있습니다.

- Details - 리비전의 상세 내용을 알 수 있습니다. 서밋 날짜, changelist, 설명 등이 포함되어있습니다.
- Integrations - 리비전이 어떤 Integration에 의해 만들어졌는지 알 수 있습니다. (그냥 서밋이면 해당 항목은 보이지 않습니다.)
- Labels - 해당 리비전에 설정된 레이블을 보여줍니다.
- Preview - 파일의 프리뷰를 보여줍니다. 파일이 크거나 바이너리일 경우에는 볼 수 없습니다.

## 마무리

리비전 그래프를 볼 수 있다는 점에서 소스트리 커밋 그래프와 비슷하지만 파일 단위의 히스토리 그래프를 볼 수 있다는 점에서 특장점이 있는 것 같습니다.
파일이 어떻게 머지되고 브랜치에 포함되었는지 볼 수 있어서 편리한 기능이라고 생각합니다.
리비전 그래프 기능 자체가 직관적이라 간단하게 소개해도 내용은 충분했을 것 같네요.
다음에는 타임 랩스 기능을 포스트해보겠습니다.