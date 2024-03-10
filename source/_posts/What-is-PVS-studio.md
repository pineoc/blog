---
title: What is PVS Studio
toc: true
date: 2024-03-10 21:25:37
categories:
- Tech
- Program&Service
tags:
- Tool
- code analyzer
- PVS Studio
---

## PVS Studio

<https://pvs-studio.com/en/>
"PVS‑Studio is a static analyzer on guard of code quality, security (SAST), and code safety"
홈페이지에 적혀있는 문구 그대로 보면 코드 정적 분석 툴로 코드 퀄리티와 보안을 위해 사용할 수 있는 툴입니다.

C, C++과 Java 코드를 분석하는 툴로 다른 정적 분석 툴로는 Cppcheck, Clang Static Analyzer, SonarQube 등이 있습니다.
PVS Studio는 클라우드 제품은 없어보이고 설치형 프로그램으로 CI에 붙여서 사용하거나 코드 에디터에 설정하고 사용할 수 있습니다.

![PVS-Studio for Visual Studio-PVS Studio blog](https://cdn.pvs-studio.com/import/docx/blog/0635_PVS-Studio-for-Visual-Studio_2019/image5.png?_ga=2.12302324.1755151432.1710071161-19417103.1708702494)

정적 코드 분석 툴로 TS(TypeScript)나 자바스크립트 앱을 제작할때 사용하는 TSLint, ESLint와 비슷하다고 볼 수 있겠네요.
실제로 빌드 및 프로그램이 실행할 때에 문제가 없을 수는 있지만 정적 코드 분석 결과 문제가 있을 요소는 미리 수정하는게 좋겠죠.


## PVS Studio 기본 설명

https://youtu.be/4Fy-JTYzEs0

사실 기본 설명은 위에 정적 코드 분석 툴 정도로 다 설명이 될 수 있다고 생각합니다.
정적 코드 분석 -> 분석 코드 Warning 확인 -> 수정 -> 코드 개선의 흐름이 정적 코드 분석 툴을 사용하는 흐름이겠죠.

분석 코드 Warning 몇가지를 살펴보고 넘어가겠습니다.
Warnings: <https://pvs-studio.com/en/docs/warnings/>

* [V501](https://pvs-studio.com/en/docs/warnings/v501/). Identical sub-expressions to the left and to the right of 'foo' operator.
    * 왼쪽, 오른쪽 동일한 표현식이 있음. -> "유의미한 표현식을 사용하지 않았네. 수정해라" warning으로 볼 수 있겠네요.
* [V502](https://pvs-studio.com/en/docs/warnings/v502/). The '?:' operator may not work as expected. The '?:' operator has a lower priority than the 'foo' operator.
    * ? 연산자의 활용이 적절하지 않게 되어있음. 말 그대로 ? 연산자가 적절히 사용되었는지 확인하고 수정하라는 warning.
* [V503](https://pvs-studio.com/en/docs/warnings/v503/). Nonsensical comparison: pointer < 0.
    * 포인터 비교가 잘못된 코드가 있음. 포인터가 아닌 다른 것을 비교해야한다는 warning으로 이해할 수 있습니다.

위 처럼 Warning에 따라 수정하고 코드를 개선할 수 있는 서비스로 이해해볼 수 있겠습니다.

<https://stackshare.io/stackups/pvs-studio-vs-sonarqube>
stackshare라는 서비스의 장단점 비교 서비스를 보았을 때 SonarQube와 인지도 차이가 크지만
PVS Studio도 C++ 개발하거나 게임 개발에 사용해볼만한 프로그램으로 사용되긴하는 것 같습니다. 😃
(SonarQube가 인지도가 높아 PVS Studio랑 어떤 차이가 있는지 확인차 살펴보았는데 PVS Studio는 인지도가 역시 낮았네요)

## PVS Studio 가이드 문서 살펴보기

공식 가이드 문서: <https://pvs-studio.com/en/docs/>
블로그: <https://pvs-studio.com/en/blog/posts/>

## 마무리

게임 개발을 하면서 코드 분석툴은 어떤 것들이 있고 그중에 PVS Studio는 뭘까 싶어 한번 찾아보게되었네요.
기본적으로 PVS Studio는 정적 코드 분석 툴로 분석한 코드는 개발자들이 확인하고 개선해나가야하는 중간 도우미 같은 친구이긴합니다.
Warning을 다 해결한다고 다 좋은 코드는 아니지만 안정성, 품질을 신경쓰고 있는 코드로 볼 수는 있겠다는 생각이듭니다.