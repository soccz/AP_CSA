# TP4: Recursion 심화 — 해설집

> **CED 2025-26 토픽**: 4.16 Recursion (트레이싱), 4.17.A Recursive String/Array/ArrayList Traversal
> **답안 분포**: A:2 / B:2 / C:2 / D:2

---

## 정답 요약

| # | 정답 | CED 토픽 | 핵심 |
|---|------|---------|------|
| 1 | **A** `14` | 4.16 자릿수 합 | 7+4+2+1=14 |
| 2 | **C** `105` | 4.16 곱셈 (n-2 step) | 7·5·3·1=105 |
| 3 | **B** `"RATS"` | 4.17.A String 역순 | substring + 결합 |
| 4 | **D** `3` | 4.17.A 문자 카운트 | "banana"의 'a' 3개 |
| 5 | **C** `23` | 4.17.A 배열 합 | 3+1+4+1+5+9=23 |
| 6 | **A** `8` | 4.16 Fibonacci | f(6)=8 |
| 7 | **D** `15` | 4.16+2.12 호출 수 | T(5)=1+T(4)+T(3)=15 |
| 8 | **B** `4` | 4.17.A ArrayList 카운트 | 양수 4개 |

---

## Section I: 문제별 상세 해설

---

### Q1. 정답: **(A) `14`**

📌 **출제 의도:** **자릿수 추출 + 재귀 누적** 패턴 (CED 2.9.A.1 "identify the individual digits in an integer"의 재귀 변형). `n % 10`으로 마지막 자리, `n / 10`으로 나머지 추출 후 재귀.

📎 **연계:** **CED 4.16.A.1**: *"A recursive method is a method that calls itself. Recursive methods contain at least one base case, which halts the recursion, and at least one recursive call."* + **CED 2.9** 표준 알고리즘 (digits).

> **핵심 개념: 자릿수 추출 패턴**
> - `n % 10` — 마지막 자리 추출 (1의 자리)
> - `n / 10` — 마지막 자리 제외한 나머지 (정수 나눗셈)
> - **base case**: `n == 0` → return 0 (더 이상 자리 없음)
> - **재귀**: `(마지막 자리) + (나머지 자리들의 합)`

> **선행 지식:**
> - 정수 나눗셈: `7421 / 10 = 742` (소수점 절사)
> - 모듈로: `7421 % 10 = 1`
> - 재귀는 base case 도달 후 unwinding으로 결과 누적

**호출 스택 트리:**

```
sumDigits(7421)  → 1 + sumDigits(742)
  sumDigits(742) → 2 + sumDigits(74)
    sumDigits(74) → 4 + sumDigits(7)
      sumDigits(7) → 7 + sumDigits(0)
        sumDigits(0) → return 0  (base case)
```

**Unwinding (반환):**

| 호출 | n | n%10 | sumDigits(n/10) | 반환 |
|---|---|---|---|---|
| 5 | 0 | — | — | **0** (base) |
| 4 | 7 | 7 | 0 | 7+0 = **7** |
| 3 | 74 | 4 | 7 | 4+7 = **11** |
| 2 | 742 | 2 | 11 | 2+11 = **13** |
| 1 | 7421 | 1 | 13 | 1+13 = **14** |

**최종: 14** ✓

**검증:** 7+4+2+1 = 14 ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `14`** ✅ | 정답 | 7+4+2+1 = 14 |
| (B) `21` | 한 자리 추가 카운트 | 7421의 자리: 7,4,2,1 (4자리). 합 14 |
| (C) `4` | 자릿수 개수(4)를 답으로 | sumDigits는 합, 개수는 다른 메서드 |
| (D) `7421` | base case 누락이라 오해 | base case 정상 → 14 |

> ⚠️ **함정 1:** **n % 10 vs n / 10 혼동**. `% 10` = 마지막 자리(값), `/ 10` = 마지막 제외한 수.

> ⚠️ **함정 2:** **base case 위치**. `if (n == 0) return 0;`이 함수 맨 위. 누락 시 무한 재귀 → StackOverflowError.

> ⚠️ **함정 3:** **순서 무관**. `n % 10 + sumDigits(n/10)`이든 `sumDigits(n/10) + n%10`이든 결과 같음 (덧셈 교환적).

