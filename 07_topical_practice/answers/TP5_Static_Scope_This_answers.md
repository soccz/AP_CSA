# TP5: Static, Final, Scope, this — 해설집

> **CED 2025-26 토픽**: 3.7 Class Variables/Methods, 3.8 Scope and Access, 3.9 `this` Keyword
> **답안 분포**: A:2 / B:2 / C:2 / D:2

---

## 정답 요약

| # | 정답 | CED 토픽 | 핵심 |
|---|------|---------|------|
| 1 | **D** `"1 2 3 3"` | 3.7.B.1 static 공유 | id는 인스턴스, total은 공유 |
| 2 | **C** `"110.0 220.0"` | 3.7 setRate 후 모든 객체 영향 | 0.10 적용 |
| 3 | **B** `"50 4"` | 3.7.B.3 + left-to-right 평가 | LIMIT 먼저, increment 나중 |
| 4 | **A** `"true true true false 3"` | 3.7.B.3 final + capacity 한계 | 4번째 실패 |
| 5 | **D** `"25 0"` | 3.8.A.2 shadowing | this 안 쓰면 self-assign |
| 6 | **B** `"8 100"` | 3.8.A.2 메서드 내 shadowing | 지역 변경, 인스턴스 보존 |
| 7 | **A** `"7 7 false"` | 3.9.A.1 this로 새 객체 | clone = 다른 참조 |
| 8 | **C** `"true false"` | 3.9.A.2 this 인자 전달 | a>b, b<a |

---

## Section I: 문제별 상세 해설

---

### Q1. 정답: **(D) `"1 2 3 3"`**

📌 **출제 의도:** **`static` 변수가 모든 인스턴스 사이에 공유**된다는 기본 동작 + 인스턴스 변수와 클래스 변수의 차이를 추적할 수 있는지 테스트.

📎 **연계:** **CED 3.7.B.1**: *"Class variables belong to the class, with all objects of a class sharing a single copy of the class variable. Class variables are designated with the static keyword before the variable type."*

> **핵심 개념: static vs instance 변수**
> - **`static int total`**: 클래스 전체에 **단일 복사본** — 모든 객체가 공유
> - **`int id`**: 인스턴스마다 **독립적인 복사본**
> - 생성자에서 `total++; id = total;` → total은 누적, id는 그 순간 값을 캡처

> **선행 지식:**
> - `static` 키워드 (CED 3.7.B.1) — 클래스 레벨
> - 인스턴스 메서드(`getId`)는 객체 통해 호출, static 메서드(`getTotal`)는 클래스명으로 호출
> - **CED 3.7.B.2**: public static은 `클래스명.변수`로 접근

**한 줄씩 추적:**

| 단계 | 동작 | total | id |
|---|---|---|---|
| 시작 | — | 0 | — |
| `new Counter()` (a) | total++ → 1, a.id = 1 | 1 | a.id=1 |
| `new Counter()` (b) | total++ → 2, b.id = 2 | 2 | b.id=2 |
| `new Counter()` (c) | total++ → 3, c.id = 3 | 3 | c.id=3 |

각 호출 결과:
- `a.getId()` = **1**
- `b.getId()` = **2**
- `c.getId()` = **3**
- `Counter.getTotal()` = **3**

**출력: `"1 2 3 3"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"3 3 3 3"` | id도 static이라고 오해 | id는 instance variable — 각 객체 독립 |
| (B) `"0 0 0 0"` | 생성자가 호출되지 않는다고 오해 | new로 생성 시 자동 호출 |
| (C) `"1 1 1 3"` | total은 공유지만 id 갱신을 잘못 추적 | id는 생성 순간의 total 값 캡처 |
| **(D) `"1 2 3 3"`** ✅ | 정답 | id는 1, 2, 3 (생성 순서), total은 최종 3 |

> ⚠️ **함정 1:** **static = "클래스 변수"** = 모든 객체 공유. instance = 객체마다 별개. 두 개념 분리 필수.

