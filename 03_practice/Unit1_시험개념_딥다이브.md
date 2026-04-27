# Unit 1 시험 개념 딥다이브
## Using Objects and Methods — 모든 시험 출제 개념의 메커니즘

> **이 파일의 원칙**
> - 시험에 등장할 수 있는 개념만 다룬다. EXCLUSION은 "왜 제외인지"만 언급한다.
> - 각 개념은 ① **시험 출제 형태** → ② **메커니즘(왜 그렇게 되는가)** → ③ **변형 문제에 적용** → ④ **2-3개 기출 스타일 문항** 순으로 전개한다.
> - 표면적 정의는 `Unit1_강의노트.md`에서 다룬다. 이 파일은 **원리 수준의 깊이**만 담당한다.

---

## 목차

| # | 개념 | 출처 토픽 |
|---|------|---------|
| DD1.1 | 에러 4종의 발견 시점과 시험 판별 | 1.1 |
| DD1.2 | primitive vs reference — 복사 규칙과 시험 함정 | 1.2, 1.12 |
| DD1.3 | 정수 나눗셈의 truncation 방향과 **음수의 trap** | 1.3 |
| DD1.4 | `%` modulo의 부호 규칙 (Java) | 1.3 |
| DD1.5 | 연산자 우선순위 & 결합성 — 시험 출제 패턴 | 1.3 |
| DD1.6 | `(int)` 캐스팅의 "0 방향 버림"과 음수 캐스팅 함정 | 1.5 |
| DD1.7 | `(double)(a/b)` vs `(double)a/b` — 괄호의 기계적 평가 | 1.5 |
| DD1.8 | `0.1 + 0.2 != 0.3` — 이진 근사와 `==` 금지 패턴 | 1.5 |
| DD1.9 | 오버플로우: `MAX_VALUE + 1`이 음수가 되는 시각 모델 | 1.5 |
| DD1.10 | 복합 대입 `+=`의 **암묵적 캐스트** 함정 | 1.6 |
| DD1.11 | 후위 `i++` 단독 문장은 IN, 표현식 내부는 OUT — 경계의 이유 | 1.6 |
| DD1.12 | Math 메서드 4종의 **반환 타입과 인자 타입** 함정 | 1.11 |
| DD1.13 | `Math.random()`의 범위 `[0.0, 1.0)` — 정수 랜덤 생성 관용구 | 1.11 |
| DD1.14 | 객체 == 참조 vs `.equals()` — 같은 내용이 왜 `false`인가 | 1.12, 1.15 |
| DD1.15 | `null`의 정체와 NullPointerException 발생 시점 | 1.12, 1.13 |
| DD1.16 | `String` immutable — 메서드가 원본을 안 바꾸는 메커니즘 | 1.15 |
| DD1.17 | `substring(a, b)`의 **exclusive b** 경계 — 인덱스 계산 함정 | 1.15 |
| DD1.18 | `indexOf` 미발견 `-1` — 경계 체크 패턴 | 1.15 |
| DD1.19 | `compareTo`의 세 가지 반환 패턴 — 부호만 신경쓰면 되는 이유 | 1.15 |
| DD1.20 | Method signature — 이름+매개변수 목록만이 시그니처인 이유 | 1.9 |
| DD1.5b | String `+` 연결 연산자 — 왼쪽→오른쪽 평가와 타입 혼합 | 1.3 |
| DD1.21 | 변수 초기화 강제 규칙 — instance vs local의 근본 차이 | 1.2, 1.3 |
| DD1.22 | Precondition / Postcondition — FRQ 지문을 읽는 규약 | 1.8 |
| DD1.23 | `new` 연산자의 3단계 메커니즘 — 객체 생성의 해부 | 1.13 |
| DD1.24 | `ClassName.method()` vs `object.method()` — 호출 문법 구분 | 1.10, 1.14 |

---

## DD1.1 에러 4종의 발견 시점과 시험 판별

### 시험 출제 형태
> "다음 중 logic error는? (A) 세미콜론 빠짐 (B) 평균을 합으로 나누지 않음 (C) 배열 범위 벗어남 (D) 변수 이름 오타"

### 메커니즘 — 발견 시점이 다르기 때문에 이름도 다르다

| 에러 | 언제 알 수 있나 | 왜 그 시점인가 |
|------|---------------|-------------|
| Syntax error | **컴파일 시** | Java 문법 규칙 위반 → 컴파일러가 바이트코드 생성 전에 거부 |
| Run-time error | **실행 중** | 문법은 맞아 바이트코드 생성됨 → 실제 실행 중에 불가능한 동작(0 나눗셈, null 접근 등)을 시도해 JVM이 Exception을 던짐 |
| Logic error | **결과를 사람이 확인한 뒤** | 문법도 맞고 실행도 끝까지 되지만 출력값이 의도와 다름. 기계는 "의도"를 모르므로 못 잡음 |
| Exception | **실행 중** | Run-time error의 구체적 형태. 이름(`ArithmeticException`, `NullPointerException` 등)이 붙은 경우 |

### 시험 판별 경로
```
문항을 읽고 → "컴파일이 안 된다" 언급?
   YES → Syntax error
   NO → "실행이 중단된다/Exception" 언급?
       YES → Run-time error (Exception)
       NO → "결과가 틀리다/예상과 다르다" 언급?
           YES → Logic error
```

### 변형 기출
1. `int avg = sum / count;`에서 `count=0`이면? → Run-time (`ArithmeticException`)
2. `int x = "hello";` → Syntax (타입 불일치는 컴파일 단계)
3. `for (int i = 0; i <= arr.length; i++)` → Logic (1개 더 접근 시도) → 실행 시 `ArrayIndexOutOfBoundsException`은 Run-time. **출제자가 "컴파일은 되지만 실행 중 중단"으로 제시하면 답은 Run-time, "결과가 이상함"으로 제시하면 Logic**

---

## DD1.2 primitive vs reference — 복사 규칙과 시험 함정

### 시험 출제 형태
> "다음 코드 실행 후 `x`의 값은?"
> ```java
> int x = 5;
> int y = x;
> y = 10;
> System.out.println(x);
> ```
> → **5**. int는 **값 자체를 복사**하므로 `y`를 바꿔도 `x`와 무관.

### 메커니즘 — 무엇이 복사되는가

**Primitive (int, double, boolean)**: 변수는 값 자체를 담는 상자. `y = x;`는 **상자 안 숫자를 복제해 다른 상자에 넣는 것**.

```
int x = 5;   →  [x|5]
int y = x;   →  [x|5]  [y|5]   (독립된 두 상자)
y = 10;      →  [x|5]  [y|10]  (x 영향 없음)
```

**Reference (String, 배열, 객체)**: 변수는 **객체의 메모리 주소**를 담는 상자. `b = a;`는 **같은 주소를 두 상자가 가리키게 만드는 것**.

```
String[] a = {"x"};    →  [a|주소#7] → [힙: "x"]
String[] b = a;        →  [a|주소#7] [b|주소#7] → 같은 힙 객체
b[0] = "y";            →  [힙: "y"]  (a, b 둘 다 영향받음!)
```

### 시험 함정: 객체 "복사"의 착각

```java
int[] arr1 = {1, 2, 3};
int[] arr2 = arr1;      // ← 이건 배열 복사가 아님! 주소 복사.
arr2[0] = 999;
System.out.println(arr1[0]);  // 1? 999?
```
→ **999**. `arr2`와 `arr1`은 같은 배열을 가리킨다.

진짜 배열 복사는 새 배열을 만들어 요소를 일일이 옮겨야 한다 (Unit 4에서 학습).

### String의 특수성
String은 reference type이지만 **immutable**이라 이런 aliasing 버그가 안 생긴다. `s2 = s1; s2 = "new";`는 `s2`만 새 String을 가리키게 바뀔 뿐 `s1`은 그대로. → **DD1.16 참조**

---

## DD1.3 정수 나눗셈의 truncation 방향과 음수의 trap

### 시험 출제 형태
> `-7 / 2`의 결과는? → **-3** (not -4)

### 메커니즘 — Java `/`는 **"0 방향으로 버림" (truncation toward zero)**

두 int를 `/`로 나누면 결과는 int. 소수부를 **수학적 내림(floor)이 아닌 0 쪽으로 잘라낸다**.

```
 7 / 2 = 3.5 → 3   (0에 가까운 정수 = 3)
-7 / 2 = -3.5 → -3 (0에 가까운 정수 = -3, NOT -4)
```

수학의 floor은 `-7/2 = -4`지만 Java의 int 나눗셈은 `-3`이다. 이 차이가 **시험 MCQ 단골**.

