# TP6: Boolean 심화 + Run-Time Analysis — 해설집

> **CED 2025-26 토픽**: 2.5 Compound Boolean, 2.6 Comparing Boolean, 2.12 Run-Time Analysis
> **답안 분포**: A:2 / B:2 / C:2 / D:2

---

## 정답 요약

| # | 정답 | CED 토픽 | 핵심 |
|---|------|---------|------|
| 1 | **A** `"3 -5 7 true"` | 2.5 short-circuit + 우선순위 | && > \|\|, side effect 추적 |
| 2 | **C** `x < 5 && y >= 8` | 2.6.A.2 De Morgan | `!(\|\|) ≡ && of !s` |
| 3 | **D** `"Empty or null"` | 2.5.A.2 NPE 회피 | `s != null && s.length()...` |
| 4 | **B** `55` | 2.12 누적 합 | 1+2+...+10 |
| 5 | **C** `6` | 2.12 절반 감소 | log₂100 ≈ 6 |
| 6 | **A** `"false true true"` | 2.6.B.1 ref vs equals | new String, c=a |
| 7 | **D** `10` | 2.12 대각선 | i==j 만족 10회 |
| 8 | **B** `"false false true"` | 2.6.A.2 + 2.5 | De Morgan 적용 |

---

## Section I: 문제별 상세 해설

---

### Q1. 정답: **(A) `"3 -5 7 true"`**

📌 **출제 의도:** **연산자 우선순위 (`&&` > `||`) + short-circuit evaluation**의 정확한 적용. side effect를 가진 메서드 호출 시 어느 메서드가 실제로 호출되는지 추적.

📎 **연계:** **CED 2.5.A.1**: *"The order of precedence for evaluating logical operators is ! (not), && (and), then || (or)."* + **CED 2.5.A.2**: *"Short-circuit evaluation occurs when the result of a logical operation using && or || can be determined by evaluating only the first Boolean expression."*

> **핵심 개념: && > ||의 우선순위 + short-circuit**
> - `A && B || C` = `(A && B) || C` (괄호 없이도 && 먼저)
> - **short-circuit**:
>   - `A && B`: A가 false면 B 미평가 (전체 false 결정)
>   - `A || B`: A가 true면 B 미평가 (전체 true 결정)
> - 본 문제: && 평가 시 **둘 다 평가** (A=true이면 B 필요), || 평가 시 **둘 다 평가** (A=false이면 B 필요)

> **선행 지식:**
> - 메서드 호출은 **side effect** (print) 발생 → 호출 추적 핵심
> - boolean 연산자는 left-to-right 평가 (단, short-circuit 적용)
> - `check(n)`: 출력 + n>0 반환

**한 단계씩 추적:**

| 단계 | 동작 | 출력 | 결과 |
|---|---|---|---|
| 1 | `check(3) && check(-5) || check(7)` 평가 시작 | — | — |
| 2 | && 우선 → `check(3) && check(-5)` 먼저 평가 | — | — |
| 3 | `check(3)` 호출 | `"3 "` | true |
| 4 | true이므로 우측(check(-5)) 평가 필요 | — | — |
| 5 | `check(-5)` 호출 | `"-5 "` | false |
| 6 | true && false = false | — | false |
| 7 | `false || check(7)` 평가 | — | — |
| 8 | false이므로 우측(check(7)) 평가 필요 | — | — |
| 9 | `check(7)` 호출 | `"7 "` | true |
| 10 | false || true = true | — | true |
| 11 | `println(true)` | `true\n` | — |

**최종 출력: `3 -5 7 true`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `"3 -5 7 true"`** ✅ | 정답 | 세 메서드 모두 호출됨 + result는 true |
| (B) `"3 true"` | check(3)에서 short-circuit으로 끝난다고 오해 | check(3)이 true라도 && 우측 평가 필요 |
| (C) `"3 -5 false"` | || 평가 안 한다고 오해 | && 결과(false)에 || 적용 → check(7) 호출 |
| (D) `"3 -5 7 false"` | 최종 결과를 false로 오해 | false || true = true |

> ⚠️ **함정 1:** **`&&` > `||` 우선순위**. `A && B || C` = `(A && B) || C`. 괄호 없이도 && 먼저. 잘못 읽으면 `A && (B || C)`로 오해 가능.

