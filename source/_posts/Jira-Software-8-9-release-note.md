---
title: Jira Software 8.9 release note
toc: true
date: 2020-05-31 16:11:52
categories:
- PM
- System
tags:
- Jira
- ReleaseNotes
thumbnail: https://wac-cdn.atlassian.com/dam/jcr:fa01756d-6dcc-45d1-83ab-696fbfeb074f/Jira-icon-blue.svg?cdnVersion=696
---

## Jira Software 8.9 릴리스 노트

Jira Software 8.9 릴리스 노트: <https://confluence.atlassian.com/jirasoftware/jira-software-8-9-x-release-notes-1003522922.html>

이번 포스트는 Jira Software 8.9 릴리스에 대해서 보겠습니다.
2020년 5월에 릴리스한 버전입니다. 이번 릴리스에도 큰 변경 사항은 없으나 그나마 멘션할 만한 내용이 있다면 속도 차트(Velocity Chart)의 업데이트가 있었습니다.

## 하이라이트 (Highlights)

- Refreshed Velocity Chart
- Get more from cluster monitoring
- Accessibility: Text spacing
- A tailored upgrade path

## Refreshed Velocity Chart

![변경된 속도 차트(Velocity Chart) 보고서](https://confluence.atlassian.com/jirasoftware/files/1003522922/1005784232/1/1588790019221/velocity_relnotes.jpg)

기능에 대한 자세한 설명은 [이 페이지](https://confluence.atlassian.com/jirasoftwareserver/velocity-chart-938845700.html)에서 볼 수 있습니다.
속도 차트는 애자일 보드에서 스프린트를 사용하는 팀이 스프린트 별 처리한 작업으로 속도를 볼 수 있도록 도와주는 차트입니다.
비즈니스 밸류, 이슈 수, 스토리 포인트 등으로 속도를 측정해볼 수 있습니다.
Board -> Reports -> Velocity Chart 메뉴에서 해당 차트를 사용해보실 수 있습니다.
(물론 스프린트를 사용해보아야 차트를 볼 수 있겠죠?)

## Accessibility: Text spacing

![](https://confluence.atlassian.com/jirasoftware/files/1003522922/1005329504/1/1589459395898/text_spacing.jpg)

개인 설정에서 자간(글자 간격)을 조정할 수 있게 되었습니다. profile > accessibilty 에서 설정할 수 있습니다.
글씨가 다닥다닥 붙어있는 것이 불편했던 분들이라면 편리한 기능이겠네요. :)

## Get more from cluster monitoring

![](https://confluence.atlassian.com/jirasoftware/files/1003522922/1005784239/1/1588790685637/Node+statuses+1+%282%29.png)

뭔가 하이라이트 항목이 앞에 있는 것과 바뀐 것 같지만, 데이터 센터 버전에서는 클러스터 모니터링과 관련한 업데이트가 있었습니다.
이번 업데이트로 오래된 노드는 눈에 띄지 않도록 변경되었습니다.
또, 클러스터 모니터링 페이지에 추가한 새로운 정보를 통해 오래된 노드를 신속하게 추적 및 제거하고 클러스터에서 실패한 노드를 수정할 수 있게 되었습니다.

Jira Administration > System > Clustering 메뉴에서 보실 수 있습니다.

## A tailored upgrade path

![](https://confluence.atlassian.com/jirasoftware/files/1003522922/1004935123/1/1588848220321/image-20200331-090110.png)

업그레이드 전에 필요한 내용들을 체크할 수 있는 기능이 8.0에 추가되었었는데 그에 대한 추가 공유네요.
버전 업그레이드하기 전에 최소한 어떤 내용을 확인해야하는지 알 수 있어서 좋은 기능이니 참고하시면 좋겠습니다.

## 마무리

이번 8.9 업데이트도 큰 컨텐츠, 기능성 업데이트는 없었네요. 버그 수정은 꽤 있긴합니다.
속도 차트의 경우는 Jira 개발팀에서 많이 사용하는 기능이라 리프레시 업데이트를 해보았다고 하는데, 속도 차트 사용 방법도 나중에 정리해서 공유해보면 어떨까 하는 생각이 드네요.
8.9 릴리스 소개는 이만 마치겠습니다. 감사합니다.