> 💡 **꿀팁 1:** **재귀 표준 골격 (자릿수 처리)**:
> ```java
> if (n == 0) return /* 항등원 */;
> return /* 작업(n%10) */ + recurse(n/10);
> ```

> 💡 **꿀팁 2:** **합의 항등원 = 0, 곱의 항등원 = 1**. base case의 반환값은 작업에 따라 다름.

> 💡 **꿀팁 3:** **재귀 vs 반복**: 같은 결과를 while로도 구현 가능 (CED 4.16.A.3). 학생은 재귀 코드 트레이싱만 출제 (작성은 4.16 EXCLUSION).

---

### Q2. 정답: **(C) `105`**

📌 **출제 의도:** **n-2 step 감소 재귀** + 곱셈 누적 패턴. base case가 `n <= 1`로 두 케이스(0, 1) 모두 1 반환 — 홀수/짝수 시작 모두 안전하게 종료.

📎 **연계:** **CED 4.16.A.2**: *"Each recursive call has its own set of local variables, including the parameters. Parameter values capture the progress of a recursive process."* — n이 매 호출마다 -2씩 감소.

> **핵심 개념: 비균일 step 재귀**
> - 일반적인 재귀는 `n - 1`로 감소
> - 본 메서드는 **`n - 2`** 로 감소 → 홀수만 또는 짝수만 방문
> - 7→5→3→1 (홀수만) 또는 6→4→2→0 (짝수만)
> - base case `n <= 1`로 1과 0 모두 종료

> **선행 지식:**
> - 곱의 항등원 = 1 → base에서 1 반환
> - n=7부터 시작하면 7, 5, 3, 1로 4번 호출
> - 결과: 7 × 5 × 3 × 1 = 105 (홀수 곱)

**호출 스택 트리:**

```
mystery(7)  → 7 * mystery(5)
  mystery(5) → 5 * mystery(3)
    mystery(3) → 3 * mystery(1)
      mystery(1) → return 1  (base, n<=1)
```

**Unwinding:**

| 호출 | n | mystery(n-2) | 반환 |
|---|---|---|---|
| 4 | 1 | — | **1** (base) |
| 3 | 3 | 1 | 3·1 = **3** |
| 2 | 5 | 3 | 5·3 = **15** |
| 1 | 7 | 15 | 7·15 = **105** |

**최종: 105** ✓

**검증:** 7·5·3·1 = 105 ✓ (이는 7의 "double factorial" 또는 7!!)

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `35` | 7·5만 계산 | 추가 재귀 단계(3, 1) 무시 |
| (B) `5040` | 7! 일반 factorial | 본 메서드는 n-2 step, 모든 정수 곱 아님 |
| **(C) `105`** ✅ | 정답 | 7·5·3·1 = 105 (double factorial of 7) |
| (D) `21` | 7+5+3+...+1 같은 합으로 오해 | 본 메서드는 곱 (`*`), 합 아님 |

> ⚠️ **함정 1:** **step 크기 무시**. `n - 1`로 가정해 7→6→5→...→1 (factorial)로 계산 → 5040. 본 메서드는 `n - 2`.

> ⚠️ **함정 2:** **base case 두 케이스**. `n <= 1`이므로 n=0과 n=1 모두 base. n=8부터 시작하면 8→6→4→2→0에서 종료, 1 반환.

> ⚠️ **함정 3:** **곱 vs 합**. `*` 연산자 정확히 식별. 본 메서드는 곱셈 누적 (factorial 변형).

> 💡 **꿀팁 1:** **base case가 0 vs 1 vs n<=1**:
> - 0만: 짝수 step에서 종료
> - 1만: 홀수 step에서 종료
> - `n <= 1`: 양쪽 모두 안전

> 💡 **꿀팁 2:** **Double factorial (n!!)**: `7!! = 7·5·3·1 = 105`, `8!! = 8·6·4·2 = 384`. 본 메서드는 정확히 double factorial.

> 💡 **꿀팁 3:** **호출 횟수**: n=7 → 4 호출 (`(n+1)/2` 정도). step이 클수록 재귀 깊이 줄어듦.

---

### Q3. 정답: **(B) `"RATS"`**

📌 **출제 의도:** **재귀로 String 역순 생성** (CED 4.17.A.1: *"Recursion can be used to traverse String objects, arrays, and ArrayList objects"*). substring으로 String을 분해하고 재귀 + 단일 문자 결합으로 역순 생성.

