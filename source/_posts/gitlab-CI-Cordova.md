---
title: GitLab CI 해보기 - Cordova
date: 2019-06-30 10:06:28
categories:
  - Tech
tags:
  - GitLab
  - CI
thumbnail: https://about.gitlab.com/images/ci/gitlab-ci-cd-logo_2x.png
---

> 이 글은 2018년 1월 기준으로 작성된 글입니다. 현재 Gitlab 설정, Cordova 환경과는 다를 수 있습니다.

## GitLab CI?

소개: <https://about.gitlab.com/product/continuous-integration/>
GitLab에서 CI를 지원한다는 것을 듣고 당시 진행하던 프로젝트를 설정해보고자 했습니다.
CI는 Continuous Integration의 약자로 지속적인 통합으로 부릅니다.

CI는 "지속적으로 퀄리티 컨트롤을 적용하는 프로세스를 실행하는 것이다. ([Wiki](https://ko.wikipedia.org/wiki/%EC%A7%80%EC%86%8D%EC%A0%81_%ED%86%B5%ED%95%A9))으로 설명할 수 있고 이 글에서는 CI에서 자세히 다룰 예정은 아니기에 다른 좋은 문서를 참고해주세요. :)

GitLab 소개문서에는 CD(Continuous Delivery OR Continuous Deployment-지속적인 배포)도
다루고 있으니 참고하시면 좋을 것 같습니다.

저는 CI까지만 설정해보겠습니다. (나중에 CD까지 해볼 수 있겠죠.)

## CI 설정 시나리오

1. 빌드 환경 설정
2. .gitlab-ci.yml 설정
3. GitLab Repo에 push!
4. 빌드!

### 빌드 환경 설정

여기서 어려울 것으로 예상한 것은 빌드 환경을 설정하는 것이라고 생각했습니다.
[freecodecamp 미디엄 글](https://medium.freecodecamp.org/how-to-setup-ci-on-gitlab-using-docker-66e1e04dcdc2)에서는 도커 이미지를 사용하여 어렵지 않게 풀어낸 것 같습니다.

빌드 환경 설정에 필요한 Cordova 환경설정이 무엇인지 살펴보았습니다.
Cordova 7.x 기준의 `안드로이드 빌드 환경`은 아래와 같습니다. ([참고](https://cordova.apache.org/docs/en/7.x/guide/platforms/android/index.html#installing-the-requirements))

- JDK 8 이상
- Android SDK, Android SDK Packages
- Node.js 8.9.4 (NPM)
- Cordova 7.x
- (옵션) 환경 변수 설정

iOS 빌드 환경은 macOS 이미지가 없어서 설정해보지 못했습니다. ;(
안드로이드 설정만 해봐야겠네요.

앞서 freecodecamp 미디엄 글에서는 docker 이미지를 사용해서 CI를 설정을 했습니다.
Cordova 관련한 docker 이미지가 있는지 확인해보았고 적당한 것을 찾았습니다.
<https://hub.docker.com/r/beevelop/cordova/>

이 이미지를 사용하여 만들어본 저장소는 아래와 같습니다. (저장소는 기본적인 프로젝트 생성한 상태입니다.)
<https://gitlab.com/pineoc/cordova-ci-demo>

### .gitlab-ci.yml 설정

```yml
image: beevelop/cordova:v7.1.0

before_script:
  - cordova platform add android

stages:
  - build

build:
  stage: build
  script:
    - cordova build android
```

### GitLab Repo에 Push!

위에서 설정한 `.gitlab-ci.yml` 파일을 프로젝트 최상단 경로에 두면 GitLab에서 파일을 인식하여
설정한 내용대로 빌드를 진행합니다. 진행된 내역은 아래 링크에서 확인할 수 있습니다.
<https://gitlab.com/pineoc/cordova-ci-demo/pipelines>

이제 커밋할 때마다 빌드가 돌아가고 빌드의 실패/성공을 확인할 수 있습니다.
커밋에 `[ci skip]` 이라고 명시하면 빌드는 스킵됩니다.
![](https://user-images.githubusercontent.com/5077086/60391408-7e365d80-9b28-11e9-8ea0-d36389f6cef1.png)
(중간에 빌드 환경이 달라져서 실패한 내용이 생겼네요.)

기본 프로젝트는 어렵지 않게 설정해보았지만
추가적인 플러그인 추가나 설정이 들어가면 어려워질 수 있을 것 같습니다.
iOS 빌드 시스템을 사용하려면 다른 것도 필요하겠구요.

기본적인 설정이라도 도움이 되었으면 좋겠습니다. :)

## 참고 문서

- Medium: <https://medium.freecodecamp.org/how-to-setup-ci-on-gitlab-using-docker-66e1e04dcdc2>
- GitLab CI quick start: <https://gitlab.com/help/ci/quick_start/README>
- GitLab CI Demo: <https://gitlab.com/ykyuen/gitlab-ci-demo>
