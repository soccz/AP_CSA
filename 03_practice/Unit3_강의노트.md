# Unit 3: Class Creation

> **시험 비중:** 10-18% | **수업 시간:** ~20-22기간  
> **FRQ:** Q2 (Complete Class Design)

---

## 3.1 Abstraction and Program Design (2기간)

### 핵심 개념

**Abstraction(추상화)** = 복잡성을 줄이고 핵심에만 집중하는 것

| 종류 | 설명 | 예시 |
|------|------|------|
| **Data Abstraction** | 데이터의 이름만으로 사용, 구현 세부사항 숨김 | `student.getName()` — 이름이 어떻게 저장되는지 몰라도 됨 |
| **Procedural Abstraction** | 메서드 이름만 알면 사용 가능, 내부 구현 몰라도 됨 | `Math.sqrt(25)` — 어떤 알고리즘인지 몰라도 됨 |

**Attribute(속성)의 두 종류:**
- **Instance variable** — 인스턴스마다 고유한 값 (예: 각 학생의 이름)
- **Class variable** — 모든 인스턴스가 공유 (예: 학생 수 카운터)

**Method Decomposition** — 큰 행동을 작은 메서드들로 분해

```java
// 나쁜 예: 하나의 거대한 메서드
public void processOrder() {
    // 100줄짜리 코드...
}

// 좋은 예: 작은 메서드로 분해
public void processOrder() {
    validateItems();
    calculateTotal();
    applyDiscount();
    generateReceipt();
}
```

### 시험 포인트
- Abstraction의 **목적** = 복잡성 감소 (reduce complexity)
- Data abstraction vs Procedural abstraction 구분 가능해야 함
- Instance variable vs Class variable 차이

### 연습문제

**Q1.** 다음 중 data abstraction의 예로 가장 적절한 것은?
- (A) `for` 루프를 사용하여 배열을 순회
- (B) `ArrayList`를 사용하여 데이터를 저장하되, 내부 구현은 신경쓰지 않음
- (C) `if-else`로 조건 분기
- (D) 변수에 값을 대입

> **정답: (B)** — 내부 구현을 모르고 이름(인터페이스)만으로 사용하는 것이 data abstraction

**Q2.** Method decomposition의 주요 이점을 두 가지 서술하시오.

> **모범답안:** (1) 코드 재사용성 향상 — 분해된 메서드를 다른 곳에서도 호출 가능 (2) 디버깅 용이 — 문제 발생 시 어느 메서드에서 발생했는지 추적 쉬움

---

## 3.2 Impact of Program Design (1기간)

### 핵심 개념

**System Reliability** — 다양한 조건에서 정상 동작하는 능력
- edge case 처리 (빈 입력, 음수, null 등)
- 테스트를 통한 검증

**사회적 영향:**

| 영향 | 긍정적 예시 | 부정적 예시 |
|------|------------|------------|
| 사회 | 의료 앱으로 건강 관리 | 알고리즘 편향(bias)으로 차별 |
| 경제 | 자동화로 효율 향상 | 일자리 감소 |
| 문화 | 온라인으로 문화 교류 | 개인정보 침해 |

**Legal Issues:**
- **Open source** — 자유롭게 사용/수정/배포 가능 (라이선스 조건 확인 필요)
- **Proprietary/Licensed code** — 허가 없이 사용 불가

### 시험 포인트
- 이 토픽은 MC에서 1문제 정도 출제 가능
- "프로그램 설계가 사회에 미치는 영향" 서술형 준비

### 연습문제

**Q1.** 소프트웨어의 system reliability를 높이기 위한 방법으로 적절하지 않은 것은?
- (A) 다양한 입력값으로 테스트
- (B) edge case 처리 코드 추가
- (C) 모든 메서드를 public으로 선언
- (D) 에러 발생 시 적절한 처리 로직 구현

> **정답: (C)** — 접근 제한자를 적절히 사용하는 것이 reliability에 기여. 모두 public은 캡슐화 위반.

---

## 3.3 Anatomy of a Class (2기간)

> **쉽게 말해**: 클래스는 **붕어빵 틀**, 객체는 **붕어빵**이다. 틀(클래스)은 하나지만 붕어빵(객체)은 여러 개 만들 수 있다. 각 붕어빵은 같은 모양이지만 안에 든 재료(인스턴스 변수)는 다를 수 있다. 클래스를 만드는 것 = 나만의 새로운 데이터 타입을 정의하는 것이다.

