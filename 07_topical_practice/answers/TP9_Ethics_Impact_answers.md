# TP9: Ethics & Impact of Computing — 해설집

> **CED 2025-26 토픽**: 3.2 Impact of Program Design
> **답안 분포**: A:2 / B:2 / C:1 / D:1

---

## 정답 요약

| # | 정답 | CED 토픽 | 핵심 |
|---|------|---------|------|
| 1 | **A** 다양한 조건 테스트 | 3.2.A.1 reliability | "variety of conditions" |
| 2 | **D** Unintended harmful effect | 3.2.A.2 부작용 | misinformation 예시 |
| 3 | **B** Permission + purchase | 3.2.A.3 Closed source | 비-오픈소스 사용법 |
| 4 | **C** 다양한 입력 테스트 | 3.2.A.1 reliability | edge case |
| 5 | **A** Beneficial impact | 3.2.A.2 유익한 영향 | 교통 앱 예 |
| 6 | **B** Harmful impact beyond intended use | 3.2.A.2 부작용 | 위치 데이터 판매 |

---

## Section I: 문제별 상세 해설

---

### Q1. 정답: **(A) 다양한 조건으로 테스트**

📌 **출제 의도:** **System Reliability(시스템 안정성)** 의 핵심 원리 — "variety of conditions" 테스트. CED 3.2.A.1의 가장 직접적 적용.

📎 **연계:** **CED 3.2.A.1**: *"System reliability refers to the program being able to perform its tasks as expected under stated conditions without failure. Programmers should make an effort to maximize system reliability by testing the program with a variety of conditions."*

> **핵심 개념: System Reliability**
> - 정의: 프로그램이 명시된 조건에서 **실패 없이 기대된 작업 수행**
> - 핵심 전략: **다양한 조건**으로 테스트
> - 일반적인 입력 + edge case (0, 음수, 매우 큰 값, null, 빈 입력 등)
> - 발견된 버그는 수정 후 재테스트

> **선행 지식:**
> - 테스트 케이스 = (입력, 기대 출력) 쌍
> - Edge case = 경계값 또는 극단적 입력
> - 좋은 테스트 = 정상 + 비정상 + 경계 모두 커버

**옵션별 분석:**

| 보기 | 분석 |
|---|---|
| **(A) 다양한 조건 테스트** ✅ | CED 3.2.A.1과 정확히 일치 — "variety of conditions" |
| (B) 문서화 후 그대로 배포 | 안정성 향상 안 됨, 사용자에게 피해 |
| (C) 기능 비활성화 | 임시 회피, 근본 해결 아님 |
| (D) 임의 지연 추가 | 버그와 무관한 변경, 안정성 향상 안 됨 |

> ⚠️ **함정 1:** **"테스트 = 모든 조건"** 잘못된 추론. 실제로는 **다양한 조건**(variety) — 대표적인 정상/비정상/경계 케이스. 모든 가능한 조합은 불가능.

> ⚠️ **함정 2:** **회피책 vs 해결책**. 기능 비활성화(C)는 회피, 다양한 테스트로 버그 식별/수정이 해결.

> ⚠️ **함정 3:** **CED 3.2.A.1 인용의 "make an effort"**. 완벽한 안정성은 어렵지만 노력은 필요 — 다양한 조건 테스트가 최선.

> 💡 **꿀팁 1:** **테스트 케이스 종류**:
> - **Normal**: 일반적 입력 (송금 100원)
> - **Boundary**: 경계값 (0, MAX_VALUE, 빈 배열)
> - **Invalid**: 잘못된 입력 (음수 송금, null)
> - **Stress**: 극단적 입력 (매우 큰 데이터)

> 💡 **꿀팁 2:** **AP에서 reliability 출제 패턴**: "어떻게 안정성을 향상시키는가?" → "다양한 조건으로 테스트" 답.

> 💡 **꿀팁 3:** **precondition 관계 (CED 1.8)**: precondition 명시로 "어떤 조건에서 동작 보장"을 명확히 → 그 조건들을 모두 테스트.

---

### Q2. 정답: **(D) Unintended harmful effect beyond intended use**