### 시각 모델
```
음수 영역 ← ─────────── 0 ─────────── → 양수 영역
   -4  -3.5  -3          0          3  3.5  4
       ↓ 0 방향 버림      0 방향 버림 ↓
       -3                             3
```

### 왜 Java가 이렇게 하나
컴파일러가 **하드웨어 div 명령**을 그대로 쓰기 때문. x86/ARM CPU의 정수 나눗셈은 truncation-toward-zero가 표준. 이 깊이는 시험에 안 나오지만 "왜 그런지" 궁금하면 여기까지.

### 변형 기출
- `13 / 4` = 3
- `-13 / 4` = -3 (NOT -4)
- `13 / (-4)` = -3
- `-13 / (-4)` = 3

**규칙**: 계산한 뒤 결과가 양수면 소수점 버림. 음수면 0에 가까운 쪽으로 버림 (= 절댓값 기준 내림).

---

## DD1.4 `%` modulo의 부호 규칙 (Java)

### 시험 출제 형태
> `-7 % 3`의 결과는? → **-1** (not 2)

### 메커니즘 — `a % b`의 부호는 **`a`의 부호를 따른다**

Java 정의:  `a % b = a - (a / b) * b`  (여기서 `/`는 정수 나눗셈)

```
-7 % 3:
  a/b = -7/3 = -2  (0 방향 버림)
  (a/b)*b = -2 * 3 = -6
  a - (a/b)*b = -7 - (-6) = -1   ← 답
```

### 부호 규칙 표

| 피연산자 | 결과의 부호 | 예 |
|---------|----------|-----|
| 양 % 양 | 양 또는 0 | `7 % 3 = 1` |
| 음 % 양 | **음** 또는 0 | `-7 % 3 = -1` |
| 양 % 음 | 양 또는 0 | `7 % -3 = 1` |
| 음 % 음 | **음** 또는 0 | `-7 % -3 = -1` |

**규칙 한 줄**: 결과의 부호 = 좌측 피연산자의 부호.

### 시험 활용 — 짝수/홀수 판정

```java
if (n % 2 == 0) { ... }  // 짝수
if (n % 2 != 0) { ... }  // 홀수 — 단, n이 음수면 -1도 포함해야 함
// 안전한 홀수 판정: if (n % 2 != 0)  또는  Math.abs(n) % 2 == 1
```

음수 홀수 판정 시 `n % 2 == 1`로 쓰면 `-3 % 2 = -1`이므로 **false**가 되어 버그. 시험에서 이 함정이 자주 나온다.

---

## DD1.5 연산자 우선순위 & 결합성 — 시험 출제 패턴

### 시험 출제 형태
> `int result = 2 + 3 * 4;`에서 `result`는? → **14** (not 20)

### 우선순위 표 (AP 범위)

| 순위 | 연산자 | 결합성 |
|-----|-------|------|
| 1 | `()` 괄호 | — |
| 2 | 단항 `-`, 단항 `+`, `!`, `(type)` 캐스트 | 오른쪽→왼쪽 |
| 3 | `*`, `/`, `%` | 왼쪽→오른쪽 |
| 4 | 이항 `+`, `-` | 왼쪽→오른쪽 |
| 5 | `<`, `<=`, `>`, `>=` | 왼쪽→오른쪽 |
| 6 | `==`, `!=` | 왼쪽→오른쪽 |
| 7 | `&&` | 왼쪽→오른쪽 |
| 8 | `\|\|` | 왼쪽→오른쪽 |
| 9 | `=`, `+=`, `-=`, `*=`, `/=`, `%=` | 오른쪽→왼쪽 |

### 메커니즘 — 파싱 순서로 변환

`2 + 3 * 4`를 파서는 다음처럼 변환:
```
    +
   / \
  2   *
     / \
    3   4
```
먼저 `3*4=12`, 그 다음 `2+12=14`.

### 시험 함정 TOP 3

1. **`+` 연결의 왼쪽→오른쪽**
   ```java
   System.out.println(1 + 2 + "a");  // "3a"
   System.out.println("a" + 1 + 2);  // "a12"
   ```
   첫 `+`부터 순서대로 평가. `"a" + 1 = "a1"`, 그 다음 `"a1" + 2 = "a12"`.

2. **캐스트와 `/` 우선순위**
   ```java
   (double) 3 / 2  // (double)3 = 3.0, 그 다음 3.0/2 = 1.5
   (double)(3 / 2) // 3/2 = 1, 그 다음 (double)1 = 1.0
   ```

3. **비교 연산자와 대입**
   ```java
   boolean b = x > 3 && y < 5;  // 우선순위: > < 먼저, && 나중
   ```

---

## DD1.5b String `+` 연결 연산자 — 왼쪽→오른쪽 평가와 타입 혼합

### 시험 출제 형태
> 다음 세 출력의 결과는?
> ```java
> System.out.println(1 + 2 + "a");   // (A)
> System.out.println("a" + 1 + 2);   // (B)
> System.out.println("a" + (1 + 2)); // (C)
> ```
> → (A) `"3a"`, (B) `"a12"`, (C) `"a3"`

### 메커니즘 — `+`의 두 가지 역할과 평가 순서

Java의 `+` 연산자는 **피연산자에 따라 의미가 바뀐다**:

| 좌 피연산자 | 우 피연산자 | `+`의 의미 |
|----------|----------|---------|
| 숫자 | 숫자 | 산술 덧셈 |
| 숫자 | String | **문자열 연결** (숫자를 자동으로 String으로 변환) |
| String | 숫자 | **문자열 연결** |
| String | String | 문자열 연결 |

그리고 **`+`는 왼쪽→오른쪽으로 결합** (DD1.5 우선순위). 그래서:

```
(A) 1 + 2 + "a"
    = (1 + 2) + "a"         ← 둘 다 숫자 → 산술
    = 3 + "a"               ← 숫자 + String → 연결
    = "3a"

(B) "a" + 1 + 2
    = ("a" + 1) + 2         ← String + 숫자 → 연결
    = "a1" + 2              ← String + 숫자 → 연결
    = "a12"

(C) "a" + (1 + 2)
    = "a" + 3               ← 괄호가 산술을 먼저 강제
    = "a3"
```

### 자동 변환의 메커니즘

`숫자 + String` 또는 `String + 숫자`일 때 Java는 숫자를 **자동으로 String으로 변환**한다. primitive는 `String.valueOf()`, 객체는 `toString()` 호출. 시험 답안으로는 이 자동 변환을 알고 있기만 하면 충분.

```java
int x = 5;
String s = "x = " + x;    // "x = 5"  (x가 "5"로 자동 변환)
System.out.println(x);    // 5 (원본 int는 그대로)
```

### 시험 단골 함정 — 괄호와 순서

```java
System.out.println(1 + 2 + "a" + 3 + 4);   // ?
// = 3 + "a" + 3 + 4
// = "3a" + 3 + 4
// = "3a3" + 4
// = "3a34"
```

**규칙 한 줄**: 왼쪽부터 평가하다가 **한번 String이 끼면 이후는 계속 연결**. 숫자 덧셈으로 돌아갈 수 없음.

### 객체의 `+` 결합

```java
Dog d = new Dog("Max");
String s = "My dog: " + d;   // d.toString()이 호출되어 연결
```

객체가 `+`의 피연산자면 자동으로 `toString()`이 불린다. **override되어 있지 않으면** `Dog@1a2b3c` 같은 기본 형태가 나온다. AP CSA에서 toString override **작성은 EXCLUSION**이지만 **호출은 IN**이다. 예를 들어 `System.out.println(obj)`도 자동으로 `toString()`을 호출한다.

---

## DD1.6 `(int)` 캐스팅의 "0 방향 버림"과 음수 캐스팅 함정

### 시험 출제 형태
> `(int)(-4.3)`의 결과는? → **-4** (not -5)

### 메커니즘 — DD1.3과 동일한 truncation-toward-zero

`(int) d`는 `d`의 소수부를 **0 쪽으로 잘라낸다**.

```
(int)  3.9  → 3    (3으로 버림)
(int)  3.1  → 3
(int) -3.1  → -3   (-3으로 버림, NOT -4)
(int) -3.9  → -3   (-3으로 버림, NOT -4)
(int) -4.3  → -4   (-4로 버림)
```

### 반올림하려면? — 시험 관용구

양수: `(int)(x + 0.5)` → `(int)(3.7 + 0.5) = (int)4.2 = 4`
음수: `(int)(x - 0.5)` → `(int)(-3.7 - 0.5) = (int)-4.2 = -4`

**왜 음수는 `-0.5`**: 음수는 `+0.5`를 더하면 오히려 0 쪽으로 당겨지기 때문. `-3.7 + 0.5 = -3.2`, 이를 (int)로 잘라내면 `-3` (반올림이 아님).