### 핵심 개념

**Data Encapsulation(캡슐화)** = 구현 세부사항을 외부로부터 숨김

```java
public class Student {
    // instance variables: 반드시 private
    private String name;
    private int grade;
    private double gpa;

    // constructor: 반드시 public
    public Student(String name, int grade, double gpa) {
        this.name = name;
        this.grade = grade;
        this.gpa = gpa;
    }

    // public 메서드: 외부에서 접근 가능
    public String getName() {
        return name;
    }

    public void setGrade(int newGrade) {
        grade = newGrade;
    }

    // private 메서드: 클래스 내부에서만 사용
    private boolean isValidGpa(double g) {
        return g >= 0.0 && g <= 4.0;
    }
}
```

**접근 제한자 규칙:**

| 요소 | 접근 제한자 | 이유 |
|------|-----------|------|
| `class` | `public` | 외부에서 사용해야 하므로 |
| `constructor` | `public` | 외부에서 객체를 생성해야 하므로 |
| `instance variable` | `private` | **캡슐화** — 직접 접근 차단 |
| accessor/mutator 메서드 | `public` | 제어된 접근 제공 |
| helper 메서드 | `private` | 내부 구현 세부사항 |

### 시험 포인트
- **instance variable은 반드시 `private`** — 시험에서 가장 자주 나오는 캡슐화 규칙
- class와 constructor는 `public`
- `private` 메서드는 같은 클래스 내부에서만 호출 가능

### 연습문제

**Q1.** 다음 코드의 문제점은?
```java
public class BankAccount {
    public double balance;

    public BankAccount(double initial) {
        balance = initial;
    }
}
```

> **정답:** `balance`가 `public`으로 선언되어 캡슐화 위반. 외부에서 `account.balance = -1000;`처럼 직접 수정 가능. `private`으로 변경하고 getter/setter를 제공해야 함.

**Q2.** `private` 메서드는 어디에서 호출할 수 있는가?
- (A) 같은 패키지의 모든 클래스
- (B) 같은 클래스 내부에서만
- (C) 어디서든 호출 가능
- (D) 같은 패키지에서만 (default access)

> **정답: (B)**

---

## 3.4 Constructors (2기간)

### 핵심 개념

**객체의 State(상태)** = 모든 instance variable의 현재 값

**has-a relationship** — 객체가 instance variable을 "가진다"
- `Student` has-a `name`, has-a `grade`, has-a `gpa`

```java
public class Dog {
    private String name;
    private String breed;
    private int age;

    // 매개변수 있는 constructor
    public Dog(String name, String breed, int age) {
        this.name = name;
        this.breed = breed;
        this.age = age;
    }

    // 오버로딩: 매개변수 다른 constructor
    public Dog(String name) {
        this.name = name;
        this.breed = "Unknown";
        this.age = 0;
    }
}
```

**Default Constructor:**
- 생성자를 하나도 작성하지 않으면 Java가 자동 제공
- 기본값: `int` → 0, `double` → 0.0, `boolean` → false, 참조형 → `null`
- **주의:** 생성자를 하나라도 작성하면 default constructor 사라짐!

**Mutable(변경 가능한) 객체 매개변수 주의:**
```java
// ★ 아래 두 생성자는 동시에 존재할 수 없습니다!
// 잘못된 방법 vs 올바른 방법을 비교하기 위한 예시입니다.

// [잘못된 방법] 같은 참조를 그대로 저장
public class ClassroomBad {
    private ArrayList<String> students;
    public ClassroomBad(ArrayList<String> students) {
        this.students = students; // 위험! 외부에서 수정 가능
    }
}

// [올바른 방법] 복사본 생성 (방어적 복사)
public class Classroom {
    private ArrayList<String> students;
    public Classroom(ArrayList<String> students) {
        this.students = new ArrayList<>(students); // 방어적 복사
    }
}
```

### 시험 포인트
- Constructor에는 **반환 타입이 없다** (`void`도 아님!)
- Constructor 이름 = 클래스 이름 (대소문자 일치)
- default constructor의 기본값 (0, 0.0, false, null) 암기
- 생성자를 하나라도 정의하면 default constructor 자동 소멸
- mutable 매개변수 → **방어적 복사(defensive copy)** 필요

#### 함정: 생성자에 반환 타입을 쓰면?

