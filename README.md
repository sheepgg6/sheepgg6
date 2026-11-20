<div align="center">

# 🐑 양금규 · Geumgyu Yang

### 느려진 이유는 재서 찾고, 멈춘 작업은 이어서 끝내는 백엔드 개발자입니다.

**Java Backend Developer**

[이력서](https://app.notion.com/p/sheep-gg/826bf5e2e34247d392a34933cb8a0bdb)

</div>

<br/>

## 👋 About me

Java·Spring Boot로 서비스 백엔드와 공공데이터 수집 배치를 만들어 왔습니다. 추측 대신 같은 조건으로 전후를 재고, 원인을 좁힌 뒤 고칩니다. 외부 장애나 중단에도 데이터가 빠지지 않고 이어서 처리되는 구조를 중요하게 생각합니다.

- **측정으로 원인을 찾습니다.** k6 부하와 실제 DB로 재현해, 커넥션 부족처럼 보이던 지연에서 행 락을 찾아 다른 API 응답을 4.1초에서 45ms로 줄였습니다.
- **멈춰도 이어지게 만듭니다.** 호출 한도와 외부 장애가 있어도 체크포인트와 재개 지점으로 남은 것만 다시 처리해, 도서 109만 건을 무인으로 수집하고 실거래 524만 건을 적재했습니다.
- **데이터가 빠지지 않게 검증합니다.** 업무 데이터와 이벤트를 같은 트랜잭션에 기록하고, 22만 건 처리 뒤 조회수·기록 수·발행 이벤트 수 일치와 교착 0건을 확인했습니다.
- **현장의 반복 업무를 개선합니다.** 행정 업무 매크로와 기록물 검수 자동화를 개발하며 사용자의 작업 흐름을 이해해 왔습니다.

<br/>

## 🚀 Projects

### ARA · Artist Reels Auction

**작업 숏폼부터 실시간 경매, 블록체인 보증서 이전까지 잇는 미술품 경매 서비스**

`2026.10 ~ 2026.11` · `6인 팀` · 도메인별 서비스 6개를 ECS Fargate에 따로 배포

<table>
<thead>
<tr><th nowrap>개인 담당</th><th>핵심 구현</th></tr>
</thead>
<tbody>
<tr><td nowrap>작품·숏폼 도메인 (주 담당)</td><td>DB·API·이벤트 계약 설계, 출품부터 알림함까지 핵심 기능, 영상 변환 워커, 부하·장애 시험</td></tr>
<tr><td nowrap>팀 개발 기반</td><td>코드 리뷰 템플릿·라벨, AI 도구(Claude Code·Codex) 공통 작업 규칙과 다른 도메인 파일 수정을 막는 훅</td></tr>
<tr><td nowrap>서비스 전체 모니터링</td><td>장애·정합성 대시보드, 업무 지표 수집, Grafana 알림, 큐·DLQ 현황, 서비스 간 이벤트 흐름 지도</td></tr>
<tr><td nowrap>AI 서버 배포</td><td>Jenkins CI/CD 파이프라인, 바뀐 경로만 골라 자동 배포</td></tr>
</tbody>
</table>

- **4.1초 → 45ms** 부하 중 다른 API 평균 응답 · 조회수 행 락을 대기 줄과 일괄 반영으로 해소
- **약 3,600건 → 약 3.2만 건** 과부하 30초 동안 받아 낸 재생 기록 · 거절하던 기록을 묶어 쓰기와 재전송으로 보존
- **362초 → 1.2초** 작품 숨김 이벤트 발행 지연 · 업무 이벤트를 먼저 보내는 Outbox 차선 분리

Java 21 · Spring Boot 4 · PostgreSQL 18 · Flyway · Python · FFmpeg · AWS S3·SQS·SNS · Testcontainers · k6 · Prometheus · Grafana · Jenkins

[서비스 화면과 문제 해결 살펴보기 →](https://github.com/sheepgg6/ara-portfolio)

### MOA · My Office Agent

**오피스맵과 실시간 협업, 사내 업무 에이전트 MOAI를 연결한 플랫폼**

`2026.07 ~ 2026.08` · `6인 팀` · **SSAFY 프로젝트 우수상**

<table>
<thead>
<tr><th nowrap>개인 담당</th><th>핵심 구현</th></tr>
</thead>
<tbody>
<tr><td nowrap>채팅</td><td>채팅방 행 잠금으로 메시지 순번, 읽음 위치, 끊긴 뒤 이어 받기</td></tr>
<tr><td nowrap>알림</td><td>업무 데이터와 같은 트랜잭션에 저장, 처리 큐로 재시도·실패 격리</td></tr>
<tr><td nowrap>Presence·실시간 인프라</td><td>여러 탭 접속을 Redis TTL 키로 묶은 활동 상태, STOMP 구독 허용 목록, 업무·위치 채널 분리</td></tr>
</tbody>
</table>

- **0건 → 매번 발행** 실시간 알림 프레임 · 커밋 뒤 실행되던 알림 저장을 새 트랜잭션으로 분리
- **2N+F회 → 최대 3회** 메시지 페이지당 추가 조회 · 반복 조회를 `IN` 조회와 배치 API로 변경
- **140ms → 7.5ms** 채팅방 100개 목록 응답 (프로젝트 후) · 같은 N+1을 실제 MySQL로 측정하고 개선

Java 25 · Spring Boot 4.1 · MySQL 8.4 · Redis 8.2 · RabbitMQ · WebSocket(STOMP) · Testcontainers

[서비스 화면과 문제 해결 살펴보기 →](https://github.com/sheepgg6/moa-portfolio)

### Rising Home

**실거래·경매·공매를 지도에서 비교하고 감정평가서 RAG로 탐색하는 서비스**

`2026.06` · `2인 팀` · **실거래 524만 건 · 단지 19.5만 개**

<table>
<thead>
<tr><th nowrap>개인 담당</th><th>핵심 구현</th></tr>
</thead>
<tbody>
<tr><td nowrap>수집 배치</td><td>국토부 실거래 4종을 지역·월 단위로 수집·정규화, 단지·면적별 가격 스냅샷과 일일 갱신</td></tr>
<tr><td nowrap>외부 API 연동</td><td>건축HUB·온비드·카카오 지오코딩을 Job으로 나누고 체크포인트·재개 지점·오류별 재시도</td></tr>
<tr><td nowrap>조회 API</td><td>공간 인덱스 지도 마커, 지역 클러스터, 단지 상세·공매·관심 목록</td></tr>
</tbody>
</table>

- **0건 → 689건** 법정동 20곳에서 저장된 건축물 표제부 · 대지구분과 PNU 토지구분 코드 변환을 테스트로 고정
- **약 44초 → 1~2초** 제공처 오류 1건 처리 · 같은 오류를 계속 주는 응답은 1초 뒤 한 번만 재시도, 물건별 체크포인트로 멈춰도 남은 것만 재실행
- **596ms → 5.5ms** 지도 클러스터 요청 p95 (프로젝트 후) · 지역별 집계 테이블과 화면 범위 인덱스

Java 21 · Spring Boot · Spring Batch · MyBatis · JdbcTemplate · MySQL 공간 인덱스

[데이터 규모와 배치 설계 살펴보기 →](https://github.com/sheepgg6/risinghome-portfolio)

### 책추책책추

**개인 서재와 독서 취향을 바탕으로 다음 책과 추천 이유를 발견하는 서비스**

`2026.08 ~ 2026.09` · `6인 팀` · **도서 331만 권 · 검색 97.6만 권 · 추천 후보 40.6만 권**

<table>
<thead>
<tr><th nowrap>개인 담당</th><th>핵심 구현</th></tr>
</thead>
<tbody>
<tr><td nowrap>데이터 수집·적재</td><td>도서관 정보나루·카카오·국립중앙도서관 수집기, DuckDB로 정제해 PostgreSQL에 적재</td></tr>
<tr><td nowrap>데이터 정책</td><td>수집 목록·검색 노출·추천 후보를 따로 정의하고 DB 제약으로 고정</td></tr>
<tr><td nowrap>인증·도서 API</td><td>카카오·Google 로그인, 리프레시 토큰 회전·재사용 감지, 인기·상세·비슷한 책 API</td></tr>
</tbody>
</table>

- **19,472건 복구** "데이터 없음"으로 잘못 기록된 도서 · 호출 한도를 넘긴 빈 응답을 감지해 재수집 대상으로
- **58,222권 제외** 소장 도서관이 없는 책의 검색 노출 · 수집 목록을 노출 기준으로 쓰던 설계 분리
- **27권 → 1권** 판본 많은 고전 30권 중 「비슷한 책」이 8권 미만인 책 (프로젝트 후) · 같은 작품의 판본을 먼저 제외

Java 21 · Spring Boot 3.5 · PostgreSQL 16 · Elasticsearch · Qdrant · DuckDB · Python

[데이터 의사결정과 문제 해결 살펴보기 →](https://github.com/sheepgg6/book-recommendation-portfolio)

<sub>도서 수는 프로젝트 데이터 스냅샷 기준입니다.</sub>

<br/>

## 🛠 Tech Stack

<table>
<thead>
<tr><th nowrap>분야</th><th nowrap>기술</th><th nowrap>숙련도</th><th>활용</th></tr>
</thead>
<tbody>
<tr><td nowrap>Backend</td><td nowrap>Java</td><td nowrap>★★★★☆</td><td>네 프로젝트의 주력 언어, 스레드 풀·락·트랜잭션 경계 설계와 테스트</td></tr>
<tr><td nowrap>Backend</td><td nowrap>Spring Boot</td><td nowrap>★★★★☆</td><td>REST API, 트랜잭션 이벤트, JWT·OAuth 인증, 장애 시 503 처리</td></tr>
<tr><td nowrap>Backend</td><td nowrap>Spring Batch</td><td nowrap>★★★☆☆</td><td>지역×월 단위 대량 수집 Job, 체크포인트로 중단 지점부터 재개</td></tr>
<tr><td nowrap>Backend</td><td nowrap>WebSocket · STOMP</td><td nowrap>★★★☆☆</td><td>구독 허용 목록, 세션 분리, 송신 상한, 신호를 놓쳐도 REST로 이어 받기</td></tr>
<tr><td nowrap>Backend</td><td nowrap>JPA · MyBatis · JdbcTemplate</td><td nowrap>★★★☆☆</td><td>조회 성격에 맞게 선택, 락·조건부 UPDATE·대량 저장은 SQL 직접 작성</td></tr>
<tr><td nowrap>Data</td><td nowrap>PostgreSQL</td><td nowrap>★★★☆☆</td><td>실행 계획 확인과 부분 인덱스, 행 락·SKIP LOCKED·DELETE … RETURNING</td></tr>
<tr><td nowrap>Data</td><td nowrap>MySQL</td><td nowrap>★★★☆☆</td><td>공간 인덱스(R-tree)와 B+tree 비교 측정, N+1을 IN 조회로 개선</td></tr>
<tr><td nowrap>Data</td><td nowrap>Redis</td><td nowrap>★★☆☆☆</td><td>만료 시간(TTL) 키로 여러 탭의 접속 상태 관리</td></tr>
<tr><td nowrap>Ops</td><td nowrap>Prometheus · Grafana</td><td nowrap>★★★☆☆</td><td>업무 지표 수집, 장애·정합성 대시보드와 알림 구성</td></tr>
<tr><td nowrap>Ops</td><td nowrap>Docker</td><td nowrap>★★☆☆☆</td><td>로컬 DB와 서비스를 Docker Compose로 구성</td></tr>
<tr><td nowrap>협업</td><td nowrap>GitHub · GitLab · Jira · Notion</td><td nowrap>—</td><td>이슈 관리, 코드 리뷰, 문서 협업</td></tr>
</tbody>
</table>

<sub>★ 1 기초 · 2 초급 · 3 중급(혼자 기능 구현과 문제 해결) · 4 상급(설계와 성능 개선까지) · 5 전문</sub>

<br/>

## 🌱 Journey & Experience

<table>
<thead>
<tr><th nowrap>기간</th><th>경험</th></tr>
</thead>
<tbody>
<tr><td nowrap>2026.01 ~ 현재</td><td><strong>SSAFY 15기 Java 전공트랙</strong></td></tr>
<tr><td nowrap>2025.08 ~ 2025.09</td><td>코멘토 백엔드 개발 실무 교육</td></tr>
<tr><td nowrap>2025.04 ~ 2025.06</td><td>제 21대 대통령선거 지역선거관리위원회 공정선거지원단 본부반 업무 지원 및 사이버 정보 파악 자동화</td></tr>
<tr><td nowrap>2024.06 ~ 2024.10</td><td>아키아카 기록물 DB 구축·검수 자동화 스크립트 개발</td></tr>
<tr><td nowrap>2024.03 ~ 2024.04</td><td>AWS Technical Essentials·3-Tier 아키텍처 실습</td></tr>
<tr><td nowrap>2022.07 ~ 2022.08</td><td>수원출입국외국인청 행정 업무 지원·매크로 개발 및 유지보수</td></tr>
<tr><td nowrap>2018.03 ~ 2024.02</td><td><strong>아주대학교 디지털미디어학·소프트웨어 복수전공</strong> · 학점 <strong>4.31 / 4.5</strong></td></tr>
</tbody>
</table>

### Certifications

**빅데이터분석기사** `2026.07` · **SQLD** `2026.06` · **정보처리기사** `2024.06` · **컴퓨터활용능력 1급** `2020.02`

**TOEIC Speaking · IH / 150점** `2023.11`

<br/>

## 🧩 etc

<p align="center">
  <img src="https://mazassumnida.wtf/api/v2/generate_badge?boj=sheep_gg" alt="sheep_gg solved.ac 프로필 배너" />
</p>