📎 **연계:** **CED 4.17.A** + **CED 1.15** String Manipulation. **EXCLUSION**: `s.charAt()` 사용 금지 (Quick Reference에 없음). 단일 문자는 `s.substring(i, i+1)`.

> **핵심 개념: 재귀 String 역순 패턴**
> ```
> reverse(s) = reverse(s 빼고 첫 문자) + (첫 문자)
> base: 길이 0 또는 1이면 그대로 반환
> ```
> - 재귀로 뒷부분을 먼저 역순 → 그 뒤에 첫 문자 추가
> - 결과: 전체 역순 String

> **선행 지식:**
> - `s.substring(0, 1)` — 첫 문자 (CED 1.15.B.3 단일 문자 추출 관용구)
> - `s.substring(1)` — 첫 문자 제외한 나머지 (CED 1.15.B.2: substring(int from))
> - String 결합 `+` (CED 1.15.A.4)
> - **`charAt` 사용 금지** — Quick Reference에 없음

**호출 스택 트리:**

```
reverse("STAR")    → reverse("TAR") + "S"
  reverse("TAR")  → reverse("AR") + "T"
    reverse("AR") → reverse("R") + "A"
      reverse("R") → return "R"  (base, length<=1)
```

**Unwinding:**

| 호출 | s | reverse(s.sub(1)) | 반환 |
|---|---|---|---|
| 4 | "R" | — | **"R"** (base) |
| 3 | "AR" | "R" | "R"+"A" = **"RA"** |
| 2 | "TAR" | "RA" | "RA"+"T" = **"RAT"** |
| 1 | "STAR" | "RAT" | "RAT"+"S" = **"RATS"** |

**최종: "RATS"** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"STAR"` | 재귀가 동작 안 한다고 오해 (원본 그대로) | 재귀 정상 동작 → 역순 생성 |
| **(B) `"RATS"`** ✅ | 정답 | "STAR" 역순 |
| (C) `"TARS"` | 첫 문자 't'와 's' 위치 헷갈림 | 정확한 역순은 "RATS" (S-T-A-R → R-A-T-S) |
| (D) `"ARTS"` | 안내 문자 순서 헷갈림 | "STAR"의 정확한 역순은 "RATS" |

> ⚠️ **함정 1:** **`reverse(s.substring(1)) + s.substring(0, 1)` vs `s.substring(0, 1) + reverse(s.substring(1))`**. 후자라면 원본 그대로 (역순 안 됨). 본 코드는 **재귀 결과가 먼저** + **첫 문자 뒤**.

> ⚠️ **함정 2:** **substring(0, 1) vs charAt(0)**. AP는 `substring(0, 1)` 사용 (Quick Reference 명시). `charAt`은 OUT.

> ⚠️ **함정 3:** **base case `length <= 1`**. 빈 String("")이나 한 글자 String은 그대로 반환. 만약 `length == 1`만 base로 쓰면 빈 String에서 무한 재귀 (substring(1)이 또 길이 0).

> 💡 **꿀팁 1:** **재귀 String 처리 패턴**:
> ```
> base: 길이 0 또는 1이면 그대로
> recursive: 첫 문자 + recurse(나머지) — 정방향 처리
>            recurse(나머지) + 첫 문자 — 역방향 처리
> ```

> 💡 **꿀팁 2:** **CED 4.17.A.1 String 순회**: 재귀 또는 반복으로 String 모든 문자 처리 가능. 두 방식 동등 (4.16.A.3).

> 💡 **꿀팁 3:** **검산법**: 결과의 첫 문자 = 원본의 마지막 문자, 결과의 마지막 문자 = 원본의 첫 문자. "STAR" → "RATS": R(원본 4번)…S(원본 1번) ✓

---

### Q4. 정답: **(D) `3`**

📌 **출제 의도:** **재귀로 String 내 특정 문자 카운트** + 단일 문자 추출 관용구. CED 1.15.B.3 명시 패턴 사용 + 재귀 누적 + `.equals()` String 비교.

📎 **연계:** **CED 4.17.A.1** + **CED 1.15.B.3**: *"A string identical to the single element substring at position index can be created by calling substring(index, index + 1)."* + **CED 1.15.B.2** equals.

> **핵심 개념: 재귀 카운트 패턴**
> ```
> 1. base: 빈 String이면 0
> 2. rest = recurse(첫 문자 제외)
> 3. 첫 문자 = target?
>    ✓: return 1 + rest
>    ✗: return rest
> ```
> - **`substring(0, 1)`** — 첫 문자 (CED 1.15.B.3)
> - **`.equals()`** — String 비교 (`==` 금지)

> **선행 지식:**
> - "banana"의 'a' 위치: index 1, 3, 5 → 3개
> - **`charAt` 사용 금지** — Quick Reference에 없음
> - target도 String 형태 (single character String)

**호출 스택 트리 (`countChar("banana", "a")`):**

```
countChar("banana", "a")  → "b"!="a" → return countChar("anana", "a")
  countChar("anana", "a") → "a"="a" → return 1 + countChar("nana", "a")
    countChar("nana", "a") → "n"!="a" → return countChar("ana", "a")
      countChar("ana", "a") → "a"="a" → return 1 + countChar("na", "a")
        countChar("na", "a") → "n"!="a" → return countChar("a", "a")
          countChar("a", "a") → "a"="a" → return 1 + countChar("", "a")
            countChar("", "a") → length=0 → return 0  (base)
