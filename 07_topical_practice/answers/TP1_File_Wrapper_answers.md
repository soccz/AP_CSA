# TP1: File I/O + Wrapper Classes — 해설집

> **CED 2025-26 토픽**: 4.6 Using Text Files, 4.7 Wrapper Classes
> **답안 분포**: A:3 / B:2 / C:3 / D:2

---

## 정답 요약

| # | 정답 | CED 토픽 | 핵심 |
|---|------|---------|------|
| 1 | **A** `255` | 4.6 — `Scanner.hasNext` + `nextInt` 누적 | 토큰 단위 `nextInt` 반복 |
| 2 | **C** `"6 9"` | 4.6 — `nextInt` 토큰 카운트 + max 추적 | 줄바꿈 무시, 토큰 6개 |
| 3 | **C** Code A: `"hello"`, Code B: `"hello world"` | 4.6 — `next()` vs `nextLine()` | 토큰 vs 라인 단위 |
| 4 | **A** `"42\|\|"` | 4.6 — `nextInt` 후 `nextLine` 함정 | 잔여 개행 함정 |
| 5 | **B** `168` | 4.7 — `Integer.parseInt` 산술 | String → int 후 `+` |
| 6 | **D** `15.75` | 4.7 — `Double.parseDouble` 누적 | String → double 후 누적 |
| 7 | **A** `[18, 10]` | 4.7 — Autoboxing/Unboxing | int ↔ Integer 자동 변환 |
| 8 | **B** true / false | 4.7 + 1.5 — `MAX_VALUE` 오버플로 | n+1이 음수가 됨 |
| 9 | **C** `180` | 4.6 + 4.7 — File 라인 + parseInt | 통합 패턴 |
| 10 | **D** 둘 다 동작, B가 권장 | 4.6 — `close()` 의미 | 자원 해제 |

---

## Section I: 문제별 상세 해설

---

### Q1. 정답: **(A) `255`**

📌 **출제 의도:** `Scanner(File)`로 파일을 열고 `hasNext` 루프 안에서 `nextInt`로 토큰 단위 정수를 누적하는 표준 파일 읽기 패턴을 추적할 수 있는지 테스트. 핵심: (1) `Scanner`는 공백/개행을 토큰 구분자로 자동 처리, (2) `nextInt`는 다음 정수 토큰만 읽음, (3) 누적 후 `close()`로 자원 정리.

📎 **연계:** AP CSA **CED 4.6 Using Text Files** (Java Quick Reference 명시 메서드: `Scanner(File f)`, `boolean hasNext()`, `int nextInt()`, `void close()`). **EXCLUSION 1.4.B.1**: *"Any specific form of input from the user is outside the scope"* — 즉 `Scanner(System.in)` 키보드 입력은 OUT, **파일 입력만** IN.

> **핵심 개념: 파일 토큰 누적 표준 패턴**
> ```java
> File f = new File("...");
> Scanner sc = new Scanner(f);
> while (sc.hasNext()) {
>     int n = sc.nextInt();
>     // 처리
> }
> sc.close();
> ```
> `hasNext()`는 다음 토큰 존재 여부, `nextInt()`는 다음 정수 토큰 읽고 커서 이동.

> **선행 지식:**
> - `File(String pathname)` — 파일 경로로 File 객체 생성
> - `Scanner(File f)` — File에서 읽기 (`InputMismatchException` 가능성)
> - `nextInt()` — 다음 토큰을 int로 변환해 반환. 정수가 아니면 예외
> - `hasNext()` — 다음 토큰 있으면 true
> - `close()` — 파일 핸들 해제 (AP는 try-with-resources 범위 외)

**파일 내용:**
```
85
92
78
```
→ 3개의 토큰: `85`, `92`, `78` (개행은 구분자로 처리)

**한 단계씩 추적:**

| 반복 | hasNext? | nextInt | sum |
|---|---|---|---|
| 시작 | — | — | 0 |
| 1 | true | 85 | 85 |
| 2 | true | 92 | 177 |
| 3 | true | 78 | 255 |
| 종료 | false | — | — |

`println(255)` → 출력: `255`

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `255`** ✅ | 정답 | 85 + 92 + 78 = 255 |
| (B) `0` | sum 초기화 후 루프가 한 번도 안 돈다고 오해 | `hasNext()`가 첫 토큰부터 true, 3회 반복 |
| (C) `85` | 첫 토큰만 읽고 break된다고 착각 | break 없음 — 모든 토큰 읽을 때까지 반복 |
| (D) `857892` | `+=`가 String 결합이라 오해 | sum이 `int`이므로 산술 합산. String 결합은 `+ ""`가 필요 |

> ⚠️ **함정 1:** **`Scanner(System.in)` 출제 안 됨** — CED 1.4.B.1 EXCLUSION. AP에서 Scanner는 항상 `Scanner(new File(...))` 형태로만 등장.

> ⚠️ **함정 2:** `nextInt()`는 **정수 토큰만** 읽음. 파일에 `"abc"` 같은 비정수가 있으면 `InputMismatchException`. 본 문제는 정수만 있으므로 안전.

> ⚠️ **함정 3:** **`close()` 호출 누락 시 컴파일은 OK**, 런타임에서 자원 누수 발생 가능. AP에서는 정확성에 영향 없으나 권장 관례.