📌 **출제 의도:** **본래 의도와 다른 부작용**의 정확한 분류. CED 3.2.A.2의 핵심 개념 — "unintended harmful effects beyond their intended use" 적용.

📎 **연계:** **CED 3.2.A.2**: *"Programs meant to fill a need or solve a problem can have unintended harmful effects beyond their intended use."*

> **핵심 개념: Unintended Harmful Effect**
> - 프로그램은 **의도된 목적**을 위해 만들어짐 (예: 친구 연결)
> - 일부 사용자가 **다른 용도로 악용** 가능 (예: 거짓 정보 확산)
> - 개발자가 의도하지 않은 결과 → "unintended"
> - 사회에 부정적 영향 → "harmful"

> **선행 지식:**
> - "Beneficial" (유익한) vs "Harmful" (해로운) 영향 모두 가능
> - "Intended" (의도된) vs "Unintended" (의도하지 않은) 구별
> - 본 문제 = unintended + harmful 조합

**옵션별 분석:**

| 보기 | 분석 |
|---|---|
| (A) System reliability failure | 시스템이 작동을 멈춘 것이 아니라, **정상 작동하나 악용**됨 |
| (B) Intellectual property violation | 저작권/IP 문제와 무관 |
| (C) Open source license violation | 라이선스 위반 아님 |
| **(D) Unintended harmful effect** ✅ | CED 3.2.A.2 정확히 일치 |

> ⚠️ **함정 1:** **시스템 작동 vs 부작용 구별**. 앱이 "고장난" 게 아니라 "정상 작동하지만 부정적 영향" → reliability 아님.

> ⚠️ **함정 2:** **현실 사례 인지**. AP에서 종종 실제 이슈(가짜 뉴스, 사이버 따돌림 등)를 예시로 출제. 개념 적용 능력 평가.

> ⚠️ **함정 3:** **"intended" 정의**. 의도된 사용 = 개발자가 원래 설계한 용도. 사용자가 다른 용도로 쓰면 unintended.

> 💡 **꿀팁 1:** **CED 3.2.A.2 키워드**: "beneficial vs harmful", "intended vs unintended". 4개 조합 모두 가능.

> 💡 **꿀팁 2:** **AP 5.A skill**: "Explain how computing impacts society, economy, and culture." — 이런 개념 문제 단골.

> 💡 **꿀팁 3:** **현실 예시 자주 출제**:
> - 소셜 미디어 → 가짜 뉴스 (unintended harmful)
> - 위치 추적 → 프라이버시 침해 (unintended harmful)
> - 인공지능 → 자동화된 차별 (unintended harmful)

---

### Q3. 정답: **(B) 원작자의 허락을 받고 종종 구매**

📌 **출제 의도:** **Open source vs Closed source의 구별** — closed source는 권한 + 종종 구매 필요. CED 3.2.A.3 정확한 이해.

📎 **연계:** **CED 3.2.A.3**: *"Programmers often reuse code written by others and published as open source and free to use. Incorporation of code that is not published as open source requires the programmer to obtain permission and often purchase the code before integrating it into their program."*

> **핵심 개념: Open Source vs Closed Source**
> - **Open source**: 자유롭게 사용 가능 (라이선스 조건 따름)
> - **Closed source (proprietary)**: **허락 + 종종 구매** 필요
> - 무단 사용 = 저작권/IP 위반
> - "permission" 첫째, "purchase" 둘째 (often)

> **선행 지식:**
> - 저작권: 창작과 동시에 자동 부여 (등록 불필요)
> - 오픈소스 라이선스: 다양한 형태 존재 (조건마다 다름)
> - 상업용 라이브러리: 라이선스 비용 발생 (CED 3.2.A.3)

**옵션별 분석:**

| 보기 | 분석 |
|---|---|
| (A) 자유롭게 사용 | closed source는 자유 사용 불가 |
| **(B) 허락 + 종종 구매** ✅ | CED 3.2.A.3 정확히 일치 |
| (C) 크레딧만 표시 | 그것만으론 부족, 권한 필요 |
| (D) 저작권 만료 대기 | 무기한 대기는 비현실적이며 합법적 사용 방법 아님 |

