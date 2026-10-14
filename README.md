# 안녕하세요, 백엔드 개발자 나영준입니다 👋

> **문제를 직접 찾아 기획하고, 배포해서 실제 사용자 앞에 내놓는 개발자입니다.**
> 학우들의 식비 고민에서 출발한 서비스로 **광주일보 인터뷰 보도**를 받았고, 4인 캡스톤 팀의 **팀장 · 백엔드 리드**로 AI 추천 기능과 협업 프로세스를 이끌었습니다.

<p>
  <a href="https://www.notion.so/af866e443fdc45cb8d58adf062166958?source=copy_link"><img src="https://img.shields.io/badge/Notion-포트폴리오_·_이력서-000000?style=flat-square&logo=notion&logoColor=white"/></a>
  <a href="https://airforce836.tistory.com"><img src="https://img.shields.io/badge/Tech_Blog-트러블슈팅_기록-EB531F?style=flat-square&logo=tistory&logoColor=white"/></a>
  <a href="http://kwangju.co.kr/article.php?aid=1779183000799171028"><img src="https://img.shields.io/badge/광주일보-인터뷰_보도-1F6FEB?style=flat-square"/></a>
</p>

---

## 🙋 About Me

- **끝까지 완주하는 실행력** — 아이디어에서 끝나지 않고 데이터 수집, 개발, 배포, 운영까지 직접 책임집니다. 조대 후문 가성비 맛집 지도는 식당을 직접 방문해 데이터를 검증하고 첫 커밋 당일 배포해, 학우들이 실제로 쓰는 서비스가 되었습니다.
- **설계 이유를 설명할 수 있는 백엔드** — 인덱스는 실제 쿼리 패턴에 맞춰 만들고, LLM 응답은 그대로 믿지 않고 DB로 다시 검증하는 것처럼 "왜 이렇게 만들었는지"를 근거와 함께 남깁니다. 정보처리기사 · SQLD로 다진 데이터 모델링 기초가 바탕입니다.
- **팀을 움직이는 리더십** — 컴퓨터공학과 학생회장으로 900명 규모 행사를 총괄했고, 캡스톤 프로젝트에서는 팀장으로서 Pull Request 18건을 모두 리뷰 · 머지하며 4명이 같은 코드베이스에서 안정적으로 협업하도록 이끌었습니다.

---

## 📌 Projects

### 🚀 [Team Builder](https://github.com/happyzerojun/team-builder-backend) — AI 추천 기반 팀원 매칭 플랫폼
`팀장 · 백엔드 리드` `4인` `2026.03 ~ 06`
`Java 21` `Spring Boot 3.5` `JPA` `MySQL` `OAuth2 · JWT` `Gemini API` `Docker` `AWS EC2`