```java
public class Dog {
    private String name;
    
    public void Dog(String name) {  // ⚠️ void 반환 타입!
        this.name = name;
    }
}

Dog d = new Dog("Buddy"); // 컴파일 에러! 
// void Dog(String)은 생성자가 아니라 "Dog"이라는 이름의 일반 메서드
// 실제 생성자가 없으므로 기본 생성자 Dog()만 존재
// Dog("Buddy")에 매칭되는 생성자가 없어서 에러
```

> **시험 포인트**: 생성자에는 **절대로 반환 타입을 쓰지 않는다.** `void`를 쓰면 메서드가 된다. AP MCQ에서 자주 나오는 트릭!

### 연습문제

**Q1.** 다음 코드의 출력은?
```java
public class Point {
    private int x;
    private int y;

    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }

    public int getX() { return x; }
    public int getY() { return y; }
}

// main에서:
Point p = new Point(3, 7);
System.out.println(p.getX() + ", " + p.getY());
```

> **정답:** `3, 7`

**Q2.** 아래 클래스에 default constructor가 존재하는가?
```java
public class Cat {
    private String name;

    public Cat(String n) {
        name = n;
    }
}
```

> **정답:** 아니오. 매개변수 있는 생성자를 정의했으므로 default constructor는 사라짐. `new Cat()`은 컴파일 에러.

**Q3.** `int`, `double`, `boolean`, 참조형의 default constructor 기본값을 각각 적으시오.

> **정답:** `int` → 0, `double` → 0.0, `boolean` → false, 참조형 → `null`

---

## 3.5 Methods: How to Write Them (4기간)

> **한국어 정리**: accessor = 접근자(getter) = 값을 **읽기만** 하는 메서드. mutator = 변경자(setter) = 값을 **바꾸는** 메서드. 쉽게 말해, accessor는 "온도계로 온도를 확인"하는 것이고, mutator는 "에어컨으로 온도를 조절"하는 것이다.

### 핵심 개념

**void vs non-void 메서드:**

```java
public class Rectangle {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    // Accessor (getter) — non-void, 값 반환
    public double getWidth() {
        return width;
    }

    public double getArea() {
        return width * height;
    }

    // Mutator (setter) — void, 상태 변경
    public void setWidth(double newWidth) {
        width = newWidth;
    }

    // void 메서드: 행동만 수행
    public void doubleSize() {
        width *= 2;
        height *= 2;
    }
}
```

**Return by Value:**
```java
public int getAge() {
    return age; // age의 복사본이 반환됨 (primitive)
}
```

**return 이후 코드 — unreachable code:**
```java
public int getValue() {
    return 42;
    System.out.println("이 코드는 실행 안 됨"); // 컴파일 에러!
}
```

**매개변수는 값으로 전달 (pass by value):**
```java
public void tryToChange(int x) {
    x = 100; // 복사본을 변경 — 원본에 영향 없음
}

// main에서:
int num = 5;
obj.tryToChange(num);
System.out.println(num); // 여전히 5
```

**Accessor vs Mutator 정리:**

| 종류 | 반환 타입 | 역할 | 이름 관례 |
|------|----------|------|----------|
| Accessor (getter) | non-void | instance variable 값 읽기 | `getXxx()` |
| Mutator (setter) | 보통 void | instance variable 값 변경 | `setXxx()` |

### 시험 포인트
- `return` 문 뒤에 코드가 있으면 **컴파일 에러**
- primitive 매개변수 → 복사본 전달, **원본 불변**
- accessor = non-void (값 반환), mutator = void (상태 변경)
- non-void 메서드는 **모든 경로에서** return 필요

### 연습문제

**Q1.** 다음 코드의 출력은?
```java
public class Counter {
    private int count;

    public Counter() { count = 0; }

    public void increment() { count++; }
    public int getCount() { return count; }
}

// main에서:
Counter c = new Counter();
c.increment();
c.increment();
c.increment();
System.out.println(c.getCount());
```

> **정답:** `3`

**Q2.** 다음 메서드의 문제점은?
```java
public double average(int a, int b) {
    double avg = (a + b) / 2.0;
    System.out.println(avg);
}
```

> **정답:** non-void 메서드(`double`)인데 `return` 문이 없음. `return avg;`를 추가해야 함.

**Q3.** 다음 코드의 출력은?
```java
public static void changeValue(int x) {
    x = 999;
}

// main에서:
int a = 10;
changeValue(a);
System.out.println(a);
```

> **정답:** `10` — primitive는 값의 복사본이 전달되므로 원본 불변.

### 메서드 오버로딩 (Method Overloading)

