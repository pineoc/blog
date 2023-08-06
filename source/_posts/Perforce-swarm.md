---
title: Perforce Swarm 소개
toc: true
date: 2022-02-28 11:30:45
categories:
- Tech
- Program&Service
tags:
- Perforce
- Helix Swarm
---

## Perforce Swarm?

이번 포스트에는 Perforce를 사용할 때 코드 리뷰를 하기 위해 사용하는 서비스인 Swarm을 소개해보려합니다.

공식 홈페이지: [https://www.perforce.com/ko/jepum/helix-swarm](https://www.perforce.com/ko/jepum/helix-swarm)

사실 Github, Gitlab, Bitbucket등 다른 소스 관리 서비스에서 기본적으로 제공하는 것을 따로 서비스로 제공하는 것이라 설치나 접근성 면에서 살짝 부족한 면은 좀 있습니다.
Swarm 기능은 다른 소스 관리 서비스와 거의 동일하지만 살짝 훑어보겠습니다.

## Swarm 소개

공식 홈페이지에 따르면 아래와 같은 기능을 소개하고 있습니다.

### 더 나은 코드를 위한 공동 작업 / 맞춤 알림

- 기본적인 리뷰 기능에 대한 소개입니다
- 화면이 가로로 분할되어 코드 변경 사항을 확인할 수 있고 코드에 바로 코멘트할 수 있습니다
- 사용자를 멘션할 수 있고 태스크를 만들어서 할당할 수 있습니다

### 그 외의 기능들

- 글로벌 리뷰 대시보드
- 멀티 팩터 인증
- CI/CD 자동화
- 다양한 컨텐츠 리뷰

> 사실 코드 리뷰 서비스라 다른 기능에 대한 소개는 부가적인 내용들이어서 스킵했습니다 😈
> 중요한 것은 리뷰 시스템이 얼마나 기본에 충실하냐인 것 같아요

## Swarm 맛보기

[https://swarm.workshop.perforce.com/](https://swarm.workshop.perforce.com/)

Swarm workshop이라는 서비스를 Perforce에서 운영하고 있는데 Swarm 동작이 어떻게되는지 알 수 있습니다. Github 오픈소스 저장소처럼 어떻게 리뷰가 이뤄지고 코멘트가 어떻게 보이는지 알 수 있어요.

[https://swarm.workshop.perforce.com/explore/](https://swarm.workshop.perforce.com/explore/) 여기서 어떤 프로젝트가 있는지 볼 수 있으니 한번 개발이 활발한 프로젝트를 하나 들어가서 보겠습니다

Perforce 서버 쪽 패키지 관리 쪽 스크립트 저장소가 최근 활발했네요. 요것으로 보겠습니다.
[https://swarm.workshop.perforce.com/projects/perforce-software-sdp/reviews/](https://swarm.workshop.perforce.com/projects/perforce-software-sdp/reviews/)

![Swarm workshop](https://user-images.githubusercontent.com/5077086/155913427-e9ccea3d-2363-41ef-bf21-1629e6980e6a.png)

> 작업 내역을 보니 최근 커밋, 리뷰 요청을 한 분이 열심히하고 있군요 ㅎㅎ 😸

- 리뷰 페이지 상단에는 브랜치, 리뷰자 유무, 검토 필요/수정 필요/승인됨 등 리뷰 현황을 필터링할 수 있는 기능이 있습니다.
- 리뷰 진행 상황(열림/닫힘)에 따라 볼 수 있기도 하네요.

대부분의 기능이 Github과 비슷하긴 하지만 열림/닫힘으로 표현되어있으니 리뷰가 완료되서 머지가 된 것인지 알려면 닫힘 탭으로 가서 “승인됨” 상태로 필터링해야 “이건 머지가 되지 않았을까?” 알 수 있겠네요.
사실 정말 머지되었는지 알기는 어렵습니다. 승인만 되었지 실제 작업자가 머지 안했을 수 있으니까요.

![참고: Github Pull requests 화면](https://user-images.githubusercontent.com/5077086/155913430-180aea17-5961-4c21-ab04-91514700e311.png)

참고: Github Pull requests 화면

## 실제 Swarm 서비스 화면

![Swarm My dashboard](https://user-images.githubusercontent.com/5077086/155913434-98fc7e4a-ab81-4198-92fe-addc3af66d73.png)

![Swarm Project overview](https://user-images.githubusercontent.com/5077086/155913439-1eb9d01b-acb9-4fdc-9734-375fb0146392.png)

![Swarm Review screen](https://user-images.githubusercontent.com/5077086/155913436-b881e0f6-9303-44fc-bdaf-ed2843439510.png)

Swarm workshop 화면과 차이가 크지만 다른 소스 관리 서비스의 코드리뷰 기능과 비슷합니다.
다만 회사에서 사용할때 아쉬웠던 점은 코드에 맞춰 하이라이팅되는 것이 부족하다고 느꼈었네요.

## Swarm 가이드 문서

[https://swarm.workshop.perforce.com/docs/ko/](https://swarm.workshop.perforce.com/docs/ko/)

Perforce 쪽에서 만든 가이드 문서(한국어)가 있는데 2015년 문서네요. 😂
(영문 가이드 문서도 2016년 버전이라 사실상 관리가 잘 안되고 있는 것처럼 보입니다 ㅎㅎ..)

최신은 따로 Perforce쪽에 있으니 여기를 보시는게 나을 것 같습니다.
[https://www.perforce.com/manuals/swarm/Content/Swarm/home-swarm.html](https://www.perforce.com/manuals/swarm/Content/Swarm/home-swarm.html)

## 마무리

이렇게 Swarm을 짧게 살펴보았는데 그동안 다른 소스 관리 서비스에서 사용했던 코드 리뷰 시스템에 비해서 너무 날 것이 아닌가 싶기도 합니다. (뭔가 UI도 굉장히 옛날 것이고...)

최신 프론트엔드 UI 맛으로 업데이트할 계획은 없는지 궁금하지만 사실 뭐... 핵심 기능인 코드 리뷰가 잘 이뤄질 수만 있으면 된 것이겠죠 ㅎㅎ

다른 게임 개발사에서는 Swarm을 어떻게 쓰고 계신지 궁금하긴하네요.
다음에는 저희는 Swarm을 어떻게 구성해서 사용하고 있는지 살펴보고 포스트할 수 있는게 있다면 남겨보겠습니다. 감사합니다~