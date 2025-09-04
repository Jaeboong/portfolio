# Sequence: 개발자 협업 및 포트폴리오 관리 플랫폼

>  아이디어 구상부터 프로젝트 아카이빙까지, 개발 협업의 모든 단계를 하나로.

<br/>

## 프로젝트 개요

**Sequence**는 분산된 개발 협업 도구들을 하나로 통합하여, 프로젝트 팀 구성부터 아이디어 구체화, 태스크 관리, 그리고 완성된 프로젝트를 포트폴리오로 관리하는 전 과정을 지원하는 **올인원 협업 플랫폼**입니다.

사용자는 아이디어를 바탕으로 프로젝트를 생성하고 팀원을 모집할 수 있으며, 프로젝트 진행 상황을 체계적으로 관리할 수 있습니다. 프로젝트가 완료되면 그 결과물과 과정, 동료들의 피드백을 **아카이브**에 기록하여 자신만의 멋진 포트폴리오를 만들어나갈 수 있습니다.

* **개발 기간**: (여기에 개발 기간을 입력하세요)
* **개발 인원**: (여기에 개발 인원을 입력하세요)

<br/>

## 주요 기능 (Key Features)

* **프로젝트 및 팀원 모집**: 아이디어를 등록하여 공개적으로 프로젝트를 생성하고, 다양한 기술 스택을 가진 개발자들에게 팀원 제안을 보내거나 지원을 받을 수 있습니다.
* **체계적인 프로젝트 관리**: 프로젝트의 현재 진행 상태(모집, 진행, 완료)를 한눈에 파악하고, 팀원을 효율적으로 관리할 수 있습니다.
* **프로젝트 아카이빙 및 포트폴리오**: 완료된 프로젝트의 과정과 결과, 사용 기술, 그리고 팀원들의 상세 정보를 기록하는 **아카이브 기능**을 제공합니다. 이는 곧바로 개인의 포트폴리오가 됩니다.
* **동료 평가 및 피드백**: 프로젝트 종료 후 함께한 동료들에 대한 객관적인 평가와 피드백을 남길 수 있으며, 이는 개인의 마이페이지에 누적되어 협업 능력의 지표가 됩니다.
* **조회수 기반 트렌드 확인**: **Redis**를 활용하여 프로젝트와 아카이브의 조회수를 실시간으로 집계하고, 인기 있는 프로젝트를 확인할 수 있는 트렌딩 시스템을 구현했습니다.
* **보안 및 인증**: **Spring Security**와 **JWT**를 도입하여 안전한 인증/인가 시스템을 구축했으며, **OAuth2**를 통한 소셜 로그인을 지원하여 사용자 편의성을 높였습니다.

---

## 🏗️ 아키텍처 (Architecture)

**MSA (Microservice Architecture)** 를 도입하여 회원 관리, 프로젝트 관리, 아카이브 등 각 도메인을 독립적인 서버로 분리하여 개발 및 배포의 유연성을 확보하고 서비스 확장성을 높였습니다.

* **API Gateway**: 모든 클라이언트 요청을 받아 적절한 마이크로서비스로 라우팅하는 단일 진입점 역할을 수행합니다.
* **Member Service**: 회원가입, 로그인, 인증/인가, 마이페이지 등 사용자 관련 기능을 전담합니다.
* **Project Service**: 프로젝트 생성, 팀원 모집, 태스크 관리 등 프로젝트 협업 기능을 담당합니다.
* **Archive Service**: 완료된 프로젝트의 기록, 동료 평가, 포트폴리오 생성 등 아카이빙 기능을 관리합니다.
* **Infra**: **Docker**와 **Jenkins**, **ArgoCD**를 활용한 CI/CD 파이프라인을 구축하여 빌드, 테스트, 배포 과정을 자동화했습니다.

---

## 🛠️ 기술 스택 (Tech Stack)

| 분야 | 기술 |
| --- | --- |
| **Backend** | ![Spring Boot](https://img.shields.io/badge/SpringBoot-6DB33F?style=for-the-badge&logo=Spring&logoColor=white) ![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=Spring-Security&logoColor=white) ![Java 17](https://img.shields.io/badge/Java_17-007396?style=for-the-badge&logo=Java&logoColor=white) ![JPA/Hibernate](https://img.shields.io/badge/JPA/Hibernate-59666C?style=for-the-badge&logo=Hibernate&logoColor=white) ![QueryDSL](https://img.shields.io/badge/QueryDSL-0d8e0d?style=for-the-badge) |
| **Database** | ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=MySQL&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=Redis&logoColor=white) |
| **Infra & DevOps**| ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=Docker&logoColor=white) ![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=Jenkins&logoColor=white) ![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=for-the-badge&logo=Argo&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=GitHub-Actions&logoColor=white) ![MinIO](https://img.shields.io/badge/MinIO-C8263F?style=for-the-badge&logo=MinIO&logoColor=white) |
| **Authentication**| ![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=JSON-Web-Tokens&logoColor=white) ![OAuth2](https://img.shields.io/badge/OAuth2-2496ED?style=for-the-badge&logo=oauth&logoColor=white) |

---

## 트러블 슈팅 및 배운 점

### **1. 무한 스크롤 구현 시 성능 최적화**
- **문제**: 프로젝트 및 아카이브 목록을 무한 스크롤로 구현할 때, 데이터가 많아질수록 쿼리 속도가 느려지고 DB 부하가 증가하는 문제가 발생했습니다. 기존의 `OFFSET` 기반 페이지네이션은 뒤 페이지로 갈수록 성능이 저하되었습니다.
- **해결**: **커서 기반 페이지네이션(Cursor-based Pagination)**을 도입했습니다. 마지막으로 조회된 데이터의 ID(혹은 정렬 기준값)를 커서로 사용하여 다음 페이지를 조회하도록 쿼리를 최적화했습니다. 이를 통해 `OFFSET` 스캔을 제거하고 일정한 쿼리 성능을 확보할 수 있었습니다.
- **배운 점**: 대용량 데이터 조회 시에는 단순 페이지네이션의 한계를 인지하고, 데이터의 특성과 서비스 요구사항에 맞는 최적화된 페이지네이션 전략(커서 기반, No-offset 등)을 적용해야 함을 배웠습니다.