> ⚠️ **함정 2:** **`id = total;` 시점**. `total++` 후 그 순간 값을 id에 복사. 따라서 a.id=1, b.id=2 (각자의 생성 순간 total 값).

> ⚠️ **함정 3:** **static 메서드 호출법**. `Counter.getTotal()` (클래스명 사용) 또는 `a.getTotal()` (객체 사용 가능하나 비권장). AP는 **클래스명** 권장.

> 💡 **꿀팁 1:** **static의 용도** (CED 3.7):
> - 모든 객체 공유: 카운터, 설정값
> - 객체와 무관: 유틸리티 메서드 (`Math.abs` 등)
> - 상수: `public static final` (Q3 참조)

> 💡 **꿀팁 2:** **instance vs static 메모리 모델**:
> - instance: heap의 객체마다 저장
> - static: 클래스 영역에 1개

> 💡 **꿀팁 3:** **카운터 패턴**: 본 예제처럼 자동 ID 부여 (생성된 객체 수 추적). 실무에서 자주 사용.

---

### Q2. 정답: **(C) `"110.0 220.0"`**

📌 **출제 의도:** **static 메서드로 클래스 변수 변경 시 모든 객체에 즉시 영향**을 미치는 동작을 추적. CED 3.7.A.2 + 3.7.B.1 결합.

📎 **연계:** **CED 3.7.A.2**: *"Class methods can access or change the values of class variables and can call other class methods."* + **CED 3.7.B.1** static 공유.

> **핵심 개념: static 변수 변경의 전파**
> - static 변수는 단일 복사본 → 한 곳에서 변경하면 **모든 인스턴스가 본 변경 후 값을 사용**
> - 본 문제: `setRate(0.10)` 호출 후 a, b 모두 새 rate(0.10) 적용
> - 변경 전 생성된 객체도 영향받음 (변경 시점 이후 호출 시)

> **선행 지식:**
> - `interestRate` 초기값 0.05
> - setRate는 **클래스 메서드** (`static void setRate`) → 클래스 변수 변경 가능
> - addInterest는 **인스턴스 메서드** → 자신의 balance 변경 + 클래스 변수 읽음

**한 줄씩 추적:**

| 단계 | 동작 | a.balance | b.balance | interestRate |
|---|---|---|---|---|
| 시작 | — | — | — | 0.05 |
| `new Bank(100.0)` | a 생성 | 100.0 | — | 0.05 |
| `new Bank(200.0)` | b 생성 | 100.0 | 200.0 | 0.05 |
| `Bank.setRate(0.10)` | rate 변경 | 100.0 | 200.0 | **0.10** |
| `a.addInterest()` | 100 + 100·0.10 | **110.0** | 200.0 | 0.10 |
| `b.addInterest()` | 200 + 200·0.10 | 110.0 | **220.0** | 0.10 |

**출력: `"110.0 220.0"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"100.0 200.0"` | addInterest가 작동 안 한다고 오해 | 정상 작동 |
| (B) `"105.0 210.0"` | 옛 rate 0.05 사용 (setRate 변경 무시) | setRate 변경 후 호출이라 새 rate 0.10 사용 |
| **(C) `"110.0 220.0"`** ✅ | 정답 | 0.10 적용 |
| (D) `"120.0 240.0"` | 0.20 같은 잘못된 rate 적용 | rate는 0.10 |

> ⚠️ **함정 1:** **변경 시점**. setRate가 addInterest **이전**에 호출 → 새 rate 적용. 만약 reverse 순서면 옛 rate 적용.

> ⚠️ **함정 2:** **모든 인스턴스 영향**. a와 b 모두 영향. instance variable이라면 각 객체 독립인데, static은 공유.

> ⚠️ **함정 3:** **double 출력 형식**. Java는 `100.0 + 100*0.10 = 110.0`을 정확히 표현 (2의 거듭제곱 분수). 부동소수점 정밀도 영향 없음.

