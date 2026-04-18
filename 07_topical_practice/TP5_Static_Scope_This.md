# TP5: Static, Final, Scope, this (보강 세트)

> **CED 2025-26 토픽**: 3.7 Class Variables and Methods, 3.8 Scope and Access, 3.9 `this` Keyword
> **문항 수**: 8 MCQ (Hard 위주)
> **시간 권장**: 20분
> **목표 정답률**: 80% 이상

---

## CED 범위 준수 사항

- **3.7.A.1**: 클래스 메서드는 인스턴스 변수/메서드에 직접 접근 불가 (객체를 매개변수로 받지 않으면)
- **3.7.A.2**: 클래스 메서드는 다른 클래스 변수/메서드 접근 가능
- **3.7.B.1**: 클래스 변수는 `static`으로 선언, 모든 객체가 **단일 복사본** 공유
- **3.7.B.2**: `public` 클래스 변수는 **클래스명.변수** 로 접근
- **3.7.B.3**: `final`로 선언된 변수의 값은 **수정 불가**
- **3.8.A.1**: 지역 변수는 선언된 블록 내에서만 접근 가능. `public`/`private` 지정 불가
- **3.8.A.2**: 지역 변수가 인스턴스 변수와 같은 이름이면 **지역 변수가 우선** (shadowing)
- **3.9.A.1**: `this`는 인스턴스 메서드/생성자 내에서 **현재 객체 참조**
- **3.9.A.2**: `this`로 현재 객체를 인자로 전달 가능
- **3.9.A.3**: 클래스 메서드는 `this` 참조 없음

- **EXCLUSION**: 상속 (`extends`, `super`), `Math.min/max`, `break`/`continue` 사용 금지

---

## 출제 토픽 분포

| # | 토픽 | 핵심 |
|---|------|------|
| 1 | 3.7.B.1 — static 변수 공유 | 모든 객체가 단일 복사본 |
| 2 | 3.7.B.1 + 3.7.A.2 — static 메서드로 클래스 변수 변경 | setRate 후 모든 객체 영향 |
| 3 | 3.7.B.3 + 3.7.A.2 — `final` + static 메서드 호출 | 평가 순서 |
| 4 | 3.7.B.3 — `final` instance 변수 | 생성자 내 1회 초기화 |
| 5 | 3.8.A.2 — shadowing (생성자 매개변수) | `this.age = age` vs `age = age` |
| 6 | 3.8.A.2 — 메서드 내 지역 변수 vs 인스턴스 | 같은 이름 시 지역 우선 |
| 7 | 3.9.A.1 — `this`로 현재 객체 참조 | clone 메서드, 새 객체 생성 |
| 8 | 3.9.A.2 — `this`를 인자로 전달 | 메서드 내 다른 객체에 자기 전달 |

**답안 분포**: A:2 / B:2 / C:2 / D:2

---

## 시험 안내

**Directions**: 다음 각 문항에 대해 가장 적절한 답을 고르시오. 별도 명시가 없는 한 Java Quick Reference의 클래스가 import되어 있다고 가정한다.

---

### 1. [CED 3.7.B.1 · Hard]

다음은 **static 변수**를 사용한 카운터 클래스이다 (CED 3.7.B.1: *"Class variables belong to the class, with all objects of a class sharing a single copy of the class variable"*).

```java
public class Counter
{
    private static int total = 0;
    private int id;

    public Counter()
    {
        total++;
        id = total;
    }

    public int getId() { return id; }
    public static int getTotal() { return total; }
}
```

다음 코드의 출력은?

```java
Counter a = new Counter();
Counter b = new Counter();
Counter c = new Counter();
System.out.println(a.getId() + " " + b.getId() + " " + c.getId() + " " + Counter.getTotal());
```

(A) `"3 3 3 3"`
(B) `"0 0 0 0"`
(C) `"1 1 1 3"`
(D) `"1 2 3 3"`

---

### 2. [CED 3.7 · Hard]

다음 클래스에서 `interestRate`는 **모든 Bank 인스턴스가 공유**하는 클래스 변수이다.

```java
public class Bank
{
    private double balance;
    private static double interestRate = 0.05;

    public Bank(double initial) { balance = initial; }
    public void addInterest() { balance += balance * interestRate; }
    public double getBalance() { return balance; }

    public static void setRate(double r) { interestRate = r; }
}
```

다음 코드의 출력은?

```java
Bank a = new Bank(100.0);
Bank b = new Bank(200.0);
Bank.setRate(0.10);
a.addInterest();
b.addInterest();
System.out.println(a.getBalance() + " " + b.getBalance());
```

(A) `"100.0 200.0"`
(B) `"105.0 210.0"`
(C) `"110.0 220.0"`
(D) `"120.0 240.0"`

---

### 3. [CED 3.7.B.3 + 3.7.A.2 · Hard]

