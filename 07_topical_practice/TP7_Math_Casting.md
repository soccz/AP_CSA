# TP7: Math + Casting + Overflow (보강 세트)

> **CED 2025-26 토픽**: 1.5 Casting and Range, 1.11 Math Class
> **문항 수**: 6 MCQ (Medium-Hard)
> **시간 권장**: 15분
> **목표 정답률**: 80% 이상

---

## CED 범위 준수 사항

- **1.5.A.1**: 캐스팅 연산자 `(int)`, `(double)` 만 사용 가능
- **1.5.A.2**: `(int)` 캐스팅은 **소수부 절사(truncation)** — 반올림 아님
- **1.5.A.3**: `int → double` 자동 승격 (widening)
- **1.5.A.4**: `(int)(x + 0.5)`로 비음수 반올림, `(int)(x - 0.5)`로 음수 반올림
- **1.5.B.1**: `Integer.MIN_VALUE`, `Integer.MAX_VALUE`
- **1.5.B.3**: int 오버플로 시 wrap-around (예외 없음)
- **1.11.A.2**: Math 메서드 — `abs(int)`, `abs(double)`, `pow`, `sqrt`, `random` (Quick Reference 명시 5개)
- **1.11.A.3**: `Math.random()`은 `[0.0, 1.0)` 반환, 산술 + 캐스팅으로 임의 범위 정수/실수 생성

- **EXCLUSION**:
  - **`Math.min`, `Math.max`, `Math.floor`, `Math.ceil`, `Math.round` 모두 OUT** (Quick Reference에 없음)
  - `long`, `short`, `float` 등 다른 수치 타입 OUT (CED 1.5.C.1)
  - 다른 특수 소수 타입 OUT (BigDecimal 등)

---

## 출제 토픽 분포

| # | 토픽 | 핵심 |
|---|------|------|
| 1 | 1.5.A.1+1.5.A.4 — `(int)` 절사 + 반올림 | truncation vs (int)(x+0.5) |
| 2 | 1.11.A.2 — `Math.abs` 두 오버로드 | int + double |
| 3 | 1.11.A.2 — `Math.pow` + (int) 캐스팅 | double 결과를 int로 |
| 4 | 1.5.A.4 — 음수 반올림 패턴 | `(int)(x - 0.5)` |
| 5 | 1.11.A.3 — `Math.random()` 범위 매핑 | 1-6 dice roll |
| 6 | 1.5.B.3 — int 오버플로 wrap-around | MAX + 1 = MIN |

**답안 분포**: A:2 / B:2 / C:1 / D:1

---

## 시험 안내

**Directions**: 다음 각 문항에 대해 가장 적절한 답을 고르시오.

---

### 1. [CED 1.5.A · Hard]

다음 코드의 출력은? (CED 1.5.A.2: `(int)` 캐스팅은 소수부 절사 / CED 1.5.A.4: `(int)(x + 0.5)`는 반올림)

```java
double x = 7.8;
int y = (int) x;
double z = (int) (x + 0.5);
System.out.println(y + " " + z);
```

(A) `"7 8.0"`
(B) `"8 8.0"`
(C) `"7 7.0"`
(D) `"8 7.0"`

---

### 2. [CED 1.11.A.2 · Medium]

다음 코드의 출력은? (CED 1.11.A.2: `Math.abs(int)`와 `Math.abs(double)`은 오버로드된 두 메서드)

```java
int a = -15;
double b = -3.7;
System.out.println(Math.abs(a) + " " + Math.abs(b));
```

(A) `"-15 -3.7"`
(B) `"15 -3.7"`
(C) `"15 3.7"`
(D) `"-15 3.7"`

---

### 3. [CED 1.11.A.2 + 1.5.A.1 · Hard]

다음 코드의 출력은? (CED 1.11.A.2: `Math.pow`는 `double` 반환)

```java
int base = 2;
int exp = 5;
int result = (int) Math.pow(base, exp);
System.out.println(result);
```

(A) `25`
(B) `32`
(C) `10`
(D) Compile-time error

---

### 4. [CED 1.5.A.4 · Hard]

다음 코드의 출력은? (CED 1.5.A.4: `(int)(x - 0.5)`는 **음수**의 반올림 표준 관용구)

```java
double x = -2.7;
int truncated = (int) x;
int rounded = (int) (x - 0.5);
System.out.println(truncated + " " + rounded);
```

(A) `"-2 -2"`
(B) `"-2 -3"`
(C) `"-3 -3"`
(D) `"-3 -2"`

---

### 5. [CED 1.11.A.3 · Hard]

다음 식이 생성하는 정수의 **가능한 범위**(양 끝 모두 포함)는? (CED 1.11.A.3: Math.random() 범위 매핑)

```java
int x = (int) (Math.random() * 6) + 1;
```

(A) `1 to 6` (inclusive)
(B) `0 to 6`
(C) `1 to 7`
(D) `0 to 5`

---

### 6. [CED 1.5.B.3 · Hard]

다음 코드의 출력은? (CED 1.5.B.3: int 오버플로 시 wrap-around)

```java
int max = Integer.MAX_VALUE;   // 2,147,483,647
int result = max + 1;
System.out.println(result);
```

(A) `2147483648`
(B) `0`
(C) Runtime error (`ArithmeticException`)
(D) `-2147483648`

---

**END OF TP7**
