---
title: fisheye webhook error (with node.js)
categories:
  - Tech
date: 2019-04-20 17:09:42
tags:
---


## Fisheye Webhook 에러 수정

SVN, Git과 같은 버전관리 프로그램에 기록되는 커밋(리비전) 내역을 트래킹해주는
`Fisheye`를 회사에서 사용 중에 Webhook 기능이 있어 사용하다 에러를 만나게 되어 해결 방법을 남겨봅니다.
저는 Node.js + Express로 웹훅을 받아 처리할 때 문제가 있었습니다.

Fisheye에 대한 자세한 내용은 추후 다른 포스트에서 남겨보겠습니다. :)

## Webhook 기본 설정

Fisheye에서 웹훅을 설정하는 방법은 간단합니다.
아래 링크를 참고하여 웹훅을 설정합니다.
<https://confluence.atlassian.com/fisheye/configuring-web-hooks-960155631.html>

## Webhook을 받기 위한 Node.js + Express 서버 구성

간단한 서버 어플리케이션을 만들어서 웹훅을 받아봅니다.
POST 요청을 받을 수 있도록 만들고 Test 기능으로 웹훅을 보내 보았습니다.

그랬더니 아래와 같은 에러가 생겼습니다.

```
POST /test/webhook 415 4.796 ms - 1426
UnsupportedMediaTypeError: unsupported content encoding "utf-8"
    at contentstream (C:\Users\pineoc\Desktop\private\pino-bot\node_modules\body-parser\lib\read.js:174:13)
    at read (C:\Users\pineoc\Desktop\private\pino-bot\node_modules\body-parser\lib\read.js:54:14)
    at jsonParser (C:\Users\pineoc\Desktop\private\pino-bot\node_modules\body-parser\lib\types\json.js:134:5)
    at Layer.handle [as handle_request] (C:\Users\pineoc\Desktop\private\pino-bot\node_modules\express\lib\router\layer.js:95:5)
    at trim_prefix (C:\Users\pineoc\Desktop\private\pino-bot\node_modules\express\lib\router\index.js:317:13)
    at C:\Users\pineoc\Desktop\private\pino-bot\node_modules\express\lib\router\index.js:284:7
    at Function.process_params (C:\Users\pineoc\Desktop\private\pino-bot\node_modules\express\lib\router\index.js:335:12)
    at next (C:\Users\pineoc\Desktop\private\pino-bot\node_modules\express\lib\router\index.js:275:10)
    at logger (C:\Users\pineoc\Desktop\private\pino-bot\node_modules\morgan\index.js:144:5)
    at Layer.handle [as handle_request] (C:\Users\pineoc\Desktop\private\pino-bot\node_modules\express\lib\router\layer.js:95:5)
```

이런 에러는 또 처음이라 좀 더 확인해보았습니다.
(제 코드 상에 문제라기 보다 웹훅에서 보내주는 데이터 쪽과 맞춰야하는 문제로 보였기 때문입니다.)

## `UnsupportedMediaTypeError` 에러 확인 및 해결 시도

에러 내용은 저에게는 생소해서 구글에서 관련 에러를 검색해보았습니다.
`UnsupportedMediaTypeError: unsupported content encoding "utf-8"`를 검색해보니
아래와 같은 글들이 나왔습니다.

- Content-Encoding issue: <https://github.com/expressjs/body-parser/issues/100>
- unsupported content encoding "utf-8": <https://github.com/Strider-CD/strider/issues/1021>

몇 가지 글을 보았을 때는 Body-parser 쪽에 문제가 있어서 안되는 것으로 예상하여 아래와 같이 해결해보려 했습니다만,
첫 번째 글을 보면 `Request Header 값 중 "Content-Encoding: UTF-8"를 빼면 해결되지 않을까?` 하는 질문이 있습니다.

바로 아래에는 헤더 값을 제거하는 코드가 답변으로 달렸죠.

```js
//...
app.use(function (req, res, next) {
  // remove invalid header
  delete req.headers['content-encoding'];
  next();
});
app.use(express.json());
app.use(express.urlencoded({ extended: false }));
// ...
```

이렇게 설정하고 웹훅 데이터를 받아보았더니 해결되었습니다.

## `Content-Encoding: UTF-8`?

`Content-Encoding: UTF-8` 는 뭐길래 에러가 났을까 확인해보았습니다.
우선 `Content-Encoding`이라는 헤더는 `미디어 타입을 압축`하기 위해 사용되는 값입니다.
참고: <https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Content-Encoding>

Content-Encoding은 주로 아래와 같이 사용되죠.
```
Content-Encoding: gzip
Content-Encoding: compress
Content-Encoding: deflate
Content-Encoding: identity
Content-Encoding: br
```

위 사용 방법에 따르면 `UTF-8` 값은 유효하지 않은 값입니다. (Invalid)
UTF-8 인코딩 혹은 문자 인코딩을 요청에 표현하고 싶다면 아래와 같이 표현해야합니다.
참고: <https://www.w3.org/International/questions/qa-headers-charset.ko>
```
Content-Type: text/html; charset=utf-8
```

## 문제 해결

해결 방법은 그렇게 어렵지 않았지만 해결하면서 다양한 내용을 알게되어서 좋았습니다.
+문제 없이 웹훅도 사용할 수 있게되어서 더 좋았죠. :)

- `Request Header` 유효성 문제
- `Content-Encoding` 헤더 값 사용 방법
- `Content-Type` 헤더 값 사용 방법

다른 웹훅을 등록하거나, 웹훅 시스템을 만들 때 고려해야하는 내용이었습니다.
