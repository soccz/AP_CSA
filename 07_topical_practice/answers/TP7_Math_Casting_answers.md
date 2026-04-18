# TP7: Math + Casting + Overflow — 해설집

> **CED 2025-26 토픽**: 1.5 Casting and Range, 1.11 Math Class
> **답안 분포**: A:2 / B:2 / C:1 / D:1

---

## 정답 요약

| # | 정답 | CED 토픽 | 핵심 |
|---|------|---------|------|
| 1 | **A** `"7 8.0"` | 1.5.A — 절사 vs 반올림 | (int) vs (int)(x+0.5) |
| 2 | **C** `"15 3.7"` | 1.11.A.2 abs 두 오버로드 | int → int, double → double |
| 3 | **B** `32` | 1.11.A.2 + 1.5 | pow(2,5)=32.0 → (int)=32 |
| 4 | **B** `"-2 -3"` | 1.5.A.4 음수 반올림 | (int)(x-0.5) |
| 5 | **A** `1 to 6` | 1.11.A.3 random 범위 | dice roll 패턴 |
| 6 | **D** `-2147483648` | 1.5.B.3 오버플로 | MAX+1 wrap |

---

## Section I: 문제별 상세 해설

---

### Q1. 정답: **(A) `"7 8.0"`**

📌 **출제 의도:** **`(int)` 캐스팅의 두 가지 사용** — (1) 단순 절사 (truncation), (2) `(int)(x + 0.5)` 반올림 관용구. CED 1.5.A의 핵심 두 패턴 구별.

📎 **연계:** **CED 1.5.A.2**: *"Casting a double value to an int value causes the digits to the right of the decimal point to be truncated."* + **CED 1.5.A.4**: *"Values of type double can be rounded to the nearest integer by (int)(x + 0.5) for non-negative numbers."*

> **핵심 개념: 절사 vs 반올림**
> - **`(int) x`** (단순): 소수부 **버림** (toward zero)
>   - 7.8 → 7, 7.2 → 7, 7.99 → 7
> - **`(int)(x + 0.5)`** (반올림 관용구): 가까운 정수
>   - 7.8 + 0.5 = 8.3 → (int) = 8 (반올림 효과)
>   - 7.2 + 0.5 = 7.7 → (int) = 7

> **선행 지식:**
> - `int → double` 자동 승격 (CED 1.5.A.3): `int z` 자리에 `double` 대입 가능
> - 본 문제 `double z = (int)(...)`: int 결과가 자동으로 double로 승격 (예: 8 → 8.0)
> - `print` 시 `double`은 `8.0` 형태 (소수점 1자리 최소)

**한 단계씩 추적:**

| 단계 | 식 | 결과 |
|---|---|---|
| 1 | `x = 7.8` | x = 7.8 (double) |
| 2 | `(int) x` | (int) 7.8 = **7** (truncate) |
| 3 | `int y = 7` | y = 7 |
| 4 | `x + 0.5` | 7.8 + 0.5 = 8.3 |
| 5 | `(int) 8.3` | **8** (truncate after add) |
| 6 | `double z = 8` | 자동 승격 → z = 8.0 |
| 7 | `println(7 + " " + 8.0)` | `"7 8.0"` |

