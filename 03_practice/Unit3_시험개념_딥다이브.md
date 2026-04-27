# Unit 3 시험 개념 딥다이브
## Class Creation — 모든 시험 출제 개념의 메커니즘

> **Unit 3는 MCQ 비중 10-18%로 가장 작지만 FRQ Q2(Class Design, 7점)가 전부 여기서 나온다.** 즉 실질 기여도는 매우 크다. Class header, instance variable, constructor (default + parameterized), accessor/mutator, pass-by-value-with-reference, defensive copy, `this`, static/instance, scope, `final` — 이 10개 기둥을 **코드로 직접 쓸 수 있게 될 때까지** 파고든다.

---

## 목차

| # | 개념 | 출처 토픽 |
|---|------|---------|
| DD3.1 | 추상화 vs 캡슐화 — 시험 개념으로서의 구분 | 3.1 |
| DD3.2 | Class의 5구성 요소와 작성 순서 | 3.3 |
| DD3.3 | Instance variable — `private` 접근자의 기계적 근거 | 3.3, 3.8 |
| DD3.4 | Constructor — default vs parameterized의 **공존 규칙** | 3.4 |
| DD3.5 | Instance variable **초기화 순서** — 선언 → 생성자 | 3.4 |
| DD3.6 | Default value 규칙 — int/double/boolean/reference | 3.4 |
| DD3.7 | Accessor (getter) — non-void, 반환 타입 규칙 | 3.5 |
| DD3.8 | Mutator (setter) — void, 상태 변경의 기계적 규칙 | 3.5 |
| DD3.9 | **Pass-by-value** — 그런데 왜 객체는 변경되는가 | 3.6 |
| DD3.10 | **Defensive copy** — 왜 생성자/getter에서 필요한가 | 3.4, 3.5 |
| DD3.11 | `this.field = field` — shadowing 해결 메커니즘 | 3.9 |
| DD3.12 | `this`의 세 가지 용법 | 3.9 |
| DD3.13 | Static variable/method — **클래스 레벨** 공유의 메커니즘 | 3.7 |
| DD3.14 | Static method에서 **`this` 사용 불가**의 근거 | 3.7, 3.9 |
| DD3.15 | `final` on primitive vs on reference | 3.7 |
| DD3.16 | Scope 규칙 — instance vs local의 우선순위 | 3.8 |
| DD3.17 | Method **overloading**의 해소 규칙 | 3.5 |
| DD3.18 | 객체 필드를 return할 때의 **캡슐화 구멍** | 3.5, 3.6 |
| DD3.19 | Constructor chain/overloading — `this(...)` 호출 | 3.4 |
| DD3.20 | FRQ Q2 작성 템플릿 — 매년 나오는 형식 |  |

---

## DD3.1 추상화 vs 캡슐화 — 시험 개념으로서의 구분

### 시험 출제 형태
> "다음 설명은 추상화와 캡슐화 중 어느 것인가?"
> (A) 구현의 세부 사항을 숨기고 핵심만 드러낸다 → **추상화**
> (B) 데이터를 private으로 만들고 public 메서드로만 접근하게 한다 → **캡슐화**

### 두 개념의 구분

| 개념 | 초점 | AP CSA 구현 |
|------|-----|----------|
| **Abstraction (추상화)** | 무엇을 하는가 (behavior) | public 메서드 이름·매개변수만 공개, 내부 로직 숨김 |
| **Encapsulation (캡슐화)** | 어떻게 보호하는가 (access control) | `private` 필드 + `public` getter/setter |

### 왜 `private` 필드가 캡슐화의 핵심인가

```java
public class BankAccount {
    public double balance;   // ❌ 외부에서 balance = -999999 강제 대입 가능
}

public class BankAccount {
    private double balance;                        // ✅
    public void deposit(double amt) {
        if (amt > 0) balance += amt;                // 검증 로직 통해서만 변경
    }
}
```

`private`은 "외부에서 직접 변경 못함"을 **문법적으로 강제**. 이게 캡슐화의 메커니즘.

### 시험 판별 경로

- 문제가 "하위 동작을 숨긴다, 인터페이스만 노출" → **추상화**
- 문제가 "private 필드 + 접근자" → **캡슐화**

두 개념은 **상호 보완**이지 대체 관계가 아님. FRQ Q2는 둘 다를 동시에 평가.

---

## DD3.2 Class의 5구성 요소와 작성 순서

### 시험 출제 형태
> FRQ Q2에서 class를 작성할 때 올바른 순서는?

### 필수 5요소 (작성 순서 권장)

```java
public class Dog {                    // ① Class header

    private String name;              // ② Instance variables (필드)
    private int age;                  //    항상 private

    public Dog(String n, int a) {     // ③ Constructor
        this.name = n;
        this.age = a;
    }

    public String getName() {          // ④ Accessor (getter)
        return name;
    }

    public void setAge(int a) {        // ⑤ Mutator (setter)
        this.age = a;
    }
}
```

### 각 요소의 기계적 규칙

| 요소 | 필수 규칙 |
|-----|---------|
| ① Class header | `public class ClassName` — public 필수 (CED 3.3.A.2) |
| ② Fields | `private` 타입 이름; — 항상 private (캡슐화) |
| ③ Constructor | 클래스 이름과 **동일**, 반환 타입 **없음** (void도 아님), `public` |
| ④ Accessor | non-void, `get필드()` 관용 |
| ⑤ Mutator | `void`, `set필드(값)` 관용 |

### 시험 함정 — 생성자 반환 타입

```java
public void Dog(String n) { ... }    // ← 생성자 아님! void 메서드.
                                      //    실제 생성자는 호출되지 않음 (default constructor만 생성됨)
```