> 💡 **꿀팁 1:** **Scanner 파일 읽기 골격 외우기**: `new File(path)` → `new Scanner(file)` → `while (sc.hasNext())` → `sc.close()`. 4단계.

> 💡 **꿀팁 2:** **Scanner 메서드 6대 (CED 4.6, Quick Reference)**: `nextInt`, `nextDouble`, `nextBoolean`, `nextLine`, `next`, `hasNext`. `next()`는 String 토큰, `nextLine()`은 라인 단위.

> 💡 **꿀팁 3:** **공백/개행 자동 처리**: `Scanner`는 기본적으로 공백/탭/개행을 토큰 구분자로 사용. 따라서 `"85\n92\n78"`은 `"85 92 78"`과 동일하게 처리됨.

---

### Q2. 정답: **(C) `"6 9"`**

📌 **출제 의도:** `Scanner.nextInt()`가 파일 내 모든 정수 토큰을 차례로 읽어들이고, 줄 구분과 무관하게 토큰 단위로 처리한다는 것을 이해하는지 테스트. 표준 알고리즘 (count + max 추적, CED 2.9.A.1) 적용.

📎 **연계:** **CED 4.6** + **CED 2.9 Implementing Selection/Iteration Algorithms** ("determine a minimum or maximum value", "compute a sum or average") 결합. AP에서 파일 데이터 분석 시 자주 등장하는 패턴.

> **핵심 개념:** 파일이 여러 줄에 걸쳐 있어도 `nextInt`는 **공백/개행을 모두 구분자**로 처리. 즉 `"3 7 2\n9 1\n5"` = `"3 7 2 9 1 5"` (토큰 6개).

> **선행 지식:**
> - `Integer.MIN_VALUE` — `int`의 최솟값 (CED 1.5.B.1, Quick Reference 명시)
> - max 갱신 표준 알고리즘: 시작은 가장 작은 값으로 → 더 큰 값 만나면 갱신
> - `Math.max`는 Quick Reference에 없음 → **반드시 `if` 비교**

**파일 내용:**
```
3 7 2
9 1
5
```
→ 토큰 6개: `3, 7, 2, 9, 1, 5`

**추적:**

| 토큰 | n | count | max 갱신 |
|---|---|---|---|
| 시작 | — | 0 | MIN_VALUE |
| 1 | 3 | 1 | 3 |
| 2 | 7 | 2 | 7 |
| 3 | 2 | 3 | 7 (그대로) |
| 4 | 9 | 4 | 9 |
| 5 | 1 | 5 | 9 (그대로) |
| 6 | 5 | 6 | 9 (그대로) |