**최종 출력: `"7 8.0"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `"7 8.0"`** ✅ | 정답 | y는 truncate=7, z는 round=8.0 |
| (B) `"8 8.0"` | y도 반올림이라 오해 | `(int) x` 단독은 truncation, +0.5 없음 |
| (C) `"7 7.0"` | z 계산에서 +0.5 무시 | (int)(x+0.5) = 8 |
| (D) `"8 7.0"` | y/z 거꾸로 적용 | y=7 (truncate), z=8.0 (round) |

> ⚠️ **함정 1:** **`(int)` 단독 = truncation**. 반올림 아님. 7.99도 7로 버림.

> ⚠️ **함정 2:** **반올림 관용구의 0.5**. 비음수에는 `+0.5`, 음수에는 `-0.5` (Q4 참조). 부호 다르면 잘못된 결과.

> ⚠️ **함정 3:** **double 변수에 int 대입**. 자동 승격으로 정상 컴파일. 출력 시 `.0` 추가.

> 💡 **꿀팁 1:** **반올림 패턴 표준 (CED 1.5.A.4)**:
> - 비음수: `(int)(x + 0.5)`
> - 음수: `(int)(x - 0.5)`
> - **`Math.round`는 Quick Reference에 없음** → AP는 위 관용구 사용

> 💡 **꿀팁 2:** **두 캐스팅 사용**:
> - `(int) x`: 정수부 추출 (소수 버림)
> - `(double) n`: int를 명시적 double로 (산술 정확도)
> - `(double) (a + b)`: 괄호 위치 주의

> 💡 **꿀팁 3:** **자동 승격 (widening)**: int → double은 자동, double → int는 명시적 캐스팅 필요. 데이터 손실 가능성 때문.

---

### Q2. 정답: **(C) `"15 3.7"`**

📌 **출제 의도:** `Math.abs`의 **두 오버로드 메서드** — `abs(int)`는 int 반환, `abs(double)`은 double 반환. 인자 타입에 따라 자동 선택.

📎 **연계:** **CED 1.11.A.2**: *"static int abs(int x) returns the absolute value of an int value. static double abs(double x) returns the absolute value of a double value."* — Quick Reference 명시 두 메서드.

> **핵심 개념: Math.abs 오버로드**
> - **`Math.abs(int)`**: int 반환. 예: `abs(-15) = 15`
> - **`Math.abs(double)`**: double 반환. 예: `abs(-3.7) = 3.7`
> - 컴파일러가 인자 타입 보고 자동 선택 (오버로드 해소)

> **선행 지식:**
> - 절댓값: 부호 제거. `abs(-15) = 15`, `abs(15) = 15`
> - **`Math.min`, `Math.max`는 Quick Reference에 없음** → AP 미출제
> - `print(int)`은 그냥 출력, `print(double)`은 `.x` 형태

**한 단계씩 추적:**

| 식 | 결과 |
|---|---|
| `Math.abs(-15)` | int 15 |
| `Math.abs(-3.7)` | double 3.7 |
| `15 + " " + 3.7` | `"15 3.7"` (String concat) |

**최종 출력: `"15 3.7"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"-15 -3.7"` | abs가 작동 안 한다고 오해 | abs는 양수로 변환 |
| (B) `"15 -3.7"` | double 버전이 작동 안 한다고 오해 | abs(double)도 정상 |
| **(C) `"15 3.7"`** ✅ | 정답 | 두 abs 모두 양수 반환 |
| (D) `"-15 3.7"` | int 버전이 작동 안 한다고 오해 | abs(int)도 정상 |

> ⚠️ **함정 1:** **공식 Math 메서드 5개만 (CED 1.11.A.2)**: `abs(int)`, `abs(double)`, `pow`, `sqrt`, `random`. 다른 Math 메서드는 모두 OUT.

> ⚠️ **함정 2:** **`Math.min`/`Math.max` 사용 금지**. AP에 출제 안 됨. 최솟값/최댓값은 if 비교로 직접.

> ⚠️ **함정 3:** **Integer.MIN_VALUE의 abs 함정**. `Math.abs(Integer.MIN_VALUE)`는 오버플로로 다시 음수 반환 (개념적, AP 직접 출제 X).

> 💡 **꿀팁 1:** **공식 Math 메서드 5개 외우기**:
> - `static int abs(int)` → int
> - `static double abs(double)` → double
> - `static double pow(double, double)` → double
> - `static double sqrt(double)` → double
> - `static double random()` → double `[0.0, 1.0)`

> 💡 **꿀팁 2:** **메서드 오버로드 (CED 1.9)**: 같은 이름 + 다른 파라미터 타입. 컴파일러가 인자 타입 보고 선택. abs는 두 버전 (int, double).

> 💡 **꿀팁 3:** **min/max 직접 구현** (3항 연산자 `?:`도 Quick Reference에 없으므로 AP는 항상 `if-else`만 사용):
> ```java
> // 방법 1: if-else 한 줄 분리
> int max = a;
> if (b > max) max = b;
>
> // 방법 2: if-else 블록
> int max;
> if (a > b) {
>     max = a;
> } else {
>     max = b;
> }
> ```

---

### Q3. 정답: **(B) `32`**

📌 **출제 의도:** `Math.pow(double, double)`이 **항상 double 반환** + `(int)` 캐스팅으로 정수 변환. 결과가 정확한 정수여도 (32.0) 명시 캐스팅 필요.

📎 **연계:** **CED 1.11.A.2**: *"static double pow(double base, double exponent) returns the value of the first parameter raised to the power of the second parameter."* — 반환 타입 **double**.

> **핵심 개념: Math.pow + 캐스팅**
> - `Math.pow(2, 5)` → **double 32.0** (정수 결과여도 double)
> - int 변수에 대입 시 **명시적 (int) 캐스팅 필수** (자동 변환 안 됨, 정확도 손실 가능)
> - `(int) 32.0 = 32`

> **선행 지식:**
> - `int + int → int` (자동 승격 없음)
> - `int + double → double` (자동 승격)
> - **double → int는 명시적 캐스팅** (CED 1.5.A.1)
> - 캐스팅 없이 `int result = Math.pow(...)` 시 컴파일 에러

**한 단계씩 추적:**

| 단계 | 식 | 결과 |
|---|---|---|
| 1 | `Math.pow(2, 5)` | int 2 → double 2.0 자동 승격 후 호출 |
| 2 | `pow(2.0, 5.0)` | double **32.0** |
| 3 | `(int) 32.0` | int **32** (truncate) |
| 4 | `int result = 32` | result = 32 |
| 5 | `println(32)` | `32` |

**최종 출력: `32`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `25` | base + exp = 27이 아닌 5²=25 (잘못 계산) | pow(2, 5) = 2⁵ = 32, 5²이 아님 |
| **(B) `32`** ✅ | 정답 | 2⁵ = 32 |
| (C) `10` | 2 × 5 = 10 (잘못 계산) | pow는 곱셈 아닌 거듭제곱 |
| (D) Compile-time error | 캐스팅에 문제 있다고 오해 | (int) 캐스팅 정상 |

> ⚠️ **함정 1:** **명시적 캐스팅 필요**. `int result = Math.pow(2, 5);`는 컴파일 에러 (double → int 자동 변환 안 됨). 본 코드 `(int)` 사용 → 정상.

> ⚠️ **함정 2:** **pow 반환 항상 double**. 결과가 정수여도 (32.0). 만약 `Math.pow(2, 0.5)`처럼 진짜 소수라면 캐스팅 시 손실.

> ⚠️ **함정 3:** **거듭제곱 vs 곱셈**. pow(a, b) = a^b (a의 b제곱). `2 * 5 = 10`이 아닌 `2⁵ = 32`.

> 💡 **꿀팁 1:** **Math.pow 자주 쓰이는 값**:
> - pow(2, n): 1, 2, 4, 8, 16, 32, 64, ...
> - pow(10, n): 1, 10, 100, 1000, ...
> - pow(n, 2): n²

> 💡 **꿀팁 2:** **(int) Math.pow(...)** 패턴: 정수 거듭제곱 시 표준. 정확도 손실 우려 시 long 사용 권장 — but **AP는 long OUT**.

> 💡 **꿀팁 3:** **부동소수점 정밀도**: 큰 수의 pow는 정확도 손실 가능. AP에서는 보통 작은 수 사용.

---

### Q4. 정답: **(B) `"-2 -3"`**

📌 **출제 의도:** **음수의 truncation vs rounding** — `(int) -2.7 = -2` (toward zero), `(int)(-2.7 - 0.5) = -3` (반올림). CED 1.5.A.4의 음수 패턴 적용.

📎 **연계:** **CED 1.5.A.4**: *"Values of type double can be rounded to the nearest integer by (int)(x + 0.5) for non-negative numbers or (int)(x - 0.5) for negative numbers."*

> **핵심 개념: 음수 truncation/rounding**
> - **truncation은 toward zero**: `-2.7 → -2`, `-2.99 → -2` (소수 버림)
> - **음수 반올림**: `(int)(x - 0.5)` (양수와 부호 반대)
>   - `-2.7 - 0.5 = -3.2` → `(int) = -3` (round to -3)
>   - `-2.3 - 0.5 = -2.8` → `(int) = -2` (round to -2)

> **선행 지식:**
> - Java의 `(int)` 캐스팅은 항상 toward zero (음수면 더 큰 정수로)
> - 수학적 floor: `floor(-2.7) = -3`, but `(int)(-2.7) = -2` (다름!)
> - **Math.floor는 Quick Reference 없음** — AP 사용 X

**한 단계씩 추적:**

| 단계 | 식 | 결과 |
|---|---|---|
| 1 | `truncated = (int) -2.7` | toward zero → **-2** |
| 2 | `x - 0.5` | -2.7 - 0.5 = **-3.2** |
| 3 | `(int) -3.2` | toward zero → **-3** |
| 4 | `println(-2 + " " + -3)` | `"-2 -3"` |

**최종 출력: `"-2 -3"`** ✓

**검증:**
- 단순 `(int) -2.7` = -2 (소수부 버림, 부호 보존)
- 반올림: -2.7은 가장 가까운 정수 -3으로 round → 표준 관용구로 -3 유도

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"-2 -2"` | rounded도 -2라고 오해 | (int)(-3.2) = -3 (음수 반올림 적용) |
| **(B) `"-2 -3"`** ✅ | 정답 | truncate=-2, round=-3 |
| (C) `"-3 -3"` | truncate가 floor라고 오해 | (int)는 toward zero, -2.7 → -2 |
| (D) `"-3 -2"` | 두 식 거꾸로 적용 | 정확히 거꾸로 |