```

**Unwinding:**

| 호출 | s | 첫 문자 | == "a"? | rest | 반환 |
|---|---|---|---|---|---|
| 7 | "" | — | — | — | **0** (base) |
| 6 | "a" | "a" | ✓ | 0 | 1+0 = **1** |
| 5 | "na" | "n" | ✗ | 1 | **1** |
| 4 | "ana" | "a" | ✓ | 1 | 1+1 = **2** |
| 3 | "nana" | "n" | ✗ | 2 | **2** |
| 2 | "anana" | "a" | ✓ | 2 | 1+2 = **3** |
| 1 | "banana" | "b" | ✗ | 3 | **3** |

**최종: 3** ✓

**검증:** "banana"의 'a': b**a**n**a**n**a** → 3개 ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `1` | 첫 일치 후 종료라고 오해 | 본 코드는 모든 위치 검사 (return은 누적값) |
| (B) `6` | "banana" 길이 카운트 | 메서드는 카운트, 길이 아님 |
| (C) `2` | 일부 'a' 빠뜨림 | "banana"의 'a' 정확히 3개 |
| **(D) `3`** ✅ | 정답 | b**a**n**a**n**a** = 3 |

> ⚠️ **함정 1:** **`==` vs `.equals()` String 비교**. `s.substring(0, 1) == c`는 거의 항상 false (참조 비교). 반드시 `.equals()`.

> ⚠️ **함정 2:** **`charAt` 사용 시도**. `s.charAt(0)`은 Quick Reference에 없음 → AP 미출제. 항상 `s.substring(0, 1)`.

> ⚠️ **함정 3:** **base case `length() == 0`**. 빈 String에서 종료. 만약 `length() == 1`만 base로 쓰면 base 직전 호출의 첫 문자 검사 누락 → 1 부족.

> 💡 **꿀팁 1:** **재귀 카운트 표준 골격**:
> ```
> if (base 조건) return 0;
> int rest = recurse(작아진 입력);
> if (현재 원소가 조건 만족) return 1 + rest;
> return rest;
> ```

> 💡 **꿀팁 2:** **Quick Reference String 메서드 (CED 1.15.B.2)**: `length`, `substring(int, int)`, `substring(int)`, `indexOf`, `equals`, `compareTo`, `split`. 다른 메서드(`charAt`, `toUpperCase` 등)는 OUT.

> 💡 **꿀팁 3:** **단일 문자 추출 관용구 (CED 1.15.B.3)**: `s.substring(i, i + 1)` — i번째 문자를 String으로 반환. AP의 표준 표현.

---

### Q5. 정답: **(C) `23`**

📌 **출제 의도:** **재귀로 배열 합 계산** (CED 4.17.A.1: array 순회). 인덱스 기반 재귀 패턴 (`idx + 1`로 진행).

📎 **연계:** **CED 4.17.A.1**: *"Recursion can be used to traverse String objects, arrays, and ArrayList objects."* + **CED 2.9** standard algorithm (sum/average).

> **핵심 개념: 재귀 배열 순회 패턴**
> ```
> base: idx >= arr.length → return 0
> recursive: arr[idx] + recurse(idx + 1)
> ```
> - 인덱스를 매개변수로 전달
> - 매 호출마다 idx 증가 → 배열 끝 도달 시 base
> - 합의 항등원 = 0

> **선행 지식:**
> - `arr.length` — 배열 크기
> - 재귀 = 반복으로도 동등하게 구현 가능 (CED 4.16.A.3)
> - 본 메서드는 정방향 순회 (idx 증가)

**호출 스택 트리 (`sumArr({3,1,4,1,5,9}, 0)`):**

```
sumArr(0) → 3 + sumArr(1)
  sumArr(1) → 1 + sumArr(2)
    sumArr(2) → 4 + sumArr(3)
      sumArr(3) → 1 + sumArr(4)
        sumArr(4) → 5 + sumArr(5)
          sumArr(5) → 9 + sumArr(6)
            sumArr(6) → idx>=length → return 0  (base)