> 💡 **꿀팁 1:** **static 메서드 시그니처**: `public static void setRate(double r)` — 키워드 순서 `public static`.

> 💡 **꿀팁 2:** **클래스 메서드 호출**: `Bank.setRate(0.10)` (클래스명) 또는 `a.setRate(0.10)` (인스턴스 통해, 비권장). AP는 클래스명 권장.

> 💡 **꿀팁 3:** **공유 상태 변경의 위험**: 한 객체의 동작이 다른 객체에 영향 (전역 상태). 멀티스레드 환경에서 조심해야 함 (AP 범위 외).

---

### Q3. 정답: **(B) `"50 4"`**

📌 **출제 의도:** `final` 상수의 **읽기 가능 + 수정 불가** + **String 결합의 좌→우 평가 순서**에서 `Constants.increment()`가 어느 시점에 호출되는지 추적.

📎 **연계:** **CED 3.7.B.3**: *"When a variable is declared final, its value cannot be modified."* + **CED 1.15.A.4** String concatenation 좌→우.

> **핵심 개념: final 변수 + 평가 순서**
> - `LIMIT`은 final → **읽기만 가능, 쓰기 불가**
> - `Constants.LIMIT = 200;` 같은 대입 시 **컴파일 에러**
> - println 인자는 좌→우 평가 → `LIMIT` 먼저 읽고, **그 다음 `increment()` 호출**

> **선행 지식:**
> - `Constants.increment()` 3회 호출 후 counter = 3
> - println의 `Constants.increment()`가 4번째 호출 → counter = 4
> - String concat: `int + " " + int` = String

**한 줄씩 추적:**

| 단계 | counter |
|---|---|
| 시작 | 0 |
| 1st `increment()` | 1 |
| 2nd `increment()` | 2 |
| 3rd `increment()` | 3 |
| println 시작 — `LIMIT` 읽음 (50) | 3 (변화 없음) |
| println — `increment()` 호출 (4번째) | **4** (return 4) |
| `"50 " + 4` = `"50 4"` | — |

**출력: `"50 4"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"50 3"` | println의 `increment()`가 호출 전 counter 값(3)이라고 오해 | `increment()`는 **호출 시 counter++** → 4 반환 |
| **(B) `"50 4"`** ✅ | 정답 | LIMIT(50) + increment 4번째 호출(=4) |
| (C) `"Compile error"` | final 사용에 문제 있다고 오해 | LIMIT은 **읽기만** 함, 정상 컴파일 |
| (D) `"100 4"` | LIMIT 값을 잘못 추적 | LIMIT = 50 (선언 시 명시) |

> ⚠️ **함정 1:** **`final` 변수의 읽기 가능성**. `final`은 **수정**만 금지. 읽기는 자유롭게 가능.

> ⚠️ **함정 2:** **println 평가 순서**. 인자는 **좌에서 우로** 평가. 본 코드는 LIMIT(50) 먼저, 그 다음 increment() 호출.

> ⚠️ **함정 3:** **side effect 호출**. println 안에서 `increment()` 호출 → counter 변경. 일견 단순 출력처럼 보이지만 상태 변경 발생.

> 💡 **꿀팁 1:** **`public static final` 패턴**: 상수 정의의 표준 (Java convention: 대문자 + 언더스코어, 예 `MAX_VALUE`).

> 💡 **꿀팁 2:** **`final` 변경 시 컴파일 에러**:
> ```java
> public static final int MAX = 100;
> MAX = 200;  // ERROR: cannot assign to final variable
> ```

> 💡 **꿀팁 3:** **수학적 평가 순서**: 함수 인자, 메서드 인자, 산술 식의 피연산자 모두 **좌→우** 평가. 부수 효과(side effect) 추적 핵심.

---

### Q4. 정답: **(A) `"true true true false 3"`**

