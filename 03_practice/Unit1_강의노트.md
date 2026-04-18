# Unit 1: Using Objects and Methods

> **시험 비중: 15-25% | 약 32-34 수업시간**
>
> 이 강의노트는 AP CSA 공식 교육과정(CED = Course and Exam Description)의 모든 학습 목표를 다룹니다.
> 환경설정 가이드에서 Java 설치와 HelloWorld를 이미 해봤다면, 이제 시험에 필요한 내용을 체계적으로 배웁니다.

---

## 1.1 Introduction to Algorithms, Programming, and Compilers (2기간)

> **쉽게 말해**: 알고리즘은 **라면 끓이는 순서**와 같다. ① 물 끓이기 ② 면 넣기 ③ 스프 넣기 — 순서를 바꾸면 결과가 달라진다. 프로그래밍도 마찬가지로, 컴퓨터에게 "정확한 순서로 할 일"을 알려주는 것이다.

### CED 학습목표
- Skill 1.A: 적절한 프로그램 설계를 선택하고 구현할 수 있다.

### 핵심 개념
- **알고리즘(Algorithm)**: 문제를 해결하기 위한 단계별 절차. 핵심은 **순서(sequencing)** — 명령을 올바른 순서로 나열해야 한다.
- **IDE**: 코드 작성, 컴파일, 실행을 한곳에서 하는 통합 개발 환경
- **컴파일러(Compiler)**: Java 소스코드(.java)를 바이트코드(.class)로 변환. 바이트코드란 컴퓨터가 이해하기 쉽게 "번역된" 코드. 우리가 쓰는 .java 파일은 사람이 읽기 쉬운 형태이고, .class 파일은 컴퓨터가 실행하기 쉬운 형태.

### 에러 유형 (필수 암기!)

| 에러 유형 | 언제 발견? | 예시 |
|-----------|-----------|------|
| **Syntax error** (구문 오류) | 컴파일 시 | 세미콜론 누락, 괄호 불일치 |
| **Logic error** (논리 오류) | 테스트로 발견 | 프로그램은 돌지만 결과가 틀림 |
| **Run-time error** (실행 오류) | 실행 중 종료 | 0으로 나누기, null 접근 |
| **Exception** (예외) | 실행 중 | ArithmeticException 등 |

> **참고**: Exception은 Run-time error의 구체적인 형태입니다. 프로그램 실행 중 문제가 발생하면 Java는 이를 Exception이라는 이름으로 보고하고, 프로그램의 정상적인 흐름을 방해합니다.

### 코드 예제

```java
public class HelloWorld {
    public static void main(String[] args) {
        // 이것은 가장 기본적인 Java 프로그램이다
        System.out.println("Hello, AP CSA!");
    }
}
```

### 시험 출제 포인트
- **Logic error는 컴파일러가 잡지 못한다** — 프로그램이 "정상 실행"되지만 결과가 틀림
- Syntax error vs Run-time error 구분 문제가 자주 출제됨

### 연습 문제

**Q1.** 다음 중 logic error에 해당하는 것은?
- (A) 세미콜론을 빠뜨려서 컴파일이 안 된다
- (B) 평균을 구하려는데 합계를 개수로 나누지 않았다
- (C) 배열 범위를 벗어나서 프로그램이 중단된다
- (D) 변수 이름을 잘못 써서 컴파일이 안 된다

> **정답: (B)** — 프로그램은 실행되지만 결과가 의도와 다르므로 logic error

---

## 1.2 Variables and Data Types (2기간)

### CED 학습목표
- 변수를 선언하고 적절한 데이터 타입을 선택할 수 있다.

### 핵심 개념
- **Data type** = 값의 집합 + 그 값에 적용 가능한 연산. 쉽게 말해 **"이 상자에 어떤 종류의 물건을 넣을 수 있는가"**를 정하는 것.
- **Primitive type** (기본 타입): 값 자체를 직접 저장 (int, double, boolean)
- **Reference type** (참조 타입): 객체가 있는 곳의 주소를 저장 (String, 배열 등 — 나중에 자세히 배움. 지금은 int/double/boolean이 Primitive라는 것만 기억!)

| Primitive Type | 설명 | 예시 |
|---------------|------|------|
| `int` | 정수 | `42`, `-7`, `0` |
| `double` | 실수 (소수점) | `3.14`, `-0.5` |
| `boolean` | 참/거짓 | `true`, `false` |

- **변수(Variable)** = 값을 저장하는 이름 붙은 공간
- Primitive 변수는 **값 자체를 직접 보유**한다 (참조가 아님!)

### 코드 예제

```java
public class VariablesDemo {
    public static void main(String[] args) {
        int age = 17;
        double gpa = 3.85;
        boolean isAPStudent = true;

        System.out.println("나이: " + age);
        System.out.println("GPA: " + gpa);
        System.out.println("AP 학생: " + isAPStudent);
    }
}
```

### 시험 출제 포인트
- `long`, `short`, `byte`, `float`, `char`는 **시험 범위 밖** (EXCLUSION)
- `int`와 `double`의 차이를 정확히 알아야 한다
- Primitive vs Reference 구분은 Unit 전체에 걸쳐 중요

### 연습 문제

**Q1.** 다음 중 올바른 변수 선언은?
- (A) `int 2ndPlace = 5;`
- (B) `double price = 9.99;`
- (C) `boolean = true;`
- (D) `int my age = 20;`

> **정답: (B)** — (A) 숫자로 시작 불가, (C) 변수 이름 없음, (D) 공백 포함 불가

---

## 1.3 Expressions and Output (3기간)

### CED 학습목표
- 산술 표현식을 평가하고 출력문을 사용할 수 있다.

### 핵심 개념

#### 출력
- `System.out.print("hello")` — 줄바꿈 **없이** 출력
- `System.out.println("hello")` — 출력 후 **줄바꿈**

#### 리터럴(Literal)과 Escape Sequence
- **리터럴(Literal)** = 코드에 직접 쓴 고정 값. 예: `42`(int 리터럴), `3.14`(double 리터럴), `true`(boolean 리터럴), `"Hello"`(String 리터럴)
- **문자열 리터럴(String literal)** = `""` 안에 쓴 문자 시퀀스
- `\"` → 쌍따옴표 출력
- `\\` → 역슬래시 출력
- `\n` → 줄바꿈