> ⚠️ **함정 2:** **short-circuit 방향**. `A && B`: A=false → 종료. `A || B`: A=true → 종료. 본 문제는 두 연산자 모두 우측 평가 필요.

> ⚠️ **함정 3:** **출력에 줄바꿈 자리**. `print`는 줄바꿈 없음, `println`은 있음. 본 문제는 모두 print → 한 줄에 누적.

> 💡 **꿀팁 1:** **연산자 우선순위 외우기**: `!` > `&&` > `||` (CED 2.5.A.1). 산술처럼 `*` > `+`와 비유.

> 💡 **꿀팁 2:** **short-circuit 활용 패턴**: NPE 회피 (Q3), 무효 인덱스 회피 (`i < length && arr[i] > 0`), 비싼 연산 회피 등.

> 💡 **꿀팁 3:** **side effect 메서드 트레이싱**: 호출 시점마다 print 출력 표시. 어느 메서드가 호출되었고, 어떤 순서인지 정확히 기록.

---

### Q2. 정답: **(C) `x < 5 && y >= 8`**

📌 **출제 의도:** **De Morgan's Law의 적용** (CED 2.6.A.2). `!(A || B) ≡ !A && !B`를 구체적 식에 적용해 동치 식 유도.

📎 **연계:** **CED 2.6.A.2**: *"De Morgan's law can be applied to Boolean expressions to create equivalent Boolean expressions. Under De Morgan's law, the Boolean expression !(a && b) is equivalent to !a || !b and the Boolean expression !(a || b) is equivalent to !a && !b."*

> **핵심 개념: De Morgan's Law**
> - `!(A && B) ≡ !A || !B` — AND 부정은 OR of 부정
> - `!(A || B) ≡ !A && !B` — OR 부정은 AND of 부정
>
> **적용 예** (`!(x >= 5 || y < 8)`):
> - `!(A || B)` 형태 → `!A && !B`
> - A = `x >= 5`, B = `y < 8`
> - `!A` = `x < 5`, `!B` = `y >= 8`
> - 결과: `x < 5 && y >= 8` ✓

> **선행 지식:**
> - 부등호 부정: `!(>=) → <`, `!(<) → >=`, `!(>) → <=`, `!(<=) → >`
> - `&&`와 `||` 의 부정 시 서로 바뀜 (De Morgan)

**진리표 검증:**

| x>=5 | y<8 | OR | NOT OR | x<5 | y>=8 | NEW AND |
|---|---|---|---|---|---|---|
| T | T | T | F | F | F | F |
| T | F | T | F | F | T | F |
| F | T | T | F | T | F | F |
| F | F | F | T | T | T | T |

두 식의 NOT OR 컬럼과 NEW AND 컬럼이 모두 일치 ✓

**오답 분석:**

| 보기 | 식 | 왜 틀린가 |
|---|---|---|
| (A) `x >= 5 && y < 8` | 부정 안 함 + && 적용 | 원식의 OR + NOT 둘 다 무시 |
| (B) `!(x >= 5) \|\| !(y < 8)` | De Morgan을 잘못 적용 (AND→OR로 변환) | 원식은 `!(A \|\| B)` → `!A && !B` (AND), OR 아님 |
| **(C) `x < 5 && y >= 8`** ✅ | 정답 | De Morgan 정확히 적용 |
| (D) `x > 5 && y <= 8` | 부등호 부정 잘못 | `!(x>=5) = x<5` (5 미포함), `x>5`는 5 제외해 다름 |

> ⚠️ **함정 1:** **부등호 부정의 경계**. `!(x >= 5)` ≡ `x < 5` (5 자체는 포함 안 됨). `x > 5`는 5도 제외해 잘못된 부정.

> ⚠️ **함정 2:** **AND ↔ OR 전환**. De Morgan의 핵심: 부정 시 두 연산자가 서로 바뀜. `!(||) → &&`.

> ⚠️ **함정 3:** **부분 적용**. (B)는 부등호 부정만 했고 AND/OR 전환을 안 함 → 잘못된 De Morgan.

> 💡 **꿀팁 1:** **De Morgan 빠른 변환 공식**:
> 1. 외부 부정 분배
> 2. 내부 연산자 뒤집기 (&& ↔ ||)
> 3. 각 항 부정 (부등호 뒤집기)

