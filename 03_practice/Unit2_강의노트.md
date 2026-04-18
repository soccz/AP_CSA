# Unit 2: Selection and Iteration

> **시험 비중: 25-35%** | 약 29-31 수업시간 | AP CSA에서 가장 비중 높은 유닛 중 하나

---

## 2.1 Algorithms with Selection and Repetition (1기간)

> **쉽게 말해**: 일상에서 선택(Selection)은 "비가 오면 우산을 챙긴다", 반복(Iteration)은 "알람이 울릴 때까지 잠을 잔다"이다. 프로그래밍에서도 조건에 따라 다른 행동을 하거나(if), 조건이 맞는 동안 반복(while/for)하는 것이 핵심이다.

**CED 학습목표:** 선택(selection)과 반복(repetition)을 사용하는 알고리즘을 설명할 수 있다.

### 핵심 개념

- **선택(Selection):** 조건에 따라 서로 다른 코드 경로를 실행하는 구조 (if, if-else)
- **반복(Repetition/Iteration):** 특정 조건이 유지되는 동안 코드 블록을 반복 실행하는 구조 (while, for)
- 모든 프로그램은 **순차(sequence)**, **선택(selection)**, **반복(iteration)** 세 가지 제어 구조의 조합으로 구성된다.

```java
// 선택: 18세 이상이면 투표 가능
if (age >= 18) {
    System.out.println("투표할 수 있습니다.");
}

// 반복: 1부터 5까지 출력
int i = 1;
while (i <= 5) {
    System.out.println(i);
    i++;
}
```

### 시험 출제 포인트
- "이 알고리즘이 selection을 사용하는가, iteration을 사용하는가?" 판별 문제
- 두 구조가 결합된 코드의 동작 추적(tracing) 문제

### 연습 문제

**Q1.** 다음 중 selection과 iteration을 **모두** 사용하는 코드는?

```java
// (A)
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}

// (B)
if (x > 0) {
    System.out.println("양수");
} else {
    System.out.println("양수 아님");
}

// (C)
for (int i = 0; i < 10; i++) {
    if (i % 2 == 0) {
        System.out.println(i);
    }
}
```

<details>
<summary>정답</summary>
(C) — for 루프(iteration)와 if문(selection)을 모두 사용
</details>

---

## 2.2 Boolean Expressions (3기간)

> **쉽게 말해**: Boolean은 **예/아니오 질문**이다. "나이가 18 이상인가?" → true/false. 컴퓨터는 모든 판단을 이런 "참/거짓 질문"으로 처리한다.

**CED 학습목표:** Boolean 표현식을 작성하고 평가할 수 있다. 관계 연산자를 사용하여 값을 비교할 수 있다.

### 핵심 개념

**관계 연산자 (Relational Operators)**

| 연산자 | 의미 | 예시 |
|--------|------|------|
| `==` | 같다 | `a == b` |
| `!=` | 같지 않다 | `a != b` |
| `<` | 작다 | `a < b` |
| `>` | 크다 | `a > b` |
| `<=` | 작거나 같다 | `a <= b` |
| `>=` | 크거나 같다 | `a >= b` |

**primitive vs 객체 비교**

```java
// primitive: == 사용 OK
int a = 5;
int b = 5;
System.out.println(a == b);  // true ✅

// 객체(String 등): .equals() 사용!
String s1 = new String("hello");
String s2 = new String("hello");
System.out.println(s1 == s2);      // false ❌ (참조 비교)
System.out.println(s1.equals(s2)); // true ✅ (내용 비교)
```

**주의:** String 리터럴은 String pool 때문에 `==`가 true일 수도 있지만, **시험에서는 항상 `.equals()`를 사용해야 한다.**

```java
String s1 = "hello";
String s2 = "hello";
System.out.println(s1 == s2);      // true (같은 pool 객체) — 하지만 이것에 의존하면 안 됨!
System.out.println(s1.equals(s2)); // true (항상 안전)
```

### 시험 출제 포인트
- `==`로 String 비교하는 코드 → "예상과 다른 결과" 유형 단골
- `double` 비교 시 부동소수점 오차 가능 (하지만 AP 시험에서는 거의 안 나옴)
- Boolean 표현식의 결과를 변수에 저장 가능: `boolean isAdult = age >= 18;`

### 연습 문제

**Q1.** 다음 코드의 출력은?

```java
String a = "cat";
String b = "cat";
String c = new String("cat");
System.out.println(a == b);
System.out.println(a == c);
System.out.println(a.equals(c));
```

<details>
<summary>정답</summary>
true (String pool)<br>
false (다른 객체)<br>
true (내용 같음)
</details>

**Q2.** `boolean result = (10 > 5) == (3 < 7);`의 result 값은?

<details>
<summary>정답</summary>
true — (10 > 5)는 true, (3 < 7)은 true, true == true → true
</details>

---