#### 산술 연산자

| 연산자 | 의미 | 예시 |
|--------|------|------|
| `+` | 덧셈 | `5 + 3` → `8` |
| `-` | 뺄셈 | `5 - 3` → `2` |
| `*` | 곱셈 | `5 * 3` → `15` |
| `/` | 나눗셈 | `5 / 3` → `1` (정수!) |
| `%` | 나머지 | `5 % 3` → `2` |

#### 정수 나눗셈 (가장 중요한 함정!)
- **int / int = int** (소수점 버림!)
- double이 하나라도 포함되면 결과는 double

#### 연산자 우선순위
1. `*`, `/`, `%` (먼저)
2. `+`, `-` (나중)
3. 같은 우선순위면 **왼쪽 → 오른쪽**
4. 괄호 `()`로 변경 가능

### 코드 예제

```java
public class ExpressionsDemo {
    public static void main(String[] args) {
        // 정수 나눗셈 주의!
        System.out.println(7 / 2);      // 출력: 3 (소수점 버림!)
        System.out.println(7.0 / 2);    // 출력: 3.5
        System.out.println(7 / 2.0);    // 출력: 3.5

        // 나머지 연산
        System.out.println(10 % 3);     // 출력: 1
        System.out.println(10 % 5);     // 출력: 0

        // 연산자 우선순위
        System.out.println(2 + 3 * 4);  // 출력: 14 (3*4 먼저)
        System.out.println((2 + 3) * 4); // 출력: 20

        // print vs println
        System.out.print("Hello ");
        System.out.print("World");       // 출력: Hello World (한 줄)
        System.out.println();            // 줄바꿈
        System.out.println("New line");  // 출력: New line

        // Escape sequence
        System.out.println("She said \"Hi\""); // 출력: She said "Hi"
        System.out.println("Line1\nLine2");    // 두 줄로 출력
    }
}
```

### 시험 출제 포인트
- **정수 나눗셈은 AP CSA 최다 출제 함정!** `7 / 2`는 `3`이다. `3.5`가 아니다.
- 정수끼리 0으로 나누면 `ArithmeticException` 발생
- EXCLUSION: 음수의 `%` 연산, `double` 0 나누기, `NaN`/`Infinity`

### 연습 문제

**Q1.** 다음 코드의 출력은?
```java
System.out.println(13 / 5 + 13 % 5);
```
- (A) 2.6
- (B) 5
- (C) 5.6
- (D) 6

> **정답: (B)** — `13 / 5` = `2`, `13 % 5` = `3`, `2 + 3` = `5`

**Q2.** 다음 코드의 출력은?
```java
System.out.print("A");
System.out.println("B");
System.out.print("C");
```
- (A) ABC
- (B) AB 다음 줄에 C
- (C) A 다음 줄에 B 다음 줄에 C
- (D) A 다음 줄에 BC

> **정답: (B)** — `print("A")`는 줄바꿈 없이 A, `println("B")`는 B 출력 후 줄바꿈, `print("C")`는 C

---

## 1.4 Assignment Statements and Input (2기간)

### CED 학습목표
- 대입문을 사용하여 변수에 값을 저장할 수 있다.

### 핵심 개념
- `=`는 "같다"가 아니라 **대입 연산자** (오른쪽 값을 왼쪽 변수에 저장)
- 변수를 사용하기 **전에 반드시 초기화**해야 한다
- **표현식(Expression)의 평가**: 실행 시 표현식은 **단일 값**으로 평가된다. 그 값의 타입은 표현식의 평가에 의해 결정된다. 예: `3 + 4`는 `int` 타입 `7`로, `3 + 4.0`은 `double` 타입 `7.0`으로 평가.
- `null` = 참조 타입 변수가 **어떤 객체도 가리키지 않음**을 의미
- **입력(Input)**: 프로그램에 데이터를 전달하는 방법. 키보드, 파일, 센서 등 다양한 형태. Java에서는 `Scanner` 클래스로 키보드 텍스트 입력을 받을 수 있다 (자세한 사용법은 1.7, 4.6에서 학습).

### 코드 예제

```java
public class AssignmentDemo {
    public static void main(String[] args) {
        int x = 5;       // 선언과 동시에 초기화
        int y;            // 선언만 (초기화 안 됨)
        // System.out.println(y); // 컴파일 에러! 초기화 안 된 변수 사용

        y = 10;           // 초기화
        x = x + 1;       // x는 이제 6 (오른쪽 먼저 계산, 왼쪽에 저장)

        System.out.println(x);  // 출력: 6
        System.out.println(y);  // 출력: 10

        // 값의 교환 (임시 변수 필요!)
        int a = 3, b = 7;
        int temp = a;
        a = b;
        b = temp;
        System.out.println("a=" + a + " b=" + b); // 출력: a=7 b=3

        // null 예시
        String name = null;  // 어떤 객체도 가리키지 않음
        name = "Alice";      // 이제 String 객체를 가리킴
        System.out.println(name); // 출력: Alice
    }
}
```

### 시험 출제 포인트
- `x = x + 1`은 수학적으로는 말이 안 되지만, 프로그래밍에서는 "x의 현재 값에 1을 더해서 x에 다시 저장"
- 값 교환 시 **임시 변수가 필요**하다는 것을 기억
- EXCLUSION: `a = b = 4;` 같은 복합 대입 표현

### 연습 문제

**Q1.** 다음 코드 실행 후 `x`의 값은?
```java
int x = 10;
int y = 20;
x = y;
y = x;
```
- (A) x=20, y=10
- (B) x=20, y=20
- (C) x=10, y=20
- (D) x=10, y=10

> **정답: (B)** — `x = y` 후 x는 20. 그 다음 `y = x`에서 x는 이미 20이므로 y도 20. 값 교환 실패!

### Scanner 기본 사용법 (참고 — 학습 도구만, 시험 출제 안 됨)

