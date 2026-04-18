# TP8: Object References + Null + Aliasing (보강 세트)

> **CED 2025-26 토픽**: 1.12 Objects (참조 타입), 1.14 Calling Instance Methods, 3.4.A.3 Defensive Copy, 3.6 Passing/Returning References
> **문항 수**: 6 MCQ (Hard)
> **시간 권장**: 15분
> **목표 정답률**: 80% 이상

---

## CED 범위 준수 사항

- **1.12.B.1**: 참조 타입 변수는 **객체 참조 또는 null** 보유
- **1.13.B.1**: 참조 타입은 **참조** 또는 **null** 저장
- **1.14.A.2**: **`null` 참조에 메서드 호출 시 NullPointerException**
- **2.6.B.1**: 두 변수가 같은 객체 참조 가능 → `==`/`!=`로 참조 비교
- **2.6.B.2**: 객체와 `null` 비교는 `==`/`!=`
- **3.4.A.3**: **mutable 객체 매개변수는 defensive copy로 인스턴스 변수 초기화 권장**
- **3.6.A.1**: 객체 참조 인자는 **참조의 복사본** 전달 (객체 자체 복사 아님)
- **3.6.A.2**: 객체 참조 반환은 **참조 그대로** 반환 (객체 복사 아님)
- **3.6.A.3**: 다른 클래스 객체 매개변수의 private 데이터 접근 불가

- **EXCLUSION**: 상속(`extends`/`super`) OUT, `Math.min/max`, `break`/`continue` 사용 금지

---

## 출제 토픽 분포

| # | 토픽 | 핵심 |
|---|------|------|
| 1 | 1.12.B.1 + 2.6.B.1 — aliasing | 두 변수 같은 객체 참조 |
| 2 | 1.14.A.2 — NullPointerException | null 메서드 호출 |
| 3 | 3.6.A.1 — 배열 참조 매개변수 | 메서드가 원본 변경 |
| 4 | 3.6.A.1 — 객체 참조 + 지역 재할당 | 객체 변경 vs 참조 재할당 |
| 5 | 3.4.A.3 — defensive copy 누락 | 외부 변경이 내부 영향 |
| 6 | 1.14.A.2 + 2.5 — null-safe 패턴 | short-circuit으로 NPE 회피 |

**답안 분포**: A:2 / B:2 / C:1 / D:1

---

## 시험 안내

**Directions**: 다음 각 문항에 대해 가장 적절한 답을 고르시오.

---

### 1. [CED 1.12 + 2.6.B.1 · Hard]

다음 코드의 출력은? (CED 2.6.B.1: *"Two different variables can hold references to the same object"*)

```java
public class Counter
{
    private int value;
    public Counter(int v) { value = v; }
    public int getValue() { return value; }
    public void increment() { value++; }
}
```

```java
Counter a = new Counter(5);
Counter b = a;          // aliasing — 같은 객체 참조
b.increment();
System.out.println(a.getValue() + " " + b.getValue());
```

(A) `"5 6"`
(B) `"5 5"`
(C) `"6 6"`
(D) `"6 5"`

---

### 2. [CED 1.14.A.2 · Hard]

다음 코드의 결과는? (CED 1.14.A.2: *"A method call on a null reference will result in a NullPointerException"*)

```java
String s = null;
int len = s.length();
System.out.println(len);
```

(A) `NullPointerException` 발생
(B) `0`
(C) Compile-time error (String을 null로 초기화 불가)
(D) `-1`

---

### 3. [CED 3.6.A.1 · Hard]

다음 메서드는 배열을 매개변수로 받는다 (CED 3.6.A.1: *"the parameter is initialized with a copy of that reference; it does not create a new independent copy of the object"*).

```java
public static void modify(int[] arr)
{
    arr[0] = 99;
}
```

다음 코드의 출력은?

```java
int[] data = {1, 2, 3};
modify(data);
System.out.println(data[0]);
```

(A) `1`
(B) `99`
(C) `0`
(D) `Compile error`

---

### 4. [CED 3.6.A.1 · Hard]

다음 메서드는 객체 참조 매개변수를 **수정한 후 새 객체로 재할당**한다.

```java
public class Box
{
    private int value;
    public Box(int v) { value = v; }
    public int getValue() { return value; }
    public void setValue(int v) { value = v; }
}

public static void modify(Box b)
{
    b.setValue(99);          // 원본 객체 수정
    b = new Box(0);          // 지역 변수 b만 재할당 (호출자에 영향 없음)
}
```

다음 코드의 출력은?

```java
Box mine = new Box(5);
modify(mine);
System.out.println(mine.getValue());
```

(A) `0`
(B) `5`
(C) `Compile error`
(D) `99`

---

### 5. [CED 3.4.A.3 · Hard]

다음 클래스는 **defensive copy를 누락**했다 (CED 3.4.A.3 위반 예시).

```java
public class Bag
{
    private int[] items;

    // ⚠️ defensive copy 없이 그대로 저장 — 권장되지 않음
    public Bag(int[] arr) { items = arr; }

    public int firstItem() { return items[0]; }
}
```

다음 코드의 출력은?

```java
int[] original = {10, 20, 30};
Bag b = new Bag(original);
original[0] = 99;             // 외부에서 원본 배열 변경
System.out.println(b.firstItem());
```

(A) `99`
(B) `10`
(C) `0`
(D) `Compile error`

---

### 6. [CED 1.14.A.2 + 2.5.A.2 · Hard]

다음 클래스는 **short-circuit evaluation**으로 null-safe 검사를 한다 (CED 2.5.A.2 + 1.14.A.2).

```java
public class Container
{
    private String label;
    public Container(String l) { label = l; }

    public boolean isEmpty()
    {
        return label == null || label.length() == 0;
    }
}
```

다음 코드의 출력은?

```java
Container a = new Container(null);
Container b = new Container("");
Container c = new Container("hello");
System.out.println(a.isEmpty() + " " + b.isEmpty() + " " + c.isEmpty());
```

(A) `"false false false"`
(B) `"true true false"`
(C) `"NullPointerException 발생 (a.isEmpty 호출 시)"`
(D) `"true false false"`

---

**END OF TP8**
