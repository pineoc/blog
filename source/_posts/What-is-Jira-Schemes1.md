---
title: Jira Schemes은 무엇일까? (1)
toc: true
date: 2019-12-15 13:35:50
categories:
- PM
- System
tags:
- Jira
thumbnail: https://wac-cdn.atlassian.com/dam/jcr:fa01756d-6dcc-45d1-83ab-696fbfeb074f/Jira-icon-blue.svg?cdnVersion=696
---

Jira에서 프로젝트를 생성한 뒤에 이슈, 워크플로우, 권한 등을 설정하는데
많이 들어보셨으리라 예상하는 스킴(Scheme)에 대해 이야기해보자 합니다.

설정할 때, 기존에 사용하던 스킴을 사용할 수도 있고 내 입맛대로 변경한 스킴을 사용할 수도 있어요.
이번 포스트에서는 스킴이란 무엇인지, 어떤 스킴들이 있는지만 짚어보겠습니다.

**참고**

- 이 포스트는 Jira 언어 설정을 영어로 해두어서 한국어로 설정하신 분들의 화면과는 다를 수 있습니다)
- 스킴에 대한 설정은 프로젝트 어드민이 아닌 시스템 어드민 권한이 있어야 가능합니다.

## Jira Scheme(스킴)

Jira에는 여러 스킴이 있는데 대부분 프로젝트를 기준으로 설정 가능합니다.
스킴 하나를 여러가지 프로젝트에 적용할 수도 있고 프로젝트마다 따로 스킴을 만들어 적용할 수도 있습니다.
(스킴 하나를 공유하는 프로젝트의 경우 스킴 변경을 신중하게 해야합니다. 다른 프로젝트에 영향을 주기 때문이죠)

이슈 타입, 워크플로우, 필드, 우선순위(Priority), 권한(Permission) 등을 설정할 수 있습니다.
먼저 Jira에서 설명하는 내용을 보고난 뒤에 하나하나 살펴보겠습니다. (좋은 그래프가 있어서 첨부해봅니다.)

### Jira Docs 설명