다음 클래스는 **`final` 상수와 static 카운터**를 함께 사용한다 (CED 3.7.B.3: *"When a variable is declared final, its value cannot be modified"*).

```java
public class Constants
{
    public static final int LIMIT = 50;
    private static int counter = 0;

    public static int increment()
    {
        counter++;
        return counter;
    }
}
```

다음 코드 실행 후 출력은?

```java
Constants.increment();
Constants.increment();
Constants.increment();
System.out.println(Constants.LIMIT + " " + Constants.increment());
```

(A) `"50 3"`
(B) `"50 4"`
(C) `"Compile error"`
(D) `"100 4"`

---

### 4. [CED 3.7.B.3 · Hard]

다음 클래스는 **인스턴스 `final` 변수**를 사용한다 (생성자에서 1회 초기화 후 수정 불가).

```java
public class Box
{
    private final int capacity;
    private int items;

    public Box(int cap)
    {
        capacity = cap;
        items = 0;
    }

    public boolean add()
    {
        if (items < capacity)
        {
            items++;
            return true;
        }
        return false;
    }

    public int getItems() { return items; }
}
```

다음 코드의 출력은?

```java
Box b = new Box(3);
boolean r1 = b.add();
boolean r2 = b.add();
boolean r3 = b.add();
boolean r4 = b.add();
System.out.println(r1 + " " + r2 + " " + r3 + " " + r4 + " " + b.getItems());
```

(A) `"true true true false 3"`
(B) `"true true true true 4"`
(C) `"true true false false 2"`
(D) `"Compile error (cannot assign to final)"`

---

### 5. [CED 3.8.A.2 · Hard]

다음 두 클래스는 매개변수와 인스턴스 변수의 **이름 충돌(shadowing)** 처리가 다르다.

```java
public class Person {
    private int age;
    public Person(int age) {
        this.age = age;       // this.age = 인스턴스, age = 매개변수
    }
    public int getAge() { return age; }
}

public class Person2 {
    private int age;
    public Person2(int age) {
        age = age;            // 매개변수 → 매개변수 자체에 대입 (인스턴스 변수에 영향 없음)
    }
    public int getAge() { return age; }
}
```

다음 코드의 출력은?

```java
Person p1 = new Person(25);
Person2 p2 = new Person2(30);
System.out.println(p1.getAge() + " " + p2.getAge());
```

(A) `"25 30"`
(B) `"0 0"`
(C) `"30 25"`
(D) `"25 0"`

---

### 6. [CED 3.8.A.2 · Hard]

다음 클래스에서 메서드 내 **지역 변수가 인스턴스 변수를 가린다(shadowing)**.

```java
public class Test
{
    private int x = 100;

    public void method()
    {
        int x = 5;            // 지역 변수가 인스턴스 변수 가림
        for (int i = 0; i < 3; i++)
        {
            x++;              // 지역 변수에만 영향
        }
        System.out.println(x + " " + this.x);
    }
}
```

다음 호출 시 출력은?

```java
Test t = new Test();
t.method();
```

(A) `"103 100"`
(B) `"8 100"`
(C) `"5 100"`
(D) `"8 103"`

---

### 7. [CED 3.9.A.1 · Hard]

다음 클래스는 `this` 키워드로 **현재 객체 참조**(CED 3.9.A.1)를 사용한다.

```java
public class Point
{
    private int x;
    private int y;

    public Point(int x, int y)
    {
        this.x = x;
        this.y = y;
    }

    public int sum() { return this.x + this.y; }

    public Point clone()
    {
        return new Point(this.x, this.y);   // 새 Point 객체 생성
    }
}
```

다음 코드의 출력은?

```java
Point p1 = new Point(3, 4);
Point p2 = p1.clone();
System.out.println(p1.sum() + " " + p2.sum() + " " + (p1 == p2));
```

(A) `"7 7 false"`
(B) `"7 7 true"`
(C) `"3 3 false"`
(D) `"Compile error"`

---

### 8. [CED 3.9.A.2 · Hard]

다음 클래스는 **`this`를 다른 메서드에 인자로 전달**한다 (CED 3.9.A.2: *"The keyword this can be used to pass the current object as an argument in a method call"*).

```java
public class Node
{
    private int value;

    public Node(int v) { value = v; }
    public int getValue() { return value; }

    public int compareWith(Node other)
    {
        return this.value - other.getValue();
    }

    public boolean isLargerThan(Node other)
    {
        // this(현재 객체)를 other.compareWith의 인자로 전달
        return other.compareWith(this) < 0;
    }
}
```

다음 코드의 출력은?

```java
Node a = new Node(10);
Node b = new Node(7);
System.out.println(a.isLargerThan(b) + " " + b.isLargerThan(a));
```

(A) `"false true"`
(B) `"false false"`
(C) `"true false"`
(D) `"true true"`

---

**END OF TP5**