```

**Unwinding:**

| 호출 | idx | arr[idx] | rest | 반환 |
|---|---|---|---|---|
| 7 | 6 | — | — | **0** (base) |
| 6 | 5 | 9 | 0 | 9+0 = **9** |
| 5 | 4 | 5 | 9 | 5+9 = **14** |
| 4 | 3 | 1 | 14 | 1+14 = **15** |
| 3 | 2 | 4 | 15 | 4+15 = **19** |
| 2 | 1 | 1 | 19 | 1+19 = **20** |
| 1 | 0 | 3 | 20 | 3+20 = **23** |

**최종: 23** ✓

**검증:** 3+1+4+1+5+9 = 23 ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `13` | 일부 원소 빠뜨림 | 모든 6 원소 합 = 23 |
| (B) `9` | 마지막 원소만 본 경우 | 모든 원소 누적 |
| **(C) `23`** ✅ | 정답 | 3+1+4+1+5+9 = 23 |
| (D) `3` | 첫 원소만 본 경우 | 모든 원소 누적 |

> ⚠️ **함정 1:** **base case 인덱스 비교**. `idx >= arr.length` (또는 `idx == arr.length`). `idx > arr.length`로 쓰면 마지막 원소 처리 후에도 한 번 더 호출 → IndexOutOfBoundsException.

> ⚠️ **함정 2:** **idx 진행 방향**. `idx + 1` (정방향) vs `idx - 1` (역방향). 역방향이면 base가 `idx < 0`. 본 코드는 정방향.

> ⚠️ **함정 3:** **인덱스 매개변수 vs 배열 자르기**. 본 코드는 인덱스 전달 (효율적). 다른 패턴: `subarray` 만들기 (비효율적, AP에서 안 씀).

> 💡 **꿀팁 1:** **인덱스 기반 재귀 골격**:
> ```
> if (idx >= arr.length) return 0;
> return /* 작업(arr[idx]) */ + recurse(arr, idx + 1);
> ```

> 💡 **꿀팁 2:** **재귀 호출 횟수**: n원소 → n+1 호출 (base case 포함). 본 문제: 6 + 1 = 7 호출.

> 💡 **꿀팁 3:** **재귀 vs 반복 비교**:
> - 재귀: 코드 짧음, stack frame 사용
> - 반복: stack 안 씀, 명시적 변수 관리
> - **결과는 동일** (CED 4.16.A.3)

---

### Q6. 정답: **(A) `8`**

📌 **출제 의도:** **다중 재귀 호출** (한 호출에서 자기 자신을 두 번 부름) — Fibonacci 수열의 정의 그대로. 트리 구조의 재귀 호출을 추적할 수 있는지 테스트.

📎 **연계:** **CED 4.16.A.1** 재귀 메서드 정의. 다중 호출은 단순 재귀(self-call 한 번)보다 분석이 복잡 — 호출 트리 그리기가 핵심.

> **핵심 개념: 다중 재귀 호출 (Fibonacci)**
> - `f(n) = f(n-1) + f(n-2)`
> - 정의: `f(0) = 0, f(1) = 1`
> - 본 코드는 정확히 Fibonacci 정의 구현
> - 호출 트리는 **이진 트리 형태** (한 노드에서 두 자식)

> **선행 지식:**
> - Fibonacci 시퀀스: 0, 1, 1, 2, 3, 5, 8, 13, 21, ...
> - f(n)을 계산하려면 f(n-1)과 f(n-2) 값 필요 → 재귀 자연스러움
> - 시간 복잡도: O(2^n) (지수적 — 비효율적이지만 트레이싱은 가능)

**Fibonacci 값 표:**

| n | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|---|---|
| f(n) | 0 | 1 | 1 | 2 | 3 | 5 | **8** | 13 |

**`f(6)` 계산 (top-down):**

```
f(6) = f(5) + f(4) = 5 + 3 = 8
  f(5) = f(4) + f(3) = 3 + 2 = 5
    f(4) = f(3) + f(2) = 2 + 1 = 3
      f(3) = f(2) + f(1) = 1 + 1 = 2
        f(2) = f(1) + f(0) = 1 + 0 = 1
          f(1) = 1 (base)
          f(0) = 0 (base)