같은 이름의 메서드를 **매개변수 타입이나 개수를 다르게** 하여 여러 개 정의할 수 있다.

```java
public class Calculator {
    public int add(int a, int b) { return a + b; }
    public double add(double a, double b) { return a + b; }
    public int add(int a, int b, int c) { return a + b + c; }
}

Calculator calc = new Calculator();
calc.add(1, 2);       // int add(int, int) 호출 → 3
calc.add(1.5, 2.5);   // double add(double, double) 호출 → 4.0
calc.add(1, 2, 3);    // int add(int, int, int) 호출 → 6
```

> **주의**: 반환 타입만 다르고 매개변수가 같으면 오버로딩이 **아님** → 컴파일 에러

### toString() 메서드 — 개념만, 작성 OUT

> **⚠️ 중대한 CED 2025-26 변경 (필독)**
> CED 1.15.A.5 EXCLUSION: *"Overriding the toString method of a class is outside the scope of the AP Computer Science A course and exam."* (CED p.50 명시)
>
> - **개념(IN)**: `println(obj)` 또는 `"..." + obj`는 자동으로 `obj.toString()` 호출 — **트레이싱 가능** (MCQ에 출제 가능)
> - **작성(OUT)**: 학생이 직접 `public String toString()` 오버라이드 작성 → **2025-26 시험 출제 안 됨**
> - **FRQ Q2 (Class Design)** 에서는 toString 대신 **`getInfo()`, `getDescription()`, `getDisplayString()` 같은 일반 메서드** 사용

#### 트레이싱 학습 예시 (이미 정의된 toString의 동작 이해)

다음 코드는 **이미 정의된** Student 클래스이며, 학생은 println의 출력 결과만 추적한다 (작성 X, 트레이싱 O).

```java
public class Student {
    private String name;
    private int grade;
    
    public Student(String name, int grade) {
        this.name = name;
        this.grade = grade;
    }
    
    // ⚠️ 학습용: toString 오버라이드는 이미 정의되어 있다고 가정
    //   (CED 1.15.A.5 EXCLUSION으로 학생이 작성하는 것은 시험 범위 외)
    public String toString() {
        return name + " (Grade " + grade + ")";
    }
}

// 사용 (학생이 트레이싱할 부분)
Student s = new Student("Kim", 11);
System.out.println(s);          // "Kim (Grade 11)"   ← 자동 toString() 호출
System.out.println("학생: " + s); // "학생: Kim (Grade 11)"
```

#### FRQ Q2 작성 권장 패턴 (toString 대신 일반 메서드)

```java
public class Student {
    private String name;
    private int grade;
    
    public Student(String name, int grade) {
        this.name = name;
        this.grade = grade;
    }
    
    // ✅ 2025-26 권장: 일반 메서드명 사용
    public String getInfo() {
        return name + " (Grade " + grade + ")";
    }
}

// 사용 (FRQ에서 명시적으로 호출)
Student s = new Student("Kim", 11);
System.out.println(s.getInfo());   // "Kim (Grade 11)"
```

> **시험 출제 포인트 (2025-26 기준)**:
> - **MCQ 트레이싱 (IN)**: 이미 정의된 toString이 println에서 자동 호출되는 동작 추적
> - **FRQ 작성 (OUT)**: 학생이 toString 오버라이드 작성 X. 대신 `getInfo()` 등 일반 메서드명 사용
> - toString을 작성하지 않으면 `클래스명@해시코드` 형태 출력 (Object 클래스 기본 동작) — 이는 트레이싱 문제로 출제 가능
> - FRQ Q2에서 객체 정보 반환 메서드가 요구되면 **`getInfo()`/`getDisplayString()` 같은 이름** 사용 (CED 1.15 EXCLUSION 회피)

#### 연습 문제 (트레이싱 — 이미 정의된 toString)

다음 코드의 출력은? (Point 클래스의 toString은 이미 정의되어 있다고 가정)

```java
public class Point {
    private int x, y;
    public Point(int x, int y) { this.x = x; this.y = y; }
    public String toString() { return "(" + x + ", " + y + ")"; }   // 트레이싱 대상 (학생 작성 X)
}
Point p = new Point(3, 7);
System.out.println("위치: " + p);
```
**(A)** `위치: Point@1a2b3c` **(B)** `위치: (3, 7)` **(C)** 컴파일 에러 **(D)** `위치: 3, 7`

