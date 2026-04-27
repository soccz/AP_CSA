# Unit 2 시험 개념 딥다이브
## Selection and Iteration — 모든 시험 출제 개념의 메커니즘

> **Unit 2는 MCQ 비중 25-35%로 4개 Unit 중 둘째로 큼.** 트레이싱 문제의 절반이 이 단원에서 나온다. 루프 종료 시 변수 상태, 중첩 루프 반복 횟수, short-circuit으로 인한 NPE 회피, De Morgan 법칙 — 이 네 기둥을 **변형 문제에도 즉답할 수 있을 때까지** 파고든다.

---

## 목차

| # | 개념 | 출처 토픽 |
|---|------|---------|
| DD2.1 | `boolean` 타입의 엄격성 — Java는 정수를 조건으로 못 씀 | 2.2 |
| DD2.2 | 관계 연산자 6종과 타입 규칙 | 2.2 |
| DD2.3 | `&&`, `\|\|`, `!`의 **진리표**와 평가 순서 | 2.5 |
| DD2.4 | **Short-circuit** 평가 — 왜 `&&`의 오른쪽이 실행 안 되는가 | 2.5 |
| DD2.5 | Short-circuit의 실전 — NullPointerException 회피 패턴 | 2.5 |
| DD2.6 | **De Morgan 법칙** — 복합 부정의 기계적 변환 | 2.6 |
| DD2.7 | `if-else if-else` 체인 — 첫 true에서 멈추는 메커니즘 | 2.3, 2.4 |
| DD2.8 | 중첩 `if` vs 복합 조건 — 언제 어느 쪽이 올바른가 | 2.4, 2.5 |
| DD2.9 | **Dangling else** — `else`가 어느 `if`에 붙는가 | 2.3 |
| DD2.10 | `while` 루프 **종료 시점의 변수 상태** | 2.7 |
| DD2.11 | `for` 루프 3부분 실행 순서 — init → cond → body → update | 2.8 |
| DD2.12 | **Off-by-one** — `<` vs `<=`의 반복 횟수 차이 4가지 | 2.8 |
| DD2.13 | `for`의 초기화/조건에서 `.length` vs `.length()` | 2.8 |
| DD2.14 | `for`와 `while`이 **논리적으로 등가**인 이유 | 2.7, 2.8 |
| DD2.15 | **무한 루프**가 생기는 3가지 메커니즘 | 2.7 |
| DD2.16 | 중첩 루프 **반복 횟수 계산** — 외 n × 내 m = n×m | 2.11 |
| DD2.17 | 표준 알고리즘 — min/max 초기값 **두 가지 전략** | 2.9 |
| DD2.18 | 표준 알고리즘 — 자릿수 추출 (`% 10`, `/ 10`) 메커니즘 | 2.9 |
| DD2.19 | String 알고리즘 — **substring 순회**의 관용구 | 2.10 |
| DD2.20 | **Run-time 분석** — O(n) vs O(n²) 판별 규칙 | 2.12 |

---

## DD2.1 `boolean` 타입의 엄격성 — Java는 정수를 조건으로 못 씀

### 시험 출제 형태
> 다음 중 컴파일되는 것은?
> ```java
> int x = 5;
> if (x) { ... }        // (A)
> if (x > 0) { ... }    // (B)
> if (x = 0) { ... }    // (C)
> if (x == 0) { ... }   // (D)
> ```

### 메커니즘 — `if`의 조건은 **정확히 `boolean` 타입**만

C/C++과 달리 Java는 **정수·참조의 암묵적 boolean 변환을 금지**한다. `if (...)`, `while (...)`, `for (...; ...; ...)`의 조건부에는 반드시 `boolean` 값이 와야 한다.

### 답 분석

- (A) `if (x)` → **컴파일 에러**. `x`는 `int`지 `boolean` 아님.
- (B) `if (x > 0)` → OK. `>` 결과는 `boolean`.
- (C) `if (x = 0)` → **컴파일 에러**. `=`는 대입 연산자이고 결과는 대입된 값(int 0)이라 `boolean` 아님. (C/C++에서는 컴파일은 되지만 0은 false로 처리 — Java는 애초에 막아버림)
- (D) `if (x == 0)` → OK. `==` 결과는 `boolean`.

### 시험 함정 — `=` vs `==`

`if (x = 0)`이 Java에서 컴파일 안 된다는 사실은 C에서 넘어온 학생이 자주 놓친다. 반대로 `if (b = true)` (b가 boolean일 때)는 **컴파일된다** — 대입된 값이 `true`이므로 조건부가 `boolean`이 됨. 항상 `true`로 평가되어 의도와 다르게 동작하므로 시험 출제 단골.

```java
boolean flag = false;
if (flag = true) { ... }   // 컴파일 OK, 항상 실행됨 (logic error)
if (flag == true) { ... }  // 의도한 비교
```

---

## DD2.2 관계 연산자 6종과 타입 규칙

### 시험 출제 형태
> 다음 중 컴파일 에러는?
> ```java
> "abc" == "abc"       // (A)
> "abc".equals("abc")  // (B)
> "abc" < "abd"        // (C)
> ```

### 6개 관계 연산자

| 연산자 | 의미 | 허용 피연산자 |
|-------|-----|-----------|
| `==` | 같음 | primitive, reference |
| `!=` | 다름 | primitive, reference |
| `<`, `<=`, `>`, `>=` | 대소 | **primitive number만** (int, double) |

### 메커니즘

- `==`/`!=`는 primitive엔 값 비교, reference엔 주소 비교 (DD1.14)
- `<` 류 네 개는 **숫자 타입에만 적용**. String이나 객체에 쓰면 **컴파일 에러**.

### 답 분석
- (A) `==` 허용, 값은 true (리터럴 풀 덕분)
- (B) `.equals()` — String 비교 관용구, true
- (C) `<` 연산자는 String에 못 씀 → **컴파일 에러**

문자열 대소 비교는 `"abc".compareTo("abd") < 0` 관용구를 써야 한다. (DD1.19)

### 시험 함정

```java
// String 정렬 조건
if (s1 < s2) { ... }                    // 에러
if (s1.compareTo(s2) < 0) { ... }       // OK
```

---

## DD2.3 `&&`, `||`, `!`의 진리표와 평가 순서

### 진리표