```

**최종: f(6) = 8** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `8`** ✅ | 정답 | f(6) = 8 (Fibonacci 7번째) |
| (B) `5` | f(5) 값 | f(6) = f(5) + f(4) = 5 + 3 |
| (C) `13` | f(7) 값 | n=7이면 13, n=6은 8 |
| (D) `21` | f(8) 값 | 한 단계 더 멀리 |

> ⚠️ **함정 1:** **Fibonacci 인덱싱**. f(0)부터 시작. f(1)=1이지만 f(2)도 1. 인덱스 헷갈리면 ±1 오류.

> ⚠️ **함정 2:** **base case `n <= 1`**. n=0과 n=1 모두 base로 처리. 만약 `n == 1`만 base로 두면 f(0)에서 무한 재귀.

> ⚠️ **함정 3:** **다중 재귀 = 호출 폭발**. f(6)은 시각적으로 작아 보이지만 실제 호출 수는 25회 (Q7 참조). 시간 복잡도 O(2^n).

> 💡 **꿀팁 1:** **Fibonacci 외우기**: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ...

> 💡 **꿀팁 2:** **재귀 트리 그리기**: 다중 재귀는 트리 구조. 같은 값(f(2) 등)이 **여러 번 중복 계산**됨. 메모이제이션으로 최적화 가능 (AP 출제 안 됨).

> 💡 **꿀팁 3:** **다중 재귀 vs 단순 재귀**: 단순 재귀는 자기 자신 1회 호출 (선형 재귀, O(n) 호출), 다중 재귀는 2회 이상 (지수적 호출).

---

### Q7. 정답: **(D) `15`**

📌 **출제 의도:** **다중 재귀의 호출 횟수** 분석 — Fibonacci 같은 함수의 호출 트리 크기 계산. CED 2.12 statement execution count + 재귀 트리 분석 능력.

📎 **연계:** **CED 4.16.A.1** 재귀 + **CED 2.12.A.1** 실행 횟수 분석. 다중 재귀의 비효율성을 정량적으로 평가.

> **핵심 개념: 호출 횟수 점화식**
> - `T(n)` = `f(n)` 메서드의 총 호출 횟수
> - **base**: T(0) = 1, T(1) = 1 (자기 자신 1번 호출)
> - **recursive**: T(n) = 1 + T(n-1) + T(n-2)  (자기 1번 + 두 재귀 호출)
> - n과 함께 지수적으로 증가

> **선행 지식:**
> - 호출 트리 = 이진 트리
> - 호출 트리의 **노드 수** = 호출 횟수
> - Fibonacci 호출 횟수 점화식 = `2*F(n+1) - 1` (별칭 공식)

**`T(n)` 계산:**

| n | T(n) | 계산 |
|---|---|---|
| 0 | 1 | base 호출 |
| 1 | 1 | base 호출 |
| 2 | 1 + T(1) + T(0) = 1 + 1 + 1 | **3** |
| 3 | 1 + T(2) + T(1) = 1 + 3 + 1 | **5** |
| 4 | 1 + T(3) + T(2) = 1 + 5 + 3 | **9** |
| 5 | 1 + T(4) + T(3) = 1 + 9 + 5 | **15** |

**최종: T(5) = 15** ✓

**호출 트리 (`f(5)`):**

```
f(5)                                  ← 1
├── f(4)                              ← 2
│   ├── f(3)                          ← 3
│   │   ├── f(2)                      ← 4
│   │   │   ├── f(1) [base]           ← 5
│   │   │   └── f(0) [base]           ← 6
│   │   └── f(1) [base]               ← 7
│   └── f(2)                          ← 8
│       ├── f(1) [base]               ← 9
│       └── f(0) [base]               ← 10
└── f(3)                              ← 11
    ├── f(2)                          ← 12
    │   ├── f(1) [base]               ← 13
    │   └── f(0) [base]               ← 14
    └── f(1) [base]                   ← 15