`println("6 9")` → 출력: `6 9`

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"3 9"` | count = 첫 줄 토큰 수(3)로 잘못 계산 | 모든 줄의 모든 토큰 카운트 → 6 |
| (B) `"3 7"` | count = 3, max = 첫 줄 최댓값(7) | 줄 단위가 아닌 **토큰 단위**로 진행 |
| **(C) `"6 9"`** ✅ | 정답 | 6 토큰, 최댓값 9 |
| (D) `"6 7"` | count는 맞지만 9를 놓침 | max = 9 (4번째 토큰) — 모든 토큰 검사해야 |

> ⚠️ **함정 1:** **줄 vs 토큰 혼동**. `nextInt`는 줄 구분 없이 토큰 단위로만 읽음. 줄 단위 처리는 `nextLine()` + `parseInt`.

> ⚠️ **함정 2:** **max 초기값**. `int max = arr[0]` 패턴이 일반적이나, 파일 입력에서는 첫 토큰을 미리 읽기 어려우므로 `Integer.MIN_VALUE`로 시작 후 첫 토큰부터 비교.

> ⚠️ **함정 3:** **`Math.max` 사용 금지** — Quick Reference에 없음. `if (n > max) max = n;`으로 직접 구현.

> 💡 **꿀팁 1:** **표준 max 패턴 (CED 2.9.A.1)**: `int max = INT_MIN; for (each n) if (n > max) max = n;`. 파일/배열/ArrayList 모두 적용.

> 💡 **꿀팁 2:** **공백 구분자**: `Scanner`는 white-space (`\s+`)를 기본 구분자로 사용. 공백, 탭, 개행 모두 동일 처리.

> 💡 **꿀팁 3:** **count + max 동시 추적** — 한 번의 순회로 두 값을 동시에 구하는 것이 효율적. AP FRQ에서 자주 요구.

---

### Q3. 정답: **(C) Code A: `"hello"`, Code B: `"hello world"`**

📌 **출제 의도:** `Scanner.next()` (토큰 단위)와 `Scanner.nextLine()` (라인 단위)의 **반환 범위** 차이를 정확히 이해하는지 테스트. 가장 자주 헷갈리는 두 메서드.

📎 **연계:** **CED 4.6** Java Quick Reference 명시 — `String next()` vs `String nextLine()`. CED p.186 정의:
- `next()`: *"Returns the next String read from the file or input source"* (토큰 = 공백 전까지)
- `nextLine()`: *"Returns the next line of text as a String read from the file"* (개행 전까지)

> **핵심 개념: `next` vs `nextLine`**
> - `next()` — **공백/개행 전까지의 토큰 하나** 반환. 구분자는 white-space.
> - `nextLine()` — **현재 위치부터 개행(`\n`)까지의 한 줄 전체** 반환 (개행 자체는 제외).
>
> 따라서 `"hello world\njava"`에서:
> - `next()` → `"hello"` (공백에서 멈춤)
> - `nextLine()` → `"hello world"` (개행에서 멈춤)

> **선행 지식:**
> - 파일 내용에 공백 또는 개행이 있을 때 두 메서드의 동작 비교
> - `next()`는 토큰 사이의 공백/개행을 **건너뛰고** 다음 토큰만 반환
> - `nextLine()`은 라인 끝의 개행 문자를 **소비**하지만 반환값에는 포함 안 함

**파일 내용:**
```
hello world
java
```

**Code A 추적:**
- `sc.next()` → 첫 토큰 = `"hello"` (공백 만나서 멈춤)
- 출력: `hello`

**Code B 추적:**
- `sc.nextLine()` → 첫 줄 전체 = `"hello world"` (개행에서 멈춤)
- 출력: `hello world`

**오답 분석:**

| 보기 | 왜 틀린가 |
|---|---|
| (A) 둘 다 `"hello world"` | `next()`도 라인 단위라고 오해. 실제로는 공백 단위 토큰 |
| (B) 둘 다 `"hello"` | `nextLine()`도 토큰 단위라고 오해. 실제로는 라인 전체 |
| **(C) Code A: `"hello"`, Code B: `"hello world"`** ✅ | 정답 — `next()`는 토큰, `nextLine()`은 라인 |
| (D) Code A: `"hello world"`, Code B: `"hello"` | 두 메서드 동작을 거꾸로 적용 |

> ⚠️ **함정 1:** **`next()` ≠ `nextLine()`**. 공백이 포함된 데이터(이름, 주소 등)를 읽을 때는 반드시 `nextLine()`. 단어/숫자 토큰은 `next()`.

> ⚠️ **함정 2:** **`next()`는 줄바꿈 무시**. `"a\nb"`에서 첫 `next()`는 `"a"`, 두 번째 `next()`는 `"b"`. 줄 구분이 사라진다.

> ⚠️ **함정 3:** **`nextLine()`은 빈 줄도 반환**. `"a\n\nb"`에서 두 번째 `nextLine()`은 빈 문자열 `""`. Q4 함정과 연결.

> 💡 **꿀팁 1:** **선택 기준**: "단어 하나 필요" → `next()`, "줄 전체 필요(공백 포함)" → `nextLine()`.

> 💡 **꿀팁 2:** **CSV 같은 구조화 데이터**: `nextLine()`으로 줄 받은 후 `String.split(",")`로 컬럼 분리. CED 4.6 + 1.15 결합 패턴.

> 💡 **꿀팁 3:** **`hasNext()` vs `hasNextLine()`** (둘 다 IN 스코프지만 `hasNext`만 Quick Reference 명시): 토큰 끝 vs 라인 끝 검사. AP 시험은 `hasNext()`만 사용.

---

### Q4. 정답: **(A) `"42||"`**

📌 **출제 의도:** `nextInt()` 호출 후 **잔여 개행 문자**가 buffer에 남아 있어 다음 `nextLine()`이 빈 문자열을 반환하는 **고전적 함정**을 추적할 수 있는지 테스트. AP에서 매년 출제되는 단골 함정.

📎 **연계:** **CED 4.6** Scanner 메서드 조합. `nextInt()`는 정수 토큰만 읽고 **그 뒤의 개행은 그대로 둠**. 직후의 `nextLine()`이 그 개행까지 읽어 **빈 String 반환**.

> **핵심 개념: nextInt 후 nextLine 함정**
> - `nextInt()`는 다음 정수 토큰을 읽고 **커서를 그 정수 바로 뒤**에 놓음 (개행은 소비 안 함)
> - 직후 `nextLine()`은 **현재 위치(개행 직전)부터 개행까지** = **빈 String** `""`
> - 실제 두 번째 줄을 읽으려면 **두 번째 `nextLine()`**이 필요

> **선행 지식:**
> - `nextInt()` 동작: 토큰 매칭 → int 변환 → 토큰 끝까지만 커서 이동
> - `nextLine()` 동작: 현재 위치부터 다음 `\n`까지 (`\n` 자체는 소비, 반환에는 포함 안 함)
> - String concatenation: `n + "|" + line + "|"`에서 `n`이 int면 자동 String 변환

**파일 내용 (보이지 않는 개행 표시):**
```
42\n
Hello World\n
```
즉 실제는 `"42\nHello World\n"`.

**한 단계씩 추적:**

| 단계 | 동작 | 커서 위치 | 변수 |
|---|---|---|---|
| 시작 | — | 파일 처음 (`4`) | — |
| `sc.nextInt()` | 토큰 `42` 매칭 → int 변환 | `42` 직후 (`\n` 직전) | `n = 42` |
| `sc.nextLine()` | 현재 위치 → 다음 `\n`까지 | 첫 `\n` 직후 (`H` 직전) | `line = ""` (빈 String!) |
| 결합 | `42 + "\|" + "" + "\|"` | — | `"42\|\|"` |
| 출력 | — | — | `42\|\|` |

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `"42\|\|"`** ✅ | 정답 | nextLine이 잔여 개행을 만나 빈 String 반환 |
| (B) `"42\|Hello World\|"` | nextLine이 두 번째 줄을 정상 읽는다고 오해 | nextInt가 첫 줄 개행을 남겨놓아 nextLine이 그것을 읽고 종료 |
| (C) `"42\| Hello World\|"` | nextLine이 `"Hello World"` 앞에 공백 한 칸 + 텍스트 | 잔여 개행 후 nextLine은 빈 String, 공백도 없음 |
| (D) `"42\|Hello\|"` | nextLine이 단어 하나만 읽는다고 오해 | nextLine은 줄 전체 (`Hello World`)를 읽거나 (이 경우엔 빈 String) |

**해결 방법** (참고용 — 본 문제 해당 없음):
```java
int n = sc.nextInt();
sc.nextLine();   // 잔여 개행 소비 (dummy 호출)
String line = sc.nextLine();  // 이제 두 번째 줄을 정상 읽음
```

> ⚠️ **함정 1:** **`nextInt() + nextLine()` 조합은 위험**. 키보드 입력에도 동일 함정. AP에서 가장 자주 출제되는 Scanner 함정.

> ⚠️ **함정 2:** **빈 String의 출력**. `"" + "\|"` = `"\|"`. 빈 String을 그대로 출력하면 보이지 않음. 구분자(`|`)로 감쌌을 때만 차이가 보임.

> ⚠️ **함정 3:** **`nextLine()` 호출 횟수**. `nextInt` 직후의 `nextLine`은 dummy(잔여 개행 소비). 실제 데이터는 그 다음 `nextLine`이 받음.

> 💡 **꿀팁 1:** **안전 패턴**: `nextInt()` 직후 줄 데이터가 필요하면 항상 **dummy `nextLine()` 한 번 호출** 후 진짜 `nextLine()`.

> 💡 **꿀팁 2:** **`next()` 사용 대안**: 만약 두 번째 토큰이 단어 하나면 `nextLine` 대신 `next()` 사용 가능 (잔여 개행 함정 없음).

> 💡 **꿀팁 3:** **출력 포맷 확인**: 구분자(`|`)로 양쪽을 감싸면 빈 String도 시각적으로 확인 가능. 디버깅 시 자주 사용.

---

### Q5. 정답: **(B) `168`**

📌 **출제 의도:** `Integer.parseInt(String)`이 String을 int로 변환한다는 기본 동작 + 변환 후 산술 연산이 정수 덧셈임을 이해하는지 테스트. 4.7 Wrapper Classes의 가장 기초.

📎 **연계:** **CED 4.7.A.4** Java Quick Reference 명시: *"static int parseInt(String s) returns the String argument as an int"*. AP에서 String 형태의 데이터(예: 파일 입력, 사용자 입력)를 숫자로 처리할 때 필수.

> **핵심 개념: `Integer.parseInt`**
> - `static int Integer.parseInt(String s)` — String을 int로 변환
> - 변환 후 **int** 타입이므로 `+`는 **산술 합**
> - String 그대로 `+` 하면 **String 결합**: `"123" + "45"` = `"12345"`

> **선행 지식:**
> - `parseInt`는 **static 메서드** → `Integer.parseInt(...)` 클래스명으로 호출
> - 변환 실패 시 `NumberFormatException` (예: `"abc"`)
> - **Quick Reference에 명시된 유일한 Integer 정적 메서드** (외에 `MIN_VALUE`, `MAX_VALUE` 상수)

**추적:**

| 단계 | 식 | 결과 |
|---|---|---|
| 1 | `Integer.parseInt("123")` | int **123** |
| 2 | `Integer.parseInt("45")` | int **45** |
| 3 | `123 + 45` | int **168** |
| 4 | `int n = 168` | — |
| 5 | `println(168)` | 출력: `168` |

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"12345"` | parseInt 호출을 잊고 String concatenation으로 추론 | parseInt가 String을 int로 변환해 산술 합 |
| **(B) `168`** ✅ | 정답 | 123 + 45 = 168 |
| (C) `"123" + "45"` | parseInt 결과가 여전히 String이라 오해 | parseInt 반환은 **int**, String 아님 |
| (D) Compile-time error | `parseInt`가 존재하지 않거나 잘못된 호출이라 의심 | `Integer.parseInt`는 Java Quick Reference 명시 메서드, 정상 컴파일 |