### 변형 기출

```java
double a = 7.9;
double b = -7.9;
System.out.println((int) a);        // 7
System.out.println((int) b);        // -7
System.out.println((int)(a + 0.5)); // 8  (양수 반올림)
System.out.println((int)(b - 0.5)); // -8 (음수 반올림)
```

---

## DD1.7 `(double)(a/b)` vs `(double)a/b` — 괄호의 기계적 평가

### 시험 출제 형태
> `int a=5, b=2;`에서 `(double)(a/b)`와 `(double)a/b`의 결과는?

### 메커니즘 — 캐스트는 **오른쪽 한 피연산자에만** 붙는다

**Case A**: `(double)(a/b)`
```
괄호 먼저: a/b = 5/2 = 2  (int 나눗셈)
그 다음 (double): (double)2 = 2.0
결과: 2.0
```

**Case B**: `(double)a/b`
```
캐스트는 바로 오른쪽 a에만: (double)a = 5.0
그 다음 5.0/b = 5.0/2
  → int 2가 자동으로 2.0으로 확장 (피연산자 중 하나가 double이면 다른 쪽도 double)
  → 5.0/2.0 = 2.5
결과: 2.5
```

**Case C**: `a/(double)b`도 2.5 — 같은 이유.

### 시험 핵심 통찰

> **"int끼리 나누면 이미 int. 그 후 (double)을 해도 되돌릴 수 없다."**

캐스트가 나눗셈 **전**에 적용되어야 소수 결과를 얻는다. 시험은 괄호 위치만 살짝 바꿔서 출제한다.

### 변형

```java
double r1 = (double) a / b;       // 2.5
double r2 = a / (double) b;       // 2.5
double r3 = (double) a / (double) b;  // 2.5
double r4 = (double)(a / b);      // 2.0 ← 다른 결과
double r5 = (double) a / (int) b; // 2.5 (b는 어차피 int)
```

---

## DD1.8 `0.1 + 0.2 != 0.3` — 이진 근사와 `==` 금지 패턴

### 시험 출제 형태
> `System.out.println(0.1 + 0.2 == 0.3);`의 출력은? → **false**

### 메커니즘 — double은 2진수로 소수를 저장

컴퓨터는 모든 값을 2진수로 저장한다. 0.1을 2진수로 쓰면 **무한 반복 소수**:
```
10진수 0.1 = 2진수 0.0001100110011001100... (무한 반복)
```
(십진수에서 1/3 = 0.3333...이 유한 자릿수로 못 적히는 것과 같은 원리)

double은 **유한한 비트**에 저장하므로 근사값만 저장 가능. 그래서:
- `0.1` 실제 저장값 ≈ 0.10000000000000001
- `0.2` 실제 저장값 ≈ 0.20000000000000001
- 합 ≈ 0.30000000000000004
- `0.3` 실제 저장값 ≈ 0.29999999999999999

두 근사값이 정확히 같지 않으므로 `==`는 **false**.

### 시험 패턴 — double 비교의 관용구

double을 `==`로 비교하지 마라. 대신:
```java
final double EPSILON = 0.0001;
if (Math.abs(x - y) < EPSILON) {
    // x와 y가 "거의 같다"고 본다
}
```

### 변형 기출

```java
double a = 1.0 / 3.0;
double b = a + a + a;
System.out.println(b == 1.0);  // false
System.out.println(b);          // 0.9999999999999999 근처
```

`int`끼리의 연산은 round-off 문제 없음. **오직 double·float에만 해당**.

---

## DD1.9 오버플로우: `MAX_VALUE + 1`이 음수가 되는 시각 모델

### 시험 출제 형태
> `Integer.MAX_VALUE + 1`의 값은? → **`Integer.MIN_VALUE` = -2,147,483,648**

### 메커니즘 — 원형 시계 모델 (bit 레벨은 시험 불요)

int는 32비트에 저장하므로 표현 가능한 정수가 **유한**하다. 범위는 `-2,147,483,648 ~ 2,147,483,647`. 이걸 **원형 시계**처럼 생각하라:

```
          0
       /  |  \
     ...  |  ...
    /           \
  MAX_VALUE    MIN_VALUE
       \       /
        \  ←  /
         \ / 
      (MAX + 1) → MIN으로 "한 바퀴 돌아" 넘어감
```

12시 다음이 1시가 되듯, int의 최댓값 다음이 최솟값으로 **순환(wrap-around)** 한다.

### 시험 변형

```java
Integer.MAX_VALUE + 1      // MIN_VALUE (음수)
Integer.MAX_VALUE + 2      // MIN_VALUE + 1
Integer.MIN_VALUE - 1      // MAX_VALUE (양수)
2_000_000_000 + 2_000_000_000  // 음수 (합이 MAX 초과)
```

### 시험 출제 포인트
- "다음 코드는 무한 루프가 되는가?"
  ```java
  for (int i = 1; i > 0; i++) { ... }
  ```
  → 무한 루프 아님! `i`가 결국 `MAX_VALUE`에 도달한 뒤 +1 하면 음수로 넘어가 조건 `i > 0`이 false가 되어 종료. (현실적으론 매우 오래 걸림)

---

## DD1.10 복합 대입 `+=`의 암묵적 캐스트 함정

### 시험 출제 형태
> 다음 중 컴파일되는 것은?
> ```java
> int x = 5;
> x = x + 1.5;    // (A)
> x += 1.5;       // (B)
> ```

### 메커니즘 — `+=`는 보기와 달리 **내부적으로 캐스트를 포함**

Java 명세:  `x += y;`  ≡  `x = (T)(x + y);`  (T = x의 타입)

즉 `x += 1.5;`는 내부적으로:
1. `x + 1.5`를 계산 → `5 + 1.5 = 6.5` (double)
2. `(int) 6.5`로 **자동 캐스트** → 6
3. x에 6 저장

### 두 형태의 차이

```java
int x = 5;
x = x + 1.5;    // 컴파일 에러! (double → int 묵시적 변환 불가)
x += 1.5;       // 컴파일 OK, x = 6 (자동 캐스트)
```

### 시험 답 (위 문제)
- (A) 에러
- (B) OK (단, 값 손실 발생)

→ **정답 (B)만 컴파일**. 시험에서 "왜 A는 에러고 B는 안 에러인가?" 관점.

### 변형

```java
short s = 100;
s = s + 1;     // 에러 (int + int = int, short로 돌아가는 암묵 변환 없음)
s += 1;        // OK (자동 캐스트)
```

(단, `short`는 AP 범위 밖이지만 원리 동일.)

---

## DD1.11 후위 `i++` 단독 문장은 IN, 표현식 내부는 OUT — 경계의 이유

### 시험 출제 형태
> 다음 중 AP CSA 시험 답안에서 허용되는 것은?
> (A) `i++;`
> (B) `++i;`
> (C) `arr[i++] = 5;`
> (D) `int y = i++ + 3;`

### 메커니즘 — CED의 명확한 선 긋기

CED 1.6.A.2는 다음을 EXCLUSION으로 명시:
- **Prefix 형태** (`++i`, `--i`): OUT
- **표현식 내부 사용** (`arr[x++]`, `int y = i++ + 3`): OUT

허용되는 형태:
- **단독 문장으로 post-increment/decrement**: `i++;`, `j--;` → IN

### 왜 경계가 이렇게 나뉘었나

prefix와 expression-internal은 값(평가 결과)이 중요하지만, 단독 statement로 쓸 때 `i++;`는 **값이 버려지고 부수효과만 남는다**. 부수효과(side effect)는 initialization/update에 흔히 쓰이는 관용구라 허용. 표현식 내부 `arr[i++]`는 "어떤 순서로 읽고 증가시키는가"가 미묘해 AP 수준에서 배제.

### 시험 답
(A)만 허용. B/C/D는 범위 밖.

### FRQ 작성 규칙
> "FRQ에서 `++`를 쓰려면 **한 줄 전체가 `i++;`** 형태일 때만."
> 반복문 업데이트식 `for (int i = 0; i < n; i++)`는 post-increment라서 OK (for의 update는 statement position).

`arr[i] = something; i++;` 두 줄로 나눠 쓰면 항상 안전하다.

### for 루프 update 위치가 OK인 이유 — statement position

```java
for (int i = 0; i < n; i++) {   // ← 이 i++는 statement position
    System.out.println(i);
}
```

for의 세 부분(`init ; cond ; update`) 중 **update는 statement 자리**. `i++` 하나만 있고 값이 식으로 참여하지 않으므로 "단독 문장으로 post-increment" 규칙을 **정확히 만족**한다. 즉:

- `for (int i = 0; i < n; i++)` → ✅ OK, update가 statement position
- `for (int i = 0; i < n; ++i)` → ❌ prefix 형태 — 사용 금지
- `sum += arr[i++];` → ❌ 표현식 내부 — 사용 금지
- `i++;` (한 줄) → ✅ OK
- `arr[i] = 0; i++;` (두 줄) → ✅ OK

**판별 한 문장**: `++`가 쓰인 **그 자리가 문장(statement)인가**만 보면 된다. 문장이면 OK, 표현식의 일부면 금지.

---

## DD1.12 Math 메서드 4종의 반환 타입과 인자 타입 함정

### Java Quick Reference (p.185) — **이것만 출제 가능**

```java
static int    abs(int x)
static double abs(double x)
static double pow(double base, double exponent)
static double sqrt(double x)
static double random()    // [0.0, 1.0)
```

### 함정 1: `Math.pow`는 double 반환

```java
int x = Math.pow(2, 3);   // 컴파일 에러! double를 int에 담을 수 없음
int x = (int) Math.pow(2, 3);  // OK, x = 8
```

### 함정 2: `Math.sqrt`도 double 반환

```java
int s = Math.sqrt(16);    // 에러
int s = (int) Math.sqrt(16);  // OK, s = 4
```

### 함정 3: `Math.abs`의 오버로딩

```java
int a = Math.abs(-5);        // OK, int → int, a = 5
double b = Math.abs(-3.14);  // OK, double → double, b = 3.14
int c = Math.abs(-3.14);     // 에러 (double 반환을 int에 담을 수 없음)
```

### 함정 4: `Math.pow(0, 0)`은 1

수학에서 `0^0`은 정의 안 되지만 Java는 `1.0`을 반환. 시험엔 잘 안 나오지만 알면 좋다.

### EXCLUSION — 출제 절대 불가

`Math.PI`, `Math.max`, `Math.min`, `Math.round`, `Math.ceil`, `Math.floor`, `Math.log`, `Math.sin` 등 **Quick Reference에 없는 모든 Math 메서드**.

---

## DD1.13 `Math.random()`의 범위 `[0.0, 1.0)` — 정수 랜덤 생성 관용구

### 시험 출제 형태
> `Math.random()`을 사용해 1부터 10까지의 랜덤 정수를 생성하려면?

### 메커니즘

`Math.random()` 반환값 `r`: `0.0 ≤ r < 1.0` (1.0은 **포함되지 않음**)

정수 랜덤 `min ~ max` (양 끝 포함) 관용구:
```java
int result = (int)(Math.random() * (max - min + 1)) + min;
```

### 유도

1. `Math.random()`: `[0.0, 1.0)`
2. `Math.random() * 10`: `[0.0, 10.0)` (10.0 미포함)
3. `(int)(Math.random() * 10)`: `[0, 10)` → 0, 1, 2, ..., 9 (정수 10개)
4. 1부터 10까지 원하면 `+1`: `(int)(Math.random() * 10) + 1` → 1, 2, ..., 10

### 시험 함정

```java
(int)(Math.random() * 10)        // 0 ~ 9  (10 미포함!)
(int)(Math.random() * 10) + 1    // 1 ~ 10
(int)(Math.random() * 11)        // 0 ~ 10
(int)(Math.random() * (max - min + 1)) + min  // min ~ max
```

**핵심 실수**: `(int)(Math.random() * 10) + 1`로 "1~10"이 나오는데, 학생들은 이걸 `(int)(Math.random() * 9) + 1`로 오인 (9개가 아니라 10개 필요!).

### 경계 케이스
- `Math.random()`이 0.0을 반환한 순간: `(int)(0.0 * 10) + 1 = 1` → OK
- `Math.random()`이 0.9999...일 때: `(int)(9.999 * 10) / 10 ...` → wait, let me redo.
  - `0.9999 * 10 = 9.999`, `(int)9.999 = 9`, `+1 = 10` → OK, 10이 정상 출현.

---

## DD1.14 객체 `==` 참조 vs `.equals()` — 같은 내용이 왜 `false`인가

### 시험 출제 형태
> ```java
> String a = "hello";
> String b = new String("hello");
> System.out.println(a == b);
> System.out.println(a.equals(b));
> ```
> 출력은? → `false` / `true`

### 메커니즘 — `==`는 항상 **참조 비교**, `.equals()`는 **내용 비교**

#### `==` 연산자
- primitive: 값을 비교
- reference: **주소를 비교** (같은 객체를 가리키는가?)

#### `.equals()` 메서드 (String 기본 구현)
- **문자 내용을 한 글자씩 비교**

### 시각 모델

```
String a = "hello";           // 리터럴 풀에 한 개만 존재
String b = "hello";           // 같은 리터럴 → 같은 주소
String c = new String("hello"); // new는 "힙에 새 객체" 강제

a       [주소: 1000] ──┐
b       [주소: 1000] ──┴─→ 힙: "hello"
c       [주소: 2000] ────→ 힙: "hello"  (다른 객체)

a == b  → 같은 주소 → true
a == c  → 다른 주소 → false
a.equals(c) → 내용 같음 → true
```

### 시험 규칙 (암기)

> **String은 항상 `.equals()`로 비교하라.**
> `==`는 때때로 맞지만 (literal pool 때문), 일반적으로는 문자 비교 의도라면 무조건 `.equals()`.

### 변형 기출

```java
String s1 = "abc";
String s2 = "abc";
String s3 = new String("abc");

s1 == s2         // true  (literal pool 덕분)
s1 == s3         // false
s1.equals(s2)    // true
s1.equals(s3)    // true
```

이런 미묘함 때문에 **"String 비교는 `==` 금지"가 시험의 불문율**.

### Literal pool의 메커니즘 (얕게)

같은 `"abc"` 리터럴을 코드 여러 곳에 써도 Java는 **메모리에 하나의 객체만** 만들어 공유한다 (이를 **String literal pool** 또는 **intern pool**이라 부름).

```
String s1 = "abc";   → pool의 "abc" 주소 가리킴
String s2 = "abc";   → 같은 주소 (pool 재사용)
String s3 = new String("abc");  → new는 pool이 아닌 힙에 새 객체 강제
```

**원칙**: `""` 리터럴은 pool을, `new String(...)`은 힙의 새 객체를 만든다. `==`로 비교 시 이 차이가 드러남.

### 시험 함정 — 연결 결과는 리터럴이 아닐 수도

```java
String s1 = "ab";
String s2 = "a" + "b";     // 컴파일 타임에 합쳐져 "ab"로 — pool 재사용
String s3 = "a";
String s4 = s3 + "b";       // 런타임 연결 — 새 힙 객체

s1 == s2     // true  (둘 다 pool의 "ab")
s1 == s4     // false (s4는 pool에 없음)
```

컴파일러가 상수끼리의 연결은 미리 계산하지만 변수가 섞이면 런타임 연결 → 새 객체.

### AP 시험 출제 범위

시험은 "왜 이 `==`가 true/false인가"의 **원리 판별**까지는 드물고, 보통 "String 비교는 `.equals()`를 쓰라"는 규칙 수준. 하지만 `new String(...)`을 제시하고 `==` 결과를 묻는 문제는 종종 나옴. 이 경우만 literal pool 개념을 써서 판별하면 됨.

**규칙 한 문장**: 내용 비교가 의도면 **항상 `.equals()`**. `==`가 답이 되는 경우는 "같은 리터럴 두 변수"이거나 "같은 객체에의 두 참조"뿐.

### 객체 일반 `.equals()` — 클래스가 override 하지 않으면?

Object의 기본 `.equals()`는 `==`과 동일 (참조 비교). 그래서 사용자 정의 클래스에서 **`.equals()`를 override하지 않았으면 내용이 같아도 `false`**. AP CSA에서는 override 작성이 EXCLUSION이므로, 시험에 나올 때는 "이미 override 되어 있음"이 주어진다.

---

## DD1.15 `null`의 정체와 NullPointerException 발생 시점

### 시험 출제 형태
> ```java
> String s;
> System.out.println(s.length());
> ```
> → 컴파일 에러 (`s`가 초기화되지 않음). 그런데:
> ```java
> String s = null;
> System.out.println(s.length());
> ```
> → **NullPointerException** 런타임 에러.

### 메커니즘 — `null`은 "아무 객체도 안 가리킴" 상태

reference 변수는 **주소를 담는다**. `null`은 "유효한 주소가 없다"는 특수 값.

```
String s = null;   → [s | null]  (힙 객체 안 가리킴)
s.length();        → null에 .length() 호출 시도 → JVM이 NullPointerException 발생
```

### 발생 시점

