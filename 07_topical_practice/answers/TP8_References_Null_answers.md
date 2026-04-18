# TP8: Object References + Null + Aliasing — 해설집

> **CED 2025-26 토픽**: 1.12 Objects, 1.14 Calling Instance Methods, 3.4.A.3 Defensive Copy, 3.6 Reference Passing
> **답안 분포**: A:2 / B:2 / C:1 / D:1

---

## 정답 요약

| # | 정답 | CED 토픽 | 핵심 |
|---|------|---------|------|
| 1 | **C** `"6 6"` | 1.12 + 2.6.B.1 aliasing | b=a, 같은 객체 |
| 2 | **A** NPE | 1.14.A.2 null 메서드 | s.length() on null |
| 3 | **B** `99` | 3.6.A.1 배열 reference | 메서드가 원본 변경 |
| 4 | **D** `99` | 3.6.A.1 객체 ref + 재할당 | 객체 변경 vs 참조 변경 |
| 5 | **A** `99` | 3.4.A.3 defensive copy 누락 | 외부 변경이 내부 영향 |
| 6 | **B** `"true true false"` | 1.14.A.2 + 2.5 null-safe | short-circuit으로 NPE 회피 |

---

## Section I: 문제별 상세 해설

---

### Q1. 정답: **(C) `"6 6"`**

📌 **출제 의도:** **객체 변수 대입 = aliasing(별칭)** — 같은 객체에 대한 두 참조 생성. 한쪽에서 변경하면 다른쪽도 영향. CED 2.6.B.1의 핵심 함정.

📎 **연계:** **CED 2.6.B.1**: *"Two different variables can hold references to the same object. Object references can be compared using == and !=."* + **CED 1.12.B.1**: *"A variable of a reference type holds an object reference, which can be thought of as the memory address of that object."*

> **핵심 개념: aliasing**
> - **`Counter b = a;`** — b와 a 모두 **같은 메모리 주소** 가리킴
> - 하나의 객체, 두 개의 변수
> - `b.increment()` → 객체의 value 변경 → a도 같은 객체 보므로 영향
> - **`==`로 비교**: a == b → true (같은 참조)

> **선행 지식:**
> - 객체 변수는 **참조** 보유 (CED 1.12.B.1)
> - primitive 변수와 다름: `int x = a;` 후 a 변경해도 x 영향 없음
> - 참조 = 메모리 주소 같음

**한 단계씩 추적:**

| 단계 | 동작 | a, b 상태 | 객체 value |
|---|---|---|---|
| 1 | `new Counter(5)` | a → 객체 R1 (value=5) | 5 |
| 2 | `Counter b = a` | b → R1 (a와 같음) | 5 |
| 3 | `b.increment()` | R1.value++ → 6 | **6** |
| 4 | `a.getValue()` | R1.value | **6** |
| 5 | `b.getValue()` | R1.value | **6** |
| 6 | `println("6 6")` | — | — |

**최종 출력: `"6 6"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"5 6"` | a와 b가 독립적이라고 오해 | aliasing — 같은 객체, 둘 다 영향 |
| (B) `"5 5"` | increment 작동 안 한다고 오해 | 정상 작동 |
| **(C) `"6 6"`** ✅ | 정답 | 두 변수 같은 객체 → 둘 다 6 |
| (D) `"6 5"` | b만 새 객체라고 오해 | b = a는 같은 참조 |

> ⚠️ **함정 1:** **primitive vs 객체 대입**. `int x = y` 후 y 변경 → x 영향 없음 (값 복사). `Counter b = a` 후 a 객체 변경 → b도 영향 (참조 복사).

> ⚠️ **함정 2:** **aliasing 의도적 활용 vs 실수**. 의도적으로 두 변수가 같은 객체 가리키게 하려면 `=` 대입. 독립 객체 원하면 `new`로 새로 만들기.

> ⚠️ **함정 3:** **`==` String 비교 함정과 연결**. 두 String 변수의 `==`은 참조 비교. literal끼리는 pool 공유로 true 가능하나 `new String(...)` 섞이면 false.