> ⚠️ **함정 1:** **`(int)` ≠ `floor`**. `(int)(-2.7) = -2` (toward zero). `floor(-2.7) = -3` (toward -∞). 음수에서 차이 큼.

> ⚠️ **함정 2:** **반올림 부호**. 비음수: `+0.5`, 음수: `-0.5`. 같은 +0.5 쓰면 음수 반올림 잘못됨.

> ⚠️ **함정 3:** **`Math.floor`/`Math.round` 사용 금지**. Quick Reference 없음. 반올림은 `(int)(x ± 0.5)` 관용구 사용.

> 💡 **꿀팁 1:** **CED 1.5.A.4 정확한 인용**: "(int)(x + 0.5) for non-negative numbers or (int)(x - 0.5) for negative numbers". 부호별 다른 식.

> 💡 **꿀팁 2:** **truncation 직관**:
> - 양수: 작은 정수 (3.9 → 3)
> - 음수: 큰 정수 (toward zero) (-3.9 → -3)
> - 0: 그대로

> 💡 **꿀팁 3:** **반올림 일반 패턴**:
> - 양수 `(int)(x + 0.5)`: 0.5 이상이면 위로
> - 음수 `(int)(x - 0.5)`: 절댓값 0.5 이상이면 더 음수로

---

### Q5. 정답: **(A) `1 to 6` (inclusive)**