NullPointerException은 **null인 참조로 메서드/필드에 접근할 때** 발생. 단순히 null을 담고 있는 것 자체는 문제 없음.

```java
String s = null;           // OK
System.out.println(s);     // OK (null 출력됨)
int len = s.length();      // ← 여기서 NPE!
```

### 시험 단골 패턴 — 초기화 안 된 배열 요소

```java
String[] names = new String[5];
System.out.println(names[0].length());  // NPE! names[0]이 null
```

reference 타입 배열은 default가 `null`. 각 원소에 실제 객체를 넣어줘야 메서드 호출 가능.

### short-circuit으로 NPE 회피 (Unit 2.5에서 심화)

```java
if (s != null && s.length() > 0) { ... }  // 안전
if (s.length() > 0 && s != null) { ... }  // 위험! s가 null이면 NPE
```

---

## DD1.16 `String` immutable — 메서드가 원본을 안 바꾸는 메커니즘

### 시험 출제 형태
> ```java
> String s = "hello";
> s.toUpperCase();
> System.out.println(s);
> ```
> → **"hello"** (대문자 안 됨)

### 메커니즘 — String 메서드는 **새 객체를 반환**하고 원본은 절대 바꾸지 않는다

immutable(불변) = 한번 만들어지면 내부 문자열을 바꿀 수 없다. `s.toUpperCase()`는 원본 s를 바꾸지 않고 **새로운 "HELLO" 객체를 반환**한다. 반환값을 어디에도 담지 않으면 그냥 버려진다.

```
String s = "hello";             → 힙: "hello", s → "hello"
s.toUpperCase();                → 힙: "hello", "HELLO" 둘 다 존재
                                  s는 여전히 "hello" 가리킴
                                  "HELLO"는 아무도 안 가리켜서 결국 사라짐
```

### 올바른 사용

```java
s = s.toUpperCase();      // 반환값을 s에 다시 대입
System.out.println(s);    // "HELLO"
```

> ⚠️ 참고: `toUpperCase()`는 Java Quick Reference에 없으므로 AP 시험에 직접 출제되지 않는다. 같은 immutability 원리는 QR에 있는 `substring`, `replace` 대체재로 출제된다.

### QR 메서드로 동일 함정

```java
String s = "hello world";
s.substring(6);           // "world"가 반환되지만 버려짐
System.out.println(s);    // "hello world" 그대로
```

시험 함정: "메서드를 호출했는데 왜 원본이 안 바뀌지?" 답: **반환값을 잡지 않았기 때문**.

### 시험 답안 관용구

```java
// 잘못
s.substring(1, 4);

// 맞음
s = s.substring(1, 4);   // 반환값 잡아 재대입
```

### 연결(concatenation)도 마찬가지

```java
String s = "ab";
s + "c";             // "abc" 반환되지만 버려짐
s += "c";            // s = s + "c"와 동일, s가 "abc"를 가리키게 됨
```

---

## DD1.17 `substring(a, b)`의 exclusive b 경계 — 인덱스 계산 함정

### 시험 출제 형태
> `"hello".substring(1, 4)`의 결과는? → **`"ell"`** (3글자, not 4)

### 메커니즘 — **`a`부터 `b-1`까지**, `b`는 제외

```
index:    0   1   2   3   4   5
char:     h   e   l   l   o   (끝)
               ↑           ↑
            from=1       to=4 (제외)
            
"hello".substring(1, 4) → index 1,2,3 = "ell"
```

**길이 공식**: `b - a` 글자수. `substring(1, 4)` → 4-1 = 3글자.

### `substring(a)` 형태

`substring(a)`는 `substring(a, length())`와 동일. 즉 `a`부터 끝까지.

```java
"hello".substring(2);  // "llo"  (index 2,3,4)
```

### 시험 함정

```java
"hello".substring(0, 5)   // "hello"  (전체)
"hello".substring(0, 4)   // "hell"
"hello".substring(4, 5)   // "o"  (마지막 글자)
"hello".substring(5, 5)   // ""  (빈 문자열) ← 에러 아님!
"hello".substring(1, 1)   // ""  (시작=끝)
"hello".substring(4, 4)   // ""
"hello".substring(0, 6)   // StringIndexOutOfBoundsException ← 런타임 에러
"hello".substring(-1, 3)  // StringIndexOutOfBoundsException
"hello".substring(3, 2)   // StringIndexOutOfBoundsException (b < a)
```

**경계 규칙**:
- `0 ≤ a ≤ b ≤ length()` → 정상
- `a == b` → 빈 문자열 (정상)
- 그 외 → Exception

### charAt 대신 substring 관용구

CED는 `charAt`을 Quick Reference에 넣지 않았으므로 AP 답안은 **한 글자도 `substring(i, i+1)`로 꺼낸다**.

```java
String ch = s.substring(i, i + 1);   // i번째 글자
```

---

## DD1.18 `indexOf` 미발견 `-1` — 경계 체크 패턴

### 시험 출제 형태
> ```java
> String s = "apple";
> int i = s.indexOf("z");
> ```
> `i`의 값은? → **-1**

### 메커니즘

`s.indexOf(target)`:
- 찾으면: **첫 발견 위치**(0부터 시작)
- 못 찾으면: **-1**

```java
"banana".indexOf("n")     // 2  (첫 n의 위치)
"banana".indexOf("na")    // 2
"banana".indexOf("x")     // -1
"banana".indexOf("")      // 0   (빈 문자열은 항상 0)
```

### 시험 관용구 — 발견 체크

```java
int idx = s.indexOf(target);
if (idx >= 0) {
    // 찾음 — idx 사용 가능
} else {
    // 못 찾음
}
```

`idx != -1`로 써도 되지만 `idx >= 0`이 의도를 더 명확히 전달하는 관용구. 시험은 둘 다 허용.

### 함정: `indexOf` 결과를 **검증 없이 바로 인덱스로 사용**

```java
String s = "hello";
int idx = s.indexOf("z");
String before = s.substring(0, idx);  // s.substring(0, -1) → Exception!
```

**규칙**: `indexOf` 결과는 **항상 `>= 0` 체크 후** 인덱스로 사용.

### 변형 기출

```java
// 단어의 존재 여부
boolean has = s.indexOf("word") >= 0;

// 단어 뒤만 잘라내기
int p = s.indexOf(",");
if (p >= 0) {
    String rest = s.substring(p + 1);
}
```

---

## DD1.19 `compareTo`의 세 가지 반환 패턴 — 부호만 신경쓰면 되는 이유

### 시험 출제 형태
> `"apple".compareTo("banana")`의 부호는? → **음수**

### 메커니즘 — 사전 순 비교의 세 결과

`a.compareTo(b)`:
- a < b (사전순 a가 앞) → **음수**
- a == b (내용 동일) → **0**
- a > b (사전순 a가 뒤) → **양수**

구체적 숫자는 구현에 따라 다르나 **부호만 보면 된다**.

### 사전순 규칙
- 첫 다른 글자에서 **ASCII(Unicode) 코드 값** 비교
- 'A' = 65, 'a' = 97 → 대소문자 다르면 대문자가 앞
- 한 글자가 다른 쪽의 접두사이면 **짧은 쪽이 앞**

### 변형

```java
"apple".compareTo("banana")  // 음수 ('a' < 'b')
"banana".compareTo("apple")  // 양수
"apple".compareTo("apple")   // 0
"apple".compareTo("applet")  // 음수 (짧은 쪽이 앞)
"apple".compareTo("Apple")   // 양수 ('a'=97, 'A'=65)
```

### 시험 관용구 — 정렬 조건

```java
if (a.compareTo(b) < 0) { ... }  // a가 사전순 앞
if (a.compareTo(b) > 0) { ... }  // a가 사전순 뒤
if (a.compareTo(b) == 0) { ... } // 같음 (또는 a.equals(b))
```

**주의**: `a.compareTo(b) == -1`로 쓰지 마라 — 반환값은 음수이기만 하면 되고 정확히 -1일 필요 없음.

---

## DD1.20 Method signature — 이름 + 매개변수 목록만이 시그니처인 이유

### 시험 출제 형태
> 다음은 모두 같은 클래스의 메서드. 충돌(중복 정의)되는 것은?
> ```java
> (A) public int add(int a, int b)
> (B) public double add(int a, int b)
> (C) public int add(int a, double b)
> (D) public int add(double a, int b)
> ```
> → **(A)와 (B)가 충돌.**

### 메커니즘 — 시그니처 = **이름 + 매개변수 타입 순서**

Java는 메서드를 구분할 때 다음만 본다:
- 메서드 이름
- 매개변수의 **타입 목록 (순서대로)**