| A | B | A && B | A \|\| B | !A |
|---|---|--------|----------|-----|
| T | T | T | T | F |
| T | F | F | T | F |
| F | T | F | T | T |
| F | F | F | F | T |

### 우선순위 (DD1.5 복습·확장)

관계 연산자(`<`, `<=`, `>`, `>=`, `==`, `!=`)와 논리 연산자(`!`, `&&`, `||`)를 섞어 쓸 때 **완전한 우선순위**:

```
(높음) 단항 !  >  *  /  %  >  +  -  >  <  <=  >  >=  >  ==  !=  >  &&  >  ||  (낮음)
```

한 줄 요약: **산술 > 관계 > 논리**. 즉 `x > 0 && y < 10`은 괄호 없이도 `(x > 0) && (y < 10)`으로 안전하게 읽힌다.

### 시험 함정 — 괄호 없이 뒤섞었을 때

```java
boolean x = true, y = false, z = true;
boolean r = !x && y || z;
// = ((!x) && y) || z
// = (false && false) || true
// = false || true
// = true
```

### 관계·논리 섞인 예

```java
int a = 5, b = 3, c = 10;
boolean r = a > b && b < c || a == c;
// 관계 먼저: (a > b) && (b < c) || (a == c)
//         = true    && true   || false
// 논리: && 먼저: (true && true) || false
//             = true || false
//             = true
```

괄호를 암기하기 어렵다면 **항상 괄호를 명시적으로 쓴다**. 시험은 정답을 찾으라고 내지, 학생이 괄호 안 쓰는 스타일을 묻지는 않는다.

### 관계·논리와 `=` 대입의 엄격한 분리

```java
boolean b = x > 3;         // 관계 결과를 boolean에 대입 (OK)
if (x > 3 && y < 5) ...    // 관계 → 논리 → if 조건 (OK)
```

`=`는 모든 연산자 중 가장 낮은 우선순위 + 오른쪽→왼쪽 결합. 그래서 `boolean b = x > 3`은 "`x > 3`을 먼저 평가한 boolean 결과를 b에 대입"으로 읽힌다.

---

## DD2.4 Short-circuit 평가 — 왜 `&&`의 오른쪽이 실행 안 되는가

### 시험 출제 형태
> ```java
> int x = 0;
> if (x != 0 && 10 / x > 2) { ... }
> ```
> → 실행 중 ArithmeticException(0 나눗셈)이 나지 않는다. 왜?

### 메커니즘 — Java의 `&&`와 `||`는 **"결과가 확정되면 오른쪽을 평가하지 않는다"**

#### `&&` (AND)
- 왼쪽이 **false**면 전체 결과 무조건 false → **오른쪽 평가 안 함**
- 왼쪽이 true이면 오른쪽도 평가 필요

#### `||` (OR)
- 왼쪽이 **true**면 전체 결과 무조건 true → **오른쪽 평가 안 함**
- 왼쪽이 false이면 오른쪽도 평가 필요

### 위 문제 분석

```java
int x = 0;
if (x != 0 && 10 / x > 2)
// 왼쪽: x != 0 → 0 != 0 → false
// &&의 왼쪽이 false → 오른쪽 평가 안 함
// → 10 / x가 실행되지 않아 Exception도 안 남
// → 전체 결과 false → if 블록 안 들어감
```

### 반대로, 순서를 바꾸면 Exception 발생

```java
if (10 / x > 2 && x != 0) { ... }
// 왼쪽부터: 10 / x → 10 / 0 → ArithmeticException!
// x != 0 체크조차 가지 못함
```

### 실전 관용구 — "가드 조건을 왼쪽에"

```java
if (divisor != 0 && number / divisor > 10) { ... }  // 안전
if (i < arr.length && arr[i] > 0) { ... }           // 안전
```

---

## DD2.5 Short-circuit의 실전 — NullPointerException 회피 패턴

### 시험 출제 형태
> ```java
> String s = null;
> if (s != null && s.length() > 0) { ... }
> ```
> → NPE가 발생하지 않는다. 왜?

### 메커니즘

1. `s != null` 평가 → `null != null` → false
2. `&&`의 왼쪽이 false → 오른쪽 **평가 안 함**
3. `s.length()`가 호출되지 않아 NPE 없음

순서를 바꾸면:
```java
if (s.length() > 0 && s != null) { ... }   // 왼쪽에서 NPE!
```
왼쪽부터 평가 → `null.length()` 시도 → **NullPointerException 발생**.

### 시험 변형

#### 변형 1: `&&` → `||`로 바꿨을 때

```java
if (s == null || s.length() == 0) { ... }
// s가 null이면 왼쪽 true → 오른쪽 안 봄 → NPE 없음
// s가 null 아니면 왼쪽 false → 오른쪽 봄, s.length() 안전
```
이 패턴도 NPE 안전. **가드 조건을 왼쪽**에 두는 원칙이 핵심.

#### 변형 2: 배열 경계 체크

```java
if (i >= 0 && i < arr.length && arr[i] > 0) { ... }
// i가 -1이면 왼쪽 false → arr[i] 평가 안 함 → AIOOBE 없음
// i가 arr.length이면 중간 false → arr[i] 평가 안 함
```

#### 변형 3: 이중 null 체크

```java
if (arr != null && arr.length > 0 && arr[0] != null) { ... }
```
각 조건이 이전 조건의 성립을 전제로 한다.

---

## DD2.6 De Morgan 법칙 — 복합 부정의 기계적 변환

### 시험 출제 형태
> 다음 두 조건 중 **동치**인 것은?
> ```java
> !(x > 0 && y > 0)
> x <= 0 || y <= 0
> ```
> → 동치.

### 법칙 (암기)

```
!(A && B)  ≡  !A || !B
!(A || B)  ≡  !A && !B
```

**말로**: "NOT을 분배할 때 `&&`↔`||` 뒤집기."

### 관계 연산자 부정 표

| 원래 | 부정 |
|-----|-----|
| `x < y` | `x >= y` |
| `x <= y` | `x > y` |
| `x > y` | `x <= y` |
| `x >= y` | `x < y` |
| `x == y` | `x != y` |
| `x != y` | `x == y` |

### 적용 예

```
!(x > 0 && y > 0)
= !(x > 0) || !(y > 0)
= x <= 0 || y <= 0
```