📌 **출제 의도:** **인스턴스 `final` 변수 + capacity 제약**을 적용한 클래스 동작 추적. 생성자에서 1회 초기화한 final값은 이후 변경 불가하지만 **읽기는 가능**.

📎 **연계:** **CED 3.7.B.3** final + **CED 3.4.A.2** 생성자 + **CED 3.5** instance methods. 객체 상태 캡슐화 패턴.

> **핵심 개념: instance final 변수**
> - `private final int capacity` — 인스턴스마다 독립적인 final 값
> - 생성자에서 `capacity = cap;` 1회 초기화 (Java 허용)
> - 이후 어떤 메서드에서도 capacity 변경 불가
> - 읽기는 자유: `if (items < capacity)` 정상

> **선행 지식:**
> - 생성자 매개변수로 final 값 결정 (인스턴스마다 다른 capacity 가능)
> - `add()`는 capacity까지 items 증가, 그 후 false 반환
> - boolean의 toString: "true" 또는 "false"

**한 줄씩 추적 (`Box(3)`):**

| 단계 | items | r1, r2, r3, r4 |
|---|---|---|
| 시작 | 0 | — |
| `b.add()` (r1) | 0<3 ✓ → items=1, return true | r1=true |
| `b.add()` (r2) | 1<3 ✓ → items=2, return true | r2=true |
| `b.add()` (r3) | 2<3 ✓ → items=3, return true | r3=true |
| `b.add()` (r4) | 3<3 ✗ → return false (no change) | r4=false |

`b.getItems()` = **3**