> 💡 **꿀팁 1:** **aliasing 시각화**:
> ```
> a → [Counter: value=6] ← b
> ```
> 두 화살표가 한 객체를 가리킴.

> 💡 **꿀팁 2:** **독립 복사 만들기**: `Counter b = new Counter(a.getValue());` (새 객체 + 같은 값). 이 경우 a, b 독립.

> 💡 **꿀팁 3:** **CED 2.6.B.1 인용**: "Two different variables can hold references to the same object." — AP 단골 개념.

---

### Q2. 정답: **(A) `NullPointerException` 발생**

📌 **출제 의도:** **null 참조에 메서드 호출 시 NPE 발생** — Java의 핵심 런타임 예외. CED 1.14.A.2 직접 테스트.

📎 **연계:** **CED 1.14.A.2**: *"A method call on a null reference will result in a NullPointerException."* + **CED 1.13.B.1**: 참조 변수는 null 보유 가능.

> **핵심 개념: null + 메서드 호출 = NPE**
> - `null`은 "객체 없음"을 나타내는 특수 값
> - null 참조에 메서드 호출 또는 필드 접근 시 **`NullPointerException`** 발생
> - 컴파일러는 잡지 못함 (런타임 발생)
> - 회피 방법: 호출 전 null 체크 (`if (s != null) ...`)

> **선행 지식:**
> - `String s = null;` 정상 컴파일 (참조에 null 대입 가능)
> - `s.length()` 시 런타임 에러
> - `len = 0` 같은 기본값 자동 부여 안 됨

**런타임 진행:**

| 단계 | 동작 | 결과 |
|---|---|---|
| 1 | `String s = null` | s = null (참조 없음) — 정상 컴파일 |
| 2 | `s.length()` 호출 시도 | null에 메서드 호출 → **`NullPointerException`** |
| 3 | 프로그램 비정상 종료 (catch 없음) | — |

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `NullPointerException` 발생** ✅ | 정답 | null.length() → NPE |
| (B) `0` | null의 length가 0이라고 오해 | null은 객체가 아니라 length 개념 자체 없음 |
| (C) Compile error | `String s = null` 컴파일 안 된다고 오해 | 참조에 null 대입은 정상 |
| (D) `-1` | indexOf 같은 -1 반환 패턴 오해 | NPE 발생 (return 자체 없음) |

> ⚠️ **함정 1:** **null과 빈 문자열("")의 차이**. `""`은 길이 0인 정상 String 객체, length() = 0. `null`은 객체 자체가 없음, length() = NPE.

> ⚠️ **함정 2:** **null 체크 누락**. AP FRQ에서 null 가능성 있는 곳에 체크 누락 시 자주 감점. 표준 패턴: `if (obj != null) obj.method();`

> ⚠️ **함정 3:** **컴파일러는 NPE 잡지 못함**. Java는 정적 분석으로 모든 null을 잡지 않음. 런타임에 발생.

> 💡 **꿀팁 1:** **null-safe 패턴 (Q6과 연결)**:
> ```java
> if (s != null && s.length() > 0) { ... }
> ```
> short-circuit으로 NPE 회피.

> 💡 **꿀팁 2:** **`!=` null 비교**. CED 2.6.B.2: *"An object reference can be compared with null, using == or !=."*

> 💡 **꿀팁 3:** **AP에서 null 출제 패턴**:
> - 직접 NPE 발생 (본 문제)
> - null 체크 패턴 (Q6, TP6 Q3)
> - 메서드가 null 반환 후 호출 (예: findItem 못 찾으면 null)

---

### Q3. 정답: **(B) `99`**

📌 **출제 의도:** **배열 매개변수 = 참조 복사 (aliasing)** — 메서드가 원본 배열을 변경 가능. CED 3.6.A.1의 핵심: "참조 복사, 객체 복사 아님".

