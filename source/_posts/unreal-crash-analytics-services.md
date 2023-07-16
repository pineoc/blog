---
title: "Unreal Engine 크래시 분석 서비스 조사"
toc: true
date: 2023-07-16 15:30:17
categories:
- Tech
- Game
tags:
- Unreal Engine
- Crash reporter
- Crash
---

## 조사 목적

- 언리얼 엔진으로 게임을 만들 때에 사용하는 크래시 분석 서비스는 무엇이 있는지 알아봅니다.
- 단순히 크래시 덤프를 수집하는 것에 그치지 않고 어떤 크래시가 많이 발생하고 있는지 트렌드나 특이점을 확인할 수 있는 서비스들이 있는지 찾아봅니다.

## 언리얼 크래시 리포터(Unreal Crash Reporter)

![Unreal Crash reporter](https://docs.unrealengine.com/5.0/Images/designing-visuals-rendering-and-graphics/rendering-optimization/fix-a-gpu-crash/render-core-crash.webp)

## 언리얼 엔진 크래시 분석 서비스

알아본 크래시 분석 서비스

- Sentry: [https://sentry.io/welcome/](https://sentry.io/welcome/)
- BugSplat: [https://www.bugsplat.com/](https://www.bugsplat.com/)
- Backtrace: [https://backtrace.io/](https://backtrace.io/)
- Raygun: [https://raygun.com/](https://raygun.com/)
- Countly: [https://countly.com/](https://countly.com/)

### Sentry 👍

![Sentry dashboard](https://docs.sentry.io/static/417f0fbf2900c7e2769ffcffb93e25e4/c1b63/attachments-list-example.png)

[https://sentry.io/welcome/](https://sentry.io/welcome/)
[https://docs.sentry.io/platforms/unreal/](https://docs.sentry.io/platforms/unreal/)


센트리(Sentry)는 웹 서비스, 앱 서비스에서도 많이 쓰는 이슈 관리 솔루션으로 알고 있습니다.
언리얼에서 사용하고자 할 경우에는 minidump를 직접 올리거나 크래시 리포터에 연결, 크래시 덤프를 올리는 방식인 것 같습니다.
가이드 문서를 보면 제한 사항이 있네요.

- *20MB* for a compressed request → 크래시 덤프 업로드시 압축된 데이터가 20MB 이하여야 하고
- *100MB* for the full crash report after decompression → 크래시 덤프 압축을 해제하면 100MB 이하여야 함

이런 제한을 참고해서 센트리를 도입해서 유의미하게 쓸 수 있는지 검토해야겠네요.
(덤프에 많은 정보를 남길 경우 센트리를 쓰지 못한다는 이야기… 😂)

> 플러그인이 있어서 설정은 쉬웠네요.
> 센트리 설정 경험기: {% post_link Sentry-UnealEngine-427-integration %}

### BugSplat 👍

![BugSplat dashboard](https://user-images.githubusercontent.com/2646053/239029615-e577b6e9-4b8e-4b9a-8a56-556909c58069.png)

[https://www.bugsplat.com/](https://www.bugsplat.com/)
[https://docs.bugsplat.com/introduction/getting-started/integrations/game-development/unreal-engine](https://docs.bugsplat.com/introduction/getting-started/integrations/game-development/unreal-engine)


요 서비스는 언리얼 플러그인까지 있는 서비스여서 설정은 편할 것 같습니다.

> 센트리는 제한이 있었는데 BugSplat에도 제한 사항이… 있군요.
> 센트리랑 비슷하게 압축된 덤프의 사이즈가 20MB 여야합니다. 😂 ([참고 링크](https://docs.bugsplat.com/introduction/getting-started/troubleshooting#the-crash-being-uploaded-is-too-large))

1. 에디터에서 프로젝트 설정에 “크래시 리포터 포함” & “디버그 파일 포함” 설정해주기
2. `DefaultEngine.ini` 에 크래시를 보낼 주소를 입력해주기
    1. DataRouterUrl="https://{database}.bugsplat.com/post/ue4/{appName}/{appVersion}”
3. 4.26 이후 버전에는 `DefaultEngine.ini` 파일을 아래 경로에 복사해줘야 함(폴더가 없으면 다 만들어서 넣어줘야 함)
    1. 패키지 빌드 폴더\Engine\Restricted\NoRedist\Programs\CrashReportClient\Config
4. 패키지 빌드에서 크래시 발생시키면 대시보드에서 바로 볼 수 있음

> BugSplat도 Trial로 설정해보고 테스트해보았는데 가이드 문서대로 설정해볼 수 있었습니다.
> BugSplat 설정 경험기: {% post_link bugsplat-UnealEngine-427-integration %}


### Backtrace 👍

![Dashboard](https://docs.saucelabs.com/img/error-reporting/console-views/project-overview.png)

[https://backtrace.io/](https://backtrace.io/)
[https://support.backtrace.io/hc/en-us/articles/360040106172-Unreal-Integration-Guide](https://support.backtrace.io/hc/en-us/articles/360040106172-Unreal-Integration-Guide)

백트레이스 서비스는 언리얼 엔진 설정이 가능한 솔루션이네요.
가이드 문서상 크래시 덤프 사이즈 제한은 보이지 않습니다.

> 요 친구도 플러그인이 있지는 않고 따로 크래시 리포터 설정에 DataRouterUrl 설정만 해주면되네요.
> BugSplat과 동일하게 패키지 빌드 폴더\Engine\Restricted\NoRedist\Programs\CrashReportClient\Config 경로에 DefaultEngine.ini 가 있어야 크래시 덤프가 업로드되는 것 같습니다.

따로 플러그인은 있지 않고 단순 크래시 리포터 설정으로 가능하며 다른 크래시 분석 서비스와 비슷한 기능들을 가지고 있습니다.

- Overview: 대시보드로 크래시 전체적인 현황을 볼 수 있는 뷰
- Release: 업데이트된 버전 별로 크래시 지표를 볼 수 있는 뷰
- Triage: 발생한 크래시를 테이블로 볼 수 있는 뷰. 필터를 적용해서 볼 수도 있음
- Debug: 각 크래시별 정보를 상세히 볼 수 있는 뷰

크래시 정보를 상세히 볼 수 있도록 심볼 업로드는 프로젝트 세팅 > 심볼 설정에서 할 수 있습니다.

> 백트레이스도 크래시 분석 서비스들과 무난히 비슷한 서비스인 것 같네요.
> 실제 다른 서비스와 장단점을 상세 분석해보려면 다양한 케이스로 사용해봐야할 것 같습니다.

### Raygun 🤔

(⚠ 언리얼 엔진에 설정하기 쉽지 않은 서비스)

![](https://assets-global.website-files.com/5e2701b416b6d176f5007781/6128362ce8fda22987a2b37e_CR-1_%402x.png)

[https://raygun.com/](https://raygun.com/)

레이건 서비스는 따로 언리얼 엔진 플러그인이 있지는 않네요.
이 서비스를 사용한다면 C++ 항목으로 구성하고 minidump(breakpad)를 업로드하는 방식으로 시도해보았는데 잘 되지 않았습니다.

1. 가이드 문서 확인 → `sender.SendCrashReport(L"https://api.raygun.com/entries/breakpad?apikey=...", userCustomData, files, 0);` 코드 확인 → URL로 덤프를 보낼 수 있도록 설정
2. DefaultEngine.ini 에서 [CrashReportClient], DataRouterUrl 항목에 위 URL 입력
3. 크래시 발생 후 크래시가 남는지 확인 → 확인할 수 없었음

> 다른 서비스에서 했던 것 처럼 크래시 업로드 URL에만 덤프를 올리면 가능할 것으로 기대했지만 잘되지 않네요.
> Raygun은 웹서비스 설정이 더 편한 서비스라고 보여서 설정을 더 시도해보지는 않았습니다.

### Countly ❓

(⚠ 언리얼 엔진에 설정하기 쉽지 않은 서비스)

[https://countly.com/](https://countly.com/)
[https://countly.com/feature/crashes-errors](https://countly.com/feature/crashes-errors)

카운틀리는 자체 서버 구축과 클라우드 서비스를 사용할 수 있는 서비스 시스템으로 볼 수 있습니다.
자체 서버 구축: [https://support.count.ly/hc/en-us/articles/360036862332-Installing-Countly-server](https://support.count.ly/hc/en-us/articles/360036862332-Installing-Countly-server)
언리얼 엔진 크래시 분석 서비스로 사용하려면 자체 서버 구축과 클라이언트에 minidump로 업로드 설정하는 방법으로 가능하네요.

## 마무리

위와 같이 언리얼 엔진 게임으로 크래시 현황, 분석을 할 수 있는 5가지 정도의 서비스를 알아보았습니다.

핵심 기능은 비슷한 것 같았고 2가지 정도는 C++ 빌드로 만들어진 프로그램을 minidump를 업로드하고 그 것을 분석하는 방식을 가지고 있었네요.
대부분 앱과 웹 서비스에서 발생하는 비정상 종료, 크래시를 분석하는 데에 맞춰져있었습니다.

언리얼 엔진으로 접근성이 좋았던 것은 Sentry 정도였고 나머지는 프로젝트 설정에 따라 커스텀 설정을 해줘야하는 것들이 좀 있었습니다.

Countly의 경우에는 서버를 자체 구축할 수 있다는 점에서 크래시 덤프 파일 사이즈가 크더라도 사용할 수 있겠다 싶었습니다.
(덤프에 많은 정보를 담고자할 경우 덤프 파일이 100MB가 넘어가는 경우도 있긴하더라구요.)

Countly 설정은 클라, 크래시 분석 서비스 서버 설정까지 해야해서 나중에 한번 해보고 포스트 남겨보겠습니다. 👋