## 2.3 if Statements (2기간)

**CED 학습목표:** if문을 사용하여 조건에 따라 코드를 실행할 수 있다.

### 핵심 개념

```java
// 기본 형태
if (condition) {
    // condition이 true일 때만 실행
}

// if-else
if (condition) {
    // true일 때
} else {
    // false일 때
}
```

**중괄호 생략의 위험 (Dangling Statement)**

```java
// 위험한 코드!
if (score >= 90)
    System.out.println("A");
    System.out.println("우수합니다");  // ⚠️ 항상 실행됨! if에 속하지 않음!

// 올바른 코드
if (score >= 90) {
    System.out.println("A");
    System.out.println("우수합니다");
}
```

**if 조건에 boolean 변수 사용**

```java
boolean isRaining = true;

// 좋은 코드
if (isRaining) { ... }

// 불필요하게 장황한 코드 (동작은 같지만 비추천)
if (isRaining == true) { ... }
```

### 시험 출제 포인트
- 중괄호 없는 if문에서 "어느 줄까지 if에 속하는가" 문제
- if문의 조건이 false일 때 body가 실행되지 않음 → 변수 값 추적
- `if (x = 5)` → Java에서는 **컴파일 에러** (C/C++과 다름)

### 연습 문제

**Q1.** 다음 코드에서 x가 3일 때 출력은?

```java
int x = 3;
if (x > 5)
    System.out.print("A");
    System.out.print("B");
System.out.print("C");
```

<details>
<summary>정답</summary>
BC — x > 5는 false이므로 "A"는 출력 안 됨. "B"는 if에 속하지 않으므로 항상 출력. "C"도 항상 출력.
</details>

---

## 2.4 Nested if Statements (2기간)

**CED 학습목표:** 중첩된 if문과 if-else if-else 체인을 사용할 수 있다.

### 핵심 개념

**if-else if-else 체인**

```java
int score = 85;

if (score >= 90) {
    System.out.println("A");
} else if (score >= 80) {
    System.out.println("B");
} else if (score >= 70) {
    System.out.println("C");
} else {
    System.out.println("F");
}
// 출력: B
```

**핵심 규칙:** 첫 번째로 true인 조건에서 실행하고, 나머지는 **전부 건너뜀**.

**조건 순서가 중요한 이유:**

```java
// 잘못된 순서 — score가 95여도 "C" 출력!
if (score >= 70) {
    System.out.println("C");
} else if (score >= 80) {
    System.out.println("B");     // 절대 도달 불가
} else if (score >= 90) {
    System.out.println("A");     // 절대 도달 불가
}
```

**중첩 if vs if-else if**

```java
// 중첩 if — 두 조건 모두 확인 가능
if (age >= 18) {
    if (hasLicense) {
        System.out.println("운전 가능");
    } else {
        System.out.println("면허 필요");
    }
} else {
    System.out.println("미성년자");
}
```

### 시험 출제 포인트
- if-else if 체인에서 조건 순서 바꿨을 때 결과 변화
- "이 코드와 동일한 동작을 하는 것은?" 유형에서 조건 범위 분석
- else는 **가장 가까운** if에 연결됨 (dangling else)

### 연습 문제

**Q1.** 다음 코드에서 x = 15일 때 출력은?

```java
if (x > 20) {
    System.out.print("A");
} else if (x > 10) {
    System.out.print("B");
} else if (x > 5) {
    System.out.print("C");
} else {
    System.out.print("D");
}
```

<details>
<summary>정답</summary>
B — x > 20은 false, x > 10은 true → "B" 출력 후 나머지 건너뜀
</details>

**Q2.** 다음 두 코드의 차이점은?

```java
// 코드 1
if (x > 0) System.out.print("양수 ");
if (x > 5) System.out.print("큰수 ");

// 코드 2
if (x > 0) System.out.print("양수 ");
else if (x > 5) System.out.print("큰수 ");
```

<details>
<summary>정답</summary>
코드 1: x=10이면 "양수 큰수 " 출력 (두 if 모두 독립적으로 검사)<br>
코드 2: x=10이면 "양수 " 출력 (첫 조건 true면 else if는 건너뜀. "큰수 "는 x ≤ 0이면서 x > 5일 때만 출력 → 불가능, 사실상 dead code)
</details>

---

## 2.5 Compound Boolean Expressions (2기간)

**CED 학습목표:** 논리 연산자 &&, ||, !를 사용하여 복합 Boolean 표현식을 작성하고 평가할 수 있다.

### 핵심 개념

| 연산자 | 이름 | 설명 |
|--------|------|------|
| `&&` | AND | 둘 다 true여야 true |
| `\|\|` | OR | 하나만 true여도 true |
| `!` | NOT | true ↔ false 반전 |

**진리표**

| A | B | A && B | A \|\| B | !A |
|---|---|--------|----------|----|
| T | T | T | T | F |
| T | F | F | T | F |
| F | T | F | T | T |
| F | F | F | F | T |