📌 **출제 의도:** **`Math.random()`의 범위 매핑** — `[0.0, 1.0)` 범위를 임의 정수 범위로 변환. CED 1.11.A.3의 표준 dice roll 패턴.

📎 **연계:** **CED 1.11.A.3**: *"The values returned from Math.random() can be manipulated using arithmetic and casting operators to produce a random int or double in a defined range based on specified criteria."*

> **핵심 개념: random 범위 매핑**
> - `Math.random()` → `[0.0, 1.0)` (0.0 포함, 1.0 제외)
> - `Math.random() * N` → `[0.0, N)` (0.0 포함, N 제외)
> - `(int) (Math.random() * N)` → `0, 1, 2, ..., N-1` (정수 N개)
> - `+ K` → `K, K+1, ..., K+N-1`
>
> **본 문제**: `(int)(random() * 6) + 1` → `0, 1, 2, 3, 4, 5` → `+1` → `1, 2, 3, 4, 5, 6` = **dice roll**

> **선행 지식:**
> - `(int)`로 음수 안 됨 (random은 항상 비음수)
> - 가능한 정수 개수 = `N` (배율의 정수 부분)
> - 시작 = `+ K` (offset)
> - 끝 = K + N - 1

**범위 도출:**

| 단계 | 식 | 범위 |
|---|---|---|
| 1 | `Math.random()` | `[0.0, 1.0)` |
| 2 | `* 6` | `[0.0, 6.0)` |
| 3 | `(int)` | `0, 1, 2, 3, 4, 5` (정수 6개) |
| 4 | `+ 1` | `1, 2, 3, 4, 5, 6` |