> 💡 **꿀팁 2:** **진리표로 검증**: 두 식이 모든 입력에서 같은 결과 → 동치. AP에서 가장 안전한 검증법.

> 💡 **꿀팁 3:** **자주 쓰이는 동치**:
> - `!(A && B) ≡ !A || !B`
> - `!(A || B) ≡ !A && !B`
> - `!!A ≡ A` (이중 부정)
> - `A && true ≡ A`
> - `A || false ≡ A`

---

### Q3. 정답: **(D) `"Empty or null"`**

📌 **출제 의도:** **Short-circuit으로 NullPointerException 회피** — `s != null` 체크가 false면 우측 `s.length()` 미평가. 안전한 null 처리 표준 패턴.

📎 **연계:** **CED 2.5.A.2** Short-circuit + **CED 1.14.A.2**: *"A method call on a null reference will result in a NullPointerException."* + **CED 2.6.B.2** null 비교.

> **핵심 개념: Null-safe 패턴**
> ```java
> if (obj != null && obj.method()) { ... }
> ```
> - 좌측 `obj != null` 먼저 체크
> - false면 우측 미평가 → NPE 회피
> - 좌측 true면 우측 안전하게 호출 가능

> **선행 지식:**
> - `s = null` → `s.length()` 호출 시 `NullPointerException`
> - `&&`의 short-circuit이 안전망 역할
> - **순서 중요**: `s.length() > 0 && s != null`로 거꾸로 쓰면 NPE 발생

**한 단계씩 추적:**

| 단계 | 동작 | 결과 |
|---|---|---|
| 1 | `s = null` | s는 null 참조 |
| 2 | `s != null` 평가 | **false** |
| 3 | && short-circuit → 우측 평가 안 함 | s.length() 호출 안 됨 → NPE 회피 |
| 4 | 전체 if 조건 = false | else 블록 실행 |
| 5 | `println("Empty or null")` | 출력 |

