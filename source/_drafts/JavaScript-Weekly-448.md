---
title: '주간 자바스크립트 #448'
toc: true
date: 2019-08-07 22:10:53
categories:
- Tech
- Javascript
tags:
- Javascript Weekly
thumbnail: https://user-images.githubusercontent.com/5077086/61992486-20028900-b09a-11e9-8e0b-3f4db9cac0ea.png
---

## Electron 6, a String#replace trick, and learning about scope in JS

JavaScript Weekly Issue 448: August 2, 2019
본문: <https://javascriptweekly.com/issues/448>

![](https://ci4.googleusercontent.com/proxy/rrLCycQx2Pi8mqIdZ7ApEmElTUkvobHeqRa-ZvS4yfSZGXI03She1B0WlU6Jrc5EVjiAtwLFeMzLsO-vFfXXLdIxd7_uei-I1hzleEgrdPvFrHBq3wsJ7YHFsJy3lwsoD8_VOcDyJVWECCk7Wi2vOiXkTCLT2U04tK8=s0-d-e1-ft#https://res.cloudinary.com/cpress/image/upload/w_1280,e_sharpen:60/v1564761454/yxzbmrchphu8andxdzrt.jpg)


[**Hotkey: Trigger an Action on an Element When a Keyboard 'Hotkey' is Pressed**](https://javascriptweekly.com/link/67833/063d4da45d) — Want quick and simple keyboard shortcuts for elements on your page? Set the `data-hotkey` attribute and use Hotkey. It even supports multiple keys pressed in sequence. GitHub built and uses it (view source on any GitHub page and look for the `data-hotkey` attributes).
GITHUB

[**Electron 6.0 Released**](https://javascriptweekly.com/link/67834/063d4da45d) — Just 3 months after version 5 was released, the popular JavaScript-based cross-platform desktop app building platform hits version 6 and uses Chromium 76, Node 12.4, and V8 7.6 under the hood.
ELECTRON.JS TEAM

[**New Introduction to Gatsby Course with Jason Lengstorf**](https://javascriptweekly.com/link/67835/web) — Build blazing 🔥 fast website by default with Gatsby. In this course, you'll build up a blog from scratch and deploy your brand new blog to Netlify for the world to see!
FRONTEND MASTERS SPONSOR

[**Did You Know**](https://javascriptweekly.com/link/67836/web) `[String.prototype.replace](https://javascriptweekly.com/link/67836/web)` [**Supports Replacement Patterns?**](https://javascriptweekly.com/link/67836/web) — It feels a bit Perl-like, but this is an interesting feature I’d never seen in JavaScript before (despite [being in the MDN docs](https://javascriptweekly.com/link/67837/web)). Example: `'abc'.replace('b', '$&-$&') === 'ab-bc'`.
STEFAN JUDIS

[**Writing a Simple MVC App in**](https://javascriptweekly.com/link/67875/web) [***Plain***](https://javascriptweekly.com/link/67875/web) [**JavaScript**](https://javascriptweekly.com/link/67875/web) — If you’re tired of hearing about React, Angular, Mithril, Ember, and the rest, and *just want to write JavaScript*, this is for you. (Ultimately, all of those frameworks are *very useful* but being able to work *without* them first will help you appreciate what they do!)
TANIA RASCIA

[**Taking Redux Off of the Main Thread with Comlink**](https://javascriptweekly.com/link/67838/web) — Using Web Workers carefully can yield major UX and performance benefits by taking computation off of the UI thread. Here’s one way to do it when using Redux.
SURMA

**Quick bytes:**

- [**VueConf US 2020**](https://javascriptweekly.com/link/67839/web) is taking place on March 2-4 in Austin, Texas. The CFP opens on September 1.
- The Ember project has [**published a roadmap for its future.**](https://javascriptweekly.com/link/67840/web)
- [**Amazon Transcribe**](https://javascriptweekly.com/link/67841/web), AWS's speech-to-text service, [**now supports WebSockets for streaming, real-time transcription.**](https://javascriptweekly.com/link/67842/web)
- Chrome is [**going to hide the 'www' subdomain**](https://javascriptweekly.com/link/67843/web) and 'https' scheme in its location bar to make URLs 'easier to read'.
- Kyle Simpson [**has started work**](https://javascriptweekly.com/link/67844/web) on the 2nd edition of his popular [**You Don't Know JavaScript**](https://javascriptweekly.com/link/67845/web) book series.


## 💻 Jobs

[**JavaScript Developer at X-Team (Remote)**](https://javascriptweekly.com/link/67846/web) — Join the most energizing community for developers. Work from anywhere with the world's leading brands.
X-TEAM

[**Front-end Engineer**](https://javascriptweekly.com/link/67847/web) — Goldstar is looking for front-end Engineers with React experience on-site in Portland, Oregon and Pasadena, California.
GOLDSTAR

[**Get Hired Based on Your Skills Not Your CV**](https://javascriptweekly.com/link/67848/web) — Our AI makes it easier and quicker to match with top JavaScript jobs, with no recruiters and an average salary of £70k.
HACKAJOB


## 📘 Tutorials, Opinions, and Videos
![](https://res.cloudinary.com/cpress/image/upload/w_1280,e_sharpen:60/v1564761084/p6agf327rmquaz6267h7.png)


**▶**  [**Let's Learn About Scope in JavaScript**](https://javascriptweekly.com/link/67849/web) — Google’s dynamic JavaScript duo, Jake and Surma, present an entertaining chat about variable scoping, complete with tablet-based demos.
GOOGLE CHROME DEVELOPERS

[**Looking at the Optional Chaining ES Proposal**](https://javascriptweekly.com/link/67850/web) — Boils down [the proposal](https://javascriptweekly.com/link/67851/web) to exactly the essentials you need to know.
DR. AXEL RAUSCHMAYER

[**The Developer’s Guide to Not Losing the Metrics You Need**](https://javascriptweekly.com/link/67852/web) — Gathering and storing metrics is a part of production. When adverse events occur, you need to have the metrics available to debug the problems.
INFLUXDATA SPONSOR

[**Do React Hooks Replace Redux?**](https://javascriptweekly.com/link/67853/web) — This question has bounced around in the community a lot recently as more use cases for hooks emerge.. but Eric’s TLDR is *‘Hooks are Great, but No.’* and he explains why in depth.
ERIC ELLIOTT

[**Getting Started with Vuetify 2.0**](https://javascriptweekly.com/link/67854/web) — [Vuetify](https://javascriptweekly.com/link/67855/web) is a Material Design-based component library for Vue.js.
BEN HONG

[**Quick Tips for Using Mocks when Unit Testing with Jest**](https://javascriptweekly.com/link/67856/web)
DANIEL CALDAS

[**First-Class Functions in JavaScript**](https://javascriptweekly.com/link/67857/web) — A brief tutorial aimed at beginners who might be wondering why being able to treat functions as first-class citizens (i.e. as objects in their own right) has merit.
NICK SCIALLI

[**Top 10 GitHub Best Practices - Lessons from Thousands of Repositories**](https://javascriptweekly.com/link/67858/web)
DATREE.IO SPONSOR

[**My VS Code Setup: Making The Most Out of VS Code**](https://javascriptweekly.com/link/67859/web) — A grab bag of addons and tools to consider if you’re a VS Code user.
DEEPU K SASIDHARAN

[**Understanding RxJS Observables and Why You Need Them**](https://javascriptweekly.com/link/67860/web) — [RxJS](https://javascriptweekly.com/link/67861/web) is a reactive programming library based around ‘observables’ and is used by Angular for its reactivity.. but you can use it separately too.
NWOSE LOTANNA


## 🔧 Code and Tools

[**Hackathon Starter: A Boilerplate for Node Web Apps**](https://javascriptweekly.com/link/67862/web) — A boilerplate for when you want to start building a Node app *quickly* (such as at a hackathon) as it includes almost everything you’d need.
SAHAT YALKABOV

[**Esprint: Runs ESLint Across Multiple Threads for More Performance**](https://javascriptweekly.com/link/67863/web) — It’s been [considered](https://javascriptweekly.com/link/67864/web) that this could be merged into ESLint itself.
PINTEREST

[**Ensure That Your Code Is Error-Free Before Merging**](https://javascriptweekly.com/link/67865/web) — Set standards on coverage, duplication, complexity, and style issues and see real-time feedback in your Git workflow.
CODACY SPONSOR

[**Treeverse: Walk Tree Structures Depth- or Breadth-First**](https://javascriptweekly.com/link/67866/web)
ISAAC Z SCHLUETER

[**Rollup: A Modern ES6 Module Bundler**](https://javascriptweekly.com/link/67867/web) — Not a new project, but it's been getting plenty of releases lately. Write your code using ES modules and get tree-shaking/dead code elimination and bundling to the format you require. One of Rollup’s wins over more popular alternatives is its *speed*.
ROLLUP CONTRIBUTORS

[**Top 25 JavaScript Plugins for WebStorm and IntelliJ**](https://javascriptweekly.com/link/67868/web)
ILANA BRUDO


## ⚡️ Quick Releases
- [**Font Awesome 5.10.0**](https://javascriptweekly.com/link/67869/web) — The popular icon toolkit.
- [**webpack 4.39.0**](https://javascriptweekly.com/link/67870/web) — 'everything but the kitchen sink' bundler.
- [**TUI Editor 1.4.5**](https://javascriptweekly.com/link/67871/web) — Markdown-based WYSIWYG editor.
- [**Spectacle 5.7**](https://javascriptweekly.com/link/67872/web) — React.js-based presentation library.
- [**Duktape 2.4**](https://javascriptweekly.com/link/67873/web) — Embeddable JavaScript engine for C/C++ projects.