```

총 노드 = **15** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `5` | f(5) 결과값과 혼동 | f(5)=5는 반환값, 호출 수는 다름 |
| (B) `8` | f(6) 값 또는 일부 카운트 | 정확한 호출 수는 15 |
| (C) `9` | T(4) 값 | 한 단계 짧음 |
| **(D) `15`** ✅ | 정답 | T(5) = 1 + 9 + 5 = 15 |

> ⚠️ **함정 1:** **결과값 vs 호출 수 혼동**. f(5)는 결과 5를 반환하지만 그 과정에서 15번 호출. 두 개념 분리.

> ⚠️ **함정 2:** **base case도 호출 카운트**. `f(0)`이나 `f(1)`이 진입 후 즉시 return해도 **호출 자체는 1회**.

> ⚠️ **함정 3:** **중복 계산**. 같은 인자(예: f(2))가 트리의 여러 위치에서 중복 호출. 그래도 각 호출은 별개로 카운트.

> 💡 **꿀팁 1:** **Fibonacci 호출 수 빠른 공식**: T(n) = 2·f(n+1) - 1. 예: T(5) = 2·f(6) - 1 = 2·8 - 1 = 15 ✓.

> 💡 **꿀팁 2:** **재귀 트리 그리기 정석**: 위에서 아래로 들여쓰기. 각 노드가 호출 1회. 잎(leaf)은 base case.

> 💡 **꿀팁 3:** **다중 재귀의 비효율성**: T(n)이 지수적 증가. n=10이면 177회, n=20이면 21,891회. 메모이제이션이나 반복형으로 O(n) 가능 (AP 출제 X).

---

### Q8. 정답: **(B) `4`**

📌 **출제 의도:** **재귀로 ArrayList 순회 + 조건부 카운트** (CED 4.17.A.1: ArrayList 순회). 인덱스 기반 재귀 + filter 조건 + 누적 패턴.

📎 **연계:** **CED 4.17.A.1** + **CED 4.8** ArrayList 6대 메서드 (`get`, `size`만 사용). 재귀 트레이싱 + ArrayList 조작.

> **핵심 개념: 재귀 ArrayList 카운트**
> ```
> base: idx >= list.size() → return 0
> rest = recurse(idx + 1)
> if (조건(list.get(idx))) return 1 + rest
> return rest
> ```
> - **`list.get(idx)`** — i번 원소 (CED 4.8 6대 메서드)
> - **`list.size()`** — 크기
> - 양수 조건: `> 0` (strict)

> **선행 지식:**
> - **`list.contains` 사용 금지** — Quick Reference에 없음
> - autoboxing/unboxing: `list.get(idx)`는 `Integer` 반환, `> 0` 비교 시 자동 unbox
> - ArrayList.size()는 메서드 (괄호 필수, length 아님)

**입력 데이터:**

```
nums = [3, -1, 5, -2, 4, -3, 7]   (size=7)
양수: 3, 5, 4, 7 → 4개
음수: -1, -2, -3 → 3개
```

**호출 스택 트리:**

```
countPositive(nums, 0)  → 3>0 ✓ → return 1 + countPositive(nums, 1)
  countPositive(nums, 1)  → -1>0 ✗ → return countPositive(nums, 2)
    countPositive(nums, 2)  → 5>0 ✓ → return 1 + countPositive(nums, 3)
      countPositive(nums, 3)  → -2>0 ✗ → return countPositive(nums, 4)
        countPositive(nums, 4)  → 4>0 ✓ → return 1 + countPositive(nums, 5)
          countPositive(nums, 5)  → -3>0 ✗ → return countPositive(nums, 6)
            countPositive(nums, 6)  → 7>0 ✓ → return 1 + countPositive(nums, 7)
              countPositive(nums, 7) → idx>=size → return 0  (base)