> **정답: (B)** — 문자열 연결에서 자동으로 toString() 호출 (CED 1.15.A.5 IN — 트레이싱 가능). 괄호와 ", "이 포함된 형식 반환.
>
> ⚠️ **학습 포인트**: 이런 패턴의 MCQ는 출제 가능 (트레이싱). 그러나 FRQ에서 **학생이 toString 오버라이드를 작성하는 것은 OUT**.

---

## 3.6 Methods: Passing and Returning References (2기간)

### 핵심 개념

**참조형 매개변수 — 같은 객체를 가리킴!**

```java
public class NameEditor {
    // ArrayList는 mutable 참조형 → 메서드 안에서 수정하면 원본도 변경!
    public void addName(ArrayList<String> list, String name) {
        list.add(name); // 원본 list가 변경됨
    }

    // 참조 자체를 바꾸는 것은 원본에 영향 없음
    public void replaceList(ArrayList<String> list) {
        list = new ArrayList<>(); // 로컬 참조만 변경, 원본 불변
    }
}
```

```java
// main에서:
ArrayList<String> names = new ArrayList<>();
names.add("Alice");

NameEditor editor = new NameEditor();
editor.addName(names, "Bob");
System.out.println(names); // [Alice, Bob] — 원본 변경됨!

editor.replaceList(names);
System.out.println(names); // [Alice, Bob] — 참조 자체는 불변
```

**핵심 구분:**

| 동작 | 원본 영향 | 이유 |
|------|----------|------|
| `list.add("Bob")` | 원본 변경됨 | 같은 객체의 상태를 변경 |
| `list = new ArrayList<>()` | 원본 불변 | 로컬 참조(복사본)만 재할당 |

**참조 반환:**
```java
public class Team {
    private ArrayList<String> members;

    // 위험: 내부 참조를 그대로 반환
    public ArrayList<String> getMembers() {
        return members; // 외부에서 수정 가능!
    }

    // 안전: 복사본 반환
    public ArrayList<String> getMembersCopy() {
        return new ArrayList<>(members);
    }
}
```

**private 데이터 접근 제한:**
- 다른 타입의 객체에서는 private 변수에 직접 접근 불가
- 반드시 public 메서드(getter/setter)를 통해 접근

### 시험 포인트
- **참조형 매개변수:** 객체의 상태 변경 → 원본도 변경
- **참조 재할당:** `param = new ...` → 원본에 영향 없음
- 이 두 가지 차이는 시험 단골 문제!
- `String`은 immutable이므로 예외 — 참조형이지만 변경 불가

### 연습문제

**Q1.** 다음 코드의 출력은?
```java
public static void modify(int[] arr) {
    arr[0] = 99;
}

// main에서:
int[] nums = {1, 2, 3};
modify(nums);
System.out.println(nums[0]);
```

> **정답:** `99` — 배열은 참조형이므로 같은 배열 객체를 가리킴. `arr[0] = 99`는 원본 배열 변경.

**Q2.** 다음 코드의 출력은?
```java
public static void modify(String s) {
    s = s + " World";
}

// main에서:
String str = "Hello";
modify(str);
System.out.println(str);
```

> **정답:** `"Hello"` — String은 immutable. `s + " World"`는 새 String 객체를 생성하고 로컬 참조 `s`에 할당할 뿐, 원본 `str`에 영향 없음.

---

## 3.7 Class Variables and Methods (2기간)

### 핵심 개념

**`static` = 클래스에 속함 (인스턴스가 아닌 클래스 자체)**

```java
public class Student {
    private String name;
    private int id;

    // static variable: 모든 인스턴스가 공유
    private static int nextId = 1000;

    // static final: 상수 (변경 불가)
    public static final int MAX_STUDENTS = 30;

    public Student(String name) {
        this.name = name;
        this.id = nextId;  // 현재 값 사용
        nextId++;           // 다음 학생은 +1
    }

    // static method: 인스턴스 없이 호출 가능
    public static int getNextId() {
        return nextId;
    }

    // static method에서 인스턴스 변수 접근 불가!
    // public static String getName() {
    //     return name;  // 컴파일 에러!
    // }
}
```

```java
// 사용법:
Student s1 = new Student("Alice"); // id = 1000
Student s2 = new Student("Bob");   // id = 1001

// static은 ClassName으로 접근
System.out.println(Student.getNextId()); // 1002
System.out.println(Student.MAX_STUDENTS); // 30
```

**static vs instance 비교:**

