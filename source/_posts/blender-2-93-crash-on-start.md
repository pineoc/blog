---
title: Blender 2.93 버전 Mac OS 시작시 크래시 이슈
toc: true
date: 2021-09-20 18:37:02
categories:
- Tech
tags:
- Blender
---

## Blender 2.93 Mac OS에서 시작시 크래시

이번에 컴퓨터 그래픽스를 공부하면서 렌더링이나 그래픽 애셋 작업이 어떤 것인지 알아보려고 Blender를 설치해보았습니다.

https://www.blender.org/

Mac OS에 설치하고 실행해보았는데 크래시가 발생하는 겁니다.

### 어떤 크래시인가?

크래시 발생에 대한 세부사항은 다음과 같았습니다.

```
Process:               Blender [39427]
Path:                  /Applications/Blender.app/Contents/MacOS/Blender
Identifier:            org.blenderfoundation.blender
Version:               2.93.4 (2.93.4 2021-09-01)
Code Type:             X86-64 (Native)
Parent Process:        ??? [1]
Responsible:           Blender [39427]
User ID:               501

Date/Time:             2021-09-20 18:36:26.898 +0900
OS Version:            macOS 11.6 (20G165)
Report Version:        12
Bridge OS Version:     5.5 (18P4759a)
Anonymous UUID:        xxx

Sleep/Wake UUID:       xxx

Time Awake Since Boot: 44000 seconds
Time Since Wake:       2400 seconds

System Integrity Protection: enabled

Crashed Thread:        0  Dispatch queue: com.apple.main-thread

Exception Type:        EXC_CRASH (SIGABRT)
Exception Codes:       0x0000000000000000, 0x0000000000000000
Exception Note:        EXC_CORPSE_NOTIFY

Application Specific Information:
abort() called
terminating with uncaught exception of type boost::locale::conv::conversion_error: Conversion failed

Thread 0 Crashed:: Dispatch queue: com.apple.main-thread
...
```

크래시 내용만 골라서 확인해보겠습니다.

```
terminating with uncaught exception of type boost::locale::conv::conversion_error: Conversion failed
```

보니까 locale과 관련한 에러같기도한데 검색해보았더니 LOCALE 쪽 이슈라고 합니다.

### 해결방법?

Mac 언어 설정을 한국어/중국어/일본어로 했을 경우 발생할 수 있다고합니다.

1. 시스템 환경설정 실행
2. 언어 및 지역 선택
3. 선호하는 언어 English 첫번째로 설정 (시스템 언어 English로 설정)
4. Blender 실행
5. 문제 해결!

향후 업데이트에는 수정될 수 있겠지만 당분간은 언어 설정 변경을 통해서 문제를 우회해서 사용해야겠네요.
Blender를 사용하는데 크래시가 발생한다면 참고하여 사용해보세요.
(실행한 뒤에는 언어 변경을 하더라도 잘 동작합니다.)