**Short-Circuit Evaluation (단축 평가)**

```java
// && : 왼쪽이 false면 오른쪽은 평가하지 않음
if (x != 0 && 10 / x > 2) { ... }
// x가 0이면 왼쪽이 false → 10/x 실행 안 함 → ArithmeticException 방지!

// || : 왼쪽이 true면 오른쪽은 평가하지 않음
if (name == null || name.length() == 0) { ... }
// name이 null이면 왼쪽이 true → name.length() 실행 안 함 → NullPointerException 방지!
```

**범위 검사 패턴**

```java
// x가 1 이상 10 이하인지 확인
if (x >= 1 && x <= 10) {
    System.out.println("범위 안");
}

// ⚠️ 수학처럼 쓰면 안 됨!
// if (1 <= x <= 10)  // 컴파일 에러!
```

### 시험 출제 포인트
- short-circuit으로 인한 **부작용(side effect) 회피** 패턴
- null 체크를 항상 `&&`의 **왼쪽**에 배치하는 이유
- 연산자 우선순위: `!` > `&&` > `||`

### 연습 문제

**Q1.** `x = 3, y = 7`일 때 다음 표현식의 결과는?

```java
!(x > 5) && (y > 5 || x < 0)
```

<details>
<summary>정답</summary>
true — !(false) && (true || false) → true && true → true
</details>

**Q2.** 다음 코드에서 `str`이 null일 때 NullPointerException이 발생하는가?

```java
if (str != null && str.length() > 0) {
    System.out.println(str);
}
```

<details>
<summary>정답</summary>
발생하지 않음 — str이 null이면 str != null이 false → short-circuit으로 str.length()를 호출하지 않음
</details>

---

## 2.6 Comparing Boolean Expressions / De Morgan's Laws (2기간)

**CED 학습목표:** De Morgan의 법칙을 적용하여 동치인 Boolean 표현식을 작성할 수 있다. 객체를 비교하는 다양한 방법을 구분할 수 있다.

### 핵심 개념

**De Morgan's Laws (드모르간 법칙)** — 반드시 암기!

```
!(a && b)  ==  !a || !b
!(a || b)  ==  !a && !b
```

**기억법:** NOT을 분배하면 **AND ↔ OR 바뀜**

```java
// 예시: "18세 미만이거나 면허가 없으면 운전 불가"
if (!(age >= 18 && hasLicense)) { ... }
// 드모르간 적용:
if (age < 18 || !hasLicense) { ... }
// 두 코드는 동일!
```

**객체 비교 정리**

| 비교 방법 | 비교 대상 | 용도 |
|-----------|----------|------|
| `==` | 참조(reference) | 같은 객체를 가리키는지 |
| `.equals()` | 내용(content) | 내용이 같은지 |
| `== null` | null 여부 | null 체크에는 `==` 사용 |

```java
String a = new String("hi");
String b = new String("hi");

a == b        // false (다른 객체)
a.equals(b)   // true  (같은 내용)
a == null      // false
a.equals(null) // false (NullPointerException 아님, .equals가 처리)
null.equals(a) // ⚠️ NullPointerException!
```

> **EXCLUSION:** equals 메서드의 커스텀 작성은 시험 범위 밖 (상속 개념 제거됨)

### 시험 출제 포인트
- De Morgan's Law 변환 문제는 **거의 매년 출제**
- `!(a < b)` → `a >= b` (부등호 방향 반전)
- 복잡한 조건을 단순화하는 문제
- null 비교 시 `.equals()` 대신 `==` 사용해야 하는 이유

### 연습 문제

**Q1.** 다음 표현식과 동치인 것은?

```java
!(x >= 10 && y < 20)
```

<details>
<summary>정답</summary>
x < 10 || y >= 20<br>
(드모르간: NOT 분배 + AND→OR 변환 + 부등호 반전)
</details>

**Q2.** 다음 표현식과 동치인 것은?

```java
!(a || !b)
```

<details>
<summary>정답</summary>
!a && b<br>
(드모르간: !(a || !b) → !a && !!b → !a && b)
</details>

---

## 2.7 while Loops (3기간)

> **쉽게 말해**: while 루프는 **"~할 때까지 반복"**이다. "배가 부를 때까지 밥을 먹는다" = `while (!배부름) { 밥먹기(); }`. 조건이 처음부터 false면 한 번도 실행하지 않는다 (이미 배가 부르면 밥을 안 먹는다).
>
> **for vs while 선택 기준**: 반복 횟수를 **아는** 경우 → `for`, **모르는** 경우 → `while`

**CED 학습목표:** while 루프를 사용하여 반복 알고리즘을 구현할 수 있다.

### 핵심 개념

```java
while (condition) {
    // condition이 true인 동안 반복
    // body 안에서 condition을 변화시켜야 함!
}
```