**최종 출력: `Empty or null`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"Has content"` | if 조건이 true라고 오해 | `s != null` = false → if 미진입 |
| (B) Compile error | `s.length()` 사용에 문제 있다고 오해 | 컴파일은 정상 (런타임 회피) |
| (C) NullPointerException | short-circuit 작동 안 한다고 오해 | && 좌측 false → 우측 평가 안 함 |
| **(D) `"Empty or null"`** ✅ | 정답 | else 블록 실행 |

> ⚠️ **함정 1:** **순서가 결정적**. `s != null && s.length() > 0` (안전) vs `s.length() > 0 && s != null` (NPE). short-circuit은 좌→우.

> ⚠️ **함정 2:** **`||` short-circuit 방향**. `||`는 좌측 true → 우측 미평가. `s == null || s.length() == 0`도 안전 패턴 (true이면 NPE 안 발생).

> ⚠️ **함정 3:** **`!=` 우선순위**. `!=`는 `&&`보다 높음. 따라서 `s != null && ...`는 `(s != null) && ...`로 자동 묶임.

> 💡 **꿀팁 1:** **null-safe 표준 패턴**:
> ```java
> if (obj != null && obj.someMethod()) { ... }
> ```
> AP FRQ에서 매우 자주 등장. 객체 참조 사용 전 null 체크.

> 💡 **꿀팁 2:** **NPE 발생 조건**: null 참조에 메서드 호출 또는 필드 접근. `null.method()`, `null.field` 모두 NPE.

> 💡 **꿀팁 3:** **else 블록 동작**: if 조건이 false면 else 실행. else 없으면 그냥 다음 코드로 진행.

---

### Q4. 정답: **(B) `55`**

📌 **출제 의도:** **중첩 루프의 statement execution count** — 외부 i, 내부 j 의 누적 실행 횟수를 등차수열 합으로 계산. CED 2.12의 핵심 패턴.

📎 **연계:** **CED 2.12.A.1**: *"A statement execution count indicates the number of times a statement is executed by the program. Statement execution counts are often calculated informally through tracing and analysis of the iterative statements."*

> **핵심 개념: 중첩 루프 실행 횟수**
> - 외부 `i = 1, 2, ..., 10` (10회)
> - 내부 `j = 1, ..., i` (i회)
> - inner `count++` 실행 횟수 = i회
> - 총합 = 1 + 2 + ... + 10 = **n(n+1)/2** = 10·11/2 = **55**

> **선행 지식:**
> - 등차수열 합 공식: 1+2+...+n = n(n+1)/2
> - 외부 루프 i회마다 내부가 i번 → "삼각형" 패턴
> - O(n²)이지만 n²/2 수준

**i별 실행 횟수:**

| i | inner 실행 | 누적 count |
|---|---|---|
| 1 | 1 | 1 |
| 2 | 2 | 3 |
| 3 | 3 | 6 |
| 4 | 4 | 10 |
| 5 | 5 | 15 |
| 6 | 6 | 21 |
| 7 | 7 | 28 |
| 8 | 8 | 36 |
| 9 | 9 | 45 |
| 10 | 10 | **55** |

**최종: 55** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `100` | n²로 계산 (full nested) | inner는 i회로 제한, n²이 아닌 n(n+1)/2 |
| **(B) `55`** ✅ | 정답 | 1+2+...+10 = 55 |
| (C) `45` | 1+2+...+9 = 45 (한 항 빠뜨림) | i=10 포함 |
| (D) `10` | 외부 루프 횟수만 카운트 | 내부 누적도 카운트 |

> ⚠️ **함정 1:** **삼각형 vs 사각형**. 본 코드는 삼각형 패턴 (n(n+1)/2). 만약 inner가 `j = 1; j <= n` (i 무관)이면 사각형 (n²).

> ⚠️ **함정 2:** **공식 헷갈림**. `n(n+1)/2` vs `n(n-1)/2`. 1부터 n까지 합은 `n(n+1)/2`, 1부터 n-1까지는 `n(n-1)/2`.

> ⚠️ **함정 3:** **<, <= 차이**. `i <= 10`은 i=10 포함. 만약 `i < 10`이면 i=10 미실행, 결과는 1+...+9 = 45.

> 💡 **꿀팁 1:** **등차수열 합 외우기**:
> - 1 + 2 + ... + n = n(n+1)/2
> - 1² + 2² + ... + n² = n(n+1)(2n+1)/6
> - n=10 → 합 55, 제곱합 385

> 💡 **꿀팁 2:** **CED 2.12 분석 패턴**: outer × inner 곱 (full nested) vs outer i 의 함수 (제한된 inner). 코드의 inner 종료 조건이 외부 변수에 의존하는지 확인.

> 💡 **꿀팁 3:** **시간 복잡도와 관계**: O(n²)이지만 정확한 횟수는 n(n+1)/2 ≈ n²/2. selection sort의 비교 횟수와 동일 패턴.

---

### Q5. 정답: **(C) `6`**

📌 **출제 의도:** **절반씩 감소하는 while 루프** — log₂n 횟수 직관 + 정수 나눗셈으로 step-by-step 추적.

📎 **연계:** **CED 2.12** Run-Time Analysis + **CED 2.7** while loop. Binary search, merge sort 분할 깊이와 동일 원리.

> **핵심 개념: 절반 감소 루프**
> - `n = n / 2` (정수 나눗셈)
> - 100 → 50 → 25 → 12 → 6 → 3 → 1 → exit
> - log₂100 ≈ 6.64 → 약 6~7회

> **선행 지식:**
> - 정수 나눗셈: 25/2 = 12 (소수점 절사), 12/2 = 6, 3/2 = 1
> - while 종료 조건: `n > 1` (n=1이면 종료)
> - 매 반복: count++ + n /= 2

**한 단계씩 추적:**

| 반복 | n (전) | n > 1? | n / 2 | count |
|---|---|---|---|---|
| 시작 | 100 | — | — | 0 |
| 1 | 100 | true | 50 | 1 |
| 2 | 50 | true | 25 | 2 |
| 3 | 25 | true | 12 | 3 |
| 4 | 12 | true | 6 | 4 |
| 5 | 6 | true | 3 | 5 |
| 6 | 3 | true | 1 | **6** |
| 종료 | 1 | false | — | — |

**최종: 6** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `7` | 한 회 더 카운트 | n=1에서 종료 (1>1 false) |
| (B) `100` | n 자체를 답으로 | count는 반복 횟수 |
| **(C) `6`** ✅ | 정답 | 100→1까지 6단계 |
| (D) `50` | 첫 반복 후 n/2 값 | count는 누적 횟수 |

> ⚠️ **함정 1:** **종료 조건 정확히**. `n > 1` (1에서 종료). `n >= 1`이면 무한 루프 (1/2=0, 0>=1 false라 안전하지만 다른 조합에서 위험).

> ⚠️ **함정 2:** **정수 나눗셈**. 25/2 = 12, 12/2 = 6, 3/2 = 1. 부동소수점 아님 (소수부 절사).

> ⚠️ **함정 3:** **±1 차이 (off-by-one)**. log₂100 = 6.64. 정확한 횟수는 ⌈log₂n⌉ 정도.

> 💡 **꿀팁 1:** **log₂ 기억**:
> - log₂10 ≈ 3.3
> - log₂100 ≈ 6.6
> - log₂1000 ≈ 10
> - log₂(2^k) = k

> 💡 **꿀팁 2:** **절반 감소 패턴 적용**:
> - Binary search (Q4.17.B)
> - Merge sort 깊이 (Q4.17.C)
> - 본 문제처럼 명시적 while

> 💡 **꿀팁 3:** **CED 2.12와 알고리즘 분석**: 이 패턴이 `O(log n)`임을 직관적으로 이해 → 큰 n에서도 적은 횟수로 종료.

---

### Q6. 정답: **(A) `"false true true"`**

📌 **출제 의도:** **`==` 참조 비교 vs `.equals()` 내용 비교** + String pool 동작 이해. CED 2.6.B의 핵심 함정.

📎 **연계:** **CED 2.6.B.1**: *"Two different variables can hold references to the same object. Object references can be compared using == and !=."* + **CED 1.15** String Manipulation.

> **핵심 개념: String 비교의 두 가지**
> - **`==`**: 참조 비교 (메모리 주소 동일 여부)
> - **`.equals()`**: 내용 비교 (문자열 내용 동일 여부)
>
> **String pool 특이사항**:
> - String literal `"hello"`은 **pool에서 공유**
> - `new String("hello")`은 **항상 새 객체** (pool과 별개)
> - 따라서 두 동일 내용 String의 `==`은 생성 방식에 따라 다름

> **선행 지식:**
> - 변수 대입 (`c = a`): 같은 참조 복사 (alias)
> - **`equals` 오버라이드는 EXCLUSION** — 작성 X, 사용 O
> - String의 `equals`는 내용 비교 (Java 정의)

**한 단계씩 추적:**

| 변수 | 생성 방식 | 참조 |
|---|---|---|
| a | `"hello"` (literal) | R1 (pool) |
| b | `new String("hello")` | R2 (heap, 새 객체) |
| c | `a` (대입) | R1 (a와 동일) |

**비교 결과:**

| 비교 | 평가 | 결과 |
|---|---|---|
| `a == b` | R1 vs R2 | **false** (다른 참조) |
| `a.equals(b)` | "hello" vs "hello" 내용 | **true** (같은 내용) |
| `a == c` | R1 vs R1 | **true** (같은 참조) |

**최종 출력: `"false true true"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `"false true true"`** ✅ | 정답 | 참조/내용/대입 정확 |
| (B) `"true true true"` | `==`도 내용 비교라 오해 | `==`은 참조 비교 |
| (C) `"false false false"` | `equals`가 참조 비교라 오해 | String의 `equals`는 내용 비교 |
| (D) `"true false true"` | `==`/`equals` 거꾸로 적용 | 거꾸로 |

