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
