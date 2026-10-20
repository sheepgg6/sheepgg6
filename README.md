<div align="center">

# 🐑 양금규 · Geumgyu Yang

### 데이터가 정확하게 남고, 실패 이후에도 복구되는 서비스를 만듭니다.

**Java Backend Developer · Data Batch**

[이력서](https://app.notion.com/p/sheep-gg/826bf5e2e34247d392a34933cb8a0bdb)

</div>

<br/>

## 👋 About me

업무의 불편을 자동화로 줄이는 백엔드 개발자 **양금규**입니다. Java·Spring Boot 기반으로 외부 데이터 수집부터 API, 실시간 상태 동기화까지 구현하며 **트랜잭션 경계·데이터 정합성·중단 후 재개**를 중심으로 문제를 해결해 왔습니다.

- **원인을 좁혀 해결합니다.** 알림이 저장되지만 전송되지 않는 경로를 추적해 트랜잭션 전파 문제를 해결했습니다.
- **데이터를 서비스에 맞게 연결합니다.** 실거래를 단지·면적별로 묶고, 도서 검색과 추천에 서로 다른 노출 정책을 적용했습니다.
- **현장의 흐름을 이해합니다.** 행정 업무 매크로와 기록물 검수 자동화를 개발하며 반복 작업을 개선했습니다.

<br/>

## 🚀 Projects

### MOA · My Office Agent

**오피스맵과 실시간 협업, 사내 업무 에이전트 MOAI를 연결한 플랫폼**

`2026.07 ~ 2026.08` · `6인 팀` · **SSAFY 공통 프로젝트 우수상**

| 개인 담당 | 핵심 구현 |
| --- | --- |
| 채팅·Presence·알림 | WebSocket/STOMP 이벤트, Redis 활동 상태, 읽음 커서와 다중 세션 동기화 |
| 트랜잭션·복구 | 알림 저장의 독립 트랜잭션 분리, 이벤트 유실 시 REST 재조회 |

**Java · Spring Boot · MySQL · Redis · WebSocket/STOMP**  
[서비스 화면과 문제 해결 살펴보기 →](https://github.com/sheepgg6/moa-portfolio)

### Rising Home

**실거래·경매·공매를 지도에서 비교하고 감정평가서 RAG로 탐색하는 서비스**

`2026.06` · `2인 팀` · **실거래 524만 건 · 단지 19만 개**

| 개인 담당 | 핵심 구현 |
| --- | --- |
| 데이터 배치·정제 | 지역·월별 수집, 단지·면적 통합, 가격 스냅샷 생성 |
| 조회·재실행 | 공간 인덱스 기반 지도 API, 물건별 체크포인트와 범위별 갱신 |

**Java · Spring Boot · Spring Batch · MyBatis · MySQL Spatial**  
[데이터 규모와 배치 설계 살펴보기 →](https://github.com/sheepgg6/risinghome-portfolio)


### 책추책책추

**개인 서재와 독서 취향을 바탕으로 다음 책과 추천 이유를 발견하는 서비스**

`2026.08 ~ 2026.09` · `6인 팀` · **약 331만 종 카탈로그 기반**

| 개인 담당 | 핵심 구현 |
| --- | --- |
| 백엔드·데이터 | 수집·정제·적재, 검색·추천 API 연계, 작품·판본·권차 판별 |
| 노출 정책·세션 | 검색 97.6만 권·추천 후보 40.6만 권 분리, 토큰 회전·재사용 감지 |

**Java · Spring Boot · PostgreSQL · OAuth/JWT**  
[데이터 의사결정과 문제 해결 살펴보기 →](https://github.com/sheepgg6/book-recommendation-portfolio)

<sub>도서 수는 프로젝트 데이터 스냅샷 기준입니다.</sub>

<br/>

## 🛠 Tech Stack

| 영역 | 프로젝트에서 사용한 기술 |
| --- | --- |
| Backend | ![Java](https://img.shields.io/badge/Java-007396?style=for-the-badge) ![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white) ![Spring Batch](https://img.shields.io/badge/Spring_Batch-6DB33F?style=for-the-badge&logo=spring&logoColor=white) ![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white) |
| Data Access | ![JPA](https://img.shields.io/badge/JPA-59666C?style=for-the-badge&logo=hibernate&logoColor=white) ![MyBatis](https://img.shields.io/badge/MyBatis-363636?style=for-the-badge) ![JDBC](https://img.shields.io/badge/JDBC-007396?style=for-the-badge) ![Flyway](https://img.shields.io/badge/Flyway-CC0200?style=for-the-badge&logo=flyway&logoColor=white) |
| Database & Search | ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white) ![Qdrant](https://img.shields.io/badge/Qdrant-DC244C?style=for-the-badge) |
| Real-time & Test | ![WebSocket](https://img.shields.io/badge/WebSocket-4353FF?style=for-the-badge) ![STOMP](https://img.shields.io/badge/STOMP-4353FF?style=for-the-badge) ![JUnit](https://img.shields.io/badge/JUnit-25A162?style=for-the-badge&logo=junit5&logoColor=white) ![Testcontainers](https://img.shields.io/badge/Testcontainers-2496ED?style=for-the-badge&logo=testcontainers&logoColor=white) |
| Delivery & Collaboration | ![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white) ![GitLab](https://img.shields.io/badge/GitLab-FC6D26?style=for-the-badge&logo=gitlab&logoColor=white) ![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) ![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white) ![Jira](https://img.shields.io/badge/Jira-0052CC?style=for-the-badge&logo=jira&logoColor=white) ![Notion](https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white) |

<br/>

## 🌱 Journey & Experience

| 기간 | 경험 |
| --- | --- |
| 2026.01 ~ 현재 | **SSAFY 15기 Java 전공트랙** |
| 2025.08 ~ 2025.09 | 코멘토 백엔드 개발 실무 교육 |
| 2025.04 ~ 2025.06 | 제 21대 대통령선거 지역선거관리위원회 공정선거지원단 본부반 업무 지원 및 사이버 정보 파악 자동화 |
| 2024.06 ~ 2024.10 | 아키아카 기록물 DB 구축·검수 자동화 스크립트 개발 |
| 2024.03 ~ 2024.04 | AWS Technical Essentials·3-Tier 아키텍처 실습 |
| 2022.07 ~ 2022.08 | 수원출입국외국인청 행정 업무 지원·매크로 개발 및 유지보수 |
| 2018.03 ~ 2024.02 | **아주대학교 디지털미디어학·소프트웨어 복수전공** · 학점 **4.31 / 4.5** |

### Certifications

**빅데이터분석기사** `2026.07` · **SQLD** `2026.06` · **정보처리기사** `2024.06` · **컴퓨터활용능력 1급** `2020.02`

**TOEIC Speaking · IH / 150점** `2023.11.18 응시`

<br/>

## 🧩 etc

<p align="center">
  <img src="https://mazassumnida.wtf/api/v2/generate_badge?boj=sheep_gg" alt="sheep_gg solved.ac 프로필 배너" />
</p>
