# AP CSA 초보자 FAQ + 개념 연결 가이드

> Java를 처음 배우는 고등학생을 위한 친절한 안내서
> AP Computer Science A (2025-26 커리큘럼 기준)

---

# Part 1: 자주 묻는 질문 50개

---

## 🔹 Java 기초 (10개)

---

### Q1. "왜 `public static void main`이 필요해요?"

**짧은 답변:** Java 프로그램의 시작점(entry point)이에요. 이게 없으면 컴퓨터가 어디서부터 실행할지 몰라요.

**자세한 설명:**

집에 현관문이 있는 것처럼, Java 프로그램에도 "입구"가 필요해요. 그게 바로 `main` 메서드예요.

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello!");
    }
}
```

각 단어의 의미:
- `public` → 누구나 접근 가능 (JVM이 호출해야 하니까)
- `static` → 객체를 만들지 않고도 실행 가능
- `void` → 아무것도 돌려주지 않음
- `main` → Java가 약속한 시작점 이름
- `String[] args` → 실행할 때 추가 정보를 받을 수 있는 칸 (지금은 무시해도 OK)

지금은 "이건 그냥 Java의 규칙이다"라고 외워도 괜찮아요. `static`과 `void`는 나중에 Unit 3에서 자세히 배워요.

**관련 토픽:** 1.1 Introduction to Algorithms, 3.7 static Variables and Methods, 3.5 Methods

---

### Q2. "세미콜론 안 쓰면 왜 에러나요?"

**짧은 답변:** 세미콜론(`;`)은 문장의 마침표예요. 없으면 Java가 "문장이 아직 안 끝났나?" 하고 혼란스러워해요.

**자세한 설명:**

한국어에서 마침표(.)를 안 쓰면 문장이 어디서 끝나는지 모르는 것처럼, Java에서는 `;`이 "여기서 이 명령 끝!"이라는 신호예요.

```java
// 올바른 코드
int x = 5;
System.out.println(x);

// 에러! 세미콜론 빠짐
int x = 5
System.out.println(x)
```

주의: `if`, `for`, `while` 같은 제어문의 헤더 뒤에는 세미콜론을 안 써요!

```java
if (x > 0) {   // ← 여기에 ; 쓰면 안 됨!
    System.out.println("양수");
}
```

**관련 토픽:** 1.1 Introduction to Algorithms, 1.3 Expressions and Output

---

### Q3. "중괄호가 왜 이렇게 많아요?"

**짧은 답변:** 중괄호 `{ }`는 "여기서부터 여기까지가 한 묶음이야"라는 표시예요. 상자 안에 상자를 넣는 거라고 생각하면 돼요.

**자세한 설명:**

중괄호는 코드의 범위(scope)를 정해줘요. 러시아 인형(마트료시카)처럼 겹겹이 들어가요:

```java
public class MyProgram {              // 클래스 상자 시작
    public static void main(String[] args) {  // 메서드 상자 시작
        if (true) {                   // if 상자 시작
            System.out.println("Hi");
        }                             // if 상자 끝
    }                                 // 메서드 상자 끝
}                                     // 클래스 상자 끝
```

팁: 들여쓰기(indentation)를 잘 하면 어떤 중괄호가 짝인지 쉽게 보여요. IDE에서 자동 정렬(Auto-Format)을 적극 활용하세요!

**관련 토픽:** 1.1 Introduction, 3.3 Anatomy of a Java Class, 3.8 Scope and Access

---

### Q4. "파일 이름이랑 클래스 이름이 왜 같아야 해요?"

**짧은 답변:** Java의 규칙이에요. `public class`의 이름과 `.java` 파일 이름이 정확히 같아야 컴파일돼요.

**자세한 설명:**

Java 컴파일러는 파일 이름으로 클래스를 찾아요. 마치 학교에서 출석부 이름과 실제 이름이 같아야 하는 것처럼요.

```java
// 파일 이름: Dog.java ← 이름이 일치해야 함!
public class Dog {
    // ...
}
```

만약 파일 이름이 `Cat.java`인데 안에 `public class Dog`가 있으면? → 컴파일 에러!

대소문자도 정확히 같아야 해요. `dog.java` ≠ `Dog.java`

**관련 토픽:** 1.1 Introduction, 3.3 Anatomy of a Java Class

---

### Q5. "`System.out.println`이 뭐예요? 왜 이렇게 길어요?"

**짧은 답변:** 화면에 글자를 출력하는 명령이에요. "System의 출력 장치에 한 줄을 인쇄해라"라는 뜻이에요.

**자세한 설명:**

분해해서 읽어봐요:
- `System` → Java에 내장된 시스템 클래스
- `out` → 출력 장치 (보통 화면/콘솔)
- `println` → print + line (출력하고 줄바꿈)

```java
System.out.println("Hello");  // Hello 출력 후 줄바꿈
System.out.print("A");        // A 출력 (줄바꿈 없음)
System.out.print("B");        // 바로 옆에 B 출력
// 결과: AB
```

`println` vs `print` 차이:
- `println` = 출력 후 다음 줄로 이동
- `print` = 출력 후 같은 줄에 머무름

길긴 하지만, IDE에서 `sout` + Tab 치면 자동완성돼요!

**관련 토픽:** 1.3 Expressions and Output

---

### Q6. "주석은 왜 쓰나요?"

**짧은 답변:** 나중에 코드를 다시 볼 때 "아, 여기서 이런 걸 하는구나" 하고 이해하려고요. 주석은 실행되지 않아요.

**자세한 설명:**

주석은 사람을 위한 메모예요. 컴퓨터는 완전히 무시해요.

```java
// 한 줄 주석: 슬래시 두 개
int age = 17;  // 학생 나이

/* 여러 줄 주석:
   이렇게 여러 줄에 걸쳐
   설명을 쓸 수 있어요 */

/** Javadoc 주석:
 *  메서드나 클래스를 문서화할 때 사용
 *  AP 시험에서도 나와요!
 */
```

"지금은 기억나니까 안 써도 되지~" → 2주 뒤에 보면 내가 쓴 코드를 못 알아봐요. 미래의 나를 위해 쓰는 거예요!

AP 시험의 FRQ에서도 주석으로 의도를 설명하면 부분 점수를 받을 수 있어요.

**관련 토픽:** 1.8 Documentation with Comments and Preconditions

---

### Q7. "Java랑 JavaScript는 같은 건가요?"

**짧은 답변:** 아니요, 완전히 다른 언어예요. 이름만 비슷할 뿐이에요.

**자세한 설명:**

"햄"과 "햄스터"가 다른 것처럼, Java와 JavaScript는 이름만 비슷한 전혀 다른 언어예요.

| | Java | JavaScript |
|---|---|---|
| 용도 | 앱, 서버, 안드로이드 | 웹페이지, 웹앱 |
| 타입 | 엄격 (int x = 5;) | 유연 (let x = 5;) |
| 실행 | 컴파일 → 실행 | 브라우저에서 바로 실행 |
| AP 시험 | AP CSA ✅ | AP CSP에서 일부 |

Java를 배우면 프로그래밍의 기본기가 탄탄해져서, 나중에 JavaScript든 Python이든 빠르게 배울 수 있어요.

**관련 토픽:** 1.1 Introduction to Algorithms

---

### Q8. "`int`랑 `double`은 언제 뭘 써요?"

**짧은 답변:** 정수(1, 2, -3)만 필요하면 `int`, 소수점(3.14, -0.5)이 필요하면 `double`을 써요.

**자세한 설명:**

```java
int students = 30;        // 학생 수 → 정수! → int
double gpa = 3.85;        // 학점 → 소수점 필요 → double
int age = 17;             // 나이 → 정수 → int
double price = 9.99;      // 가격 → 소수점 → double
boolean isHappy = true;   // 참/거짓 → boolean (이것도 있어요!)
```

선택 기준:
- 소수점이 절대 필요 없다 → `int` (더 빠르고, 정확함)
- 소수점이 있을 수도 있다 → `double`
- 참/거짓이다 → `boolean`

주의: `int`끼리 나누면 소수점이 사라져요! (Q11에서 자세히!)

**관련 토픽:** 1.2 Variables and Data Types, 1.5 Casting and Ranges of Values

---

### Q9. "변수 이름은 아무거나 해도 돼요?"

**짧은 답변:** 규칙만 지키면 자유롭지만, 의미 있는 이름을 쓰는 게 훨씬 좋아요.

**자세한 설명:**

**규칙 (어기면 에러):**
- 문자, `_`, `$`로 시작해야 함 (숫자로 시작 불가)
- 예약어 사용 불가 (`int`, `class`, `for` 등)
- 공백 불가

```java
int myAge = 17;      // ✅ 좋은 이름
int x = 17;          // ⚠️ 작동하지만 뭔지 모름
int 2ndPlace = 2;    // ❌ 숫자로 시작 불가
int my age = 17;     // ❌ 공백 불가
int class = 5;       // ❌ 예약어
```

**관례 (어겨도 작동하지만 지키면 좋음):**
- 변수/메서드: `camelCase` → `studentName`, `getAge()`
- 클래스: `PascalCase` → `Student`, `BankAccount`
- 상수: `ALL_CAPS` → `MAX_SIZE`

AP 시험에서 변수 이름의 의미를 묻는 문제가 나와요!

**관련 토픽:** 1.2 Variables and Data Types

---

### Q10. "`=`는 수학에서랑 다른 건가요?"

**짧은 답변:** 네! 수학에서 `=`는 "같다"이지만, Java에서 `=`는 "오른쪽 값을 왼쪽에 넣어라"예요.

**자세한 설명:**

```java
int x = 5;    // "x에 5를 넣어라" (대입)
x = x + 1;   // 수학에서는 말이 안 되지만, Java에서는 OK!
              // "x에 x+1의 결과(6)를 넣어라"