| | static (클래스) | instance (인스턴스) |
|---|---|---|
| 소속 | 클래스 자체 | 각 객체 |
| 공유 | 모든 인스턴스가 공유 | 각 인스턴스 고유 |
| 접근 | `ClassName.method()` | `objectRef.method()` |
| instance 변수 접근 | **불가** | 가능 |
| `this` 사용 | **불가** | 가능 |

**`final` 키워드:**
- `final` 변수 = 값 변경 불가 (상수)
- 관례: `ALL_CAPS_WITH_UNDERSCORES`
- `static final` = 클래스 상수

### 시험 포인트
- static method는 **instance variable과 instance method에 직접 접근 불가**
- static method에서 `this` 사용 불가
- `static final` = 상수, 대문자 + 밑줄 관례
- static variable은 객체 수 카운터 등에 자주 사용

### 연습문제

**Q1.** 다음 중 컴파일 에러가 발생하는 것은?
```java
public class Example {
    private int x;
    private static int y;

    public static void methodA() {
        System.out.println(y);    // (1)
        System.out.println(x);    // (2)
    }

    public void methodB() {
        System.out.println(y);    // (3)
        System.out.println(x);    // (4)
    }
}
```

> **정답:** (2)만 에러. static method `methodA()`에서 instance variable `x`에 직접 접근 불가. (1)(3)(4)는 정상.

**Q2.** `Student` 클래스에서 생성된 총 학생 수를 추적하려면 어떤 종류의 변수를 사용해야 하는가?

> **정답:** `private static int` 변수. 모든 인스턴스가 공유하며, constructor에서 증가시킴.

---

## 3.8 Scope and Access (2기간)

### 핵심 개념

**Scope(유효 범위)** = 변수가 사용 가능한 코드 영역

```java
public class ScopeDemo {
    private int instanceVar = 10;   // scope: 클래스 전체

    public void method(int param) { // param scope: 이 메서드 전체
        int localVar = 20;          // scope: 선언 이후 ~ 메서드 끝

        for (int i = 0; i < 5; i++) { // i scope: for 블록 안에서만
            int loopVar = 30;          // scope: for 블록 안에서만
            System.out.println(instanceVar + localVar + i + loopVar);
        }
        // 여기서 i, loopVar 사용 불가!

        System.out.println(localVar);    // OK
        // System.out.println(i);        // 컴파일 에러
        // System.out.println(loopVar);  // 컴파일 에러
    }
}
```

**Scope 종류 정리:**

| 변수 종류 | 유효 범위 | 접근 제한자 가능? |
|----------|----------|----------------|
| Instance variable | 클래스 전체 | `private`/`public` |
| Class (static) variable | 클래스 전체 | `private`/`public` |
| Local variable | 선언된 블록 `{}` 안 | **불가** |
| Parameter (매개변수) | 메서드 전체 | **불가** |

**Shadowing (이름 충돌):**
```java
public class Shadow {
    private int value = 100; // instance variable

    public void demo(int value) { // parameter가 shadowing
        System.out.println(value);      // parameter의 value
        System.out.println(this.value); // instance variable의 value
    }
}
```
- **local variable > instance variable** (같은 이름이면 local이 우선)
- `this.변수명`으로 instance variable에 접근 가능

### 시험 포인트
- **local variable에는 `public`/`private` 사용 불가** — 시험에 자주 출제
- 매개변수도 local variable의 일종
- for 루프 안에서 선언한 변수는 루프 밖에서 사용 불가
- shadowing: 같은 이름 → local이 instance variable을 가림

### 연습문제

**Q1.** 다음 코드의 컴파일 에러를 찾으시오.
```java
public void process() {
    for (int i = 0; i < 10; i++) {
        // ...
    }
    System.out.println(i);
}
```

> **정답:** `i`는 for 블록 안에서 선언되었으므로 블록 밖에서 접근 불가. `System.out.println(i)`에서 컴파일 에러.

**Q2.** 다음 코드의 출력은?
```java
public class Test {
    private int x = 5;

    public void show(int x) {
        System.out.println(x);
        System.out.println(this.x);
    }
}

// main에서:
Test t = new Test();
t.show(20);
```

> **정답:** `20` (parameter), `5` (instance variable)

---

## 3.9 this Keyword (1기간)

### 핵심 개념

**`this`** = 현재 객체 자신을 가리키는 참조