> ⚠️ **함정 1:** **"open source"의 의미 혼동**. open source ≠ "공짜로 모든 것 가능". 라이선스 조건 (GPL은 파생물도 GPL 등) 따라야.

> ⚠️ **함정 2:** **"종종(often)" 키워드**. 모든 closed source가 유료는 아님 — 무료지만 허가 필요한 경우도. 그러나 "often purchase" 표현 정확.

> ⚠️ **함정 3:** **크레딧만으로 부족**. Attribution(출처 표시)은 일부 라이선스 요구사항이지 자동 권리 아님.

> 💡 **꿀팁 1:** **AP에서 IP 출제 패턴**:
> - "open source = free" 알고
> - "closed = permission/purchase" 알고
> - "copyright = automatic protection" 알고

> 💡 **꿀팁 2:** **현실 예시**:
> - 오픈소스: Linux, Java SDK, Apache HTTP, Junit
> - 클로즈드: Microsoft Office, Adobe Photoshop, 게임 엔진 (일부)

> 💡 **꿀팁 3:** **윤리적 측면**: 무단 사용은 단순 법적 문제 + **개발자 노력에 대한 존중 부족**. AP는 윤리 + 법적 측면 함께 강조.

---

### Q4. 정답: **(C) 다양한 입력으로 테스트**

📌 **출제 의도:** **Q1의 변형** — 구체적 시나리오 (sqrt 프로그램)로 reliability 원칙 적용. "variety of conditions"의 실제 의미 이해.

📎 **연계:** **CED 3.2.A.1** + **CED 1.8** Documentation (preconditions로 테스트 범위 정의).

> **핵심 개념: 좋은 테스트의 4가지 종류**
> 1. **Normal**: 일반 케이스 (sqrt(4) = 2.0)
> 2. **Boundary**: 경계값 (sqrt(0) = 0.0, sqrt(MAX_VALUE))
> 3. **Special**: 특이 케이스 (sqrt(1) = 1.0)
> 4. **Invalid**: 잘못된 입력 (sqrt(-1) → NaN)

> **선행 지식:**
> - sqrt: 음수에 대해 NaN 반환 (Math.sqrt 동작)
> - 0의 sqrt = 0
> - 1의 sqrt = 1 (특이값)
> - 매우 큰 수도 처리 가능 (overflow 위험은 적음 — double 범위 큼)

**옵션별 분석:**

| 보기 | 분석 |
|---|---|
| (A) 양의 정수만 | 다양성 부족 — 음수, 0, 매우 큰 수 누락 |
| (B) 자주 쓰는 숫자만 | "favorite numbers" — 비논리적 |
| **(C) 다양한 입력** ✅ | CED 3.2.A.1 "variety of conditions" |
| (D) 개발자 선호 숫자만 | 검증 불충분 |

> ⚠️ **함정 1:** **"variety = 모든 가능한 입력"** 잘못된 추론. 실제로는 **대표적인 다양한 케이스** — 모든 입력은 불가능 (예: int 범위 약 43억 개).

> ⚠️ **함정 2:** **음수 sqrt 처리**. Java Math.sqrt는 음수 시 NaN 반환 (예외 없음). 테스트로 발견되어야 함.

> ⚠️ **함정 3:** **매우 작은/큰 수**. 0.0001, 1e10 같은 극단 값도 테스트 가치 있음 (정밀도 문제).

> 💡 **꿀팁 1:** **테스트 케이스 설계 가이드**:
> - 입력 도메인을 **여러 카테고리**로 나누기
> - 각 카테고리에서 1~2 케이스 선택
> - Boundary는 반드시 포함

> 💡 **꿀팁 2:** **TDD (Test-Driven Development)** 개념: 테스트 먼저 작성 → 코드 작성 → 통과 확인. AP 범위 외이지만 테스트 중요성 강조.

> 💡 **꿀팁 3:** **AP FRQ 사고 방식**: 코드 작성 후 "어떤 입력이 잘못된 결과를 줄까?" 자문. 예: 빈 ArrayList, null, 경계값.

---

### Q5. 정답: **(A) 사회·경제에 유익한 영향**

