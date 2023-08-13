---
title: Qingmi Smart Powerstrip timeout 문제 해결
toc: true
date: 2019-07-21 23:19:16
categories:
- Life
- IoT
tags:
- IoT
---

# Qingmi Smart Powerstrip 연결 문제

최근에 스마트 홈 구축에 계속 빠져서 이것저것 찾아보다가 스마트 플러그 제품을 구매해보았습니다
구매 링크: <https://smartstore.naver.com/shop360/products/611051018>

여기서 제가 구매한 제품은 5구 스마트 멀티탭(Qingmi 스마트 파워스트립) 입니다
앱에 연결하려다 연결이 되지 않고 연결 시간 초과 현상이 지속되는 문제가 있었는데 해결해보았습니다
빠르게 문제 상황 & 문제 해결방법으로 가보겠습니다

## 문제 해결

빠르게 문제 해결만 보고 싶으신 분들을 위해 해결 방법부터 정리합니다

- Mi 홈 계정 생성시 `중국` 계정으로 생성해야 함
- 샤오미 중국 계정으로 생성해야 중국 본토 지역에서 사용 가능한 기능들을 사용할 수 있음
- 샤오미 중국 계정의 ID는 4294967295 (32bit) 보다 작은 값으로 설정됨
- 샤오미 `중국 계정`으로 연결 성공

## 문제 상황

문제 상황에 대해 짧게 정리해보면 아래와 같습니다

- Mi 홈 앱에서 Qingmi 스마트 플러그를 찾아 연결을 시작한다
- 앱에서 나온 설명대로 플러그 연결을 진행한다
- 와이파이, 스마트 플러그, 스마트폰을 가깝게 둔다
- 연결 완료를 기다리지만 `연결 실패`가 계속 발생한다

### 연결시 확인했던 준비사항

- Mi 홈 앱에서 지역을 `중국 (본토)`로 설정
- 와이파이 2.4GHz 인지 확인
- 와이파이 비밀번호 정확한지 확인
- 와이파이 무선 인터넷 채널 10 채널 미만인지 확인
- 와이파이 DNS 블로킹으로 샤오미 클라우드가 막혀있는지 확인

### 나중에 알게된 확인해야했던 사항

**샤오미 계정 중국 계정인지 확인**

- 계정 ID 값이 4294967295 (32bit) 미만 값 인지 확인
- 한국 계정으로 만들었을 때는 65xxxxxxxx 값으로 32비트 값이 초과된 값이었음
- <https://forum.yeelight.com/t/topic/9582> 참고

# 문제 해결 후기

사고 나서 약 2주 뒤에나 해결할 수 있었던게 다행인지 아닌지 모르겠지만
지금은 잘 사용하고 있습니다. :)
다음 포스트는 어떻게 잘 사용하고 있는지를 올려볼 수 있으면 좋겠네요.