> ⚠️ **함정 1:** **String → int 변환 잊음**. `"123" + "45"`가 자동으로 정수 덧셈이 된다고 오해. **`parseInt` 호출 필수**.

> ⚠️ **함정 2:** **`NumberFormatException`**. `Integer.parseInt("abc")` 같이 정수가 아닌 String을 넘기면 런타임 예외. 본 문제는 정상 정수 String이라 안전.

> ⚠️ **함정 3:** **`Integer.parseInt(int)` 호출 시도**. `parseInt`는 `String`만 받음. 이미 int면 변환 불필요. 정수 → String은 `"" + n` 또는 `String.valueOf(n)`.

> 💡 **꿀팁 1:** **Java Quick Reference Integer 메서드 (CED 4.7)**: `parseInt(String)`, `MIN_VALUE`, `MAX_VALUE` **3개**. 그 외 (parseLong, valueOf, intValue 등)는 **출제 범위 외**.

> 💡 **꿀팁 2:** **`Double.parseDouble`** (CED 4.7.A.5): String을 double로 변환. parseInt와 동일 패턴, double 반환.

> 💡 **꿀팁 3:** **파일 입력에 자주 사용**: `Scanner.nextLine()`으로 String 받은 후 `Integer.parseInt(line)`로 변환하는 패턴이 표준 (Q9 참조).