**출력: `"true true true false 3"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `"true true true false 3"`** ✅ | 정답 | 3번 성공 + 1번 실패 + items=3 |
| (B) `"true true true true 4"` | capacity 제약 무시 | capacity=3이라 4번째는 실패 |
| (C) `"true true false false 2"` | items 카운트 잘못 | 3번 성공이 정확 |
| (D) `"Compile error..."` | `capacity = cap;` 생성자 내 대입을 final 위반이라 오해 | **생성자 내 1회 초기화는 허용** |

> ⚠️ **함정 1:** **생성자 내 final 초기화 허용**. final은 "1회 초기화 후 변경 불가"이지 "전혀 대입 불가"가 아님. 생성자에서 1번 대입 OK.

> ⚠️ **함정 2:** **`<` strict**. `items < capacity` (3<3 false → 추가 안 됨). `<=`였다면 4번째도 성공.

> ⚠️ **함정 3:** **failed add는 상태 변경 없음**. r4=false일 때 items 그대로 3 유지.

> 💡 **꿀팁 1:** **`final` 인스턴스 변수 패턴**:
> - 생성자에서 1회 초기화
> - 객체 생명주기 동안 불변 (immutable)
> - 예: 사용자 ID, 날짜, 좌표 등 변하지 않는 속성

> 💡 **꿀팁 2:** **`static final` vs `final`**:
> - `public static final int MAX = 100;` — 클래스 상수 (선언 시 초기화)
> - `private final int id;` — 인스턴스 상수 (생성자에서 초기화)

> 💡 **꿀팁 3:** **boolean 변수 출력**: `System.out.println(true)` → "true". `println(false)` → "false". String 결합도 자동 변환.

---

### Q5. 정답: **(D) `"25 0"`**

📌 **출제 의도:** **shadowing의 효과** — 매개변수와 인스턴스 변수가 같은 이름일 때 `this.` 사용 여부의 결정적 차이. CED 3.8.A.2의 핵심.

📎 **연계:** **CED 3.8.A.2**: *"When there is a local variable or parameter with the same name as an instance variable, the variable name will refer to the local variable instead of the instance variable within the body of the constructor or method."* + **CED 3.9.A.1** this.

> **핵심 개념: shadowing 해결**
> - 같은 이름 → **지역(local/parameter) 우선**
> - 인스턴스 변수 접근하려면 **`this.변수`** 사용
> - 매개변수에 자기 자신 대입 (`age = age;`) → 인스턴스 변수에 영향 없음 (no-op)

> **선행 지식:**
> - 인스턴스 변수 기본값: int = 0, double = 0.0, boolean = false, reference = null (CED 3.4.A.5)
> - 생성자에서 인스턴스 변수 초기화 안 하면 기본값 그대로
> - `this.age = age;` 표준 관용구 (생성자에서 매개변수를 인스턴스 변수에 대입)

**Person 추적 (`new Person(25)`):**

| 단계 | 동작 | 결과 |
|---|---|---|
| 시작 | age 매개변수 = 25, this.age (instance) = 0 (기본) | — |
| `this.age = age` | this.age (instance) ← age (매개변수=25) | this.age = 25 |
| 생성자 종료 | — | p1.age = **25** |

`p1.getAge()` = **25**

**Person2 추적 (`new Person2(30)`):**

| 단계 | 동작 | 결과 |
|---|---|---|
| 시작 | age 매개변수 = 30, this.age (instance) = 0 (기본) | — |
| `age = age` | age (매개변수) ← age (매개변수, 자기 자신) | no-op |
| 생성자 종료 | this.age 변경 없음 | p2.age = **0** |

`p2.getAge()` = **0**

**출력: `"25 0"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"25 30"` | 두 클래스 모두 정상 작동이라 오해 | Person2의 `age = age`는 인스턴스 변수에 영향 없음 |
| (B) `"0 0"` | 두 클래스 모두 작동 안 한다고 오해 | Person은 정상 (this. 사용) |
| (C) `"30 25"` | 매개변수 값 직접 출력으로 오해 | getAge()는 인스턴스 변수 반환 |
| **(D) `"25 0"`** ✅ | 정답 | Person 정상, Person2 self-assign |

> ⚠️ **함정 1:** **`this.` 누락의 치명성**. shadowing 상황에서 `this.` 없으면 매개변수만 가리킴 → 인스턴스 변수에 영향 없음.

> ⚠️ **함정 2:** **`age = age;` 컴파일 정상**. Java 컴파일러는 self-assignment를 경고만 하고 에러 없음 (compile OK, 의도와 다른 결과).

> ⚠️ **함정 3:** **인스턴스 변수 기본값**. 명시 초기화 없으면 0 (int), 0.0 (double), false (bool), null (ref). CED 3.4.A.5 명시.

> 💡 **꿀팁 1:** **표준 생성자 관용구**:
> ```java
> public Class(int x, int y) {
>     this.x = x;
>     this.y = y;
> }
> ```

> 💡 **꿀팁 2:** **매개변수 이름을 다르게 짓는 대안**:
> ```java
> public Person(int initialAge) { age = initialAge; }
> ```
> shadowing 회피, 단점은 이름이 길어짐.

> 💡 **꿀팁 3:** **Q5와 Q6의 차이**:
> - Q5: 생성자 매개변수 vs 인스턴스 (this. 필요)
> - Q6: 메서드 내 지역 변수 vs 인스턴스 (this. 필요)

---

### Q6. 정답: **(B) `"8 100"`**

📌 **출제 의도:** **메서드 내 지역 변수 선언 시 인스턴스 변수 가림(shadowing)** — 지역에서의 변경은 인스턴스에 영향 없음. `this.x`로 명시적 인스턴스 접근 시 원본 유지.

📎 **연계:** **CED 3.8.A.2** shadowing + **CED 3.9.A.1** this. Q5의 변형 (생성자 → 메서드).

> **핵심 개념: 메서드 내 지역 변수 우선**
> - `int x = 5;` (메서드 내 선언) → **새 지역 변수 생성**
> - 이후 `x++`은 **지역 변수만** 변경 (인스턴스 그대로)
> - `this.x`로 인스턴스 변수 명시 접근 가능

> **선행 지식:**
> - 인스턴스 변수: 객체에 저장 (heap)
> - 지역 변수: stack frame에 저장 (메서드 종료 시 사라짐)
> - shadowing: 같은 이름 → 가까운 scope 우선

**한 줄씩 추적:**

| 단계 | 지역 x | this.x (인스턴스) |
|---|---|---|
| 시작 (생성 후) | — | 100 |
| `int x = 5;` | 5 | 100 |
| 루프 i=0: `x++` | 6 | 100 |
| 루프 i=1: `x++` | 7 | 100 |
| 루프 i=2: `x++` | 8 | 100 |
| `println(x + " " + this.x)` | 출력: `"8 100"` |

**출력: `"8 100"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"103 100"` | x가 인스턴스를 직접 가리킨다고 오해 (지역 변수 무시) | 지역 변수 우선 |
| **(B) `"8 100"`** ✅ | 정답 | 지역 5+3=8, 인스턴스 100 그대로 |
| (C) `"5 100"` | x++ 작동 안 한다고 오해 | 정상 작동 |
| (D) `"8 103"` | this.x도 변경된다고 오해 | this.x는 변경 안 됨 |

> ⚠️ **함정 1:** **shadowing 의도**. 같은 이름의 지역 선언은 의도적으로 인스턴스 가리기. 본 코드는 명백히 지역 의도.

> ⚠️ **함정 2:** **`this.x`로 인스턴스 접근**. 지역 x가 가린 상태에서 인스턴스에 접근하려면 반드시 `this.`.

> ⚠️ **함정 3:** **메서드 종료 후 지역 변수 소멸**. 다음 메서드 호출 시 다시 5로 초기화 (이전 변경 잃음).

> 💡 **꿀팁 1:** **shadowing 회피 권장**: 가능하면 변수 이름을 다르게 짓자. 디버깅 어려움.

> 💡 **꿀팁 2:** **`this`의 두 용법**:
> 1. shadowing 해결: `this.x = x;` (CED 3.9 + 3.8)
> 2. 현재 객체 전달: `other.method(this);` (Q8 참조)

> 💡 **꿀팁 3:** **scope 규칙 (CED 3.8.A.1)**: 지역 변수는 선언 블록 내에서만 유효. for의 `int i`도 for 블록 안에서만. 밖에서 사용 시 컴파일 에러.

---

### Q7. 정답: **(A) `"7 7 false"`**

📌 **출제 의도:** **`this`로 새 객체 생성** (clone 패턴) — 메서드 안에서 `this.x`, `this.y`로 자신의 필드를 읽고 새 Point를 만들어 반환. 두 객체는 **다른 메모리 주소**.

📎 **연계:** **CED 3.9.A.1**: *"Within an instance method or constructor, the keyword this acts as a special variable that holds a reference to the current object — the object whose method or constructor is being called."* + **CED 2.6.B.1** `==` 참조 비교.

> **핵심 개념: clone 패턴**
> - `this.x`, `this.y` — 현재 객체의 필드 읽기
> - `new Point(this.x, this.y)` — **새 Point 객체 생성** (다른 메모리)
> - `==`은 **참조 비교** → 다른 객체면 false

> **선행 지식:**
> - clone은 **얕은 복사(shallow copy)** — primitive 필드는 값 복사
> - p1 == p2: 두 변수가 같은 객체 가리키는지 (참조 비교)
> - p1.equals(p2): 객체 내용 비교 (Object.equals 기본 동작은 ==와 동일)

**한 줄씩 추적:**

| 단계 | p1 | p2 |
|---|---|---|
| `new Point(3, 4)` | x=3, y=4 (참조 R1) | — |
| `p1.clone()` | R1 그대로 | new Point(3, 4) (참조 R2, R1≠R2) |
| `p1.sum()` | 3+4 = 7 | — |
| `p2.sum()` | — | 3+4 = 7 |
| `p1 == p2` | R1 vs R2 | **false** (다른 참조) |

**출력: `"7 7 false"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `"7 7 false"`** ✅ | 정답 | 같은 값(7) but 다른 객체 (false) |
| (B) `"7 7 true"` | clone이 같은 객체 반환이라 오해 | `new Point(...)`는 항상 새 객체 |
| (C) `"3 3 false"` | sum이 x만 반환이라 오해 | sum() = x+y |
| (D) `"Compile error"` | this 사용에 문제 있다고 오해 | this 사용 정상 |

