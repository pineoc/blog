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

XML 입력창에 입력만 하면 되긴 하지만 JIRA UI 아이템들이 어떻게 배치되어있는지
알고 작성해야하는 것이 어렵긴합니다.

`section`에 `system.top.navigation.bar`이 있는지, `<web-item>` 태그가 있는지 알기 쉽지 않지만
일단 예제로 따라해보고 다른 web-item, web-section 등의 태그를 알아가야할 것 같습니다.

#### 참고 외부 링크

- Jira Server Developer (Web Item): <https://developer.atlassian.com/server/jira/platform/web-item/>
- Jira Server Developer (Web Section): <https://developer.atlassian.com/server/jira/platform/web-section/>

### Install web resource

[Web Resource Docs](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/WebResource.html)
이 기능은 Javascript, CSS 리소스를 사용할 수 있도록 하는 기능입니다.
우선 설정을 하려면 아래와 같이 환경 설정을 해야합니다. (경로는 다를 수 있습니다.)

```sh
JVM_REQUIRED_ARGS='-Dplugin.resource.directories=/app/home/scripts -Dother.properties...'
```
설정 후, 해당 폴더에 JS, CSS를 넣고 Resouces 입력창에 경로를 넣어줍니다.

![](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/image/web-resource.png)

커스텀한 리소스를 사용할 수 있다는 점에서는 좋은 것 같지만
잘못하면 많이 망가질 수 있다는 생각이 들긴하는 기능입니다.
### Create a custom web section

[Web Section Docs](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/WebSection.html)
웹 섹션(Web section)은 새로운 로케이션 또는 섹션, web-item을 추가할 때 사용할 수 있습니다.

web-item에서 web-section을 사용하고자 한다면,
web-section 만들 때 사용했던 `key` 값을 사용해야합니다.

### Constrained create issue dialog

[Create Constrained Issue](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/CreateConstrainedIssue.html)
문서 설명 그대로 가져오자면, `Create Constrained Issue` -> 제한된 문제 만들기!
제한된 설정 안에서 이슈를 만들 수 있도록 설정할 수 있습니다.

문서에서는 `Behaviours`와 함께 사용해서 구성한 메뉴를 눌렀을 경우,
특정 필드를 읽기전용으로 바꾸고 값도 설정할 수 있는 것을 보여줍니다.

### Custom web item

[Web Item](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/WebItem.html)

### Custom web item provider

[Web Item Provider Built-In Script](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/WebItemProvider.html)

### Show a web panel

[Web Panel](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/WebPanel.html)
커스텀 웹 패널을 만들고 그 영역에 정보를 담을 수 있도록 설정할 수 있습니다.

![](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/image/web-panel.png)

- Location : 설정 코멘트
- Key: UI상 ID가 필요하여 사용하는 것으로 보입니다.
- Menu text: 보이는 메뉴의 타이틀 문구로 사용됩니다.
- Weight: UI 우선순의 값으로, 양수로 설정할 수 있으며 입력하지 않아도 됩니다.
- Condition: 해당 패널이 보이는 조건을 설정할 수 있습니다.
- Provider class/script: 패널에 들어갈 데이터를 넣어주는 코드를 작성할 수 있습니다.

```groovy
writer.write("<div style='background-color: yellow; text-align: center'>" +
    "This project is going to be deprecrated. Please create" +
    " all issues in the WIDGET project</div>");
```

위 이미지 상에서 설정한대로 설정할 경우 이슈 오른쪽 패널에는 아래처럼 보여집니다.
![](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/image/web-panel-banner.png)

부모 이슈의 설명(Description) 값을 가져와서 서브태스크에 보여주는 방법도 있습니다.
[WebPanel.html#_parent_issue_example](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/WebPanel.html#_parent_issue_example)

잘 사용하면 필요한 정보를 적재적소에 보여줄 수 있을 것 같지만,
잘못 사용하면 난잡해질 수 있겠다는 생각이 드네요. 위의 예시를 살펴보고 세팅해보면 좋을 것 같습니다.
패널 뿐만 아니라 JIRA 이곳 저곳에 정보를 넣을 수 있으니 잘 사용하면 좋을 것 같습니다. :)

### Hide system or plugin UI element

[Hide UI Element Build-In Script](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/HideUIElement.html)
JIRA에서 특정 프로젝트나 특정 이슈에서 UI 요소를 숨길 수 있는 기능입니다.
예시로는 아래와 같은 것을 할 수 있습니다.

- Move, Clone 기능을 특정 프로젝트에서 이슈 Operation 목록에서 보이지 않게 함
- source control이 필요없는 프로젝트에서 Development panel을 보이지 않게 함

설정을 위해 입력해야하는 값은 많지 않습니다.

- Note: script note, 이 설정의 설명을 적는 곳입니다.
- Hide what: 어떤 요소를 숨길지 설정합니다. 설정할 수 있는 요소는 `web items` 들로 리스트는 굉장히 많습니다.
  - `com.atlassian.jira.plugin.system.issueoperations:*` - 이슈 관련 UI 요소
  - `com.pyxis.greenhopper.jira:board-*` - board 관련 UI 요소
- Condition: 어떤 조건에서 UI를 숨길 것인지 조건을 설정합니다.
  - 프로젝트, 이슈 등을 조건으로 설정할 수 있습니다.

이 설정을 사용하기전에 다른 프로젝트에 영향이 있을지 주의가 필요할 것 같습니다.
잘못하면 다른 구성원에게 필요한 기능이 보이지 않게될 수 있을테니까요.

### Planning board context menu item

[Board Context Menu Item](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/BoardContextMenuItem.html)
`Web Item` 기능 중에 하나라고 볼 수 있습니다.
스크럼, 칸반 보드에서 오른쪽 버튼을 눌렀을 때 나오는 드롭다운에 메뉴를 추가할 수 있는 기능입니다.

![](https://scriptrunner.adaptavist.com/5.5.3.1-jira8/jira/fragments/image/context-menu-items.png)
<center>`Ready for release` 메뉴를 추가한 모습</center>

가이드 문서에는 메뉴를 누르면 간단한 동작을 하는 것을 보여줍니다.

1. 스크럼 보드에서 액티브 스프린트에 있는 이슈를 `Ready for release` 메뉴를 누르면,
2. REST endpoint로 등록한 `/rest/scriptrunner/latest/custom/ghAddLabel` 로 이슈 정보를 보낸다.
3. REST endpoint 등록된 함수에서 이슈의 label 필드에 "red" 입력한다.
4. flag으로 오른쪽 위에 노티를 보여준다.

```groovy
// ...
def flag = [
  type: 'success',
  title: "Label Added",
  close: 'auto',
  body : "This issue has been approved for release"
]
Response.ok(JsonOutput.toJson(flag)).build()
```

`Condition`은 복수의 이슈를 받을 수 있기에 List 객체를 받을 수 있게 되어있습니다.
예시 코드는 아래와 같이 볼 수 있습니다.

```groovy
// All selected issues are resolved
issues.every { it.resolution }
// Selected issues in same project
issues*.projectObject.unique().size() == 1
// Only a single issue is selected
issues.size() == 1
```

`Do what`에는 사용할 수 있는 동작이 많습니다.
link로 데이터를 보내서 추가 동작을 설정하거나, 수정, 할당 등을 할 수 있습니다.

![](https://user-images.githubusercontent.com/5077086/57022026-da841a80-6c68-11e9-8ba6-00015ca85e01.png)
