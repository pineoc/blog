---
title: Jira Bulk remove issue links (by link type)
toc: true
date: 2020-02-28 19:37:15
categories:
  - PM
tags:
  - Jira
  - ScriptRunner
thumbnail: https://wac-cdn.atlassian.com/dam/jcr:fa01756d-6dcc-45d1-83ab-696fbfeb074f/Jira-icon-blue.svg?cdnVersion=696
---

# Jira 이슈 링크(issue link) 삭제하기

관련 포스트: {% post_link Bulk-remove-change-Jira-issue-links %}
위 포스트에서는 이슈에 걸려있는 모든 링크를 삭제하는 것을 공유드렸었습니다.
이번 포스트에서는 이슈에 걸려있는 링크 중에 특정 타입의 링크를 삭제하는 방법을 공유해보겠습니다.

## 이슈 - 이슈 링크

Jira에서 이슈와 이슈를 연결해주는 이슈 링크,
전의 포스트에서는 링크를 그냥 다 삭제하는 포스트였기에 자세히 다루지는 않았지만 이번 포스트에서는 링크 타입에 대해 알아야 정확하게 삭제할 수 있기에 조금 더 자세히 설명해보고자 합니다.

![Administration > issues > Issue linking 설정 화면](https://user-images.githubusercontent.com/5077086/75603626-8ad5e000-5b13-11ea-8e18-3dde7627b794.png)

위와 같이 이슈 링크 속성에는 `Name`, `Outward Description`, `Inward Description` 항목이 있습니다.
> 한국어 버전으로는 이슈 링크 속성 이름이 명확한지 모르겠지만 다음과 같네요. `이름(Name)`, `가르키는 입장 설명(Outward Desc)`, `받는 입장 설명(Inward Desc)`

Jira 시스템에 기본적으로 있는 이슈 링크 타입은 4개로 `Blocks`, `Cloners`, `Duplicate`, `Relates` 이렇게 구성되어 있습니다.
각각 링크 타입 항목들을 보면 이슈와 이슈를 연결했을 때 각 이슈에 보이는 링크의 이름이 다르게 보일 수 있도록 설정할 수 있습니다.

이슈 링크를 설정하고 어떻게 보이는지 아래의 문서 링크를 참고하시면 좋을 것 같습니다.
[(EN) Jira Docs: linking issues](https://confluence.atlassian.com/jiracoreserver/linking-issues-939937913.html)

"이슈 - 이슈 링크"의 관계를 정리해보자면, 아래와 같이 볼 수 있겠습니다.

- 이슈는 **목적지**
- 이슈 링크는 **출발지와 도착지 정보를 가지고 있는 화살표**

## 이슈 링크 타입 확인해보자

개념적인 설명은 이만 마치고 스크립트를 통해 이슈에 있는 이슈 링크들을 한번 확인해보겠습니다.
우선 테스트를 위해 이슈에 설정한 이슈 링크들은 아래와 같습니다.

![PUB-16 issue link 설정](https://user-images.githubusercontent.com/5077086/75604076-5fa1bf80-5b18-11ea-8a20-41cda7e01a67.png)

링크된 항목들을 정리해보면 다음과 같습니다. 괄호 내용은 이슈 링크 이름입니다.

- PUB-16 (blocks) PUB-1
- PUB-16 (blocks) PUB-2
- PUB-16 (blocks) PUB-3
- PUB-16 (clones) PUB-5570
- PUB-16 (duplicates) PUB-17
- PUB-16 (is blocked by) PUB-4

PUB-16 이슈에 연결된 이슈 링크들을 확인하기 위한 스크립트 입니다.
스크립트를 ScriptRunner에 Script console에서 실행된 내용을 볼 수 있습니다.

### 스크립트 코드

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
def results = searchService.search(user, jqlQueryParser.parseQuery("key=PUB-16"), PagerFilter.getUnlimitedFilter())
def issueManager = ComponentAccessor.getIssueManager()
def issueLinkManager = ComponentAccessor.getIssueLinkManager()

results.getResults().each
{
  def issue = issueManager.getIssueObject(it.id)
  log.warn("Get InwardLinks")
  def linkInwardList = issueLinkManager.getInwardLinks(issue.getId())
  linkInwardList.each {
    log.warn("${it.getIssueLinkType().getName()}, ${it.getSourceObject().getKey()}")
  }
  log.warn("Get OutwardLinks")
  def linkOutwardList = issueLinkManager.getOutwardLinks(issue.getId())
  linkOutwardList.each {
    log.warn("${it.getIssueLinkType().getName()}, ${it.getDestinationObject().getKey()}")
  }
}
```

### 스크립트 실행 결과

```log
...: Get InwardLinks
...: Blocks, PUB-4
...: Duplicate, PUB-17
...: Get OutwardLinks
...: Blocks, PUB-1
...: Blocks, PUB-2
...: Blocks, PUB-3
...: Clones, PUB-5570
```

## 이슈 링크 타입에 따라 이슈 링크를 삭제해보자

이슈 링크 타입을 확인했으니 이슈 링크 타입에 따라 삭제할 수 있게 되었습니다.
사실 위 링크 확인 스크립트 코드에서 **타입**과 **inward/outward** 만 확인해서 이슈 링크 삭제 함수만 사용하면 우리가 원하는 링크 삭제가 가능합니다.

### 이슈 링크 타입 확인 & 삭제

이슈 링크 타입을 확인하는 것 자체는 어렵지 않습니다.
`issueLinkObj.getIssueLinkType().getName()`로 이름을 확인하면 되니까요.
다만 Inward, Outward 링크 타입을 확인해야하는데, 삭제할 때에 아래 옵션을 선택할 수 있도록 함수를 만들어야겠네요.

- Inward 링크만
- Outward 링크만
- 모든 링크

삭제 함수도 간단합니다. 참고: [Jira API Docs: IssueLinkManager.removeIssueLink()](https://docs.atlassian.com/software/jira/docs/api/8.5.1/com/atlassian/jira/issue/link/IssueLinkManager.html#removeIssueLink-com.atlassian.jira.issue.link.IssueLink-com.atlassian.jira.user.ApplicationUser-)
아래 함수를 위에서 확인한 이슈 링크를 파라미터로 호출하면 링크 삭제가 가능합니다.

```groovy
// issueLink - the issue link to remove
// remoteUser - needed for creation of change items
void removeIssueLink(IssueLink issueLink, ApplicationUser remoteUser)
```

### 스크립트 코드

```groovy
import com.atlassian.jira.component.ComponentAccessor
import com.atlassian.jira.issue.IssueManager
import com.atlassian.jira.jql.parser.JqlQueryParser
import com.atlassian.jira.bc.issue.search.SearchService
import com.atlassian.jira.web.bean.PagerFilter
import com.atlassian.query.Query
import com.atlassian.jira.issue.MutableIssue

def searchService = ComponentAccessor.getComponent(SearchService)
def jqlQueryParser = ComponentAccessor.getComponent(JqlQueryParser)
def issueManager = ComponentAccessor.getIssueManager()
def issueLinkManager = ComponentAccessor.getIssueLinkManager()

def user = ComponentAccessor.getJiraAuthenticationContext().getLoggedInUser()
// NOTE: jql options
def results = searchService.search(user, jqlQueryParser.parseQuery("key=PUBGTEST-3"), PagerFilter.getUnlimitedFilter())

// NOTE: remove link options
def removeLinkType = "Blocks"
def removeLinkIO = "all" // all, inward, outward

def removeInwardLinks = {MutableIssue issue ->
  def linkInwardList = issueLinkManager.getInwardLinks(issue.getId())
  linkInwardList.each {
    def link = it
    if (link.getIssueLinkType().getName() == removeLinkType) {
      log.warn("removed links: ${link.getIssueLinkType().getName()}, ${link.getSourceObject().getKey()}")
      issueLinkManager.removeIssueLink(link, user)
    }
  }
}
def removeOutwardLinks = {MutableIssue issue ->
  def linkInwardList = issueLinkManager.getOutwardLinks(issue.getId())
  linkInwardList.each {
    def link = it
    if (link.getIssueLinkType().getName() == removeLinkType) {
      log.warn("removed links: ${it.getIssueLinkType().getName()}, ${it.getDestinationObject().getKey()}")
      issueLinkManager.removeIssueLink(link, user)
    }
  }
}

results.getResults().each {
  def issue = issueManager.getIssueObject(it.id)
  if (removeLinkIO == "all" || removeLinkIO == "inward") {
    log.warn("Get & Remove InwardLinks")
    removeInwardLinks(issue)
  }

  if (removeLinkIO == "all" || removeLinkIO == "outward") {
    log.warn("Get & Remove OutwardLinks")
    removeOutwardLinks(issue)
  }
}
```

### 스크립트 결과

현재 스크립트 상으로는 **all(inward, outward)**, **blocks** 타입의 링크만 삭제하도록 구성되어 있어 실행시 blocks 타입의 링크가 모두 삭제됩니다.

## 활용

위 스크립트를 활용시에는 **NOTE:** 라고 표시된 내용에 링크 삭제가 필요한 이슈, 링크 타입을 알맞게 변경을 한 뒤에 사용하시면 됩니다.
이슈 링크 삭제 시에 주의해서 사용해주세요!

## 마무리

이번 내용은 약간 길어졌는데요. 포스트를 작성하면서 이슈와 이슈 링크의 관계, 이슈 링크의 속성 등에 대해서 공부할 수 있어서 좋았고 이 글을 보시는 다른분들도 스크립트를 이용하여 원하는 이슈 링크를 삭제할 수 있었으면 좋겠습니다.
감사합니다. 😀