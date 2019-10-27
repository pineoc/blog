---
title: Confluence 6.12-6.15 Release notes
toc: true
date: 2019-10-15 00:12:38
categories:
- PM
- System
tags:
- Confluence
---

## Confluence Release Notes

- [All Release Notes](https://confluence.atlassian.com/doc/confluence-release-notes-327.html)
- [6.13 Release Notes](https://confluence.atlassian.com/doc/confluence-6-13-release-notes-959288785.html)
- [6.14 Release Notes](https://confluence.atlassian.com/doc/confluence-6-14-release-notes-963655609.html)
- [6.15 Release Notes](https://confluence.atlassian.com/doc/confluence-6-15-release-notes-965554120.html)

## Confluence 6.12 - 6.15 릴리스 노트

컨플루언스 릴리스 중 6.12부터 6.15를 살펴보고자 합니다.
왜 6.12부터인지는... 현재 회사에서 6.12에서 6.15로 업데이트하면서 알게된 내용을 남겨보게되었습니다.
지금은 7.0 버전의 릴리스 노트가 나왔네요. (나중에 7.0 버전도 업데이트하면서 정리해봐야겠습니다.)

그럼 최신 순서대로 살펴보겠습니다.

## 6.15 릴리스

### Filter your search by space category

![](https://confluence.atlassian.com/doc/files/965554120/967334152/2/1551847079975/space-categories.png)

스페이스(공간) 카테고리에 따라 검색할 수 있도록 스페이스 카테고리가 추가되었습니다.
스페이스를 카테고리로 나누고 그에 따라 검색할 수 있는 기능을 사용할 수 있게되면서
스페이스를 많이 사용하는 곳에서는 유용한 기능일 수 있겠네요.

### Import with confidence

![](https://confluence.atlassian.com/doc/files/965554120/967336434/1/1551916170556/backup-restore-rn.png)

임포트할 때 실수하지 않도록 UI를 개선했다는 내용이네요.
경고 사항이나 여러가지 설명 사항들이 추가되었습니다.

## 6.14 릴리스

### Find work faster with the new Confluence search

이번 업데이트에서 검색이 빨라졌다고 합니다.
그동안에는 약간 느린 느낌이 있었는데 업데이트 이후에는 빨라진 느낌이 있긴했습니다.
검색 기능이 많이 강화되긴 했습니다.

#### Search for anything

기존에는 제목을 기반으로 검색하여 결과가 제한적이었습니다.
이번 업데이트에서는 파일, 내용 등 컨플루언스 컨텐츠 전체를 대상으로 검색하도록 개선되었습니다.

#### Quickly refine results with filters

검색 결과에 필터를 할 수 있도록 반응형 필터가 추가되었습니다.
스페이스, 작성자, 작성 시간 등으로 검색 결과를 필터링 할 수 있습니다.

### Massive editor improvements

에디터의 기능 및 버그 등을 많이 수정했다고 합니다.

> table cells, bullet points, and cursor behaviour, especially when copying and pasting content

위와 같은 것들을 수정했다고 하는데 많이 개선된 것 같기는 하지만 몇가지 버그가 계속 존재하긴 하는 것 같습니다.
(에디터 특성상 어쩔 수 없다고 생각하긴합니다. 명확히 정리하기 힘든 버그들이 있긴해요)

### More ways to edit files

6.11 릴리스에서 첨부 파일 업데이트 기능이 업데이트 되었는데
이번 릴리스에서는 페이지에서 직접 파일을 수정할 수 있는 기능이 추가되었습니다. (Attachments macro)

### Delete profile picture

관리자가 사용자의 프로필 사진을 지울 수 있는 기능이 추가되었습니다.
Delete Profile Picture 내용으로 검색해보면 메뉴를 볼 수 있습니다.

### Number your PDFs the easy way

스페이스를 익스포트할 때 PDF로 하는 경우 페이지 숫자를 넣을 수 있는 기능이 추가되었습니다.
사실 사용해보지 않아서 잘 모르겠는 기능이긴 하지만 많은 페이지를 익스포트할 일이 있고
그것을 리포트 형식으로 보여줘야한다면 쓸만할 것 같기도 합니다.

## 6.13 릴리스

6.13 릴리스는 엔터프라이즈 릴리스 입니다.
(엔터프라이즈 릴리스: 해당 릴리스가 수명이 다할 때까지 버그 수정 릴리스를 제공하는 릴리스)

### Supporting your GDPR efforts

GDPR에 대응할 수 있도록 기능을 몇가지 추가하였습니다.
계정을 삭제하거나, 사용 중지 등을 할 수 있고 그 계정의 컨텐츠도 삭제할 수 있게됩니다.
(한번에 모든 내용이 삭제될 수 있게됩니다.)

### PDF export improvements

pdf 익스포트 기능이 개선되었습니다. (자주 개선되는 PDF 익스포트 기능이네요.)
레이아웃에 맞게 익스포트하는 것이 어렵다는 점 알고 있어서 항상 개선하는 점은 좋은 것 같습니다.
아래는 수정된 내용입니다.

- Tables better match their Confluence counterparts, no longer filling the whole width, or forcing the columns to be equal width.
- Headings have been refreshed, with more consistent sizing.
- Ugly ducklings like the recently worked on, status, and tip macros now display more consistently.
- Each Confluence page starts on a new PDF page, making your documents easier to read.
- Long words and strings now wrap correctly.

### Moving to the Cloud has never been easier

![](https://confluence.atlassian.com/doc/files/959288785/960713714/2/1552435822739/MigrationAssistant-SelectSpaces.png)

컨플루언스 클라우드로 마이그레이션을 쉽게 진행할 수 있도록 개선되었습니다.
마이그레이션이 필요한 내용들을 직접 선택하고 마이그레이션이 진행되는 모습도 볼 수 있도록 개선되었다고 합니다.
(그전에는 어떻게 마이그레이션을 할 수 있었는지 모르겠습니다..)

## 마무리

컨플루언스는 많은 기능들이 추가되기보다 버그 수정이나 QoL의 내용이 많은 것 같네요.
사실 많은 기능들은 매크로로 빠져있어서 그런 것 같기는 합니다.
다음에는 7.0 릴리스 소식을 들고오겠습니다.

감사합니다.