`public void Dog(...)`는 Java가 **일반 메서드**로 처리. `new Dog(...)`를 호출해도 default 생성자만 동작하고 이 메서드는 호출 안 됨. 시험의 극단 함정.

---

## DD3.3 Instance variable — `private` 접근자의 기계적 근거

### 시험 출제 형태
> 다음 두 코드 중 캡슐화를 올바르게 적용한 것은?
> ```java
> // (A)
> public class Point {
>     public int x, y;
> }
> 
> // (B)
> public class Point {
>     private int x, y;
>     public int getX() { return x; }
>     public int getY() { return y; }
> }
> ```

### 메커니즘 — `private`의 효력

`private`은 **같은 클래스 내부에서만 접근 가능**. 외부 클래스에서는:

```java
Point p = new Point();
p.x = 5;       // (A)에서는 OK, (B)에서는 컴파일 에러
int v = p.x;   // (A)에서는 OK, (B)에서는 컴파일 에러
```

### 답
(B)가 캡슐화. (A)는 캡슐화 실패.

### 왜 항상 `private`이 정답인가 — FRQ Q2 채점 기준

FRQ Q2 채점 rubric은 "Fields가 `private`으로 선언되었는가"를 **1점 항목**으로 분리해서 본다. 즉:
- `private int x;` → 1점
- `public int x;` 또는 `int x;` (접근 제한자 누락) → 0점

**"항상 private"**을 외운다. 예외 없음.

### 시험 변형

```java
public class Box {
    int width;           // 접근 제한자 없음 = package-private (public도 private도 아님)
}
// → 캡슐화 감점 대상 (FRQ에서)
```

---

## DD3.4 Constructor — default vs parameterized의 공존 규칙

### 시험 출제 형태
> ```java
> public class Cat {
>     private String name;
>     public Cat(String n) { name = n; }
> }
> 
> Cat c1 = new Cat("Tom");    // OK
> Cat c2 = new Cat();         // ???
> ```

### 메커니즘 — default 생성자의 **자동 생성 조건**

> **"사용자 정의 생성자가 하나도 없으면** Java가 default 생성자(매개변수 없는 public 생성자)를 자동 생성한다. **하나라도 있으면 자동 생성하지 않는다**."

위 예에서 `Cat(String n)`이 정의되어 있으므로 default 생성자가 **자동 생성되지 않음** → `new Cat()` 컴파일 에러.

### 해결

매개변수 없는 생성자도 추가로 명시:
```java
public Cat() { }                    // 매개변수 없는 생성자 (default 역할)
public Cat(String n) { name = n; }  // 매개변수 있는 생성자 (overloading)
```

이제 `new Cat()`과 `new Cat("Tom")` 둘 다 OK.

### 시험 단골 함정

학생은 "Java가 자동으로 해주겠지"라고 생각했다가 컴파일 에러에 당황. 규칙은:

```
사용자 정의 생성자 0개 → default 자동 생성
사용자 정의 생성자 1개 이상 → 자동 생성 안 함
```

### FRQ Q2 체크리스트

- [ ] 생성자가 **정확히 요구된 매개변수**를 받는가
- [ ] 모든 인스턴스 변수를 **생성자 내부에서 초기화**하는가
- [ ] 생성자 이름이 클래스 이름과 **정확히 일치**하는가 (대소문자 포함)
- [ ] 반환 타입을 쓰지 않는가 (void도 아님)
- [ ] `public`으로 선언되었는가

---

## DD3.5 Instance variable 초기화 순서 — 선언 → 생성자

### 시험 출제 형태
> ```java
> public class Test {
>     private int x = 10;
>     public Test() {
>         System.out.println(x);   // 10? 0?
>         x = 20;
>     }
> }
> ```

### 메커니즘 — 3단계 초기화 순서

1. **필드 default value 할당** (int=0, double=0.0, boolean=false, reference=null)
2. **필드 선언 시 초기화 식 실행** (`private int x = 10;`이면 10 대입)
3. **생성자 본체 실행**

### 위 예의 트레이스

| 단계 | x 값 |
|-----|-----|
| 1. default | 0 |
| 2. 선언 초기화 `= 10` | 10 |
| 3. 생성자 진입, `println(x)` | 10 출력 |
| 4. `x = 20` | 20 |

출력: **10**.

### 시험 함정 — 생성자가 필드를 명시적으로 초기화하지 않으면?

```java
public class Test {
    private int x;     // 선언만, 초기화 없음
    public Test() { }  // 생성자도 x 건드리지 않음
}

Test t = new Test();
System.out.println(t.getX());   // ?
```

- 단계 1: x = 0 (default)
- 단계 2: 없음
- 단계 3: 생성자 본체 비어있음 → x 건드리지 않음

결과: `x = 0`. 컴파일/런타임 에러 없음 (클래스는 default value를 보장).

### 비교: local variable은 default value **없음**

```java
public void method() {
    int y;
    System.out.println(y);   // 컴파일 에러! (initialize 안 됨)
}
```

**규칙**:
- **Instance variable**: default value 자동 할당
- **Local variable**: 명시적 초기화 필수, 아니면 컴파일 에러

---

## DD3.6 Default value 규칙

### 표 (암기)

| 타입 | Default |
|-----|--------|
| `int` | `0` |
| `double` | `0.0` |
| `boolean` | `false` |
| 참조 타입 (`String`, 배열, 객체) | `null` |
| `char` (AP 범위 밖이지만 알면 좋음) | `' '` (null char) |

### 시험 출제 형태

```java
public class Box {
    private int n;
    private double d;
    private boolean b;
    private String s;
    private int[] arr;
}

Box box = new Box();
System.out.println(box.getN());   // 0
System.out.println(box.getD());   // 0.0
System.out.println(box.getB());   // false
System.out.println(box.getS());   // null
System.out.println(box.getArr()); // null
```