- **자연어 프로젝트 추천 엔진** — 요청에서 기술 스택을 추출해 DB에서 후보를 먼저 좁히고(RAG), Gemini가 고른 결과를 **DB에서 다시 검증해 존재하지 않는 프로젝트(환각)를 걸러내는** 구조로 설계
- 사용자 · 프로젝트 · 기술 스택 · 지원 · 상호 평가를 아우르는 **ERD와 엔티티 설계**, N:M 관계 분리와 도메인 메서드로 규칙 캡슐화
- Docker Compose 실행 환경 표준화, Swagger 문서화, **PR 18건 리뷰 · 머지 및 병합 충돌 해결**
- 종료 후 셀프 리뷰로 예외 메시지 노출 · 외부 API 타임아웃 부재 · 상태 전이 검증 누락을 고치고 GitHub Actions CI 도입 → [트러블슈팅](https://github.com/happyzerojun/team-builder-backend/blob/main/docs/troubleshooting.md)

### 🛒 [Commerce Web](https://github.com/happyzerojun/commerceweb-project) — 협업 필터링 추천 쇼핑몰
`풀스택` `2인` `2026.01`
`Java 21` `Spring Boot 3.4` `Spring Security` `PostgreSQL` `Redis` `React` `Docker Compose` `Nginx` `AWS EC2`

- **사용자 기반 협업 필터링** — 셀프 조인 쿼리로 유사 사용자를 DB에서 한 번에 찾고, 신규 사용자 Cold Start는 인기 상품으로 대체, 결과는 **Redis에 캐싱**
- JWT 무상태 인증과 역할(구매자 / 판매자)별 접근 제어, **주문 이력으로 검증하는 리뷰**로 평점 조작 방지
- PostgreSQL · Redis · Spring · Nginx 4개 서비스를 Docker Compose로 구성해 EC2 배포, Mockito 단위 테스트로 추천 로직 검증
- 셀프 리뷰로 위조 서명 JWT가 500이 되던 문제, 추천 순위가 `IN` 조회 순서로 뒤섞이던 버그를 회귀 테스트와 함께 수정 → [트러블슈팅](https://github.com/happyzerojun/commerceweb-project/blob/main/docs/troubleshooting.md)

### 🍽️ [조대 후문 가성비 맛집 지도](https://github.com/happyzerojun/chosun-food-map) — 위치 기반 맛집 · 익명 리뷰 서비스
`1인 개발` `광주일보 보도` `2026.05 ~ 06`
`React 19` `Kakao Map` `Supabase (PostgreSQL)` `Vercel Serverless`

- 로그인 없는 익명 리뷰의 도배를 막기 위해 **IP를 SHA-256 + pepper로 해시해 저장(원문 미보관)** 하고, 식당별 하루 1회 작성 제한을 서버에서 검증
- 리뷰 비밀번호는 bcrypt 해시만 저장, DB 쓰기 키는 서버리스 함수에만 두어 브라우저에 노출하지 않는 구조
- 실제 실행되는 두 쿼리에 맞춘 **복합 인덱스 설계**, 가격 · 별점을 마커에 바로 띄우는 지도 UX와 마커 클러스터링
- 하루 1회 제한의 조회 후 저장 경쟁 조건을 DB 유니크 인덱스로 막고, UTC 기준 날짜 버그를 KST로 수정 → [트러블슈팅](https://github.com/happyzerojun/chosun-food-map/blob/main/docs/troubleshooting.md)

### 🏫 [M-SPACE](https://github.com/happyzerojun/M-SPACE) — 학과 공간 예약 시스템
`백엔드` `요구사항 → ERD → API → 구현` · [데모](https://m-space-rho.vercel.app)
`Java` `Spring Boot 4.1` `JPA` `PostgreSQL 17` `Testcontainers` `Git Flow`

- 겹치는 예약을 애플리케이션 조회가 아니라 **PostgreSQL `EXCLUDE` 제약(btree_gist)** 으로 막도록 스키마 설계, 같은 방·같은 시간 동시 INSERT 10건 중 1건만 성공함을 Testcontainers 테스트로 검증 (예약 API는 설문 반영 후 구현 중)
- 최대 2시간 · 하루 1건 · 7일 이내, 15분 노쇼 · 2주 내 2회 시 7일 제한 규칙을 **예약 상태 머신**으로 설계
- H2 대신 Testcontainers로 실제 PostgreSQL에서 제약까지 검증, CHANGELOG(v0.1.0 ~ v0.3.1)와 트러블슈팅 14건 문서화

---

## 🛠 Tech Stack

| 분야 | 기술 |
| --- | --- |
| **Backend** | ![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white) ![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white) ![JPA](https://img.shields.io/badge/Spring_Data_JPA-6DB33F?style=flat-square&logo=spring&logoColor=white) ![Node.js](https://img.shields.io/badge/Node.js_(Serverless)-339933?style=flat-square&logo=nodedotjs&logoColor=white) |
| **Database** | ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white) ![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white) |
| **Infra** | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![AWS EC2](https://img.shields.io/badge/AWS_EC2-FF9900?style=flat-square&logo=amazonec2&logoColor=white) ![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white) ![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white) |
| **AI** | ![Gemini](https://img.shields.io/badge/Gemini_API-8E75B2?style=flat-square&logo=googlegemini&logoColor=white) |
| **Frontend** | ![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB) ![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white) |
| **Test · Collab** | ![JUnit5](https://img.shields.io/badge/JUnit5-25A162?style=flat-square&logo=junit5&logoColor=white) ![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white) ![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white) ![Notion](https://img.shields.io/badge/Notion-000000?style=flat-square&logo=notion&logoColor=white) |

---

## 🏅 Certifications & Activities

| 구분 | 내용 |
| --- | --- |
| 자격증 | 정보처리기사 · SQLD · NCA (Naver Cloud Platform Certified Associate) |
| 언론 | 광주일보 인터뷰 — 대학가 가성비 맛집 지도 개발 |
| 리더십 | 컴퓨터공학과 학생회장 — 900명 규모 행사 총괄 |
| 프로젝트 리드 | 캡스톤 디자인 4인 팀 팀장 · 백엔드 리드 |

---

## 📬 Contact

프로젝트별 설계 근거와 트러블슈팅은 [**기술 블로그**](https://airforce836.tistory.com)와 [**노션 포트폴리오**](https://www.notion.so/af866e443fdc45cb8d58adf062166958?source=copy_link)에 정리해 두었습니다.
