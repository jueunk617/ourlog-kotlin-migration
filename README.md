# ✈️ OurLog (Kotlin Migration & Refactoring)
> **OurLog**는 영화·음악·책 등의 감상 기록을 아카이빙하고, 취향을 공유할 수 있는 **콘텐츠 다이어리 플랫폼**입니다.  
> 기존 Java 기반 프로젝트를 **Kotlin**으로 전면 **마이그레이션**하고, 코드 품질 및 배포 효율성을 개선한 프로젝트입니다. (2025.08.27 ~ 2025.09.03)  
> 
> 🔗 [**기존 프로젝트로 이동하기**](https://github.com/jueunk617/ourlog-java)

<br>

## 📚 목차

1. 👥 [팀 구성 및 역할](#-팀-구성-및-역할)  
2. 🧭 [프로젝트 목표](#-프로젝트-목표)  
3. 💾 [주요 기능](#-주요-기능)  
4. ⚙️ [기술 스택](#-기술-스택)  
5. 🚀 [배포 아키텍처](#-배포-아키텍처)  
6. 🌐 [Java to Kotlin 마이그레이션 전략](#-java-to-kotlin-마이그레이션-전략)  
7. 🏗️ [개선된 아키텍처](#-개선된-아키텍처)  
8. 🧠 [리팩토링 & 트러블슈팅](#-리팩토링--트러블슈팅)  
9. 🎯 [주요 결정 & 배운 점](#-주요-결정--배운-점)  

<br>

## 👥 팀 구성 및 역할
| 팀원 | 이름 | GitHub | 담당 기능 |
|:------:|:----:|:--------:|:-----------|
| <img src="https://avatars.githubusercontent.com/u/125340502?v=4" width="80px" style="border-radius:10px;"> | **김주은** | [@jueunk617](https://github.com/jueunk617) | • 감상일기 등록 / 수정 / 삭제<br>• 콘텐츠 조회 (영화, 음악)<br>• 배포 인프라 구축 |
| <img src="https://avatars.githubusercontent.com/u/84756980?v=4" width="80px" style="border-radius:10px;"> | **남기은** | [@namgigun](https://github.com/namgigun) | • 감상일기 조회<br>• 댓글 등록 / 조회 / 수정 / 삭제<br>• 콘텐츠 조회 (도서) |
| <img src="https://avatars.githubusercontent.com/u/127588192?v=4" width="80px" style="border-radius:10px;"> | **노희철** | [@Nohheechul](https://github.com/Nohheechul) | • 통계 카드 (감상 수, 평균 별점, 주요 감정)<br>• 최근 6개월 감상 그래프 / 콘텐츠 분포<br>• 타입·장르·감정·OTT별 그래프 |
| <img src="https://avatars.githubusercontent.com/u/68084426?v=4" width="80px" style="border-radius:10px;"> | **박영빈** | [@yeongbin1999](https://github.com/yeongbin1999) | • 회원가입 / 로그인 / 로그아웃<br>• 내 프로필 조회<br>• 무중단 CI/CD 구축 |
| <img src="https://avatars.githubusercontent.com/u/145415884?v=4" width="80px" style="border-radius:10px;"> | **임종현** | [@dlawhd](https://github.com/dlawhd) | • 타임라인<br>• 팔로우 / 언팔로우<br>• 다른 유저 프로필 조회<br>• 좋아요 기능 |

<br>

## 🧭 프로젝트 목표
1️⃣ **Java to Kotlin 100% 전환**

2️⃣ **CI/CD 무중단 배포 환경 구축**

3️⃣ **프론트 UI/UX 개선**

<br>

## 💾 주요 기능

https://github.com/user-attachments/assets/8ea6d2eb-387d-4d55-871a-cb9d873892c6

| 기능 | 설명 |
| --- | --- |
| **콘텐츠 검색** | TMDB, Spotify, 국립중앙도서관 API를 연동하여 영화, 음악, 책 검색 기능 제공 |
| **감상일기** | 콘텐츠 기반 감상일기 작성/수정/삭제 (공개/비공개, 평점, 태그, OTT 선택) |
| **통계 기능** | 월별 감상 수, 장르/태그/OTT 기반 통계 시각화 |
| **마이페이지** | 나의 감상일기 리스트, 수정/삭제 기능 제공 |
| **인증/인가** | JWT 기반 인증 + OAuth(Google, Kakao, Naver) 구현, 권한에 따라 접근 제한 |
| **배포/인프라** | Terraform으로 인프라 구축(IaC), Nginx + Docker + EC2 + RDS 환경에서 무중단 배포 |

<br>

## ⚙️ 기술 스택 

### Backend
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)
![SpringBoot](https://img.shields.io/badge/SpringBoot-6DB33F?style=for-the-badge&logo=SpringBoot&logoColor=white)
![Spring Data JPA](https://img.shields.io/badge/Spring_Data_JPA-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)
![QueryDSL](https://img.shields.io/badge/QueryDSL-47A447?style=for-the-badge&logoColor=white)

### Frontend
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=Next.js&logoColor=white)

### Database & Cache
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)

### Deployment & Infra
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)
![AWS EC2](https://img.shields.io/badge/AWS_EC2-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![AWS RDS](https://img.shields.io/badge/AWS_RDS-527FFF?style=for-the-badge&logo=amazonrds&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)

### Open API
<img src="https://img.shields.io/badge/TMDB-01D277?style=for-the-badge&logo=themoviedatabase&logoColor=white"/> <img src="https://img.shields.io/badge/Spotify-1DB954?style=for-the-badge&logo=spotify&logoColor=white"/> <img src="https://img.shields.io/badge/국립중앙도서관-A9A9A9?style=for-the-badge&logoColor=white"/> <img src="https://img.shields.io/badge/Naver-03C75A?style=for-the-badge&logo=naver&logoColor=white"/> <img src="https://img.shields.io/badge/Google-4285F4?style=for-the-badge&logo=google&logoColor=white"/> <img src="https://img.shields.io/badge/Kakao-FEE500?style=for-the-badge&logo=kakao&logoColor=black"/>

### 협업 
<img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/> <img src="https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white"/> <img src="https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white"/> <img src="https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=white"/>

<br>

## 🚀 배포 아키텍처

| 항목 | 도구 / 내용 |
| --- | --- |
| **프론트엔드** | Vercel |
| **백엔드** | AWS EC2 (t3.micro) + Docker + Spring Boot (Kotlin) |
| **데이터베이스** | AWS RDS (MySQL) |
| **인증서** | Let's Encrypt (Nginx 프록시 서버에서 HTTPS 인증) |
| **프록시** | Nginx (리버스 프록시, 무중단 배포, SSL 처리) |
| **CI/CD** | GitHub Actions (main 브랜치 push 시 자동 빌드 및 배포) |
| **캐시/세션** | Redis (Docker + EC2 내 구성) |
| **인프라 관리** | Terraform |

> 💡 배포 자동화와 IaC 환경 덕분에 인프라 관리 비용이 감소하고, 서비스 안정성이 크게 향상되었습니다.

<br>

## 🌐 Java to Kotlin 마이그레이션 전략
### ① Null 안전성 확보

  * **Before (Java):** `Optional<T>` 남용 및 방어적인 `if (obj != null)` 체크 반복.
  * **After (Kotlin):**
      * `Optional`을 모두 제거하고, Kotlin의 **Nullable Type (`T?`)** 로 명시적 처리 강제.
      * `?.let {}` (Null이 아닐 때 실행), `?:` (엘비스 연산자)를 사용해 간결하고 안전한 코드 구현.
      * `Spring Data JPA`의 `findById` 결과는 서비스 계층에서 즉시 `.orElseThrow()`로 예외를 발생시키거나 Kotlin 확장 함수로 처리함.

### ② 함수형 프로그래밍 도입

  * **Before (Java):** `for` 루프와 `Stream` API 혼용.
  * **After (Kotlin):**
      * Java `Stream`을 Kotlin의 네이티브 **컬렉션 함수** (`mapNotNull`, `associateBy`, `filter` 등)로 100% 대체하여 가독성 향상.
      * `Base64` 인코딩 등 유틸리티성 정적 메서드들은 **확장 함수**로 분리, 마치 해당 객체의 원래 메서드인 것처럼 사용 가능하게 함. (예: `"string".toBase64()`)

### ③ 보일러플레이트 코드 제거 

  * **Before (Java):** `@Getter`, `@Setter`, `@Builder` 등 Lombok 어노테이션에 의존.
  * **After (Kotlin):**
      * **Lombok을 100% 제거.**
      * 모든 DTO는 `data class`로 전환하여 `equals()`, `hashCode()`, `copy()` 등 자동 구현.
      * `var` (가변) 대신 **`val` (불변)을 기본**으로 사용, Side Effect 최소화 및 데이터 불변성 확보.


### ④ 마이그레이션 성과

| 기능 | Before (Java) | After (Kotlin) | 감소율 |
|------|--------------|----------------|--------|
| **다이어리 컨트롤러** | 70줄 | 56줄 | **20%** ↓ |
| **다이어리 서비스** | 136줄 | 107줄 | **21%** ↓ |
| **댓글 기능** | 118줄 | 67줄 | **43%** ↓ |
| **팔로우/언팔로우** | 197줄 | 135줄 | **31.5%** ↓ |
| **통계 리포지토리** | 352줄 | 313줄 | **11%** ↓ |
| **통계 서비스** | 190줄 | 128줄 | **33%** ↓ |

> 💡 data class, 확장 함수, 컬렉션 API 등을 적극 활용하여 보일러플레이트 코드를 제거한 결과입니다.

<br>

## 🏗️ 개선된 아키텍처
### 아키텍처의 흐름

1.  **서비스 (Service):** 비즈니스 로직에만 집중. 실패 시 `CustomException(ErrorCode)`를 `throw`.
2.  **컨트롤러 (Controller):** **'성공' 케이스만 가정**하고 서비스를 호출.
3.  **ControllerAdvice (전역):** `CustomException`을 전역에서 `catch`하여, 표준화된 **실패** 응답을 자동 생성.

### 공통 응답 및 확장 함수

```kotlin
// 모든 API 응답을 감싸는 공통 래퍼
data class RsData<T>(
    val resultCode: String,
    val code: String?,
    val msg: String,
    val data: T?
) { ... }

// [확장 함수] 컨트롤러에서 성공 시 호출
fun <T> T.toSuccessResponse(msg: String = "성공"): ResponseEntity<RsData<T>> =
    ResponseEntity.ok(RsData.success(msg, this))

// [확장 함수] ControllerAdvice에서 실패 시 호출
fun ErrorCode.toFailResponse(customMsg: String? = null): ResponseEntity<RsData<Nothing>> =
    ResponseEntity.status(this.status)
        .body(RsData.fail(this, customMsg))
```

### 적용 예시

```kotlin
// 1. ErrorCode 정의
enum class ErrorCode(val status: HttpStatus, val code: String, val message: String) {
    USER_NOT_FOUND(HttpStatus.NOT_FOUND, "U001", "사용자를 찾을 수 없습니다.")
}

// 2. 서비스 계층: 로직 실패 시 예외 Throw
@Service
class UserService(private val userRepository: UserRepository) {
    fun findById(id: Long): User {
        // 비즈니스 로직에 집중
        return userRepository.findById(id)
            .orElseThrow { CustomException(ErrorCode.USER_NOT_FOUND) }
    }
}

// 3. 컨트롤러 계층: 성공 응답만 처리
@RestController
class UserController(private val userService: UserService) {

    @GetMapping("/user/{id}")
    fun getUser(@PathVariable id: Long) =
        // try-catch가 전혀 없음.
        // 서비스가 성공적으로 User를 반환하면, .toSuccessResponse가 실행됨
        // 만약 서비스가 예외를 던지면, ControllerAdvice가 가로챔
        userService.findById(id).toSuccessResponse("사용자 조회 성공")
}
```

이 구조 덕분에 컨트롤러는 `try-catch`나 예외 상황을 고려할 필요 없이 비즈니스 로직 호출에만 집중 가능.

<br>

## 🧠 리팩토링 & 트러블슈팅

### 1️⃣ 외부 API 호출 재구성 

* 💥 **문제:** TMDB, Spotify 등 여러 외부 API 호출 로직이 서비스 곳곳에 흩어져 있었음. Kotlin `data class`를 Redis에 캐시할 때 `LinkedHashMap`으로 잘못 변환되는 직렬화 오류 발생.  
* 🔍 **원인:** Redis 캐시에 Kotlin 객체 직렬화 설정이 전역적으로 적용되지 않음.  
* ✅ **해결:**  
  1. **Facade 패턴:** `ContentSearchFacade`를 두어 외부 API 호출 창구 일원화  
  2. **전역 ObjectMapper:** `KotlinModule`, `JavaTimeModule`을 등록한 `ObjectMapper`를 `@Primary`로 지정, 애플리케이션 전역에서 동일 설정 사용  
  3. **캐시 관리:** `CacheVersionManager` 도입, DTO 변경으로 캐시 포맷 깨짐 시 자동 초기화

### 2️⃣ N+1 API 호출 최적화

* 💥 **문제:** 콘텐츠 목록 검색 시, 각 항목의 상세 정보(감독, 장르)를 얻기 위해 N+1 API 호출이 발생, 응답 속도 저하  
* 🔍 **원인:** 개별 API 호출 방식으로 요청 수 과다 발생  
* ✅ **해결:**  
  * **TMDB:** `append_to_response=credits` 파라미터로 1회 호출 시 영화 + 감독 정보 동시에 조회  
  * **Spotify:** 트랙 검색 후 아티스트 ID 수집 → `GET /v1/artists?ids=...` 1회 호출, 총 2회 호출로 장르 정보 매핑

### 3️⃣ 레거시 HTTP 클라이언트 및 동시성 제어

* 💥 **문제:** `RestTemplate` 사용 중, Spotify 액세스 토큰 갱신 시 여러 스레드가 동시에 갱신 시도  
* 🔍 **원인:** 동시성 제어 미흡  
* ✅ **해결:**  
  1. **WebClient 전환:** Non-Blocking 지원, 필요 시 `.block()` 사용  
  2. **동시성 제어:** `Double-Checked Locking` 적용 (`synchronized(tokenLock) { ... }`), 단일 스레드만 갱신

### 4️⃣ JPA N+1 쿼리 최적화 

* 💥 **문제:** 감상일기 목록 조회 시 `LazyInitializationException` 및 연관 엔티티 조회로 인한 N+1 쿼리 발생  
* 🔍 **원인:** To-One / To-Many 관계 엔티티 조회 전략 미설정  
* ✅ **해결:**  
  1. **To-One 관계:** `fetch join` (QueryDSL 활용)  
  2. **To-Many 관계:** Lazy 유지, `hibernate.default_batch_fetch_size=50` 설정 → IN 절 쿼리 1회로 최적화  
  3. **검증:** `DiaryListQueryCountTest` 작성, N+1 재발 방지

### 5️⃣ 도메인 책임 분리 및 트랜잭션 전파

* 💥 **문제:** `DiaryService`가 일기 저장뿐만 아니라, 태그/장르 생성 및 연관관계 매핑 등 과도한 책임  
* 🔍 **원인:** SRP 미준수, 트랜잭션 범위 불명확  
* ✅ **해결:**  
  1. **책임 분리:** `TagService`, `GenreService`로 연관관계 동기화 로직 이동, 메서드명 `syncXxx()` 사용  
  2. **트랜잭션 전파:** `@Transactional(propagation = Propagation.MANDATORY)` 적용, 부모 트랜잭션 내에서만 호출되도록 강제

<br>

## 🎯 주요 결정 & 배운 점
  * **Lesson 1 - 최적화보다 데이터 정확성이 우선이다.**

      * TMDB API 호출 횟수를 줄이기 위해 `append_to_response`를 사용했으나, 일부 영화의 장르/제작자 매핑 누락 케이스 발견. 무조건 적은 호출 수보다 데이터의 정확성이 더 중요하다고 판단, 정확성을 위해 추가 1회 조회를 감수하는 방향으로 일부 로직을 되돌림.

  * **Lesson 2 - 좋은 아키텍처는 코드를 단순하게 만든다.**

      * `RsData` 래퍼, `toSuccessResponse` / `toFailResponse` 확장 함수, `ControllerAdvice` 도입은 컨트롤러에서 성공 케이스만 다루게 하여 코드를 극도로 단순화시킴. 서비스 계층은 비즈니스 로직(예외 `throw`)에만 집중할 수 있게 됨.

  * **Lesson 3 - 도메인 서비스는 자신의 책임만진다 (SRP).**

      * `Diary` 수정 시 연관된 `Tag` 처리 로직을 `DiaryService`가 아닌 `TagService.syncTags()`로 분리함. 이를 통해 `Tag` 관련 로직(찾거나, 없으면 생성)은 `TagService`만 알도록 캡슐화되어 단일 책임 원칙 준수 및 유지보수성 향상.

  * **Lesson 4 - 인프라는 코드로 관리한다 (IaC).**

      * Terraform을 통해 AWS EC2, RDS, VPC, 보안 그룹 등 모든 인프라를 코드로 관리함. 이를 통해 동일 환경을 1분 내로 재생성하거나, 변경 이력을 `git`으로 관리 가능. 수동 설정으로 인한 휴먼 에러 원천 차단.