### 참고: 배열 생성 시

```java
int[] arr = new int[3];      // {0, 0, 0}
String[] names = new String[3]; // {null, null, null}
```

배열 요소도 **배열이 생성되는 순간** 각 타입의 default value로 채워진다 → Unit 4에서 심화.

### 시험 함정 — null reference 사용 시도

```java
String[] names = new String[3];
System.out.println(names[0].length());   // NPE!
```

각 원소가 `null`이므로 `null.length()` → NullPointerException.

---

## DD3.7 Accessor (getter) — non-void, 반환 타입 규칙

### 표준 작성 형식

```java
public <반환타입> get필드() {
    return <필드>;
}
```

### 규칙

- **반환 타입**: 필드의 타입과 동일 (예: `private int x;` → `getX()`의 반환 타입 `int`)
- **매개변수**: **없음**
- **이름**: 관용적으로 `get + 필드명` (첫 글자 대문자)
- **void 안 됨**: accessor는 값을 반환하므로 void는 accessor 아님

### 시험 함정

```java
public class Dog {
    private String name;
    
    public void getName() { ... }    // ❌ void는 getter 아님
    public String name() { ... }     // getter 역할이지만 get 관용 위배 — FRQ 채점에서 이름으로 감점
    public String getName() { return name; }  // ✅
}
```

### boolean 필드의 관용

```java
private boolean active;

public boolean isActive() { return active; }   // is+필드명 관용
// 또는
public boolean getActive() { return active; }  // get+필드명도 허용
```

AP FRQ는 둘 다 인정. 하지만 "is..." 패턴이 더 일반적.

### 시험 변형

```java
private int[] scores;

public int[] getScores() { return scores; }   // ← 캡슐화 구멍! DD3.18 참조
```

배열/ArrayList 같은 **가변 참조**를 그대로 반환하면 외부에서 내부를 변경할 수 있어 캡슐화가 깨진다.

---

## DD3.8 Mutator (setter) — void, 상태 변경의 기계적 규칙

### 표준 작성 형식

```java
public void set필드(<필드타입> <매개변수>) {
    this.필드 = 매개변수;
}
```

### 규칙

- **반환 타입**: **void**
- **매개변수**: 필드 타입과 동일한 1개
- **이름**: `set + 필드명`
- 내부에서 `this.필드 = 매개변수` (shadowing 해결)

### 검증이 있는 mutator

```java
public void setAge(int age) {
    if (age >= 0) {
        this.age = age;
    }
    // 또는 예외 처리 (AP 범위 밖)
}
```

FRQ는 보통 **검증 로직 포함**을 요구한다. 예: "age는 0 이상이어야 한다"라는 precondition.

### 시험 함정 — return 타입 혼동

```java
public int setAge(int age) { ... }   // ← int 반환이라 setter 관용 위배
public void setAge(int age) { ... }  // ✅
```

### 시험 변형 — chain setter (AP 범위 밖이지만 이해에 도움)

```java
public Dog setAge(int age) {
    this.age = age;
    return this;   // 자기 자신 반환
}

// 체이닝: dog.setAge(3).setName("Max").setColor("brown");
```

FRQ에서는 단순 void 형태만 요구. chain은 알면 덤.

---

## DD3.9 Pass-by-value — 그런데 왜 객체는 변경되는가

### 시험 출제 형태
> ```java
> public static void changeIt(int[] a) {
>     a[0] = 999;
> }
> 
> int[] arr = {1, 2, 3};
> changeIt(arr);
> System.out.println(arr[0]);  // ?
> ```
> → **999**. 왜?

### 메커니즘 — Java는 **항상 pass-by-value**

Java는 **모든 매개변수를 값으로 전달**한다. 예외 없음. 그런데 "값"의 의미가 타입에 따라 다름:

- **Primitive**: 값 자체(숫자)가 복사됨
- **Reference**: **주소값**이 복사됨 (객체 자체는 복사 안 됨)

### 위 예의 동작

```
원래 arr      [arr | 주소#1000] → 힙: {1, 2, 3}
changeIt 호출 시
  → 매개변수 a = 주소#1000 복사
  → [a | 주소#1000] → 힙: 같은 객체
  → a[0] = 999  // 주소#1000의 객체 수정
  → 힙: {999, 2, 3}
호출 후 arr의 주소#1000 여전히 같은 객체 가리킴
  → arr[0] = 999
```

`a`와 `arr`은 **같은 객체를 가리키는** 두 개의 참조. `a`를 통한 변경이 힙 객체를 바꾸므로 `arr`을 통해 봐도 변경된 결과.

### 왜 "pass-by-reference"가 아닌가

만약 Java가 진짜 pass-by-reference라면:

```java
public static void reassign(int[] a) {
    a = new int[]{7, 8, 9};   // a에 새 배열 대입
}

int[] arr = {1, 2, 3};
reassign(arr);
System.out.println(arr[0]);  // 1? 7?
```

결과는 **1**. `a`에 새 주소를 대입해도 `arr`은 그대로. 왜냐하면 `a`는 `arr`의 **주소의 복사본**이라, `a`가 다른 주소를 가리키게 바뀌어도 `arr`은 원래 주소 그대로.

### 정리 — FRQ 출제 관점

| 메서드가 하는 일 | 호출자에게 보이는 결과 |
|---------------|-------------------|
| 매개변수 자체 재대입 (`a = ...`) | **반영 안 됨** |
| 매개변수가 가리키는 객체 내부 변경 (`a[0] = ...`, `a.setX(...)`) | **반영됨** |

### 시험 변형 — 객체 교체

```java
public static void swap(Dog a, Dog b) {
    Dog temp = a;
    a = b;
    b = temp;
}

Dog x = new Dog("X");
Dog y = new Dog("Y");
swap(x, y);
System.out.println(x.getName());  // "X" or "Y"?
```