### 시험 함정 — 부등호 헷갈림

`!(x > 0)`는 `x < 0`이 **아니라** `x <= 0`이다 (0도 포함). 시험은 정확히 이 경계에서 오답을 유도한다.

### 변형 기출

```java
// 원래
while (x > 0 && y < 10) { ... }

// "언제 루프가 끝나는가?" → 조건의 부정
// 종료 조건: !(x > 0 && y < 10) = x <= 0 || y >= 10
```

루프 종료 조건 = 루프 진행 조건의 **부정**. De Morgan을 써서 기계적으로 유도한다.

---

## DD2.7 `if-else if-else` 체인 — 첫 true에서 멈추는 메커니즘

### 시험 출제 형태
> ```java
> int x = 15;
> if (x > 0) System.out.println("A");
> else if (x > 10) System.out.println("B");
> else System.out.println("C");
> ```
> 출력은? → **`A`** (not `A B`)

### 메커니즘 — 체인의 조건을 **위에서 아래로** 평가, 첫 true를 만나면 **나머지 스킵**

체인 구조는 **상호 배타(mutually exclusive)** 분기다.
```
if (조건1)       ─── 조건1 true → 블록1 실행, 끝
else if (조건2)  ─── 조건1 false, 조건2 true → 블록2 실행, 끝
else if (조건3)  ─── 조건1,2 false, 조건3 true → 블록3 실행, 끝
else             ─── 모두 false → else 블록 실행
```

위 예에서 `x > 0`이 먼저 true이므로 `x > 10`은 **평가조차 안 됨**. 출력은 "A"만.

### 시험 함정 — 독립 `if` vs 체인

```java
// 독립 if (else if 아님)
if (x > 0) System.out.println("A");
if (x > 10) System.out.println("B");
// x=15일 때 출력: "A"와 "B" 둘 다!
```

두 `if`를 줄바꿈만 해서 이어 놓으면 **독립적으로 모두 평가**된다. 학생들이 헷갈리는 포인트.

### 올바른 체인 작성 — "더 좁은 조건을 위에"

```java
// 잘못: x > 10에 걸리는 값이 아무것도 없음
if (x > 0) ...
else if (x > 10) ...   // x > 10이면 이미 x > 0에 잡힘!

// 맞음: 더 구체적인 조건을 위에
if (x > 10) ...
else if (x > 0) ...
else ...
```

---

## DD2.8 중첩 `if` vs 복합 조건 — 언제 어느 쪽이 올바른가

### 시험 출제 형태
> 다음 두 코드가 동일한 결과를 내는가?
> ```java
> // (A)
> if (x > 0) {
>     if (y > 0) System.out.println("both positive");
> }
> 
> // (B)
> if (x > 0 && y > 0) System.out.println("both positive");
> ```
> → **동일**.

### 메커니즘 — 중첩 `if`는 `&&`와 논리적으로 같다

```
if (A) { if (B) { X; } }    ≡    if (A && B) { X; }
```

### 차이가 생기는 경우 — **else가 붙을 때**

```java
// (C) 중첩 if with else
if (x > 0) {
    if (y > 0) System.out.println("P1");
    else       System.out.println("P2");
}

// (D) && with else
if (x > 0 && y > 0) System.out.println("P1");
else                System.out.println("P2");
```

x=5, y=-3일 때:
- (C): 내부 if-else가 y>0를 체크 → y<=0 → "P2"
- (D): 외부 if가 false → "P2"

x=-5, y=5일 때:
- (C): 외부 if가 false → **아무것도 안 찍음**
- (D): 전체 조건 false → "P2"

**결론**: else 붙으면 두 형태가 다르다. 시험은 정확히 이 경계를 묻는다.

### 안전한 작성 규칙

- 양쪽 조건이 다 필요하고 둘 다 만족 안 할 때 else를 원하면 → **`&&` + 단일 if-else**
- 내부 조건만 분기하고 싶으면 → **중첩 if-else**

---

## DD2.9 Dangling else — else가 어느 if에 붙는가

### 시험 출제 형태
> ```java
> int x = 5, y = -2;
> if (x > 0)
>     if (y > 0) System.out.println("A");
> else System.out.println("B");
> System.out.println("C");
> ```
> 출력은?

### 메커니즘 — `else`는 **가장 가까운 (중괄호 없는) `if`에 붙는다**

들여쓰기는 무관하다. Java는 공백을 무시하고 토큰 순서로만 판단. 위 코드의 `else`는 **안쪽 if (`if (y > 0)`)에 붙는다**. 실제 의미는:

```java
if (x > 0) {
    if (y > 0) System.out.println("A");
    else       System.out.println("B");
}
System.out.println("C");
```

x=5, y=-2:
- x > 0 → 안쪽 진입
- y > 0 → false → else 실행 → "B"
- 그 다음 "C"

출력: **"B"와 "C"**.

### 시험 함정

학생은 들여쓰기 보고 "else가 바깥 if에 붙는다"고 착각:
```java
if (x > 0)
    if (y > 0) System.out.println("A");
else System.out.println("B");    // ← 이거 바깥 if에 붙는다고 오해
```
하지만 Java 문법 규칙은 **가장 가까운 if**. 따라서 실제론 안쪽 if의 else.

### 방지책 — 항상 **중괄호**

```java
if (x > 0) {
    if (y > 0) {
        System.out.println("A");
    }
} else {
    System.out.println("B");    // 이제 바깥 if의 else
}
```

FRQ 답안은 **항상 중괄호를 쓰라**는 불문율은 이 함정을 피하기 위함.

### 한 줄 if 없이 쓸 때의 더 큰 함정

`if (cond) statement;` 형태 (중괄호 생략)는 **딱 다음 한 문장만 if 블록**이다. 학생이 이걸 착각해서 여러 문장을 묶이는 줄 알면 버그.

```java
// 잘못 생각한 의도: x>0이면 두 줄 모두 실행
if (x > 0)
    System.out.println("pos");
    count++;          // ← if와 무관! 항상 실행됨

// 실제 동작:
// x > 0이면 "pos" 출력
// 어떤 x 값이든 count++ 실행
```

들여쓰기가 의도를 드러내지만 Java는 들여쓰기를 무시한다. 컴파일러에겐:
```
if (x > 0) System.out.println("pos");
count++;     // 별개 문장, if와 무관
```