---

### Q6. 정답: **(D) `15.75`**

📌 **출제 의도:** `Double.parseDouble`로 소수 문자열을 double로 변환 후 누적하는 패턴을 추적할 수 있는지 테스트. enhanced for + 누적 + 형변환 결합. **이진 정확 표현 가능한 값(.5, .25 등)을 사용하여 부동소수점 정밀도 오차 회피**.

📎 **연계:** **CED 4.7.A.5** Java Quick Reference: *"static double parseDouble(String s) returns the String argument as a double"*. 1.5 Casting (int → double 자동 승격)과 결합.

> **핵심 개념: `Double.parseDouble`**
> - `static double Double.parseDouble(String s)` — String을 double로 변환
> - `"3.5"` → `3.5`, `"10"` → `10.0` (정수 String도 double 가능)
> - `+=`로 누적 시 결과는 double (혼합 연산)

> **선행 지식:**
> - `parseDouble`은 정수 형태(`"10"`)도 OK → `10.0`으로 변환
> - 0.5, 0.25, 0.125 등 **2의 거듭제곱 분수**는 이진 정확 표현 (정밀도 오차 없음)
> - enhanced for: `for (String s : inputs)`로 배열 각 원소 순회

**추적:**

| 반복 | s | parseDouble | sum |
|---|---|---|---|
| 시작 | — | — | 0.0 |
| 1 | `"3.5"` | 3.5 | 3.5 |
| 2 | `"2.25"` | 2.25 | 5.75 |
| 3 | `"10"` | 10.0 | 15.75 |

`println(15.75)` → 출력: `15.75`

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `15` | 소수부 무시 (int 누적이라 오해) | sum이 `double`이므로 소수부 보존 |
| (B) `"3.52.2510"` | parseDouble 호출을 잊고 String 결합으로 추론 | parseDouble이 String을 double로 변환 |
| (C) Runtime error | `"10"`이 double 아니라 예외라고 오해 | parseDouble은 정수 String도 정상 변환 (`10.0`) |
| **(D) `15.75`** ✅ | 정답 | 3.5 + 2.25 + 10.0 = 15.75 |

> ⚠️ **함정 1:** **`parseDouble` vs `parseInt`**. `"3.5"`를 `parseInt`로 호출하면 `NumberFormatException`. 소수가 있으면 반드시 `parseDouble`.

> ⚠️ **함정 2:** **누적 변수 타입**. `int sum = 0;`이면 `sum += parseDouble(...)`은 컴파일 에러 (int에 double 대입 불가). 반드시 `double sum = 0.0;`.

> ⚠️ **함정 3:** **부동소수점 정밀도 (CED 1.5.C.1)**. `0.1 + 0.2` ≠ `0.3` (반올림 오차). 0.1, 0.3, 3.14 같은 값은 이진 정확 표현 불가 → `15.640000000001` 같은 출력 가능. **본 문제는 0.5, 0.25 (2의 거듭제곱 분수)** 만 사용하여 정확한 결과 보장.

> 💡 **꿀팁 1:** **자동 승격 (CED 1.5.A.3)**: `int + double` → `double`. 따라서 정수 String도 parseDouble로 변환 가능 (`"10"` → `10.0`).

> 💡 **꿀팁 2:** **이진 정확 표현 가능한 소수**: 0.5, 0.25, 0.125, 0.0625 등 (2⁻ⁿ 형태) — 모든 합/차도 정확. 0.1, 0.2, 3.14 등은 부정확 → 정밀도 오차 발생.

> 💡 **꿀팁 3:** **출력 형식**: `15.75` 같은 정확한 표현은 그대로 출력. 부정확 표현은 `0.30000000000000004` 같이 나타남.

---

### Q7. 정답: **(A) `[18, 10]`**

📌 **출제 의도:** **Autoboxing**(int → Integer)과 **Unboxing**(Integer → int)이 Java 컴파일러에 의해 자동으로 일어나는 것을 이해하고, `ArrayList<Integer>`를 사용한 표준 조작을 추적할 수 있는지 테스트.

📎 **연계:** **CED 4.7.A.2** Autoboxing: *"automatic conversion that the Java compiler makes between primitive types and their corresponding object wrapper classes"*. **4.7.A.3** Unboxing 동일. **CED 4.8 ArrayList Methods** (`add`, `get`, `set`)와 결합.

> **핵심 개념: Autoboxing/Unboxing**
> - **Autoboxing**: `int` → `Integer` 자동 변환 (예: `list.add(5)`)
> - **Unboxing**: `Integer` → `int` 자동 변환 (예: `int x = list.get(0)`)
> - 자동이지만 **타입 일관성**은 유지 — `ArrayList<Integer>`에 `int`를 넣어도 내부적으로는 `Integer`

> **선행 지식:**
> - `ArrayList<Integer>` — 박싱된 Integer 객체만 저장 가능
> - `int`로 받아도 산술 가능 (자동 unboxing)
> - `set(idx, obj)` — 이전 원소 반환 (본 문제는 활용 안 함)

**추적:**