> ⚠️ **함정 1:** **`==` String 비교 위험성**. literal끼리는 pool 공유로 `==` true 가능, but `new String(...)`이 섞이면 false. **항상 `.equals()` 사용 권장**.

> ⚠️ **함정 2:** **`.equals()` 오버라이드 작성 OUT** (CED 2.6.B.3 EXCLUSION). 학생은 String의 `equals` **사용**만 하고, 직접 작성은 출제 안 됨.

> ⚠️ **함정 3:** **변수 대입 = aliasing**. `c = a`는 새 객체 생성 아님, **같은 참조**. 따라서 `a == c` true.

> 💡 **꿀팁 1:** **String 비교 표준**: 항상 `.equals()` 사용. AP FRQ에서 `==` String 비교 시 거의 항상 감점.

> 💡 **꿀팁 2:** **pool vs new**:
> - `String s1 = "hello"; String s2 = "hello";` → s1 == s2 true (pool 공유)
> - `String s3 = new String("hello");` → s1 == s3 false (다른 객체)
> - 그러나 `s1.equals(s3)` 항상 true

> 💡 **꿀팁 3:** **객체 비교 일반론**:
> - primitive: `==`로 값 비교
> - 객체: `==`로 참조 비교, `.equals()`로 내용 비교 (각 클래스의 정의에 따름)