```

비교:
| 기호 | 수학에서 | Java에서 |
|------|---------|---------|
| `=` | 같다 | 대입 (넣어라) |
| `==` | - | 같은지 비교 |

```java
int a = 3;
int b = 3;
System.out.println(a == b);  // true (비교)
a = 10;                       // a에 10을 넣어라 (대입)
```

자주 하는 실수: `if (x = 5)` → 이건 대입이라 에러! `if (x == 5)`로 써야 해요.

**관련 토픽:** 1.4 Assignment and Input, 2.2 Boolean Expressions

---

## 🔹 연산/타입 (8개)

---

### Q11. "`7/2`가 왜 3이에요? 3.5 아니에요?"

**짧은 답변:** `int ÷ int = int`예요. 정수끼리 나누면 소수점 아래를 **버려요** (반올림 아님!).

**자세한 설명:**

Java에서 정수(int)끼리의 나눗셈은 **정수 나눗셈**이에요. 소수점 이하를 그냥 잘라버려요.

```java
System.out.println(7 / 2);     // 3 (0.5 버림)
System.out.println(7 / 2.0);   // 3.5 (하나라도 double이면 OK)
System.out.println((double)7 / 2);  // 3.5 (캐스팅)

// 주의! 이건 여전히 3.0
System.out.println((double)(7 / 2));  // 3.0 (이미 3이 된 후에 double 변환)
```

3.5를 얻고 싶으면:
1. 하나를 `double`로 만들기: `7 / 2.0` 또는 `7.0 / 2`
2. 캐스팅하기: `(double) 7 / 2`

AP 시험 단골 문제예요! 순서를 잘 봐야 해요.

**관련 토픽:** 1.3 Expressions and Output, 1.5 Casting and Ranges of Values

---

### Q12. "`(int)3.9`가 왜 3이에요? 반올림 아닌가요?"

**짧은 답변:** `(int)` 캐스팅은 반올림이 아니라 **소수점 아래를 버리는 것(truncation)**이에요.

**자세한 설명:**

```java
System.out.println((int) 3.9);   // 3 (버림!)
System.out.println((int) 3.1);   // 3
System.out.println((int) -2.7);  // -2 (0 방향으로 버림)
```

반올림을 하고 싶다면 `Math.round()`를 쓰거나, `+0.5` 후 캐스팅:

```java
// 반올림 방법
System.out.println((int)(3.9 + 0.5));  // 4
System.out.println((int)(3.1 + 0.5));  // 3
```

이건 AP 시험에서 정말 자주 나와요. **truncation = 소수점 아래 잘라내기**라고 기억하세요!

**관련 토픽:** 1.5 Casting and Ranges of Values

---

### Q13. "`%` 나머지 연산은 언제 써요?"

**짧은 답변:** 나눗셈의 나머지를 구할 때 써요. 짝수/홀수 판별, 자릿수 추출 등에 유용해요.

**자세한 설명:**

`%`는 모듈로(modulo) 연산자라고 해요.

```java
System.out.println(7 % 2);   // 1 (7÷2=3 나머지 1)
System.out.println(10 % 3);  // 1 (10÷3=3 나머지 1)
System.out.println(8 % 4);   // 0 (딱 나누어떨어짐)
```

실전 활용:
```java
// 짝수/홀수 판별
if (n % 2 == 0) { /* 짝수 */ }

// 마지막 자릿수 추출
int lastDigit = 1234 % 10;  // 4

// N번마다 뭔가 하기
if (i % 5 == 0) { /* 5의 배수마다 실행 */ }
```

**관련 토픽:** 1.3 Expressions and Output, 2.9 Selection/Iteration Algorithms

---

### Q14. "`int`를 `double`로, `double`을 `int`로 바꾸는 게 뭐예요?"

**짧은 답변:** 타입을 변환하는 걸 **캐스팅(casting)**이라 해요. `int→double`은 자동, `double→int`는 수동으로 해야 해요.

**자세한 설명:**

```java
// 자동 변환 (widening) - 안전하니까 자동으로 됨
int a = 5;
double b = a;  // 5 → 5.0 (정보 손실 없음)

// 수동 변환 (narrowing) - 소수점 잃으니까 직접 해야 함
double c = 3.7;
int d = (int) c;  // 3.7 → 3 (소수점 버림! 반올림 아님!)
// int d = c;     // ❌ 에러! 명시적 캐스팅 필요
```

비유: 작은 컵(int)의 물을 큰 컵(double)에 부으면 OK. 큰 컵의 물을 작은 컵에 부으면 넘칠 수 있으니까 "넘쳐도 괜찮아!"라고 확인이 필요한 거예요.

**관련 토픽:** 1.5 Casting and Ranges of Values

---

### Q15. "`+=`이 뭐예요?"

**짧은 답변:** `x += 3`은 `x = x + 3`의 줄임말이에요.

**자세한 설명:**

**복합 대입 연산자**라고 해요. 더 짧게 쓸 수 있어요:

```java
int score = 10;

score += 5;   // score = score + 5;  → 15
score -= 3;   // score = score - 3;  → 12
score *= 2;   // score = score * 2;  → 24
score /= 4;   // score = score / 4;  → 6
score %= 4;   // score = score % 4;  → 2
```

특히 자주 쓰는 것:
```java
count++;      // count += 1; 과 같음 (1 증가)
count--;      // count -= 1; 과 같음 (1 감소)
```

AP 시험에서 `x++`과 `++x`의 차이를 물어보진 않아요. 둘 다 1 증가라고만 알면 돼요.

**관련 토픽:** 1.6 Compound Assignment Operators

---

### Q16. "`String`이 primitive가 아니라고요?"

**짧은 답변:** 맞아요! `String`은 클래스(참조 타입)예요. `int`, `double`, `boolean`만 primitive(기본 타입)예요.

**자세한 설명:**

Java의 타입은 크게 두 종류:

| Primitive (기본 타입) | Reference (참조 타입) |
|---|---|
| `int`, `double`, `boolean` | `String`, `ArrayList`, 모든 클래스 |
| 소문자로 시작 | 대문자로 시작 |
| 값 자체를 저장 | 주소(참조)를 저장 |
| `==`로 비교 OK | `==`는 주소 비교! `.equals()`를 써야 함 |

```java
int a = 5;           // 기본 타입: 값 5를 직접 저장
String s = "Hello";  // 참조 타입: "Hello"가 있는 곳의 주소를 저장
```

그래서 `String`은 대문자로 시작하고, `.length()`, `.substring()` 같은 메서드를 가질 수 있는 거예요!

**관련 토픽:** 1.2 Variables and Data Types, 1.12 Objects, 1.15 Strings

---

### Q17. "`null`이 뭐예요?"

**짧은 답변:** "아무것도 가리키지 않음"이라는 뜻이에요. 참조 변수가 어떤 객체도 가리키지 않는 상태예요.

**자세한 설명:**

비유: 빈 주소록 칸이에요. "이 칸에는 아직 아무 주소도 적혀있지 않아요."

```java
String name = null;   // name이 아무 객체도 가리키지 않음
String greeting = "Hi";

System.out.println(greeting.length());  // 2 (OK)
System.out.println(name.length());      // ❌ NullPointerException!
```

`null`인 변수에 메서드를 호출하면 `NullPointerException`이라는 에러가 터져요. 초보자가 가장 많이 만나는 에러 중 하나!

```java
// 안전하게 쓰려면
if (name != null) {
    System.out.println(name.length());
}
```

참고: `int`, `double`, `boolean` 같은 primitive 타입은 `null`이 될 수 없어요.

**관련 토픽:** 1.12 Objects, 1.14 Instance Methods

---

### Q18. "overflow가 뭐예요?"

**짧은 답변:** `int`가 담을 수 있는 최대값(약 21억)을 넘으면 값이 엉뚱하게 바뀌는 현상이에요.

**자세한 설명:**

`int`는 약 -21억 ~ +21억(`-2,147,483,648` ~ `2,147,483,647`)까지만 저장할 수 있어요.

```java
int big = 2147483647;  // int의 최대값
System.out.println(big + 1);  // -2147483648 (?!)
```

마치 자동차 계기판이 999999에서 000000으로 돌아가는 것과 같아요. 최대값을 넘기면 최소값으로 돌아가버려요.

AP 시험에서는 `Integer.MAX_VALUE`를 알아두면 좋아요:
```java
System.out.println(Integer.MAX_VALUE);  // 2147483647
System.out.println(Integer.MIN_VALUE);  // -2147483648
```

**관련 토픽:** 1.5 Casting and Ranges of Values

---

## 🔹 String (7개)

---

### Q19. "`==`로 String 비교하면 왜 안 돼요?"

**짧은 답변:** `==`는 두 String이 "같은 객체인지(주소 비교)"를 보고, `.equals()`는 "내용이 같은지"를 봐요.

**자세한 설명:**

```java
String a = "Hello";
String b = "Hello";
String c = new String("Hello");

