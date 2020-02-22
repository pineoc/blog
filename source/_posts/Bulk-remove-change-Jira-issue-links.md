---
title: Bulk remove change Jira issue links
toc: true
date: 2020-02-23 01:17:16
categories:
  - PM
tags:
  - Jira
  - ScriptRunner
thumbnail: https://wac-cdn.atlassian.com/dam/jcr:fa01756d-6dcc-45d1-83ab-696fbfeb074f/Jira-icon-blue.svg?cdnVersion=696
---

# Jira 이슈에 연결되어있는 이슈 링크 한번에 삭제하기

참고: <https://community.atlassian.com/t5/Jira-questions/Bulk-remove-change-issue-links-in-Jira/qaq-p/659381>

## 문제 인식

최근 특정 Jira 이슈에 연결된 이슈들을 삭제해야하는 일이 있었습니다.
(한 작업 이슈에 확인한 버그를 모두 링크를 달고 링크된 버그 이슈들을 보다가 링크 타입이 잘못된 것도 있는 등의 이슈가 있어 수정이 필요했습니다.)
Bulk로 링크들을 삭제하는 기능이 있는지 찾아보았는데 없더군요. 그래서 스크립트러너로 가능한지 찾아보았습니다.

![하나하나에 커서를 놓고 지워야합니다](https://user-images.githubusercontent.com/5077086/75095788-11eafb80-55dc-11ea-997f-30ae5dfed055.png)

다행히, 당연하게도 이미 같은 고민을 했던 사람들이 있었고 아틀라시안 커뮤니티 채널에 해결방법이 있었습니다.
기본 Jira 기능에는 없지만 스크립트러너를 사용해서 가능하다는 것이었죠.

제가 현재 사용하고 있는 Jira 버전은 8.5여서 위 링크의 8.x 코드를 보면서 설명해보고자 합니다.
(위 링크에 7.13 버전에서 사용할 수 있는 코드도 있으니 참고해서 쓰시면 됩니다.)

## 문제 해결 방법 (ScriptRunner)

```groovy
import com.atlassian.jira.component.ComponentAccessor
import com.atlassian.jira.issue.IssueManager
import com.atlassian.jira.jql.parser.JqlQueryParser
import com.atlassian.jira.bc.issue.search.SearchService
import com.atlassian.jira.web.bean.PagerFilter
import com.atlassian.query.Query

def searchService = ComponentAccessor.getComponent(SearchService)
def jqlQueryParser = ComponentAccessor.getComponent(JqlQueryParser)
def user = ComponentAccessor.getJiraAuthenticationContext().getLoggedInUser()
def results = searchService.search(user, jqlQueryParser.parseQuery("Your JQL Filter"), PagerFilter.getUnlimitedFilter())
def issueManager = ComponentAccessor.getIssueManager()

results.getResults().each
{
  def issue = issueManager.getIssueObject(it.id)
  log.warn(issue.key)
  // get all linked issues
  log.warn(ComponentAccessor.issueLinkManager.getLinkCollection(issue, user).getAllIssues())
  ComponentAccessor.issueLinkManager.removeIssueLinks(issue, user)
}
```

로그 관련한 코드는 설명 중 불필요하여 삭제했습니다. 실제 코드 동작하는데에 영향이 없습니다.
사실 코드 상으로는 크게 어려운 부분이 없습니다.

### 스크립트 Flow

1. 검색, JQL 파서, 사용자, 이슈 컨트롤러를 정의한다. (검색 및 설정 준비 과정)
2. JQL을 통해 이슈들을 가져온다.
3. 각 이슈들의 모든 링크를 삭제한다.

### issueLinkManager, removeIssueLinks

issueLinkManager 인터페이스 설명은 [jira/docs/api/8.5.1/.../IssueLinkManager](https://docs.atlassian.com/software/jira/docs/api/8.5.1/com/atlassian/jira/issue/link/IssueLinkManager.html) 이 문서에서 볼 수 있습니다.
이 매니저에는 여러가지 함수들이 있습니다. 이슈 링크의 생성, 삭제, 조회, 변경 등이 가능합니다.

removeIssueLinks() 함수도 위 issueLinkManager에서 볼 수 있는데요.

```groovy
int removeIssueLinks(Issue issue, ApplicationUser remoteUser)
// Parameters:
// issue - the Issue
// remoteUser - the remote user
// Returns:
// The total number of issuelinks deleted.
```

모든 링크를 삭제하고자하는 이슈와 삭제할 때 필요한 사용자를 받아 함수가 동작합니다.

### 스크립트 결과

맨 처음 이미지를 보여드렸던 이슈의 키를 JQL로 입력하고 실행해보겠습니다.
"key=PUBGTEST-112"로 입력하고 스크립트 콘솔에서 테스트 해보았습니다.

![](https://user-images.githubusercontent.com/5077086/75096410-b7a16900-55e2-11ea-98c1-2efedb7842d5.png)

Logs:
```
2020-02-23 02:16:42,545 WARN [runner.AbstractScriptRunner]: PUBGTEST-112
2020-02-23 02:16:42,545 WARN [runner.AbstractScriptRunner]: [PUBGTEST-75, PUBGTEST-111, PUBGTEST-225]
```

Timing: Elapsed: 4949 ms / CPU time: 531 ms
동작하는데 생각보다 시간이 많이 걸리긴 하네요.
(약 5초 정도 걸리는 것으로 보이는데 링크 삭제가 오래걸리는 것인지 다른 것이 오래걸리는 것인지는 봐야겠습니다.)

실행 결과로는 이슈의 히스토리에 아래와 같이 남았습니다.
![삭제 완료!](https://user-images.githubusercontent.com/5077086/75096443-fd5e3180-55e2-11ea-9e5f-4e6164812b95.png)

링크가 걸려있는 이슈의 모든 이슈 링크들이 삭제되었습니다! 👍

## 문제 해결!

제가 했던 하나의 이슈만 링크를 삭제할 수도 있고 JQL로 검색된 모든 이슈들의 모든 링크를 삭제할 수 있습니다.
다만 여기서 제가 원했던 것은 모든 링크의 삭제가 아니라 특정 타입의 링크들만 삭제하고 싶었던 것이어서
다음 포스트에서는 특정 링크 타입의 링크를 삭제하는 내용으로 한번 더 다뤄봐야겠습니다.

다음 포스트에서 만나요! :)