**"X"**. 매개변수 a,b의 값만 바뀌고, 호출자의 x,y는 그대로.

---

## DD3.10 Defensive copy — 왜 생성자/getter에서 필요한가

### 시험 출제 형태
> ```java
> public class TeamRoster {
>     private ArrayList<String> players;
>     
>     public TeamRoster(ArrayList<String> players) {
>         this.players = players;   // ← 캡슐화 구멍!
>     }
> }
> 
> ArrayList<String> list = new ArrayList<>();
> list.add("A");
> TeamRoster team = new TeamRoster(list);
> list.add("B");            // 외부에서 list에 추가
> // team 내부 players에도 "B"가 들어가 있다!
> ```

### 메커니즘 — 참조 공유가 캡슐화를 깨는 원리

`this.players = players;`는 **주소 복사**. 즉 외부 `list`와 클래스 내부 `this.players`가 같은 ArrayList 객체를 가리킨다. 외부가 `list`를 수정하면 내부도 바뀐다.

### 해결 — Defensive copy

```java
public TeamRoster(ArrayList<String> players) {
    this.players = new ArrayList<>(players);   // 새 ArrayList 생성, 요소 복사
}
```

이제 외부의 `list` 변경이 내부 `this.players`에 영향 없음.

### CED 3.4.A.3 — 공식 규칙

> "가변(mutable) 객체 매개변수는 방어적 복사로 instance variable을 초기화한다."

FRQ Q2에서 ArrayList나 배열을 매개변수로 받는 생성자가 나오면 **반드시 방어적 복사**를 해야 만점.

### Getter도 동일한 위험

```java
public ArrayList<String> getPlayers() {
    return players;   // ← 외부가 list.add()로 내부 수정 가능!
}
```

방어적 복사 getter:
```java
public ArrayList<String> getPlayers() {
    return new ArrayList<>(players);
}
```

### 배열 버전

```java
// 생성자
public TeamRoster(int[] scores) {
    this.scores = new int[scores.length];
    for (int i = 0; i < scores.length; i++) {
        this.scores[i] = scores[i];
    }
}

// 또는 더 간결히 (AP 범위의 관용)
public TeamRoster(int[] scores) {
    this.scores = new int[scores.length];
    for (int i = 0; i < scores.length; i++) this.scores[i] = scores[i];
}
```

### 언제 방어적 복사 불필요?

**immutable 타입**(primitive, String)은 방어적 복사 불필요:
```java
public class Person {
    private int age;       // primitive — 복사 필요 없음
    private String name;   // immutable — 복사 필요 없음
    
    public Person(int age, String name) {
        this.age = age;          // OK
        this.name = name;        // OK (String은 immutable)
    }
}
```

mutable 타입(`ArrayList`, 배열, 사용자 정의 가변 객체)만 방어적 복사.

### 왜 immutable이면 방어적 복사가 불필요한가 — DD1.16과의 연결

**핵심 원리**: immutable 객체는 "한 번 생성되면 내부 상태를 바꿀 방법이 없다." 

`String name`을 `this.name = name;`으로 참조 공유해도:
- 외부가 `name = "X"` 해도 → **새 String 객체를 가리킬 뿐**, 기존 객체(=내부 참조 대상)는 불변
- 외부가 `name.substring(...)` 해도 → 새 객체 반환, 기존 객체 무영향
- **어떤 메서드 호출로도 기존 String 내부 문자는 바뀌지 않음** (DD1.16)

즉 "외부와 내부가 같은 객체를 공유"해도 **외부가 그 객체를 변경할 수단이 없기 때문**에 캡슐화가 깨지지 않는다.

### 판별 알고리즘 — "방어적 복사 필요?"

```
Q1. 매개변수 타입이 primitive(int, double, boolean)인가?
    YES → 복사 불필요 (primitive는 항상 값 복사)
    NO → Q2로

Q2. 매개변수 타입이 immutable 클래스인가?
    (AP CSA 범위: String, Integer, Double만 immutable로 간주)
    YES → 복사 불필요
    NO → Q3로

Q3. mutable reference (ArrayList, 배열, 사용자 정의 가변 객체)인가?
    YES → 방어적 복사 필요 (생성자에서 새 객체 생성)
```

### 시험 핵심 판별표

| 매개변수 타입 | 방어적 복사 | 이유 |
|-----------|---------|-----|
| `int`, `double`, `boolean` | ❌ 불요 | primitive — 값 복사 |
| `String` | ❌ 불요 | **immutable** (DD1.16) |
| `Integer`, `Double`, `Boolean` | ❌ 불요 | wrapper도 immutable |
| `int[]`, `String[]` 등 배열 | ✅ **필요** | 배열은 항상 mutable |
| `ArrayList<String>` | ✅ **필요** | ArrayList는 mutable (원소가 String이어도 리스트 자체는 변경 가능) |
| 사용자 정의 클래스 (setter 있음) | ✅ **필요** | setter로 변경 가능 → mutable |
| 사용자 정의 클래스 (setter 없음, 모든 필드 final) | ❌ 불요 | 사실상 immutable |

**한 문장 기억법**: **"외부가 내용 변경할 수단이 있으면 방어적 복사"**. 원시·String만 예외(변경 수단 없음).

### FRQ Q2 채점 연결 (DD3.20 참조)

FRQ Q2에서 `ArrayList`나 배열 매개변수를 **받는 생성자**가 나오면 **방어적 복사**가 별도 1점 채점 기준. 이 1점을 놓치지 않으려면 위 판별표를 즉답할 수 있어야 함.

---

## DD3.11 `this.field = field` — shadowing 해결 메커니즘