📎 **연계:** **CED 3.6.A.1**: *"When an argument is an object reference, the parameter is initialized with a copy of that reference; it does not create a new independent copy of the object. If the parameter refers to a mutable object, the method or constructor can use this reference to alter the state of the object."*

> **핵심 개념: 배열 = 참조 타입**
> - 배열도 객체 (heap에 저장, 참조로 접근)
> - `modify(data)` 호출 시 `arr`은 **`data`의 참조 복사본** (같은 배열 가리킴)
> - `arr[0] = 99` → 같은 배열의 인덱스 0 변경 → `data[0]`도 99
> - 메서드 종료 후에도 변경 영향 남음

> **선행 지식:**
> - 배열은 객체 (CED 4.1)
> - primitive 매개변수는 값 복사, 객체/배열 매개변수는 참조 복사
> - 메서드가 원본을 변경할 수 있음 → side effect

**한 단계씩 추적:**

| 단계 | 동작 | data | arr (메서드 내) |
|---|---|---|---|
| 1 | `data = {1, 2, 3}` | {1, 2, 3} (R1) | — |
| 2 | `modify(data)` 호출 | (R1) | arr → R1 (data와 같음) |
| 3 | `arr[0] = 99` | {99, 2, 3} (R1) | arr → R1 (변경됨) |
| 4 | 메서드 종료 | {99, 2, 3} (R1) | — |
| 5 | `data[0]` | 99 | — |

**최종 출력: `99`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `1` | 배열도 값 복사라고 오해 | 배열은 참조 복사 (CED 3.6.A.1) |
| **(B) `99`** ✅ | 정답 | 메서드가 원본 변경 |
| (C) `0` | 배열이 초기화된다고 오해 | data는 그대로 |
| (D) Compile error | 배열을 메서드에 못 넘긴다고 오해 | 정상 컴파일 |

> ⚠️ **함정 1:** **primitive vs 참조 매개변수**. `int x` 매개변수: 값 복사, 메서드 내 변경 호출자 영향 없음. `int[] arr` 매개변수: 참조 복사, 객체 변경은 영향 있음.

> ⚠️ **함정 2:** **변경 가능 객체 (mutable)**. 배열은 mutable (`arr[i] = ...`). String은 immutable (변경 불가). mutable 객체는 메서드에서 변경 시 영향.

> ⚠️ **함정 3:** **`arr = new int[]{...}` 차이**. 메서드 내 재할당은 호출자 영향 없음 (Q4 참조). 객체 자체 변경(`arr[0] = ...`)은 영향.

> 💡 **꿀팁 1:** **AP FRQ 패턴**: "modify the array in place" — 배열 매개변수로 받아 직접 변경. void 반환.

> 💡 **꿀팁 2:** **side effect 의도적 설계**: 큰 배열을 매번 새로 만들기 비효율 → 매개변수로 받아 in-place 수정 표준 관용구.

> 💡 **꿀팁 3:** **방어적 패턴 (CED 3.4.A.3)**: 호출자의 객체를 변경하고 싶지 않으면 메서드 내에서 복사 후 작업.

---

### Q4. 정답: **(D) `99`**

📌 **출제 의도:** **객체 변경 vs 참조 재할당의 차이** — 매개변수로 받은 객체의 메서드 호출(setValue)은 호출자에 영향, 매개변수 변수 자체에 새 객체 대입(`b = new Box`)은 호출자에 영향 없음.

📎 **연계:** **CED 3.6.A.1** 객체 참조 매개변수 + Java의 매개변수 전달 메커니즘 (call by value of reference).

> **핵심 개념: 객체 변경 vs 참조 변경**
> - **객체 변경** (`b.setValue(99)`): 같은 객체의 상태 변경 → 호출자도 영향
> - **참조 재할당** (`b = new Box(0)`): 매개변수 변수만 새 객체 가리킴 → 호출자의 mine은 그대로
> - Java는 **call by value** (참조 자체는 값으로 전달)
> - 매개변수 b는 호출자의 mine과 별개 변수이지만, 처음에 같은 객체 가리킴