System.out.println(a == b);        // true (같은 곳을 가리킴 - 우연히!)
System.out.println(a == c);        // false (다른 객체!)
System.out.println(a.equals(c));   // true (내용이 같음 ✅)
```

비유: 두 명이 같은 책을 가지고 있어요.
- `==` → "너네 둘이 **같은** 책을 공유하고 있어?" (같은 물리적 책?)
- `.equals()` → "너네 책 **내용**이 같아?" (내용 비교)

**규칙: String 비교는 항상 `.equals()`를 쓰세요!**

AP 시험에서 `==`와 `.equals()`의 차이를 묻는 문제가 반드시 나와요.

**관련 토픽:** 1.15 Strings, 1.12 Objects

---

### Q20. "`substring(1,3)`에서 왜 3번 인덱스가 안 들어가요?"

**짧은 답변:** `substring(start, end)`는 `start` 이상 `end` **미만**이에요. `end` 인덱스의 문자는 포함 안 돼요.

**자세한 설명:**

```java
String s = "Hello";
//          01234  ← 인덱스

System.out.println(s.substring(1, 3));  // "el" (인덱스 1, 2만!)
System.out.println(s.substring(0, 5));  // "Hello" (전체)
System.out.println(s.substring(2));     // "llo" (2부터 끝까지)
```

기억법: `substring(start, end)`에서 추출되는 글자 수 = `end - start`

```
H  e  l  l  o
0  1  2  3  4
   ^     ^
   1     3 (3은 포함 안 됨!)
   → "el"
```

울타리 기둥(fence post)으로 생각하면 이해가 쉬워요. 기둥 1~3 사이의 구간에 있는 문자(인덱스 1, 2)만 포함돼요.

**관련 토픽:** 1.15 Strings, 2.10 String Algorithms

---

### Q21. "String은 왜 바꿀 수 없다고 해요? `s = s + "a"` 되잖아요?"

**짧은 답변:** 기존 String 객체를 바꾸는 게 아니라, **새로운** String을 만들어서 s가 그걸 가리키게 하는 거예요.

**자세한 설명:**

String은 **immutable(불변)**이에요. 한번 만들어지면 그 내용을 바꿀 수 없어요.

```java
String s = "Hello";   // 메모리에 "Hello" 생성, s가 가리킴
s = s + " World";     // 새로 "Hello World" 생성, s가 새 객체를 가리킴
                      // 기존 "Hello"는 버려짐 (garbage collection)
```

비유:
- 칠판에 쓴 글씨를 지우개로 지우고 다시 쓰는 게 아니라 (mutable)
- 새 칠판에 다시 쓰고 이전 칠판을 버리는 거예요 (immutable)

AP 시험에서: String 메서드(`.substring()`, `.toUpperCase()` 등)는 원본을 바꾸지 않고 **새 String을 반환**한다는 걸 기억하세요!

```java
String s = "hello";
s.toUpperCase();           // 원본 안 바뀜!
System.out.println(s);     // "hello" 그대로

s = s.toUpperCase();       // 결과를 다시 저장해야 함!
System.out.println(s);     // "HELLO"
```

**관련 토픽:** 1.15 Strings, 1.12 Objects

---

### Q22. "`indexOf`가 -1을 반환하면 뭐예요?"

**짧은 답변:** "못 찾았다"는 뜻이에요. 찾는 문자/문자열이 없으면 -1을 돌려줘요.

**자세한 설명:**

```java
String s = "Hello World";
System.out.println(s.indexOf("World"));  // 6 (6번 인덱스에서 시작)
System.out.println(s.indexOf("Java"));   // -1 (없음!)
System.out.println(s.indexOf("o"));      // 4 (첫 번째로 발견된 위치)
```

활용 패턴:
```java
String text = "I like Java";
if (text.indexOf("Java") != -1) {
    System.out.println("Java가 포함되어 있어요!");
} else {
    System.out.println("Java가 없어요.");
}

// 또는 이렇게도
if (text.indexOf("Java") >= 0) {
    System.out.println("찾았다!");
}
```

**관련 토픽:** 1.15 Strings, 2.10 String Algorithms

---

### Q23. "`compareTo`가 뭔 숫자를 반환해요?"

**짧은 답변:** 사전 순서를 비교해요. 음수면 앞에, 0이면 같고, 양수면 뒤에 있다는 뜻이에요.

**자세한 설명:**

```java
String a = "Apple";
String b = "Banana";

System.out.println(a.compareTo(b));  // 음수 (-1) → a가 사전에서 앞
System.out.println(b.compareTo(a));  // 양수 (1)  → b가 사전에서 뒤
System.out.println(a.compareTo("Apple")); // 0 → 같다
```

기억법:
- **음수** → 내(a)가 앞 (a - b < 0이면 a가 작다 = 앞에 있다)
- **0** → 같다
- **양수** → 내(a)가 뒤

정확한 값은 중요하지 않아요! AP 시험에서는 **부호(양/음/0)만** 알면 돼요.

대소문자 주의: 대문자가 소문자보다 앞이에요. `"A".compareTo("a")` → 음수

**관련 토픽:** 1.15 Strings, 4.14 Searching, 4.15 Sorting

---

### Q24. "문자열 + 숫자 하면 어떻게 돼요?"

**짧은 답변:** 숫자가 문자열로 변환되어 이어붙어요. 이걸 **문자열 연결(concatenation)**이라 해요.

**자세한 설명:**

`+`의 한쪽이라도 String이면, 다른 쪽도 String으로 변환돼요.

```java
System.out.println("점수: " + 95);     // "점수: 95"
System.out.println("나이: " + 17);     // "나이: 17"
System.out.println(1 + 2 + "점");      // "3점" (1+2=3 먼저, 그 다음 "3"+"점")
System.out.println("점수" + 1 + 2);    // "점수12" (왼→오로 문자열 연결!)
```

**주의!** 왼쪽에서 오른쪽으로 계산하기 때문에 순서가 중요해요:
```java
System.out.println(1 + 2 + " = " + 1 + 2);
// 3 = 12   (앞의 1+2는 산술, 뒤의 1+2는 문자열 연결!)
```

이건 AP 시험의 MCQ에서 아주 자주 나오는 함정이에요!

**관련 토픽:** 1.3 Expressions and Output, 1.15 Strings

---

### Q25. "`charAt`은 안 배워요?"

**짧은 답변:** AP CSA 2025-26 시험 범위에는 포함되지 않아요. 대신 `substring(i, i+1)`로 한 글자를 추출해요.

**자세한 설명:**

```java
String s = "Hello";

// charAt - 시험 범위 아님 (하지만 알면 편함)
char c = s.charAt(0);  // 'H' (char 타입 반환)

// substring으로 같은 일 하기 - 시험에서는 이걸 씀
String c2 = s.substring(0, 1);  // "H" (String 타입 반환)
```

AP 시험에서 문자열의 i번째 글자를 다룰 때는 항상 `substring`을 사용해요:
```java
// i번째 글자 추출
String letter = s.substring(i, i + 1);

// 문자열 순회
for (int i = 0; i < s.length(); i++) {
    String ch = s.substring(i, i + 1);
    System.out.println(ch);
}
```

Quick Reference Sheet에도 `charAt`은 없어요. `substring`만 있으니 `substring`에 익숙해지세요!

**관련 토픽:** 1.15 Strings, 2.10 String Algorithms

---

## 🔹 조건문/루프 (8개)

---

### Q26. "`if` 다음에 중괄호 없으면 어떻게 돼요?"

**짧은 답변:** 중괄호가 없으면 **바로 다음 한 줄만** if에 속해요. 두 번째 줄부터는 항상 실행돼요.

**자세한 설명:**

```java
// 중괄호가 없는 경우 - 위험!
if (score > 90)
    System.out.println("A등급!");       // 이 줄만 if에 속함
    System.out.println("축하합니다!");   // 이 줄은 항상 실행됨! (함정!)