### 시험 출제 형태
> ```java
> public class Point {
>     private int x;
>     public Point(int x) {
>         x = x;           // ← 무엇이 일어나는가?
>     }
> }
> ```

### 메커니즘 — Scope 해결 규칙

scope 내에 같은 이름의 변수가 둘 있으면 **더 안쪽(local) scope의 것이 우선**. 위 예에서:

- 매개변수 `x` (local scope)
- 필드 `x` (instance scope)

→ 생성자 내부에서 `x`는 **매개변수**를 가리킨다 (필드는 **shadowing됨**).

`x = x;`는 "매개변수 x에 매개변수 x를 대입" = **아무 일도 안 함**. 필드 x는 여전히 default value 0.

### 해결 — `this.` 접두사로 필드 지시

```java
public Point(int x) {
    this.x = x;   // 왼쪽: 필드 x (this.), 오른쪽: 매개변수 x
}
```

`this`는 "현재 객체" 참조. `this.x`는 "현재 객체의 필드 x" = 인스턴스 변수.

### 시험 함정 — `this` 생략 가능성

Shadowing이 **없을 때**는 `this.`를 생략해도 된다:

```java
public Point(int value) {     // 매개변수 이름이 필드와 다름
    x = value;                 // shadowing 없음, this.x와 동일
}
```

하지만 **shadowing이 있을 때**는 반드시 `this.` 필요.

### FRQ Q2의 관용

매개변수 이름을 **필드와 같게** 짓고 `this.필드 = 필드;` 패턴을 쓰는 것이 **관용**이자 **명확**하다:

```java
public Point(int x, int y) {
    this.x = x;
    this.y = y;
}
```

채점자 관점에서 읽기 좋음. 매개변수 이름을 바꾸면 (`int newX`) 어색함.

### FRQ 안전 규칙 — `this.` 쓰는 게 거의 항상 맞다

이론상 shadowing이 없으면 `this.`는 생략 가능(DD3.11). 하지만 **FRQ 답안에서는 다음 원칙**을 따르는 게 안전:

| 상황 | 권장 |
|-----|-----|
| 생성자 안에서 필드 대입 | **항상 `this.x = x;`** (shadowing 여부 무관) |
| 메서드 안에서 필드 읽기 | `this.x` 또는 `x` 어느 쪽이든 OK, `this.x`가 더 명확 |
| 메서드 안에서 필드 쓰기 | `this.x = ...` 권장 (local 변수와 혼동 방지) |
| static 메서드 안 | **`this` 금지** (DD3.14) |

**이유**:
1. 채점자가 코드를 빠르게 읽을 때 `this.`가 "이건 필드"임을 즉시 알려줌
2. 나중에 매개변수 이름을 바꿔서 shadowing이 생겨도 이미 `this.`가 있으면 버그 없음
3. 일관된 스타일 → 감점 위험 제로

### 매개변수 이름을 다르게 지었을 때

```java
public class Point {
    private int x, y;
    
    // shadowing 없음: 매개변수 이름이 필드와 다름
    public Point(int newX, int newY) {
        x = newX;           // OK, this.x = newX와 동일
        y = newY;           // OK
    }
}
```

이 코드도 정답. 단 **FRQ 지문이 매개변수 이름을 지정**하면 그대로 써야 한다. 지문이 "생성자는 매개변수 `int x, int y`를 받는다"고 명시하면 shadowing 상황 → `this.` 필수.

### 시험 채점 실수 방지 — 한 줄 규칙

> **"필드에 대입하는 코드에는 항상 `this.`를 써라."**

이 한 규칙만 따르면 생성자·setter·일반 메서드 어디서든 안전. 암기 부담 최소 + 감점 위험 0.

---

## DD3.12 `this`의 세 가지 용법

### 1. Shadowing 해결 (DD3.11)

```java
public void setX(int x) {
    this.x = x;
}
```

### 2. 자신을 다른 객체에 전달

```java
public class Circle {
    public void addToList(ArrayList<Circle> list) {
        list.add(this);   // 현재 객체를 리스트에 추가
    }
}
```

### 3. 자기 자신의 메서드 호출 (생략 가능)

```java
public class Rectangle {
    private int width, height;
    
    public int getArea() {
        return this.width * this.height;   // this. 생략 가능
        // return width * height;          // 동일
    }
    
    public int getPerimeter() {
        return 2 * (getArea() / getHeight());  // this.getHeight()도 가능
    }
}
```

### 핵심 규칙

> "**`this`는 현재 인스턴스를 가리키는 참조**. instance 메서드와 생성자 안에서만 존재. **static 메서드에는 없음** (DD3.14)."

---

## DD3.13 Static variable/method — 클래스 레벨 공유의 메커니즘

### 시험 출제 형태
> ```java
> public class Counter {
>     private static int count = 0;
>     public Counter() { count++; }
> }
> 
> Counter a = new Counter();
> Counter b = new Counter();
> Counter c = new Counter();
> System.out.println(Counter.???);   // 3
> ```

### 메커니즘 — static은 **클래스가 공유**

| 종류 | 저장 위치 | 공유 범위 |
|-----|---------|--------|
| instance variable | 각 인스턴스에 개별 저장 | 각 객체마다 별도 |
| **static variable** | **클래스 자체에 한 번만** 저장 | 모든 인스턴스 공유 |

위 예에서 `count`는 static → 객체 a, b, c가 **같은 count 하나**를 공유.

### 접근 방법

```java
Counter.count         // 클래스 이름으로 접근 (권장)
a.count               // 인스턴스로도 접근 가능 (비권장, 혼동 유발)
```

AP FRQ는 **클래스 이름으로 접근**하는 것을 맞다고 본다.

### Static method도 동일