> **선행 지식:**
> - 매개변수도 지역 변수 (메서드 종료 시 사라짐)
> - 매개변수 자체에 대입은 호출자의 변수에 영향 없음
> - 매개변수가 가리키는 객체의 메서드 호출은 영향

**한 단계씩 추적:**

| 단계 | 동작 | mine | b (메서드 내) | 객체 R1 |
|---|---|---|---|---|
| 1 | `mine = new Box(5)` | → R1 | — | value=5 |
| 2 | `modify(mine)` 진입 | → R1 | b → R1 (같은 참조) | value=5 |
| 3 | `b.setValue(99)` | → R1 | → R1 | **value=99** |
| 4 | `b = new Box(0)` | → R1 (변화 없음) | b → R2 (새 객체) | R1 그대로 |
| 5 | 메서드 종료 | → R1 | — | value=99 |
| 6 | `mine.getValue()` | → R1.value = 99 | — | — |

**최종 출력: `99`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `0` | `b = new Box(0)`이 mine에도 영향 준다고 오해 | 지역 변수 b만 재할당, mine 영향 없음 |
| (B) `5` | setValue가 작동 안 한다고 오해 | 같은 객체 변경 → mine.value = 99 |
| (C) Compile error | 메서드 내 `b = new Box(0)` 못 한다고 오해 | 정상 컴파일 (지역 변수 재할당 OK) |
| **(D) `99`** ✅ | 정답 | setValue 영향 (99), b 재할당은 영향 없음 |

> ⚠️ **함정 1:** **참조 재할당 vs 객체 변경 구별**. `b = new ...`는 b 변수에만 영향. `b.method()`는 객체에 영향 (호출자도 본다).

> ⚠️ **함정 2:** **Java는 call by reference 아님**. 항상 call by value (단, 객체 매개변수는 참조의 값을 복사). 따라서 매개변수 재할당이 호출자에 영향 없음.

> ⚠️ **함정 3:** **메서드 내 순서**. `b.setValue(99)` 먼저 → 객체 영향. `b = new Box(0)` 이후 → b만 새 객체로. 두 효과 모두 추적해야.

> 💡 **꿀팁 1:** **참조 재할당 효과 시각화**:
> ```
> 시작:  mine → R1 (value=5)
>        b    → R1 (같은 객체)
> setValue 후: R1.value = 99
> b 재할당 후: mine → R1 (value=99 그대로)
>             b    → R2 (새 객체, 메서드 종료 시 소멸)
> ```

> 💡 **꿀팁 2:** **swap 메서드 불가**. `void swap(int a, int b) { int t=a; a=b; b=t; }`로 호출자 변수 swap 안 됨 (call by value). 객체 매개변수도 마찬가지.

> 💡 **꿀팁 3:** **defensive 의도**: 호출자의 객체를 보호하려면 메서드 시작 시 defensive copy 수행 → 이후 작업이 원본에 영향 없음.

---

### Q5. 정답: **(A) `99`**

📌 **출제 의도:** **defensive copy 누락의 위험** — 생성자에서 mutable 객체를 그대로 저장하면 외부에서의 변경이 클래스 내부 상태에 영향. CED 3.4.A.3의 안티패턴.

📎 **연계:** **CED 3.4.A.3**: *"When a mutable object is a constructor parameter, the instance variable should be initialized with a copy of the referenced object. In this way, the instance variable does not hold a reference to the original object, and methods are prevented from modifying the state of the original object."*

> **핵심 개념: defensive copy 누락**
> - `items = arr;` → 인스턴스 변수가 매개변수와 **같은 배열** 가리킴
> - 외부에서 `original` 변경 시 → `items`도 같이 변경 (aliasing)
> - **권장 방식**: 새 배열 만들어 복사
>   ```java
>   items = new int[arr.length];
>   for (int i = 0; i < arr.length; i++) items[i] = arr[i];
>   ```

> **선행 지식:**
> - 배열은 mutable (요소 변경 가능)
> - String은 immutable → defensive copy 불필요
> - CED 3.4.A.3은 "should be" (권장) — 위반 시 컴파일 에러는 아니지만 버그 위험