| 단계 | 동작 | 결과 (list 상태) |
|---|---|---|
| 1 | `list = []` | `[]` |
| 2 | `list.add(5)` (autoboxing) | `[5]` |
| 3 | `list.add(10)` (autoboxing) | `[5, 10]` |
| 4 | `int x = list.get(0)` (unboxing) | `x = 5` |
| 5 | `int y = list.get(1) + 3` (unboxing + 산술) | `y = 10 + 3 = 13` |
| 6 | `list.set(0, x + y)` = `list.set(0, 18)` (autoboxing) | `[18, 10]` |
| 7 | `println(list)` | 출력: `[18, 10]` |

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `[18, 10]`** ✅ | 정답 | set(0, 18)로 인덱스 0이 18로 갱신, 인덱스 1은 그대로 |
| (B) `[5, 10]` | set이 적용되지 않는다고 오해 | set은 in-place 갱신 (반환값 무시해도 변경 효과 있음) |
| (C) `[15, 10]` | y 계산을 `5 + 10 = 15`로 잘못 (x = 5, y = 10) | y는 `list.get(1) + 3 = 13`. x + y = 5 + 13 = 18 |
| (D) Compile-time error | `int`를 `ArrayList<Integer>`에 직접 add 불가하다고 오해 | **autoboxing이 자동으로 변환**. 컴파일 정상 |

> ⚠️ **함정 1:** **autoboxing/unboxing 인지**. `ArrayList<Integer>`에 `add(5)`를 직접 사용 가능. 명시적 `new Integer(5)` 불필요. CED 4.7.A.2 명시.

> ⚠️ **함정 2:** **`get(0)`이 Integer 반환**. `int x = list.get(0)`은 unboxing이 자동 수행되어 정상 동작. 만약 list가 null이거나 Integer가 null이면 `NullPointerException`.

> ⚠️ **함정 3:** **set 반환값 무시**. `list.set(0, 18)`은 이전 원소 `5`를 반환하지만, 본 코드는 받지 않음. 그래도 list는 갱신됨.

> 💡 **꿀팁 1:** **`ArrayList<int>` 불가**. Java는 generic에 primitive 타입을 직접 사용 못함. 반드시 wrapper 사용 (`ArrayList<Integer>`).

> 💡 **꿀팁 2:** **autoboxing 발생 위치 (CED 4.7.A.2)**: 
> - 메서드 인자로 wrapper class를 기대할 때 (`list.add(5)`)
> - wrapper class 변수에 대입 (`Integer i = 5;`)
>
> **unboxing 발생 위치 (4.7.A.3)**:
> - 메서드 인자로 primitive를 기대할 때
> - primitive 변수에 대입 (`int x = list.get(0);`)

> 💡 **꿀팁 3:** **null 위험**: `Integer obj = null; int x = obj;` → unboxing 시 `NullPointerException`. AP에서는 보통 null 가정 안 함.

---

### Q8. 정답: **(B) true / false**

📌 **출제 의도:** `Integer.MAX_VALUE`의 정확한 값을 알고, **`int` 오버플로** 시 음수로 wrap-around되는 동작을 이해하는지 테스트. CED 1.5.B (range of variables) 핵심.

📎 **연계:** **CED 4.7** Quick Reference: `Integer.MIN_VALUE`, `Integer.MAX_VALUE`. **CED 1.5.B.3** Overflow: *"If an expression would evaluate to an int value outside of the allowed range, an integer overflow occurs. The result is an int value in the allowed range but not necessarily the value expected."*

> **핵심 개념: int 오버플로**
> - `Integer.MAX_VALUE` = 2,147,483,647 (2³¹ - 1)
> - `Integer.MIN_VALUE` = -2,147,483,648 (-2³¹)
> - **MAX_VALUE + 1 = MIN_VALUE** (wrap-around)
> - 즉, 양수에서 1 더해서 음수가 될 수 있음

> **선행 지식:**
> - `int`는 4바이트(32비트), 부호 있는 정수
> - 오버플로 시 **예외 발생 안 함**, 그냥 wrap-around
> - 비교 `==`로 정확한 값 검증 가능

**추적:**

| 단계 | 식 | 결과 |
|---|---|---|
| 1 | `n = Integer.parseInt("2147483647")` | `n = 2147483647` (= MAX_VALUE) |
| 2 | `m = n + 1` | overflow → `m = -2147483648` (= MIN_VALUE) |
| 3 | `n == Integer.MAX_VALUE` | `2147483647 == 2147483647` → **true** |
| 4 | `m > 0` | `-2147483648 > 0` → **false** |

**출력:**
```
true
false
```

**오답 분석:**

| 보기 | 출력 | 왜 틀린가 |
|---|---|---|
| (A) true / true | 오버플로 모르고 `m`이 여전히 양수라 가정 | MAX_VALUE + 1은 음수로 wrap. m > 0은 false |
| **(B) true / false** ✅ | 정답 | n은 정확히 MAX_VALUE, m은 오버플로로 음수 |
| (C) false / true | n이 MAX_VALUE 아니라고 오해 | `parseInt("2147483647")`은 정확히 MAX_VALUE 반환 |
| (D) false / false | 둘 다 잘못된 추론 | n == MAX_VALUE는 true, m > 0은 false |

> ⚠️ **함정 1:** **오버플로는 예외 없음**. C와 달리 Java도 정수 오버플로 시 예외 발생 안 함, 그냥 wrap-around. 프로그램은 계속 실행되지만 결과가 예상과 다름.