[Project screens, schemes and fields (EN)](https://confluence.atlassian.com/adminjiraserver/project-screens-schemes-and-fields-938847220.html)
![](https://confluence.atlassian.com/adminjiraserver/files/938847220/938847221/1/1507216023026/fields_diagram.png)

**원문**
> Information for each issue is held in the fields that are associated with that issue. You can tailor these fields to suit your organization's needs. The diagram below is a representation of how these fields are associated with an issue, via screens and schemes. A screen is the user's view of an issue, and the screen is mapped to a specific issue operation (such as creating an issue, or editing an issue) via a screen scheme. The screen scheme is then mapped to an issue type via the issue type screen scheme. This configuration is associated with the project, and is applicable to all issues within the project.

**번역문**
각 이슈에 대한 정보는 해당 이슈와 관련된 필드에 있습니다. 조직의 요구에 맞게 이 필드를 조정할 수 있습니다. 아래 다이어그램은 스크린(화면) 및 스킴(구성표)을 통해 이러한 필드가 이슈와 연결되는 방식을 나타냅니다. 스크린은 사용자가 이슈를 볼 수 있는 화면이며 스크린 스킴을 통해 특정 이슈 작업 (예 : 이슈 생성 또는 이슈 편집)에 맵핑됩니다. 그런 다음 스크린 스킴은 이슈 타입 스크린 스킴을 통해 이슈 타입에 맵핑됩니다. 이 구성은 프로젝트와 관련이 있으며 프로젝트 내의 모든 이슈에 적용됩니다.

설명을 대략 구글 번역기로 돌렸는데 깔끔하게 번역된 것 같습니다. (의미로 번역하지 않고 되도록 음차로 두고 정리해두었습니다.)
위 그림 및 설명대로 스킴, 설정들이 묶여 동작하고 있는 것을 아래에서 설명드리겠습니다. 가보시죠!

### Issue types Scheme(이슈 타입 스킴)

이슈 타입 스킴은 이슈 타입에 대한 것을 정의합니다.
이 스킴은 프로젝트 -> Project settings(프로젝트 설정) -> issue types(이슈 타입)에서 볼 수 있습니다.

![프로젝트 설정 - 이슈 타입](https://user-images.githubusercontent.com/5077086/70858259-3e322e00-1f42-11ea-8613-7989884e36ed.png)

위 화면에서 볼 수 있듯이,
현재 프로젝트에서 사용하고 있는 이슈 타입들을 설정할 수 있습니다.
설정은 위에 `Actions` 버튼을 누르면 `Edit issue types`가 나옵니다.

![이슈 타입 스킴 수정](https://user-images.githubusercontent.com/5077086/70858314-3aeb7200-1f43-11ea-9de8-1beb42ec5963.png)

해당 프로젝트에서 사용할 이슈 타입을 스킴 수정을 통해 추가/삭제할 수 있습니다.
변경하고자하는 이슈 타입을 드래그&드롭으로 옮겨서 설정합니다.
프로젝트에서 기본적으로 생성되는 이슈 타입도 설정할 수 있습니다. (Default issue type)

**관련 컨플루언스 링크**

- [Adding, editing, and deleting an issue type scheme(EN)](https://confluence.atlassian.com/adminjiracloud/adding-editing-and-deleting-an-issue-type-scheme-844500754.html)
- [Issue type schemes(EN)](https://confluence.atlassian.com/adminjiracloud/issue-type-schemes-844500752.html)

### Workflow Scheme(워크플로우 스킴)

이슈 타입 스킴과 같이 프로젝트 설정 -> Workflows(워크플로우) 메뉴에서 볼 수 있습니다.
눌러보면 프로젝트에서 사용하는 각 이슈 타입에 할당되어있는 워크플로우를 볼 수 있습니다.
(현재 세팅되어있는 이슈 타입, 워크플로우 스킴 세팅에 따라 화면은 다르게 보일 수 있습니다.)

![프로젝트 설정 - 워크플로우](https://user-images.githubusercontent.com/5077086/70859554-f8cd2b00-1f58-11ea-8196-f60e32cf7bd1.png)

위 화면에서 스킴을 수정할 수는 없고 스킴을 변경하는 `Switch Scheme` 버튼으로 다른 스킴으로 `변경`할 수 있습니다.
현재 있는 스킴들 중 하나를 골라서 변경할 수 있습니다. 다만 미리 만들어두고 설정해야겠죠.

화면에서 볼 수 있듯 현재 워크플로우 스킴은 지금 프로젝트 외에 다른 2개의 프로젝트에도 적용되어있습니다.
`This workflow scheme is being used by multiple projects` 라는 문구가 있는데,
`다른 프로젝트도 사용하고 있는 스킴을 변경하려면 워크플로우 스킴 페이지로 가서 변경해야한다`는 이야기입니다.

`Workflow Schemes`를 누르면, 워크플로우 스킴을 변경할 수 있는 페이지가 나옵니다.
페이지로 가보면 이슈 타입에 워크플로우를 추가하거나 수정, 삭제할 수 있습니다.
설정되어있는 워크플로우 내용을 Text, Diagram 타입으로 볼 수 있습니다.

![워크플로우 스킴 설정](https://user-images.githubusercontent.com/5077086/70859696-ebb13b80-1f5a-11ea-8829-3c3e27d8c259.png)

첫 항목의 `All Unassigned issue Types`는 아래에 할당되어있는 이슈 타입 외에
모든 이슈 타입에 대해 PUBG Workflow가 적용된다는 것 입니다.
지금 사용하는 프로젝트는 Epic, Task, Sub-Task 이슈 타입이 PUBG Workflow(기본 워크플로우)를 사용하고 있습니다.

### Screen Scheme(스크린 스킴)

프로젝트 설정 -> Screens 메뉴에서 볼 수 있습니다.
어떤 스크린 스킴들이 설정되어있는지 볼 수 있고, 설정은 어드민 페이지에 가서 수정할 수 있습니다.

![프로젝트 설정 - 스크린 스킴](https://user-images.githubusercontent.com/5077086/70859786-2ff10b80-1f5c-11ea-94ac-07b2c451eb01.png)

여기서는 각 이슈가 Create/Edit/View(생성/수정/조회) 시 볼 수 있는 스크린을 각각 설정할 수 있습니다.
처음 스크린 스킴 생성시에는 Default로 한가지 스크린이 생성되어있으며 각각의 경우에 맞게 스크린을 생성하여 설정할 수 있습니다.
(위 화면에서 볼 수 있듯 Task, Epic, Sub-task의 각각의 경우에 맞게 스크린을 설정해두었습니다.)

각 이슈에 맞게 스크린 스킴이 설정되어있는 것을 보실 수 있을 겁니다.
상위에 이슈 타입 스크린 스킴(Issue type screen schemes)에 따라 설정되어있는 것인데 다음 순서에 설명하겠습니다.

**여기서 스크린이란?**

![스크린 설정 페이지](https://user-images.githubusercontent.com/5077086/70859936-3ed8bd80-1f5e-11ea-9f9d-edf125bfc2de.png)

- 이슈의 생성/수정/조회 시 보여지는 필드를 정의한 것을 의미합니다.
- 이슈 생성시 필요한 스크린의 경우 Summary, Description, Assignee, priority 등이 필요할 수 있겠죠?
- 이슈 화면에서 입력이 필요하거나 보여줘야하는 내용이 있다면 설정할 수 있습니다.
- 위에 `Field Tab`의 기능을 이용하면 탭을 이용하여 입력해야하는 필드를 나눠서 보여줄 수도 있습니다.

### Issue type screen schemes(이슈 타입 스크린 스킴)

`이슈 타입 스크린 스킴`은 각 이슈 타입에 따라 `스크린 스킴`을 설정할 수 있는 스킴입니다.
어떻게 보면 `스크린 스킴`과 `이슈 타입 스킴`을 연결해주는 `스킴`이라고 볼 수 있겠네요.
위 스크린 스킴 메뉴 화면에서 오른쪽 상단의 Actions -> Edit screens를 통해 수정할 수 있습니다.

![이슈 타입 스크린 스킴 설정 페이지](https://user-images.githubusercontent.com/5077086/70860068-1a7de080-1f60-11ea-8c18-c5c26df21eff.png)

설정 페이지 오른쪽 상단의 `Associate an issue type with a screen scheme` 메뉴 버튼을 통해 이슈 타입과 스크린 스킴을 연결할 수 있습니다.
기존에 있던 항목의 `Edit`버튼을 누를 경우, 다른 스크린 스킴으로 변경하는 설정화면이 나옵니다.

### Field Scheme(필드 스킴)

필드 스킴은 프로젝트에서 사용하는 이슈 타입 들의 필드 항목을 정의하는 스킴입니다.
필드 스킴에서는 각 이슈 타입에 사용할 필드를 정의한 Field configuration(필드 설정)을 설정합니다.
프로젝트 설정 화면에서 오른쪽 상단의 Actions -> Edit screens를 통해 수정할 수 있습니다.

![필드 스킴 설정 페이지](https://user-images.githubusercontent.com/5077086/70860370-44390680-1f64-11ea-96fd-e933fd9270d4.png)

설정 페이지 오른쪽 상단의 `Associate an issue type with a field scheme` 메뉴 버튼을 통해 이슈 타입과 필드 설정을 연결할 수 있습니다.
현재는 Bug 이슈 타입 외에 몇가지 커스텀한 설정이 되어있지만 Epic, Task, Sub-task 타입은 Default 필드 설정을 사용하고 있습니다.
각 항목의 Edit 버튼을 누를 경우, 다른 필드 설정으로 변경하는 설정화면이 나옵니다.

**필드 설정(Field configuration)이란?**

- 이슈에 입력할 수 있는 필드를 설정합니다.
- 입력 필드의 옵션도 설정할 수 있습니다.
  - 필수 입력(Required), 보여지지 않게 할지 등
- 필요하지 않은 필드는 숨김(Hide) 처리할 수 있습니다.

### Priority Scheme(우선순위 스킴)

프로젝트 설정에 이슈와 직접적인 관계가 있는 스킴 중 마지막 스킴이라고 할 수 있겠습니다.
이슈의 우선순위 값을 어떤 값을 입력할 수 있게할지 설정하는 스킴입니다.
주로 Blocker, Critical, Major, Minor, Trivial(Nonessential) 정도로 설정하는 것으로 알고 있습니다.

다른 스킴들과 다른 것은 우선순위 값이 시스템에 묶여 있어 순서를 변경하기 힘들다는 것입니다.
그래서 이슈 검색 시, 우선순위 정렬이 종종 안맞는 경우가 있어 확인해보면 우선순위 정렬이 안맞는 경우가 있습니다.
스킴에 묶여 있는 순서가 아닌 시스템 우선순위 값 정렬에 따라 정렬되니 참고하세요!

> 나중에 우선순위 정렬에 대한 것이 스킴에 맞게 정렬될 수 있으면 좋겠네요.
> 다만 생각해보면, 다른 우선순위 스킴을 가지고 있는 여러 프로젝트의 이슈들의 우선순위를 정렬하려면 그렇게 하기 힘들 수 있겠다는 생각도 드네요.

## 마무리

스킴에 대한 것이 아직 몇개 남았지만 프로젝트의 이슈와 연관이 큰 스킴을 중심으로 다루어 보았습니다.
남은 스킴들은 이슈 보안, 노티피케이션, 퍼미션 정도가 남았는데 다음 포스트를 통해 소개하겠습니다.
긴 글 읽어주셔서 감사합니다.