**반환 타입은 시그니처의 일부가 아니다**. 접근 제한자(`public`)도 아니다.

### 왜 반환 타입은 제외인가

메서드 호출 시점에 컴파일러는 인자만 보고 어떤 메서드인지 고른다. `add(3, 4)`라는 호출을 만나면 "이름 add + int,int 인자에 맞는 메서드 하나"를 찾는다. 만약 반환 타입으로 구분한다면 `add(3, 4)` 호출이 어느 쪽인지 알 수 없음. 그래서 Java는 아예 이걸 허용하지 않는다.

### 오버로딩 판정 예시

```java
int add(int a, int b)          // 시그니처: add(int,int)
double add(int a, int b)       // 시그니처: add(int,int)    ← 충돌!
int add(int a, double b)       // 시그니처: add(int,double) ← 다른 메서드
int add(double a, int b)       // 시그니처: add(double,int) ← 다른 메서드
int add(int a, int b, int c)   // 시그니처: add(int,int,int) ← 다른 메서드
```

### 시험 함정

```java
// 문제: 다음 두 메서드는 서로 오버로딩인가?
void foo(int x) { }
int foo(int x) { return x; }
```
→ **아니오, 컴파일 에러**. 이름과 매개변수가 같고 반환 타입만 달라서 Java가 구분 못함.

```java
// 문제: 다음은 오버로딩인가?
void foo(int a, int b) { }
void foo(int b, int a) { }   // 매개변수 이름만 다름
```
→ **아니오, 같은 시그니처**. 매개변수 **이름**은 시그니처에 포함되지 않는다.

---

## DD1.22 Precondition / Postcondition — FRQ 지문을 읽는 규약

### 시험 출제 형태 (FRQ)

> ```java
> /** Precondition: arr.length > 0, arr contains only positive integers.
>  *  Postcondition: returns the index of the largest element.
>  */
> public static int findMaxIndex(int[] arr) { ... }
> ```

### 메커니즘 — 계약(contract)으로서의 두 조건

FRQ 메서드는 **"계약"**으로 지문이 기술된다:

| 조건 | 의미 | 학생 책임 |
|-----|-----|--------|
| **Precondition (전제조건)** | 호출 시점에 반드시 참 | **검증하지 않는다** — "항상 참"으로 가정하고 풀이 |
| **Postcondition (사후조건)** | 메서드 종료 시점에 반드시 참 | **반드시 달성** — 모든 경로에서 |

### 왜 precondition을 체크하면 감점인가

AP FRQ의 전제조건은 "이 상황은 절대 발생 안 한다"는 **출제자의 약속**이다. 학생이 `if (arr.length == 0) return -1;` 같은 방어 코드를 넣으면:

1. **불필요한 코드** — 지문에서 "arr.length > 0 전제"인데 체크하는 건 낭비
2. **점수 영향 없음** (감점 아님, 단지 낭비) — 단, 잘못된 반환값을 넣으면 감점 가능
3. **시간 낭비** — 90분 제한에서 불필요한 줄 쓰기

**예외**: 지문이 "precondition 없음" 또는 "빈 배열일 수 있다"고 하면 그때는 반드시 처리.

### 시험 판별표

| 지문 문구 | 어떻게 해석? |
|---------|---------|
| "Precondition: arr has at least one element" | `arr.length > 0` **가정**. 체크 불필요 |
| "Precondition: target is in arr" | target은 반드시 있음. -1 반환 경로 **불필요** |
| "Precondition: 0 <= n <= 100" | 범위 체크 불필요 |
| "Postcondition: returns smallest element" | 반드시 최솟값 반환 |
| "If target is not in arr, return -1" | precondition 아님 — 엣지 처리 **필요** |
| (precondition 명시 없음) | 모든 입력에 대해 safe하게 작성 |

### 예시 — 같은 문제를 두 버전으로

#### 버전 A (precondition 명시됨)

> Precondition: arr.length > 0  
> Postcondition: returns arr[0]

```java
public static int first(int[] arr) {
    return arr[0];          // 체크 불필요
}
```

#### 버전 B (precondition 없음)

> Returns arr[0] if arr has elements, otherwise returns -1.

```java
public static int first(int[] arr) {
    if (arr.length == 0) return -1;   // 엣지 필요
    return arr[0];
}
```

### FRQ 실전 조언

> **"지문의 precondition을 신뢰하라. 출제자가 거짓말하지 않는다."**

Q2, Q3, Q4에도 동일 원리. 특히 Q3(ArrayList)에서 "list contains at least one element"라고 써 있으면 빈 리스트 체크 불요.

### 시험 코드에서 `throws IOException`의 postcondition 관점

Unit 4 파일 읽기(DD4.9)에서 `throws IOException`을 쓰는 것은 **"이 메서드는 IOException을 던질 수 있다"**는 postcondition 선언. 호출자는 이를 알고 준비해야 한다.

---

## DD1.23 `new` 연산자의 3단계 메커니즘 — 객체 생성의 해부

### 시험 출제 형태
> ```java
> Dog d = new Dog("Rex", 3);
> ```
> 위 한 줄에서 Java가 하는 일을 3단계로 설명하시오.

### 메커니즘 — `new`는 3가지 일을 한다

```
new Dog("Rex", 3)
     ↓
1. 힙(heap)에 Dog 크기만큼의 메모리 할당
   - 모든 필드를 default value로 채움 (int=0, reference=null 등)
   
2. 해당 메모리에서 생성자 호출 (Dog("Rex", 3) 실행)
   - 필드 선언 시 초기화 식 실행 (예: private int x = 5;)
   - 생성자 본체 실행 (this.name = "Rex"; this.age = 3;)
   
3. 새로 생성된 객체의 **참조(주소)를 반환**
   - 이 반환값이 d에 대입됨
```

### 시각 모델

```
[지역 변수 영역]           [힙 메모리]
d  [주소#1234] ─────────→ [Dog 객체: name="Rex", age=3]
```

### 단계별 상세 — 3단계의 순서가 중요

1. **할당**: JVM이 heap에 공간 확보. 이 시점에 필드는 **모두 default value** (DD3.6).
2. **생성자 실행 with 초기화 순서** (DD3.5):
   - 필드 선언 초기화 식 (`private int x = 10;`) → x가 10
   - 생성자 본체 (`this.x = 20;`) → x가 20
3. **참조 반환**: 이 참조값이 `d`에 저장됨. d는 heap의 객체를 가리키는 포인터(주소).

### 시험 단골 함정 — 생성자가 예외 던지면?

`new`의 2단계(생성자 실행) 중에 예외가 나면:
- 객체는 생성되지 않음 (또는 일관되지 않은 상태)
- 3단계(반환)도 실행 안 됨
- 참조가 변수에 대입 안 됨

AP CSA에서는 생성자 예외는 거의 다루지 않지만 원리는 알아둘 만함.

### 배열의 `new`도 동일 메커니즘

```java
int[] arr = new int[5];
```

1. 힙에 `int` 5개 공간 할당 + 전부 0으로 초기화
2. 배열 객체의 `length` 필드에 5 대입 (자동)
3. 배열 참조 반환, `arr`에 대입

```java
String[] names = new String[3];
```

1. 힙에 `String[]` 3개 공간 할당 + 전부 **null로 초기화**
2. `length`에 3 대입
3. 참조 반환

**함정**: `names[0]`이 자동으로 `""`가 되지 **않는다** — null이다. 메서드 호출 시 NPE. (DD1.15)

### 2D 배열 `new`

```java
int[][] grid = new int[3][4];
```

1. 힙에 **외부 배열** (크기 3) 할당 + 각 원소가 내부 배열 참조
2. **내부 배열 3개**를 각각 `new int[4]`로 생성 + 각자 힙에 저장, 모두 0으로 채움
3. 외부 배열 참조 반환

즉 `new int[3][4]`는 **1 + 3 = 4개의 heap 할당**을 한 번에 수행. 2D = array of arrays 구조의 근거(DD4.14).

### `new`가 안 쓰이는 경우 — String 리터럴

```java
String s = "hello";       // new 없음 — literal pool에서 가져옴 (DD1.14)
String s2 = new String("hello");   // new 명시 — heap에 새 객체 강제
```

대부분의 String은 literal pool 덕에 `new` 없이 생성. `new String(...)`을 명시하면 pool 우회 → 새 heap 객체.

### FRQ Q2 연결 — constructor가 `new`의 핵심

FRQ Q2에서 학생이 작성하는 생성자는 정확히 **`new` 2단계에서 호출되는 것**이다. 생성자 안의 `this.field = param;` 구문이 필드를 default value에서 원하는 값으로 바꾸는 실제 작업.

---