```java
public class Circle {
    private double radius;

    // 용법 1: shadowing 해결
    public Circle(double radius) {
        this.radius = radius; // this.radius = instance variable
    }

    // 용법 2: 자기 자신을 인자로 전달
    public void addToList(ArrayList<Circle> circles) {
        circles.add(this); // 현재 객체를 리스트에 추가
    }

    // 용법 3: 메서드 체이닝 (AP 시험 범위는 아니지만 이해에 도움)
    public Circle setRadius(double radius) {
        this.radius = radius;
        return this;
    }

    public double getArea() {
        return Math.PI * this.radius * this.radius;
        // this 생략 가능: Math.PI * radius * radius
    }
}
```

**`this`의 핵심 규칙:**

| 상황 | this 사용 가능? |
|------|---------------|
| Instance method | O |
| Constructor | O |
| Static method | **X — 컴파일 에러** |

```java
// static 메서드에서 this 사용 불가
public static void staticMethod() {
    // System.out.println(this); // 컴파일 에러!
    // this는 "현재 인스턴스"인데, static은 인스턴스 없이 호출되므로
}
```

### 시험 포인트
- `this`의 가장 흔한 용도: **constructor에서 매개변수와 instance variable 이름이 같을 때**
- `this`는 static 메서드에서 사용 불가 (인스턴스가 없으므로)
- `this`를 메서드 인자로 전달 가능 — 현재 객체 자체를 넘김

### 연습문제

**Q1.** 다음 코드에서 `this`가 필요한 이유는?
```java
public class Person {
    private String name;

    public Person(String name) {
        this.name = name;
    }
}
```

> **정답:** parameter `name`과 instance variable `name`이 같은 이름이므로 shadowing 발생. `this.name`으로 instance variable임을 명시해야 함. `this` 없이 `name = name;`이면 parameter에 parameter를 대입하는 의미없는 코드가 됨.

**Q2.** 다음 중 컴파일 에러가 발생하는 것은?
```java
public class MyClass {
    private int val;

    public MyClass(int val) {
        this.val = val;             // (A)
    }

    public static void reset() {
        this.val = 0;               // (B)
    }

    public void show() {
        System.out.println(this.val); // (C)
    }
}
```

> **정답:** (B) — static 메서드에서 `this` 사용 불가.

---

## FRQ Q2 대비: Complete Class Design

### 출제 형식
- 시나리오 설명 + 스펙 표 (메서드 시그니처, 설명, precondition, postcondition)
- 완전한 클래스를 처음부터 작성

### 체크리스트

1. **Class header:** `public class ClassName`
2. **Private instance variables** 선언
3. **Constructor:** 모든 instance variable 초기화
4. **Accessor methods:** 필요한 getter
5. **Mutator methods:** 필요한 setter
6. **기타 메서드:** 스펙에 따라 구현

### 실전 예제

> **문제:** `BookOrder` 클래스를 설계하시오.  
> - 책 제목(title), 수량(quantity), 단가(price)를 가짐  
> - 총 가격을 계산하는 메서드  
> - 수량을 변경하는 메서드  
> - 할인 적용 메서드 (할인율을 받아 단가 조정)

```java
public class BookOrder {
    // Step 1: private instance variables
    private String title;
    private int quantity;
    private double price;

    // Step 2: Constructor — 모든 instance variable 초기화
    public BookOrder(String title, int quantity, double price) {
        this.title = title;
        this.quantity = quantity;
        this.price = price;
    }

    // Step 3: Accessor methods
    public String getTitle() {
        return title;
    }

    public int getQuantity() {
        return quantity;
    }

    public double getPrice() {
        return price;
    }

    // Step 4: Mutator method
    public void setQuantity(int quantity) {
        this.quantity = quantity;
    }

    // Step 5: 비즈니스 로직 메서드
    public double getTotalPrice() {
        return quantity * price;
    }

    /**
     * 할인 적용
     * @param discountRate 0.0 ~ 1.0 사이의 할인율 (예: 0.2 = 20% 할인)
     */
    public void applyDiscount(double discountRate) {
        price = price * (1 - discountRate);
    }
}
```

### FRQ 채점 핵심 (자주 감점되는 부분)

| 실수 | 감점 |
|------|------|
| instance variable을 `public`으로 선언 | -1 |
| constructor에서 일부 변수 초기화 누락 | -1 |
| non-void 메서드에 `return` 누락 | -1 |
| 메서드 시그니처가 스펙과 다름 | -1 |
| `this` 빠뜨려서 shadowing 발생 | -1 |

### 종합 연습 문제

> **문제:** 다음 스펙에 맞는 `Thermostat` 클래스를 완성하시오.