```java
public class Counter {
    private static int count = 0;
    public static int getCount() { return count; }   // static method
    public static void reset() { count = 0; }
}

int n = Counter.getCount();
Counter.reset();
```

### Instance method가 static field를 쓸 수 있나?

**YES**. Instance method는 instance field와 static field 둘 다 접근 가능.

### Static method가 instance field를 쓸 수 있나?

**NO**. Static method는 어떤 인스턴스인지 모르므로 instance field에 접근 불가 → 컴파일 에러.

```java
public class Test {
    private int x;           // instance
    private static int y;    // static
    
    public static void foo() {
        y = 1;               // OK
        x = 1;               // 컴파일 에러
    }
}
```

### 대표 용례 — 이미 써온 Math·Integer·Double은 전부 static의 실전

Unit 1부터 써 온 관용 호출들이 모두 **static의 완벽한 예시**다. 여기서 패턴을 체화하면 "왜 `Math.sqrt`는 객체 생성 없이 호출되는가"가 이해된다.

| 호출 관용 | 어디의 static인가 | DD 참조 |
|---------|----------------|--------|
| `Math.abs(x)` | `Math.abs` — Math 클래스의 static method | DD1.12 |
| `Math.pow(a, b)` | 동일 | DD1.12 |
| `Math.sqrt(x)` | 동일 | DD1.12 |
| `Math.random()` | 동일 | DD1.13 |
| `Integer.parseInt("42")` | `Integer.parseInt` — Integer 클래스의 static method | DD4.10 |
| `Double.parseDouble("3.14")` | 동일 | DD4.10 |
| `Integer.MAX_VALUE` | `Integer.MAX_VALUE` — **static variable (상수)** | DD1.9, DD4.10 |
| `Integer.MIN_VALUE` | 동일 | DD4.10 |

### 왜 이들이 static이어야 하는가

- **Math**: 수학 함수는 "특정 객체의 상태와 무관". 어떤 Math 객체를 만들든 `sqrt(16)`은 항상 4.0. 상태 없는 순수 계산 → 인스턴스 불필요 → static.
- **parseInt/parseDouble**: 문자열 → 숫자 변환도 상태 없음. 어떤 Integer 인스턴스에 호출해도 같은 결과. → static.
- **MAX_VALUE/MIN_VALUE**: int의 한계값은 **프로그램 전체에서 단 하나의 상수**. 인스턴스마다 다를 이유 없음. → static variable (`public static final`).

### 정리 — static 판별 기준

> **"객체의 개별 상태와 무관한 기능은 static"**.

반대로, 객체마다 다른 상태(name, balance 등)를 다루는 기능은 **instance method**. 이 구분이 Unit 3 FRQ Q2 작성 시 "이 메서드를 static으로 해야 하나?" 판단 기준.

### FRQ Q2에서는 — 거의 모두 instance

FRQ Q2의 클래스는 보통 "상태를 가진 객체" (Book, Account, Player 등). 따라서 생성자·accessor·mutator·일반 메서드 모두 **instance**. static은 거의 쓰이지 않음. 만약 지문이 "객체 수를 세는 counter"를 요구하면 그때 static variable 등장.

---

## DD3.14 Static method에서 `this` 사용 불가의 근거

### 시험 출제 형태
> ```java
> public class Foo {
>     public static void bar() {
>         System.out.println(this);   // 컴파일 에러
>     }
> }
> ```

### 메커니즘 — `this`가 무엇을 가리키겠는가?

`this`는 "현재 인스턴스". 그런데 static method는 **인스턴스 없이** 호출된다 (`ClassName.method()`). 그러므로 "현재 인스턴스"가 존재하지 않음. `this`가 **가리킬 게 없음** → Java는 컴파일 에러로 차단.

```java
Foo.bar();                    // 이 호출 시 어떤 인스턴스?
// "어떤 Foo 인스턴스인지" 정보가 없음 → this 불가
```

### 체크

- Instance method 안: `this` **OK**
- Constructor 안: `this` **OK** (생성 중인 인스턴스)
- Static method 안: `this` **불가** (컴파일 에러)

### 시험 함정 — static method에서 instance field 접근

```java
public class Counter {
    private int x;                        // instance
    public static void set(int v) {
        x = v;                            // 컴파일 에러! (this.x와 동일, this 없음)
    }
}
```

"왜 컴파일 에러?" → `x`는 `this.x`의 생략. static에는 `this`가 없으므로 `this.x`도 불가.

---

## DD3.15 `final` on primitive vs on reference

### 시험 출제 형태
> ```java
> final int x = 5;
> x = 10;                    // (A)
> 
> final int[] arr = {1, 2, 3};
> arr[0] = 999;              // (B)
> arr = new int[]{9, 8, 7};  // (C)
> ```
> 컴파일 되는 것은? → **(B)만**

### 메커니즘 — `final`은 **변수의 바인딩**을 고정

`final`은 "이 변수에 새 값을 재대입할 수 없다"는 의미.

- **primitive의 경우**: 값 자체가 고정 → (A) 에러
- **reference의 경우**: **가리키는 주소가 고정**. 하지만 **객체 내부는 바꿀 수 있음** → (B) OK (주소 같음, 내용만 변경), (C) 에러 (주소 바꾸려 함)

### 시각 모델

```
final int[] arr = {1, 2, 3};
                     ┌─────────────┐
[arr | 주소#1000] → [힙: 1, 2, 3]   ← arr[0] = 999 하면 힙의 내용은 바뀜
                     └─────────────┘
arr = new...         ← 새 주소로 바꾸려 하면 final이 차단
```

### 시험 함정

학생은 "final이니까 절대 못 바꾼다"고 생각. 배열·ArrayList 내부는 변경 가능. `final`이 막는 건 **재대입**뿐.

### 상수 관용