> **⚠️ CED 주의 (필독)**: `Scanner(System.in)` 키보드 입력은 **CED 1.4.B.1 EXCLUSION**으로 **2025-26 AP CSA 시험에 출제되지 않습니다**. 시험에서 Scanner는 **`Scanner(new File(...))` 파일 읽기만 출제** (Unit 4.6, CED p.186 Quick Reference 명시). 아래 코드는 객체 생성과 메서드 호출의 **실습 학습용**으로만 보고, **시험 답안에는 절대 사용 금지**.

```java
import java.util.Scanner;

// ⚠️ 학습용 데모 — 시험 답안 작성 시 절대 사용 금지
Scanner sc = new Scanner(System.in);
System.out.print("나이를 입력하세요: ");
int age = sc.nextInt();        // 정수 입력
System.out.print("이름을 입력하세요: ");
sc.nextLine();                  // nextInt() 뒤의 남은 개행 소비
String name = sc.nextLine();   // 문자열 입력
System.out.println(name + "님은 " + age + "세입니다.");
```

> **시험 출제 형태 (4.6)**: `Scanner sc = new Scanner(new File("data.txt"));` 같은 파일 입력만 출제. `nextInt()`, `nextDouble()`, `nextBoolean()`, `nextLine()`, `next()`, `hasNext()`, `close()` 메서드만 IN.

---

## 1.5 Casting and Range of Variables (2기간)

### CED 학습목표
- 형변환(casting)을 사용하고 변수 범위를 이해할 수 있다.

### 핵심 개념
- **(int)** double값 → 소수점 **버림** (반올림이 아님!)
- **(double)** int값 → `.0` 추가
- **자동 형 확장(Widening)**: int 값이 double과 함께 사용되면 자동으로 double로 변환된다 (예: `3 + 2.5` → `3`이 `3.0`으로 자동 변환 후 `5.5`)
- `int` 범위: `Integer.MIN_VALUE` (-2,147,483,648) ~ `Integer.MAX_VALUE` (2,147,483,647)
- **오버플로우(Overflow)**: 범위를 초과하면 예상 밖의 값이 나온다
- **double 정밀도 한계 (Round-off Error)**: double은 메모리에 유한한 비트로 저장되므로 모든 실수를 정확히 표현할 수 없다. 예를 들어 `0.1 + 0.2`는 정확히 `0.3`이 아니라 `0.30000000000000004`가 될 수 있다. 정확한 정수 계산이 필요하면 int를 사용하라.
- **반올림 트릭**: 양수 `(int)(x + 0.5)`, 음수 `(int)(x - 0.5)`

### 코드 예제

```java
public class CastingDemo {
    public static void main(String[] args) {
        // (int) 캐스팅 — 소수점 버림! (반올림 아님)
        System.out.println((int) 3.9);   // 출력: 3 (반올림하면 4이지만, 버림!)
        System.out.println((int) -2.7);  // 출력: -2 (0쪽으로 버림)

        // (double) 캐스팅
        System.out.println((double) 5);  // 출력: 5.0

        // 캐스팅으로 정수 나눗셈 해결
        int a = 7, b = 2;
        System.out.println((double) a / b);  // 출력: 3.5
        System.out.println(a / (double) b);  // 출력: 3.5
        System.out.println((double)(a / b)); // 출력: 3.0 (먼저 정수 나눗셈 후 캐스팅!)

        // int 범위
        System.out.println(Integer.MAX_VALUE);     // 2147483647
        System.out.println(Integer.MAX_VALUE + 1); // -2147483648 (오버플로우!)

        // 반올림 트릭
        double val = 3.7;
        int rounded = (int)(val + 0.5); // 4 (양수일 때 반올림 효과)
        System.out.println(rounded);

        double neg = -3.7;
        int roundedNeg = (int)(neg - 0.5); // -4 (음수일 때 반올림 효과)
        System.out.println(roundedNeg);

        // double 정밀도 한계 (Round-off Error)
        System.out.println(0.1 + 0.2);           // 출력: 0.30000000000000004 (정확히 0.3이 아님!)
        System.out.println(0.1 + 0.2 == 0.3);    // 출력: false (!!)

        // 자동 형 확장 (Widening)
        int i = 5;
        double d = i;  // int → double 자동 변환
        System.out.println(d);  // 출력: 5.0
    }
}
```

### 시험 출제 포인트
- `(int) 3.9`는 **3**이다. 4가 아니다! (가장 많이 틀리는 문제)
- `(double)(a / b)`와 `(double) a / b`는 **결과가 다르다!** 괄호 위치 주의
- 오버플로우 문제: `Integer.MAX_VALUE + 1`은 음수가 된다

### 연습 문제

**Q1.** 다음 코드의 출력은?
```java
int x = 5;
int y = 3;
double result = (double)(x / y);
System.out.println(result);
```
- (A) 1.6666666666666667
- (B) 1.0
- (C) 2.0
- (D) 1.67

> **정답: (B)** — `x / y`가 먼저 정수 나눗셈으로 `1`, 그 후 `(double)` 캐스팅으로 `1.0`

**Q2.** `(int) -4.3`의 결과는?
- (A) -5
- (B) -4
- (C) -3
- (D) 4

> **정답: (B)** — (int) 캐스팅은 0 방향으로 소수점 버림

---

## 1.6 Compound Assignment Operators (1기간)

> **쉽게 말해**: `x += 3`은 "지갑에 3만원을 더 넣는 것"이다. 기존 금액에 더하는 것이지 새로 바꾸는 게 아니다. `x = 3`은 "지갑을 비우고 3만원만 넣는 것"과 같다.

### CED 학습목표
- 복합 대입 연산자와 증감 연산자를 사용할 수 있다.

### 핵심 개념

| 복합 대입 | 동등한 표현 |
|-----------|-----------|
| `x += 3` | `x = x + 3` |
| `x -= 3` | `x = x - 3` |
| `x *= 3` | `x = x * 3` |
| `x /= 3` | `x = x / 3` |
| `x %= 3` | `x = x % 3` |

- `x++` → `x = x + 1` (증가)
- `x--` → `x = x - 1` (감소)

### 코드 예제