**실행 순서:** 조건 검사 → (true면) body 실행 → 조건 검사 → ... → (false면) 루프 종료

**0번 실행 가능:** 처음부터 조건이 false면 body가 한 번도 실행되지 않는다.

```java
int x = 10;
while (x < 5) {
    System.out.println(x);  // 실행 안 됨!
    x++;
}
```

**무한 루프 (Infinite Loop)**

```java
// 실수로 만드는 무한 루프
int count = 1;
while (count <= 10) {
    System.out.println(count);
    // count++를 빼먹음! → 무한 반복
}
```

**while 루프 기본 패턴**

```java
// 패턴 1: 카운터 기반
int i = 0;
while (i < 5) {
    System.out.println(i);  // 0, 1, 2, 3, 4
    i++;
}

// 패턴 2: 센티넬(sentinel) 기반
int sum = 0;
int input = scanner.nextInt();
while (input != -1) {      // -1이 입력되면 종료
    sum += input;
    input = scanner.nextInt();
}
```

### 시험 출제 포인트
- **Off-by-one error:** `<` vs `<=`에 따라 반복 횟수가 1번 차이남
  - `i = 0; while (i < 5)` → 0,1,2,3,4 → **5번** 반복
  - `i = 0; while (i <= 5)` → 0,1,2,3,4,5 → **6번** 반복
  - `i = 1; while (i < 5)` → 1,2,3,4 → **4번** 반복
  - `i = 1; while (i <= 5)` → 1,2,3,4,5 → **5번** 반복
- 루프 종료 후 변수 값 묻는 문제
- "이 루프는 몇 번 실행되는가?" 유형

### 연습 문제

**Q1.** 다음 코드의 출력은?

```java
int x = 1;
while (x < 10) {
    x *= 2;
}
System.out.println(x);
```

<details>
<summary>정답</summary>
16<br>
x: 1→2→4→8→16 (16 < 10은 false이므로 루프 종료, x는 16)
</details>

**Q2.** 다음 코드는 몇 번 "Hello"를 출력하는가?

```java
int n = 1;
while (n < 100) {
    System.out.println("Hello");
    n *= 3;
}
```

<details>
<summary>정답</summary>
5번<br>
n: 1→3→9→27→81→243 (반복 시 n값: 1, 3, 9, 27, 81 → 5번 출력 후 243에서 종료)
</details>

> **EXCLUSION (시험 범위 밖):**
> - `do-while` 루프: Java에 존재하지만 AP CSA 시험에 출제되지 않음
> - `switch` 문: 다중 분기에 유용하지만 시험 범위 밖
> - `continue` 키워드: 루프의 나머지를 건너뛰지만 시험 범위 밖
> - `for-each` (enhanced for): Unit 4에서 별도 학습

---

## 2.8 for Loops (3기간)

> **쉽게 말해**: for 루프는 **"N번 반복"**이다. "운동장 5바퀴 뛰기" = `for (int i = 0; i < 5; i++) { 뛰기(); }`. 시작(0바퀴), 조건(5바퀴 미만인가?), 증가(1바퀴 추가)가 한 줄에 모두 있다.

**CED 학습목표:** for 루프를 사용하여 반복 알고리즘을 구현할 수 있다. for와 while의 상호 변환을 이해한다.

### 핵심 개념

```java
for (initialization; condition; update) {
    // body
}
```

**실행 순서:**
1. `initialization` (1번만)
2. `condition` 검사 → false면 종료
3. `body` 실행
4. `update` 실행
5. 2번으로 돌아감

```java
for (int i = 0; i < 5; i++) {
    System.out.print(i + " ");
}
// 출력: 0 1 2 3 4
```

**for ↔ while 변환**

```java
// for 루프
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}

// 동일한 while 루프
int i = 0;
while (i < 10) {
    System.out.println(i);
    i++;
}
```

> **차이점:** for 루프의 `int i`는 루프 안에서만 유효 (scope). while 변환 시 `i`는 루프 밖에서도 접근 가능.

**다양한 for 루프 패턴**

```java
// 역순
for (int i = 10; i > 0; i--) { ... }  // 10, 9, 8, ..., 1

// 2씩 증가
for (int i = 0; i < 20; i += 2) { ... }  // 0, 2, 4, ..., 18

// 루프 변수를 바꾸지 않기! (AP 시험에서 권장하지 않음)
for (int i = 0; i < 10; i++) {
    i += 2;  // ⚠️ 나쁜 습관 — 결과 예측 어려움
}
```

### 시험 출제 포인트
- for 루프를 while로 변환 (또는 반대)하는 문제
- 루프 변수의 scope: for 안에서 선언하면 밖에서 사용 불가
- update 부분이 `i++`이 아닌 경우의 반복 횟수 계산
- for 루프에서도 body 실행 전에 condition 검사 → 0번 실행 가능

### 연습 문제