```java
public static final double PI = 3.14159;   // 클래스 상수 (보통 UPPER_CASE)
```

`public static final`의 결합은 "모든 인스턴스가 공유하는 불변 값" = **상수**. AP CSA에서는 FRQ에서 이 패턴을 만날 수 있다.

### 왜 항상 UPPER_CASE?

Java 컨벤션. 상수는 전통적으로 대문자와 언더스코어로 쓴다: `MAX_SIZE`, `DEFAULT_NAME`.

---

## DD3.16 Scope 규칙 — instance vs local의 우선순위

### 시험 출제 형태
> ```java
> public class Test {
>     private int x = 10;
>     public void foo() {
>         int x = 5;
>         System.out.println(x);    // ?
>         System.out.println(this.x); // ?
>     }
> }
> ```

### Scope 우선순위

가장 안쪽 scope의 변수가 우선. 우선순위:
1. 가장 안쪽 블록(`{ ... }`) local variable
2. 메서드 매개변수
3. Instance variable (this.)
4. Static variable

### 위 예 분석

- `System.out.println(x)` → local `x = 5` 출력
- `System.out.println(this.x)` → instance `x = 10` 출력

### 블록 scope

```java
public void method() {
    int x = 10;
    for (int i = 0; i < 5; i++) {
        int x = 20;        // 컴파일 에러! (바깥 x와 충돌)
    }
}
```

Java는 메서드 내에서 같은 이름 local variable을 **중복 선언 못하게** 막는다. 하지만 instance variable과 local은 가능 (다른 scope).

### 블록 다른 경우

```java
public void method() {
    for (int i = 0; i < 5; i++) {
        int x = i;   // 각 반복마다 새 x
    }
    for (int i = 0; i < 3; i++) {
        int x = i * 2;   // 이건 OK (이전 for와 별개)
    }
}
```

같은 이름을 다른 블록에서는 쓸 수 있음.

### 시험 함정 — shadowing

```java
public class Box {
    private int value;
    public void set(int value) {
        value = value;       // local에 local 대입 — 필드 안 바뀜!
    }
}
```

이 setter는 아무 일도 안 한다. 필드를 바꾸려면 `this.value = value;`.

---

## DD3.17 Method overloading의 해소 규칙

### 시험 출제 형태
> ```java
> public class Printer {
>     public void print(int x) { System.out.println("int"); }
>     public void print(double x) { System.out.println("double"); }
> }
> 
> Printer p = new Printer();
> p.print(5);       // ?
> p.print(5.0);     // ?
> ```

### 메커니즘 — **인자의 타입에 맞는 메서드를 정적으로 선택**

Java 컴파일러는 호출 시점에 **인자의 컴파일 타임 타입**을 보고 어느 오버로드를 부를지 결정한다.

- `p.print(5)`: int 인자 → `print(int)` → "int"
- `p.print(5.0)`: double 인자 → `print(double)` → "double"

### 시험 함정 — 암묵적 타입 확장

```java
public class Printer {
    public void print(double x) { System.out.println("double"); }
    // int 버전 없음
}

Printer p = new Printer();
p.print(5);   // ?
```

int → double 자동 확장 가능. `print(double)`이 호출됨. 출력 "double".

만약 `long` 버전과 `double` 버전이 둘 다 있다면? (AP 범위 밖이지만 원리만) Java는 "가장 덜 손실되는 변환"을 택한다.

### 시그니처 구분 규칙 (DD1.20 복습)

시그니처는 **이름 + 매개변수 타입 목록**. 반환 타입은 무관.

```java
void print(int x) {...}
int print(int x) {...}    // 중복 정의 에러 — 같은 시그니처
```

---

## DD3.18 객체 필드를 return할 때의 캡슐화 구멍

### 시험 출제 형태
> 다음 클래스의 캡슐화 결함은?
> ```java
> public class Roster {
>     private ArrayList<String> names;
>     
>     public ArrayList<String> getNames() {
>         return names;
>     }
> }
> ```

### 메커니즘 — 참조 반환으로 인한 내부 노출

```java
Roster r = new Roster();
ArrayList<String> list = r.getNames();
list.add("hacker");       // ← 외부에서 r 내부 ArrayList 수정 가능!
```

getter가 참조 자체를 반환했기 때문에 외부와 내부가 같은 객체를 공유. 외부의 `list.add()`가 내부 `names`에도 반영.

### 해결 1 — 방어적 복사

```java
public ArrayList<String> getNames() {
    return new ArrayList<>(names);
}
```

### 해결 2 — 불변 view 반환 (AP 범위 밖, FYI)

`Collections.unmodifiableList(names)` — 이 건 AP CSA 답안으로는 쓰지 않는다.

### 해결 3 — 필요한 연산만 메서드로 제공

```java
public int getNameCount() { return names.size(); }
public String getNameAt(int i) { return names.get(i); }
```

String은 immutable이라 `get(i)`로 반환해도 캡슐화 문제 없음. ArrayList 자체를 주지 않는 방식.

### primitive 반환은 안전

```java
public int getX() { return x; }   // int는 값 복사 → 캡슐화 OK
public String getName() { return name; }  // String immutable → 안전
```

### 시험 판별

- 반환 타입이 **primitive 또는 immutable** (String) → 안전
- 반환 타입이 **가변 참조** (ArrayList, 배열, 사용자 정의 mutable 객체) → 방어적 복사 필요

---

## DD3.19 Constructor chain/overloading — `this(...)` 호출

### Constructor overloading

```java
public class Point {
    private int x, y;
    
    public Point() {
        this.x = 0;
        this.y = 0;
    }
    
    public Point(int x) {
        this.x = x;
        this.y = 0;
    }
    
    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```