---

### Q7. 정답: **(D) `10`**

📌 **출제 의도:** **조건부 카운트의 statement execution count** — 중첩 루프 안의 if 조건이 만족되는 횟수 추적. 대각선 패턴 인식.

📎 **연계:** **CED 2.12** Run-Time Analysis + **CED 2.3** if Statements + **CED 2.11** Nested Iteration.

> **핵심 개념: 조건 카운트**
> - 중첩 루프 inner 실행 횟수 = n × n = 100
> - if 조건 (`i == j`) 만족 횟수 = **count++ 실행 횟수**
> - i와 j가 같은 경우: (0,0), (1,1), ..., (9,9) → **n번** (대각선)

> **선행 지식:**
> - i, j 모두 0~n-1 순회
> - i == j는 정확히 n번 발생 (각 i에 대해 j=i 한 번)
> - count는 if true 시에만 증가

**대각선 시각화 (n=10):**

```
   j=0 j=1 j=2 ... j=9
i=0  ✓   ✗   ✗  ...  ✗
i=1  ✗   ✓   ✗  ...  ✗
i=2  ✗   ✗   ✓  ...  ✗
...
i=9  ✗   ✗   ✗  ...  ✓
```

대각선 셀 = n = **10**

**최종: 10** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `100` | inner 총 실행 횟수 (if 조건 무시) | count는 if true일 때만 증가 |
| (B) `20` | 대각선 + 반대 대각선이라 오해 (n+n) | i==j는 정확히 한 대각선만 |
| (C) `1` | i==j가 한 번만 발생이라 오해 | n번 발생 (각 i 별로 한 번) |
| **(D) `10`** ✅ | 정답 | n=10 대각선 셀 수 |

> ⚠️ **함정 1:** **inner 실행 vs count 증가**. inner는 100번 실행되지만 count는 10번만 증가. 두 개념 분리.

> ⚠️ **함정 2:** **n에 따른 변화**. count = n. n=5면 5, n=20이면 20. 일반화 가능.

> ⚠️ **함정 3:** **다른 조건 패턴**:
> - `i + j == n - 1`: 반대 대각선 (n번)
> - `i + j == n`: 대각선 위 (n-1번)
> - `i < j`: 상삼각 (n(n-1)/2번)
> - `i <= j`: 상삼각 + 대각선 (n(n+1)/2번)

> 💡 **꿀팁 1:** **2D 조건 카운트 패턴**: 조건 시각화 → 매트릭스에 ✓/✗ 표시 → 합산.

> 💡 **꿀팁 2:** **CED 2.12 + 2.13 결합**: 2D 배열 순회 + 조건 카운트는 4.13 표준 알고리즘과 같은 골격.

> 💡 **꿀팁 3:** **표준 알고리즘 (CED 2.9.A.1)**: "determine the frequency with which a specific criterion is met". 조건 만족 카운트는 매우 빈번한 패턴.

---

### Q8. 정답: **(B) `"false false true"`**

📌 **출제 의도:** **De Morgan 동치 검증** — Q2의 응용. 두 식이 실제로 같은 결과를 내는지 구체적 값으로 확인 + 동치임을 `a == b`로 검증.

📎 **연계:** **CED 2.6.A.2** De Morgan + **CED 2.5** Compound Boolean. Q2의 변형 (개념 확인 → 실제 트레이스).

> **핵심 개념: De Morgan 동치 식의 실제 동작**
> - `!(x >= 5 || y < 8)` (원식)
> - `(x < 5 && y >= 8)` (De Morgan 적용)
> - **모든 입력에서 같은 결과** → `a == b` 항상 true

