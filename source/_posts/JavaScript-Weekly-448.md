---
title: '주간 자바스크립트 #448'
toc: true
date: 2019-09-01 16:27:53
categories:
- Tech
- Javascript
tags:
- Javascript Weekly
thumbnail: https://user-images.githubusercontent.com/5077086/61992486-20028900-b09a-11e9-8e0b-3f4db9cac0ea.png
---

## Electron 6, String#replace 트릭과 JS에서의 스코프 학습

JavaScript Weekly Issue 448: August 2, 2019
본문: <https://javascriptweekly.com/issues/448>

![Hotkey](https://ci4.googleusercontent.com/proxy/rrLCycQx2Pi8mqIdZ7ApEmElTUkvobHeqRa-ZvS4yfSZGXI03She1B0WlU6Jrc5EVjiAtwLFeMzLsO-vFfXXLdIxd7_uei-I1hzleEgrdPvFrHBq3wsJ7YHFsJy3lwsoD8_VOcDyJVWECCk7Wi2vOiXkTCLT2U04tK8=s0-d-e1-ft#https://res.cloudinary.com/cpress/image/upload/w_1280,e_sharpen:60/v1564761454/yxzbmrchphu8andxdzrt.jpg)

### [Hotkey: 키보드에서 ‘핫키’가 눌렸을 때, 요소에 동작을 트리거하는 것](https://javascriptweekly.com/link/67833/063d4da45d)

<!-- Want quick and simple keyboard shortcuts for elements on your page? Set the `data-hotkey` attribute and use Hotkey. It even supports multiple keys pressed in sequence. GitHub built and uses it (view source on any GitHub page and look for the `data-hotkey` attributes). -->
페이지의 요소에 대한 빠르고 간단한 바로 가기 키를 원하십니까? `data-hotkey` 특성을 설정하고 핫키를 사용하십시오. 순차적으로 누르는 여러 개의 키를 지원하기도 한다. GitHub를 구축하여 사용(GitHub 페이지에서 소스 확인 및 `data-hotkey` 속성 확인)
`GITHUB`

### [Electron 6.0 릴리스](https://javascriptweekly.com/link/67834/063d4da45d)

<!-- Just 3 months after version 5 was released, the popular JavaScript-based cross-platform desktop app building platform hits version 6 and uses Chromium 76, Node 12.4, and V8 7.6 under the hood. -->
버전 5가 출시된 지 3개월 만에, 인기있는 JavaScript 기반 크로스 플랫폼 데스크탑 앱 구축 플랫폼은 버전 6에 도달했고 Chromium 76, Node 12.4 및 V8 7.6을 사용한다.
`ELECTRON.JS TEAM`

### [Jason Lengstorf와 함께 Gatsby 과정 소개](https://javascriptweekly.com/link/67835/web)

<!-- Build blazing 🔥 fast website by default with Gatsby. In this course, you'll build up a blog from scratch and deploy your brand new blog to Netlify for the world to see! -->
기본적으로 Gatsby를 사용하여 굉장히 🔥 빠른 웹 사이트를 구축하십시오. 이 과정에서는, 당신은 처음부터 블로그를 만들고, 당신의 새로운 블로그를 Netlify로 배포하여 세계가 볼 수 있도록 할 것이다!
`FRONTEND MASTERS SPONSOR`

### [당신은 `String.prototype.replace`가 치환 패턴을 지원하는지 알고 있습니까?](https://javascriptweekly.com/link/67836/web)

<!-- It feels a bit Perl-like, but this is an interesting feature I’d never seen in JavaScript before (despite [being in the MDN docs](https://javascriptweekly.com/link/67837/web)). Example: `'abc'.replace('b', '$&-$&') === 'ab-bc'`. -->
약간 Perl처럼 느껴지지만, 이것은 내가 전에 자바스크립트에서 본 적이 없는 흥미로운 기능이다. ([MDN에 문서가 있음에도](https://javascriptweekly.com/link/67837/web) 불구하고) 예시: `'abc'.replace('b', '$&-$&') === 'ab-bc'.`
`STEFAN JUDIS`

### [간단한 MVC 앱을 플레인 자바스크립트로 만들기](https://javascriptweekly.com/link/67875/web)

<!-- If you’re tired of hearing about React, Angular, Mithril, Ember, and the rest, and *just want to write JavaScript*, this is for you. (Ultimately, all of those frameworks are *very useful* but being able to work *without* them first will help you appreciate what they do!) -->
만약 여러분이 React, Angular, Mithrill, Ember, 그리고 나머지 것들에 대해 듣는 것에 싫증이 나서 자바스크립트를 쓰고 싶다면, 이것은 여러분을 위한 것이다. (궁극적으로, 그러한 모든 프레임워크들은 매우 유용하지만 그것들 없이 먼저 작업할 수 있다는 것은 그들이 하는 것에 감사하는 데 도움이 될 것이다!)
`TANIA RASCIA`

### [Comlink로 메인 스레드에서의 Redux 해제](https://javascriptweekly.com/link/67838/web)

<!-- Using Web Workers carefully can yield major UX and performance benefits by taking computation off of the UI thread. Here’s one way to do it when using Redux. -->
Web Workers를 주의깊게 사용하면 UI 스레드에서 계산을 제거하여 주요 UX 및 성능상의 이점을 얻을 수 있다. 여기 Redux를 사용할 때 할 수 있는 한 가지 방법이 있다.
`SURMA`

### 짧은 소식들

- [**VueConf US 2020**](https://javascriptweekly.com/link/67839/web)가 3월 2-4일 Texas에 Austin에서 열린다. CFP는 9월 1일에 열린다.
- Ember 프로젝트가 [**그들의 미래를 위한 로드맵을 발표했다.**](https://javascriptweekly.com/link/67840/web)
- [**Amazon Transcribe**](https://javascriptweekly.com/link/67841/web), AWS의 speech-to-text 서비스가 앞으로 [**웹소켓을 통한 스트리밍과 실시간 녹음을 지원한다.**](https://javascriptweekly.com/link/67842/web)
- Chrome은 앞으로 ‘[www’ 서브 도메인과 ‘https’ 형식을 URL이 쉽게 읽힐 수 있도록 주소창에서 숨기려한다.]((https://javascriptweekly.com/link/67843/web))
- Kyle Simpson가 그의 유명한 책 시리즈인 [**You Don't Know JavaScript**](https://javascriptweekly.com/link/67845/web)의 2번째 에디션 [작업을 시작했다](https://javascriptweekly.com/link/67844/web).

## 💻 채용 공고

채용 공고는 따로 번역하지 않습니다.

### [**JavaScript Developer at X-Team (Remote)**](https://javascriptweekly.com/link/67846/web)

Join the most energizing community for developers. Work from anywhere with the world's leading brands.
`X-TEAM`

### [**Front-end Engineer**](https://javascriptweekly.com/link/67847/web)

Goldstar is looking for front-end Engineers with React experience on-site in Portland, Oregon and Pasadena, California.
`GOLDSTAR`

### [**Get Hired Based on Your Skills Not Your CV**](https://javascriptweekly.com/link/67848/web)

Our AI makes it easier and quicker to match with top JavaScript jobs, with no recruiters and an average salary of £70k.
`HACKAJOB`

## 📘 튜토리얼, 오피니언, 영상

![자바스크립트에서 스코프](https://res.cloudinary.com/cpress/image/upload/w_1280,e_sharpen:60/v1564761084/p6agf327rmquaz6267h7.png)

### ▶ [자바스크립트에서 스코프에 대해 알아보자](https://javascriptweekly.com/link/67849/web)

<!-- Google’s dynamic JavaScript duo, Jake and Surma, present an entertaining chat about variable scoping, complete with tablet-based demos. -->
구글의 역동적인 자바스크립트 듀오 Jake와 Surma가 태블릿 기반의 데모를 완성한 변수 스코프와 관련된 재미있는 대화를 선보이고 있다.
`GOOGLE CHROME DEVELOPERS`

### [옵셔널 체이닝에 대한 ES 제안 보기](https://javascriptweekly.com/link/67850/web)

<!-- Boils down [the proposal](https://javascriptweekly.com/link/67851/web) to exactly the essentials you need to know. -->
당신이 알아야 할 필수 사항으로 [제안](https://javascriptweekly.com/link/67851/web)을 요약한다.
`DR. AXEL RAUSCHMAYER`

### [필요한 측정 지표를 잃지 않기 위한 개발자 가이드](https://javascriptweekly.com/link/67852/web)

<!-- Gathering and storing metrics is a part of production. When adverse events occur, you need to have the metrics available to debug the problems. -->
측정 지표를 수집하고 저장하는 것은 생산의 일부분이다. 안좋은 사건이 발생할 때, 당신은 문제를 디버깅하기 위해 이용할 수 있는 지표를 가질 필요가 있다.
`INFLUXDATA SPONSOR`

### [React Hook이 Redux를 대체하는가?](https://javascriptweekly.com/link/67853/web)

<!-- This question has bounced around in the community a lot recently as more use cases for hooks emerge.. but Eric’s TLDR is *‘Hooks are Great, but No.’* and he explains why in depth. -->
이 질문은 최근 커뮤니티에서 훅(hook) 사용 사례가 증가함에 따라 자주 제기되었다. 그러나 Eric의 TLDR은 '훅은 위대하지만, 대체할 수 없다'이며, 그 이유를 심도 있게 설명한다.
`ERIC ELLIOTT`

### [Vuetify 2.0 시작하기](https://javascriptweekly.com/link/67854/web)

<!-- [Vuetify](https://javascriptweekly.com/link/67855/web) is a Material Design-based component library for Vue.js. -->
[Vuetify](https://javascriptweekly.com/link/67855/web)는 Vue.js를 위한 머터리얼 디자인 기반 구성요소 라이브러리이다.
`BEN HONG`

### [Jest를 사용한 유닛 테스트 시 Mock 사용을 위한 빠른 팁](https://javascriptweekly.com/link/67856/web)

`DANIEL CALDAS`

### [자바스크립트에서 최상위 함수들](https://javascriptweekly.com/link/67857/web)

<!-- A brief tutorial aimed at beginners who might be wondering why being able to treat functions as first-class citizens (i.e. as objects in their own right) has merit. -->
왜 1등 시민으로서의 기능(즉, 그 나름대로의 물건으로서)을 취급할 수 있는지 궁금해 하는 초심자를 대상으로 하는 간단한 튜토리얼은 장점이 있다.
`NICK SCIALLI`

### [상위 10개의 GitHub 모범 사례 - 수천 개의 저장소에서 얻은 교훈](https://javascriptweekly.com/link/67858/web)

`DATREE.IO SPONSOR`

### [나의 VS Code 설정: VS Code를 최대한 활용](https://javascriptweekly.com/link/67859/web)

<!-- A grab bag of addons and tools to consider if you’re a VS Code user. -->
VS Code 사용자라면 고려할만한 추가 기능 및 툴.
`DEEPU K SASIDHARAN`

### [RxJS Observable을 이해하고 왜 필요한지](https://javascriptweekly.com/link/67860/web)

<!-- [RxJS](https://javascriptweekly.com/link/67861/web) is a reactive programming library based around ‘observables’ and is used by Angular for its reactivity.. but you can use it separately too. -->
[RxJS](https://javascriptweekly.com/link/67861/web)는 'observables'을 기반으로 하는 반응형 프로그래밍 라이브러리로서, Angular가 반응성을 위해 사용한다. 따로 쓸 수도 있다.
`NWOSE LOTANNA`

## 🔧 코드와 도구들

### [Hackathon Starter: Node 웹 앱용 보일러 플레이트](https://javascriptweekly.com/link/67862/web)

<!-- A boilerplate for when you want to start building a Node app *quickly* (such as at a hackathon) as it includes almost everything you’d need. -->
필요한 거의 모든 것이 포함되어 있기 때문에 (해커톤과 같은) Node 앱을 빠르게 만들기 시작할 때 사용하는 보일러 플레이트.
`SAHAT YALKABOV`

### [Esprint: 여러 스레드 간에 ESLint를 실행하여 성능 향상](https://javascriptweekly.com/link/67863/web)

<!-- It’s been [considered](https://javascriptweekly.com/link/67864/web) that this could be merged into ESLint itself. -->
이것은 ESLint로 [통합될 수 있다고 여겨져 왔다](https://javascriptweekly.com/link/67864/web).
`PINTEREST`

### [병합하기 전에 코드가 오류 없는지 확인하십시오](https://javascriptweekly.com/link/67865/web)

<!-- Set standards on coverage, duplication, complexity, and style issues and see real-time feedback in your Git workflow. -->
적용 범위, 중복, 복잡성 및 스타일 문제에 대한 표준을 설정하고 Git 워크플로우에서 실시간 피드백을 확인하십시오.
`CODACY SPONSOR`

### [Treeverse: 트리 구조를 깊이 또는 면적을 먼저 걷기](https://javascriptweekly.com/link/67866/web)

`ISAAC Z SCHLUETER`

### [Rollup: 최신 ES6 모듈 번들러](https://javascriptweekly.com/link/67867/web)
<!--Not a new project, but it's been getting plenty of releases lately. Write your code using ES modules and get tree-shaking/dead code elimination and bundling to the format you require. One of Rollup’s wins over more popular alternatives is its speed.-->
새로운 프로젝트는 아니지만, 최근에 많이 릴리스되고 있다. ES 모듈을 사용하여 코드를 작성하고 트리 흔들기/죽은 코드를 삭제하고 필요한 형식으로 번들링하십시오. Rollup이 더 인기 있는 대안들에 비해 이긴 것 중 하나는 **속도**다.
`ROLLUP CONTRIBUTORS`

### [WebStorm 및 IntelliJ용 자바스크립트 플러그인 상위 25개](https://javascriptweekly.com/link/67868/web)

`ILANA BRUDO`

## ⚡️ 릴리스 요약

- **Font Awesome 5.10.0** — 유명한 아이콘 툴킷.
- **webpack 4.39.0** — '웬만한 건 빼고 거의 다 있는' 번들러.
- **TUI Editor 1.4.5** — 마크다운 기반의 WYSIWYG 에디터.
- **Spectacle 5.7** — \React.js 기반 프레젠테이션 라이브러리.
- **Duktape 2.4** — C/C++ 프로젝트를 위한 내장형 자바스크립트 엔진.
