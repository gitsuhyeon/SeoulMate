# 🗺️ Seoul Mate (서울 메이트)

> **K-뷰티·덕질·탐방·클래스, 모두 동네의 서울 메이트와 함께!** > Seoul Foreigner Life & Local Tour Information App

<p align="center">
  <img src="https://img.shields.io/badge/Android-3DDC84?style=flat-square&logo=android&logoColor=white"/>
  <img src="https://img.shields.io/badge/Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jetpack_Compose-4285F4?style=flat-square&logo=jetpackcompose&logoColor=white"/>
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white"/>
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white"/>
  <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/AWS_EC2-FF9900?style=flat-square&logo=amazonec2&logoColor=white"/>
</p>

---

## 📖 Project Overview (프로젝트 소개)

### [🇰🇷 Korean]
**Seoul Mate**는 서울을 방문하는 외국인과 내국인이 함께 지역 기반의 모임을 만들고, AI를 활용해 맞춤형 서울 여행 코스를 생성할 수 있는 플랫폼입니다. 5인의 팀 프로젝트로 진행되었으며, 최신 Android UI 툴킷인 Jetpack Compose와 Spring Boot 기반의 안정적인 REST API, 그리고 FastAPI 기반의 AI 서버를 유기적으로 연동하여 구축되었습니다.

### [🇺🇸 English]
**Seoul Mate** is a comprehensive platform designed to help foreigners and locals create location-based meetups and generate AI-driven, customized tour courses in Seoul. Developed as a 5-member team project, it features a modern Android client built with Jetpack Compose, a robust REST API powered by Spring Boot, and an intelligent AI server utilizing FastAPI.

---

## ✨ Key Features (주요 기능)

* **🔐 Secure Authentication (안전한 인증)**
  * Firebase 기반의 Google OAuth 간편 로그인
  * JWT (Firebase ID Token) 기반의 Stateless Spring Security 인증 인프라
* **🤖 AI Course Generator (AI 기반 맞춤형 코스 생성)**
  * 사용자의 프롬프트(일정, 예산, 테마)를 분석하여 최적의 동선 추천 (FastAPI + LangChain)
  * AI가 추천한 코스를 드래그 & 화살표로 자유롭게 순서 변경 및 커스터마이징 가능
* **📍 Interactive Local Maps (반응형 로컬 지도)**
  * Naver Map SDK를 활용한 직관적인 위치 검색 및 렌더링
* **💰 Good Price Store Integration (착한가격업소 공공데이터 연동)**
  * 서울시 공공데이터 API를 활용한 식당/서비스 정보 제공
  * Spring Scheduler를 통한 매월 1일 새벽 대규모 데이터 자동 배치(Batch) 업데이트

---

## 🏗 Architecture & Tech Stack (기술 스택)

### 📱 Client (Android)
* **UI:** Jetpack Compose, Material Design 3
* **Architecture:** MVVM (Model-View-ViewModel), Clean Architecture Concepts
* **Network/DI:** Retrofit2, OkHttp3, Dagger Hilt
* **Async/Concurrency:** Kotlin Coroutines, Flow, StateFlow
* **Map & Auth:** Naver Map SDK, Firebase Authentication (Google Id Token)

### ⚙️ Backend (Spring Boot)
* **Framework:** Java 17, Spring Boot 3.x
* **Security:** Spring Security, Firebase Admin SDK (Custom Token Filter)
* **Database & ORM:** PostgreSQL (Production), H2 (Local), Spring Data JPA
* **API Docs:** Springdoc OpenAPI (Swagger UI)

### 🧠 AI Server (Python)
* **Framework:** FastAPI
* **AI Core:** LangChain, LangGraph

### 🚀 DevOps & Infrastructure
* **CI/CD:** GitHub Actions (Automated build and deployment)
* **Containerization:** Docker, Docker Compose
* **Cloud:** AWS EC2 (Spring Boot), Render (FastAPI)

---

## 🧑‍💻 담당 역할 및 기여 (My Contributions)

> **Role:** Full-Stack Developer & DevOps  
> **Key Focus:** 분산 환경 아키텍처 설계, AI 마이크로서비스 연동, 클라이언트-서버 간 통신 및 모니터링 파이프라인 구축

### 1. 분산 추적 및 인프라 모니터링 (DevOps & Logging)
* **분산 환경 Trace-ID 구축:** 클라이언트(Android)부터 Spring Boot, FastAPI까지 이어지는 다중 서버 환경에서 요청 흐름을 추적하기 위해 커스텀 `MdcFilter` 구현. HTTP 헤더에 `X-Trace-Id`를 주입하여 트러블슈팅 시간을 획기적으로 단축.
* **실시간 모니터링 관제탑(PLG 스택):** Grafana Cloud, Loki, Promtail, Prometheus를 연동하여 서버 메트릭 및 로그 중앙화. 장애 발생 시 Discord Webhook을 통한 실시간 알림 파이프라인 구축.
* **클라우드 스토리지 비용 방어:** Promtail의 `pipeline_stages`를 튜닝하여 헬스체크(Actuator) 등 불필요한 로그를 정규식으로 필터링(Drop)함으로써 로그 스토리지 비용 최적화.