```java
public class CompoundAssignDemo {
    public static void main(String[] args) {
        int x = 10;

        x += 5;   // x = 15
        System.out.println(x);

        x -= 3;   // x = 12
        System.out.println(x);

        x *= 2;   // x = 24
        System.out.println(x);

        x /= 5;   // x = 4 (정수 나눗셈!)
        System.out.println(x);

        x %= 3;   // x = 1
        System.out.println(x);

        x++;       // x = 2
        System.out.println(x);

        x--;       // x = 1
        System.out.println(x);
    }
}
```

### 시험 출제 포인트
- `x /= 3`에서 x가 int이면 **정수 나눗셈** 적용
- `++`와 `--`는 AP CSA에서 독립 문장으로만 사용 (전위/후위 차이는 시험 범위 밖)

### 연습 문제

**Q1.** 다음 코드 실행 후 `n`의 값은?
```java
int n = 17;
n /= 5;
n %= 3;
```
- (A) 0
- (B) 1
- (C) 2
- (D) 3

> **정답: (A)** — `17 / 5` = `3` (정수 나눗셈), `3 % 3` = `0`

---

## 1.7 Application Program Interface (API) and Libraries (1기간)

> **쉽게 말해**: API는 **음식점 메뉴판**과 같다. 주방(라이브러리)이 어떻게 요리하는지 몰라도, 메뉴판(API)에서 원하는 것을 골라 주문(호출)할 수 있다. Java Quick Reference는 시험장에서 제공되는 "메뉴판"이다.

### CED 학습목표
- API 문서를 읽고 라이브러리 클래스를 사용할 수 있다.

### 핵심 개념
- **API (Application Program Interface)** = 사용 가능한 클래스와 메서드의 목록 및 사용법
- `import` 문으로 외부 라이브러리의 클래스를 가져온다
- `java.lang` 패키지 (String, Math, System 등)는 import 없이 사용 가능
- API 문서(documentation)를 읽고 메서드의 매개변수, 반환 타입 등을 파악하는 능력이 중요

### 코드 예제

```java
import java.util.Scanner;  // Scanner 클래스를 사용하기 위해 import

public class APIDemo {
    public static void main(String[] args) {
        // java.lang 패키지는 import 필요 없음
        double result = Math.sqrt(16.0);  // Math는 java.lang에 속함
        System.out.println(result);       // 출력: 4.0

        // import가 필요한 클래스 사용 (시험 형태: 파일 입력)
        // Scanner sc = new Scanner(new File("data.txt"));   // ← 시험 출제 형태
        // 학습용 데모: Scanner sc = new Scanner(System.in); ← 시험 출제 안 됨 (CED 1.4 EXCLUSION)
    }
}
```

### 시험 출제 포인트
- AP 시험에서는 Java Quick Reference Sheet가 제공된다 — 이 문서에 있는 메서드를 빠르게 찾는 연습 필수
- `Math`, `String`, `System`은 import 없이 사용 가능 (java.lang)

### 연습 문제

**Q1.** API 문서에 다음과 같은 메서드가 기술되어 있다:
```
public static int abs(int a)
  Returns the absolute value of an int value.
```
다음 중 이 메서드를 올바르게 사용하는 코드는?

- (A) `int result = abs(-5);`
- (B) `int result = Math.abs(-5);`
- (C) `import java.lang.Math; int result = Math.abs(-5);`
- (D) `String result = Math.abs(-5);`

> **정답: (B)** — `abs`는 `Math` 클래스의 static 메서드이므로 `Math.abs()`로 호출해야 한다. (A)는 클래스명 없이 호출하여 오류. (C)는 동작하지만 `java.lang`은 import가 불필요하므로 가장 올바른 사용은 아님. (D)는 반환 타입이 `int`인데 `String`에 저장하려 하여 컴파일 에러.

---

## 1.8 Documentation with Comments (1기간)

### CED 학습목표
- 주석을 사용하여 코드를 문서화하고, precondition/postcondition을 이해할 수 있다.

### 핵심 개념

| 주석 유형 | 문법 | 용도 |
|-----------|------|------|
| 한 줄 주석 | `// 내용` | 간단한 설명 |
| 블록 주석 | `/* 내용 */` | 여러 줄 설명 |
| Javadoc 주석 | `/** 내용 */` | API 문서 생성용 |

- **Precondition** (사전 조건): 메서드 호출 **전에** 충족해야 할 조건
- **Postcondition** (사후 조건): 메서드 실행 **후에** 보장되는 조건

> **비유**: Precondition은 "이 놀이기구는 키 120cm 이상만 탑승 가능"과 같다. 조건을 지키지 않으면 결과를 보장하지 않는다. 코드에서는 이 조건을 직접 검사할 필요 없이, "지켜졌다고 가정하고" 작성한다.

### 코드 예제

```java
public class CommentsDemo {

    /**
     * 두 정수의 최대값을 반환한다.
     * @param a 첫 번째 정수
     * @param b 두 번째 정수
     * @return a와 b 중 큰 값
     *
     * Precondition: 없음 (모든 int 값 허용)
     * Postcondition: 반환값은 a 이상이고 b 이상이다
     */
    public static int max(int a, int b) {
        // 삼항 연산자 대신 if문으로도 가능
        if (a >= b) {
            return a;
        }
        return b;
    }

    public static void main(String[] args) {
        /* 이 프로그램은 max 메서드를 테스트한다.
           여러 줄 주석의 예시이다. */
        System.out.println(max(3, 7));  // 출력: 7
    }
}
```

### 시험 출제 포인트
- FRQ에서 precondition이 주어지면, 그 조건이 참이라고 **가정**하고 코드를 작성한다 (조건 검사 불필요)
- 주석은 실행에 영향을 주지 않는다 — 하지만 시험에서 주석으로 힌트를 줄 때가 있다

### 연습 문제

**Q1.** 다음 메서드의 Javadoc 주석을 보자.
```java
/**
 * 배열에서 target 값의 인덱스를 반환한다.
 * Precondition: arr는 오름차순으로 정렬되어 있다.
 * Postcondition: target이 arr에 없으면 -1을 반환한다.
 */
public int search(int[] arr, int target)
```
이 메서드를 호출할 때 프로그래머가 **반드시** 해야 하는 것은?

