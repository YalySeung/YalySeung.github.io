---
title : "Git Repository Managing System"
excerpt : "Git Repository Managing System"
toc : true
toc_sticky : true
toc_label : "Git Repository Managing System"
categories:
- Git
tags:
- [Git]
last_modified_at: 2024-08-20T08:00:00-10:00:00
---
  
---
  
 이 글에서는 **Git Repository Managing System** 에 대해서 알아보고 어떤 제품군이 있는지 살펴보겠다.

 필자는 금융권 SI 프로젝트에 투입될 예정이며, 서버 개발자로서 **폐쇄망**에 Git Repository를 구성해야 해야 하는 상황에 처했다.

 어떤 Git Repository Manager System이 프로젝트에 적합할까 찾아보며, 정리해보았다.
  
## Git Repository Managing System 종류
 우리가 흔히 알고 있는 Github, GitLab, Gitea 이외에도 다양한 제품군이 존재한다.
  
| 제품명           | 설명                                                                                                    |
| ------------- | ----------------------------------------------------------------------------------------------------- |
| Bitbucket     | Atlassian에서 제공하는 Git, Mercurial Repository 호스팅 서비스로 Jira, Confluence와 같은 Atlassian 제품과 통합 가능          |
| GitKraken     | Git Client 및 호스팅 플랫폼 제공, GUI 기반의 Git Client로 유명함, 자제적 Repository 호스팅 가능                               |
| SourceForge   | 오픈 소스 프로젝트를 중심으로 한 Git 호스팅 플랫폼                                                                        |
| Phabricator   | Facebook에서 개발된 Git Repository 관리 및 코드 리뷰 도구, 강력한 코드 리뷰, 작업 관리 및 버전 관리 기능을 제공                          |
| Gerrit        | Google에서 개발된 오픈소스 Git 코드 리뷰 툴, 대규모 프로젝트에서 코드 리뷰 프로세스를 강력하게 관리                                         |
| RhodeCode     | 기업용으로 설계된 Git, Mercurial, Subversion 호스팅 플랫폼, 코드리뷰와 CI/CD 와 같은 고급 기능 제공                               |
| AWSCodeCommit | Amazon Web Service 에서 제공하는 Git 호스팅 서비스, 클라우드 환경에서 Git Repository를 안정하게 관리 가능                          |
| GitHub        | 가장 널리 사용되는 Git 호스팅 플랫폼, 오픈 소스와 개인 프로젝트 모두를 위한 웹 기반 Git Repository 호스팅을 제공, 다양한 협업 기능과 커뮤니티 지원을 갖추고 있음 |
| Gitea         | GitHub와 유사한 인터페이스를 제공, 설치와 운영이 간편함, 다양한 플랫폼을 지원하며, Docker 이미지로 배포 가능                                  |
| GitBlit       | java로 작성된 오픈소스 Git Repository 관리 툴, 비교적 단순하며, 소규모 팀이나 개인 프로젝트에 적합, 웹 인터페이스를 통해 Repository 관리 용이       |
| GitLab        | CI/CD 기능이 뛰어난 Git Repository Managing System, 프로젝트 관리, 코드리뷰, 이슈 트래킹, CI/CD 파이프라인 등의 기능 제공             |

 필자는 이중에 폐쇄망에 적합한 Git Repository managing System으로 Gitea를 선택했다. **가볍고 설치 및 관리가 간편**하며, **낮은 시스템 리소스를 사용**하기 때문에 이번 프로젝트에 적합하다고 판단했다.
  
---
  
# 연결문서