// 중괄호가 있는 경우 - 안전!
if (score > 90) {
    System.out.println("A등급!");
    System.out.println("축하합니다!");   // 둘 다 if에 속함
}
```

들여쓰기가 같아 보여도 Java는 들여쓰기를 무시해요! 중괄호만 봐요.

**규칙: 항상 중괄호를 쓰세요. 한 줄이더라도!** AP 시험에서도 이런 함정 문제가 나와요.

**관련 토픽:** 2.3 if Statements, 2.4 Nested if Statements

---

### Q27. "`&&`랑 `||` 차이가 뭐예요?"

**짧은 답변:** `&&`는 "그리고(AND)", `||`는 "또는(OR)"이에요.

**자세한 설명:**

```java
int age = 17;
boolean hasID = true;

// && (AND): 둘 다 참이어야 참
if (age >= 18 && hasID) {
    System.out.println("입장 가능");  // 실행 안 됨 (age < 18이니까)
}

// || (OR): 하나만 참이어도 참
if (age >= 18 || hasID) {
    System.out.println("입장 가능");  // 실행됨! (hasID가 true니까)
}
```

진리표:
| A | B | A && B | A \|\| B |
|---|---|--------|----------|
| T | T | T | T |
| T | F | F | T |
| F | T | F | T |
| F | F | F | F |

**Short-circuit evaluation (단축 평가):**
- `&&`: 앞이 false면 뒤는 보지도 않음
- `||`: 앞이 true면 뒤는 보지도 않음

```java
// str이 null일 때 안전한 코드
if (str != null && str.length() > 0) { ... }
// str이 null이면 && 앞이 false → 뒤를 실행 안 함 → NullPointerException 방지!
```

**관련 토픽:** 2.5 Compound Boolean Expressions

---

### Q28. "De Morgan이 뭐예요? 왜 외워야 해요?"

**짧은 답변:** "not (A and B) = (not A) or (not B)" 같은 논리 변환 법칙이에요. 조건문 단순화에 필요해요.

**자세한 설명:**

**De Morgan의 법칙:**
```
!(A && B)  ==  !A || !B
!(A || B)  ==  !A && !B
```

쉽게 기억하기: **"NOT을 분배하면 AND↔OR이 바뀐다!"**

```java
// 원래 코드
if (!(age >= 18 && hasID)) { ... }

// De Morgan 적용
if (age < 18 || !hasID) { ... }
// !(age >= 18) → age < 18
// &&가 ||로 바뀜
```

왜 필요한가?
1. AP 시험 MCQ에서 "다음 중 동일한 조건은?" 문제가 나옴
2. 복잡한 조건을 단순하게 다시 쓸 때
3. `!`의 범위를 분배할 때

**관련 토픽:** 2.6 Comparing Boolean Expressions (De Morgan's Laws)

---

### Q29. "`for` 루프랑 `while` 루프 차이가 뭐예요?"

**짧은 답변:** `for`는 "몇 번 반복할지 아는 경우", `while`은 "언제 끝날지 모르는 경우"에 주로 써요.

**자세한 설명:**

```java
// for: 횟수가 정해져 있을 때
for (int i = 0; i < 5; i++) {
    System.out.println(i);  // 0, 1, 2, 3, 4
}

// while: 조건이 충족될 때까지
int num = 1;
while (num < 100) {
    num *= 2;  // 1, 2, 4, 8, 16, 32, 64, 128에서 멈춤
}
```

for 루프의 구조:
```java
for (초기화; 조건; 업데이트) {
    // 반복할 코드
}
// ↓ while로 변환하면
초기화;
while (조건) {
    // 반복할 코드
    업데이트;
}
```

실제로는 어떤 걸 쓰든 동일하게 작동할 수 있지만, 가독성을 위해:
- 배열/리스트 순회 → `for`
- 사용자 입력 대기, 조건 충족까지 → `while`

**관련 토픽:** 2.7 While Loops, 2.8 For Loops

---

### Q30. "무한루프에 빠지면 어떡해요?"

**짧은 답변:** Ctrl+C로 프로그램을 강제 종료하세요. 그리고 루프 조건이 왜 false가 안 되는지 확인하세요.

**자세한 설명:**

무한루프는 조건이 영원히 true인 경우 발생해요:

```java
// 무한루프 예시 1: 업데이트 빠뜨림
int i = 0;
while (i < 10) {
    System.out.println(i);
    // i++; 을 빠뜨림! i는 계속 0
}

// 무한루프 예시 2: 조건이 항상 참
while (true) {
    // 여기서 빠져나갈 방법이 없음!
}

// 무한루프 예시 3: 방향이 반대
for (int i = 10; i > 0; i++) {  // i++면 영원히 > 0
    System.out.println(i);
}
```

무한루프 방지 체크리스트:
1. 루프 변수가 조건에 가까워지는 방향으로 변하는가?
2. 업데이트 문이 빠지진 않았는가?
3. 조건이 false가 될 수 있는 경우가 있는가?

**관련 토픽:** 2.7 While Loops, 2.8 For Loops

---

### Q31. "off-by-one이 뭐예요?"

**짧은 답변:** 루프가 1번 더 돌거나 1번 덜 도는 실수예요. 경계값(`<` vs `<=`, `0` vs `1`)을 잘못 설정하면 생겨요.

**자세한 설명:**

```java
// 1부터 10까지 출력하고 싶은데...
for (int i = 1; i < 10; i++) {
    System.out.print(i + " ");
}
// 출력: 1 2 3 4 5 6 7 8 9  ← 10이 빠짐! (off-by-one)

// 수정: < 를 <= 로
for (int i = 1; i <= 10; i++) {
    System.out.print(i + " ");
}
// 출력: 1 2 3 4 5 6 7 8 9 10 ✅
```

자주 발생하는 상황:
```java
String s = "Hello"; // 길이 5, 인덱스 0~4
// 인덱스 범위: 0 이상, s.length() 미만
for (int i = 0; i <= s.length(); i++) {  // ❌ i=5일 때 에러!
    // s.substring(i, i+1) → StringIndexOutOfBoundsException
}
for (int i = 0; i < s.length(); i++) {   // ✅ 올바름
    // ...
}
```

팁: "0부터 시작하면 `<` length, 1부터 시작하면 `<=` length"

**관련 토픽:** 2.8 For Loops, 2.9 Algorithms, 4.4 Array Traversals

---

### Q32. "enhanced for가 뭐예요? 일반 for랑 뭐가 달라요?"

**짧은 답변:** `for (타입 변수 : 배열/리스트)` 형태로, 인덱스 없이 원소를 하나씩 꺼내는 간편한 루프예요.

**자세한 설명:**

```java
int[] nums = {10, 20, 30, 40};

// 일반 for 루프
for (int i = 0; i < nums.length; i++) {
    System.out.println(nums[i]);
}

// enhanced for 루프 (for-each)
for (int n : nums) {
    System.out.println(n);
}
// 둘 다 같은 결과: 10, 20, 30, 40
```

**enhanced for의 한계:**
- 인덱스를 모름 → "몇 번째인지" 알 수 없음
- 원소를 수정할 수 없음 (배열의 값을 바꾸는 게 안 됨)
- 뒤에서부터 순회 불가

```java
// ❌ enhanced for로는 못 하는 것
for (int n : nums) {
    n = n * 2;  // 원본 배열은 안 바뀜!
}

// ✅ 값을 바꾸려면 일반 for 사용
for (int i = 0; i < nums.length; i++) {
    nums[i] = nums[i] * 2;  // 원본 배열 변경됨
}
```

**관련 토픽:** 4.4 Array Traversals, 4.9 ArrayList Traversals

---

### Q33. "중첩 루프는 왜 이해가 안 돼요?"

**짧은 답변:** 바깥 루프가 1번 돌 때마다 안쪽 루프가 **처음부터 끝까지** 다 돌아요. 시계의 시침과 분침처럼요.

**자세한 설명:**

시계를 생각해보세요:
- 시침(바깥 루프)이 1에서 12까지 갈 때
- 분침(안쪽 루프)은 매번 0에서 59까지 **전부** 돌아요

```java
for (int i = 1; i <= 3; i++) {        // 바깥: 1, 2, 3
    for (int j = 1; j <= 4; j++) {    // 안쪽: 1, 2, 3, 4
        System.out.print("(" + i + "," + j + ") ");
    }
    System.out.println();  // 줄바꿈
}
```
출력:
```
(1,1) (1,2) (1,3) (1,4)
(2,1) (2,2) (2,3) (2,4)
(3,1) (3,2) (3,3) (3,4)
```

총 실행 횟수: 3 × 4 = 12번

**이해하는 팁:** 손으로 직접 표를 그려보세요!

| i | j | 출력 |
|---|---|------|
| 1 | 1 | (1,1) |
| 1 | 2 | (1,2) |
| 1 | 3 | (1,3) |
| 1 | 4 | (1,4) |
| 2 | 1 | (2,1) |
| ... | ... | ... |

**관련 토픽:** 2.11 Nested Iteration, 4.12 2D Array Traversals

---

## 🔹 OOP (7개)

---

### Q34. "클래스가 뭐예요? 왜 필요해요?"

**짧은 답변:** 클래스는 **설계도(blueprint)**예요. "학생"이라는 설계도가 있으면, 그걸로 여러 학생 객체를 만들 수 있어요.

**자세한 설명:**

클래스는 "이런 종류의 것은 이런 정보를 가지고, 이런 일을 할 수 있어"라고 정의하는 거예요.

```java
// 클래스 = 설계도
public class Student {
    // 속성 (데이터)
    private String name;
    private int grade;

