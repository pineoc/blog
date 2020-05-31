---
title: What is Clumsy
toc: true
date: 2020-03-21 03:14:21
categories:
- Tech
tags:
- Tool
---

# Clumsy 소개

[https://jagt.github.io/clumsy/index.html](https://jagt.github.io/clumsy/index.html)

네트워크 환경, 상태를 컨트롤할 수 있는 툴 입니다.
Windows 환경에서만 동작하는 툴이어서 맥(Mac), 리눅스(Linux)에서는 사용할 수 없는 툴입니다.
(Windows의 `WinDivert`라는 네트워크 관련 패키지를 사용해서 컨트롤하는 프로그램이기 때문입니다.)

![clumsy demo](https://jagt.github.io/clumsy/clumsy-demo.gif)

## 다운로드

- [https://jagt.github.io/clumsy/download.html](https://jagt.github.io/clumsy/download.html)

# 사용 방법

[https://jagt.github.io/clumsy/manual.html](https://jagt.github.io/clumsy/manual.html)

## General

![Clumsy Screen](https://jagt.github.io/clumsy/screen.png)

1. Filtering: 패킷은 이 필터를 조건으로 캡처됩니다. 필터링에 있는 내용을 조건으로 패킷을 잡아 아래 함수들이 동작합니다.
2. Presets 메뉴: 선택할 수 있는 내장 프리셋 목록이 있습니다. 어떤 필터들이 있는지 드롭다운을 눌러서 볼 수 있습니다.
  * config.txt 에 실행파일과 함께 번들로 필터를 추가할 수도 있습니다.
3. Start 버튼: 패킷 캡쳐를 시작합니다. 필터의 구문이 맞지 않거나, 다른 이슈로 인해 시작이 안될수도 있습니다.
  * 캡쳐가 시작되면 버튼은 "Stop"으로 변경되고, 버튼 왼쪽 작은 아이콘에 녹색으로 표시됩니다.
  * 캡쳐에 실패하면 아이콘은 적색으로 표시됩니다.
4. Function control: 캡쳐된 패킷에 대해 원하는 기능을 사용할 수 있습니다.
  * Lag - 패킷 전송을 지연시킵니다. Lag time 만큼 지연시킵니다.
  * Drop - 패킷을 전송하지 않고 떨어뜨립니다.(드롭합니다) Chance 값에 따라 떨어뜨립니다.
  * Throttle - 특정 시간 동안 트래픽을 차단하고 나중에 일괄적으로 보냅니다.
  * Out of order - 순서를 뒤섞습니다.
  * Duplicate - 패킷을 중복으로 보냅니다.
  * Tamper - 패킷 내용을 변경(변조)합니다.
5. Parameters control
  * Inbound - 밖에서 안으로 들어오는 패킷에 대해 적용합니다.
  * Outbound - 안에서 밖으로 나가는 패킷에 대해 적용합니다.
  * Lag time / Chance - 적용하고자하는 확률, 지연 값을 설정할 수 있습니다.
6. Status: 현재 상태에 대한 메세지를 보여줍니다.

## Client Packet Loss Test

![10% packet loss test](https://user-images.githubusercontent.com/5077086/77194242-ef88c700-6b22-11ea-9b55-78cf442c60bb.png)

- 모든 패킷에 대해서 10% 확률로 패킷을 드롭시키는 설정입니다.

# 정리

이 틀을 네트워크 테스트를 하다가 알게되었는데 가이드 문서가 없어서 블로그에 한번 정리해보았습니다.
툴 자체는 간단하고 네트워크 지식(UDP, TCP, 인바운드, 아웃바운드 정도) 알면 사용하는데에는 무리가 없어보이는 툴입니다.
네트워크 상태 테스트에서 일반적으로 발생하는 문제 케이스에 대한 테스트 케이스도 한번 정리해두면 좋을 것 같습니다.
