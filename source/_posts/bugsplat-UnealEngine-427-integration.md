---
title: "BugSplat - Uneal Engine 4.27 integration"
toc: true
date: 2023-07-10 23:30:17
categories:
- Tech
- Game
tags:
- Unreal Engine
- BugSplat
---

## BugSplat

![](https://user-images.githubusercontent.com/2646053/239029615-e577b6e9-4b8e-4b9a-8a56-556909c58069.png)

홈페이지: <https://www.bugsplat.com/>
가이드 문서: <https://docs.bugsplat.com/introduction/getting-started/integrations/game-development/unreal-engine>

## 설치, 설정 방법

가이드 문서: <https://docs.bugsplat.com/introduction/getting-started/integrations/game-development/unreal-engine>

설정 방법은 간단합니다.

1. 에디터에서 프로젝트 설정에 “크래시 리포터 포함” & “디버그 파일 포함” 설정해주기
2. `DefaultEngine.ini` 에 크래시 덤프를 보낼 주소를 입력해주기
    1. DataRouterUrl="https://{database}.bugsplat.com/post/ue4/{appName}/{appVersion}"
3. 4.26 이후 버전에는 `DefaultEngine.ini` 파일을 아래 경로에 복사해줘야 함(폴더가 없으면 다 만들어서 넣어줘야 함)
    1. 패키지 빌드 폴더\Engine\Restricted\NoRedist\Programs\CrashReportClient\Config
4. 패키지 빌드 폴더에서 심볼 파일 업로드(.pdb)
    1. sendpdbs 커맨드라인 프로그램을 이용해서 심볼 파일 업로드 (가이드 문서 참고)
    2. SendPdbs.exe /u {username} /p {password} /b {database} /a {appName} /v {appVersion} /s /f "*.pdb;*.dll;*.exe"
5. 패키지 빌드에서 크래시 발생시키면 대시보드에서 바로 볼 수 있음

## 설정 상세

- `DefaultEngine.ini`에 DataRouterUrl에는 {} 값을 실제 사용할 값으로 바꿔서 입력해야합니다
    - {database} 는 BugSplat에 설정에서 데이터베이스를 만들어서 사용할 수 있습니다
- 언리얼엔진 4.27.2 버전은 가이드 문서에 있는 아래 내용을 참고하여 추가 설정해줘야합니다
    - "For capturing crashes in packaged games in Unreal Engine 4.26 and newer, copyDefaultEngine.ini to {output directory}\Engine\Restricted\NoRedist\Programs\CrashReportClient\Config making sure to create folders that don't exist (where{output directory} is the location of your packaged build)."
    - 이 폴더에 DefaultEngine.ini 파일이 없는 경우 BugSplat에서 크래시를 확인할 수 없었습니다

## 크래시 업로드 확인

프로젝트 패키지로 만들어진 바이너리 실행 후 크래시를 발생시킵니다.
저는 크래시 발생시키는 명령어 이름을 `crashMe`로 지어두었고 콘솔 명령어로 실행하면 아래와 같이 크래시 리포터가 뜨게됩니다.

![크래시 리포터](https://user-images.githubusercontent.com/5077086/250354005-5cde418e-4cc5-4fe8-b14c-bbeb24459f76.png)

"Send and Close"로 크래시 정보를 보내면 센트리에서 크래시 정보를 볼 수 있게됩니다.

![BugSplat-이슈 대시보드](https://user-images.githubusercontent.com/5077086/252392323-dfdb743d-8264-48b3-b2ab-0da6be5b65f6.png)
![BugSplat-이슈 상세](https://user-images.githubusercontent.com/5077086/252392814-6e7e17cc-4ec1-45de-bb8b-438fca4b0851.png)

## 마무리

Sentry에 이어서 BugSplat이라는 서비스에서 크래시 업로드, 크래시 대시보드 확인을 한번 해보았습니다.
BugSplat은 Sentry에 비해서 투박한 느낌이 있습니다.
Overview / Other Threads / Registers / Modules 등 각 항목별로 나눠서 보여주고 있지만 Sentry를 보고 BugSplat을 보니 뭔가 필요한 정보는 알아서 찾아서 보세요의 느낌이 강했네요.
두 서비스 모두 크래시 분석을 위한 정보들을 잘 보여주고 있는 것 같았습니다.
(엔지니어분과 같이 이런 뷰 형태는 어떤지 확인은 해봐야겠지만요 😂)

다른 크래시 분석 서비스도 다음 포스트에서 다뤄보겠습니다.

## 참고: Sentry - Unreal

{% post_link Sentry-UnealEngine-427-integration %}