📌 **출제 의도:** **Beneficial impact**의 식별 — 프로그램이 사회/경제/문화에 긍정적 영향을 미치는 사례. CED 3.2.A.2의 균형있는 측면 이해.

📎 **연계:** **CED 3.2.A.2**: *"These impacts can be both beneficial and harmful."* — 두 측면 모두 출제 가능. 본 문제는 beneficial.

> **핵심 개념: Beneficial Impact 예시**
> - **시간 절약**: 교통 앱, 검색 엔진
> - **연결성 향상**: 화상 회의, 메신저
> - **접근성**: 음성 인식, 번역
> - **효율성**: 자동화, 데이터 분석

> **선행 지식:**
> - "Beneficial"의 사회적 가치 — 자원 절약, 삶의 질 향상
> - 경제적 이익 — 비용 절감, 새 시장 창출
> - 문화적 영향 — 정보 접근성, 표현 다양화

**옵션별 분석:**

| 보기 | 분석 |
|---|---|
| **(A) 사회·경제 유익한 영향** ✅ | 교통 효율성, 시간 절약 명확한 beneficial |
| (B) 의도하지 않은 유해한 부작용 | 본 시나리오는 의도된 유익 |
| (C) 지적 재산권 침해 | IP와 무관 |
| (D) 시스템 안정성 실패 | 앱은 정상 작동 |

> ⚠️ **함정 1:** **모든 앱이 부정적이라는 편향**. CED는 **균형** 강조 — 컴퓨팅은 양면성.

> ⚠️ **함정 2:** **의도된 vs 부작용**. 본 시나리오는 **의도된 유익** — 교통 예측이 본래 목적. 부작용 (운전자 데이터 추적 등)은 별개.

> ⚠️ **함정 3:** **"economy"의 의미**. 시간 절약 = 생산성 증가 = 경제적 이익. 직접 돈만 의미하지 않음.

> 💡 **꿀팁 1:** **CED 3.2.A.2 균형 이해**: 항상 "beneficial vs harmful" 양면. AP는 둘 다 출제.

> 💡 **꿀팁 2:** **AP 5.A skill**: 컴퓨팅의 사회/경제/문화 영향 설명. 다양한 예시 알면 좋음.

> 💡 **꿀팁 3:** **간단한 분류법**:
> - 사회: 사람 간 관계, 공공 생활
> - 경제: 비용, 효율, 시장
> - 문화: 표현, 가치관, 라이프스타일

---

### Q6. 정답: **(B) 본래 의도된 용도를 넘어선 유해한 영향**

📌 **출제 의도:** **Privacy 침해를 unintended harmful effect로 분류** — 위치 데이터 수집(의도)과 광고주 판매(의도 외)의 구별. CED 3.2.A.2의 깊은 이해.

📎 **연계:** **CED 3.2.A.2**: *"Programs meant to fill a need or solve a problem can have unintended harmful effects beyond their intended use."* — 본 시나리오 = 의도된 용도(예보) + 의도 외 유해(데이터 판매).

> **핵심 개념: Privacy as Harmful Impact**
> - 데이터 수집 = 본래 목적 (예보)
> - 데이터 판매 = **본래 의도 외 사용**
> - 사용자 동의 없는 사용 = **harmful** (privacy 침해)
> - 결과: 신뢰 상실, 잠재적 피해 (스토킹, 차별 등)

> **선행 지식:**
> - 의도된 용도 = 사용자가 동의한 사용
> - 의도 외 사용 = 사용자가 인지하지 못한/동의하지 않은 사용
> - 개인 정보 보호 관련 법적 보호 체계 존재 (AP 출제 범위 외 — CED 3.2는 개념만 다룸)

**옵션별 분석:**

| 보기 | 분석 |
|---|---|
| (A) 시스템 안정성 실패 | 앱은 정상 작동, 안정성 문제 아님 |
| **(B) 의도 외 유해한 영향** ✅ | CED 3.2.A.2 정확 — 본래 목적(예보)을 넘은 부작용 |
| (C) 지적 재산권 침해 | IP 문제 아님 (사용자 데이터, 코드 아님) |
| (D) 의도하지 않은 유익한 효과 | "유익"이 아닌 "유해" |