## DD1.24 `ClassName.method()` vs `object.method()` — 호출 문법 구분

### 시험 출제 형태

> 다음 중 컴파일 에러는?
> ```java
> Math.sqrt(16)                    // (A)
> new Math().sqrt(16)              // (B)
> Integer.parseInt("42")           // (C)
> "hello".length()                 // (D)
> "hello".substring(1, 3)          // (E)
> String.length("hello")           // (F)
> ```

### 두 가지 호출 방식

Java의 메서드 호출은 **static**이냐 **instance**냐에 따라 문법이 다르다:

| 종류 | 호출 방식 | 의미 |
|-----|---------|-----|
| **static method** | `ClassName.method()` | 클래스 자체의 기능 (특정 객체 무관) |
| **instance method** | `object.method()` | 특정 객체의 상태/행동 |

### 답 분석

- (A) `Math.sqrt(16)` → **OK**. sqrt는 static
- (B) `new Math().sqrt(16)` → 컴파일 에러. Math는 생성자 없음(private) — 인스턴스 못 만듦
- (C) `Integer.parseInt("42")` → **OK**. parseInt는 static
- (D) `"hello".length()` → **OK**. length는 instance method, `"hello"`는 String 객체
- (E) `"hello".substring(1, 3)` → **OK**. instance method
- (F) `String.length("hello")` → **컴파일 에러**. length는 static이 아님

### 시험 함정 — 문법만 보면 뭐가 static인지 모른다

학생이 코드만 보고 "이 메서드는 static인가?"를 판별해야 할 때:

**판별법**:
- `클래스이름.메서드()` 형태 → static
- `객체변수.메서드()` 형태 → instance
- **QR에 선언으로 구분** (`static`이 붙음)

### QR (Java Quick Reference) 기준

| 메서드 | 선언 | 호출 |
|-------|-----|-----|
| `Math.sqrt` | `static double sqrt(double x)` | `Math.sqrt(16)` |
| `Math.pow` | `static double pow(double a, double b)` | `Math.pow(2, 3)` |
| `Math.abs` | `static int abs(int x)` etc | `Math.abs(-5)` |
| `Math.random` | `static double random()` | `Math.random()` |
| `Integer.parseInt` | `static int parseInt(String s)` | `Integer.parseInt("42")` |
| `Double.parseDouble` | `static double parseDouble(String s)` | `Double.parseDouble("3.14")` |
| `Integer.MAX_VALUE` | `static int MAX_VALUE` (변수) | `Integer.MAX_VALUE` |
| `String.length` | `int length()` (static 없음) | `s.length()` |
| `String.substring` | `String substring(...)` | `s.substring(...)` |
| `String.equals` | `boolean equals(...)` | `s.equals(...)` |
| `String.compareTo` | `int compareTo(...)` | `s.compareTo(...)` |
| `ArrayList.size` | `int size()` | `list.size()` |
| 등... | | |

**QR의 모든 String/ArrayList/Scanner/File 메서드는 instance**. **Math/Integer/Double의 모든 메서드는 static**. 이 단순 규칙 암기.

### 시험 변형 — static과 instance를 섞은 호출

```java
double r = Math.sqrt(Integer.parseInt("16"));
// 순서: Integer.parseInt("16") → int 16
//      Math.sqrt(16) → double 4.0
// 두 static 호출이 중첩됨
```

```java
int len = "hello".length();
// "hello"는 String 객체 → .length() instance method 호출
// 결과: int 5
```

### FRQ 작성 시 고려

FRQ Q1/Q2/Q3/Q4 모든 답안에서:
- Math·Integer·Double 메서드 사용 시 → `Math.xxx()`, `Integer.xxx()` 형태 필수
- String·ArrayList·File·Scanner 메서드 → 반드시 객체 변수 뒤에 `.xxx()`
- 문법 틀리면 **컴파일 에러로 전체 점수 영향** 가능 → 엄격 체크

---

## DD1.21 변수 초기화 강제 규칙 — instance vs local의 근본 차이

### 시험 출제 형태
> 다음 중 컴파일 에러는?
> ```java
> public class A {
>     private int x;                   // (A)
>     public void foo() {
>         int y;                        // (B)
>         System.out.println(y);
>     }
> }
> ```

### 메커니즘 — 어디에 선언됐는가가 default 적용을 결정한다

Java는 변수의 **선언 위치**에 따라 초기값 제공 여부를 다르게 처리한다:

| 변수 종류 | 선언 위치 | 초기화 안 하면? |
|---------|---------|-------------|
| **Instance variable** (field) | 클래스 본문 (메서드 밖) | **자동으로 default value** (int=0, double=0.0, boolean=false, ref=null) |
| **Local variable** | 메서드/생성자 본문 | **컴파일 에러** — 사용 전 반드시 초기화 필수 |
| **매개변수 (parameter)** | 메서드 시그니처 | 호출자가 인자로 초기화해 줌 |
| **for 루프 변수** | for의 init 부분 | 거기서 초기화 |

### 위 예의 답

- (A) `private int x;` → **OK**. instance field는 default 0 자동 할당
- (B) `int y; System.out.println(y);` → **컴파일 에러**. local variable은 사용 전 초기화 필수

### 왜 Java가 이렇게 설계했나

Instance variable은 **객체 생성 시점에 메모리가 할당**되고 필드 전체를 한 번에 0으로 초기화하는 게 비용 없음. 반면 local variable은 **메서드 호출마다 스택에 새로 만들어지는데**, 개발자가 사용 전에 값을 넣지 않으면 "이전 메서드의 쓰레기값"이 남을 수 있음 → Java는 컴파일러가 선제적으로 차단.

### 시험 단골 함정 — 조건 분기에서 초기화

```java
public void foo(int x) {
    int y;
    if (x > 0) {
        y = 10;
    }
    System.out.println(y);   // ← 컴파일 에러!
}
```

`x > 0`이 false면 `y`가 초기화되지 않으므로 println에서 에러. Java 컴파일러는 **모든 분기에서 초기화가 보장되지 않으면 사용 금지**.

해결:
```java
int y = 0;               // 선언 시 초기화
int y;                   // 또는 분기 모두 커버
if (x > 0) y = 10;
else       y = -10;
```

### 시험 변형 — 배열·객체의 경우

```java
public class A {
    private int[] arr;              // field → 자동 null
    public void foo() {
        int[] local;                 // local → 사용 전 초기화 필수
        // System.out.println(local.length);   // 컴파일 에러
        local = new int[5];          // 초기화
        System.out.println(local.length);  // OK
    }
}
```

**규칙 한 문장**: 메서드 **안**에 선언된 변수는 "사용 전 초기화" 필수, **밖**(클래스 본문)에 선언된 것은 기본값 자동.

---

## 부록 A: Unit 1 시험 대비 Quick Reference 사용 규칙

### String 메서드 — 이 8개만 쓸 수 있다

| 메서드 | 반환 | 예 |
|-------|-----|---|
| `String(String str)` | String | `new String("abc")` |
| `int length()` | int | `"abc".length() → 3` |
| `String substring(int from, int to)` | String | `"abcd".substring(1,3) → "bc"` |
| `String substring(int from)` | String | `"abcd".substring(2) → "cd"` |
| `int indexOf(String str)` | int | `"abc".indexOf("b") → 1` |
| `boolean equals(Object other)` | boolean | `"a".equals("a") → true` |
| `int compareTo(String other)` | int | 부호만 의미 |
| `String[] split(String del)` | String[] | `"a,b".split(",") → {"a","b"}` |

### Math 메서드 — 이 5개만

| 메서드 | 반환 | 용도 |
|-------|-----|-----|
| `abs(int)` | int | 절댓값 |
| `abs(double)` | double | 절댓값 |
| `pow(double, double)` | double | 거듭제곱 |
| `sqrt(double)` | double | 제곱근 |
| `random()` | double | `[0.0, 1.0)` |

### 답안 작성 체크리스트

- [ ] 한 글자 추출: `charAt` 쓰지 말고 `substring(i, i+1)`
- [ ] 정수 랜덤: `(int)(Math.random() * (max - min + 1)) + min`
- [ ] String 비교: 항상 `.equals()`, `==` 쓰지 말기
- [ ] Math.pow/sqrt 반환: double, int에 담을 때 `(int)` 캐스트
- [ ] `Math.PI`, `Math.max`, `Math.min` 등 다른 Math 메서드 쓰지 말기
- [ ] `++`, `--`는 **단독 문장**에서만
- [ ] Scanner는 File 전용, `Scanner(System.in)` 금지

---

## 부록 A¼: AP CSA 에러 메시지 해석 가이드