**범위: 1 to 6 (inclusive)** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `1 to 6` (inclusive)** ✅ | 정답 | dice roll 패턴 |
| (B) `0 to 6` | +1 잊음 또는 max 잘못 | +1로 시작 1, max 6 |
| (C) `1 to 7` | random()이 1.0 포함이라 오해 | `[0.0, 1.0)` 1.0 미포함 → max 5 (캐스팅 후) |
| (D) `0 to 5` | +1 잊음 | offset +1 적용 |

> ⚠️ **함정 1:** **`Math.random()`의 1.0 미포함**. `[0.0, 1.0)` 반열린 구간. * 6 후 6.0 미포함, (int) 후 5 max.

> ⚠️ **함정 2:** **캐스팅 후 정수 N개**. `(int)(random() * N)` → 0..N-1 정확히 N개. +K로 K..K+N-1.

> ⚠️ **함정 3:** **음수 범위**: `(int)(random() * N) - K` → -K..N-K-1. AP에서 음수 시작 시 +K 대신 -K 사용 가능.

> 💡 **꿀팁 1:** **표준 random 패턴 (CED 1.11.A.3)**:
> - `(int)(Math.random() * N)`: 0..N-1 (N개 정수)
> - `(int)(Math.random() * N) + K`: K..K+N-1
> - 일반: `[lo, hi]` (양 끝 포함) → `(int)(random() * (hi - lo + 1)) + lo`

> 💡 **꿀팁 2:** **유명 예시**:
> - 동전 (0 또는 1): `(int)(random() * 2)`
> - 주사위 (1-6): `(int)(random() * 6) + 1`
> - 1-100: `(int)(random() * 100) + 1`

> 💡 **꿀팁 3:** **double random (`a, b)`)**: `random() * (b - a) + a`. 정수 캐스팅 안 함. 예: `[0.5, 2.5)` → `random() * 2 + 0.5`.

---

### Q6. 정답: **(D) `-2147483648`**

📌 **출제 의도:** **int 오버플로 시 wrap-around** 동작 — `MAX_VALUE + 1 = MIN_VALUE`. 예외 발생 없이 음수로 wrap. CED 1.5.B.3의 핵심.

📎 **연계:** **CED 1.5.B.3**: *"If an expression would evaluate to an int value outside of the allowed range, an integer overflow occurs. The result is an int value in the allowed range but not necessarily the value expected."*

> **핵심 개념: int 오버플로**
> - int 범위: `[Integer.MIN_VALUE, Integer.MAX_VALUE]` = `[-2,147,483,648, 2,147,483,647]`
> - 4바이트 (32비트), 부호 있는 정수
> - 범위 초과 시 **wrap-around** (예외 없음)
>   - `MAX_VALUE + 1 = MIN_VALUE`
>   - `MIN_VALUE - 1 = MAX_VALUE`

> **선행 지식:**
> - C와 달리 Java도 정수 오버플로 시 예외 없음, 그냥 wrap
> - `Integer.MAX_VALUE` = 2³¹ - 1 = 2147483647
> - `Integer.MIN_VALUE` = -2³¹ = -2147483648
> - **CED 1.5.C.1**: long 등 다른 타입 OUT (오버플로 회피용 long 사용 X)