**Q1.** 다음 for 루프와 동일한 while 루프를 작성하시오.

```java
for (int k = 100; k >= 0; k -= 10) {
    System.out.println(k);
}
```

<details>
<summary>정답</summary>

```java
int k = 100;
while (k >= 0) {
    System.out.println(k);
    k -= 10;
}
```
출력: 100, 90, 80, ..., 10, 0 (11번 반복)
</details>

**Q2.** 다음 코드의 출력은?

```java
for (int i = 1; i <= 5; i++) {
    for (int j = 1; j <= i; j++) {
        System.out.print("*");
    }
    System.out.println();
}
```

<details>
<summary>정답</summary>

```
*
**
***
****
*****
```
</details>

---

## 2.9 Implementing Selection and Iteration Algorithms (3기간)

**CED 학습목표:** 선택과 반복을 결합하여 표준 알고리즘을 구현할 수 있다.

### 핵심 개념 — 표준 알고리즘 모음

**1. 짝수/홀수 판별**

```java
if (num % 2 == 0) {
    System.out.println("짝수");
} else {
    System.out.println("홀수");
}
```

**2. 정수의 각 자릿수 추출**

```java
int num = 12345;
while (num > 0) {
    int digit = num % 10;      // 마지막 자릿수
    System.out.println(digit); // 5, 4, 3, 2, 1
    num /= 10;                 // 마지막 자릿수 제거
}
```

**3. 특정 조건 빈도 세기 (counting)**

```java
int count = 0;
for (int i = 1; i <= 100; i++) {
    if (i % 3 == 0) {
        count++;
    }
}
System.out.println("1~100에서 3의 배수 개수: " + count);  // 33
```

**4. 최솟값/최댓값 찾기**

```java
int max = Integer.MIN_VALUE;  // 가능한 가장 작은 값으로 초기화
int min = Integer.MAX_VALUE;  // 가능한 가장 큰 값으로 초기화

// 입력값들을 반복하며...
for (int i = 0; i < values.length; i++) {
    if (values[i] > max) max = values[i];
    if (values[i] < min) min = values[i];
}
```

**5. 합계/평균 계산**

```java
int sum = 0;
int count = 0;
for (int i = 0; i < values.length; i++) {
    sum += values[i];
    count++;
}
double average = (double) sum / count;  // 캐스팅 주의!
```

> **주의:** `sum / count`는 정수 나눗셈 → 소수점 버림. `(double) sum / count`로 캐스팅!

### 시험 출제 포인트
- `%` 연산자를 활용한 조건 판별 (짝수, 배수, 자릿수)
- 초기값 설정 실수: max를 0으로 초기화하면 모두 음수일 때 오류
- 정수 나눗셈 vs 실수 나눗셈
- FRQ에서 이 패턴들이 그대로 활용됨

### 연습 문제

**Q1.** 정수 n의 자릿수 합을 구하는 코드를 작성하시오. (예: 1234 → 10)

<details>
<summary>정답</summary>

```java
int n = 1234;
int digitSum = 0;
while (n > 0) {
    digitSum += n % 10;
    n /= 10;
}
System.out.println(digitSum);  // 10
```
</details>

**Q2.** 1부터 n까지의 정수 중 3의 배수이면서 5의 배수가 아닌 수의 개수를 구하는 코드를 작성하시오.

<details>
<summary>정답</summary>

```java
int n = 50;
int count = 0;
for (int i = 1; i <= n; i++) {
    if (i % 3 == 0 && i % 5 != 0) {
        count++;
    }
}
System.out.println(count);
```
</details>

---

## 2.10 Implementing String Algorithms (2기간)

**CED 학습목표:** 문자열을 순회하면서 특정 조건을 만족하는 부분을 찾거나 변환하는 알고리즘을 구현할 수 있다.

### 핵심 개념

**문자열 순회 기본 (CED 1.15.B.3 표준 관용구: `substring(i, i+1)`)**

```java
String str = "Hello";
for (int i = 0; i < str.length(); i++) {
    String ch = str.substring(i, i + 1);   // 한 글자(String) 추출
    System.out.println(ch);
}
```

**1. 특정 문자 개수 세기**

```java
String str = "banana";
int count = 0;
for (int i = 0; i < str.length(); i++) {
    if (str.substring(i, i + 1).equals("a")) {     // String 비교는 .equals()
        count++;
    }
}
System.out.println(count);  // 3
```

**2. 문자열 뒤집기 (reverse)**

```java
String str = "Hello";
String reversed = "";
for (int i = str.length() - 1; i >= 0; i--) {
    reversed += str.substring(i, i + 1);
}
System.out.println(reversed);  // olleH
```

**3. 부분문자열 찾기**

```java
String str = "abcabcabc";
int count = 0;
for (int i = 0; i <= str.length() - 3; i++) {  // length - 부분문자열 길이
    if (str.substring(i, i + 3).equals("abc")) {
        count++;
    }
}
System.out.println(count);  // 3
```