### 시험 트레이스

```java
int x = -5, count = 0;
if (x > 0)
    count = 10;
    count++;
System.out.println(count);    // ?
```

- `x > 0` → false → `count = 10;` 안 함
- `count++;`는 if 밖이라 **무조건 실행** → count = 0 + 1 = 1
- 출력: **1**

학생은 들여쓰기 보고 "count가 아무것도 안 될 줄" 생각하지만 **실제론 1**.

### 불변 규칙 — FRQ는 **항상 중괄호**

```java
if (cond) {
    statement1;
    statement2;
}

if (cond) {
    singleStatement;
}
```

한 문장만 있어도 `{}`를 씀으로써:
1. Dangling else 함정 회피
2. 여러 문장 추가할 때 버그 방지
3. 채점자가 읽기 쉬움 → 감점 위험 제로

### 시험 MCQ 변형

```java
if (a > 0)
    if (b > 0)
        c++;
else c--;
```

들여쓰기는 "a>0이고 b<=0이면 c--"처럼 보이지만 Java는 **else를 가장 가까운 if에 붙인다**. 즉 **안쪽 if의 else**. 실제 의미:
```java
if (a > 0) {
    if (b > 0) c++;
    else c--;              // b <= 0일 때 (a > 0 전제)
}
// a <= 0일 때는 아무 것도 안 함
```

MCQ는 정확히 이 차이를 묻는다.

---

## DD2.10 `while` 루프 종료 시점의 변수 상태

### 시험 출제 형태
> ```java
> int i = 0;
> while (i < 5) {
>     i++;
> }
> System.out.println(i);
> ```
> 출력은? → **5**

### 메커니즘 — 루프는 **조건이 false가 되는 순간** 종료

종료 시점의 `i` 값은 **조건 `i < 5`를 false로 만드는 첫 값**이다.

### 트레이스 표

| iter 전 i | 조건 i<5 | body 실행 후 i |
|----------|--------|------------|
| 0 | true | 1 |
| 1 | true | 2 |
| 2 | true | 3 |
| 3 | true | 4 |
| 4 | true | 5 |
| 5 | **false** | (body 안 들어감) |

→ 종료 시 `i = 5`.

### 변형 기출

```java
int i = 1;
while (i * 2 < 20) {
    i *= 2;
}
System.out.println(i);
```

| iter | i 시작 | i*2<20 | i 끝 |
|-----|-------|--------|-----|
| 1 | 1 | true | 2 |
| 2 | 2 | true | 4 |
| 3 | 4 | true | 8 |
| 4 | 8 | true | 16 |
| 5 | 16 | **32<20=false** | (안 들어감) |

→ 출력 **16**.

### 시험 핵심 규칙

> "종료 시점의 변수값 = **조건이 false가 되는 순간의 값**"

트레이스 표를 그려 **조건이 false가 된 행**의 변수값을 읽는다.

---

## DD2.10b Sentinel-controlled vs Count-controlled Loop — 두 루프 구조의 본질

### 시험 출제 형태 (CED 2.1 LO)
> 다음 두 루프 중 **sentinel-controlled**인 것은?
> ```java
> // (A)
> for (int i = 0; i < 10; i++) process(arr[i]);
> 
> // (B)
> int input = read();
> while (input != -1) {
>     process(input);
>     input = read();
> }
> ```
> → (B)

### 두 구조의 정의

| 구조 | 종료 조건 | 언제 사용? |
|-----|---------|---------|
| **Count-controlled** | **반복 횟수**를 미리 알고 있음 | 고정 횟수 반복, 배열 전체 순회 |
| **Sentinel-controlled** | 특수 값(sentinel)을 만나면 종료 | 입력 개수 미정, "끝" 표시값까지 읽기 |

### Count-controlled 패턴

```java
// 명확한 반복 횟수
for (int i = 0; i < n; i++) { ... }
for (int i = 0; i < arr.length; i++) { ... }

// while로 변환
int i = 0;
while (i < n) { ... ; i++; }
```

### Sentinel-controlled 패턴

```java
// 특정 값을 만나면 종료 (sentinel = -1)
int value = getNext();
while (value != -1) {
    process(value);
    value = getNext();
}

// 배열에서 sentinel까지만 처리
int i = 0;
while (i < arr.length && arr[i] != 0) {  // 0이 sentinel
    process(arr[i]);
    i++;
}
```

### 구조적 차이 — 왜 분류가 중요한가

| 관점 | Count-controlled | Sentinel-controlled |
|-----|---------------|-------------------|
| 전제 | 반복 횟수 확정 가능 | 미리 모름 |
| 종료 보장 | 자동 (변수 증가) | sentinel 도달 시 (도달 안 하면 무한) |
| 대표 구조 | `for` | `while` |
| 시험 함정 | off-by-one (DD2.12) | sentinel 안 만남 → 무한 루프 |

### 시험 유형 분류

1. "배열 전체를 합산" → **Count-controlled** (for with length)
2. "파일에서 EOF까지 읽기" → **Sentinel-controlled** (while with hasNext)
3. "점수가 0 이하까지만 읽기" → **Sentinel-controlled**
4. "10번 반복" → **Count-controlled**

### 혼합 — 두 구조 모두 쓸 때

```java
// 배열 순회 + 조건으로 조기 종료 = 두 구조 하이브리드
int i = 0;
while (i < arr.length && arr[i] > 0) {   // count + sentinel
    sum += arr[i];
    i++;
}
```

이 형태는 "count-bounded sentinel" — 배열 끝까지 또는 음수 만날 때까지. Short-circuit으로 AIOOBE 방어 (DD2.5).

### 무한 루프 방지 — 메커니즘 (DD2.15 연결)

- Count-controlled: update 식이 조건을 **언젠가 false**로 만들어야 함
- Sentinel-controlled: 입력 흐름이 sentinel을 **반드시 포함**해야 함 (안 그러면 EOF 도달 후 문제)

### 실전 — 파일 읽기 (DD4.9 연결)

```java
Scanner sc = new Scanner(new File("input.txt"));
while (sc.hasNext()) {           // sentinel = EOF
    String word = sc.next();
    process(word);
}
sc.close();
```