**한 단계씩 추적:**

| 단계 | 식 | 결과 |
|---|---|---|
| 1 | `int max = Integer.MAX_VALUE` | max = 2147483647 |
| 2 | `max + 1` | overflow → wrap to MIN_VALUE |
| 3 | `int result = -2147483648` | result = -2147483648 |
| 4 | `println(-2147483648)` | `-2147483648` |

**최종 출력: `-2147483648`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `2147483648` | int 범위 초과 값 그대로 표시라 오해 | int 범위 초과 → wrap, 그 값 자체가 저장되지 않음 |
| (B) `0` | wrap이 0으로 간다고 오해 | wrap은 MIN_VALUE (-2³¹)로 |
| (C) Runtime error (`ArithmeticException`) | 오버플로 시 예외 발생이라 오해 | Java는 int 오버플로 예외 없음 |
| **(D) `-2147483648`** ✅ | 정답 | MAX+1 = MIN |

> ⚠️ **함정 1:** **오버플로 = 예외 없음**. C/Python과 다른 Java 동작. 정상적으로 계속 실행되지만 결과가 예상과 다름.

> ⚠️ **함정 2:** **MAX_VALUE 정확한 값**. AP에서 정확한 숫자 외울 필요는 없으나 "31비트 양수 최댓값"이라는 개념은 알아야.

> ⚠️ **함정 3:** **AP는 long 출제 안 함**. 일반 프로그래밍에서는 `long`으로 회피하지만, **CED 1.5.C.1 EXCLUSION**으로 AP 미출제.

> 💡 **꿀팁 1:** **wrap-around 양방향**:
> - MAX + 1 = MIN
> - MIN - 1 = MAX
> - 같은 원리로 큰 곱셈/덧셈도 wrap 가능

> 💡 **꿀팁 2:** **오버플로 감지 어려움**: 결과가 음수가 되면 의심해볼 만. 단, 의도적인 음수 결과와 구별 어려움.

> 💡 **꿀팁 3:** **AP에서 오버플로 유형 문제**:
> - `MAX_VALUE + 1`
> - `MIN_VALUE - 1`
> - `MAX_VALUE * 2` (음수)
> - 과 같은 패턴 출제

---

## 종합 정리

### 1.5 Casting 핵심
```java
double x = 7.8;
int truncated = (int) x;             // 7 (소수부 버림)
int rounded_pos = (int)(x + 0.5);    // 8 (비음수 반올림)
int rounded_neg = (int)(-x - 0.5);   // -8 (음수 반올림)
double upcast = (double) 5;          // 5.0 (자동도 가능)
```

### 1.5.B 범위 + 오버플로
```java
Integer.MAX_VALUE  // 2,147,483,647
Integer.MIN_VALUE  // -2,147,483,648
Integer.MAX_VALUE + 1   // -2,147,483,648 (wrap)
Integer.MIN_VALUE - 1   // 2,147,483,647 (wrap)
```

### 1.11 Math 메서드 5개 (Quick Reference)
```java
Math.abs(int)         → int
Math.abs(double)      → double
Math.pow(d, d)        → double  // 거듭제곱
Math.sqrt(d)          → double  // 제곱근
Math.random()         → double  // [0.0, 1.0)
```

### Math.random() 범위 매핑 (CED 1.11.A.3)
```java
(int)(Math.random() * N)          // 0..N-1
(int)(Math.random() * N) + K      // K..K+N-1
// 일반: [lo, hi] inclusive
(int)(Math.random() * (hi - lo + 1)) + lo
```

### EXCLUSION 재확인
- **`Math.min`, `Math.max`, `Math.floor`, `Math.ceil`, `Math.round` OUT** — Quick Reference 없음
- **`long`, `short`, `float` OUT** (CED 1.5.C.1)
- **다른 특수 소수 타입 OUT** (BigDecimal 등)
- **정수 오버플로는 예외 없음**, wrap-around로 처리