> ⚠️ **함정 1:** **`==` vs `.equals()`**. 객체 비교에서 `==`은 **참조 비교** (메모리 주소). 본 문제는 두 다른 객체 → false.

> ⚠️ **함정 2:** **clone = 새 객체**. `new` 키워드 사용 → 항상 새 메모리 할당. 같은 값이라도 다른 객체.

> ⚠️ **함정 3:** **얕은 복사 vs 깊은 복사**. 본 예제는 primitive 필드라 얕은 복사로 충분. 객체 필드(예: 배열)면 얕은 복사 시 aliasing 문제 (CED 3.4.A.3 defensive copy).

> 💡 **꿀팁 1:** **clone 패턴**:
> ```java
> public Point clone() {
>     return new Point(this.x, this.y);
> }
> ```

> 💡 **꿀팁 2:** **`this.x` vs `x`**: 메서드 내에서 같은 이름 지역 변수가 없으면 `this.` 생략 가능. 명시적 `this.`는 가독성 + 안전성.

> 💡 **꿀팁 3:** **객체 동등성 비교**: `==`는 참조, `.equals()`는 내용. CED 2.6.B.3: 클래스가 자체 `equals` 정의 가능 (단 작성은 EXCLUSION).

---

### Q8. 정답: **(C) `"true false"`**

