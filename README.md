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

<img width="4270" height="2235" alt="Image" src="https://github.com/user-attachments/assets/125c48a7-a490-4d62-ac28-369c0b78e4b6" />

### [🇺🇸 English]
**Seoul Mate** is a comprehensive platform designed to help foreigners and locals create location-based meetups and generate AI-driven, customized tour courses in Seoul. Developed as a 5-member team project, it features a modern Android client built with Jetpack Compose, a robust REST API powered by Spring Boot, and an intelligent AI server utilizing FastAPI.

### [🇰🇷 Korean]
**Seoul Mate**는 서울을 방문하는 외국인과 내국인이 함께 지역 기반의 모임을 만들고, AI를 활용해 맞춤형 서울 여행 코스를 생성할 수 있는 플랫폼입니다. 5인의 팀 프로젝트로 진행되었으며, 최신 Android UI 툴킷인 Jetpack Compose와 Spring Boot 기반의 안정적인 REST API, 그리고 FastAPI 기반의 AI 서버를 유기적으로 연동하여 구축되었습니다.

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

## 🧑‍💻 My Contributions(담당 역할 및 기여)

> **Role:** Full-Stack Developer & DevOps  
> **Key Focus:** 분산 환경 아키텍처 설계, AI 마이크로서비스 연동, 클라이언트-서버 간 통신 및 모니터링 파이프라인 구축


### [🇺🇸 English]

### 1. Logging & Monitoring
- Implemented request tracing using `X-Trace-Id` across Android → Spring Boot → FastAPI
- Configured centralized logging and metrics with Grafana, Loki, and Prometheus
- Set up alert notifications using Discord Webhook
- Filtered unnecessary logs (e.g., health check) to reduce storage usage

---

### 2. AI Service Integration (FastAPI)
- Developed a separate FastAPI service for AI-based course recommendation
- Integrated OpenAI API for generating travel courses
- Structured responses using Pydantic models for consistent API output
- Composed prompts using user input and external data

---

### 3. Backend (Spring Boot)
- Implemented scheduled batch processing for public data updates
- Developed Firebase JWT authentication filter
- Applied API rate limiting using interceptor-based logic

---

### 4. Android Client
- Set up MVVM architecture and introduced Hilt for dependency injection
- Implemented network layer using Retrofit and OkHttp Interceptor
- Added handling for server errors (Timeout, 401, 429)
- Implemented internationalization (i18n)
- Developed login and signup flow

---
### [🇰🇷 Korean]

### 1. 로깅 및 모니터링
- Android → Spring Boot → FastAPI 간 요청 추적을 위한 `X-Trace-Id` 적용
- Grafana, Loki, Prometheus 기반 로그 및 메트릭 수집 환경 구성
- Discord Webhook 알림 설정
- 헬스체크 로그 등 불필요 로그 필터링 적용

---

### 2. AI 서비스 연동 (FastAPI)
- AI 추천 기능을 별도 FastAPI 서비스로 분리 구현
- OpenAI API 연동
- Pydantic 기반 구조화된 응답 처리
- 사용자 입력 및 외부 데이터를 활용한 프롬프트 구성

---

### 3. 백엔드 (Spring Boot)
- 공공데이터 배치 처리 (Scheduler 기반)
- Firebase JWT 인증 필터 구현
- API 호출 제한 로직 적용

---

### 4. Android 클라이언트
- MVVM 아키텍처 적용 및 Hilt 도입
- Retrofit + OkHttp 기반 네트워크 구성
- Timeout, 401, 429 에러 처리
- 다국어(i18n) 적용
- 로그인/회원가입 기능 구현

---
- @gitsuhyeon — AI (FastAPI), Full-Stack
- @hyw1222 — Backend (Spring Boot)
- @faithjua — Frontend (Android)
- ISC — Design
- JHP — Planning


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
- The backend server is currently deployed on AWS for internal testing (alpha stage).
- Due to security reasons, the deployment endpoint is not publicly shared.

## 🌐 Deployment (배포 이미지)

서비스의 안정성과 비용 효율성을 고려하여 하이브리드 클라우드 아키텍처를 구축했습니다.

* **Backend API (Spring Boot):** 
  * AWS 프리티어 환경에서 가용 메모리 최적화를 위해 Grafana Cloud로 로그를 외부 적재하도록 설계.
    <img width="370" height="688" alt="Image" src="https://github.com/user-attachments/assets/a7333cb3-d584-4b77-925e-78cb66003af3" />
* **AI Microservice (FastAPI):** 
  * render로 배포하여 Cold Start 있음, 인스턴스 활성화를 통해 응답 지연 최소화 관리.
    <img width="1422" height="697" alt="Image" src="https://github.com/user-attachments/assets/55478873-0c9d-4462-b926-5ec782e14ad8" />
* **Grafana Monitoring (with prometheus+loki):**
  * 로그 모니터링 진행중. discord와 연동해 에러 발생시 알림 발생.
    <img width="1422" height="722" alt="Image" src="https://github.com/user-attachments/assets/7c00fad1-eae4-463e-933f-f8623a39b041" />     
