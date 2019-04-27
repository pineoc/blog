---
title: ScriptRunner 소개 3
date: 2019-04-27 18:55:29
categories:
  - JIRA
  - PM
tags:
---

## ScriptRunner 소개 #3

- 소개 #1: <https://pineoc.github.io/blog/2019/04/21/scriptrunner1/>
- 소개 #2: <https://pineoc.github.io/blog/2019/04/21/scriptrunner2/>

지난 #2 소개 글에서는 Script Fields 기능까지 보았고
그 다음에 있는 아래 리스트의 기능들을 보겠습니다.

- REST Endpoints
- Script Fragments
- Escalation Services
- Script JQL Functions

소개 글을 쓰는 도중에 JIRA 시스템 버전이 7에서 8로 올라가는 과정에서 UI, 기능이 약간 변경되었습니다.
버전 변경에 따라 큰 차이는 없겠지만 참고해주세요. :)

- JIRA version: 7.13 -> 8.0
- ScriptRunner: 5.5.2 -> 5.5.3

## REST Endpoints

<https://scriptrunner.adaptavist.com/latest/jira/rest-endpoints.html>
ScriptRunner 공식 문서를 보면 아래와 같은 용도로 사용할 수 있다고 합니다.

- use in dashboard gadgets
  - 대시보드 가젯으로 사용
- receive notifications from external systems
  - 외부 시스템으로부터 알림 받기
- plug gaps in the official REST API
  - 공식 REST API 갭을 보완(매꾸기)
- allow all your XHRs to proxy through to other systems
  - 모든 XHR이 다른 시스템으로 프록시되도록 허용

![](/images/s3-1.png)
<center>Create Rest Endpoint 버튼을 통해 만들 수 있습니다.</center>

![](/images/s3-2.png)
![](/images/s3-3.png)

위 화면처럼 inline script 입력 창에 코드를 입력하여 REST API를 구현합니다.
공식 문서와 Show examples에서는 `Simple 'get'` 코드를 보여줍니다.

```groovy
import com.onresolve.scriptrunner.runner.rest.common.CustomEndpointDelegate
import groovy.json.JsonBuilder
import groovy.transform.BaseScript

import javax.ws.rs.core.MultivaluedMap
import javax.ws.rs.core.Response

@BaseScript CustomEndpointDelegate delegate // 1

doSomething( // 2
  httpMethod: "GET", groups: ["jira-administrators"]) { // 3
    MultivaluedMap queryParams, String body -> // 4
    return Response.ok(new JsonBuilder([abc: 42]).toString()).build(); // 5
}
```

코드의 설명 내용은 [공식 문서](https://scriptrunner.adaptavist.com/5.5.3/jira/rest-endpoints.html#_adding_a_rest_endpoint)에 나와있으나 짧게 설명해보겠습니다. (영어로 되어있어 한국어로 설명할 겸..!)

1. 이 줄이 코드는 스크립트가 엔드포인트로 사용할 수 있도록 하는 코드입니다. 엔드포인트를 사용하고자 한다면 꼭 필요한 코드입니다.
2. REST 엔드포인트의 이름입니다. URL에서 사용할 이름으로 이 코드에서는 `doSomething`으로 사용될 것입니다.
3. 엔드포인트의 설정으로 `HTTP GET`, 권한 그룹은 `jira-administrators` 그룹이 사용할 수 있는 엔드포인트가 됩니다.
4. 메서드 바디에 제공될 파라미터 입니다.
5. 작성된 값은 메서드 바디에 포함되어 `javax.ws.rs.core.Response` 객체를 반환할 것 입니다.

이렇게 추가하게되면 아래의 링크에 접근하여 데이터를 받을 수 있습니다.
`<jira_base_url>/rest/scriptrunner/latest/custom/doSomething`
curl로 테스트해보면 아래와 같이 결과 값이 나올 수 있겠습니다.
(`admin:admin`는 username:password 값을 입력하면 됩니다.)

```sh
> curl -u admin:admin http://localhost:8080/jira/rest/scriptrunner/latest/custom/doSomething
> {"abc":42}
```

### 예시

예시: [ScriptRunner REST Endpoints Examples](https://scriptrunner.adaptavist.com/5.5.3/jira/rest-endpoints.html#_examples)

- Create Priority Object
- Get the user making the request

문서에 코드도 같이 포함되어 있으니 링크 참고하셔서 설정하면 되겠습니다.
특정 URL로 요청해서 시스템 설정을 하거나 데이터를 가져오거나 할 수 있는 기능으로
REST Endpoints 소래를 마무리할 수 있겠습니다.

## Script Fragments

<https://scriptrunner.adaptavist.com/latest/jira/CustomisingUI.html>
설정화면에 있는 설명을 그대로 가져와보겠습니다.

> Use script fragments to customise the user interface and add new functionality to a Jira instance. Use customisable built-in script fragments to display web items, web panels and web sections or to include JavaScript and CSS resources using web resources. All script fragments can be customised, or use the raw XML module to create a fully custom web fragment.

간단히 설명하자면 필요한 Web items, panels, section을 만들 수 있다는 것입니다.
XML 설정이나 다른 리소스가 필요할 수는 있으나 팝업, 패널 등을 사용자가 원하는대로 만들 수 있는 기능입니다.

![](https://user-images.githubusercontent.com/5077086/56850463-12742080-693e-11e9-84f0-296f0a1b0b78.png)
![](https://user-images.githubusercontent.com/5077086/56850466-19029800-693e-11e9-91f5-6e4fadccdf66.png)

설정을 할 수 있는 메뉴를 하나하나 알아보겠습니다.

### Raw xml module

[XmlModuleItem Docs](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/XmlModuleItem.html)
xml 코드를 입력하여 원하는 위치에 메뉴를 보여주거나, 버튼들을 보여줄 수 있습니다.
아래 코드로 JIRA 상단 메뉴의 Projects > View all projects > `My Projects`를 볼 수 있습니다.

```xml
<web-item key='link-to-myprojects' name='ScriptRunner generated web item - link-to-myprojects' section='browse_link/project_view_all' weight='50'>
  <label>My Projects</label>
  <link linkId='link-to-myprojects'></link>
  <tooltip>Show only my projects</tooltip>
  <icon height="16" width="16">
    <link>/images/icons/print.gif</link>
  </icon>
</web-item>
```

![](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/common/fragments/image/xml.png)

### install web resource

[WebResource Docs](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/WebResource.html)

### Create a custom web section

- [WebSection Docs](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/WebSection.html)

### Constrained create issue dialog

- [CreateConstrainedIssue Docs](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/CreateConstrainedIssue.html)

### Custom web item

- [WebItem Docs](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/WebItem.html)

- Custom web item provider
- Show a web panel
- Hide system or plugin UI element
- Planning board context menu item