    // 생성자 (만드는 방법)
    public Student(String name, int grade) {
        this.name = name;
        this.grade = grade;
    }

    // 메서드 (할 수 있는 일)
    public String getName() {
        return name;
    }
}
```

왜 필요한가? → 관련된 데이터와 기능을 한 곳에 묶어서 정리정돈!

빵틀(클래스)로 빵(객체)을 찍어내는 거예요. 빵틀 하나로 같은 모양의 빵을 여러 개 만들 수 있죠.

**관련 토픽:** 3.1 Abstraction, 3.3 Anatomy of a Java Class

---

### Q35. "객체가 뭐예요? 클래스랑 뭐가 달라요?"

**짧은 답변:** 클래스가 설계도면, 객체는 그 설계도로 **실제로 만든 것**이에요. 클래스 하나로 객체는 여러 개 만들 수 있어요.

**자세한 설명:**

```java
// Student = 클래스 (설계도)
// kim, park = 객체 (실제 인스턴스)
Student kim = new Student("김철수", 11);
Student park = new Student("박영희", 12);
```

| 비유 | 클래스 | 객체 |
|------|--------|------|
| 빵틀과 빵 | 빵틀 | 빵 |
| 도면과 건물 | 건축 도면 | 실제 건물 |
| 붕어빵 틀 | 틀 | 각각의 붕어빵 |

`kim`과 `park`은 같은 설계도(Student)로 만들었지만, 각각 다른 이름과 학년을 가진 **별개의 객체**예요.

객체를 만드는 것을 **인스턴스화(instantiation)**라고 하고, `new` 키워드를 사용해요.

**관련 토픽:** 1.12 Objects, 1.13 Constructors

---

### Q36. "`private`은 왜 써요? `public`이 편하잖아요."

**짧은 답변:** 데이터를 보호하려고요. 아무나 값을 막 바꾸면 프로그램이 엉망이 될 수 있어요. 이걸 **캡슐화(encapsulation)**라 해요.

**자세한 설명:**

```java
// private을 안 쓰면?
public class BankAccount {
    public double balance;  // 누구나 접근 가능
}

BankAccount acc = new BankAccount();
acc.balance = -1000000;  // 잔고를 음수로?! 말이 안 됨!

// private + 메서드로 보호
public class BankAccount {
    private double balance;  // 외부에서 직접 접근 불가

    public void deposit(double amount) {
        if (amount > 0) {           // 검증!
            balance += amount;
        }
    }

    public double getBalance() {
        return balance;             // 읽기만 허용
    }
}
```

비유: 은행 금고를 아무나 열 수 있으면 안 되잖아요. 창구(메서드)를 통해서만 입출금하는 거예요.

AP 시험에서: 인스턴스 변수는 **항상 `private`**, 메서드는 보통 `public`이에요.

**관련 토픽:** 3.8 Scope and Access, 3.3 Anatomy of a Java Class

---

### Q37. "생성자가 뭐예요? 메서드랑 뭐가 달라요?"

**짧은 답변:** 생성자는 객체를 **만들 때** 자동으로 호출되는 특별한 메서드예요. 반환 타입이 없고, 클래스 이름과 같아요.

**자세한 설명:**

```java
public class Dog {
    private String name;
    private int age;

    // 생성자: 클래스 이름과 같고, 반환 타입 없음!
    public Dog(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // 일반 메서드: 반환 타입 있음
    public String getName() {
        return name;
    }
}

// 생성자 호출 (new와 함께)
Dog myDog = new Dog("멍멍이", 3);
```

생성자 vs 메서드:

| | 생성자 | 메서드 |
|---|---|---|
| 이름 | 클래스 이름과 동일 | 자유 |
| 반환 타입 | **없음** (void도 아님!) | 있음 (void 포함) |
| 호출 시점 | `new`로 객체 만들 때 | 객체 만든 후 아무 때나 |
| 용도 | 초기화 | 기능 수행 |

**관련 토픽:** 1.13 Constructors, 3.4 Writing Constructors, 3.5 Methods

---

### Q38. "`this`가 뭐예요?"

**짧은 답변:** "나 자신(이 객체)"을 가리키는 키워드예요. 매개변수 이름과 인스턴스 변수 이름이 같을 때 구분하려고 써요.

**자세한 설명:**

```java
public class Student {
    private String name;  // 인스턴스 변수

    public Student(String name) {  // 매개변수도 name!
        this.name = name;  // this.name = 인스턴스 변수, name = 매개변수
    }