📌 **출제 의도:** **`this`를 다른 객체의 메서드에 인자로 전달** (CED 3.9.A.2 명시). 두 객체 간의 비교에서 호출자(this)와 인자(other)의 관계 추적.

📎 **연계:** **CED 3.9.A.2**: *"The keyword this can be used to pass the current object as an argument in a method call."* + **CED 3.6.A.1** 객체 참조 매개변수.

> **핵심 개념: this 인자 전달**
> - `other.compareWith(this)` → `other`의 메서드에 **현재 객체(this)를 인자로**
> - other 입장에서는 `this = other`, `other(매개변수) = 호출자`
> - this/other 시점이 **메서드 진입마다 바뀜** — 추적 핵심

> **선행 지식:**
> - 메서드 호출 시 호출자 = `this`
> - 인스턴스 변수 vs 매개변수 구별 필수
> - `compareWith`의 결과: this.value - other.getValue()

**`a.isLargerThan(b)` 추적:**

| 시점 | 위치 | this | other |
|---|---|---|---|
| 1 | a.isLargerThan 진입 | a | b |
| 2 | other.compareWith(this) → b.compareWith(a) | — | — |
| 3 | b.compareWith 진입 | **b** (호출자) | **a** (인자) |
| 4 | return this.value - other.getValue() = b.value - a.value = 7 - 10 | — | -3 |
| 5 | a.isLargerThan: -3 < 0 → **true** | — | — |

`a.isLargerThan(b)` = **true** (a가 b보다 큼)

**`b.isLargerThan(a)` 추적:**

| 시점 | 위치 | this | other |
|---|---|---|---|
| 1 | b.isLargerThan 진입 | b | a |
| 2 | other.compareWith(this) → a.compareWith(b) | — | — |
| 3 | a.compareWith 진입 | **a** (호출자) | **b** (인자) |
| 4 | return this.value - other.getValue() = a.value - b.value = 10 - 7 | — | 3 |
| 5 | b.isLargerThan: 3 < 0 → **false** | — | — |

