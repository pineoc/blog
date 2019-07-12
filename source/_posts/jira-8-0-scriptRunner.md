---
title: Jira 8.0 & ScriptRunner로 JQL issue 가져오기
date: 2019-06-24 23:01:44
categories:
  - PM
tags:
  - Jira
  - ScriptRunner
toc: true
thumbnail: https://marketplace-cdn.atlassian.com/files/images/396d3521-7734-4137-9a47-d7afedf1ea18.png
---

## Jira 8.0 & ScriptRunner로 JQL issue 가져오기

최근에 `ScriptRunner로 JQL 결과 이슈 가져오기` 스크립트를 찾아보고 실행해보려 했는데 잘 안되서 포스트를 작성해보았습니다.
(다른분들도 같은 문제를 겪을 것 같아서..!)

스크립트러너 문서에서의 코드는 링크에서 확인하시면 좋을 것 같습니다.
[ScriptRunner Doc: running-a-jql-query](https://scriptrunner.adaptavist.com/5.5.6/jira/recipes/misc/running-a-jql-query.html)

위 링크에 있는 코드에서 몇몇 Deprecated 코드를 수정하면 다음과 같은 코드로 정리해볼 수 있습니다.

```groovy
import com.atlassian.jira.component.ComponentAccessor;
import com.atlassian.jira.issue.search.SearchProvider;
import com.atlassian.jira.jql.parser.JqlQueryParser;
import com.atlassian.jira.web.bean.PagerFilter;

def jqlQueryParser = ComponentAccessor.getComponent(JqlQueryParser);
def searchProvider = ComponentAccessor.getComponent(SearchProvider);
def issueManager = ComponentAccessor.getIssueManager();
def user = ComponentAccessor.getJiraAuthenticationContext().getLoggedInUser();

// edit this query to suit
def query = jqlQueryParser.parseQuery("project = JRA and assignee = currentUser()");

def results = searchProvider.search(query, user, PagerFilter.getUnlimitedFilter());

log.debug("Total issues: ${results.total}");

results.getIssues().each {documentIssue ->
  log.debug(documentIssue.key);

  // if you need a mutable issue you can do:
  def issue = issueManager.getIssueObject(documentIssue.id);

  // do something to the issue...
  log.debug(issue.summary);
}
```

## 문제의 시작

그런데..
이 코드를 Script Console에서 실행해보면 아래와 같은 에러가 발생합니다.

```
groovy.lang.MissingMethodException: No signature of method: com.atlassian.jira.issue.search.providers.LuceneSearchProvider.search() is applicable for argument types: (com.atlassian.query.QueryImpl, com.atlassian.jira.user.DelegatingApplicationUser, com.atlassian.jira.web.bean.PagerFilter) values: [{project = "JRA"} AND {assignee = currentUser()}, pineoc(pineoc), ...]
Possible solutions: search(com.atlassian.jira.issue.search.SearchQuery, com.atlassian.jira.web.bean.PagerFilter), search(com.atlassian.jira.issue.search.SearchQuery, com.atlassian.jira.web.bean.PagerFilter, java.util.Set), search(com.atlassian.jira.issue.search.SearchQuery, org.apache.lucene.search.Collector), each(groovy.lang.Closure)
	at Script1071.run(Script1071.groovy:14)
```

### 에러를 요약해보자면..

- LuceneSearchProvider에 그런 메서드가 없다.
- `search(.issue.search.SearchQuery, .web.bean.PagerFilter)` 요런 형식이어야하는데
- `search(.query.QueryImpl, .user.DelegatingApplicationUser, .web.bean.PagerFilter)` 요렇게 부르고 있어서 안되는거다.
- 파라미터 형식이 너무 길어서 생략하겠습니다. (com.atlassian.jira 등이 앞에 붙어있었습니다.)

에러 내용만 봤을 때는 잘못된 파라미터로 인해 함수를 호출하지 못한다고 합니다.
공식 가이드 문서로 보고 진행했는데 에러가 나서 잠시 당황했지만 파라미터를 확인해보았습니다.

## 문제 파악

`searchProvider`의 `search()` 함수에는 다음과 같은 파라미터가 들어가야한다고 합니다.
[JIRA API docs(8.0.2)-LuceneSearchProvider](https://docs.atlassian.com/software/jira/docs/api/8.0.2/com/atlassian/jira/issue/search/providers/LuceneSearchProvider.html)

- com.atlassian.jira.issue.search.SearchQuery
- com.atlassian.jira.web.bean.PagerFilter

근데 가이드 문서에서 사용했던 함수에는 아래와 같은 파라미터를 사용했습니다.
[JIRA API docs(7.0.5)-LuceneSearchProvider](https://docs.atlassian.com/software/jira/docs/api/7.0.5/com/atlassian/jira/issue/search/providers/LuceneSearchProvider.html)

- Query query
- ApplicationUser searcher
- PagerFilter pager

위 처럼 찾아보는 과정에서 LuceneSearch 쪽 업데이트가 있어 함수 변경이 있었습니다.
그 업데이트가 Jira 8.0 버전으로 올라가면서 반영된 것 같습니다.
ScriptRunner는 Jira 8.0을 지원한다고 했지만 문서는 아직 지원하지 않는 것 같네요. (...)

### 참고

- <https://confluence.atlassian.com/adminjira/lucene-upgrade-955171970.html>
- <https://confluence.atlassian.com/adminjira/preparing-for-jira-8-0-955171967.html#PreparingforJira8.0-m06>

## 문제 해결 시도

그래도 결과를 찾아봐야하니까 문제를 해결해봅니다.

아래와 같이 코드를 수정하여 스크립트 콘솔에 적용해보았습니다.
변경된 내용 및 이유도 함께 적어둡니다.
(바로 적용해볼 수 있는 코드는 아래에 있으니 바로 사용해보시면 될 것 같습니다.)

- searchProvider.search() 함수도 앞서 설명한 것 처럼 메서드를 확인하여 변경했다.
- results.getIssues() 함수는 Jira 8.0.x에 더 이상 존재하지 않았다.
  - SearchResults에 함수에는 getResults() 함수가 존재한다.
  - getResults() 함수는 List를 반환하는데 DocumentWithId List를 반환한다. ([참고 링크 - search 함수](https://docs.atlassian.com/software/jira/docs/api/8.0.2/com/atlassian/jira/issue/search/DocumentWithId.html))
  - DocumentWithId 클래스에는 getDocument() 함수가 있는데 이 함수로 Document에 접근할 수 있다.
  - Document 오브젝트는 org.apache.lucene.document.Document 메서드를 사용하여 데이터를 접근할 수 있다. ([참고 링크 - Document 메서드](https://lucene.apache.org/core/7_2_0/core/org/apache/lucene/document/Document.html))
  - Document.getField("key") 로 접근하여 이슈의 키를 얻을 수 있다. (ex: JRA-1)

```groovy
import com.atlassian.jira.component.ComponentAccessor;
import com.atlassian.jira.jql.parser.JqlQueryParser;
import com.atlassian.jira.issue.search.SearchProvider;
import com.atlassian.jira.web.bean.PagerFilter;
import com.atlassian.jira.component.ComponentAccessor;
import com.atlassian.jira.issue.search.SearchQuery;

def findIssues(String jqlQuery) {
  def issueManager = ComponentAccessor.issueManager;
  def user = ComponentAccessor.getJiraAuthenticationContext().getLoggedInUser();
  def jqlQueryParser = ComponentAccessor.getComponent(JqlQueryParser);
  def searchProvider = ComponentAccessor.getComponent(SearchProvider);
  def query = jqlQueryParser.parseQuery(jqlQuery);
  def searchQuery = SearchQuery.create(query, user);

  // search 함수를 type 에 맞게 수정해주었다.
  def results = searchProvider.search(searchQuery, PagerFilter.getUnlimitedFilter());
  log.warn "issue cnt: ${results.getTotal()}"; // query로 얻은 이슈의 수를 확인한다.
  results.getResults().collect { res ->
    def doc = res.getDocument();
    def key = doc.get("key");
    def issue = ComponentAccessor.getIssueManager().getIssueObject(key);
    return issue;
  }
}
def jqlQuery = "project=JRA AND issuetype=Bug";
def issues = findIssues(jqlQuery);
```

### 참고

- Document 클래스 설명 문서: <https://lucene.apache.org/core/7_2_0/core/index.html?org/apache/lucene/document/Document.html>
- Document.getFields() 참고: <https://www.programcreek.com/java-api-examples/?class=org.apache.lucene.document.Document&method=getFields>
- groovy Collection 다루기<http://docs.groovy-lang.org/next/html/documentation/working-with-collections.html>

## 정리

다소 문제 해결에 애를 먹기는 했지만 해결은 했습니다.
이 글을 쓰고나서 ScriptRunner 쪽에 문서 최신화좀 해달라고 요청해야겠네요.
문서 최신화가 어려운 것은 알지만 다들 삽질할 것 같은데 피드백 얼른 남겨야겠네요.

종종 스크립트러너로 할 수 있는 기능들을 포스팅 해보겠습니다. :)
