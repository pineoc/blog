---
title: ScriptRunner 소개 2
categories:
  - PM
  - System
date: 2019-04-21 16:00:00
tags:
  - Jira
  - ScriptRunner
toc: true
thumbnail: https://user-images.githubusercontent.com/5077086/72972150-3fdaf580-3e0e-11ea-998a-108879c7874c.png
---

## ScriptRunner 소개 #2

- {% post_link scriptrunner1 %}
- **{% post_link scriptrunner2 %}**
- {% post_link scriptrunner3 %}
- {% post_link scriptrunner4 %}

지난 글에서는 Behaviours를 보았고 다음 내용인 콘솔, 리스너 등을 보겠습니다.

- Administration > Add-ons > ScriptRunner
  - Script Console
  - Built-in Scripts
  - Script Listeners
  - Script Fields
  - REST Endpoints
  - Script Fragments
  - Escalation Services
  - Script JQL Functions

### Script Console

Script Console은 실시간으로 스크립트를 작성하고 결과를 볼 수 있는 곳 입니다.

[![img](https://1.bp.blogspot.com/-jyVHGTsCUlE/XJ49sjj9HTI/AAAAAAAANXc/JZdZTXyJBC8EioVsiQtxFcKt1KBjO2QFgCLcBGAs/s640/script%2Bconsole.png)](https://1.bp.blogspot.com/-jyVHGTsCUlE/XJ49sjj9HTI/AAAAAAAANXc/JZdZTXyJBC8EioVsiQtxFcKt1KBjO2QFgCLcBGAs/s1600/script%2Bconsole.png)

실제로 스크립트를 작성해보고 실행해본 모습입니다.

[![img](https://4.bp.blogspot.com/-vNFrVfpMtjA/XJ5AFdvHzpI/AAAAAAAANXo/sVegoMWUoAYSbSNmYgKENI2QvEmKNDV8QCLcBGAs/s640/script%2Bconsole2.png)](https://4.bp.blogspot.com/-vNFrVfpMtjA/XJ5AFdvHzpI/AAAAAAAANXo/sVegoMWUoAYSbSNmYgKENI2QvEmKNDV8QCLcBGAs/s1600/script%2Bconsole2.png)

1. 스크립트를 작성하는 곳 입니다.
  - 자동 완성 기능은 없지만 없는 변수나 없는 함수 등은 오류를 보여줍니다.
2. 스크립트를 작성한 뒤에 Run 버튼으로 실행할 수 있습니다.
3. Result / Logs / Timing 값을 각각 볼 수 있습니다.
  - Result: 스크립트에서 나온 결과물을 볼 수 있습니다.
  - Logs: 스크립트에서 출력한 log들을 볼 수 있습니다.
  - Timing: Elapsed: 208 ms / CPU time: 78 ms 와 같은 내용을 볼 수 있습니다.

아래는 의도적으로 함수명을 다르게 입력하면 볼 수 있는 에러 화면 입니다.

[![img](https://3.bp.blogspot.com/-Q4CFbQXQTNE/XJ5BqfC_YMI/AAAAAAAANX0/zjIHJ0pQjCE28iro5VPIxaHBEQs6Mq44QCLcBGAs/s640/console3.png)](https://3.bp.blogspot.com/-Q4CFbQXQTNE/XJ5BqfC_YMI/AAAAAAAANX0/zjIHJ0pQjCE28iro5VPIxaHBEQs6Mq44QCLcBGAs/s1600/console3.png)

정적 타입 체크 밖에 해주지 못하지만 최소한의 체크는 할 수 있기에
스크립트 작성은 할 수 있습니다.

### Built-in Scripts

ScriptRunner 에 이미 설정(구현)되어 있는 스크립트들을 사용할 수 있는 메뉴입니다.
아래 참고 문서에서 사용할 수 있는 스크립트 리스트를 볼 수 있습니다.
참고 문서: <https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html>

[![img](https://4.bp.blogspot.com/-EMtlwxDO6XE/XKBtiYrzz3I/AAAAAAAANYM/sQU3nhhre3M_4CVfim_aaxiiowo9pF5cwCLcBGAs/s640/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%2B2019-03-31%2B%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%2B4.26.35.png)](https://4.bp.blogspot.com/-EMtlwxDO6XE/XKBtiYrzz3I/AAAAAAAANYM/sQU3nhhre3M_4CVfim_aaxiiowo9pF5cwCLcBGAs/s1600/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%2B2019-03-31%2B%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2B4.26.35.png)
<center><아래에 더 많은 스크립트가 있습니다></center>

위 화면의 스크립트 중 **"Bulk Fix Resolutions"** 스크립트를 확인해보겠습니다.
이 스크립트는 Filter에 있는 티켓들의 Resolution을 변경할 수 있습니다.
참고 링크: [Bulk Fix Resolutions](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html#_bulk_fix_resolutions)

[![img](https://2.bp.blogspot.com/-yX8IA8-n0Ok/XKBwoHW0l8I/AAAAAAAANYY/bO32KMbtTVULbmsygDrQpGy884sVWV-JgCLcBGAs/s640/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%2B2019-03-31%2B%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%2B4.28.31.png)](https://2.bp.blogspot.com/-yX8IA8-n0Ok/XKBwoHW0l8I/AAAAAAAANYY/bO32KMbtTVULbmsygDrQpGy884sVWV-JgCLcBGAs/s1600/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%2B2019-03-31%2B%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2B4.28.31.png)

JQL을 바로 작성하는 것은 아니며 기존에 만들어둔 Filter를 사용하여 동작하는 스크립트 입니다.
그 외에 다른 스크립트의 목록은 아래와 같습니다.

- [Escalation Service](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html#_escalation_service)
- [Switch User](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html_switch_user)
- [Change dashboard or filter ownership](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html#_change_dashboard_or_filter_ownership)
- [Copy Project](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html#_copy_project)
- [Copy Custom Field Values](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html#_copy_custom_field_values)
- [Bulk Import Custom Field Values](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html#_bulk_import_custom_field_values)
- [Split Custom Field Context](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html#_split_custom_field_context)
- [Script Registry](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html#_script_registry)
- [Condition Tester](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html#_condition_tester)
- [Clear JIRA or Groovy Caches](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html#_clear_jira_or_groovy_caches)
- [Bulk Copy SLAs](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html#_bulk_copy_slas)
- [List scheduled jobs](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html#_list_scheduled_jobs)
- [View server log files](https://scriptrunner.adaptavist.com/latest/jira/builtin-scripts.html#_view_server_log_files)

### Listeners

Listeners는 JIRA에서 일어나는 이벤트에 따라 스크립트를 동작하게 합니다.
프로젝트, 특정 이슈, 특정 이벤트에 따라 동작할 수 있도록 설정할 수 있습니다.
참고 문서: <https://scriptrunner.adaptavist.com/latest/jira/listeners.html>

[![img](https://2.bp.blogspot.com/-6iNvRNsQRj0/XKB0ggjPDgI/AAAAAAAANYk/qdiOnIs2CjMvSl0HXcs9MrX1MHaDV1xmwCLcBGAs/s640/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%2B2019-03-31%2B%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%2B5.02.39.png)](https://2.bp.blogspot.com/-6iNvRNsQRj0/XKB0ggjPDgI/AAAAAAAANYk/qdiOnIs2CjMvSl0HXcs9MrX1MHaDV1xmwCLcBGAs/s1600/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%2B2019-03-31%2B%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2B5.02.39.png)

<center><여러가지 리스너를 추가할 수 있습니다></center>

이미 있는 리스너 타입을 사용해도 되고
아예 이벤트를 받는 처음부터 스크립트 마무리까지 관리하는 Custom listener를 사용할 수도 있습니다.

이미 있는 리스너 타입 하나를 한번 보겠습니다.
<https://scriptrunner.adaptavist.com/5.4.39/jira/builtin-scripts.html>
`Create a sub-task: Create a sub-task, Will Optionally reopen a matching sub-task`

[![img](https://4.bp.blogspot.com/-WixKlg4utC0/XKB25DQ5OdI/AAAAAAAANYw/oKiVUh9f3qMkRVnkyvolL1S5a-v_WEcbQCLcBGAs/s640/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%2B2019-03-31%2B%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%2B5.14.14.png)](https://4.bp.blogspot.com/-WixKlg4utC0/XKB25DQ5OdI/AAAAAAAANYw/oKiVUh9f3qMkRVnkyvolL1S5a-v_WEcbQCLcBGAs/s1600/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%2B2019-03-31%2B%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2B5.14.14.png)
<center><특정 이벤트에서 Sub-task를 만들 수 있는 리스너 입니다></center>

 Create a sub-task Listener를 등록하는 화면의 각각 입력 필드에 대해 알아보겠습니다.

- **Note**: Listener 등록시 해당 설명으로 Listener 리스트에서 설명을 볼 수 있습니다.
- **Project(s)**: 해당 이벤트가 발생하는 프로젝트를 설정합니다.
  - 프로젝트는 자동 완성되어 입력할 수 있습니다.
- **Events**: 어떤 이벤트를 받아서 처리할 것인지 이벤트를 설정합니다.
  - All Issue Events, Issue Created, Issue Updated 등의 이벤트를 추가할 수 있습니다.
- **Condition**: 해당 이벤트가 발생했을 경우, True / False를 판단할 스크립트를 설정합니다.
  - `Show examples`를 누르면 예시 코드를 볼 수 있습니다.
  - `Priority changed to Major (Listeners only)` - Listeners 에서만 동작하는 코드로 **priority가 Major로 변경되었을 경우 True를 반환**하는 스크립트 입니다.
  - 그 외에 많은 예제 스크립트가 있으니 참고하여 작성하면 됩니다.
- **Target Issue Type**: Sub-task 카테고리의 이슈 타입을 설정합니다.
- **Subtask Summary**: 생성할 Sub-task 제목(Summary)를 설정합니다.
- **Fields to copy**: All / None / Custom 으로 상위 태스크의 필드 값을 복사할 것인지 설정합니다.
- **As User**: 어떤 유저로 티켓 생성을 할 것인지 설정합니다.
  - 값이 없을 경우 현재 유저로 설정합니다.
- **Additional issue action**: Sub-task 생성 이후 타겟 이슈(부모 이슈)에 대해 추가적인 작업을 하도록 설정합니다.
  - Condition과는 달리 추가적인 작업을 할 수 있도록 하는 스크립트 입력 필드입니다.
  - 제목을 바꾸거나 팝업 메세지를 따로 띄우거나 할 수 있습니다.
  - `Show examples`를 누르면 예시 코드를 볼 수 있습니다.
- **Subtask Action**: 이미 생성된 Subtask가 있을 경우 transition을 진행할 것인지 설정합니다.
  - 주의할 점은 적용하고자하는 프로젝트의 서브 태스크가 어떤 워크플로우를 쓰는가를 확인하여 적용해야 합니다.

Create a sub-task 외에 다른 listener 타입이 있으며 아예 커스텀한 listener도 만들 수 있습니다.
Custom listener의 경우 다음과 같이 만들 수 있습니다.

[![img](https://4.bp.blogspot.com/-dAM7Fai7N3g/XKCwT0APuhI/AAAAAAAANZA/fGBS_fDR9XgwXx60hy4TiPeeYq-uUfj1wCLcBGAs/s640/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%2B2019-03-31%2B%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%2B9.18.54.png)](https://4.bp.blogspot.com/-dAM7Fai7N3g/XKCwT0APuhI/AAAAAAAANZA/fGBS_fDR9XgwXx60hy4TiPeeYq-uUfj1wCLcBGAs/s1600/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%2B2019-03-31%2B%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2B9.18.54.png)

이 listener는 앞서 설명드린 create a sub-task 와 프로젝트, 이벤트 필드 설정하는 것은 같지만
이벤트를 받고 처리하는 방식이 다릅니다.

발생한 이벤트에서 각종 데이터를 받아 처리해야하는 listener 타입 입니다.
listener에 필요한 listener 타입이 없다면 커스텀하게 만들어서 사용하면 됩니다.

// Listener 중 Remote Custom listener는 JIRA에 등록되어있는 application에도 scriptRunner를 설치해야 사용할 수 있습니다.

### Script Fields

Script fields는 아래와 같이 설명이 나와있습니다.

> A script field is a custom field that allows you to automatically display a value according to the results of a ScriptRunner script.

요약하자면, "**스크립트러너의 스크립트 결과를 보여주는** **Custom field**" 입니다.
참고 문서: <https://scriptrunner.adaptavist.com/latest/jira/scripted-fields.html>

  [![img](https://1.bp.blogspot.com/-_Qd-7-EplLA/XKC2n-cYvLI/AAAAAAAANZM/-XGMfWnQO3wReeQcTW4tCRk0jGAYNB2IQCLcBGAs/s640/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%2B2019-03-31%2B%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%2B9.45.39.png)](https://1.bp.blogspot.com/-_Qd-7-EplLA/XKC2n-cYvLI/AAAAAAAANZM/-XGMfWnQO3wReeQcTW4tCRk0jGAYNB2IQCLcBGAs/s1600/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%2B2019-03-31%2B%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2B9.45.39.png)

다음 글에서는 남은 기능을 소개해보겠습니다.

- REST Endpoints
- Script Fragments
- Escalation Services
- Script JQL Functions
