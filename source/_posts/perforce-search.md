---
title: Perforce(P4) Search(검색) 기능
toc: true
date: 2021-03-31 07:19:37
categories:
- Tech
- Program&Service
tags:
- Perforce
---

## P4V 검색 기능

이번 포스트에서는 P4V에서 검색 기능을 알아보려합니다.
가이드 문서: [P4V User Guide: Searching and filtering](https://www.perforce.com/manuals/p4v/Content/P4V/using.filters.html#Searching_and_filtering)

P4V 검색 기능 가이드 문서를 간단히 요약하면,
파일, changelist, workspace, branch, stream, job, label을 필터를 통해 검색할 수 있습니다.
Cmd+F(Ctrl+F)를 통해서 검색도 가능합니다.

![](https://user-images.githubusercontent.com/5077086/113065341-a9fde000-91f3-11eb-8eb6-206155cf3561.png)

### changelist description 검색 기능

사실 저나 대부분의 사용자는 submit된 changelist에서 설명으로 입력된 내용을 검색을 원할 것 같은데
P4V에는 Ctrl+F 기능을 통해서 간단하게 제공하고 있습니다. (너무 간단해요)
Find File 기능도 사실 Changelist 조건이 있어서 설명 검색이 가능하지 않을까해서 보았는데 숫자로만 검색이 가능한 상태입니다.
(탭 이름도 파일 찾는 탭이니 그럴 수 있다고는 생각합니다.)

![](https://user-images.githubusercontent.com/5077086/113066920-5c36a700-91f6-11eb-9b99-6e5ac3f7bad9.png)

검색할 때 필터를 사용하라고 하지만 필터에도 description으로 필터링해서 보여주는 것은 없어요. 🤯
이참에 p4vjs로 커스텀 html tab을 만드는게 낫겠다 싶어서 검색 페이지를 만들어보았습니다.

## p4v custom html tab을 통한 검색 기능 설정

<https://github.com/pineoc/p4v-html-utils>

가이드에 맞춰 설정해주시고 Run Queries 메뉴를 눌러보시면 아래와 같은 화면으로 검색해보실 수 있습니다.

![](https://user-images.githubusercontent.com/5077086/113067599-95bbe200-91f7-11eb-8ba2-7b422093fe77.png)
한번 사용해보셔요 😈

## 마무리

P4V 검색 기능을 소개하려했는데 사실 기본적으로 제공하는 검색 기능이 크게 도움이 되는지는 모르겠습니다. 😂
제가 모르는 기능이 있을지는 모르겠지만.. PM으로 업무를 하면서 사용해본 P4V에는 검색 기능이 좋지는 않은 것 같아요.
그래서 custom html tab까지 만들어서 사용해보고 있는데 나름 만족하고 있습니다.

> 제가 P4V를 완전히 깊게 사용하지 못해서 모르는 부분이 있을 수 있으니 정정이 필요한 부분이 있다면 댓글로 남겨주세요!

향후 업데이트에 검색 기능이 강화될 수 있지만.. 현재는 원하는 changelist를 검색하기가 어려운 상태이긴합니다.
description으로 필터링하는 기능이 생기기를 기원하며 마치겠습니다.
감사합니다 😸
