---
title: Atlassian playbook - DACI 프레임워크
toc: true
date: 2020-10-25 15:43:13
categories:
- PM
- Framework
tags:
- Framework
- Playbook
thumbnail: https://wac-cdn.atlassian.com/dam/jcr:e7903b3d-0efb-41b5-8ae7-d668b6c6281d/DACI.png?cdnVersion=1316
---

## Atlassain playbook 번역해보기 #1

올해 초 부터 해보고 싶었던 Playbook 번역이었는데 조금씩 하다가 이제 정말 해보자하고 진행하고 있네요.
이번 글에서는 Atlassian Playbook에 있는 [DACI](https://www.atlassian.com/team-playbook/plays/daci) 프레임워크를 소개해보고자 합니다.
되도록 글의 번역에 초점을 맞춰보고 추가할 내용은 조금씩 수정, 보완해볼 예정입니다.

원글: <https://www.atlassian.com/team-playbook/plays/daci>

## DACI (Driver, Approver, Contributors, Informed) framework

**DACI 프레임워크**는 그룹 결정을 효율적이고 효과적으로 내릴 수 있도록 도와줍니다.

### 이 플레이북 활동을 사용하면?

이 DACI 프레임워크 활동을 사용하여, 영향력이 높거나 위험이 높은 그룹 결정을 내리기 위한 역할을 정의합니다.

### DACI가 왜 필요한가요? (상황 예시)

<!-- If you've ever found yourself standing at the counter of your favorite sandwich shop tormented by the question of whether to get the Reuben or the turkey, you know this universal truth: decisions are hard. -->
당신이 좋아하는 샌드위치 가게의 카운터에 서서 루벤(Reuben)을 먹을 것 인지 칠면조를 먹을 것 인지에 대한 질문으로 고통받는 자신을 발견했다면, 이 보편적인 진실을 알고있을 것입니다. 결정은 어렵습니다.

<!-- Decisions at work are even harder because the stakes feel higher. Then you add the opinions of teammates, stakeholders, customers, and your boss to the equation... yikes. -->
직장에서의 결정은 훨씬 더 어렵습니다. 그런 다음 팀원, 이해 관계자, 고객 및 상사의 의견을 방정식에 추가합니다... 으으 😰

<!-- If we don't approach decisions about our projects with urgency, they stall out because nobody is making the call on things.
And if we don't agree on whose call it is, we end up revisiting decisions over and over, which further delay our progress. -->
프로젝트에 대한 의사결정에 긴급하게 접근하지 않으면 아무도 결정을 내리지 못하기 때문에 지연됩니다.
그리고 우리가 누구의 결정이냐에 동의하지 않으면, 우리는 결국 결정을 반복해서 재검토하게 되고, 이것은 우리의 발전을 더욱 지연시킵니다.

<!-- By clarifying who-plays-what-role in each decision up front, we have a better shot at making the right decisions, and making them at the right time – like choosing the Reuben, which is the right call every time. -->
각 의사 결정에서 누가 어떤 역할을 하는지 명확히 함으로써, 올바른 결정을 내리고 적절한 시기에 결정을 내릴 수 있는 더 나은 기회를 얻을 수 있습니다.
(항상 루벤을 선택하는 것이 옳은 것 처럼요.)

> 이건 작성자 개인의 취향인듯 합니다. 😂
> 루벤 샌드위치를 비유할만한 한국 음식은 떠오르지 않는군요. 😄

### 누가 참여해야하나요?

결정 및 진행을 위해 그룹 전체 인원이 참여합니다.

## 플레이북 활동 진행

DACI는 그룹 의사결정에 구조를 가져오는 것에 관한 것입니다.
그러니 먼저 이 활동을 자세히 복습하여 그 구조를 확실히 이해하시길 바랍니다.

|인원 수|준비 시간|시간|난이도|
|:-:|:-:|:-:|:-:|
|4-8|15분|다양|중간(Moderate)|

### 준비물

- 컴퓨터(노트북)
- Confluence 용 DACI 프레임워크 템플릿
- [DACI 프레임워크 템플릿 PDF (EN)](https://www.atlassian.com/ko/dam/jcr:f6b56375-3d78-496a-857e-ca47e89816ce/DACI-Decision-template.pdf)

### 활동 시작 전에 먼저

#### "DACI"는 무엇을 의미하나요?

|용어|설명|
|:-:|:-:|
|`D`river<br>(운전자)|이해 관계자를 모으고 필요한 모든 정보를 수집하고 합의된 날짜까지 결정을 내릴 책임이 있는 한 사람입니다. 결정에 따라 프로젝트의 풀타임 작업자일 수도 있고 아닐 수도 있습니다.|
|`A`pprover<br>(승인자)|결정을 내리는 한 사람입니다.|
|`C`ontributors<br>(기여자)|그들은 결정에 영향을 줄 수 있는 지식이나 전문 지식을 가지고 있습니다. 즉, 목소리는 있지만 투표권은 없습니다.|
|`I`nformed<br>(정보 수신자)|최종 결정에 대한 정보를 받습니다.|

<!-- The DACI only works if everyone in the group rallies behind decisions once they're made – even if they don't agree. 
Without a willingness to share concerns and trust they'll be considered, your team will find itself mired in a bog of circular debates and inaction.
Team members may even pursue their preferred option on the sly, in the hopes the official decision is a failure.
Make sure everyone is prepared to fully committed to whatever is decided so you can skip the bullshit politics.  -->
DACI는 비록 그들이 동의하지 않더라도, 그룹의 모든 사람들이 일단 결정이 내려지면 결정 뒤에 집회를 열 때만 작동합니다.
우려와 신뢰를 기꺼이 공유하지 않으면, 여러분의 팀은 끝없는 토론과 무반응의 늪에 빠질 것입니다.
팀원들은 심지어 공식적인 결정이 실패하기를 바라면서 몰래 선호하는 선택지를 추구할 수도 있습니다.
여러분이 헛소리 정치는 건너뛸 수 있도록 모든 사람들이 결정된 모든 일에 완전히 전념할 준비가 되어 있는지 확인하세요.

#### DACI가 필요한가요?

<!-- It's a question we often find ourselves asking. -->
그것은 우리가 자주 하는 질문입니다.

<!-- As you consider whether a  group decision needs the full-on DACI treatment, take the timeliness and impact into account. Decisions that affect the work of multiple people on the project (e.g. "Where should we hold our user conference next year?") probably need a DACI. Smaller, isolated decisions (e.g., "What will the conference's social media hashtag be?") do not. -->
그룹 의사결정에 전체 DACI 치료가 필요한지 여부를 고려할 때 `적절한 시기`와 `영향`을 고려해야 합니다.
프로젝트에서 여러 사람의 작업에 영향을 미치는 의사 결정(예: "내년에는 어디에서 사용자 회의를 개최해야 합니까?")에는 DACI가 필요할 수 있습니다.
소규모의 고립된 결정(예: "회의의 소셜 미디어 해시태그는 어떻게 될 것인가?")은 그렇지 않습니다.

### Step 1, 결정을 추적할 페이지를 만듭니다. (5분)

<!-- Most projects benefit from documenting what's being considered, relevant research, trade-offs, recommendations, etc. This makes it easier for the core team to provide feedback on options and helps stakeholders understand the final decision. -->
대부분의 프로젝트는 검토 중인 사항, 관련 연구, 트레이드오프, 권장 사항 등을 문서화함으로써 이득을 얻습니다.
이를 통해 핵심 팀은 보다 쉽게 옵션에 대한 피드백을 제공하고 이해 관계자가 최종 결정을 이해할 수 있도록 지원합니다.

<!-- Open up a new page in Confluence (or your documentation tool-of-choice) and insert a 2x4 grid at the top
– or create the page using the DACI Blueprint for Confluence.
Label the rows in the left column as Driver, Approver, Contributors, Informed.
You'll add more to this page in the coming days/weeks as you work through the decision. -->
컨플루언스(또는 문서화 도구 선택)에서 새 페이지를 열고 맨 위에 2x4 그리드를 삽입하거나 [DACI Blueprint for Confluence](http://marketplace.atlassian.com/plugins/atlassian-playbook-daci-decision/cloud/overview)를 사용하여 페이지를 만듭니다.
왼쪽 열의 행에 드라이버, 승인자, 기여자, 알림으로 레이블을 지정합니다. 결정을 진행하는 동안 며칠/주 내에 이 페이지에 더 많은 정보를 추가할 수 있습니다.

컨플루언스 사용자가 아닌가요? 걱정하지 마세요.
대신 [DACI 템플릿 PDF](https://www.atlassian.com/ko/dam/jcr:f6b56375-3d78-496a-857e-ca47e89816ce/DACI-Decision-template.pdf)을 다운로드하여 사용할 수 있습니다.

### Step 2, 그룹 결정을 위한 역할을 정의합니다. (10분)

**운전자(Driver)는 누구입니까?**
<!-- Agree on one person per decision. They don't necessarily drive the entire project – just that decision. -->
각 결정마다 한 사람씩 있는 것이 좋습니다. 이 사람들은 반드시 전체 프로젝트를 주도하지는 않습니다. 그 결정에만 있으면 됩니다.

**승인자(Approver)는 누구입니까?**
<!-- Again, one person per decision. -->
다시 한 번 말하지만, 한 결정당 한 명만 있어야합니다.

**기여자(Contributors)는 누구입니까?**
<!-- This may be multiple people per decision, and may even include someone from outside the core team. Anyone with relevant knowledge or experience is fair game. -->
이 사람들은 결정당 여러 사람이 될 수 있으며, 심지어 핵심 팀 외부의 사람을 포함할 수도 있습니다. 관련 지식이나 경험이 있는 사람은 누구나 공정한 게임입니다.

**정보 수신자(Informed)는 누구입니까?**
<!-- This is anyone directly affected by the decision. Note that this may include people outside the core team. -->
이 사람들은 그 결정의 직접적인 영향을 받는 모든 사람들입니다. 여기에는 핵심 팀 외부의 사람들이 포함될 수 있습니다.
<!-- Ask questions like "If the driver is away, who would they delegate to?" and "Do we have too many people who need to be consulted?". Adjust your DACI accordingly. -->
"운전자가 부재중이라면 누구에게 위임하겠습니까?", "상담을 받아야 할 사람이 너무 많습니까?"와 같은 질문을 던집니다. 이에 따라 DACI를 조정합니다.

### Step 3, 공격 계획을 세우세요. (15 min)

<!-- Think about all the information you'll need to gather in order to make the decision. If you're not using the DACI blueprint for Confluence, mark off the following sections on your page. You don't need to fill them out right now, but feel free to add notes in each one. -->
결정을 내리기 위해 수집해야 할 모든 정보를 생각해 보세요.
Confluence에 DACI Blueprint를 사용하지 않는 경우 페이지에서 다음 섹션을 표시합니다.
지금 바로 작성하실 필요는 없지만, 각 메모에 내용을 추가하셔도 됩니다.
<!-- 
- Due date: the deadline for making the decision.
- Background: the reason(s) this decision is required.
- Current state: where you're at right now.
- Supporting data: the research you've done to inform your decision.
- Options considered: a table with a column for each option where you can summarise pros n' cons, risks, trade-offs, estimated cost or effort, etc.
- Recommendations: opinions from your contributors.
- FAQs: a place to answer frequently-asked (or anticipated) questions.
- References: a list of links out to reference material, along with a brief description of why it's relevant.
- Action items: a list of tasks or follow-ups related to the decision.
- Outcome: a place to state which option you ultimately go with. -->

|항목|설명|
|:-:|:-:|
|마감일|결정 기한|
|결정 배경|결정이 필요한 이유|
|현재 상태|지금 결정 단계상 있는 곳|
|정보 지원|당신의 결정을 알리기 위해 당신이 조사한 것|
|고려된 옵션들|장단점, 리스크, 트레이드오프, 예상 비용 또는 노력 등을 요약할 수 있는 각 옵션에 대한 열이 있는 표|
|추천 사항/제안|기여자들의 의견|
|FAQs|자주 묻는 질문(또는 예상 질문)에 답변할 수 있는 곳|
|참조|참조 자료로 연결되는 링크 목록과 관련 이유를 간략히 설명|
|조치 목록|결정과 관련된 작업 또는 후속 조치 목록|
|결정 결과|최종적으로 어떤 옵션을 선택하는지 설명하는 곳|

### Step 4, 팀을 참여시키기

<!-- Send the page around to your team, asking for feedback and input. If you'll need specific people to help fill in specific sections of the page, now is the time to let them know. -->
피드백과 입력을 요청하는 페이지를 팀으로 보냅니다.
페이지의 특정 섹션을 작성하는 데 도움이 되는 특정 사용자가 필요한 경우, 지금이 바로 알려야 할 때입니다.

<!-- If at some point you feel like things have stalled out or you're going in circles, get the driver and contributors in a room together. If you're close to making the call, it might be helpful to include the approver, too. Let people express their concerns, recommendations, ideas for other options to consider, etc. An hour of hashing it out in person can save you days of comment (or – horrors! – email) threads, and get your decision back on track. -->
만약 어떤 시점에서 상황이 정체되거나 빙빙 돌고 있다고 느낀다면, 운전자와 기여자들을 방에 함께 모으세요. 결정에 가까워질 경우, 승인자를 포함시키는 것도 도움이 될 수 있습니다. 사람들이 자신의 우려 사항, 추천 사항, 고려해야 할 다른 옵션에 대한 아이디어 등을 표현할 수 있도록 합니다. 한 시간 동안 직접 해싱하면(합의에 도달하기 위해 다른 사람들과 이야기를 나누면) 며칠간의 의견(또는 - 공포! - 이메일) 스레드를 절약할 수 있으며, 결정을 다시 정상으로 되돌릴 수 있습니다.

<!-- ...then take a deep breath! The DACI play can be a stressful, especially if decisions are contentious or politically-charged. You just did your team a great service by taking time to lay down a clear group decision-making framework to work with. -->
...그럼 심호흡을 하세요! DACI 활동은 특히 결정이 논쟁적이거나 정치적 책임을 지는 경우 스트레스가 될 수 있습니다. 여러분은 함께 일할 수 있는 명확한 그룹 의사 결정 프레임워크를 구축하는 것에 시간을 할애하여 팀원들에게 훌륭한 서비스를 제공했습니다.

## 다른 사례 - 서비스 팀

<!-- In the context of providing services like desktop support or recruiting, a matrix of DACIs helps front-line service team members understand which calls they can make independently and when they should involve teammates or a manager. Note that the full decision page described above isn't needed for each decision in your matrix. A brief description, plus the D, A, Cs, and Is for each scenario is usually enough. -->
데스크톱 지원 또는 채용과 같은 서비스를 제공하는 맥락에서, 일련의 DACI는 일선 서비스 팀 구성원들이 독립적으로 어떤 통화를 할 수 있는지, 팀원이나 관리자가 언제 참여해야 하는지 이해할 수 있도록 도와줍니다. 위에서 설명한 전체 결정 페이지가 매트릭스의 각 결정에 필요하지 않습니다. 각 시나리오에 대한 간단한 설명과 D, A, C 및 I로 충분합니다.

<!-- Create a DACI matrix on a per-service basis (vs. a per-project basis). Think of your deliverable as a set of escalation paths and procedures for communicating information after those independent decisions are made. -->
서비스 별로(프로젝트 별로) DACI 매트릭스를 만듭니다. 이러한 독립적 의사 결정이 이루어진 후 정보를 전달하기 위한 일련의 에스컬레이션 경로 및 절차로 제공될 수 있다고 생각하시면 됩니다.

<!-- A service team's DACI matrix is relatively static, but it's not carved in stone. Review and revise your DACI annually for services that are established and stable. For new service teams, we like to review the DACI quarterly or twice-yearly during the first year. -->
서비스 팀의 DACI 매트릭스는 비교적 정적인 편이지만, 돌에 새겨진 것은 아닙니다. 확립되어있고 안정적인 서비스에 대해 DACI를 매년 검토하고 수정하세요. 신규 서비스 팀의 경우 DACI를 분기별 또는 1년 동안 2회 검토하기를 권장합니다.

## 다음 조치(Follow-ups) - 의사결정 기록

<!-- Optional. Larger initiatives that affect multiple groups or departments (lookin' at you, leadership teams!) often benefit from a decision register page. It serves as a portal that makes it easy for team members and stakeholders to access detailed information about each decision. -->
선택 사항입니다. 여러 그룹 또는 부서에 영향을 미치는 대규모 이니셔티브(리더십 팀, 리더십 팀)는 종종 의사결정 기록 페이지에서 이점을 얻습니다. 의사결정 기록 페이지는 팀 구성원과 이해관계자가 각 결정에 대한 세부 정보에 쉽게 액세스할 수 있는 포털 역할을 합니다.

<!-- On your decision register, include a brief summary of the project (such as your elevator pitch). Below that, link off to the page detailing each decision. Also note each decision's status, level of impact, driver, approver, and due date. You might also include a legend defining important terms – e.g., what exactly does it mean when a decision is labeled "high impact". -->
의사결정 기록에 프로젝트에 대한 간략한 요약(예: [엘리베이터 피치(EN)](https://www.atlassian.com/team-playbook/plays/elevator-pitch))을 포함합니다. 그 아래, 각 결정을 자세히 설명하는 페이지로 연결합니다. 또한 각 결정의 상태, 영향 수준, 운전자, 승인자 및 만료 날짜를 기록합니다. 또한 중요한 용어를 정의하는 범례도 포함할 수 있습니다. 예를 들어, 의사결정에 "높은 영향"이라는 레이블이 지정된 경우 정확히 무엇을 의미하는지 알 수 있습니다.

## 연관된 활동

- [프로젝트 킥오프(Kick-off)](https://www.atlassian.com/team-playbook/health-monitor/project-teams)
- [역할과 책임](https://www.atlassian.com/software/confluence/marketing/guide/stakeholder-management)
- [트레이드 오프 슬라이더](https://www.atlassian.com/team-playbook/plays/trade-off-sliders)

## Playbook - DACI 활동 문서 번역을 마치며

맨 처음에 DACI라는 내용을 들었을 때, 무슨 프로세스지? 방법론인가? 하고 막연히 생각했습니다.
(프레임워크라고 해서 SWOT(강점, 약점, 기회, 위협) 같은 것으로 생각했었죠.)
다른 PM 분들이 소개해주시는 내용이나 요즘 PM과 관련한 글들을 많이 보면서 어렴풋이 알게되었고 Atlassian에 관련 자료가 있어서 마침 공부하는 겸 번역하게되었습니다.

> 제가 일하고 있는 곳에서 일어나는 일을 DACI에 대입해보면.. 프로젝트(작은 피쳐 또는 스펙)를 진행할 때에 PM이 보통 운전자(드라이버)로 진행을 하고
> PD, 리더분들이 승인자 역할 그리고 사업 부서와 운영 부서는 기여자와 정보 수신자가 될 수 있겠네요.

사실 번역하면서 어느정도 이해는 했고 실제 업무에 알맞게 써먹을 수 있을지가 관건이겠죠.
나중에 이런 프레임워크가 있으니 한번 써볼까하는 생각은 들 수 있겠습니다. (언젠가 🙈)
이 글을 읽으신 분들에게 조금이나마 도움이 되었기를 바라며 마칩니다. 고맙습니다.

## 참고하면 좋을만한 글

- [브런치: DACI 팀 결정을 효율적으로 하는 방법](https://brunch.co.kr/@seungjoonlernnx/64)
  - [ProductPlan: DACI Decision-Making Framework(원문)](https://www.productplan.com/glossary/daci/)
- [Medium PM101, DACI Framework: a Tool For Group Decisions(EN)](https://medium.com/pm101/daci-framework-a-tool-for-group-decisions-665bd71585cf)