> ⚠️ **함정 1:** **사용자 동의의 중요성**. 동의가 있으면 "intended use"로 분류 가능. 본 문제는 명시적 동의 없음 → unintended.

> ⚠️ **함정 2:** **데이터 ≠ IP**. 사용자 데이터의 무단 사용은 IP 위반이 아니라 privacy 침해 (CED 3.2.A.2).

> ⚠️ **함정 3:** **앱 자체는 정상 작동**. reliability 실패 아님. 정상 작동하지만 데이터 사용 방식이 문제.

> 💡 **꿀팁 1:** **Privacy 관련 출제 패턴**:
> - 위치 추적
> - 검색 기록 수집
> - 음성 인식 데이터
> - 의료 정보
> - 모두 unintended harmful로 분류 가능

> 💡 **꿀팁 2:** **균형 인식**: 데이터 수집 자체가 항상 나쁜 것 X. 의료 연구, 통계 분석 등 beneficial 측면도. **사용 목적 + 동의** 가 핵심.

> 💡 **꿀팁 3:** **AP에서 윤리 출제 시 키워드**:
> - "without explicit consent" → 의도 외 harmful
> - "for advertising purposes" → 본래 목적 외
> - "to improve service" → 본래 목적 내 (intended)

---

## 종합 정리

### 3.2 핵심 개념 3가지

**1. System Reliability (3.2.A.1)**
- 다양한 조건으로 테스트
- Edge case + Boundary + Normal 모두 포함
- 발견된 버그는 수정 후 재테스트

**2. Impacts on Society/Economy/Culture (3.2.A.2)**
- **Beneficial vs Harmful** 양면
- **Intended vs Unintended** 구별
- 4 조합 모두 가능 (intended+beneficial, unintended+harmful, etc.)

**3. Legal/IP (3.2.A.3)**
- **Open source**: 자유 사용 가능
- **Closed source**: permission + often purchase
- 무단 사용은 저작권 위반

### 자주 등장하는 시나리오 패턴

| 시나리오 | CED 분류 |
|---|---|
| 거짓 정보 확산 (소셜 미디어) | Unintended harmful |
| 시간 절약 앱 | Beneficial |
| 무단 데이터 판매 | Unintended harmful (privacy) |
| 자동화로 인한 일자리 변화 | Beneficial + harmful 양면 |
| 라이브러리 무단 사용 (closed source) | IP violation |
| 0원 송금 시 충돌 | Reliability failure |

### EXCLUSION / 제한 사항

- **CED 3.2는 개념 위주** — 코드 작성 출제 안 됨
- **법적 디테일 출제 안 됨** (GDPR, CCPA 등 구체 법규)
- **특정 도구/플랫폼 평가 출제 안 됨** (예: 특정 SNS 비판)
- **광범위한 윤리적 토론 출제 안 됨** — CED의 3가지 (reliability, impact, IP) 한정

### 시험 대비 팁

- **CED 인용문 외우기**: 3.2.A.1, 3.2.A.2, 3.2.A.3의 핵심 문구
- **시나리오를 분류**: 어느 카테고리에 속하는지 빠르게 판별
- **상식 + CED 키워드**: 일반적 윤리관 + CED 정확한 용어

---

## 누적 진행 (전체 70/70 완료)

본 TP9를 끝으로 **9개 보강 세트, 총 70 MCQ** 완성.

| 세트 | 토픽 | 문항 |
|------|------|------|
| TP1 | 4.6 File / 4.7 Wrapper | 10 |
| TP2 | 4.14 Linear / 4.17.B Binary | 8 |
| TP3 | 4.15 Sort / 4.17.C Merge | 10 |
| TP4 | 4.16 Recursion 심화 | 8 |
| TP5 | 3.7/3.8/3.9 Static/Scope/this | 8 |
| TP6 | 2.5/2.6/2.12 Boolean/RTA | 8 |
| TP7 | 1.5/1.11 Math/Casting | 6 |
| TP8 | References/Null/Aliasing | 6 |
| **TP9** | **3.2 Ethics & Impact** | **6** |
| **총** | | **70** |
