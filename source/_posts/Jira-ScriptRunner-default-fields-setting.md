---
title: ScriptRunner를 이용하여 Jira 이슈 생성시 설명(Description) 기본 값 설정하기
toc: true
date: 2020-06-18 16:48:00
categories:
  - PM
  - System
tags:
  - Jira
  - ScriptRunner
thumbnail: https://user-images.githubusercontent.com/5077086/72972150-3fdaf580-3e0e-11ea-998a-108879c7874c.png
---

## Needs: Jira 이슈 생성시 설명(Description) 항목 기본 값 설정하기

Jira를 사용하다 보면 이슈를 생성할 때 설명 항목에 자주 쓰는 내용들이 있습니다.
예를 들면, 현재 사용하는 프로젝트의 버그 이슈에서 버그에 대한 상세한 설명, 참고 사항 등이 있죠.
현재 사용하고 있는 프로젝트에서는 아래와 같은 내용을 버그 티켓 생성시 작성하고 있습니다.

### 예시: 버그 이슈 설명(Description) 내용

```
(QA 환경)
환경 설명
(상세 설명)
상세 설명
(참고)
참고 설명
(영상)
영상 링크
(기대 결과)
기대 결과 설명
```

이러한 내용을 항상 이슈 생성시 마다 작성하는 것도 번거롭고, 각 작성자가 입력하는 내용도 일정하지 않을 때가 있었습니다.
이런 상황들을 개선해보고자 기본 값, 템플릿을 설정할 수 있는지 확인해보았고 다른 Jira 앱(플러그인)들이 있지만 현재 설치되어있는 ScriptRunner로 개선해보았습니다.

## ScriptRunner로 설명 항목 기본 값 설정 Flow

ScriptRunner에는 많은 기능들이 있지만 그 중에서 Behaviours 기능을 사용하여 특정 항목의 기본 값 설정을 해보겠습니다.
순서는 다음과 같이 진행합니다. (ScriptRunner [가이드 문서 - Setting Field Defaults](https://scriptrunner.adaptavist.com/6.3.0/jira/recipes/behaviours/setting-default-fields.html)에도 있는 내용이니 참고해주세요!)

![ScriptRunner Behaviours](https://scriptrunner.adaptavist.com/6.3.0/image/jira/bhv/navigating-to-behaviours.png)

1. Jira > Manage apps > Behaviours 이동
2. Add Behaviours 추가
3. Add Mapping - 프로젝트 및 이슈 타입 설정
4. Fields 설정 > Initialiser 스크립트 설정

### Add Behaviours 추가

첫 번째 설정으로 이동하는 단계는 스킵하고 Behaviours를 추가하는 것 부터 진행하겠습니다.
위에 있던 이미지 항목대로 behaviour 이름을 입력해주고 Add 버튼을 누르면 끝입니다.

### Add Mapping - 프로젝트 및 이슈 타입 설정

![](https://user-images.githubusercontent.com/5077086/84995592-281e5800-b187-11ea-95a8-a63988b9e2c1.png)

- **Choose projects**: 프로젝트는 기본 값 설정이 필요한 프로젝트를 선택하여 지정해주시면 됩니다.
- **Choose Issue types**: 모든 이슈 타입 또는 특정 이슈 타입에 대해서 지정할 수 있습니다.

이 설정으로 behaviour가 동작할 프로젝트, 이슈 타입이 맵핑되었습니다.

### Fields 설정 > Initialiser 스크립트 설정

![](https://user-images.githubusercontent.com/5077086/84996722-9a436c80-b188-11ea-9812-f7dff1913d85.png)

Add Behaviours 화면에서 만든 behaviour 항목에 있는 Fields를 눌러 설정을 진행합니다.
처음에는 Initialiser Function이 없다고 나오는데 Create initialiser를 눌러 생성해주세요.
생성하고 나면 위와 같은 스크립트를 입력할 수 있는 항목을 볼 수 있습니다. 스크립트를 입력해볼까요?

![](https://user-images.githubusercontent.com/5077086/84999525-3e7ae280-b18c-11ea-9faa-5702ea8d7f9f.png)

#### 스크립트

```groovy
import com.atlassian.jira.component.ComponentAccessor
import static com.atlassian.jira.issue.IssueFieldConstants.DESCRIPTION;

if (getActionName() != "Create Issue") {
    return // not the initial action, so don't set default values
}

def desc = getFieldById(DESCRIPTION);
if (!desc.getValue()) {
    desc.setFormValue("test form");
}
```

스크립트는 심플해서 설명할 내용은 많지 않네요.
- Create Issue 타입의 액션이 아니면 스크립트 실행 중지
- getFieldById()를 가져오고 setFormValue() 함수를 통해 이슈 생성시 form에 기본 값을 입력

스크립트러너 가이드 문서에 있는 내용이 더 복잡한 내용을 담고 있어 다른 항목의 기본 값 설정시 참고하시면 좋을 것 같습니다.
기본 값 설정시 setFormValue() 함수에 string 값으로 설정해주시면 됩니다.
이미지와 스크립트가 다른 것은 설명 값이 있는지 유무를 확인하는 정도이니 설정시 참고부탁드립니다. 😀

## 설명 항목 기본 값 설정시 참고

설명 항목 기본 값 설정하면서 몇가지 참고할 만한 사항이 있습니다.

- 기본적으로 설명 항목은 HTML 값을 인식하기에 줄바꿈이 필요할 경우 `<br/>`을 입력해서 설정해주시면 됩니다.
- h1, h2와 같은 항목도 마찬가지로 `<h2>`, `<h3>`로 입력해서 설정해주시면 됩니다.
- 만약 현재 Jira 시스템에 JEditor가 설치되어 사용중일 경우 JEditor 기능을 사용하여 기본 값을 설정해주셔야 합니다.
  - 이건 ScriptRunner 기능보다는 JEditor 내용이니 다른 포스트에서 다뤄보겠습니다.

## 마무리

ScriptRunner 기능 중에 Behaviours 기능을 이용하여 기본 값 설정을 해보았습니다.
사실 다른 Jira 앱을 통해서 쉽게 설정할 수 있는데 ScriptRunner는 코드를 입력해야하는 점이 어려울 수 있겠다는 생각이 드네요.
(그만큼 커스텀할 수 있는 것이 많아서 좋긴 하지만요. ㅎㅎ)

다른 항목에 대한 기본 값 설정은 가이드 문서를 참고해주시구요. 다른 유용한 기능이 있다면 포스팅해보겠습니다.
긴글 읽어주셔서 감사합니다. 👍

## 참고 문서 / 링크

- <https://scriptrunner.adaptavist.com/6.3.0/jira/recipes/behaviours/setting-default-fields.html>
- <https://community.atlassian.com/t5/Marketplace-Apps-Integrations/Scriptrunner-behavior-default-text-and-validation-error-resets/qaq-p/581980>