> ⚠️ **함정 2:** **MAX_VALUE 정확한 값**. AP 시험에 정확한 값을 외울 필요는 없으나, "31비트 양수의 최댓값"이라는 개념은 알아야 함. CED 1.5.B.2 명시.

> ⚠️ **함정 3:** **`MAX_VALUE + 1 == MIN_VALUE`**. `MIN_VALUE - 1 == MAX_VALUE` 도 같은 원리 (음수 → 양수 wrap). 양방향 모두 발생.

> 💡 **꿀팁 1:** **Integer 메서드 (CED 4.7, Quick Reference)**: `MIN_VALUE`, `MAX_VALUE`, `parseInt(String)` 3개만. 다른 정수 변환은 출제 안 됨.

> 💡 **꿀팁 2:** **오버플로 회피 전략**: 큰 수 다룰 때 `long` 사용? — **AP는 long 출제 안 함** (CED 1.5.C.1 EXCLUSION). 따라서 AP에서는 오버플로 위험 코드 자체가 거의 등장 안 함.

> 💡 **꿀팁 3:** **표준 문제 패턴**: "다음 중 오버플로 발생하는 식은?" — `MAX_VALUE * 2`, `MAX_VALUE + 1`, `Integer.MIN_VALUE - 1` 등 모두 오버플로.

---

### Q9. 정답: **(C) `180`**

📌 **출제 의도:** `Scanner.nextLine()`으로 한 줄씩 String 받은 후 `Integer.parseInt`로 변환해 누적하는 **파일 + Wrapper 통합 패턴**을 추적할 수 있는지 테스트. AP에서 파일 입력 처리의 표준 형태.

📎 **연계:** **CED 4.6** (`Scanner.nextLine`, `hasNext`) + **CED 4.7** (`Integer.parseInt`) 결합. AP FRQ에서 "파일에서 정수 읽어 분석" 시 자주 사용되는 패턴.

> **핵심 개념: 라인 단위 파일 처리**
> - 파일이 **한 줄에 하나씩 정수**가 있을 때, `nextInt()` 대신 `nextLine() + parseInt()` 패턴 사용 가능
> - 두 방법 모두 동작, 본 문제는 후자 사용
> - `nextLine()` → String, `parseInt(String)` → int

> **선행 지식:**
> - 파일 각 줄에 `"100"`, `"50"`, `"30"` (정수 String)
> - `nextLine()`은 `\n`을 소비하고 라인 내용 반환
> - `parseInt`는 정수 형태 String만 변환 (양옆 공백은 안 됨, 본 문제는 안전)

**추적:**

| 반복 | hasNext? | nextLine | parseInt | total |
|---|---|---|---|---|
| 시작 | — | — | — | 0 |
| 1 | true | `"100"` | 100 | 100 |
| 2 | true | `"50"` | 50 | 150 |
| 3 | true | `"30"` | 30 | 180 |
| 종료 | false | — | — | — |