**한 단계씩 추적:**

| 단계 | 동작 | original | b.items |
|---|---|---|---|
| 1 | `original = {10, 20, 30}` | {10, 20, 30} (R1) | — |
| 2 | `new Bag(original)` 호출 | (R1) | arr → R1 |
| 3 | `items = arr` (defensive copy 없음!) | (R1) | items → R1 (같은 배열!) |
| 4 | `original[0] = 99` | {99, 20, 30} (R1) | items → R1 (변경됨!) |
| 5 | `b.firstItem()` = items[0] = R1[0] | (R1) | **99** |

**최종 출력: `99`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `99`** ✅ | 정답 | aliasing — 외부 변경이 내부에 영향 |
| (B) `10` | defensive copy가 자동으로 일어난다고 오해 | 명시적 복사 없음 → aliasing |
| (C) `0` | 새 배열로 초기화된다고 오해 | 코드는 그대로 참조 저장 |
| (D) Compile error | 코드 문법 문제 의심 | 정상 컴파일 (단, 좋은 디자인 아님) |

> ⚠️ **함정 1:** **defensive copy 권장 (should be)**. CED는 "권장"이지 "필수"가 아님. 본 코드는 컴파일되고 실행되지만 디자인 결함.

> ⚠️ **함정 2:** **mutable vs immutable**. 배열, ArrayList, 사용자 정의 mutable 클래스는 defensive copy 필요. String, Integer 등 immutable은 안전.

> ⚠️ **함정 3:** **getter 반환에도 같은 문제**. `getItems()`로 내부 배열 그대로 반환하면 외부 코드가 변경 가능. 반환 시도 defensive copy 필요.

> 💡 **꿀팁 1:** **올바른 defensive copy** (CED 3.4.A.3 권장):
> ```java
> public Bag(int[] arr) {
>     items = new int[arr.length];
>     for (int i = 0; i < arr.length; i++) {
>         items[i] = arr[i];
>     }
> }
> ```

> 💡 **꿀팁 2:** **AP FRQ 단골 함정**: 생성자에서 매개변수를 그대로 저장하면 채점에서 감점 가능. 특히 "내부 상태 보호" 명시 시 defensive copy 필수.

> 💡 **꿀팁 3:** **shallow vs deep copy**: 배열 안에 객체가 있으면 shallow copy (참조만 복사)도 부족. deep copy 필요. AP는 1D 배열 위주라 shallow로 충분한 경우 많음.

---

### Q6. 정답: **(B) `"true true false"`**

📌 **출제 의도:** **null + short-circuit으로 안전한 검사** — `label == null` 먼저 체크, true면 우측 미평가 (NPE 회피). null과 빈 문자열을 모두 "비어있음"으로 분류.

📎 **연계:** **CED 1.14.A.2** (NPE) + **CED 2.5.A.2** (short-circuit) + **CED 2.6.B.2** (null 비교).

> **핵심 개념: null-safe + 빈 문자열 처리**
> ```java
> return label == null || label.length() == 0;
> ```
> - **`label == null`** 먼저 평가:
>   - true → short-circuit, return true (NPE 회피)
>   - false → 우측 평가 가능
> - **`label.length() == 0`** (label이 non-null 보장된 후 안전):
>   - 빈 문자열 ""이면 true
>   - 내용 있으면 false

> **선행 지식:**
> - null과 "" (빈 String)은 다름! 둘 다 "비어있다"고 보려면 둘 다 체크
> - `||` short-circuit: 좌측 true → 우측 미평가
> - 순서 중요: null 체크가 먼저여야 NPE 회피

**3개 인스턴스 추적:**

**a (label=null):**

| 단계 | 평가 |
|---|---|
| 1 | `null == null` → **true** |
| 2 | short-circuit → 우측 미평가 (NPE 회피) |
| 3 | return **true** |

**b (label=""):**

