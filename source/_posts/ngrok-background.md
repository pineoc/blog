---
title: 꺼지지 않는 백그라운드 ngrok 실행기
toc: true
date: 2021-01-25 23:55:48
categories:
- Tech
- Program&Service
tags:
- ngrok
thumbnail: https://ngrok.com/static/img/ngrok-black.svg
---

## ngrok?

<https://ngrok.com/>

간단하게 설명하면 로컬에서 실행중인 서비스를 터널링(포워딩)해주는 서비스입니다.
저는 주로 간단하게 만든 웹서비스를 잠깐 외부에서 테스트하거나 시연할 때 사용하곤합니다.
근데 ngrok은 자꾸 껐다 켰다 하기에 귀찮아서 백그라운드로 오래 돌릴 방법이 없나 찾아보게되었어요.

긴 글을 읽기 귀찮으신분들은 요약만 읽어주시면 알 수 있습니다. 😸

## 꺼지지 않는 백그라운드 ngrok 실행기 요약

1. `./ngrok http 80 -log=stdout > ngrok.log &`
  - 그냥 백그라운드 실행 옵션으로 실행할 수는 있습니다.
  - 터미널이 닫히면 ngrok도 같이 꺼집니다.
2. `screen`을 사용해서 `./ngrok http 80 -log=stdout > ngrok.log &`
  - 스크린을 사용하더라도 스크린을 사용하던 터미널이 닫히면 ngrok도 같이 꺼집니다.
3. 그냥 터미널 끄지말고 ngrok 백그라운드 상태로 두고 사용하자..

## 꺼지지 않는 백그라운드 ngrok 실행?

우선 ngrok으로 터널링 하는 방법은 서비스 페이지에 잘 나와있으니 백그라운드로 실행하는 방법에 대해 고민해보았습니다.
ngrok을 4000 포트로 http 터널링을 하기 위해서 아래와 같이 실행할 수 있습니다.

```sh
$ ngrok http 4000
ngrok by @inconshreveable                    (Ctrl+C to quit)

Session Status                online
Account                       Allen Yunseok Lee (Plan: Basic)
Version                       2.3.35
Region                        United States (us)
Web Interface                 http://127.0.0.1:4040
Forwarding                    http://4a3ed4201b8f.ngrok.io -> http://localhost:4000
Forwarding                    https://4a3ed4201b8f.ngrok.io -> http://localhost:4000

Connections                   ttl     opn     rt1     rt5     p50     p90
                              0       0       0.00    0.00    0.00    0.00
```

> 무료 버전은 포워딩을 랜덤으로 받는 것이 기본 옵션이고 결제를 하게되면 서브 도메인에 이름을 정해서 포워딩할 수 있습니다.

### Take #1

근데 이렇게 실행하고 나서 다른 작업을 위해 이 터미널을 닫으면 그대로 포워딩이 풀려버립니다.
처음엔 이걸 유지하기 위해 간단히 백그라운드 실행을 해보았죠.

```sh
$ ./ngrok http 80 -log=stdout > ngrok.log &
[1] 76732
```

이렇게 하고 ngrok.log 파일을 보고 URL에 접속하면 포워딩이 잘되는 것을 확인했습니다.
다만 이것도 터미널을 닫으면 포워딩이 풀리는 것은 마찬가지였습니다. 😂

### Take #2

사실 원했던 것은 ngrok을 백그라운드로 계속 돌려두고 싶었던 것인데 방법이 없을까 찾아보았습니다.
(터미널에 종속되지 않고 백그라운드로 돌아가는 서비스 말이죠.)

그래서 screen 명령어를 사용해서 터미널을 백그라운드처럼 두고 하면 어떨까 싶어서 시도해보았습니다.
(없다면 설치해야하는 명령어입니다.)

```sh
$ screen a
$ ./ngrok http 80 -log=stdout > ngrok.log &
# Ctrl-a, d를 입력하면 터미널에서 나오게됩니다.
```

이렇게 하면 스크린이 백그라운드에 떠있고 그 뒤에 ngrok이 실행되겠지 했지만...
터미널 끄면 마찬가지로 꺼지게됩니다. 😂 😂 😂

### Take #3

ngrok 서비스에 뭔가 없나하고 찾아보게 되었습니다.
[stack overflow: How to keep ngrok running even when signing off of a server](https://stackoverflow.com/questions/50681671/how-to-keep-ngrok-running-even-when-signing-off-of-a-server) 글도 보고 찾아보게 되었죠.

[Installing ngrok as a service](https://ngrok.com/docs/ngrok-link#service)에서 ngrok을 서비스 형태로 설치하는 방법에 대한 것인데 알고보니 ngrok link는 엔터프라이즈 서비스로 돈을 `많이` 내고 써야하는 물건이어서 이것도 실패했네요. 🔥

## 끝

더 찾아보고 시도해봤지만 더 좋은 방법은 나오지 않아서 결론은...

> ngrok을 실행한 터미널을 끄지말고 백그라운드 정도로만 ngrok을 사용하자.

로 결론을 내고 포스트를 마무리해봅니다. 🤭
시도는 다 보실 필요 없으니 위에 요약만 보셔도 되었겠네요. 여기까지 읽어주셔서 고맙습니다. 😸

> 혹시 다른 방법이 있다면 댓글로 알려주세요!