- (A) 메서드 내부에서 배열이 정렬되어 있는지 확인하는 코드를 작성한다
- (B) 호출 전에 배열이 오름차순 정렬되어 있도록 보장한다
- (C) 반환값이 -1인 경우를 메서드 내부에서 처리한다
- (D) postcondition을 만족하도록 호출 전에 검사한다

> **정답: (B)** — Precondition은 메서드 **호출자**가 보장해야 할 조건이다. 배열이 정렬되어 있다는 것은 사전 조건이므로, 호출 전에 정렬을 보장해야 한다. Postcondition은 메서드가 보장하는 것이지 호출자가 처리할 사항이 아니다.

---

## 1.9 Method Signatures (1기간)

### CED 학습목표
- 메서드 시그니처를 읽고 해석할 수 있다.

### 핵심 개념
- **메서드 시그니처(Method Signature)** = **메서드 이름** + **매개변수 목록** (타입과 순서)
- 반환 타입은 시그니처에 **포함되지 않음** (but 메서드 헤더에는 포함)
- 메서드 헤더 = 접근제한자 + (static) + 반환타입 + 메서드이름 + 매개변수목록

```
메서드 헤더:   public static double average(int a, int b)
                ^^^^^^ ^^^^^^ ^^^^^^ ^^^^^^^^^^^^^^^^^^^^^^^
                접근    static 반환타입  메서드 시그니처
                제한자                  (이름 + 매개변수)
```

### 코드 예제

```java
public class MethodSignatureDemo {

    // 메서드 시그니처: add(int, int)
    // 반환 타입 int는 시그니처에 포함되지 않음
    public static int add(int a, int b) {
        return a + b;
    }

    // 메서드 시그니처: add(double, double)
    // 같은 이름이지만 매개변수 타입이 다르므로 다른 시그니처 (오버로딩)
    public static double add(double a, double b) {
        return a + b;
    }

    public static void main(String[] args) {
        System.out.println(add(3, 4));       // 출력: 7 (int 버전 호출)
        System.out.println(add(3.0, 4.0));   // 출력: 7.0 (double 버전 호출)
    }
}
```

### 시험 출제 포인트
- "메서드 시그니처"라고 하면 반환 타입은 **빠진다**
- 오버로딩(Overloading): 같은 이름, 다른 매개변수 목록 → 서로 다른 메서드

### 연습 문제

**Q1.** 다음 메서드의 시그니처는?
```java
public static boolean isEven(int number)
```
- (A) `public static boolean isEven(int number)`
- (B) `boolean isEven(int)`
- (C) `isEven(int)`
- (D) `isEven(int number)`

> **정답: (C)** — 시그니처는 메서드 이름 + 매개변수 타입 목록만 포함

#### parameter(매개변수) vs argument(인수) 구분

| 용어 | 위치 | 예시 |
|------|------|------|
| **parameter** (매개변수, formal parameter) | 메서드 **정의**할 때 | `public int add(int a, int b)` 에서 `a`, `b` |
| **argument** (인수, actual parameter) | 메서드 **호출**할 때 | `add(3, 5)` 에서 `3`, `5` |

> 쉽게: parameter = 빈 칸, argument = 빈 칸에 넣는 실제 값

---

## 1.10 Calling Class Methods (3기간)

### CED 학습목표
- static 메서드(클래스 메서드)를 호출할 수 있다.

### 핵심 개념
- **Static 메서드** = 객체 없이 **클래스 이름으로 직접 호출**하는 메서드
- 호출 방법: `ClassName.methodName(arguments)`
- **`Math.random()`**: `0.0` 이상 `1.0` 미만의 랜덤 double 반환
- 랜덤 정수 공식: `(int)(Math.random() * n)` → **0 ~ n-1** 범위

### 코드 예제

```java
public class StaticMethodDemo {
    public static void main(String[] args) {
        // Math.random() — 0.0 <= 값 < 1.0
        double rand = Math.random();
        System.out.println(rand);

        // 0 ~ 9 사이 랜덤 정수
        int randInt = (int)(Math.random() * 10);
        System.out.println("0~9: " + randInt);

        // 1 ~ 6 사이 랜덤 정수 (주사위)
        int dice = (int)(Math.random() * 6) + 1;
        System.out.println("주사위: " + dice);

        // 5 ~ 15 사이 랜덤 정수
        // 공식: (int)(Math.random() * (max - min + 1)) + min
        int rangeRand = (int)(Math.random() * 11) + 5;
        System.out.println("5~15: " + rangeRand);
    }
}
```

### 시험 출제 포인트
- `Math.random()`은 `1.0`을 **절대 반환하지 않는다** (0.0 이상, 1.0 **미만**)
- 랜덤 범위 공식: `(int)(Math.random() * (max - min + 1)) + min`
- `(int)`를 빼먹으면 double이 나온다

### 연습 문제

**Q1.** 다음 코드가 생성할 수 있는 값의 범위는?
```java
int x = (int)(Math.random() * 5) + 3;
```
- (A) 0 ~ 4
- (B) 3 ~ 7
- (C) 3 ~ 8
- (D) 0 ~ 7

> **정답: (B)** — `Math.random() * 5`는 0.0~4.999..., `(int)` 캐스팅으로 0~4, `+3`으로 3~7

---

## 1.11 Math Class (2기간)

### CED 학습목표
- Math 클래스의 static 메서드를 적절히 사용할 수 있다.

### 핵심 개념 (모두 static 메서드!)

| 메서드 | 설명 | 예시 |
|--------|------|------|
| `Math.abs(x)` | 절대값 | `Math.abs(-5)` → `5` |
| `Math.pow(base, exp)` | 거듭제곱 | `Math.pow(2, 3)` → `8.0` |
| `Math.sqrt(x)` | 제곱근 | `Math.sqrt(25)` → `5.0` |
| `Math.random()` | 0.0 이상 1.0 미만 랜덤 | `Math.random()` → `0.73...` |

### 코드 예제