`hasNext()`가 false가 되는 순간(=파일 끝)이 sentinel. AP CSA 파일 입력은 **항상 sentinel-controlled**.

---

## DD2.11 `for` 루프 3부분 실행 순서 — init → cond → body → update

### 시험 출제 형태
> ```java
> for (int i = 0; i < 3; i++) {
>     System.out.print(i);
> }
> ```
> 출력은? → **012**

### 메커니즘 — for의 실행 순서

```
for (init ; cond ; update) { body }
```

1. **init** 한 번 실행
2. **cond** 평가 → false면 종료
3. **body** 실행
4. **update** 실행
5. 2로 돌아가기

### 트레이스 표

| 단계 | i | 비고 |
|-----|---|-----|
| init | 0 | 초기화 |
| cond | 0 < 3 → true | body로 |
| body | 출력 "0" | |
| update | i = 1 | |
| cond | 1 < 3 → true | |
| body | 출력 "1" | |
| update | i = 2 | |
| cond | 2 < 3 → true | |
| body | 출력 "2" | |
| update | i = 3 | |
| cond | 3 < 3 → **false** | 종료 |

출력: `012`, 종료 시 `i = 3`.

### 시험 함정 — body에서 i 변경

```java
for (int i = 0; i < 10; i++) {
    System.out.print(i);
    i++;   // body 안에서도 i 증가
}
// 출력: 0, 2, 4, 6, 8
```

body와 update 둘 다에서 i가 증가하므로 각 반복마다 i가 2 증가. 시험은 이런 미묘한 동작을 trace시켜 "몇 번 반복?"을 묻는다.

---

## DD2.12 Off-by-one — `<` vs `<=`의 반복 횟수 차이 4가지

### 시험 출제 형태
> 다음 네 루프의 **반복 횟수**는?
> ```java
> for (int i = 0; i < 5; i++)   (A)
> for (int i = 0; i <= 5; i++)  (B)
> for (int i = 1; i < 5; i++)   (C)
> for (int i = 1; i <= 5; i++)  (D)
> ```

### 공식

> `for (int i = a; i <op> b; i++)`
> - `op` = `<`: 반복 횟수 = `b - a`
> - `op` = `<=`: 반복 횟수 = `b - a + 1`

### 적용

| 루프 | 공식 | 횟수 | i 값 |
|-----|-----|-----|-----|
| (A) | 5-0 | 5 | 0,1,2,3,4 |
| (B) | 5-0+1 | 6 | 0,1,2,3,4,5 |
| (C) | 5-1 | 4 | 1,2,3,4 |
| (D) | 5-1+1 | 5 | 1,2,3,4,5 |

### 배열 순회 관용구

```java
// 전체 순회 — 정확히 arr.length번
for (int i = 0; i < arr.length; i++)

// 역순 순회
for (int i = arr.length - 1; i >= 0; i--)

// 연속 쌍 비교 — arr.length - 1번
for (int i = 0; i < arr.length - 1; i++) {
    arr[i]과 arr[i+1] 비교
}
```

### 시험 함정 — `<=`와 `arr.length`

```java
for (int i = 0; i <= arr.length; i++) {
    arr[i] ...   // ← 마지막 반복에서 arr[arr.length] 접근 → AIOOBE!
}
```

`<= arr.length`는 인덱스가 범위를 넘어 `arr[arr.length]`에 접근하므로 **ArrayIndexOutOfBoundsException**. 항상 `< arr.length`가 맞다.

---

## DD2.13 `for`의 초기화/조건에서 `.length` vs `.length()`

### 시험 출제 형태
> ```java
> int[] arr = {1, 2, 3};
> String s = "abc";
> for (int i = 0; i < arr.length; i++) ...    // (A)
> for (int i = 0; i < s.length(); i++) ...    // (B)
> ```
> 둘 다 3번 반복. 차이는?

### 규칙 (암기)

| 대상 | 길이 |
|-----|-----|
| **배열** (`int[]`, `String[]` 등) | `arr.length` — **괄호 없음** (field) |
| **String** | `s.length()` — **괄호 있음** (method) |
| **ArrayList** | `list.size()` — 다른 이름 |

### 왜 다른가

- 배열은 Java에서 특별한 객체 — 크기가 고정이라 단순 **field**로 노출
- String은 클래스 객체 — **method**로 노출
- ArrayList도 method지만 이름이 `size()`

### 시험 함정

```java
arr.length()     // 에러 — arr.length가 맞음
s.length         // 에러 — s.length()가 맞음
list.length()    // 에러 — list.size()가 맞음
```

자주 섞어 쓰는 세 가지를 묶어 "배열=length, String=length(), ArrayList=size()" 공식으로 암기.

---

## DD2.14 `for`와 `while`이 논리적으로 등가인 이유

### 변환 규칙

```java
// for 형태
for (A; B; C) {
    body
}

// 등가인 while 형태
A;
while (B) {
    body
    C;
}
```

### 예시 변환

```java
// for
for (int i = 0; i < 5; i++) {
    sum += arr[i];
}

// 등가 while
int i = 0;
while (i < 5) {
    sum += arr[i];
    i++;
}
```

### 시험 활용

"다음 for를 while로 바꿔라" 또는 "이 while은 for로 어떻게 쓰나" 유형. **기계적 변환**이 가능하다는 걸 이해하면 된다.

### 선택 기준

- 반복 **횟수가 명확** → `for` (init/cond/update를 한 줄에)
- 반복 **횟수가 불명**, 조건만 있음 → `while`

문법은 등가지만 가독성이 다르다.

### 통합 원칙 — 종료 상태는 둘 다 "조건이 false가 되는 순간"

DD2.10에서는 while을, DD2.11에서는 for를 각각 다뤘지만 **두 루프의 종료 메커니즘은 동일**하다:

> **루프는 조건이 false로 평가되는 순간 종료되고, 그 시점의 변수값이 루프 이후의 "종료 상태"다.**

이 원칙을 **for에도 그대로 적용**하면 분리된 두 DD를 하나로 통합해 기억할 수 있다.

### for/while 공통 트레이스 표 양식

```
| 단계 | 조건 평가 | 변수값 | body 실행? |
|-----|---------|------|----------|
| 1   | T/F     | ...  | 예/아니오 |
| 2   | T/F     | ...  | 예/아니오 |
| ... | ...     | ...  | ...      |
| 끝  | F       | 종료값 | — (멈춤) |
```