시험 MCQ에서 "다음 코드의 결과는?" 중 선택지에 **에러 유형**이 포함되는 경우가 있다. 컴파일 에러와 런타임 에러를 정확히 구분해야 정답.

### Compile-time Error (컴파일 에러) — 실행 자체가 불가

| 메시지 의미 | 언제 발생 | 예 |
|---------|--------|---|
| `cannot find symbol` | 선언되지 않은 변수·메서드 사용 | `System.out.prinln(x)` (오타), `foo(y)` (y 미선언) |
| `incompatible types` | 타입 불일치 대입 | `int x = 3.14;` (double→int 자동 변환 불가) |
| `variable might not have been initialized` | local 변수 사용 전 초기화 안 함 | `int y; print(y);` (DD1.21) |
| `missing return statement` | non-void 메서드의 일부 경로에서 return 없음 | 조건 분기에서 일부만 return |
| `method ... cannot be applied to ...` | 메서드 시그니처 불일치 호출 | `Math.sqrt("16")` (String 넘김) |
| `class, interface, or enum expected` | 중괄호·세미콜론 실수 | 클래스 밖에 문장 넣음 |
| `';' expected` | 세미콜론 빠짐 | `int x = 5`(끝 `;`  없음) |
| `non-static variable this cannot be referenced from a static context` | static 메서드에서 instance 멤버 접근 | DD3.14 |

### Run-time Error (실행 중 예외) — 실행은 되나 중간에 멈춤

| Exception | 언제 발생 | 예 |
|-----------|--------|---|
| `ArithmeticException` | 0 나눗셈 (int만) | `int x = 10 / 0;` |
| `NullPointerException` (NPE) | null 참조로 멤버 접근 | `s.length()` 할 때 s=null (DD1.15) |
| `ArrayIndexOutOfBoundsException` (AIOOBE) | 배열 범위 밖 접근 | `arr[arr.length]`, `arr[-1]` |
| `StringIndexOutOfBoundsException` | String 범위 밖 접근 | `s.substring(0, s.length()+1)` (DD1.17) |
| `NumberFormatException` | parseInt/parseDouble 실패 | `Integer.parseInt("abc")` (DD4.10) |
| `ClassCastException` | 잘못된 타입 캐스팅 | 주로 Object 계열 (AP 범위 밖) |
| `InputMismatchException` | Scanner 타입 불일치 | `nextInt()` 호출 시 파일에 문자 (DD4.9) |
| `ConcurrentModificationException` | Enhanced for 중 컬렉션 수정 | DD4.13 |
| `StackOverflowError` | 재귀 무한 + base case 없음 | DD4.23 |

### Logic Error — 에러 메시지 없음 (DD1.1)

- 컴파일·실행 다 되지만 결과가 틀림
- 예: 평균 구할 때 `sum / count`로 int 나눗셈 사용
- **프로그램이 중단되지 않음** → 학생이 직접 발견해야

### 시험 판별 플로우

```
코드를 보고:

Q1. 세미콜론·중괄호·타입·이름이 문법적으로 맞는가?
    NO → Compile-time Error

Q2. 컴파일은 되지만 실행 중 "불가능한 동작"을 시도하는가?
    (null 호출, 배열 범위 밖, 0 나눗셈, 잘못된 캐스팅 등)
    YES → Run-time Error (특정 Exception)

Q3. 실행은 끝까지 되지만 결과가 의도와 다른가?
    YES → Logic Error (에러 메시지 없음)
```

### 대표 시험 MCQ 유형

```java
int[] arr = {1, 2, 3};
System.out.println(arr[3]);
```

→ (A) 0  (B) null  (C) **ArrayIndexOutOfBoundsException**  (D) "3"  
컴파일 OK, 실행 중 4번째 원소 접근 시도 → **(C)**

```java
String s = null;
int len = s.length();
```

→ (A) 0  (B) **NullPointerException**  (C) -1  (D) 컴파일 에러  
컴파일 OK (s는 선언 + 초기화 됨), null에 .length() → **(B)**

```java
int y;
System.out.println(y);
```

→ (A) 0  (B) **컴파일 에러**  (C) Exception  (D) null  
local 변수 초기화 안 함 → **(B)**

### 시험 관용 — Exception인지 컴파일 에러인지 헷갈릴 때

**"문법적으로 정상인가? 실행 전에 컴파일러가 거부하는가?"**를 먼저 본다.
- 선언·타입·이름·괄호가 맞으면 → 컴파일은 됨 → Run-time 또는 Logic
- 문법이 틀리면 → Compile-time

---

## 부록 A½: "0 방향 버림" 원리 통합 — DD1.3, DD1.4, DD1.6의 같은 정체

Unit 1에서 가장 자주 걸리는 세 함정은 실은 **단 하나의 원리**에서 파생된다.

### 원리 (한 줄)

> **Java의 정수 연산·캐스팅은 소수 부분을 "0에 더 가까운 정수 쪽으로" 잘라낸다 (truncation toward zero).**

### 세 맥락에서의 반복

| 맥락 | 공식 | 예 | 결과 |
|-----|-----|---|-----|
| 정수 나눗셈 `/` (DD1.3) | 수학 결과에서 소수부를 0 방향으로 버림 | `-7 / 2` | -3 (수학의 -3.5 → 0쪽인 -3) |
| 모듈로 `%` (DD1.4) | `a - (a/b)*b`, 여기서 `/`도 0 방향 버림 | `-7 % 3` | -1 (부호가 좌 피연산자 따라감) |
| 캐스팅 `(int)` (DD1.6) | double의 소수부를 0 방향으로 버림 | `(int)(-4.3)` | -4 |

### 시각 통합

```
           음수 영역          0          양수 영역
              ←────────────── 0 ──────────────→
    -4.3  -3.9  -3.1        0        3.1  3.9  4.3
     ↓     ↓     ↓                    ↓    ↓    ↓
    -4    -3    -3                    3    3    4
     └─────── 0 방향 버림 ───────┘  └─ 0 방향 버림 ─┘
```

양수: 소수점 버리면 자연스러운 내림. 음수: 수학적 내림(floor)과 **달라짐** — 0 쪽으로 가면 절댓값이 **작아지는** 방향.

### 시험 한 문장 판별

- "음수가 등장" + "정수 `/`, `%`, `(int)` 중 하나" → **0 방향 버림**을 적용하면 즉답
- 수학의 floor(항상 아래 정수) ≠ Java의 int 나눗셈/캐스팅
- `%`의 부호는 **좌 피연산자**를 따른다

이 하나의 원리를 체화하면 DD1.3, DD1.4, DD1.6 세 DD가 **같은 질문**으로 느껴진다.

---

## 부록 B: Unit 1 자주 헷갈리는 쌍 — 10초 판별표

| 상황 | A | B | 어느 쪽? |
|-----|---|---|--------|
| `(double)(5/2)` vs `(double)5/2` | 2.0 | 2.5 | 괄호 있는 쪽이 int 나눗셈 우선 |
| `-7 / 2` vs `-7 % 2` | -3 | -1 | / 는 몫, % 는 나머지 (둘 다 음수) |
| `(int)(-3.9)` vs `(int)(-4.1)` | -3 | -4 | 0 방향 버림 |
| `s == "abc"` vs `s.equals("abc")` | 주소 비교 | 내용 비교 | 항상 .equals |
| `s.substring(2, 5)` vs `s.substring(2)` | 2~4 (3글자) | 2~끝 | to는 제외 |
| `indexOf` 못 찾음 vs 빈 String 찾음 | -1 | 0 | 경계 체크 필수 |
| `Math.sqrt(16)` vs `(int) Math.sqrt(16)` | 4.0 | 4 | sqrt는 double 반환 |
| `0.1 + 0.2 == 0.3` | false | — | double `==` 금지 |
| `Integer.MAX_VALUE + 1` | MIN_VALUE | — | wrap-around |
| `null.length()` | NPE | — | 참조 호출 전 null 체크 |

---

## 검증 — L1 완료 체크리스트

- [x] Unit 1 CED 토픽 1.1~1.15 중 시험 빈출 개념 20개 메커니즘 수준 설명
- [x] 각 개념: 출제 형태 + 메커니즘 + 변형 3종 이상
- [x] Quick Reference 범위 엄격 준수 (Math.PI, charAt, toUpperCase 경고만)
- [x] EXCLUSION 항목의 "왜 제외인가"까지 설명
- [x] 시험 답안 체크리스트 + 10초 판별표 부록

다음 루프 (L2 red-team): 이 파일만으로 답할 수 없는 **변형 시험 문제**를 찾아 공백 보충.
다음 Unit (Unit 2 딥다이브): Selection and Iteration — short-circuit, 루프 종료 상태, nested iteration, run-time 분석.