    public void introduce() {
        System.out.println("저는 " + this.name + "입니다.");
        // this를 생략해도 되지만, 명확하게 쓰는 게 좋아요
    }
}
```

비유: 자기소개할 때 "**제** 이름은 ○○입니다"에서 "제"와 같아요. "이 객체의 name"이라는 뜻이에요.

`this`가 반드시 필요한 경우: 매개변수 이름과 인스턴스 변수 이름이 같을 때!
```java
// this가 없으면?
public Student(String name) {
    name = name;  // 둘 다 매개변수! 인스턴스 변수는 안 바뀜!
}
```

**관련 토픽:** 3.9 this Keyword, 3.4 Writing Constructors

---

### Q39. "`static`이 뭐예요?"

**짧은 답변:** 객체가 아니라 **클래스 자체**에 속하는 거예요. 객체를 안 만들어도 쓸 수 있어요.

**자세한 설명:**

```java
public class MathHelper {
    // static 메서드: 클래스 이름으로 바로 호출
    public static int add(int a, int b) {
        return a + b;
    }
}

// 객체 안 만들어도 됨!
int result = MathHelper.add(3, 5);  // 8
```

`static` vs 일반(instance):

| | static | instance |
|---|---|---|
| 소속 | 클래스 | 각 객체 |
| 호출 | `클래스이름.메서드()` | `객체.메서드()` |
| 예시 | `Math.abs(-5)` | `str.length()` |
| 객체 필요? | 불필요 | 필요 |

이미 쓰고 있었어요!
```java
Math.random()            // static! Math 객체 안 만들었죠?
Math.abs(-5)             // static!
System.out.println()     // out은 System의 static 변수!
```

**관련 토픽:** 1.10 Calling Class Methods, 3.7 static Variables and Methods

---

### Q40. "`void`가 뭐예요?"

**짧은 답변:** "이 메서드는 아무것도 돌려주지 않는다"는 뜻이에요. 일만 하고 결과를 반환하지 않아요.

**자세한 설명:**

```java
// void: 결과를 돌려주지 않음 (일만 함)
public void sayHello() {
    System.out.println("Hello!");
    // return 없음 (또는 return; 만 가능)
}

// 반환 타입 있음: 결과를 돌려줌
public int add(int a, int b) {
    return a + b;  // int 값을 돌려줌
}
```

비유:
- `void` 메서드 = 배달원이 택배를 놓고 감 (영수증 안 줌)
- 반환 메서드 = 가게에서 물건을 사면 물건을 돌려받음

```java
// void 메서드는 변수에 저장 불가
// int x = sayHello();  // ❌ 에러!

// 반환 메서드는 변수에 저장 가능
int sum = add(3, 5);    // ✅ sum = 8
```

**관련 토픽:** 3.5 Methods, 1.9 Method Signatures

---

## 🔹 자료구조 (10개)

---

### Q41. "배열이랑 ArrayList 차이가 뭐예요?"

**짧은 답변:** 배열은 크기가 고정이고, ArrayList는 크기가 자동으로 늘어나요.

**자세한 설명:**

| | 배열 (Array) | ArrayList |
|---|---|---|
| 크기 | 고정 (만들 때 정함) | 가변 (자동으로 늘어남) |
| 선언 | `int[] arr = new int[5];` | `ArrayList<Integer> list = new ArrayList<>();` |
| 접근 | `arr[0]` | `list.get(0)` |
| 변경 | `arr[0] = 10;` | `list.set(0, 10);` |
| 길이 | `arr.length` (괄호 없음!) | `list.size()` (괄호 있음!) |
| 타입 | primitive OK | primitive 불가 (Wrapper 필요) |

```java
// 배열: 크기 5로 고정
int[] scores = new int[5];
scores[0] = 95;
// scores[5] = 100;  // ❌ ArrayIndexOutOfBoundsException!

// ArrayList: 크기 자유
ArrayList<Integer> scoreList = new ArrayList<>();
scoreList.add(95);     // 자동으로 추가
scoreList.add(100);    // 계속 추가 가능
```

언제 뭘 쓸까?
- 크기가 정해져 있다 → 배열
- 추가/삭제가 많다 → ArrayList

**관련 토픽:** 4.3 Array Creation, 4.8 ArrayList Methods

---

### Q42. "배열 인덱스가 왜 0부터 시작해요?"

**짧은 답변:** 컴퓨터가 메모리에서 위치를 계산할 때 "시작점에서 얼마나 떨어져 있나(offset)"로 따지기 때문이에요.

**자세한 설명:**

```java
int[] arr = {10, 20, 30, 40, 50};
//          [0]  [1]  [2]  [3]  [4]  ← 인덱스

System.out.println(arr[0]);  // 10 (첫 번째 원소)
System.out.println(arr[4]);  // 50 (마지막 원소)
// System.out.println(arr[5]);  // ❌ 에러! 범위 초과
```

기억할 것:
- 첫 번째 원소: `arr[0]`
- 마지막 원소: `arr[arr.length - 1]`
- 유효 인덱스: `0` ~ `length - 1`

처음엔 어색하지만 금방 익숙해져요! 거의 모든 프로그래밍 언어가 0부터 시작해요.

**관련 토픽:** 4.3 Array Creation and Access

---

### Q43. "enhanced for에서 왜 배열을 못 바꿔요?"

**짧은 답변:** enhanced for의 변수는 원소의 **복사본**이에요. 복사본을 바꿔도 원본은 안 바뀌어요.

**자세한 설명:**

```java
int[] nums = {1, 2, 3, 4, 5};

// enhanced for: 복사본을 바꾸는 것!
for (int n : nums) {
    n = n * 2;  // n은 복사본! 원본 배열 안 바뀜!
}
System.out.println(Arrays.toString(nums));
// [1, 2, 3, 4, 5] ← 그대로!

// 일반 for: 원본을 직접 바꿈
for (int i = 0; i < nums.length; i++) {
    nums[i] = nums[i] * 2;  // 원본 직접 수정!
}
System.out.println(Arrays.toString(nums));
// [2, 4, 6, 8, 10] ← 바뀜!
```

비유: 사진(복사본)에 낙서해도 원본 사진은 안 바뀌는 것과 같아요.

**주의:** 참조 타입 객체의 배열에서는 enhanced for로도 객체의 **내부 상태**를 바꿀 수 있어요 (원소 자체를 교체하는 건 안 됨).

**관련 토픽:** 4.4 Array Traversals, 4.9 ArrayList Traversals

---

### Q44. "ArrayList에서 remove하면 왜 뒤가 밀려요?"

**짧은 답변:** ArrayList는 연속된 공간이라, 중간을 빼면 뒤의 원소들이 앞으로 한 칸씩 당겨져요.

**자세한 설명:**

```java
ArrayList<String> list = new ArrayList<>();
list.add("A");  // [A]
list.add("B");  // [A, B]
list.add("C");  // [A, B, C]
list.add("D");  // [A, B, C, D]

list.remove(1);  // 인덱스 1("B") 제거
// [A, C, D]  ← C와 D가 앞으로 밀림!
// 원래 인덱스 2였던 C가 이제 인덱스 1!
```

**순회하면서 remove할 때 주의!**

```java
// ❌ 잘못된 방법: 원소를 건너뜀!
for (int i = 0; i < list.size(); i++) {
    if (list.get(i).equals("제거대상")) {
        list.remove(i);
        // 뒤가 밀려서 다음 원소가 i로 오는데, i++로 건너뜀!
    }
}

// ✅ 해결법 1: 뒤에서부터 순회
for (int i = list.size() - 1; i >= 0; i--) {
    if (list.get(i).equals("제거대상")) {
        list.remove(i);  // 앞쪽은 영향 없음!
    }
}

// ✅ 해결법 2: remove 후 i-- (또는 i를 증가시키지 않기)
```

AP 시험에서 자주 나오는 함정! 꼭 기억하세요.

**관련 토픽:** 4.8 ArrayList Methods, 4.9 ArrayList Traversals, 4.10 ArrayList Algorithms

---

### Q45. "`ArrayList<Integer>`에서 왜 `int` 안 되고 `Integer`를 써요?"

**짧은 답변:** ArrayList는 객체만 담을 수 있어서, `int` 대신 그 객체 버전인 `Integer`(래퍼 클래스)를 써야 해요.

**자세한 설명:**

| Primitive | Wrapper Class |
|---|---|
| `int` | `Integer` |
| `double` | `Double` |
| `boolean` | `Boolean` |

```java
// ArrayList<int> list = ...;    // ❌ 에러! primitive 불가
ArrayList<Integer> list = new ArrayList<>();

// 하지만 넣고 뺄 때는 int 그냥 써도 됨 (autoboxing)
list.add(5);           // int 5 → Integer 5 (자동 변환!)
int num = list.get(0); // Integer 5 → int 5 (자동 변환!)
```

**Autoboxing/Unboxing:**
- Autoboxing: `int` → `Integer` (자동으로 포장)
- Unboxing: `Integer` → `int` (자동으로 꺼냄)

Java가 알아서 해주니까, 선언할 때만 `Integer`를 쓰고 나머지는 `int`처럼 쓰면 돼요!

**관련 토픽:** 4.7 Wrapper Classes, 4.8 ArrayList Methods

---

### Q46. "2D 배열이 뭐예요?"

**짧은 답변:** 배열 안에 배열이 있는 거예요. 행(row)과 열(column)이 있는 표/격자라고 생각하면 돼요.

**자세한 설명:**

```java
// 3행 4열 2D 배열
int[][] grid = {
    {1, 2, 3, 4},     // row 0
    {5, 6, 7, 8},     // row 1
    {9, 10, 11, 12}   // row 2
};

System.out.println(grid[0][2]);     // 3 (0행 2열)
System.out.println(grid[2][3]);     // 12 (2행 3열)
System.out.println(grid.length);    // 3 (행 수)
System.out.println(grid[0].length); // 4 (열 수)
```

시각적으로:
```
        열0  열1  열2  열3
행0  [  1,   2,   3,   4  ]
행1  [  5,   6,   7,   8  ]
행2  [  9,  10,  11,  12  ]
```

접근: `grid[행][열]` → "행 먼저, 열 나중"

**관련 토픽:** 4.11 2D Array Creation and Access, 4.12 2D Array Traversals

---

### Q47. "row-major, column-major가 뭐예요?"

**짧은 답변:** 2D 배열을 순회할 때, 행을 먼저 다 보는 게 row-major, 열을 먼저 다 보는 게 column-major예요.

**자세한 설명:**

```java
int[][] grid = {
    {1, 2, 3},
    {4, 5, 6}
};

// Row-major: 행 우선 (가장 일반적!)
// 바깥 = row, 안쪽 = col
for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[r].length; c++) {
        System.out.print(grid[r][c] + " ");
    }
}
// 출력: 1 2 3 4 5 6 (→ 방향으로 읽기)

// Column-major: 열 우선
// 바깥 = col, 안쪽 = row
for (int c = 0; c < grid[0].length; c++) {
    for (int r = 0; r < grid.length; r++) {
        System.out.print(grid[r][c] + " ");
    }
}
// 출력: 1 4 2 5 3 6 (↓ 방향으로 읽기)
```

AP 시험에서: "이 코드의 출력은?" 문제에서 순회 순서를 물어봐요. 바깥 루프가 row면 row-major!

**관련 토픽:** 4.12 2D Array Traversals, 4.13 2D Array Algorithms

---

### Q48. "재귀가 뭐예요? 왜 자기 자신을 호출해요?"

**짧은 답변:** 메서드가 자기 자신을 호출하는 거예요. 큰 문제를 같은 형태의 작은 문제로 쪼개서 풀어요.

**자세한 설명:**

비유: 러시아 인형! 큰 인형 안에 같은 모양의 작은 인형이 있고, 그 안에 더 작은 인형이... 마지막에 가장 작은 인형(base case)에 도달하면 끝!

```java
// 팩토리얼: 5! = 5 × 4 × 3 × 2 × 1
public static int factorial(int n) {
    if (n == 1) {           // Base case (기저 조건) - 멈추는 조건!
        return 1;
    }
    return n * factorial(n - 1);  // Recursive case - 자기 자신 호출!
}

// factorial(4) → 4 * factorial(3)
//                    → 3 * factorial(2)
//                          → 2 * factorial(1)
//                                → 1 (base case!)
// 거꾸로: 1 → 2*1=2 → 3*2=6 → 4*6=24
```

재귀의 2가지 필수 요소:
1. **Base case**: 더 이상 호출하지 않는 조건 (이게 없으면 무한 재귀 → StackOverflowError!)
2. **Recursive case**: 문제를 더 작게 만들어서 자기를 다시 호출

**관련 토픽:** 4.16 Recursion, 4.17 Recursive Searching and Sorting

---

### Q49. "File이랑 Scanner가 뭐예요?"

**짧은 답변:** `File`은 파일을 가리키는 객체이고, `Scanner`는 그 파일의 내용을 읽는 도구예요.

**자세한 설명:**

2025-26 커리큘럼에서 새로 추가된 내용이에요!

```java
import java.io.File;
import java.util.Scanner;
import java.io.IOException;