`println(180)` → 출력: `180`

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"1005030"` | parseInt 호출 잊고 String 결합으로 추론 | parseInt가 String을 int로 변환해 산술 합 |
| (B) Runtime error | 파일 형식이 맞지 않다고 오해 | `"100"`, `"50"`, `"30"` 모두 정상 정수 String |
| **(C) `180`** ✅ | 정답 | 100 + 50 + 30 = 180 |
| (D) `0` | 루프가 한 번도 실행 안 된다고 오해 | hasNext는 첫 줄부터 true, 3회 반복 |

> ⚠️ **함정 1:** **`nextLine()` vs `nextInt()` 선택**. 본 문제는 둘 다 사용 가능 (정수 토큰이 한 줄에 하나씩). 그러나 `nextLine`은 **줄 전체** 받으므로 String 처리 후 변환 필요.

> ⚠️ **함정 2:** **공백/특수문자 함정**. `parseInt(" 100")` (앞에 공백) → `NumberFormatException`. 안전하려면 `line.trim()` (Quick Reference에는 없음 → 출제 안 됨). 본 문제는 안전.

> ⚠️ **함정 3:** **빈 줄 처리**. 만약 파일에 빈 줄이 있으면 `nextLine()`이 `""`을 반환 → `parseInt("")` → 예외. 본 문제는 빈 줄 없음.

> 💡 **꿀팁 1:** **두 가지 표준 파일 입력 패턴**:
> 1. `nextInt`로 직접 토큰 읽기 (Q1, Q2 패턴)
> 2. `nextLine` + `parseInt`로 라인 단위 처리 (본 문제 패턴)
>
> 둘 다 IN 스코프, 데이터 형식에 따라 선택.

> 💡 **꿀팁 2:** **CSV 데이터 처리**: `nextLine()` + `String.split(",")` + `parseInt` 조합. CED 1.15 split + 4.6 + 4.7 결합 패턴.

> 💡 **꿀팁 3:** **`hasNext()` vs `hasNextLine()`**: Quick Reference에는 `hasNext()`만 명시. AP는 `hasNext()`만 사용.

---

### Q10. 정답: **(D) Code A와 B 모두 정상 동작하지만 Code B가 권장 — `close()`로 파일 핸들/자원을 해제**

📌 **출제 의도:** `Scanner.close()`의 **목적과 효과**를 정확히 이해하는지 테스트. 핵심: (1) `close()`는 **선택적 권장 사항**(미호출 시에도 컴파일/런타임 동작 정상), (2) 자원 누수 방지를 위한 모범 사례.

📎 **연계:** **CED 4.6** Java Quick Reference: `void close()` — *"Closes this scanner"*. **EXCLUSION**: `try-with-resources`는 CED 본문 등장 없음 → AP는 명시적 `close()`만 사용.

> **핵심 개념: `close()`의 역할**
> - **목적**: 파일 핸들, 시스템 자원 해제
> - **호출 안 해도** 프로그램은 정상 동작 (컴파일/런타임 OK)
> - 그러나 **권장 관례**: 자원 누수 방지, 다른 프로세스의 파일 접근 가능
> - `close()` 호출 후에는 더 이상 `nextInt`/`hasNext` 등 사용 불가 (`IllegalStateException`)

> **선행 지식:**
> - Java는 garbage collector가 사용하지 않는 객체를 정리하지만, **파일 핸들 같은 OS 자원**은 명시적 `close()`가 안전
> - AP에서는 `try-with-resources` 출제 안 됨 → 명시적 `close()`로 학습
> - `close()` 후 `println` 등 일반 출력은 **정상 실행** (Scanner와 무관)

**Code A와 B 비교:**

| 코드 | `close()` | 컴파일 | 런타임 | 동작 |
|---|---|---|---|---|
| Code A | 없음 | OK | OK | 정상 (자원 누수 가능) |
| Code B | 있음 | OK | OK | 정상 (권장) |

두 코드 모두 출력은 같다. 차이는 **자원 정리** 여부.

**오답 분석:**

| 보기 | 왜 틀린가 |
|---|---|
| (A) Code A는 컴파일 에러 — `close()` 필수 | `close()`는 **선택적**. 미호출도 컴파일/런타임 OK. Java 컴파일러는 close 강제 안 함 |
| (B) Code B는 `close()` 후 `System.out.println`이 실행 안 됨 | `close()`는 **Scanner만 닫음**. `System.out`은 별개 → println 정상 실행 |
| (C) Code A는 Scanner가 닫히지 않아 `IOException` | 자동 garbage collection이 결국 정리. 명시적 IOException 발생 안 함 (단, OS 자원 효율은 떨어짐) |
| **(D) Code A와 B 모두 정상 동작하지만 Code B가 권장** ✅ | 정답 — `close()`는 best practice |

> ⚠️ **함정 1:** **`close()`가 필수라고 오해**. 일부 언어/프레임워크는 close 강제하지만, Java Scanner는 선택적. 권장이지 의무 아님.

> ⚠️ **함정 2:** **`close()` 후 사용 시도**. 만약 `sc.close(); int x = sc.nextInt();`를 쓰면 **`IllegalStateException`**. 본 문제는 close 후 sc를 사용 안 함.

> ⚠️ **함정 3:** **`close()`는 출력 스트림과 무관**. `System.out`은 standard output stream, Scanner는 input stream. 서로 영향 없음.

> 💡 **꿀팁 1:** **AP 답안 작성 권장**: FRQ에서 Scanner 사용 시 항상 `sc.close();`를 마지막에 호출. 채점 자체에는 영향 없으나 모범 답안.

> 💡 **꿀팁 2:** **자원 정리의 의미**: 파일 핸들은 OS가 제공하는 제한된 자원. 많이 열고 안 닫으면 다른 프로세스가 파일을 못 열 수도 있음 (실무에서 중요).

> 💡 **꿀팁 3:** **`try-with-resources`** (참고): Java 7+에서 `try (Scanner sc = ...) { ... }`로 자동 close 가능. 그러나 **CED 본문 등장 없음** → AP 출제 범위 외. 명시적 `close()`만 학습.

---

## 종합 정리

### 4.6 Using Text Files 핵심 골격
```java
File file = new File("path");
Scanner sc = new Scanner(file);
while (sc.hasNext()) {
    // sc.nextInt() / sc.nextDouble() / sc.nextLine() / sc.next() / sc.nextBoolean()
}
sc.close();
```

### 4.7 Wrapper Classes 핵심
- `Integer.parseInt(String)` → int
- `Double.parseDouble(String)` → double
- `Integer.MIN_VALUE`, `Integer.MAX_VALUE`
- Autoboxing: `int → Integer` (예: `list.add(5)`)
- Unboxing: `Integer → int` (예: `int x = list.get(0)`)

### 흔한 함정 모음
1. **`nextInt + nextLine` 함정** (Q4): 잔여 개행으로 빈 String 반환
2. **`next` vs `nextLine`** (Q3): 토큰 vs 라인 단위
3. **오버플로 wrap-around** (Q8): MAX_VALUE + 1 = MIN_VALUE
4. **parseInt 호출 잊음** (Q5, Q9): String concat 오해
5. **`close()` 의미** (Q10): 선택적 권장, 의무 아님

### EXCLUSION 재확인
- `Scanner(System.in)` 키보드 입력 OUT (CED 1.4.B.1)
- `try-with-resources` CED 본문 없음 → AP 미출제
- `Math.min/max/floor/ceil/round` Quick Reference 없음 → 본 세트 미사용 ✓
- `ArrayList.contains/clear/indexOf` Quick Reference 없음 → 본 세트 미사용 ✓