```java
public class MathClassDemo {
    public static void main(String[] args) {
        // abs — 절대값
        System.out.println(Math.abs(-7));    // 출력: 7
        System.out.println(Math.abs(7));     // 출력: 7
        System.out.println(Math.abs(-3.5));  // 출력: 3.5

        // pow — 거듭제곱 (반환 타입이 항상 double!)
        System.out.println(Math.pow(2, 10)); // 출력: 1024.0
        System.out.println(Math.pow(3, 0));  // 출력: 1.0

        // sqrt — 제곱근 (반환 타입이 항상 double!)
        System.out.println(Math.sqrt(144));  // 출력: 12.0
        System.out.println(Math.sqrt(2));    // 출력: 1.4142135623730951

        // 두 점 사이의 거리: sqrt((x2-x1)^2 + (y2-y1)^2)
        double x1 = 1, y1 = 2, x2 = 4, y2 = 6;
        double distance = Math.sqrt(Math.pow(x2 - x1, 2) + Math.pow(y2 - y1, 2));
        System.out.println("거리: " + distance); // 출력: 거리: 5.0
    }
}
```

### 시험 출제 포인트
- `Math.pow()`와 `Math.sqrt()`는 **항상 double을 반환**한다
- `Math.abs()`는 int를 넣으면 int, double을 넣으면 double 반환
- `Math.pow(2, 3)`의 결과는 `8`이 아니라 `8.0`이다

### 연습 문제

**Q1.** 다음 코드의 출력은?
```java
System.out.println(Math.abs(-3) + Math.pow(2, 2));
```
- (A) 7
- (B) 7.0
- (C) 1.0
- (D) 1

> **정답: (B)** — `Math.abs(-3)` = `3` (int), `Math.pow(2, 2)` = `4.0` (double), `3 + 4.0` = `7.0` (double)

---

## 1.12 Objects: Instances of Classes (1기간)

> **쉽게 말해**: 클래스는 **붕어빵 틀**, 객체는 **붕어빵**이다. 틀(클래스)은 하나지만 붕어빵(객체)은 여러 개 만들 수 있다. 각 붕어빵은 같은 모양이지만, 안에 든 재료(팥, 슈크림 = 인스턴스 변수)는 다를 수 있다.

### CED 학습목표
- 클래스와 객체의 관계를 이해할 수 있다.

### 핵심 개념
- **클래스(Class)** = 객체의 설계도 (blueprint/template)
- **객체(Object)** = 클래스의 **인스턴스(instance)** — 실제로 메모리에 생성된 것
- **참조 변수(Reference variable)** = 객체의 **메모리 주소**를 가리키는 변수
  - Primitive 변수: 값 자체를 저장
  - Reference 변수: 객체가 있는 곳의 주소를 저장

```
Primitive:   int x = 5;       →  x: [5]

Reference:   String s = "Hi"; →  s: [주소] ──→ String 객체 "Hi"
```

### 코드 예제

```java
public class ObjectsDemo {
    public static void main(String[] args) {
        // String은 클래스, s는 참조 변수, "Hello"는 객체
        String s = "Hello";

        // 같은 클래스에서 여러 객체 생성 가능
        String s1 = "AP";
        String s2 = "CSA";
        // s1과 s2는 각각 다른 String 객체를 가리킴

        System.out.println(s);   // 출력: Hello
        System.out.println(s1);  // 출력: AP
        System.out.println(s2);  // 출력: CSA
    }
}
```

### 시험 출제 포인트
- 하나의 클래스에서 **여러 개의 객체**를 만들 수 있다
- Reference 변수에 저장된 것은 객체 자체가 아니라 **객체의 주소**

### 연습 문제

**Q1.** 다음 변수 선언 중 **reference type** 변수는 어느 것인가?
```java
int a = 10;
double b = 3.14;
String c = "Hello";
boolean d = true;
```

- (A) `a`
- (B) `b`
- (C) `c`
- (D) `d`

> **정답: (C)** — `String`은 클래스이므로 `c`는 reference 변수이다. `int`, `double`, `boolean`은 모두 primitive type으로 값 자체를 저장한다. Reference 변수인 `c`는 `"Hello"` 객체의 메모리 주소를 저장한다.

---

## 1.13 Object Creation and Storage (2기간)

### CED 학습목표
- `new` 키워드로 객체를 생성하고, 참조가 어떻게 저장되는지 이해할 수 있다.

### 핵심 개념
- 객체 생성: `new ClassName(arguments)` → **생성자(Constructor)** 호출
- 생성자: 객체를 초기화하는 특별한 메서드 (클래스와 이름이 같음)
- **Aliasing** (별칭): 여러 변수가 **같은 객체**를 가리키는 것

### 코드 예제

```java
import java.util.Scanner;

public class ObjectCreationDemo {
    public static void main(String[] args) {
        // new 키워드로 객체 생성 (시험 출제 형태: 파일 입력)
        // Scanner sc = new Scanner(new File("input.txt"));  // ← 시험 형태
        String greeting = new String("Hello");

        // Aliasing — 같은 객체를 두 변수가 가리킴
        String a = new String("Java");
        String b = a;  // b도 같은 객체를 가리킴! (복사가 아님)

        System.out.println(a);  // 출력: Java
        System.out.println(b);  // 출력: Java
        System.out.println(a == b);  // 출력: true (같은 객체를 가리킴)

        // 다른 객체를 가리키면?
        String c = new String("Java");
        System.out.println(a == c);  // 출력: false (내용은 같지만 다른 객체)
        System.out.println(a.equals(c));  // 출력: true (내용이 같음)
    }
}
```

### 시험 출제 포인트
- **Aliasing 주의!** `b = a`는 객체를 복사하는 것이 아니라, b가 a와 **같은 객체를 가리키게** 하는 것
- `==`는 참조(주소) 비교, `equals()`는 내용 비교 — 이 차이 필수 암기
- `null`인 변수로 메서드를 호출하면 `NullPointerException` 발생

### 연습 문제

**Q1.** 다음 코드 실행 후, `a == b`와 `a.equals(b)`의 결과는?
```java
String a = new String("test");
String b = new String("test");
```
- (A) true, true
- (B) false, true
- (C) true, false
- (D) false, false

> **정답: (B)** — `new`로 각각 생성했으므로 다른 객체(==는 false), 내용은 같음(equals는 true)

---

## 1.14 Calling Instance Methods (2기간)

### CED 학습목표
- 인스턴스 메서드(non-static)를 올바르게 호출할 수 있다.

