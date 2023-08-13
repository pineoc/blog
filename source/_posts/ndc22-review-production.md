---
title: NDC22 프로덕션 발표 리뷰 - 피파 온라인4 라이브 서비스
toc: true
date: 2022-06-18 22:40:59
categories:
- PM
- Work
tags:
- Project management
- NDC
---

## NDC22 발표 리뷰

![](https://user-images.githubusercontent.com/5077086/174442099-2457aa21-d640-47a8-aa20-32d40aec5f7b.png)

6월에 여러 컨퍼런스가 있었는데 게임 업계 프로덕션 직군에서 일하는 사람이니 NDC 프로덕션 내용들은 잘 챙겨서 봐야겠다 싶어서 보면서 슬쩍 정리해보았습니다.

리뷰라고 말하긴했지만 배울 것과 우리 조직, 프로덕션 상황을 같이 보면서 되돌아볼 수 있는 것들이 있어 흥미롭게 발표를 보았어요. ㅎㅎ

## Youtube link

[https://www.youtube.com/watch?v=rK83XrOU5Bg](https://www.youtube.com/watch?v=rK83XrOU5Bg)

## 리뷰

처음에는 피파 온라인 서비스를 오래 운영한 팀의 이야기가 궁금해서 들어보았는데 외부에 공유할 수 있는 만큼 잘 정제(?)해서 공유해주셨구나 싶었습니다.

> 조직 구조, 업무 방식을 외부에 공유한다는게 긍정적인 것 보다 우려가 많을 수 있는데 적당히 추상화해서 공유해서 가능했던 걸까 싶었네요.

- **서비스 기간**
    - 피파 온라인4는 2018년 부터 서비스한 게임이지만 피파 온라인 시리즈는 발표에서 말하길 16년차된 서비스로 소개해주셨습니다.
    - 히스토리를 좀 확인해보았더니 피파 온라인1은 2006년에 런칭했었네요. 1부터 보면 16년차 맞습니다. ㅎㅎ
    - 게임을 개발하고 서비스하면서 어떤 어려움들이 있었을까, 어떤 그림자들이 있었을까 궁금하기도 했네요.
- **조직 구조** - 약 150명 정도
    - 조직 구조는 기능 조직으로 구성하고 모든 기능 조직들을 묶는 Line 조직에 PD를 두는 것으로 보이네요.
    - PD 중심으로 기능적으로 조직을 구성하고 조직에 시니어들은 매니저 부담을 덜고 개인과 주니어의 커리어와 제작의 퀄리티를 담당하게 한 것에 대해 매니저(DD)와 시니어를 분리해서 평가 체계를 가져간 것이 신기했습니다
- **2개의 개발팀(Meta/Core) 로테이션**
    - 라이브팀 운영을 해보려했지만 개발자들은 콘텐츠를 만들고 싶어하는 경향과 라이브팀 운영 특성상 노령화가 될 수 밖에 없고 해보았으나 조직 운영에 어려움이 있었던 것 같았습니다.
    - 3, 6개월 단위의 업데이트도 시도해보았지만 라이브 대응이 어려웠다고 합니다.
    (이슈 대응과 업데이트는 다른 카테고리의 이슈인데 왜 그 단위만큼 늘어지는 구조를 사용했었을까하는 의문이 있었네요. 🤔)
- **의사결정**
    - 앞에서 조직 구조 이야기하면서 PD 중심의 조직이 있고 그 조직에는 모든 직군팀이 있다고 했었습니다. 이에 따라 기능 조직을 모았지만 목적 조직 아래에 기능 조직이 모인 형태로 이해했어요.
    - 이런 목적 조직 구조의 특성상 의사결정 속도는 빠르게 이뤄질 수 있겠다 싶었습니다.
- **프로덕션 프로세스**
    - 각 프로세스 단계의 정의와 결과물의 정의를 깔끔하게 했다는 인상을 받았습니다. 라이브 서비스를 오래했던 만큼 프로세스가 잘 닦여있다는 인상을 받았어요.
    - 각 프로세스에서 진행되는 일에 대해 다이어그램으로 표현한 것을 보면서 우리도 저런게 잘 정리되면 좋겠다 싶었습니다.
    - Hardening 이라는 표현은 생소했는데 피파 온라인팀에서는 퍼블리셔와 함께 빌드가 단단한지 확인하고 문제가 있다면 수정하는 단계 정도로 정의한게 신기했습니다. (우리는 릴리스 준비 정도로 간략히 정리해볼 수 있겠다 싶었네요)
- **라이브 이슈 대응 우선순위**
    - 가이드 문서에서 기억에 남는 것은 이슈 우선순위에 따라 대응을 며칠 전까지 해야하는가에 대해 정의되어있었다는 점이네요. 추가로 연락 방법도! (전화, 메일, Jira 이런식으로 나눠짐)
    - 라이브 이슈 대응 우선순위 가이드라인 내용이 우리도 필요하겠다 싶었습니다
- **라이브 서비스 플랜**
    - 롱텀 플랜을 만들고 명확한 기준으로 개발, 출시하고 있는데 피파 온라인 게임 콘텐츠 특성상 현실세계 시즈널 이벤트들이 있고 그에 맞춰 계획, 개발하고 있다고 합니다.
    - 개인적인 생각으로는 코로나 영향으로 축구 경기도 연기되고 하느라 이벤트 대응에 이슈가 있었지 않았을까 싶긴했네요. 😂

## 발표 내용 노트

### 개발팀 구조

- 22년 조직 변경 방향성: 직능적 구조(직군 모임)로 바꾸고 매니저 역할(목표 관리), 시니어 역할(업무 관리, 퀄리티 관리) 나눠서 결정을 빠르게하고 대응함
- Core, Meta, Codev 등 직군별로 팀을 나누고 PD 중심 기능적으로 조직을 변경
- 2개의 프로덕션팀 - Core, Meta
    - Core: Fun, Competitive Gaming, Core Ex 등 UI/UX 개발
    - Meta: 프로그레션, 라이브 서비스, 유료화, 개인화 경험 개발
    - 2개의 프로덕션팀은 2개월 로테이션으로 콘텐츠 개발, 라이브 서비스를 돌아가면서 대응함
        ![](https://user-images.githubusercontent.com/5077086/174441506-5c06f100-27de-4a5b-8249-ee9b777f85a5.png)
    - 버그 대응: 본인의 팀에서 개발한 콘텐츠 버그는 콘텐츠 개발팀에서 수정한다
- 스페셜팀(DET): 개발환경 개선, 인프라 개선 등 긴 호흡으로 스페셜한 영역의 일을 함
- Art, CODEV 등 팀이 있음
- 우리와 비슷한 이슈
    - 버그 수정하더라도 1-2달 뒤에나 수정한 것을 배포할 수 있었음

### Work Process

![](https://user-images.githubusercontent.com/5077086/174441505-f9313a15-311b-4521-bd89-862e4a32048e.png)

- High-level Roadmap
    - 로드맵을 만들 때 PD는 어떤 것을 개발할지 결정
    - GD는 콘텐츠 목표, 방향성을 정의
- Pre-Planning
    - 피쳐에 대한 상세 정의
    - 결과물: IDD, PDD, FDD 등 디자인 문서
- Planning
    ![](https://user-images.githubusercontent.com/5077086/174441501-b404ef22-b458-441d-a76d-e58532fb55e9.png)
    - Pre Planning 하면서 이미 유관부서는 컨텍스트를 알고 있기에 안정적인 계획을 할 수 있음
    - 결과물: FDD 기준으로 만들어진 TDB(기술 문서), 로그 설계 문서, 테스트 설계 문서
- Development
    - 진짜 개발, 프로덕션 시작
    - 개발하면서 사전 테스트 프로세스를 진행하여 안정성을 올림
- Debugging
    - 테스트 문서를 기반으로 디버깅 진행
    - QA팀은 빌드 내에서 전체 기능 테스트 진행. 목표는 퍼블리셔 스테이징 환경에서 진행할 QA를 위해 빌드를 준비하는 것
- Hardening
    - 퍼블리셔 시스템, 모바일 플랫폼 확인 등 빌드 유효성 검증 테스트
    - 결과물: 최종 빌드, 빌드 노트, 점검 노트
- Release / Live Support
    - 릴리스 모니터링 및 피쳐 분석
    - 버그 모니터링 후 핫픽스, 다음 패치 목표를 결정하기도 함
    - 결과물: 피쳐 분석 리포트, 유저 피드백들

![](https://user-images.githubusercontent.com/5077086/174441502-d3e66382-3cae-4e0b-ae4f-10a8e8bdbd88.png)

![](https://user-images.githubusercontent.com/5077086/174441503-c176bd05-b569-47ee-8b98-02a5f8b02236.png)

![](https://user-images.githubusercontent.com/5077086/174441504-d0d748aa-75fd-4d65-9999-a918fad2d774.png)

피파온라인은 16년 동안 서비스한 게임으로 지금의 조직 구조가 탄탄하다고 평가하고 있음
2022년 목표로 피파온라인을 완성해보려하고 있음

## 마무리

NDC에서 소중한 프로덕션 사례를 발표해주신 EA Korea, 피파 온라인팀에 감사한 마음으로 보았습니다.
사실 프로덕션, 내부 조직 구조 내용은 발표나 자료들을 찾아보기 쉽지 않은데요.
이렇게라도 다른 개발 조직은 어떻게 살아가고 있는지 알 수 있어서 좋았습니다. 👍
이 포스트 이후에 팀 내부에 우리 조직과의 차이점, 배울점을 고민해보면 좋을 것 같다는 생각이 들었네요.
이만 포스트를 마치겠습니다. 🙏