**주요 String 메서드 (이 단원에서 자주 사용)**

| 메서드 | 설명 | 예시 |
|--------|------|------|
| `str.length()` | 문자열 길이 | `"abc".length()` → 3 |
| `str.substring(i, i+1)` | i번째 문자 (CED 1.15.B.3 단일 문자 추출 관용구) | `"abc".substring(0, 1)` → `"a"` |
| `str.substring(a, b)` | 인덱스 a부터 b-1까지 | `"abcde".substring(1, 4)` → "bcd" |
| `str.substring(a)` | 인덱스 a부터 끝까지 | `"abcde".substring(2)` → "cde" |
| `str.indexOf(s)` | s의 첫 위치 (-1이면 없음) | `"abc".indexOf("bc")` → 1 |
| `str.equals(s)` | 내용 비교 | |
| `str.compareTo(s)` | 사전순 비교 | 음수/0/양수 |

### 시험 출제 포인트
- `str.substring(i, i + k)`에서 **인덱스 범위** (i + k가 length 초과하면 에러)
- 루프 조건: `i <= str.length() - k` (부분문자열 길이만큼 빼야 함)
- 문자열 연결(`+=`)은 새 String 객체 생성 → 비효율적이지만 AP 시험에서는 OK
- `charAt`은 `char` 반환 → `==`로 비교. `substring`은 `String` 반환 → `.equals()`로 비교
- **CED 핵심 (필독)**: `char` 타입과 `String.charAt()` 메서드 모두 **AP CSA 2025-26 Quick Reference에 없으므로 시험 출제 안 됨**. 한 글자 추출은 **반드시 `substring(i, i+1)`** 사용 (CED 1.15.B.3 명시 관용구). 위 모든 코드 예시는 `substring`만 사용한다 — 시험 답안도 동일하게 작성할 것.

### 연습 문제

**Q1.** 문자열에서 특정 문자 (`"o"`)의 개수를 세는 코드를 작성하시오.

> 참고: 대소문자 비교는 `'A'~'Z'` 같은 char 비교가 필요해 CED 범위 외(char 타입 OUT). 한 문자 일치 검사는 `substring(i, i+1).equals("X")` 패턴이 표준.

<details>
<summary>정답</summary>

```java
String str = "Hello World";
int count = 0;
for (int i = 0; i < str.length(); i++) {
    if (str.substring(i, i + 1).equals("o")) {
        count++;
    }
}
System.out.println(count);  // 2 (Hello, World 각각의 o)
```
</details>

**Q2.** 다음 코드의 출력은?

```java
String s = "racecar";
String rev = "";
for (int i = s.length() - 1; i >= 0; i--) {
    rev += s.substring(i, i + 1);
}
System.out.println(s.equals(rev));
```

<details>
<summary>정답</summary>
true — "racecar"를 뒤집으면 "racecar" (회문/palindrome)
</details>

---

## 2.11 Nested Iteration (2기간)

**CED 학습목표:** 중첩 루프를 사용하여 2차원적인 문제를 해결할 수 있다.

### 핵심 개념

**기본 구조**

```java
for (int i = 0; i < 3; i++) {       // 외부 루프: 3번
    for (int j = 0; j < 4; j++) {   // 내부 루프: 매번 4번
        System.out.print("* ");
    }
    System.out.println();
}
```

출력:
```
* * * * 
* * * * 
* * * * 
```

**실행 횟수:** 외부 루프 × 내부 루프 = 3 × 4 = **12번**

**내부 루프가 외부 변수에 의존하는 경우**

```java
for (int i = 1; i <= 4; i++) {
    for (int j = 1; j <= i; j++) {
        System.out.print(j + " ");
    }
    System.out.println();
}
```

출력:
```
1 
1 2 
1 2 3 
1 2 3 4 
```

실행 횟수: 1 + 2 + 3 + 4 = **10번**

**구구단 출력**

```java
for (int i = 2; i <= 9; i++) {
    for (int j = 1; j <= 9; j++) {
        System.out.println(i + " x " + j + " = " + (i * j));
    }
}
```

### 시험 출제 포인트
- "print문이 총 몇 번 실행되는가?" 계산
- 내부 루프 조건이 외부 변수에 의존할 때 실행 횟수
- 중첩 루프에서 `break`는 **가장 안쪽 루프만** 탈출. **CED EXCLUSION:** `break`는 AP CSA 시험 범위에 포함되지 않는다. 실무에서는 유용하지만 시험에는 나오지 않으므로 암기할 필요 없다.
- 2차원 배열(Unit 4의 2D Array 토픽)과 밀접하게 연결됨

### 연습 문제

**Q1.** 다음 코드의 출력은?

```java
for (int r = 3; r > 0; r--) {
    for (int c = 0; c < r; c++) {
        System.out.print("#");
    }
    System.out.println();
}
```