`b.isLargerThan(a)` = **false** (b가 a보다 크지 않음)

**출력: `"true false"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"false true"` | this/other 역할 거꾸로 추적 | a(10)이 b(7)보다 큼 → true |
| (B) `"false false"` | 비교 로직 부정 | a > b 케이스에서 true |
| **(C) `"true false"`** ✅ | 정답 | a>b: true, b>a: false |
| (D) `"true true"` | 둘 다 true라 오해 | b>a는 false |

> ⚠️ **함정 1:** **this 시점 변화**. 메서드 진입마다 새로 결정. 본 문제는 한 호출 안에서 두 메서드를 거치며 this/other가 바뀜.

> ⚠️ **함정 2:** **간접 비교 (other를 거쳐 this 평가)**. `other.compareWith(this)`로 비교 결과의 의미가 반대됨. compareWith는 "호출자 - 인자".

> ⚠️ **함정 3:** **isLargerThan의 정의**. `other.compareWith(this) < 0` → `other - this < 0` → `this > other`. 이중 부정 추적 필수.

> 💡 **꿀팁 1:** **this 인자 전달 패턴 (CED 3.9.A.2)**:
> ```java
> public void register(Manager m) {
>     m.add(this);  // 자신을 다른 객체에 등록
> }
> ```

> 💡 **꿀팁 2:** **상호 비교 메서드**: 본 예제처럼 두 객체 간 비교 시 한쪽 메서드에서 다른쪽으로 위임. 디자인 패턴 (Visitor 등)에서 빈번.

> 💡 **꿀팁 3:** **this의 3가지 용법 정리** (CED 3.9):
> 1. shadowing 해결: `this.x = x;` (Q5)
> 2. 현재 객체의 필드/메서드 명시: `this.value` (Q7, Q8 compareWith)
> 3. 현재 객체를 인자로 전달: `other.method(this)` (Q8)

---

## 종합 정리

### 3.7 Static & Final 핵심
```java
public class Counter {
    private static int total = 0;       // static: 모든 객체 공유
    public static final int MAX = 100;  // static final: 클래스 상수
    private final int id;                // final: 인스턴스 상수 (생성자 1회 초기화)

    public Counter() {
        total++;
        id = total;
    }

    public static int getTotal() { return total; }   // class method
    public int getId() { return id; }                // instance method
}
```

### 3.8 Scope 규칙
- 지역 변수 + 인스턴스 변수 같은 이름 → **지역 우선**
- 인스턴스 접근하려면 **`this.변수`**
- 지역 변수는 선언된 블록 내에서만 유효

### 3.9 this 키워드 3대 용법
1. **Shadowing 해결**: `this.x = x;`
2. **현재 객체 필드/메서드 명시**: `this.value`, `this.method()`
3. **현재 객체 인자 전달**: `other.method(this)`

### 흔한 함정 모음
1. **`this.` 누락 → self-assignment** (Q5): `age = age` (no-op)
2. **shadowing → 인스턴스 영향 없음** (Q6): 지역 변경, 인스턴스 보존
3. **`==` vs `.equals()`** (Q7): 객체 참조 비교 vs 내용 비교
4. **this 시점 변화** (Q8): 메서드 진입마다 재결정
5. **static = 모든 객체 영향** (Q1, Q2): 한 번 변경, 전체 영향
6. **final = 1회 초기화 후 불변** (Q3, Q4): 읽기는 자유, 쓰기 금지

### EXCLUSION 재확인
- **상속 (`extends`, `super`) OUT** (CED 1.12 EXCLUSION) ✓ — 본 세트는 단일 클래스만
- **`Math.min/max` OUT** ✓ — 본 세트는 if 비교만 사용
- **`break`/`continue` OUT** ✓ — 본 세트는 미사용
- **`switch`, `do-while` OUT** ✓
- **재귀 작성 OUT** (CED 4.16 EXCLUSION) ✓ — 본 세트는 재귀 미사용