### 예 — 동일 로직을 for/while로 나란히 풀기

```java
// for 형태
int sum = 0;
for (int i = 1; i <= 5; i++) sum += i;
// 종료 시: sum = 15, i = 6 (조건 6 <= 5가 false)

// 등가 while
int sum = 0;
int i = 1;
while (i <= 5) {
    sum += i;
    i++;
}
// 종료 시: sum = 15, i = 6 (동일)
```

**핵심**: 둘 다 `i=6`에서 종료. 왜? `i <= 5`가 처음으로 false가 된 값이 6이기 때문. **for와 while이 종료 상태에서 보이는 `i` 값은 항상 동일**.

### 시험 변형 — 루프 안에서 변수 여러 개 갱신

```java
int a = 0, b = 100;
while (a < b) {
    a += 3;
    b -= 2;
}
// 종료 시 a, b?
```

트레이스:
| iter | a 시작 | b 시작 | a < b? | a 끝 | b 끝 |
|------|-------|-------|-------|-----|-----|
| 1 | 0 | 100 | T | 3 | 98 |
| 2 | 3 | 98 | T | 6 | 96 |
| ... | ... | ... | T | ... | ... |
| k | | | T | ... | ... |
| 종료 | — | — | F | a ≥ b 최초 순간 | |

차이 `a - b`가 매 iter 5씩 증가 (a:+3, b:-2). 초기 `a - b = -100`. a가 b를 처음 따라잡는 순간 = `-100 + 5k ≥ 0` → `k ≥ 20`. 20번째 iter 종료 시 `a = 60, b = 60` → 조건 false → 종료. 답: **a = 60, b = 60**.

이 계산식은 FRQ에 나올 만큼 깊진 않지만 **루프 변수 2개 이상일 때 "어떤 식이 먼저 조건을 깨트리는지"를 따라가는 훈련**으로 유효.

---

## DD2.15 무한 루프가 생기는 3가지 메커니즘

### 시험 출제 형태
> 다음 중 **무한 루프**는?
> ```java
> (A) while (x > 0) { x--; }   // x의 초기값 = 5
> (B) while (true) { ... }
> (C) for (int i = 0; i < 10; ) { print(i); }
> (D) int i = 0; while (i < 5) { if (i == 3) break; i++; }
> ```

### 원인 1 — 조건이 항상 true

```java
while (true) { ... }
for (;;) { ... }       // 조건 생략 = true
```

### 원인 2 — 업데이트 식 누락

```java
for (int i = 0; i < 10; ) {   // update 부분 비어있음
    System.out.println(i);
    // i를 어디서도 증가시키지 않으므로 i=0 영원히 → 0 < 10은 항상 true
}
```

### 원인 3 — 잘못된 업데이트 방향

```java
int i = 0;
while (i < 10) {
    i--;   // 증가해야 하는데 감소 → -1, -2, ...
}
// i < 10은 영원히 참 (사실 int wrap-around 발생 후에도 대부분 참)
```

### 답 분석
- (A) 유한: x=5→4→3→2→1→0, 종료
- (B) 무한 (의도적)
- (C) **무한** (update 없음)
- (D) 유한 (break로 탈출)

### `break` / `continue`의 AP CSA 범위 정리

`break`와 `continue`는 CED 2025-26 본문에 **명시적으로 언급되지는 않지만 EXCLUSION 목록에도 없다**. 실제 AP CSA 시험·FRQ 채점 기준의 관용:

| 키워드 | 동작 | AP 시험 사용 | 근거 |
|-------|-----|---------|-----|
| `break;` | 가장 가까운 루프를 **즉시 탈출** | ✅ 사용 가능 | 발견 즉시 탈출 등 관용적 패턴으로 FRQ 답안 허용 |
| `continue;` | 이번 iteration을 건너뛰고 다음 iteration으로 | ✅ 사용 가능 | 덜 흔하지만 허용 |
| `break label;` / `continue label;` | 라벨 레이블 기반 제어 | ❌ AP 범위 밖 | 복잡한 흐름 — 출제 안 됨 |

### 실전 — 존재 확인에서의 break

```java
// 양수 존재 찾기
boolean hasPositive = false;
for (int v : arr) {
    if (v > 0) {
        hasPositive = true;
        break;       // 발견 즉시 탈출 — 효율적
    }
}
```

break 없어도 같은 결과(전체 순회). 하지만 시험에서는 **두 형태 모두 정답**으로 인정. 성능 목적이면 break 쓰는 게 낫고, 단순함 중시면 break 없이도 OK.

### return도 유사 효과

메서드 안이라면 `return`도 루프 탈출용으로 쓸 수 있다:

```java
public static int find(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) return i;   // 루프 + 메서드 모두 탈출
    }
    return -1;
}
```

FRQ에서 `return`으로 탈출하는 패턴이 **가장 흔함**.

### 시험 함정 — break 안 써야 하는 경우

```java
// 틀림: 첫 원소만 체크하고 종료
boolean allPositive = true;
for (int v : arr) {
    if (v <= 0) {
        allPositive = false;
        break;     // ← 이건 올바름 (조건 확정 시 탈출)
    }
}
// 참고: for-all에서는 break가 **최적화**로 OK, 단 결과 정답성은 동일
```

```java
// 오용 예: 합계 구하기 (break 쓰면 의도와 다름)
int sum = 0;
for (int v : arr) {
    if (v < 0) break;   // ← 음수 만나면 멈춘다 — 의도와 다름
    sum += v;
}
```

### int wrap-around의 미묘한 함정 (DD1.9 연결)

```java
for (int i = 1; i > 0; i++) { ... }
// i가 MAX_VALUE까지 증가 후 +1 하면 MIN_VALUE → 음수 → 종료
// "무한"처럼 보이나 실제로 ~2초 만에 종료
```

시험은 "이것이 무한 루프인가?" 물을 때 이 wrap-around까지 테스트할 수 있다.

---

## DD2.16 중첩 루프 반복 횟수 계산 — 외 n × 내 m = n×m

### 시험 출제 형태
> ```java
> for (int i = 0; i < 3; i++) {
>     for (int j = 0; j < 4; j++) {
>         System.out.print("*");
>     }
> }
> ```
> 출력된 `*`의 개수는? → **12** (= 3 × 4)