public class FileReader {
    public static void main(String[] args) throws IOException {
        // 1. File 객체 만들기 (파일을 가리키는 이름표)
        File myFile = new File("data.txt");

        // 2. Scanner로 파일 연결 (파일을 읽는 돋보기)
        Scanner reader = new Scanner(myFile);

        // 3. 한 줄씩 읽기
        while (reader.hasNextLine()) {
            String line = reader.nextLine();
            System.out.println(line);
        }

        reader.close();  // 다 읽으면 닫기!
    }
}
```

비유:
- `File` = 도서관에서 책의 위치를 알려주는 카드
- `Scanner` = 그 책을 실제로 펼쳐서 읽는 행위

**관련 토픽:** 4.6 Using Text Files

---

### Q50. "`throws IOException`은 왜 써야 해요?"

**짧은 답변:** 파일이 없거나 읽을 수 없는 상황이 발생할 수 있다고 Java에게 알려주는 거예요.

**자세한 설명:**

파일을 다룰 때는 항상 "이 파일이 진짜 있을까? 읽을 수 있을까?"라는 불확실성이 있어요. Java는 이런 위험한 상황을 미리 처리하도록 강제해요.

```java
// 방법 1: throws로 떠넘기기 (AP CSA에서 주로 사용)
public static void main(String[] args) throws IOException {
    Scanner reader = new Scanner(new File("data.txt"));
    // ...
}

// 방법 2: try-catch로 직접 처리 (AP CSA 범위는 아님)
public static void main(String[] args) {
    try {
        Scanner reader = new Scanner(new File("data.txt"));
        // ...
    } catch (IOException e) {
        System.out.println("파일을 열 수 없습니다!");
    }
}
```

AP 시험에서는 `throws IOException`만 쓸 줄 알면 돼요. "이 메서드에서 IOException이 발생할 수 있다"는 선언이에요.

`import java.io.IOException;` 또는 `import java.io.*;`도 필요해요!

**관련 토픽:** 4.6 Using Text Files

---

---

# Part 2: 개념 선수 지식 맵

> "이걸 배우려면 먼저 뭘 알아야 하나?"
>
> 형식: `선수 → [현재 토픽] → 후속`

---

## Unit 1: Using Objects and Methods

```
(없음)
  → [1.1 Introduction to Algorithms, Programming, and Compilers]
  → 1.2, 1.3

1.1 Introduction
  → [1.2 Variables and Data Types]
  → 1.3, 1.4, 1.5

1.2 Variables
  → [1.3 Expressions and Output]
  → 1.4, 1.5, 1.6

1.2 Variables, 1.3 Expressions
  → [1.4 Assignment and Input]
  → 1.6, 2.2

1.2 Variables, 1.3 Expressions
  → [1.5 Casting and Ranges of Values]
  → 1.6, 2.9

1.3 Expressions, 1.4 Assignment
  → [1.6 Compound Assignment Operators]
  → 2.7, 2.8

1.1 Introduction
  → [1.7 APIs and Libraries]
  → 1.10, 1.11

1.1 Introduction
  → [1.8 Documentation with Comments and Preconditions]
  → 3.4, 3.5

1.3 Expressions, 1.7 APIs
  → [1.9 Method Signatures]
  → 1.10, 1.14, 3.5

1.7 APIs, 1.9 Method Signatures
  → [1.10 Calling Class Methods]
  → 1.11, 3.7

1.10 Class Methods
  → [1.11 Using the Math Class]
  → 2.9

1.2 Variables
  → [1.12 Objects - Instances of Classes]
  → 1.13, 1.14, 3.3

1.12 Objects
  → [1.13 Creating and Initializing Objects: Constructors]
  → 1.14, 3.4

1.12 Objects, 1.13 Constructors, 1.9 Method Signatures
  → [1.14 Calling Instance Methods]
  → 1.15, 4.8

1.12 Objects, 1.14 Instance Methods
  → [1.15 Strings]
  → 2.5, 2.10
```

---

## Unit 2: Selection and Iteration

```
1.2 Variables, 1.3 Expressions
  → [2.1 Algorithms with Selection and Repetition]
  → 2.2, 2.3, 2.7

1.2 Variables, 1.3 Expressions
  → [2.2 Boolean Expressions]
  → 2.3, 2.5, 2.7

2.2 Boolean Expressions
  → [2.3 if Statements]
  → 2.4, 2.5

2.3 if Statements
  → [2.4 Nested if Statements]
  → 2.9

2.2 Boolean Expressions, 2.3 if Statements
  → [2.5 Compound Boolean Expressions]
  → 2.6, 2.9

