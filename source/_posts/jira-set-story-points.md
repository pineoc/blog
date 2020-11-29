---
title: Jira 스토리 포인트(Story points) 설정하기
toc: true
date: 2020-11-27 23:58:55
categories:
- PM
- System
tags:
- Jira
thumbnail: https://manifesto.co.uk/wp-content/uploads/2014/08/estimating-in-agile-and-scrum.png
---

## Jira 이슈 스토리 포인트 설정

이 포스트에는 스토리 포인트에 대한 개념적인 내용은 다루지 않고 Jira에서 이슈에 스토리 포인트를 설정하는 방법에 대해서만 다룹니다.
스토리 포인트와 관련한 이야기는 구글링해도 많이 나오니 참고해주세요. 😀

## 스토리 포인트 설정

단계별로 빠르게 설정해봅시다! (단, Admin 계정만 가능합니다)

1. Jira settings > issues 이동
2. Fields > Custom Fields 이동
3. Story Points를 찾아 Configure > Edit Configuration
4. Choose applicable issue type에서 story points를 사용하고자 하는 이슈 타입을 선택 후 설정
5. 사용하는 프로젝트로 가서 프로젝트 설정 > Screens에 스토리 포인트를 사용하고자하는 이슈 타입의 스크린 접근
6. 스크린에 스토리 포인트 필드 추가
7. 6에서 설정한 이슈 생성/수정/기본 스크린에 스토리 포인트 확인

## 마무리

이 글을 빠르게 정리해보게된 이유는 어드민 설정 > 이슈 > 커스텀 필드 >`스토리 포인트`를 일부 이슈 타입에 설정한 경우가 있기 때문입니다.
이 경우 시스템 관리자(어드민)이 `스토리 포인트` 필드의 이슈 타입을 설정해주어야 해당 이슈 타입에서 `스토리 포인트`를 사용할 수 있기에 종종 저도 까먹어서 정리해보게 되었습니다.
(사실 그냥 제일 좋은 것은 스토리 포인트 필드를 그냥 any issue type으로 제한을 풀어버리면 모든 문제는 쉽게 해결됩니다. ㅎㅎ)