세 개의 생성자가 오버로딩 (시그니처 다름). 호출:
```java
new Point();           // 첫 번째
new Point(5);          // 두 번째
new Point(5, 3);       // 세 번째
```

### Constructor chaining — `this(...)` (AP 범위 경계)

```java
public Point() {
    this(0, 0);                 // 다른 생성자 호출
}
public Point(int x) {
    this(x, 0);
}
public Point(int x, int y) {
    this.x = x;
    this.y = y;
}
```

`this(...)`는 같은 클래스의 다른 생성자를 호출. **반드시 생성자 첫 줄에** 와야 한다.

CED는 `this(...)` 호출을 명시적으로 다루지는 않지만 **EXCLUSION도 아님** → 시험 답안에서 써도 감점 없음. 단, FRQ에서는 보통 명시적 초기화가 더 명확해서 선호됨.

---

## DD3.20 FRQ Q2 작성 템플릿 — 매년 나오는 형식

### FRQ Q2 형식

문제는 **Complete class**를 작성하라고 지시. 보통:
- 클래스 이름, 필드 목록, 생성자, 특정 메서드들이 지문으로 주어짐
- 학생은 이를 **완전한 Java 코드**로 작성

### 표준 템플릿

```java
public class ClassName {
    private Type1 field1;
    private Type2 field2;
    // ... 모든 필드 private
    
    // 생성자
    public ClassName(Type1 p1, Type2 p2) {
        this.field1 = p1;
        this.field2 = p2;
        // 방어적 복사가 필요하면 여기서
    }
    
    // Accessor
    public Type1 getField1() {
        return field1;
    }
    
    // Mutator
    public void setField1(Type1 newValue) {
        this.field1 = newValue;
    }
    
    // 문제가 요구하는 추가 메서드
    public ReturnType methodName(ParamType param) {
        // 로직
        return result;
    }
}
```

### 채점 기준 패턴 (7점 기준)

문제마다 다르지만 보통:
1. Class header 올바른가 (`public class ClassName`)
2. Fields가 `private`인가
3. 생성자 signature 맞는가
4. 생성자가 모든 필드 초기화하는가
5. 요구된 메서드 signature 맞는가
6. 메서드 알고리즘 정답인가
7. 엣지 케이스 처리 (빈 배열, null 등)

### 시험 관용구

- **매개변수 이름 = 필드 이름**: `this.` 사용 패턴 확립
- **모든 필드 private, 모든 메서드 public**
- **방어적 복사**: mutable 파라미터 받는 경우 반드시
- **접근자/변경자 이름**: `get`, `set`, `is` 관용

### 체크리스트 (FRQ 제출 직전)

- [ ] `public class` 선언 시작
- [ ] 모든 instance variable `private`
- [ ] 생성자 이름 = 클래스 이름 (대소문자 정확)
- [ ] 생성자 반환 타입 **없음** (void도 아님)
- [ ] 모든 instance variable이 생성자에서 초기화됨
- [ ] mutable 파라미터는 방어적 복사
- [ ] 메서드 signature가 지문과 정확히 일치
- [ ] `this.field = field` 패턴으로 shadowing 해결
- [ ] 요구된 예외 케이스 (빈 배열, null) 처리
- [ ] `toString`, `equals` override 작성 **금지** (EXCLUSION)

---

## 부록 A: Unit 3 FRQ Q2 합격 코드 예시

### 지문 (가상 예)

> `Book` 클래스 작성:
> - private String title
> - private String author
> - private int pages
> - 생성자: `Book(String t, String a, int p)`
> - `public String getTitle()`
> - `public void addPages(int n)`: n ≥ 0이면 pages에 더함
> - `public boolean isLong()`: pages > 300이면 true

### 정답 코드

```java
public class Book {
    private String title;
    private String author;
    private int pages;
    
    public Book(String t, String a, int p) {
        title = t;
        author = a;
        pages = p;
    }
    
    public String getTitle() {
        return title;
    }
    
    public void addPages(int n) {
        if (n >= 0) {
            pages += n;
        }
    }
    
    public boolean isLong() {
        return pages > 300;
    }
}
```

### 채점 체크

- ✅ `public class Book`
- ✅ 모든 필드 `private`
- ✅ 생성자 signature + 초기화
- ✅ getTitle() 올바른 반환 타입
- ✅ addPages() 검증 로직 포함 (`n >= 0`)
- ✅ isLong() boolean 반환, 조건 올바름
- ✅ String은 immutable이라 방어적 복사 불요
- ✅ toString/equals 작성 안 함

---

## 부록 B: Unit 3 시험 빈출 Top 10 유형

1. FRQ Q2 Complete class 작성 (7점) — 매년 출제
2. `this`의 용법 묻기
3. default vs parameterized 생성자 공존
4. Pass-by-value지만 객체 내부 변경되는 트레이싱
5. 방어적 복사 필요 여부 판별
6. `private` vs `public`의 캡슐화 결과
7. static variable 공유 카운팅
8. scope/shadowing 트레이싱
9. `final` on reference (내부 변경 가능)
10. accessor/mutator 관용 구분

---

## 검증 — L1 완료 체크리스트

- [x] CED 토픽 3.1~3.9 중 시험 빈출 개념 20개 메커니즘 수준 설명
- [x] 각 개념: 출제 형태 + 메커니즘 + 변형
- [x] Pass-by-value 이해 — 원리·함정·반례
- [x] Defensive copy의 필요 조건과 해결 코드
- [x] `this`의 3 용법 + static에서 불가 이유
- [x] `final` on primitive vs reference
- [x] Scope 우선순위 + shadowing 해결
- [x] FRQ Q2 작성 템플릿 + 채점 체크리스트
- [x] EXCLUSION 엄수 (toString/equals override 작성 금지, 상속 금지 언급)