<details>
<summary>정답</summary>

```
###
##
#
```
실행 횟수: 3 + 2 + 1 = 6번
</details>

**Q2.** 다음 코드에서 `count++`는 총 몇 번 실행되는가?

```java
int count = 0;
for (int i = 0; i < 5; i++) {
    for (int j = i; j < 5; j++) {
        count++;
    }
}
```

<details>
<summary>정답</summary>
15번<br>
i=0: j는 0~4 → 5번<br>
i=1: j는 1~4 → 4번<br>
i=2: j는 2~4 → 3번<br>
i=3: j는 3~4 → 2번<br>
i=4: j는 4~4 → 1번<br>
합계: 5+4+3+2+1 = 15
</details>

---

## 2.12 Informal Run-Time Analysis (2기간)

**CED 학습목표:** 코드의 statement execution count(실행 횟수)를 비공식적으로 분석할 수 있다.

### 핵심 개념

**Statement Execution Count:** 특정 코드 줄이 실행되는 총 횟수

**단일 루프**

```java
for (int i = 0; i < n; i++) {    // condition 검사: n+1번
    doSomething();                // 실행: n번
}
```

**이중 루프 — 독립적**

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        doSomething();            // 실행: n × m 번
    }
}
```

**이중 루프 — 의존적**

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < i; j++) {
        doSomething();            // 실행: 0+1+2+...+(n-1) = n(n-1)/2 번
    }
}
```

**순차적 루프 (중첩 아님)**

```java
for (int i = 0; i < n; i++) {
    a();                          // n번
}
for (int j = 0; j < m; j++) {
    b();                          // m번
}
// 총: n + m 번 (곱이 아님!)
```

**비공식적 분석 방법**
- 루프 없음 → 1번 (상수)
- 단일 루프 → n번
- 이중 중첩 루프 → n²번 (대략)
- 루프 안에서 반씩 줄어듦 → log n번 (AP에서 깊이 다루진 않음)

### 시험 출제 포인트
- "다음 코드에서 `System.out.println`이 몇 번 실행되는가?" 직접 계산
- 중첩 루프 vs 순차 루프 구분 (곱 vs 합)
- 코드 tracing으로 정확한 횟수를 세는 연습이 중요
- n에 구체적인 값을 대입해서 세는 것이 가장 확실

### 연습 문제

**Q1.** n = 4일 때, 다음 코드에서 `x++`는 몇 번 실행되는가?

```java
int x = 0;
for (int i = 0; i < n; i++) {
    for (int j = i; j < n; j++) {
        x++;
    }
}
```

<details>
<summary>정답</summary>
10번<br>
i=0: 4번, i=1: 3번, i=2: 2번, i=3: 1번<br>
4+3+2+1 = 10 = n(n+1)/2 = 4×5/2
</details>

**Q2.** 다음 두 코드 중 어느 것이 더 많이 실행되는가? (n = 10)

```java
// 코드 A
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        doA();
    }
}

// 코드 B
for (int i = 0; i < n; i++) {
    doB();
}
for (int j = 0; j < n; j++) {
    doB();
}
```

<details>
<summary>정답</summary>
코드 A: n × n = 100번 (이중 중첩)<br>
코드 B: n + n = 20번 (순차적)<br>
코드 A가 훨씬 많이 실행됨
</details>

#### Big-O 표기법 (비공식 이해)

AP CSA에서 "비공식(informal)" 분석이란, 정확한 수학적 증명 없이 **루프 구조를 보고 실행 횟수의 증가 패턴을 판단**하는 것이다.

| 패턴 | 루프 구조 | 이름 | 의미 |
|------|----------|------|------|
| 단일 루프 (n번) | `for (int i = 0; i < n; i++)` | **O(n)** — 선형 | n이 2배 → 시간 2배 |
| 이중 루프 (n×n번) | `for (i) { for (j) }` | **O(n²)** — 이차 | n이 2배 → 시간 4배 |
| 단일 루프 2개 순차 | `for (i) { } for (j) { }` | **O(n)** — 선형 | n+n = 2n ≈ n |

> **시험에서**: "다음 코드 세그먼트의 실행 횟수를 n으로 표현하시오" 형태. 정확한 Big-O 표기는 요구하지 않지만, n번 vs n²번 구분은 알아야 한다.

---

## FRQ 대비: 반복문+조건문 조합 연습

FRQ Q1은 루프와 조건문을 조합하여 메서드를 구현하는 문제다. 아래를 직접 풀어보자.

### 연습 1: 연속 같은 문자 최대 길이

문자열에서 같은 문자가 연속으로 나타나는 최대 길이를 반환하시오.

예: `maxRun("aabbbccdd")` → `3` ("bbb"), `maxRun("abcd")` → `1`

Precondition: str의 길이는 1 이상

```java
public static int maxRun(String str)
```

