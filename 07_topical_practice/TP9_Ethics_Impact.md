# TP9: Ethics & Impact of Computing (보강 세트)

> **CED 2025-26 토픽**: 3.2 Impact of Program Design
> **문항 수**: 6 MCQ (Easy-Medium 위주)
> **시간 권장**: 10분
> **목표 정답률**: 90% 이상 (개념 위주)

---

## CED 범위 준수 사항

- **3.2.A.1 System Reliability**: *"System reliability refers to the program being able to perform its tasks as expected under stated conditions without failure. Programmers should make an effort to maximize system reliability by testing the program with a variety of conditions."*
- **3.2.A.2 Impacts**: *"The creation of programs has impacts on society, the economy, and culture. These impacts can be both beneficial and harmful. Programs meant to fill a need or solve a problem can have unintended harmful effects beyond their intended use."*
- **3.2.A.3 Legal/IP**: *"Legal issues and intellectual property concerns arise when creating programs. Programmers often reuse code written by others and published as open source and free to use. Incorporation of code that is not published as open source requires the programmer to obtain permission and often purchase the code before integrating it into their program."*

- **Skill 5.A**: *"Explain how computing impacts society, economy, and culture."* (CED practice)

---

## 출제 토픽 분포

| # | 토픽 | 핵심 |
|---|------|------|
| 1 | 3.2.A.1 — System Reliability | "test with variety of conditions" |
| 2 | 3.2.A.2 — Unintended Harmful Effect | 사회적 부작용 |
| 3 | 3.2.A.3 — Closed Source 사용 | permission + purchase |
| 4 | 3.2.A.1 — 테스트 케이스 다양성 | edge cases |
| 5 | 3.2.A.2 — Beneficial Impact | 사회적 유익 |
| 6 | 3.2.A.2 — Privacy as Unintended Harm | 의도하지 않은 부작용 |

**답안 분포**: A:2 / B:2 / C:1 / D:1

---

## 시험 안내

**Directions**: 다음 각 문항에 대해 가장 적절한 답을 고르시오.

---

### 1. [CED 3.2.A.1 · Easy]

은행의 송금 프로그램이 0원 송금 시 충돌(crash)한다고 보고되었다. CED 3.2.A.1 (*"Programmers should make an effort to maximize system reliability by testing the program with a variety of conditions"*)에 따라, 개발자가 시스템 안정성을 향상시키기 위해 가장 먼저 해야 할 일은?

(A) **다양한 조건**(0원, 음수, 매우 큰 금액 등)으로 테스트하여 모든 경우를 검증한다
(B) 오류를 문서화하고 그대로 배포한다
(C) 송금 기능 자체를 비활성화한다
(D) 송금 전에 임의의 지연 시간을 추가한다

---

### 2. [CED 3.2.A.2 · Medium]

친구들과 연결되도록 설계된 소셜 미디어 앱이, 일부 사용자에 의해 **거짓 정보(misinformation) 확산**에 사용되고 있다. CED 3.2.A.2 (*"unintended harmful effects beyond their intended use"*)에 따라 이 상황을 가장 잘 설명하는 용어는?

(A) System reliability failure (시스템 안정성 실패)
(B) Intellectual property violation (지적 재산권 침해)
(C) Open source license violation (오픈소스 라이선스 위반)
(D) **Unintended harmful effect** beyond intended use (의도하지 않은 유해한 부작용)

---

### 3. [CED 3.2.A.3 · Medium]

Java 프로그램에 어떤 라이브러리를 사용하려고 한다. 그 라이브러리는 **closed source(폐쇄형)** 로 공개되어 있다. CED 3.2.A.3에 따라, 이 라이브러리를 합법적으로 사용하려면 어떻게 해야 하는가?

(A) 모든 코드는 자유롭게 사용 가능하므로 별다른 조치 불필요
(B) **원작자의 허락(permission)을 받고, 종종 구매(purchase)** 가 필요
(C) 원작자에게 크레딧만 표시하면 됨
(D) 저작권이 만료될 때까지 무기한 대기

---

### 4. [CED 3.2.A.1 · Medium]

제곱근(square root)을 계산하는 프로그램의 신뢰성을 검증하려 한다. CED 3.2.A.1의 "**variety of conditions**"에 가장 부합하는 테스트 전략은?

(A) 양의 정수만으로 테스트
(B) 가장 자주 사용되는 숫자 한두 개만 테스트
(C) **양수, 0, 음수, 매우 큰 수, 매우 작은 수 등 다양한 입력**으로 테스트
(D) 개발자가 좋아하는 숫자만 테스트

---

### 5. [CED 3.2.A.2 · Easy]

도시의 교통 흐름을 예측해 통근자들이 시간을 절약하도록 돕는 앱이 출시되었다. CED 3.2.A.2 (*"impacts can be both beneficial and harmful"*)에 따라, 이 앱이 사회/경제/문화에 미치는 효과는?

(A) **사회·경제에 유익한 영향(beneficial impact)** — 시간 절약, 효율성 증가
(B) 의도하지 않은 유해한 부작용
(C) 지적 재산권 침해
(D) 시스템 안정성 실패

---

### 6. [CED 3.2.A.2 · Hard]

날씨 예보 앱이 사용자의 **위치 정보**를 수집하여 일기 예보를 제공한다. 이후 회사가 그 위치 데이터를 사용자의 명시적 동의 없이 광고주에게 판매한다. CED 3.2.A.2에 따라 이는 무엇으로 설명되는가?

(A) 시스템 안정성 실패 (system reliability failure)
(B) **본래 의도된 용도를 넘어선 유해한 영향**(harmful impact beyond intended use)
(C) 지적 재산권 침해 (intellectual property violation)
(D) 의도하지 않은 유익한 효과 (unintended beneficial impact)

---

**END OF TP9**