| 메서드 | 설명 |
|--------|------|
| `Thermostat(double temp)` | 현재 온도(currentTemp)와 목표 온도(targetTemp)를 모두 temp로 초기화 |
| `void setTarget(double target)` | 목표 온도 설정 |
| `double getCurrentTemp()` | 현재 온도 반환 |
| `double getTargetTemp()` | 목표 온도 반환 |
| `boolean isHeating()` | 현재 온도 < 목표 온도이면 true |
| `void adjustTemp()` | isHeating()이면 currentTemp를 1.0 증가, 아니면 1.0 감소 |

```java
public class Thermostat {
    private double currentTemp;
    private double targetTemp;

    public Thermostat(double temp) {
        currentTemp = temp;
        targetTemp = temp;
    }

    public void setTarget(double target) {
        targetTemp = target;
    }

    public double getCurrentTemp() {
        return currentTemp;
    }

    public double getTargetTemp() {
        return targetTemp;
    }

    public boolean isHeating() {
        return currentTemp < targetTemp;
    }

    public void adjustTemp() {
        if (isHeating()) {
            currentTemp += 1.0;
        } else {
            currentTemp -= 1.0;
        }
    }
}
```

---

## Quick Reference: Unit 3 핵심 키워드

| 키워드 | 의미 |
|--------|------|
| `public` | 어디서든 접근 가능 |
| `private` | 같은 클래스 내부에서만 |
| `static` | 클래스에 속함 (인스턴스 아님) |
| `final` | 값 변경 불가 (상수) |
| `this` | 현재 객체 자신의 참조 |
| `void` | 반환값 없음 |
| `return` | 값을 반환하고 메서드 종료 |
| `new` | 객체 생성 (constructor 호출) |

---

## FRQ Q2 실전 연습

### 연습 FRQ 1: Library 클래스

다음 명세에 따라 `Library` 클래스를 작성하시오.

- `Library` 객체는 도서관 이름(String)과 총 장서 수(int)를 가진다.
- 생성자는 도서관 이름과 초기 장서 수를 매개변수로 받는다.
- `addBooks(int count)` 메서드는 장서 수를 count만큼 증가시킨다.
- `getInfo()` 메서드는 `"도서관이름 (N권)"` 형태를 반환한다. 예: `"중앙도서관 (5000권)"`

> **⚠️ 2025-26 CED 주의**: 정보 반환 메서드명은 **`toString` 오버라이드 금지** (CED 1.15.A.5 EXCLUSION). 일반 메서드명 (`getInfo`, `getDescription` 등) 사용 필수.

<details>
<summary>모범 답안</summary>

```java
public class Library {
    private String name;
    private int bookCount;
    
    public Library(String name, int bookCount) {
        this.name = name;
        this.bookCount = bookCount;
    }
    
    public void addBooks(int count) {
        bookCount += count;
    }
    
    public String getInfo() {
        return name + " (" + bookCount + "권)";
    }
}
```

**채점 기준 (7점)**:
1. 클래스 헤더 `public class Library` — 1점
2. private instance variables 2개 — 1점
3. 생성자가 매개변수를 올바르게 저장 — 1점
4. addBooks가 bookCount를 올바르게 증가 — 1점
5. getInfo가 올바른 형식의 문자열 반환 — 1점
6. getInfo에서 문자열 연결이 정확 — 1점
7. 전체 알고리즘 정합성 — 1점

> **채점 주의**: `public String toString()` 오버라이드로 작성 시 **CED 1.15.A.5 EXCLUSION 위반**으로 5번/6번 항목 인정 불가. 반드시 일반 메서드명 사용.
</details>

---

## 시험 직전 체크리스트

- [ ] instance variable은 반드시 `private`
- [ ] constructor: `public`, 반환 타입 없음, 클래스 이름과 동일
- [ ] default constructor 기본값: 0, 0.0, false, null
- [ ] primitive 매개변수 = 값 복사, 참조형 매개변수 = 같은 객체
- [ ] 참조형 매개변수에서 상태 변경 → 원본 영향 / 참조 재할당 → 원본 불변
- [ ] static 메서드: instance variable 접근 불가, this 사용 불가
- [ ] local variable: 블록 안에서만 유효, public/private 불가
- [ ] this: shadowing 해결, static에서 사용 불가
- [ ] non-void 메서드: 모든 경로에서 return 필요
- [ ] mutable 객체: 방어적 복사 (constructor, getter 모두)