2.5 Compound Boolean Expressions
  → [2.6 Comparing Boolean Expressions (De Morgan's Laws)]
  → 2.9

2.2 Boolean Expressions, 1.2 Variables, 1.6 Compound Assignment
  → [2.7 While Loops]
  → 2.8, 2.9, 2.11

2.7 While Loops
  → [2.8 For Loops]
  → 2.9, 2.11, 4.4

2.3~2.8 (조건문+루프 전체)
  → [2.9 Implementing Selection and Iteration Algorithms]
  → 4.5, 4.10

1.15 Strings, 2.7 While/2.8 For Loops
  → [2.10 Implementing String Algorithms]
  → 4.5

2.8 For Loops
  → [2.11 Nested Iteration]
  → 4.12, 4.13

2.7 While Loops, 2.8 For Loops
  → [2.12 Informal Runtime Analysis of Loops]
  → 4.14, 4.15
```

---

## Unit 3: Class Creation

```
1.12 Objects, 1.1 Introduction
  → [3.1 Abstraction and Program Design]
  → 3.2, 3.3

3.1 Abstraction
  → [3.2 Impact of Program Design]
  → 3.3

1.12 Objects, 1.14 Instance Methods
  → [3.3 Anatomy of a Java Class]
  → 3.4, 3.5, 3.7, 3.8

3.3 Class Anatomy, 1.13 Constructors
  → [3.4 Writing Constructors]
  → 3.9

3.3 Class Anatomy, 1.9 Method Signatures
  → [3.5 Methods: How to Write Them]
  → 3.6

3.5 Methods, 1.12 Objects
  → [3.6 Methods: Passing and Returning References]
  → 4.8

1.10 Class Methods, 3.3 Class Anatomy
  → [3.7 Class (static) Variables and Methods]
  → main 메서드 이해

3.3 Class Anatomy, 1.2 Variables
  → [3.8 Scope and Access]
  → 3.9

3.4 Constructors, 3.8 Scope
  → [3.9 this Keyword]
  → (Unit 3 마무리)
```

---

## Unit 4: Data Collections

```
3.1 Abstraction
  → [4.1 Ethical and Social Issues Around Data Collection]
  → 4.2

4.1 Ethics
  → [4.2 Data Sets]
  → 4.3, 4.6

1.2 Variables, 2.8 For Loops
  → [4.3 Array Creation and Access]
  → 4.4, 4.5, 4.11

4.3 Arrays, 2.8 For Loops
  → [4.4 Array Traversals]
  → 4.5, 4.9

4.4 Array Traversals, 2.9 Algorithms
  → [4.5 Implementing Array Algorithms]
  → 4.10, 4.14, 4.15

4.2 Data Sets, 1.7 APIs, 1.13 Constructors
  → [4.6 Using Text Files]
  → 4.5, 4.10

1.2 Variables, 1.12 Objects
  → [4.7 Wrapper Classes - Integer and Double]
  → 4.8

1.12 Objects, 1.14 Instance Methods, 4.7 Wrapper Classes
  → [4.8 ArrayList and its Methods]
  → 4.9, 4.10

4.8 ArrayList, 4.4 Array Traversals (개념 유사)
  → [4.9 ArrayList Traversals]
  → 4.10

4.9 ArrayList Traversals, 4.5 Array Algorithms
  → [4.10 Implementing ArrayList Algorithms]
  → 4.14, 4.15

4.3 Arrays, 2.11 Nested Iteration
  → [4.11 2D Array Creation and Access]
  → 4.12, 4.13

4.11 2D Arrays, 2.11 Nested Iteration
  → [4.12 2D Array Traversals: Nested Loops]
  → 4.13

4.12 2D Traversals, 4.5 Array Algorithms
  → [4.13 Implementing 2D Array Algorithms]
  → (2D 마무리)

4.4 Array Traversals, 2.9 Algorithms, 2.12 Runtime Analysis
  → [4.14 Searching Algorithms]
  → 4.17

4.4 Array Traversals, 2.9 Algorithms, 2.12 Runtime Analysis
  → [4.15 Sorting Algorithms]
  → 4.17

3.5 Methods
  → [4.16 Recursion]
  → 4.17

4.16 Recursion, 4.14 Searching, 4.15 Sorting
  → [4.17 Recursive Searching and Sorting]
  → (Unit 4 마무리)
```

---

## Unit 5: Inheritance (보너스 - 시험 범위 아님)

```
3.3 Class Anatomy, 3.5 Methods
  → [5.1 Inheritance, Superclass, Subclass]
  → 5.2, 5.3

5.1 Inheritance, 3.4 Constructors
  → [5.2 Inheritance and Constructors]
  → 5.4

5.1 Inheritance, 3.5 Methods
  → [5.3 Overriding Methods]
  → 5.6

5.2 Constructors, 5.3 Overriding
  → [5.4 super Keyword]
  → 5.5

5.1~5.4 전체
  → [5.5 Inheritance Hierarchies]
  → 5.6

5.3 Overriding, 5.5 Hierarchies
  → [5.6 Polymorphism]
  → 5.7

5.1~5.6 전체
  → [5.7 Object Superclass]
  → (Unit 5 마무리)
```

---

---

# Part 3: "처음 1시간" 생존 가이드

> Java를 난생처음 보는 학생이 **이것만 알면** 코드를 읽을 수 있는 10가지 규칙

---

## 규칙 1: 모든 코드는 클래스 안에 산다

```java
public class 파일이름 {
    // 모든 코드는 여기 안에!
}
```

- 파일 이름과 클래스 이름이 **정확히** 같아야 해요
- `Dog.java` 파일 안에는 `public class Dog`

---

## 규칙 2: 프로그램은 main에서 시작한다

```java
public static void main(String[] args) {
    // 프로그램이 여기서 시작!
    // 위에서 아래로, 한 줄씩 실행
}
```

- 이 줄은 지금 외우세요. 의미는 나중에 배워요
- 모든 Java 프로그램의 출발점

---

## 규칙 3: 모든 문장은 세미콜론으로 끝난다

```java
int x = 5;                      // ← 세미콜론!
System.out.println("Hello");    // ← 세미콜론!

if (x > 0) {    // ← 여기는 세미콜론 없음! (제어문 헤더)
    // ...
}
```

- 빼먹으면 에러. 가장 흔한 실수 1위
- `if`, `for`, `while`, 클래스/메서드 선언 뒤에는 안 붙임

---

## 규칙 4: 변수는 "이름표 붙은 상자"다

```java
int age = 17;          // int 상자에 17을 넣고, "age"라는 이름표를 붙임
double gpa = 3.5;      // 소수점 상자에 3.5
String name = "Kim";   // 글자 상자에 "Kim"
boolean pass = true;   // 참/거짓 상자에 true
```

- `int` = 정수, `double` = 소수, `String` = 문자열, `boolean` = 참/거짓
- `=`는 "같다"가 아니라 **"넣어라"**

---

## 규칙 5: 출력은 System.out.println

```java
System.out.println("Hello!");     // Hello! 출력하고 줄바꿈
System.out.println(3 + 4);       // 7 출력
System.out.println("답: " + 7);  // 답: 7 출력
```

- `println` = 출력 + 줄바꿈
- `print` = 출력만 (줄바꿈 없음)
- 문자열은 반드시 큰따옴표 `"` 로 감싸기

---

## 규칙 6: 중괄호는 "묶음 표시"다

```java
public class Dog {                    // 클래스 묶음 시작
    public static void main(...) {    // 메서드 묶음 시작
        if (true) {                   // if 묶음 시작
        }                             // if 묶음 끝
    }                                 // 메서드 묶음 끝
}                                     // 클래스 묶음 끝
```

- 여는 `{`와 닫는 `}`는 항상 짝이 맞아야 함
- 들여쓰기로 어떤 묶음에 속하는지 눈으로 확인

---

## 규칙 7: if는 "만약 ~라면"

```java
if (조건) {
    // 조건이 참이면 실행
} else {
    // 조건이 거짓이면 실행
}
```

```java
if (score >= 90) {
    System.out.println("A");
} else if (score >= 80) {
    System.out.println("B");
} else {
    System.out.println("C");
}
```

- 조건에는 `==`(같다), `!=`(다르다), `<`, `>`, `<=`, `>=` 사용
- `=`(대입)과 `==`(비교) 헷갈리지 않기!

---

## 규칙 8: for는 "N번 반복해"

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
// 출력: 0, 1, 2, 3, 4 (5번 반복)
```

읽는 법:
1. `int i = 0` → i를 0으로 시작
2. `i < 5` → i가 5보다 작은 동안 반복
3. `i++` → 매 반복 후 i를 1 증가
4. 중괄호 안의 코드를 실행

---

## 규칙 9: 메서드는 "이름 붙은 기능"

```java
// 메서드 정의 (만들기)
public static int add(int a, int b) {
    return a + b;
}

// 메서드 호출 (쓰기)
int result = add(3, 5);  // result = 8
```

- `void` = 돌려주는 게 없음
- `return` = 결과를 돌려줌
- 메서드 이름 뒤에는 항상 소괄호 `()`

---

## 규칙 10: 에러 메시지를 읽어라

에러가 나면 당황하지 말고, **마지막 줄**부터 읽으세요:

| 에러 메시지 | 의미 | 해결 |
|---|---|---|
| `;` expected | 세미콜론 빠짐 | 해당 줄에 `;` 추가 |
| cannot find symbol | 변수/메서드 이름 오타 | 철자 확인 |
| incompatible types | 타입이 안 맞음 | 타입 확인/캐스팅 |
| ArrayIndexOutOfBounds | 배열 범위 초과 | 인덱스 확인 |
| NullPointerException | null에 메서드 호출 | null 체크 추가 |

에러 메시지의 **줄 번호**를 보세요 → 그 줄 근처에 문제가 있어요!

---

## 요약: 처음 1시간 체크리스트

```
□ 클래스 안에 main 메서드를 쓰는 구조를 안다
□ System.out.println으로 출력할 수 있다
□ int, double, String, boolean 변수를 만들 수 있다
□ =는 대입, ==는 비교임을 안다
□ 세미콜론을 문장 끝에 붙인다
□ 중괄호의 짝을 맞출 수 있다
□ if/else로 조건 분기를 읽을 수 있다
□ for 루프가 몇 번 도는지 세 볼 수 있다
□ 메서드 호출 코드를 읽을 수 있다
□ 에러 메시지의 줄 번호를 찾을 수 있다
```

이 10가지를 알면 Java 코드를 **읽을 수** 있어요. 쓰는 건 연습하면서 자연스럽게!

---

---

## 추가 FAQ: 2025-26 시험 관련

### Q: 왜 상속(Inheritance)을 안 배우나요? 다른 AP CSA 자료에는 있던데요.

2025-26부터 AP CSA 커리큘럼이 대폭 개편되면서 **상속(Inheritance)이 시험 범위에서 완전히 제거**되었습니다. `extends`, `super`, `override`, `abstract class`, `interface` 등은 더 이상 출제되지 않습니다. 인터넷에서 검색하면 상속이 포함된 옛날 자료가 많으니 주의하세요. 2025-26 이후 자료인지 반드시 확인!

### Q: File/Scanner가 뭔가요? 파일에서 데이터를 읽는 건가요?

네! 2025-26부터 **새로 추가된 토픽**입니다. `File` 클래스로 파일을 지정하고, `Scanner` 클래스로 그 파일의 내용을 한 줄씩 읽을 수 있습니다.

```java
// 기본 패턴 (반드시 throws IOException 필요!)
public static void main(String[] args) throws IOException {
    Scanner sc = new Scanner(new File("data.txt"));
    while (sc.hasNext()) {
        String line = sc.nextLine();
        System.out.println(line);
    }
}
```

주요 메서드:
- `hasNext()` — 읽을 데이터가 남아있는지 확인
- `nextLine()` — 한 줄 전체를 String으로 읽기
- `nextInt()` — 정수 하나 읽기 (주의: 개행문자가 남음!)

### Q: 재귀(Recursion)를 직접 코드로 작성할 줄 알아야 하나요?

아니요! 2025-26부터 재귀 코드를 **직접 작성**하는 것은 시험 범위 밖입니다. MCQ에서 주어진 재귀 코드를 **읽고 추적(tracing)**하여 결과를 예측하는 문제만 나옵니다. FRQ에서는 재귀가 절대 출제되지 않습니다.

### Q: MCQ가 5지선다인가요 4지선다인가요?

2025-26부터 **4지선다(A, B, C, D)**입니다. 이전에는 5개였지만 변경되었습니다. 총 42문제, 90분, 오답 감점 없음!

---

> 이 문서는 AP CSA 2025-26 커리큘럼(CSAwesome2) 기준으로 작성되었습니다.
> 시험에 나오지 않는 Unit 5(Inheritance)는 보너스로 선수 지식 맵에만 포함되어 있습니다.