| 단계 | 평가 |
|---|---|
| 1 | `"" == null` → **false** |
| 2 | 우측 평가: `"".length() == 0` → **true** |
| 3 | false || true = **true** |

**c (label="hello"):**

| 단계 | 평가 |
|---|---|
| 1 | `"hello" == null` → **false** |
| 2 | 우측 평가: `"hello".length() == 0` → 5==0 → **false** |
| 3 | false || false = **false** |

**최종: a=true, b=true, c=false → 출력 `"true true false"`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `"false false false"` | 모든 메서드가 false 반환이라 오해 | a, b는 비어있음 → true |
| **(B) `"true true false"`** ✅ | 정답 | null과 빈 String 모두 true |
| (C) `NPE 발생` | a.isEmpty()에서 NPE라 오해 | short-circuit으로 회피 |
| (D) `"true false false"` | 빈 String("")이 비지 않음이라 오해 | length()==0이면 비어있음 |

> ⚠️ **함정 1:** **null vs "" 구별**. `null`은 객체 없음, `""`은 길이 0인 객체. 두 케이스 모두 처리하려면 OR.

> ⚠️ **함정 2:** **`||` 순서가 결정적**. `length() == 0 || label == null`로 거꾸로 쓰면 a에서 NPE 발생. **반드시 null 체크 먼저**.

> ⚠️ **함정 3:** **`label.length() == 0` vs `label.equals("")`**. 동등하지만 length 체크가 더 효율적. 둘 다 정상 (단, `==`로 String 비교 X).

> 💡 **꿀팁 1:** **표준 null-safe + empty 검사**:
> ```java
> if (s == null || s.length() == 0) { /* 비어있음 */ }
> ```

> 💡 **꿀팁 2:** **`!isEmpty()` 패턴**: 비어있지 않을 때 처리하려면 `if (s != null && s.length() > 0)` (De Morgan: `!(A || B) ≡ !A && !B`).

> 💡 **꿀팁 3:** **isEmpty 메서드 정의 (사용자 클래스)**: AP에서 클래스에 `isEmpty` 메서드를 직접 정의하는 패턴 자주 등장. 본 문제처럼 null + length 결합.

---

## 종합 정리

### 1.12 + 1.13 객체 참조
- 참조 변수: 객체 주소 또는 null 보유
- 객체는 heap에 저장
- primitive와 다름 (값 복사 vs 참조 복사)

### 2.6.B Aliasing
```java
Counter b = a;      // b와 a는 같은 객체 가리킴
b.method();         // a 객체에도 영향
a == b              // true (같은 참조)
```

### 1.14.A.2 NullPointerException
- null에 메서드 호출 → NPE
- 회피: `if (obj != null) obj.method();`
- short-circuit: `obj != null && obj.method()` (Q6)

### 3.6.A.1 객체 매개변수
- 참조 복사 (객체 자체 복사 아님)
- 메서드가 객체 변경 시 호출자에 영향
- 매개변수 자체 재할당은 호출자에 영향 없음

### 3.4.A.3 Defensive Copy
```java
// 권장 (defensive copy)
public Bag(int[] arr) {
    items = new int[arr.length];
    for (int i = 0; i < arr.length; i++) items[i] = arr[i];
}

// 위험 (aliasing)
public Bag(int[] arr) {
    items = arr;
}
```

### 흔한 함정 모음
1. **aliasing 인지 못함** (Q1): `b = a` 후 변경이 양쪽에 영향
2. **null 메서드 호출 → NPE** (Q2)
3. **배열 매개변수 = 참조 복사** (Q3): 메서드가 원본 변경 가능
4. **객체 변경 vs 참조 재할당** (Q4): `b.method()` vs `b = new ...`
5. **defensive copy 누락** (Q5): 외부 변경이 내부 영향
6. **null + 빈 String 동시 처리** (Q6): `==null || length==0`

### EXCLUSION 재확인
- **상속 (`extends`/`super`) OUT** ✓
- **`Math.min/max` OUT** ✓
- **`break`/`continue` OUT** ✓
- **`switch`/`do-while` OUT** ✓
