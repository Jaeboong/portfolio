# 🏫 Campung: AI 기반 차세대 캠퍼스 커뮤니티

> 🚀 실시간 감정 분석, 위치 공유, AI 랜드마크 요약으로 캠퍼스 라이프를 혁신합니다.

<br/>

<br/>

## ✨ 주요 기능 (Key Features)

* **🤖 AI 기반 캠퍼스 감정 분석**: **OpenAI의 GPT-5**를 활용해 캠퍼스 내 게시글의 감정을 실시간으로 분석하고 '온도'와 '날씨'로 시각화하여 보여줍니다.
* **📍 실시간 위치 공유 및 주변 알림**: **Geohash**와 **WebSocket** 기술을 통해 친구와 실시간으로 위치를 공유하고, 주변의 새로운 소식을 즉시 알려주는 동적인 소셜 경험을 제공합니다.
* **🔥 HOT 게시글 시스템**: **Redis**의 실시간 캐싱을 활용하여 24시간 동안 가장 인기 있는 게시글을 동적으로 선정하고 보여줍니다.
* **🏢 AI 랜드마크 요약**: 캠퍼스 내 주요 건물이나 장소에 대한 게시글을 AI가 분석하고 요약하여, 방문하지 않고도 그곳의 분위기를 파악할 수 있습니다.
* **🔒 안전하고 편리한 소셜 기능**: **Spring Security**와 **FCM**을 기반으로 친구 관계, 실시간 채팅, 맞춤형 알림 등 안전하고 다채로운 소셜 기능을 제공합니다.
* **☁️ 안정적인 클라우드 인프라**: **AWS S3**를 통한 미디어 파일 관리, **Docker**와 **GitHub Actions**를 이용한 CI/CD 파이프라인 구축으로 안정적이고 효율적인 서비스 운영을 보장합니다.

---

## 🏗️ 아키텍처 (Architecture)

📦 Campung Fullstack Architecture
```
┌────────────────┐      ┌─────────────────┐      ┌─────────────┐
│ Android App    │◀──▶│   Spring Boot   │◀───▶│  MariaDB    │
│(Kotlin/Compose)│      │     Backend     │      │  (Main DB)   │
└────────────────┘      └─────────────────┘      └─────────────┘
▲                          │ ▲                      │
│ FCM Push                 │ │ REST API             │ Redis (Cache)
▼                          │ ▼                      ▼
┌──────────────┐      ┌───────────────┐      ┌─────────────┐
│ Firebase FCM │◀──▶│     AWS S3    │      │ OpenAI GPT-5│
│ (알림 시스템) │      │ (미디어 저장소)│      │ (AI 분석)   │
└──────────────┘      └───────────────┘      └─────────────┘
```
---

## 🛠️ 기술 스택 (Tech Stack)

### **Backend**

* **Framework**: Spring Boot 3.x, Spring Security
* **Language**: Java 17
* **Database**: MariaDB, Redis 7.x
* **AI**: OpenAI GPT-5 API
* **Cloud Infra**: AWS S3, Firebase Cloud Messaging (FCM)
* **Real-time**: WebSocket
* **ORM**: JPA/Hibernate with QueryDSL
* **API Documentation**: Swagger/OpenAPI 3.0
* **Build & Deploy**: Gradle, Docker Compose, GitHub Actions CI/CD

### **Android**

* **Language**: Kotlin
* **UI**: Jetpack Compose
* **Architecture**: MVVM (Model-View-ViewModel), Hilt (DI)
* **Async**: Coroutines, Flow
* **Networking**: Retrofit2, OkHttp3
* **Database**: Room
* **Map**: Naver Maps SDK
* **Real-time**: WebSocket, FCM

---

## 🔥 핵심 기능 상세 (Core Feature Details)

### **1. AI 기반 캠퍼스 감정 분석 시스템**

> 캠퍼스의 실시간 감정 상태를 '온도'와 '날씨'로 측정하는 세계 최초의 시스템

**동작 원리**
1.  **데이터 수집**: `EmotionAnalysisScheduler`가 매시간 정각, 최근 1시간 동안 작성된 모든 게시글을 수집합니다.
2.  **AI 감정 분석**: 수집된 텍스트를 `EmotionPromptBuilder`로 가공하여 **GPT-5 API**에 전송, 6가지 감정(우울함, 밝음, 신남, 화남, 슬픔, 흥분) 점수를 추출합니다.
3.  **온도 및 날씨 변환**: `EmotionCalculatorService`가 감정 점수를 통계 처리하여 '감정 날씨'를 결정하고, `CampusTemperatureManager`는 사용자 활동량까지 종합하여 '캠퍼스 온도'를 계산합니다.

```java
// 감정 분석 파이프라인 예시
// 텍스트 → GPT-5 분석 → 6차원 감정 점수 → 온도 변환 → 날씨 매핑
// EmotionAnalysisService -> E