### 핵심 개념
- **인스턴스 메서드**: 특정 객체에 대해 호출하는 메서드
- 호출 방법: `objectName.methodName(arguments)`
- **void 메서드**: 값을 반환하지 않음 (동작만 수행)
- **반환값 있는 메서드**: 결과를 돌려줌 → 변수에 저장하거나 출력 가능

| 구분 | Static 메서드 | Instance 메서드 |
|------|-------------|----------------|
| 호출 방법 | `ClassName.method()` | `objectName.method()` |
| 예시 | `Math.sqrt(4)` | `str.length()` |
| 객체 필요? | 아니오 | 예 |

### 코드 예제

```java
public class InstanceMethodDemo {
    public static void main(String[] args) {
        String name = "AP Computer Science A";

        // 반환값 있는 인스턴스 메서드 (CED 1.15 Quick Reference 준수)
        int len = name.length();           // 반환값을 변수에 저장
        System.out.println(len);           // 출력: 21

        String first = name.substring(0, 12);  // 새 String 반환 (인덱스 0~11)
        System.out.println(first);             // 출력: AP Computer

        // void 메서드 예시 (ArrayList에서 볼 수 있음)
        // list.add("item"); → 반환값 없이 동작만 수행

        // 메서드 체이닝 (반환값에 바로 메서드 호출)
        System.out.println("hello".substring(1, 4).length()); // 출력: 3 ("ell"의 길이)
    }
}
```

### 시험 출제 포인트
- void 메서드의 결과를 변수에 저장하려고 하면 **컴파일 에러**
- 반환값이 있는 메서드를 호출만 하고 결과를 사용하지 않으면 값이 **사라진다**
- `null` 참조에 인스턴스 메서드를 호출하면 `NullPointerException`
- 반환 타입과 변수 타입이 일치하지 않으면 **타입 불일치 컴파일 에러**

### 연습 문제

**Q1.** 다음 코드의 실행 결과는?
```java
import java.util.ArrayList;

ArrayList<String> list = new ArrayList<String>();
String result = list.add("Java");
System.out.println(result);
```

- (A) `Java`
- (B) `true`
- (C) `null`
- (D) 컴파일 에러

> **정답: (D)** — `ArrayList`의 `add(E e)` 메서드는 `boolean`을 반환한다 (void가 아님). `boolean result = list.add("Java")`는 정상 동작하지만, 여기서는 `String result`에 `boolean` 값을 저장하려 하므로 **타입 불일치(type mismatch) 컴파일 에러**가 발생한다. 핵심: 메서드의 반환 타입을 정확히 알고, 그에 맞는 변수 타입을 사용해야 한다.

---

## 1.15 String Manipulation (4기간)

### CED 학습목표
- String 클래스의 주요 메서드를 사용하여 문자열을 조작할 수 있다.

### 핵심 개념
- **String은 immutable(불변)** — 한번 생성되면 변경 불가. 메서드 호출 시 **새로운 String 반환**

> **비유**: String이 불변(immutable)인 것은 **펜으로 쓴 글씨**와 같다. 지울 수 없고, 수정하려면 새 종이에 다시 써야 한다. `s.substring(1, 3)`은 원본 `s`를 바꾸지 않고 **새 문자열**을 만들어 반환한다 (잘라낸 부분).

- **인덱스는 0부터 시작!**

```
문자열:   "A P C S A"
인덱스:    0 1 2 3 4 5 6 7 8
```

### 주요 메서드 (필수 암기!)

| 메서드 | 설명 | 예시 (`s = "Hello"`) |
|--------|------|------|
| `s.length()` | 문자열 길이 | `5` |
| `s.substring(from, to)` | from ~ to-1 추출 | `s.substring(1, 4)` → `"ell"` |
| `s.substring(from)` | from ~ 끝까지 | `s.substring(2)` → `"llo"` |
| `s.indexOf(str)` | str의 첫 위치 (-1 = 없음) | `s.indexOf("ll")` → `2` |
| `s.equals(other)` | 내용 비교 | `s.equals("Hello")` → `true` |
| `s.compareTo(other)` | 사전순 비교 | 음수/0/양수 |

#### compareTo 규칙
- `s.compareTo(other)` < 0 → s가 사전순으로 **앞**
- `s.compareTo(other)` == 0 → 같음
- `s.compareTo(other)` > 0 → s가 사전순으로 **뒤**

#### 문자열 연결 (Concatenation)
- `+` 연산자로 문자열 연결
- **숫자 + 문자열 = 문자열** (자동 변환)

### 코드 예제

```java
public class StringDemo {
    public static void main(String[] args) {
        String s = "AP CSA";

        // length()
        System.out.println(s.length());         // 출력: 6

        // substring(from, to) — from 포함, to 미포함!
        System.out.println(s.substring(0, 2));   // 출력: "AP"
        System.out.println(s.substring(3, 6));   // 출력: "CSA"
        System.out.println(s.substring(3));      // 출력: "CSA"

        // indexOf
        System.out.println(s.indexOf("CS"));     // 출력: 3
        System.out.println(s.indexOf("Java"));   // 출력: -1 (없음)

        // equals vs ==
        String a = new String("Hello");
        String b = new String("Hello");
        System.out.println(a == b);              // 출력: false (다른 객체)
        System.out.println(a.equals(b));         // 출력: true (내용 같음)

        // compareTo
        System.out.println("Apple".compareTo("Banana"));  // 음수 (A < B)
        System.out.println("Cat".compareTo("Cat"));       // 0 (같음)
        System.out.println("Dog".compareTo("Cat"));       // 양수 (D > C)

        // 문자열 연결
        String name = "Kim";
        int score = 95;
        System.out.println(name + " scored " + score);  // 출력: Kim scored 95
        System.out.println(1 + 2 + " apples");          // 출력: 3 apples
        System.out.println("apples " + 1 + 2);          // 출력: apples 12

        // String은 불변!
        String original = "Hello";
        original.substring(1, 3);  // 새 String "el"이 반환되지만 저장 안 함!
        System.out.println(original);  // 출력: Hello (변하지 않음!)

        String changed = original.substring(1, 3);
        System.out.println(changed);   // 출력: el (substring 결과는 changed에 저장됨)
    }
}
```