### 메커니즘 — 외부 루프 각 반복에 대해 내부 루프 전체가 실행

```
i=0: j=0,1,2,3 → *4
i=1: j=0,1,2,3 → *4
i=2: j=0,1,2,3 → *4
총 12개
```

### 내부 루프 조건이 외부에 의존하는 경우

```java
for (int i = 0; i < 4; i++) {
    for (int j = 0; j < i; j++) {
        System.out.print("*");
    }
    System.out.println();
}
```

| i | j 범위 | * 개수 |
|---|-------|------|
| 0 | 0 < 0 → false | 0 |
| 1 | 0 | 1 |
| 2 | 0,1 | 2 |
| 3 | 0,1,2 | 3 |
| 합 | | **6** |

출력:
```
(빈 줄)
*
**
***
```

### 시험 관용구

외부 i번, 내부 i+1번 등의 패턴 → **삼각수** 합: `1 + 2 + ... + n = n(n+1)/2`. 시험은 삼각수나 직사각형 합을 묻는다.

### 3중 중첩

```java
for (int i = 0; i < n; i++)
    for (int j = 0; j < n; j++)
        for (int k = 0; k < n; k++)
            ...
// 총 n³ 회
```

이 구조를 트레이싱하라고 하면 정말 힘들다 — AP는 거의 2중 중첩까지만 출제.

---

## DD2.17 표준 알고리즘 — min/max 초기값 두 가지 전략

### 시험 출제 형태
> 배열에서 최솟값을 찾는 올바른 코드는?
> ```java
> // (A)
> int min = 0;
> for (int v : arr) if (v < min) min = v;
> 
> // (B)
> int min = arr[0];
> for (int i = 1; i < arr.length; i++) if (arr[i] < min) min = arr[i];
> 
> // (C)
> int min = Integer.MAX_VALUE;
> for (int v : arr) if (v < min) min = v;
> ```

### 두 가지 초기값 전략

#### 전략 1 — 배열 첫 원소로 초기화 (권장)

```java
int min = arr[0];
for (int i = 1; i < arr.length; i++) {
    if (arr[i] < min) min = arr[i];
}
```

- 항상 올바름
- 배열이 비어있으면 `arr[0]`에서 AIOOBE (빈 배열 처리는 별도 체크)

#### 전략 2 — 극값으로 초기화

```java
int min = Integer.MAX_VALUE;
for (int v : arr) {
    if (v < min) min = v;
}
```

- 빈 배열이면 MIN이 `MAX_VALUE` 그대로 남음 (논리 오류 가능성)
- 양수만 있는 배열이라면 `int min = 0;`은 **틀림** (모든 값이 0보다 크면 min이 0이 되는 오류)

### 답 분석
- (A) **틀림**: 초기값 0 때문에 모든 값이 양수면 min이 0이 됨
- (B) **맞음**: arr[0]로 초기화
- (C) **맞음**: MAX_VALUE로 초기화

### 시험 핵심

> "`min = 0;` 또는 `max = 0;`은 **거의 항상 틀린다**."

최솟값은 `arr[0]`로, 최댓값도 `arr[0]`로 초기화하는 게 안전한 관용구.

### max 버전

```java
int max = arr[0];
for (int i = 1; i < arr.length; i++) {
    if (arr[i] > max) max = arr[i];
}
```

---

## DD2.18 표준 알고리즘 — 자릿수 추출 (`% 10`, `/ 10`) 메커니즘

### 시험 출제 형태
> `123`의 자릿수를 각각 출력하려면?

### 관용구

```java
int n = 123;
while (n > 0) {
    int digit = n % 10;    // 마지막 자릿수
    System.out.println(digit);
    n = n / 10;            // 마지막 자릿수 제거
}
// 출력: 3, 2, 1 (역순!)
```

### 메커니즘

- `n % 10`: 10으로 나눈 나머지 = 1의 자리
- `n / 10`: 정수 나눗셈으로 1의 자리 제거

```
n=123 → digit=3, n=12
n=12  → digit=2, n=1
n=1   → digit=1, n=0
n=0   → 종료
```

### 자릿수 개수 세기

```java
int n = 12345;
int count = 0;
while (n > 0) {
    count++;
    n /= 10;
}
// count = 5
```

### 자릿수 합

```java
int n = 123, sum = 0;
while (n > 0) {
    sum += n % 10;
    n /= 10;
}
// sum = 6 (1+2+3)
```

### 음수·0 처리 함정

```java
int n = 0;
while (n > 0) ...  // 0은 조건 false → 자릿수 0개로 처리되는 문제
```

0을 "자릿수 1개"로 세려면 do-while이 필요하지만 AP 범위 밖. 해결: 특수 처리.
```java
if (n == 0) count = 1;
else while (n > 0) { count++; n /= 10; }
```

음수는 `Math.abs(n)`으로 절댓값부터 처리.

---

## DD2.19 String 알고리즘 — substring 순회 관용구

### 시험 출제 형태
> 문자열의 각 글자를 순회하려면?

### 관용구 — `substring(i, i+1)`

```java
String s = "hello";
for (int i = 0; i < s.length(); i++) {
    String ch = s.substring(i, i + 1);
    // ch를 사용
}
```

`charAt`은 Quick Reference에 없으므로 **항상 substring 사용**.

### 표준 String 알고리즘

#### 1. 부분 문자열의 개수 세기

```java
// s 안에 "aa"가 몇 번 등장?
int count = 0;
for (int i = 0; i <= s.length() - 2; i++) {
    if (s.substring(i, i + 2).equals("aa")) count++;
}
```

경계: `i <= s.length() - 2`. "aa"는 2글자이므로 시작 가능한 마지막 i는 `length - 2`.

**일반화**: k-글자 부분 문자열을 찾는다면 `i <= s.length() - k`.

#### 2. 문자열 역순

```java
String result = "";
for (int i = s.length() - 1; i >= 0; i--) {
    result += s.substring(i, i + 1);
}
```

#### 왜 String 쌓기는 O(n²)인가 — immutable 원리의 연쇄 (DD1.16 연결)

`String`은 immutable이므로 `result += ch`는 내부적으로 **새 String 객체를 생성**하고 `result`가 새 주소를 가리키게 한다 (DD1.16). 이게 루프 안에서 일어나면:

| iter | result 길이 | 새 객체 만들 때 복사 문자 수 |
|------|-----------|---------------------|
| 1 | 1 | 1 (기존 0 + 새 1) |
| 2 | 2 | 2 |
| 3 | 3 | 3 |
| ... | ... | ... |
| n | n | n |

총 복사 문자 수 = `1 + 2 + 3 + ... + n = n(n+1)/2` → **O(n²)**.

즉 **immutable의 대가**: 반복 연결마다 점점 커지는 문자열 전체를 다시 복사해야 함. AP 시험은 Big-O 엄밀 증명을 요구하지 않지만 **"왜 n² 번 동작하나"** 메커니즘은 알아야 Unit 2.12 run-time 분석 문제에 대응 가능.

### 시험 관점 — O(n²)이 지문에 등장하는 경우

```java
String s = "";
for (int i = 0; i < n; i++) {
    s += i;
}
```

"이 코드의 실행 시간이 n에 따라 어떻게 증가하는가?" → **O(n²)**. 이유: `s += i`가 매번 점점 커지는 s를 새로 복사.

#### 3. 특정 글자만 남기기 (필터)

```java
String result = "";
for (int i = 0; i < s.length(); i++) {
    String ch = s.substring(i, i + 1);
    if (!ch.equals(" ")) result += ch;
}
// result: 공백 제거된 s
```

### 시험 함정 — substring 경계

- `s.substring(i, i+2)`는 `i`가 `s.length()-1`이면 `i+2 > length`라서 Exception
- 항상 루프 조건에 여유를 둔다: `i + k <= s.length()` 또는 `i <= s.length() - k`

---

## DD2.20 Run-time 분석 — O(n) vs O(n²) 판별 규칙

### 시험 출제 형태
> 다음 코드의 실행 횟수를 n으로 나타내면?
> ```java
> for (int i = 0; i < n; i++)
>     for (int j = 0; j < n; j++)
>         count++;
> ```
> → **n²**

### 판별 규칙 (AP 수준)

| 패턴 | 실행 횟수 | 복잡도 |
|-----|---------|-------|
| 단일 루프 `for (i = 0 ~ n)` | n | **O(n)** |
| 단일 루프 2개 순차 | n + n = 2n | **O(n)** |
| 중첩 루프 `i, j = 0 ~ n` | n × n = n² | **O(n²)** |
| 반씩 줄이는 루프 (binary search) | log₂ n | **O(log n)** |
| 중첩이지만 내부가 `j < i` | 1+2+...+n = n(n+1)/2 | **O(n²)** |

### AP 시험의 계산 방식

AP는 엄밀한 Big-O 증명을 요구하지 않는다. 대신 **"n이 2배 되면 시간이 몇 배?"** 관점.

- O(n): 2배
- O(n²): 4배
- O(log n): 1 단위 증가 (n=100일 때 약 7, n=1000일 때 약 10)

### 대표 알고리즘 복잡도 (Unit 4 준비)

| 알고리즘 | 시간 | 비고 |
|---------|-----|-----|
| Linear search | O(n) | |
| Binary search | O(log n) | 정렬된 배열 필요 |
| Selection sort | O(n²) | |
| Insertion sort | O(n²) | 거의 정렬된 경우 O(n)에 가까움 |
| Merge sort | O(n log n) | 추가 메모리 필요 |

### 시험 활용

"다음 코드는 **n=100일 때 10,000번**, **n=200일 때 40,000번** 실행된다. 복잡도는?" → O(n²).

---

## 부록 A: 루프 종료 상태 체크리스트

FRQ에서 루프 후 변수 상태를 묻는 문제가 자주 나옴. 다음 트레이스 규칙:

1. **`while`**: 조건이 **false가 되는 순간**의 변수값을 읽는다
2. **`for`**: update가 마지막으로 실행된 후의 값. 종료 시점에는 조건을 false로 만드는 i값이 남음
3. **체인 `if-else if-else`**: 처음으로 true인 블록만 실행되고 나머지는 스킵
4. **독립 여러 `if`**: 모두 독립 평가, 여러 블록이 동시 실행 가능

---

## 부록 B: short-circuit 가드 패턴 모음

| 체크하려는 것 | 안전한 패턴 |
|------------|----------|
| String이 null 아니고 비어있지 않음 | `s != null && s.length() > 0` |
| 배열 인덱스 안전 접근 | `i >= 0 && i < arr.length` |
| 0 나눗셈 방지 | `divisor != 0 && num / divisor > 0` |
| 배열 요소가 null 아님 | `arr[i] != null && arr[i].length() > 0` |
| 2차원 배열 안전 접근 | `r >= 0 && r < m.length && c >= 0 && c < m[0].length` |

**공통 원칙**: 가드 조건을 **왼쪽에** 놓아 short-circuit이 위험한 접근을 막도록 한다.

---

## 부록 C: Unit 2 출제 빈도 Top 10 유형

1. 중첩 for의 `*` 개수 세기 (16)
2. while 종료 후 변수값 (10)
3. short-circuit으로 NPE 회피 설명 (4, 5)
4. De Morgan으로 조건 변환 (6)
5. off-by-one `<` vs `<=` 비교 (12)
6. 자릿수 합/개수 알고리즘 (18)
7. `if-else if` 체인 분기 결과 (7)
8. Dangling else 매칭 (9)
9. String 순회 중 조건 만족 개수 (19)
10. n vs n² 복잡도 판별 (20)

이 10개를 변형까지 즉답 가능하면 Unit 2 MCQ는 거의 다 맞힐 수 있다.

---

## 검증 — L1 완료 체크리스트

- [x] CED 토픽 2.1~2.12 중 시험 빈출 개념 20개 메커니즘 수준 설명
- [x] 각 개념: 출제 형태 + 메커니즘 + 변형 2-3종
- [x] short-circuit의 NPE 회피 원리까지 도달
- [x] De Morgan 법칙 기계적 변환
- [x] 루프 종료 상태 트레이스 표 제공
- [x] 중첩 루프·삼각수 패턴 반복 횟수 계산
- [x] O(n) vs O(n²) AP 수준 판별 규칙
- [x] EXCLUSION (switch, do-while, break 심화) 구분