```

**Unwinding:**

| 호출 | idx | list.get(idx) | > 0? | rest | 반환 |
|---|---|---|---|---|---|
| 8 | 7 | — | — | — | **0** (base) |
| 7 | 6 | 7 | ✓ | 0 | 1+0 = **1** |
| 6 | 5 | -3 | ✗ | 1 | **1** |
| 5 | 4 | 4 | ✓ | 1 | 1+1 = **2** |
| 4 | 3 | -2 | ✗ | 2 | **2** |
| 3 | 2 | 5 | ✓ | 2 | 1+2 = **3** |
| 2 | 1 | -1 | ✗ | 3 | **3** |
| 1 | 0 | 3 | ✓ | 3 | 1+3 = **4** |

**최종: 4** ✓

**검증:** 양수 = 3, 5, 4, 7 → 4개 ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `7` | size 자체를 답으로 (필터 무시) | 양수만 카운트, 모든 원소 아님 |
| **(B) `4`** ✅ | 정답 | 양수 4개 (3, 5, 4, 7) |
| (C) `3` | 음수 개수 또는 한 양수 빠뜨림 | 양수 정확히 4 |
| (D) `10` | 총합 추적이라 오해 | 합 = 3+(-1)+5+(-2)+4+(-3)+7 = 13. 카운트는 4 |

> ⚠️ **함정 1:** **`> 0` strict**. 0은 양수 아님 (수학적 정의). 본 데이터에는 0이 없으므로 영향 없으나 일반적으로 주의.

> ⚠️ **함정 2:** **`list.size()` vs `list.length`**. ArrayList는 `size()` 메서드 (괄호 필수). `length`는 array에만.

> ⚠️ **함정 3:** **`list[idx]` 사용 시도**. ArrayList는 인덱싱 연산자 `[]` 사용 불가. **반드시 `list.get(idx)`**.

> 💡 **꿀팁 1:** **재귀 ArrayList 카운트 골격** (CED 4.17.A.1):
> ```
> if (idx >= list.size()) return 0;
> int rest = recurse(list, idx + 1);
> if (조건(list.get(idx))) return 1 + rest;
> return rest;
> ```

> 💡 **꿀팁 2:** **공식 ArrayList 6 메서드 (CED 4.8)**: `size`, `add(E)`, `add(int,E)`, `get`, `set`, `remove(int)`. 본 문제는 `size`, `get`만 사용 (읽기 전용 순회).

> 💡 **꿀팁 3:** **재귀 vs 반복** (CED 4.16.A.3): 같은 결과를 enhanced for로도 구현 가능. AP는 두 형태 모두 트레이싱 가능해야 함.

---

## 종합 정리

### 4.16 Recursion 핵심 패턴

**1. 자릿수 처리**
```java
if (n == 0) return /* 항등원 */;
return /* 작업(n%10) */ + recurse(n/10);
```

**2. 인덱스 기반 (배열/ArrayList)**
```java
if (idx >= length) return /* 항등원 */;
int rest = recurse(idx + 1);
if (조건) return /* 누적 */ + rest;
return rest;
```

**3. String 처리 (CED 4.17.A)**
```java
if (s.length() <= 1) return /* base */;
String rest = recurse(s.substring(1));
return /* 첫 문자 처리 */ + rest;
// 또는: rest + 첫 문자 (역순)
```

**4. 다중 재귀 (Fibonacci)**
```java
if (n <= 1) return /* base */;
return f(n-1) + f(n-2);
```

### 항등원 정리

| 작업 | 항등원 | base 반환 |
|---|---|---|
| 합 (sum) | 0 | 0 |
| 곱 (product) | 1 | 1 |
| 카운트 (count) | 0 | 0 |
| 최댓값 (max) | -∞ (또는 첫 원소) | Integer.MIN_VALUE |
| 최솟값 (min) | +∞ (또는 첫 원소) | Integer.MAX_VALUE |
| String 결합 | "" | "" |

### EXCLUSION 재확인
- **CED 4.16 EXCLUSION**: *"Writing recursive code is outside the scope"* ✓ — 본 세트는 모두 트레이싱
- **`charAt` 사용 금지** ✓ — 모든 문제 `substring(i, i+1)` 사용
- **`Math.min/max` 사용 금지** ✓
- **`break`/`continue` 사용 금지** ✓
- **`ArrayList.contains/indexOf` 사용 금지** ✓
- **CED 4.16.A.3**: 재귀 ↔ 반복 변환 가능 (개념 인지)