<details>
<summary>모범 답안</summary>

```java
public static int maxRun(String str) {
    int maxLen = 1;
    int currentLen = 1;
    for (int i = 1; i < str.length(); i++) {
        if (str.substring(i, i + 1).equals(str.substring(i - 1, i))) {
            currentLen++;
        } else {
            currentLen = 1;
        }
        if (currentLen > maxLen) {
            maxLen = currentLen;
        }
    }
    return maxLen;
}
```

**핵심**: 현재 연속 길이(`currentLen`)와 최대 길이(`maxLen`)를 별도로 추적. 문자가 바뀌면 `currentLen`을 1로 리셋.
</details>

### 연습 2: 조건을 만족하는 요소 카운트

정수 배열에서 짝수이면서 10 이상인 요소의 개수를 반환하시오.

```java
public static int countEvenAboveTen(int[] arr)
```

<details>
<summary>모범 답안</summary>

```java
public static int countEvenAboveTen(int[] arr) {
    int count = 0;
    for (int val : arr) {
        if (val % 2 == 0 && val >= 10) {
            count++;
        }
    }
    return count;
}
```

**핵심**: `&&`로 두 조건을 결합. enhanced for로 순회. 카운터 패턴.
</details>

---

## 자주 틀리는 코드 모음 (Unit 2)

### if문 중괄호 생략 + 들여쓰기 함정

```java
// ❌ 잘못된 코드: 의도와 다른 동작
int x = 5;
if (x > 10)
    System.out.println("크다");
    System.out.println("항상 출력됨");  // 들여쓰기와 무관하게 항상 실행!

// ✅ 올바른 코드: 중괄호 필수
if (x > 10) {
    System.out.println("크다");
    System.out.println("이것도 조건 안에");
}
```

### for 루프 경계값 실수 (off-by-one)

```java
// ❌ 잘못된 코드: 마지막 원소 누락
int[] arr = {1, 2, 3, 4, 5};
for (int i = 0; i < arr.length - 1; i++) {  // < length-1이면 마지막 못 봄!
    System.out.print(arr[i] + " ");
}
// 출력: 1 2 3 4 (5가 빠짐!)

// ✅ 올바른 코드
for (int i = 0; i < arr.length; i++) {  // < length
    System.out.print(arr[i] + " ");
}
// 출력: 1 2 3 4 5
```

### while 무한 루프

```java
// ❌ 잘못된 코드: 종료 조건 갱신 누락
int n = 10;
while (n > 0) {
    System.out.println(n);
    // n-- 를 빠뜨림! → 무한 루프
}

// ✅ 올바른 코드
int n = 10;
while (n > 0) {
    System.out.println(n);
    n--;  // 반드시 종료 조건에 다가가야 함
}
```

### 초기값 실수 (max/min)

```java
// ❌ 잘못된 코드: max를 0으로 초기화
int max = 0;
int[] arr = {-5, -2, -8, -1};
for (int val : arr) {
    if (val > max) max = val;
}
System.out.println(max);  // 0 출력! (모든 값이 음수이므로)

// ✅ 올바른 코드: 첫 원소로 초기화
int max = arr[0];
for (int i = 1; i < arr.length; i++) {
    if (arr[i] > max) max = arr[i];
}
System.out.println(max);  // -1 (올바른 최대값)
```

---

## 시험 대비 종합 정리

### 출제 비중
- **Analyze Code (코드 분석):** 시험의 37-53% → **tracing 능력이 핵심**
- Unit 2는 MC와 FRQ 모두에서 가장 많이 출제됨

### 반드시 암기할 것
1. **De Morgan's Laws:** `!(a && b) == !a || !b`, `!(a || b) == !a && !b`
2. **Short-circuit evaluation:** `&&` 왼쪽 false → 오른쪽 안 봄, `||` 왼쪽 true → 오른쪽 안 봄
3. **String 비교:** `==`는 참조, `.equals()`는 내용
4. **Off-by-one:** `<` vs `<=`의 차이
5. **for 루프 실행 순서:** init → condition → body → update → condition → ...

### 자주 하는 실수 TOP 5
1. String을 `==`로 비교하여 예상과 다른 결과
2. 중괄호 없는 if에서 두 번째 줄이 if에 속한다고 착각
3. off-by-one: 루프 1번 많거나 적게 반복
4. while 루프에서 변수 업데이트 빠뜨려서 무한 루프
5. 정수 나눗셈에서 소수점 버림 (평균 계산 시 캐스팅 필요)

### FRQ 연관
- **FRQ Q1:** 거의 항상 loop + conditional 조합으로 출제
- **FRQ Q3 (배열/ArrayList):** Unit 2의 루프 패턴이 기반
- 표준 알고리즘(max/min, 합계, 카운팅)을 자유자재로 사용해야 함

---

> **다음 단원:** Unit 3 — Class Design and Object-Oriented Concepts