### 2. AI 마이크로서비스 및 프롬프트 엔지니어링 (FastAPI & AI)
* **독립적 AI 추천 엔진 구축:** LangChain과 OpenAI(gpt-4o-mini)를 활용하여 사용자의 여행 코스를 생성하는 FastAPI 마이크로서비스 분리 개발.
* **데이터 기반 프롬프트 엔지니어링(RAG):** 사용자의 입력(예산, 인원)과 백엔드의 외부 데이터(착한 가격업소 정보, 실시간 혼잡도)를 프롬프트에 동적으로 주입하여 환각 현상(Hallucination)을 줄이고 쾌적한 코스를 추천하도록 최적화.
* **안정적인 구조화 응답(Structured Output):** Pydantic 모델을 활용하여 AI의 응답을 클라이언트가 즉시 렌더링할 수 있는 규격화된 JSON 형태(`CourseResponse`, `Place`)로 강제 변환 처리.

### 3. 백엔드 아키텍처 및 보안 (Spring Boot)
* **데이터 배치(Batch) 자동화:** '착한 가격업소' 공공데이터를 매월 1일 새벽 3시에 Spring Scheduler를 통해 자동 업데이트하도록 설계. 지역명 기반 동적 프롬프트 매핑을 위한 데이터 정제 및 카테고리화 적용.
* **Stateless 인증 필터 구현:** Firebase Admin SDK를 활용한 `FirebaseTokenFilter`를 직접 구현하여 JWT 검증 및 SecurityContext 인증 처리. 만료된 토큰에 대한 커스텀 401 예외 처리로 클라이언트 사용성 증대.
* **API Rate Limiting (호출 제한):** 과도한 AI API 과금을 방지하기 위해 Bucket4j와 HandlerInterceptor를 도입하여 일일 호출 횟수 제한 로직 적용. 개발자 프리패스(Bypass) 로직을 병행하여 운영 안정성 확보.

### 4. 프론트엔드 아키텍처 및 UI/UX (Android)
* **클라이언트 아키텍처 제안:** MVVM 패턴과 Dagger Hilt(DI) 도입을 팀 내에 제안하고 초기 아키텍처를 세팅.
* **NetworkModule 설계:** Retrofit 기반의 REST API 통신 모듈을 구축하고, 모든 API 요청에 자동으로 `X-Trace-Id`와 인증 토큰이 포함되도록 OkHttp Interceptor 구현.
* **탄력적인 클라이언트 에러 핸들링:** AI 서버의 응답 지연(Timeout), 429(Too Many Requests), 401(Unauthorized) 등 예외 상황을 ViewModel과 Kotlin Flow를 활용해 캐치하여 직관적인 팝업/토스트로 처리.
* **글로벌 서비스 대응(i18n):** Locale 설정을 적용하여 사용자의 국적 선택에 따라 UI 언어가 동적으로 변경되도록 다국어 처리 구현. 
* **회원가입/로그인 화면 구현:** 회원가입 및 로그인 흐름(UI/API) End-to-End 완성.
---

## 🛠 Getting Started (실행 방법)

### Prerequisites (사전 준비)
* Android Studio (Latest Version)
* JDK 17+
* Firebase Project Configuration (`google-services.json` needed in `app/` directory)
* Naver Map Client ID
* Seoul Public Data API Key

### 1. Android Setup
1. Clone the repository: `git clone [repository-url]`
2. Open the project in Android Studio.
3. Create `local.properties` in the root directory and add the following:
   ```properties
   BASE_URL="[http://10.0.2.2:8080/](http://10.0.2.2:8080/)" # Or your actual backend IP
4. Build and run on an Emulator or physical device.

### 2. Spring Boot Setup
1. Navigate to the backend directory.
2. The project uses profiles to manage environments. For local testing, use the local profile.
3. Configure the application-local.yml with your H2 DB settings.
4. Run the Application.

## 🌐 Deployment (배포 이미지)

서비스의 안정성과 비용 효율성을 고려하여 하이브리드 클라우드 아키텍처를 구축했습니다.

* **Backend API (Spring Boot):** 
  * AWS 프리티어 환경에서 가용 메모리 최적화를 위해 Grafana Cloud로 로그를 외부 적재하도록 설계.
    <img width="370" height="688" alt="Image" src="https://github.com/user-attachments/assets/b0624447-8c6e-4098-b10c-639ebff668f3" />
* **AI Microservice (FastAPI):** 
  * render로 배포하여 Cold Start 있음, 인스턴스 활성화를 통해 응답 지연 최소화 관리.
    <img width="1422" height="697" alt="Image" src="https://github.com/user-attachments/assets/55478873-0c9d-4462-b926-5ec782e14ad8" />
* **Grafana Monitoring (with prometheus+loki):**
  * 로그 모니터링 진행중. discord와 연동해 에러 발생시 알림 발생.
    <img width="1422" height="722" alt="Image" src="https://github.com/user-attachments/assets/7c00fad1-eae4-463e-933f-f8623a39b041" />     