> **선행 지식:**
> - x=5, y=10 입력으로 두 식 평가
> - boolean의 `==`: 같은 truth value면 true
> - short-circuit이 결과에 영향 없음 (Q2의 진리표 검증과 일치)

**한 단계씩 추적:**

| 단계 | 식 | 평가 |
|---|---|---|
| 1 | `x >= 5` | 5 >= 5 → **true** |
| 2 | `y < 8` | 10 < 8 → **false** |
| 3 | `(true || false)` | **true** |
| 4 | `!(true)` | **false** |
| 5 | `a = false` | a = false |
| 6 | `x < 5` | 5 < 5 → **false** |
| 7 | && short-circuit (left false) | 우측 평가 안 함 |
| 8 | `b = false` | b = false |
| 9 | `a == b` | false == false → **true** |
| 10 | println | `"false false true"` |

**최종 출력: `"false false true"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"true true false"` | 두 식이 다른 결과라고 오해 | De Morgan 동치라 항상 같음 |
| **(B) `"false false true"`** ✅ | 정답 | 두 식 모두 false, equal |
| (C) `"true false false"` | a 평가 잘못 + 동치 무시 | a = false (정확) |
| (D) `"false true true"` | b 평가 잘못 | b = false (short-circuit) |

> ⚠️ **함정 1:** **De Morgan 동치 = 항상 같음**. 입력이 어떻든 두 식의 결과는 같음 → `a == b` 항상 true.

> ⚠️ **함정 2:** **short-circuit 영향 없음**. b 평가에서 `5 < 5`가 false라 우측 미평가, but 결과는 정확.

> ⚠️ **함정 3:** **`a == b`로 boolean 비교**. boolean `==`은 truth value 비교. 본 문제는 둘 다 false라 true.

> 💡 **꿀팁 1:** **De Morgan 검증법**: 서로 다른 입력 값으로 두 식이 같은 결과 내는지 확인. 항상 같으면 동치.

> 💡 **꿀팁 2:** **boolean `==` 활용**: 두 식의 동치성 검사 (`expr1 == expr2`), boolean 변수 비교, `if (flag == true)` 등.

> 💡 **꿀팁 3:** **De Morgan 패턴 외우기**:
> - `!(>= && <)` ↔ `< || >=` (양쪽 부정 + AND→OR)
> - `!(|| && ||)` ↔ De Morgan + 분배 등 복잡한 식도 단계적 적용 가능

---

## 종합 정리

### 2.5 Compound Boolean 핵심
- 우선순위: `!` > `&&` > `||`
- Short-circuit: 좌측만으로 결정 시 우측 미평가
- NPE 회피 패턴: `obj != null && obj.method()`

### 2.6.A.2 De Morgan's Law
```
!(A && B) ≡ !A || !B
!(A || B) ≡ !A && !B
```
- 부정 시 연산자 뒤집기 (&& ↔ ||)
- 각 항도 부정 (부등호 뒤집기)

### 2.6.B 객체 비교
- `==`: 참조 비교 (메모리 주소)
- `.equals()`: 내용 비교 (각 클래스 정의)
- String literal vs `new String(...)` 차이 주의

### 2.12 Statement Execution Count
- 단순 for: n회
- 중첩 사각형: n × m
- 중첩 삼각형: 1+2+...+n = n(n+1)/2
- 절반 감소 while: log₂n 회
- 조건부: 조건 만족 횟수만 카운트

### 흔한 함정 모음
1. **`&&` > `||` 우선순위 무시** (Q1)
2. **De Morgan 부분 적용** (Q2): 부등호만 부정 + 연산자 안 바꿈
3. **NPE를 short-circuit으로 회피 가능** (Q3)
4. **n² vs n(n+1)/2 혼동** (Q4)
5. **String `==` vs `.equals()`** (Q6)

### EXCLUSION 재확인
- **`equals` 오버라이드 작성 OUT** (CED 2.6.B.3) ✓ — 본 세트는 사용만
- **`Math.min/max` OUT** ✓
- **`break`/`continue`, `switch`, `do-while` OUT** ✓
- **재귀 작성 OUT** (CED 4.16) ✓