### 시험 출제 포인트
- **`substring(from, to)`에서 to는 미포함!** `"Hello".substring(1, 3)` → `"el"` (인덱스 1, 2만)
- **String은 불변** — `s.substring(...)`을 호출해도 s 자체는 변하지 않는다 (새 String 반환)
- **`==` vs `equals()`** — String 비교는 반드시 `equals()` 사용!
- 문자열 연결 시 **왼쪽에서 오른쪽 순서**로 평가: `1 + 2 + "a"` → `"3a"`, `"a" + 1 + 2` → `"a12"`
- `indexOf()`가 문자열을 못 찾으면 `-1` 반환
- **FRQ Q1은 String 메서드 활용을 요구한다** — substring, indexOf, length 연습 필수!

### 연습 문제

**Q1.** 다음 코드의 출력은?
```java
String s = "Computer";
System.out.println(s.substring(3, 6));
```
- (A) "mpu"
- (B) "put"
- (C) "pute"
- (D) "mput"

> **정답: (B)** — 인덱스 3='p', 4='u', 5='t' (6은 미포함). `"put"`

**Q2.** 다음 코드의 출력은?
```java
System.out.println("Java" + 2 + 3);
System.out.println(2 + 3 + "Java");
```
- (A) Java23, 23Java
- (B) Java5, 5Java
- (C) Java23, 5Java
- (D) Java5, 23Java

> **정답: (C)** — 첫 줄: "Java"가 먼저이므로 뒤 숫자도 문자열로 연결 → "Java23". 둘째 줄: 2+3이 먼저 산술연산 → 5, 그 다음 문자열 연결 → "5Java"

---

## FRQ 대비: String 메서드 조합 연습

FRQ Q1은 Unit 1의 String 메서드를 핵심적으로 사용한다. 아래 문제를 "메서드를 구현하시오" 형태로 풀어보자.

### 연습 1: 첫 글자와 마지막 글자 교환

주어진 문자열의 첫 글자와 마지막 글자를 교환한 새 문자열을 반환하는 메서드를 작성하시오.

예: `swapEnds("Hello")` → `"oellH"`, `swapEnds("ab")` → `"ba"`

Precondition: str의 길이는 2 이상

```java
public static String swapEnds(String str)
```

<details>
<summary>모범 답안</summary>

```java
public static String swapEnds(String str) {
    String first = str.substring(0, 1);
    String last = str.substring(str.length() - 1);
    String middle = str.substring(1, str.length() - 1);
    return last + middle + first;
}
```

**핵심**: `substring(0, 1)` = 첫 글자, `substring(length()-1)` = 마지막 글자, `substring(1, length()-1)` = 중간 부분
</details>

### 연습 2: 단어 수 세기

공백으로 구분된 문자열에서 단어의 수를 반환하는 메서드를 작성하시오.

예: `countWords("hello world java")` → `3`, `countWords("one")` → `1`

Precondition: str은 빈 문자열이 아니며, 연속 공백 없음

```java
public static int countWords(String str)
```

<details>
<summary>모범 답안</summary>

```java
public static int countWords(String str) {
    int count = 1;
    for (int i = 0; i < str.length(); i++) {
        if (str.substring(i, i + 1).equals(" ")) {
            count++;
        }
    }
    return count;
}
```

**핵심**: 공백 수 + 1 = 단어 수. `charAt` 대신 `substring(i, i+1).equals(" ")`를 사용 (AP 표준 패턴)
</details>

---

## 자주 틀리는 코드 모음 (Unit 1)

### 복합 대입 연산자 실수

```java
// ❌ 잘못된 코드: 타입 불일치
int x = 10;
x += "3";  // 컴파일 에러! int에 String을 더할 수 없다

// ❌ 잘못된 코드: 0으로 나누기
int y = 5;
y /= 0;    // ArithmeticException! (런타임 에러)

// ✅ 올바른 코드
int z = 10;
z += 3;    // z = 13
z *= 2;    // z = 26
z %= 5;    // z = 1 (26을 5로 나눈 나머지)
```

### API/메서드 호출 실수

```java
// ❌ 잘못된 코드: static 메서드를 객체로 호출
Math m = new Math();      // 컴파일 에러! Math는 new로 생성 불가
double r = m.random();

// ✅ 올바른 코드: 클래스 이름으로 호출
double r = Math.random();  // 0.0 이상 1.0 미만

// ❌ 잘못된 코드: pow/sqrt 반환값을 int에 저장
int result = Math.pow(2, 10);  // 컴파일 에러! double을 int에 저장 불가

// ✅ 올바른 코드: 캐스팅 필요
int result = (int) Math.pow(2, 10);  // 1024
```

### 객체 비교 실수

```java
// ❌ 잘못된 코드: String을 ==로 비교
String s1 = new String("hello");
String s2 = new String("hello");
if (s1 == s2) {           // false! (주소 비교)
    System.out.println("같다");
}

// ✅ 올바른 코드: .equals()로 비교
if (s1.equals(s2)) {      // true (내용 비교)
    System.out.println("같다");
}
```

---

## 시험 대비 종합 팁

### 코드 Tracing (추적)
- 변수 값의 변화를 **표로 그려가며** 추적하는 연습을 충분히 할 것
- 특히 대입문, 복합 대입, 캐스팅이 섞인 문제

### Java Quick Reference 활용
- 시험장에서 제공되는 Quick Reference를 평소에 자주 참조하는 습관
- String 메서드, Math 메서드의 매개변수와 반환 타입을 정확히 숙지

### FRQ 대비
- **FRQ Q1**이 이 Unit의 String 메서드 활용을 요구함
- `substring()`, `indexOf()`, `length()`, `equals()`의 조합 연습

### 자주 틀리는 TOP 5
1. **정수 나눗셈**: `7 / 2` → `3` (3.5가 아님!)
2. **(int) 캐스팅 = 버림**: `(int) 3.9` → `3` (반올림 아님!)
3. **substring to는 미포함**: `s.substring(1, 3)` → 인덱스 1, 2만
4. **String 불변**: `s.substring(...)`은 s를 안 바꿈, 새 String 반환
5. **문자열 비교**: `==`이 아니라 `equals()` 사용
