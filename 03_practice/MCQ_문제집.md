# AP Computer Science A — MCQ 연습문제집

> Unit 1~4 | 총 119문제 | 난이도: 쉬움(E) / 보통(M) / 어려움(H)
>
> 실제 AP CSA 시험 형식 (4지선다, Java 코드 포함)

---

## Unit 1: Using Objects and Methods (39문제)

---

### 문제 1 (Unit 1 - 토픽 1.1) [E]

다음 중 Java에서 유효한 변수 선언은?

(A) `int 2ndPlace = 5;`
(B) `double my-score = 9.5;`
(C) `String class = "AP";`
(D) `boolean isValid = true;`

<details>
<summary>정답 및 해설</summary>

**정답: (D)**

(A) 변수 이름은 숫자로 시작할 수 없다. (B) 하이픈(`-`)은 변수 이름에 사용할 수 없다 (뺄셈 연산자로 해석). (C) `class`는 Java 예약어(reserved word)이므로 변수 이름으로 사용 불가. (D) `boolean` 타입 변수를 `true`로 초기화하는 올바른 선언이다.
</details>

---

### 문제 2 (Unit 1 - 토픽 1.2) [E]

```java
int x = 5;
double y = x;
System.out.println(y);
```

출력 결과는?

(A) `5`
(B) `5.0`
(C) 컴파일 에러
(D) `5.00`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`int`를 `double`에 대입하면 자동 형변환(widening conversion)이 일어난다. `int 5`가 `double 5.0`으로 변환되어 저장되고, `println`은 `double`을 출력할 때 소수점 첫째 자리까지 표시하므로 `5.0`이 출력된다.
</details>

---

### 문제 3 (Unit 1 - 토픽 1.2) [M]

```java
double d = 7.9;
int n = (int) d;
System.out.println(n);
```

출력 결과는?

(A) `7`
(B) `8`
(C) `7.9`
(D) 컴파일 에러

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

`double`을 `int`로 캐스팅하면 **소수점 이하를 버린다(truncation)**. 반올림이 아니다. `7.9`의 소수 부분 `.9`가 잘려서 `7`이 된다. 이것은 AP CSA에서 자주 출제되는 함정이다.
</details>

---

### 문제 4 (Unit 1 - 토픽 1.2) [M]

```java
int a = 17;
int b = 5;
double result = a / b;
System.out.println(result);
```

출력 결과는?

(A) `3.4`
(B) `3.0`
(C) `3`
(D) 컴파일 에러

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

**정수 나눗셈 함정**: `a / b`에서 `a`와 `b` 모두 `int`이므로 정수 나눗셈이 수행된다. `17 / 5 = 3` (소수 부분 버림). 이 `int` 값 `3`이 `double` 변수에 대입되면서 `3.0`으로 변환된다. `3.4`를 얻으려면 `(double) a / b`처럼 캐스팅해야 한다.
</details>

---

*문제 5는 CED 제외 항목(음수의 % 연산)이므로 삭제되었습니다.*

---

### 문제 6 (Unit 1 - 토픽 1.3) [E]

```java
int x = 10;
x += 3;
x *= 2;
System.out.println(x);
```

출력 결과는?

(A) `23`
(B) `26`
(C) `16`
(D) `36`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

순서대로 실행: `x = 10` → `x += 3`이면 `x = 13` → `x *= 2`이면 `x = 26`. 복합 대입 연산자는 왼쪽에서 오른쪽으로 순서대로 실행된다.
</details>

---

### 문제 7 (Unit 1 - 토픽 1.3) [M]

```java
int a = 17;
int b = 5;
a %= b;
a += 3;
b *= a;
System.out.println(a + " " + b);
```

출력 결과는?

(A) `5 25`
(B) `5 15`
(C) `5 5`
(D) `3 15`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

`a %= b` → `a = 17 % 5 = 2`. `a += 3` → `a = 2 + 3 = 5`. `b *= a` → `b = 5 * 5 = 25`. 최종: `a = 5`, `b = 25`. 복합 대입 연산자(`%=`, `+=`, `*=`)는 왼쪽 변수에 연산 결과를 다시 저장한다.
</details>

---

### 문제 8 (Unit 1 - 토픽 1.2) [H]

```java
double x = 0.1 + 0.2;
System.out.println(x == 0.3);
System.out.println(x);
```

출력 결과는?

(A) `true` 다음 줄에 `0.3`
(B) `false` 다음 줄에 `0.30000000000000004`
(C) `true` 다음 줄에 `0.30000000000000004`
(D) 컴파일 에러

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

부동소수점(floating-point) 표현의 한계로 `0.1 + 0.2`는 정확히 `0.3`이 아니라 `0.30000000000000004`가 된다. 따라서 `==` 비교 결과는 `false`이다. 이것이 실수 비교 시 `==` 대신 오차 범위(epsilon)를 사용해야 하는 이유이다.
</details>

---

### 문제 9 (Unit 1 - 토픽 1.4) [M]

```java
int x = 3;
int y = 4;
double z = (double)(x + y) / 2;
System.out.println(z);
```

출력 결과는?

(A) `3.0`
(B) `3.5`
(C) `4.0`
(D) `3`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`x + y = 7`. `(double)(x + y)`는 `7`을 `7.0`으로 캐스팅한다. 그 후 `7.0 / 2`는 실수 나눗셈이 되어 `3.5`가 된다. 만약 `(double)` 캐스팅이 없었다면 `7 / 2 = 3` (정수 나눗셈)이 되었을 것이다.
</details>

---

### 문제 10 (Unit 1 - 토픽 1.4) [E]

```java
int num = (int)(Math.random() * 6) + 1;
```

`num`에 저장될 수 있는 값의 범위는?

(A) 0에서 5까지
(B) 1에서 6까지
(C) 0에서 6까지
(D) 1에서 7까지

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`Math.random()`은 `0.0` 이상 `1.0` 미만의 `double`을 반환한다. `* 6`하면 `0.0` 이상 `6.0` 미만. `(int)` 캐스팅으로 소수점 버리면 0~5. `+ 1`하면 1~6. 이것은 주사위 굴리기를 시뮬레이션하는 표준 패턴이다.
</details>

---

### 문제 11 (Unit 1 - 토픽 1.2) [M]

```java
int a = 10;
int b = 3;
System.out.println(a % b + a / b);
```

출력 결과는?

(A) `3`
(B) `4`
(C) `4.333`
(D) `1`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`a % b = 10 % 3 = 1` (나머지). `a / b = 10 / 3 = 3` (정수 나눗셈, 소수점 버림). `1 + 3 = 4`.
</details>

---

### 문제 12 (Unit 1 - 토픽 1.3) [H]

```java
int x = 5;
x = x + x * x - x / x;
System.out.println(x);
```

출력 결과는?

(A) `29`
(B) `24`
(C) `30`
(D) `49`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

연산자 우선순위에 따라: `x * x = 25`, `x / x = 1`. 그 다음 `x + 25 - 1 = 5 + 25 - 1 = 29`. 곱셈과 나눗셈이 덧셈과 뺄셈보다 먼저 수행된다.
</details>

---

### 문제 13 (Unit 1 - 토픽 1.2) [M]

```java
double a = 9 / 4;
double b = 9.0 / 4;
double c = (double) 9 / 4;
System.out.println(a + " " + b + " " + c);
```

출력 결과는?

(A) `2.25 2.25 2.25`
(B) `2.0 2.25 2.25`
(C) `2.0 2.0 2.25`
(D) `2.25 2.25 2.0`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`9 / 4`: 둘 다 `int`이므로 정수 나눗셈 → `2`, `double`에 저장되어 `2.0`. `9.0 / 4`: 하나가 `double`이므로 실수 나눗셈 → `2.25`. `(double) 9 / 4`: `9`를 `double`로 캐스팅 후 나눗셈 → `9.0 / 4` → `2.25`. 정수 나눗셈을 피하려면 피연산자 중 하나 이상이 `double`이어야 한다.
</details>

---

### 문제 14 (Unit 1 - 토픽 1.4) [E]

다음 중 `int` 타입의 유효 범위에 대한 설명으로 올바른 것은?

(A) `int`는 약 -32,768에서 32,767까지 저장할 수 있다.
(B) `int`는 약 -2.1 billion에서 2.1 billion까지 저장할 수 있다.
(C) `int`는 소수점을 포함한 숫자를 저장할 수 있다.
(D) `int`의 크기는 운영체제에 따라 달라진다.

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

Java의 `int`는 32비트 정수로, 범위는 `-2,147,483,648`에서 `2,147,483,647`까지이다 (약 ±2.1 billion). (A)는 `short`의 범위이다. (C) `int`는 정수만 저장한다. (D) Java는 플랫폼 독립적이므로 `int`는 항상 32비트이다.
</details>

---

### 문제 15 (Unit 1 - 토픽 1.4) [H]

```java
int max = Integer.MAX_VALUE;
System.out.println(max + 1);
```

출력 결과는?

(A) `2147483648`
(B) `-2147483648`
(C) `0`
(D) 런타임 에러 (ArithmeticException)

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

**정수 오버플로우(integer overflow)**: `Integer.MAX_VALUE`는 `2147483647`이다. 여기에 1을 더하면 32비트 범위를 넘어서 **래핑(wrapping)** 이 발생하여 `Integer.MIN_VALUE`인 `-2147483648`이 된다. Java는 정수 오버플로우에 대해 예외를 발생시키지 않는다.
</details>

---

### 문제 16 (Unit 1 - 토픽 2.1) [E]

다음 중 올바른 객체 생성 문장은?

(A) `String s = new String;`
(B) `String s = new String("hello");`
(C) `String s = String("hello");`
(D) `new String s = "hello";`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

객체 생성은 `new` 키워드와 생성자 호출(괄호 포함)이 필요하다. (A) 괄호가 없다. (C) `new` 키워드가 없다. (D) 문법이 틀렸다. 참고로 `String s = "hello";`도 유효하지만 선택지에 없다.
</details>

---

### 문제 17 (Unit 1 - 토픽 2.2) [E]

```java
String s = "Computer Science";
System.out.println(s.length());
```

출력 결과는?

(A) `15`
(B) `16`
(C) `17`
(D) `14`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`"Computer Science"`는 공백 포함 16개의 문자로 구성된다. `length()` 메서드는 문자열의 총 문자 수를 반환한다. C-o-m-p-u-t-e-r(8) + 공백(1) + S-c-i-e-n-c-e(7) = 16.
</details>

---

### 문제 18 (Unit 1 - 토픽 2.7) [M]

```java
String s = "ABCDEF";
System.out.println(s.substring(2, 5));
```

출력 결과는?

(A) `BCD`
(B) `CDE`
(C) `BCDE`
(D) `CDEF`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`substring(beginIndex, endIndex)`는 `beginIndex`부터 `endIndex - 1`까지의 문자를 반환한다 (**endIndex는 포함하지 않음**). 인덱스: A=0, B=1, C=2, D=3, E=4, F=5. `substring(2, 5)` → 인덱스 2, 3, 4의 문자 → `"CDE"`. 이것은 AP CSA에서 매우 자주 출제되는 함정이다.
</details>

---

### 문제 19 (Unit 1 - 토픽 2.6) [M]

```java
String a = "hello";
String b = "hello";
String c = new String("hello");

System.out.println(a == b);
System.out.println(a == c);
System.out.println(a.equals(c));
```

출력 결과는?

(A) `true true true`
(B) `true false true`
(C) `false false true`
(D) `true false false`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

**`==` vs `equals()` 함정**: `==`는 참조(reference, 메모리 주소)를 비교하고, `equals()`는 내용(content)을 비교한다. `a`와 `b`는 String pool의 같은 객체를 참조하므로 `a == b`는 `true`. `c`는 `new`로 생성된 별도 객체이므로 `a == c`는 `false`. `a.equals(c)`는 내용이 같으므로 `true`. 문자열 비교는 항상 `equals()`를 사용해야 한다.
</details>

---

### 문제 20 (Unit 1 - 토픽 2.7) [E]

```java
String s = "Hello World";
System.out.println(s.indexOf("World"));
```

출력 결과는?

(A) `5`
(B) `6`
(C) `7`
(D) `-1`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`indexOf()` 메서드는 부분 문자열이 처음 나타나는 인덱스를 반환한다. `"Hello World"`에서 H=0, e=1, l=2, l=3, o=4, 공백=5, W=6. `"World"`는 인덱스 6에서 시작한다.
</details>

---

### 문제 21 (Unit 1 - 토픽 2.7) [M]

```java
String s = "Hello";
s.substring(1, 4);
System.out.println(s);
```

출력 결과는?

(A) `ell`
(B) `Hello`
(C) `Hllo`
(D) 컴파일 에러

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

**String은 불변(immutable)** 이다. `substring(1, 4)`은 새로운 String 객체 `"ell"`을 반환할 뿐 원본을 수정하지 않는다. 반환값을 변수에 저장하거나 출력하지 않았으므로 `s`는 그대로 `"Hello"`이다. 올바른 사용: `String t = s.substring(1, 4);` 또는 `s = s.substring(1, 4);`.
</details>

---

### 문제 22 (Unit 1 - 토픽 2.7) [M]

```java
String s = "AP Computer Science A";
System.out.println(s.substring(3, 11));
```

출력 결과는?

(A) `Computer`
(B) `Compute`
(C) `omputer `
(D) `Computer`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

인덱스: A=0, P=1, 공백=2, C=3, o=4, m=5, p=6, u=7, t=8, e=9, r=10, 공백=11. `substring(3, 11)` → 인덱스 3부터 10까지 = `"Computer"` (8글자). endIndex 11의 문자(공백)는 포함되지 않는다.
</details>

---

### 문제 23 (Unit 1 - 토픽 2.3) [E]

```java
String s = null;
System.out.println(s.length());
```

실행 결과는?

(A) `0`
(B) `null`
(C) 컴파일 에러
(D) NullPointerException

<details>
<summary>정답 및 해설</summary>

**정답: (D)**

`null` 참조에 대해 메서드를 호출하면 `NullPointerException`이 발생한다. `null`은 어떤 객체도 참조하지 않는 상태이므로 `length()` 메서드를 호출할 수 없다. 이 코드는 컴파일은 되지만 실행 시 예외가 발생한다.
</details>

---

### 문제 24 (Unit 1 - 토픽 2.4) [M]

*(참고: `Integer.valueOf()`는 Quick Reference에 없는 메서드)*

```java
Integer a = Integer.valueOf(200);
Integer b = Integer.valueOf(200);
System.out.println(a == b);
System.out.println(a.equals(b));
```

출력 결과는?

(A) `true true`
(B) `true false`
(C) `false true`
(D) `false false`

<details>
<summary>정답 및 해설</summary>

**정답: (C)**

`Integer.valueOf(200)`은 -128~127 범위 밖이므로 매번 새로운 객체를 생성한다. `==`는 참조를 비교하므로 서로 다른 객체를 가리켜 `false`. `equals()`는 값을 비교하므로 `true`. Wrapper 클래스도 객체이므로 `==` 대신 `equals()`를 사용해야 한다. (참고: `Integer.valueOf(100)`처럼 -128~127 범위에서는 캐싱으로 `==`가 `true`일 수 있다.)
</details>

---

### 문제 25 (Unit 1 - 토픽 2.5) [E]

```java
int x = 5;
Integer y = x;
int z = y;
System.out.println(z);
```

출력 결과는?

(A) `5`
(B) 컴파일 에러
(C) NullPointerException
(D) `0`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

Java는 **autoboxing** (`int` → `Integer`)과 **unboxing** (`Integer` → `int`)을 자동으로 수행한다. `Integer y = x;`에서 `5`가 `Integer` 객체로 autoboxing되고, `int z = y;`에서 다시 unboxing되어 `5`가 저장된다.
</details>

---

### 문제 26 (Unit 1 - 토픽 2.8) [M]

```java
double d = Math.sqrt(25) + Math.pow(2, 3);
System.out.println(d);
```

출력 결과는?

(A) `13`
(B) `13.0`
(C) `7.0`
(D) `10.0`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`Math.sqrt(25)` = `5.0`, `Math.pow(2, 3)` = `8.0`. `5.0 + 8.0 = 13.0`. 두 메서드 모두 `double`을 반환하므로 결과도 `double`이다.
</details>

---

### 문제 27 (Unit 1 - 토픽 2.8) [E]

```java
System.out.println(Math.abs(-7));
System.out.println(Math.abs(7));
```

출력 결과는?

(A) `-7` 다음 줄에 `7`
(B) `7` 다음 줄에 `7`
(C) `7` 다음 줄에 `-7`
(D) `-7` 다음 줄에 `-7`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`Math.abs()`는 절댓값을 반환한다. `Math.abs(-7) = 7`, `Math.abs(7) = 7`. 음수의 절댓값은 양수, 양수의 절댓값은 그대로 양수이다.
</details>

---

### 문제 28 (Unit 1 - 토픽 2.7) [H]

```java
String s = "banana";
System.out.println(s.substring(0, s.indexOf("na")));
```

출력 결과는?

(A) `ba`
(B) `ban`
(C) `b`
(D) `bana`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

`s.indexOf("na")`는 `"na"`가 처음 나타나는 인덱스를 반환한다. `"banana"`에서 b=0, a=1, n=2, a=3, n=4, a=5. `"na"`는 인덱스 2에서 처음 나타난다. `s.substring(0, 2)` → 인덱스 0, 1의 문자 → `"ba"`.
</details>

---

### 문제 29 (Unit 1 - 토픽 2.6) [H]

```java
String a = "Java";
String b = "Java";
String c = "Ja" + "va";
String d = "Ja";
d += "va";

System.out.println(a == b);
System.out.println(a == c);
System.out.println(a == d);
```

출력 결과는?

(A) `true true true`
(B) `true true false`
(C) `true false false`
(D) `true false true`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`a`와 `b`는 같은 String literal이므로 String pool에서 같은 객체를 참조 → `true`. `c = "Ja" + "va"`는 **컴파일 타임 상수 결합**이므로 `"Java"` literal과 같은 객체 → `true`. `d`는 `+=` 연산을 통해 **런타임에** 새 문자열을 생성하므로 String pool의 `"Java"`와 다른 객체 → `false`.
</details>

---

### 문제 30 (Unit 1 - 토픽 2.7) [M]

```java
String s = "Hello";
System.out.println(s.substring(5));
```

출력 결과는?

(A) `o`
(B) `""`  (빈 문자열)
(C) StringIndexOutOfBoundsException
(D) `null`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`substring(5)`는 인덱스 5부터 끝까지의 문자열을 반환한다. `"Hello"`의 길이는 5이고, 마지막 문자의 인덱스는 4이다. 인덱스 5는 문자열 끝 바로 다음이므로 빈 문자열 `""`을 반환한다. `substring(6)`이었다면 `StringIndexOutOfBoundsException`이 발생했을 것이다.
</details>

---

### 문제 31 (Unit 1 - 토픽 2.7) [M]

```java
String s = "computer";
String t = s.substring(3, 6);
int idx = s.indexOf(t);
System.out.println(t + " " + idx);
```

출력 결과는?

(A) `put 3`
(B) `pute 3`
(C) `put 4`
(D) `mpu 3`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

`s.substring(3, 6)` → 인덱스 3부터 5까지(6 미포함)의 문자를 추출: `"put"`. `s.indexOf("put")` → `"computer"`에서 `"put"`이 처음 나타나는 인덱스는 3. 최종 출력: `put 3`. `substring(beginIndex, endIndex)`에서 endIndex는 포함되지 않는다는 점에 주의.
</details>

---

### 문제 32 (Unit 1 - 토픽 2.7) [E]

```java
String name = "Alice";
System.out.println(name.substring(0, 1));
```

출력 결과는?

(A) `A`
(B) `Al`
(C) `Alice`
(D) 컴파일 에러

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

`substring(0, 1)`은 인덱스 0부터 0까지(endIndex 1은 포함하지 않음)의 문자를 반환한다. 첫 글자 `"A"`만 반환된다.
</details>

---

### 문제 33 (Unit 1 - 토픽 2.6) [M]

```java
String s1 = "abc";
String s2 = "ABC";
System.out.println(s1.equals(s2));
System.out.println(s1.compareTo(s2) > 0);
```

출력 결과는?

(A) `false false`
(B) `false true`
(C) `true true`
(D) `true false`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`equals()`는 대소문자를 구분하므로 `"abc"`와 `"ABC"`는 다르다 → `false`. `compareTo()`는 사전순으로 비교하는데, 소문자의 ASCII 값이 대문자보다 크다 ('a' = 97, 'A' = 65). 따라서 `s1.compareTo(s2) > 0`은 `true`이다.
</details>

---

### 문제 34 (Unit 1 - 토픽 2.3) [M]

다음 중 `void` 메서드에 대한 설명으로 올바른 것은?

(A) `void` 메서드는 항상 `return` 문이 필요하다.
(B) `void` 메서드는 값을 반환하지 않는다.
(C) `void` 메서드는 매개변수를 가질 수 없다.
(D) `void` 메서드는 `static`이어야 한다.

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`void`는 반환 타입이 없음을 의미한다. `void` 메서드는 작업을 수행하지만 값을 반환하지 않는다. `return;`문은 사용할 수 있지만 필수는 아니다. 매개변수는 가질 수 있으며, `static`일 필요도 없다.
</details>

---

### 문제 35 (Unit 1 - 토픽 2.4) [H]

```java
String s1 = "Cat";
String s2 = "cat";
int result = s1.compareTo(s2);
System.out.println(result < 0);
```

출력 결과는?

(A) `true`
(B) `false`
(C) `0`
(D) 컴파일 에러

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

`compareTo()`는 사전순으로 비교한다. 대문자 `'C'`의 ASCII 값은 67이고, 소문자 `'c'`는 99이다. 첫 문자에서 이미 차이가 나므로 `67 - 99 = -32` (음수). 따라서 `result < 0`은 `true`이다. 대문자가 소문자보다 사전순으로 앞에 온다.
</details>

---

### 문제 36 (Unit 1 - 토픽 2.7) [H]

```java
String s = "Hello World";
String result = s.substring(s.indexOf(" ") + 1);
System.out.println(result);
```

출력 결과는?

(A) `Hello`
(B) `World`
(C) ` World`
(D) `Hello `

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`s.indexOf(" ")`는 공백의 인덱스인 `5`를 반환한다. `5 + 1 = 6`. `s.substring(6)`은 인덱스 6부터 끝까지 → `"World"`. 이 패턴은 공백 이후의 문자열을 추출하는 데 자주 사용된다.
</details>

---

### 문제 37 (Unit 1 - 토픽 2.8) [M]

```java
System.out.println((int)(Math.random() * 10) + 5);
```

이 코드가 생성할 수 있는 값의 범위는?

(A) 5에서 14까지
(B) 5에서 15까지
(C) 0에서 14까지
(D) 0에서 15까지

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

`Math.random()`은 `[0.0, 1.0)` 범위. `* 10` → `[0.0, 10.0)`. `(int)` 캐스팅 → `0`~`9`. `+ 5` → `5`~`14`. 최솟값은 `0 + 5 = 5`, 최댓값은 `9 + 5 = 14`.
</details>

---

### 문제 38 (Unit 1 - 토픽 2.3) [E]

```java
String s = "Java";
System.out.println(s.substring(1));
System.out.println(s);
```

출력 결과는?

(A) `ava` 다음 줄에 `ava`
(B) `ava` 다음 줄에 `Java`
(C) `Java` 다음 줄에 `ava`
(D) `Java` 다음 줄에 `Java`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`s.substring(1)`은 인덱스 1부터 끝까지의 **새로운** 문자열 `"ava"`를 반환한다. 원본 `s`는 **불변(immutable)** 이므로 변경되지 않는다. 첫 줄은 반환된 새 문자열 `"ava"`, 둘째 줄은 원본 `"Java"`.
</details>

---

### 문제 39 (Unit 1 - 토픽 2.5) [H]

```java
Integer x = null;
int y = x;
```

실행 결과는?

(A) `y`는 `0`이 된다
(B) 컴파일 에러
(C) NullPointerException
(D) `y`는 `null`이 된다

<details>
<summary>정답 및 해설</summary>

**정답: (C)**

`Integer x = null;`은 유효하다 (참조 타입이므로 `null` 가능). `int y = x;`에서 unboxing을 시도하지만, `x`가 `null`이므로 `NullPointerException`이 발생한다. 이 코드는 컴파일은 되지만 실행 시 예외가 발생한다. Autoboxing/unboxing과 `null`의 조합은 흔한 함정이다.
</details>

---

### 문제 40 (Unit 1 - 토픽 2.7) [M]

```java
String s = "programming";
System.out.println(s.substring(3, 7).indexOf("am"));
```

출력 결과는?

(A) `2`
(B) `5`
(C) `-1`
(D) `0`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

`s.substring(3, 7)`: p=0, r=1, o=2, g=3, r=4, a=5, m=6, m=7. 인덱스 3~6 → `"gram"`. 그 다음 `"gram".indexOf("am")`을 호출 — `"gram"` 안에서 `"am"`은 g=0, r=1, a=2, m=3 중 인덱스 2에서 시작 → `2`. 메서드 체이닝에서는 왼쪽부터 순서대로 실행된다.
</details>

---

## Unit 2: Selection and Iteration (38문제)

---

### 문제 41 (Unit 2 - 토픽 3.1) [E]

```java
int x = 10;
if (x > 5)
    System.out.println("A");
    System.out.println("B");
```

출력 결과는?

(A) `A`만 출력
(B) `A` 다음 줄에 `B`
(C) `B`만 출력
(D) 아무것도 출력되지 않음

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

중괄호 `{}`가 없으면 `if` 문은 **바로 다음 한 문장만** 제어한다. `x > 5`가 `true`이므로 `"A"` 출력. 두 번째 `println("B")`는 `if` 문과 무관하게 **항상 실행**된다. 들여쓰기는 Java 실행에 영향을 주지 않는다. 이것은 매우 흔한 함정이다.
</details>

---

### 문제 42 (Unit 2 - 토픽 3.1) [E]

```java
int x = 7;
if (x > 10)
    System.out.println("A");
    System.out.println("B");
```

출력 결과는?

(A) `A`만 출력
(B) `A` 다음 줄에 `B`
(C) `B`만 출력
(D) 아무것도 출력되지 않음

<details>
<summary>정답 및 해설</summary>

**정답: (C)**

문제 41과 같은 패턴이지만 조건이 `false`인 경우. `x > 10`이 `false`이므로 `"A"`는 출력되지 않음. `"B"`는 `if` 문 밖이므로 항상 출력됨. 중괄호 없는 `if` 문의 범위를 정확히 이해해야 한다.
</details>

---

### 문제 43 (Unit 2 - 토픽 3.5) [M]

```java
boolean a = true;
boolean b = false;
System.out.println(!(a && b));
System.out.println(!a || !b);
```

출력 결과는?

(A) `true` 다음 줄에 `true`
(B) `false` 다음 줄에 `true`
(C) `true` 다음 줄에 `false`
(D) `false` 다음 줄에 `false`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

**De Morgan의 법칙**: `!(a && b)` 는 `!a || !b`와 동치이다. `a && b = true && false = false`. `!(false) = true`. `!a || !b = false || true = true`. 둘 다 `true`가 출력되며, 이것이 De Morgan의 법칙을 증명한다: `!(A && B) == !A || !B`.
</details>

---

### 문제 44 (Unit 2 - 토픽 3.5) [H]

다음 중 `!(x > 5 && y < 10)`과 동치인 것은?

(A) `x > 5 || y < 10`
(B) `x <= 5 || y >= 10`
(C) `x <= 5 && y >= 10`
(D) `x < 5 || y > 10`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

**De Morgan의 법칙**을 적용: `!(A && B)` = `!A || !B`. `A = x > 5`이면 `!A = x <= 5`. `B = y < 10`이면 `!B = y >= 10`. 따라서 `!(x > 5 && y < 10)` = `x <= 5 || y >= 10`. (D)는 `<`와 `>`를 사용했는데, `>`의 부정은 `<=`이고 `<`의 부정은 `>=`이므로 틀렸다 (경계값 함정).
</details>

---

### 문제 45 (Unit 2 - 토픽 3.4) [M]

```java
int score = 85;
if (score >= 90)
    System.out.println("A");
else if (score >= 80)
    System.out.println("B");
else if (score >= 70)
    System.out.println("C");
else
    System.out.println("F");
```

출력 결과는?

(A) `A`
(B) `B`
(C) `B` 다음 줄에 `C`
(D) `C`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`score = 85`. `score >= 90`은 `false` → 다음. `score >= 80`은 `true` → `"B"` 출력. `else if` 체인에서는 **첫 번째로 참인 조건**만 실행되고 나머지는 건너뛴다. `score >= 70`도 참이지만 실행되지 않는다.
</details>

---

### 문제 46 (Unit 2 - 토픽 3.6) [H]

```java
int x = 5;
if (x > 3)
    if (x > 10)
        System.out.println("A");
    else
        System.out.println("B");
```

출력 결과는?

(A) `A`
(B) `B`
(C) 아무것도 출력되지 않음
(D) 컴파일 에러

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

**"dangling else" 함정**: `else`는 **가장 가까운** `if`와 결합한다. 들여쓰기와 상관없이, `else`는 `if (x > 10)`에 결합된다. `x > 3`은 `true` → 내부 `if` 실행. `x > 10`은 `false` → `else` 실행 → `"B"` 출력.
</details>

---

### 문제 47 (Unit 2 - 토픽 3.3) [M]

```java
int x = 0;
if (x != 0 && 10 / x > 2)
    System.out.println("Yes");
else
    System.out.println("No");
```

출력 결과는?

(A) `Yes`
(B) `No`
(C) ArithmeticException (0으로 나눗셈)
(D) 컴파일 에러

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

**단축 평가(short-circuit evaluation)**: `&&` 연산에서 왼쪽이 `false`이면 오른쪽을 평가하지 않는다. `x != 0`이 `false`이므로 `10 / x`는 실행되지 않아 `ArithmeticException`이 발생하지 않는다. 전체 조건이 `false`이므로 `"No"` 출력. 단축 평가는 안전한 조건 체크에 유용하다.
</details>

---

### 문제 48 (Unit 2 - 토픽 3.5) [M]

다음 중 `!(a || b)`와 동치인 것은?

(A) `!a || !b`
(B) `!a && !b`
(C) `a && b`
(D) `!a || b`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

**De Morgan의 법칙**: `!(A || B)` = `!A && !B`. OR의 부정은 AND로 바뀌고, 각 항이 부정된다. (A)는 `!(A && B)`의 결과이므로 틀렸다.
</details>

---

### 문제 49 (Unit 2 - 토픽 3.2) [E]

```java
double x = 0.1 + 0.1 + 0.1;
if (x == 0.3)
    System.out.println("Equal");
else
    System.out.println("Not Equal");
```

출력 결과는?

(A) `Equal`
(B) `Not Equal`
(C) 컴파일 에러
(D) 실행 결과가 매번 다르다

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

부동소수점 정밀도 문제: `0.1 + 0.1 + 0.1`은 정확히 `0.3`이 아니다. 이진수로 `0.1`을 정확히 표현할 수 없기 때문이다. 실수 비교에 `==`를 사용하면 안 되고, 대신 `Math.abs(x - 0.3) < 0.0001`처럼 오차 범위를 사용해야 한다.
</details>

---

### 문제 50 (Unit 2 - 토픽 3.6) [H]

```java
int a = 5, b = 3, c = 8;
if (a > b && b > c || c > a)
    System.out.println("True");
else
    System.out.println("False");
```

출력 결과는?

(A) `True`
(B) `False`
(C) 컴파일 에러
(D) 결과를 알 수 없음

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

**연산자 우선순위**: `&&`가 `||`보다 우선순위가 높다. 따라서 `(a > b && b > c) || (c > a)`로 평가된다. `a > b` = `true`, `b > c` = `false`. `true && false = false`. `c > a` = `true`. `false || true = true`. `"True"` 출력.
</details>

---

### 문제 51 (Unit 2 - 토픽 3.3) [M]

```java
String s = null;
if (s != null && s.length() > 0)
    System.out.println("Valid");
else
    System.out.println("Invalid");
```

출력 결과는?

(A) `Valid`
(B) `Invalid`
(C) NullPointerException
(D) 컴파일 에러

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

단축 평가(short-circuit evaluation)가 `NullPointerException`을 방지한다. `s != null`이 `false`이므로 `&&`의 오른쪽 `s.length() > 0`은 평가되지 않는다. 이 패턴은 null-safe한 코드를 작성하는 표준적인 방법이다.
</details>

---

### 문제 52 (Unit 2 - 토픽 3.4) [M]

```java
int x = 15;
String result;
if (x % 3 == 0 && x % 5 == 0)
    result = "FizzBuzz";
else if (x % 3 == 0)
    result = "Fizz";
else if (x % 5 == 0)
    result = "Buzz";
else
    result = "" + x;
System.out.println(result);
```

출력 결과는?

(A) `Fizz`
(B) `Buzz`
(C) `FizzBuzz`
(D) `15`

<details>
<summary>정답 및 해설</summary>

**정답: (C)**

`x = 15`. `15 % 3 == 0`은 `true`, `15 % 5 == 0`은 `true`. 첫 번째 조건 `x % 3 == 0 && x % 5 == 0`이 `true`이므로 `"FizzBuzz"`가 대입된다. `else if` 체인에서 첫 번째 참인 조건만 실행된다. 만약 `else if`의 순서를 바꾸면 다른 결과가 나올 수 있으므로 가장 구체적인 조건을 먼저 검사해야 한다.
</details>

---

### 문제 53 (Unit 2 - 토픽 4.1) [E]

```java
int count = 0;
while (count < 5) {
    System.out.print(count + " ");
    count++;
}
```

출력 결과는?

(A) `1 2 3 4 5 `
(B) `0 1 2 3 4 `
(C) `0 1 2 3 4 5 `
(D) `1 2 3 4 `

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`count`는 0에서 시작하여 `count < 5`인 동안 반복한다. 0, 1, 2, 3, 4가 출력된 후 `count`가 5가 되면 조건이 `false`가 되어 루프가 종료된다. 총 5회 반복.
</details>

---

### 문제 54 (Unit 2 - 토픽 4.2) [E]

```java
for (int i = 1; i <= 5; i++) {
    System.out.print(i * 2 + " ");
}
```

출력 결과는?

(A) `2 4 6 8 10 `
(B) `1 2 3 4 5 `
(C) `2 4 6 8 `
(D) `0 2 4 6 8 `

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

`i`는 1에서 5까지 1씩 증가. 각 반복에서 `i * 2`를 출력: `1*2=2`, `2*2=4`, `3*2=6`, `4*2=8`, `5*2=10`.
</details>

---

### 문제 55 (Unit 2 - 토픽 4.2) [M]

```java
int sum = 0;
for (int i = 0; i < 10; i += 3) {
    sum += i;
}
System.out.println(sum);
```

출력 결과는?

(A) `18`
(B) `15`
(C) `12`
(D) `9`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

`i`의 값: 0, 3, 6, 9 (그 다음은 12인데 `12 < 10`이 `false`이므로 종료). `sum = 0 + 3 + 6 + 9 = 18`.
</details>

---

### 문제 56 (Unit 2 - 토픽 4.1) [M]

```java
int x = 100;
int count = 0;
while (x > 1) {
    x /= 2;
    count++;
}
System.out.println(count);
```

출력 결과는?

(A) `6`
(B) `7`
(C) `50`
(D) `100`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

정수 나눗셈으로 `x`를 반씩 줄인다: 100→50→25→12→6→3→1. `x`가 1이 되면 루프 종료. 총 6회 반복. 주의: `25 / 2 = 12` (정수 나눗셈으로 12.5가 아닌 12).
</details>

---

### 문제 57 (Unit 2 - 토픽 4.2) [H]

```java
for (int i = 0; i < 5; i++) {
    for (int j = 0; j <= i; j++) {
        System.out.print("*");
    }
    System.out.println();
}
```

출력 결과는?

(A)
```
*****
*****
*****
*****
*****
```
(B)
```
*
**
***
****
*****
```
(C)
```
*****
****
***
**
*
```
(D)
```
*
***
*****
```

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

외부 루프에서 `i`는 0~4. 내부 루프에서 `j`는 0~`i`까지. `i=0`: `*` (1개), `i=1`: `**` (2개), `i=2`: `***` (3개), `i=3`: `****` (4개), `i=4`: `*****` (5개). 삼각형 패턴이 만들어진다.
</details>

---

### 문제 58 (Unit 2 - 토픽 4.2) [M]

```java
int result = 1;
for (int i = 0; i < 4; i++) {
    result *= 3;
}
System.out.println(result);
```

출력 결과는?

(A) `12`
(B) `27`
(C) `81`
(D) `243`

<details>
<summary>정답 및 해설</summary>

**정답: (C)**

`result`에 3을 4번 곱한다: `1*3=3`, `3*3=9`, `9*3=27`, `27*3=81`. 이것은 3^4 = 81을 계산하는 코드이다. **Off-by-one 주의**: `i < 4`이므로 정확히 4번 반복 (i = 0, 1, 2, 3).
</details>

---

### 문제 59 (Unit 2 - 토픽 4.3) [E]

```java
String s = "Hello";
for (int i = 0; i < s.length(); i++) {
    System.out.print(s.substring(i, i + 1));
}
```

출력 결과는?

(A) `Hello`
(B) `ello`
(C) `Hell`
(D) `H e l l o`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

각 반복에서 `substring(i, i+1)`은 인덱스 `i`의 한 글자를 추출한다. `i=0`: `"H"`, `i=1`: `"e"`, `i=2`: `"l"`, `i=3`: `"l"`, `i=4`: `"o"`. 모든 글자가 순서대로 출력되어 `"Hello"`. 이것은 문자열을 한 글자씩 순회하는 표준 패턴이다.
</details>

---

### 문제 60 (Unit 2 - 토픽 4.3) [M]

```java
String s = "abcba";
int count = 0;
for (int i = 0; i < s.length(); i++) {
    if (s.substring(i, i + 1).equals("a"))
        count++;
}
System.out.println(count);
```

출력 결과는?

(A) `1`
(B) `2`
(C) `3`
(D) `0`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

문자열 `"abcba"`에서 `"a"`가 나타나는 횟수를 센다. 인덱스 0과 4에서 `"a"`가 나타나므로 `count = 2`. 문자열에서 문자를 비교할 때 `==` 대신 `equals()`를 사용해야 한다.
</details>

---

### 문제 61 (Unit 2 - 토픽 4.1) [H]

```java
int n = 1234;
int reversed = 0;
while (n > 0) {
    reversed = reversed * 10 + n % 10;
    n /= 10;
}
System.out.println(reversed);
```

출력 결과는?

(A) `1234`
(B) `4321`
(C) `432`
(D) `3214`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

숫자 뒤집기 알고리즘. 각 반복에서 `n`의 마지막 자릿수를 추출(`n % 10`)하여 `reversed`에 추가한다.
- `n=1234`: `reversed = 0*10+4 = 4`, `n = 123`
- `n=123`: `reversed = 4*10+3 = 43`, `n = 12`
- `n=12`: `reversed = 43*10+2 = 432`, `n = 1`
- `n=1`: `reversed = 432*10+1 = 4321`, `n = 0`
루프 종료. `reversed = 4321`.
</details>

---

### 문제 62 (Unit 2 - 토픽 4.2) [M]

```java
for (int i = 10; i >= 1; i -= 2) {
    System.out.print(i + " ");
}
```

출력 결과는?

(A) `10 8 6 4 2 `
(B) `10 8 6 4 2 0 `
(C) `10 9 8 7 6 5 4 3 2 1 `
(D) `8 6 4 2 `

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

`i`는 10에서 시작하여 2씩 감소하며 `i >= 1`인 동안 반복. `i`의 값: 10, 8, 6, 4, 2. 그 다음 `i = 0`이 되면 `0 >= 1`이 `false`이므로 종료.
</details>

---

### 문제 63 (Unit 2 - 토픽 4.4) [M]

```java
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        if (i == j)
            System.out.print("* ");
        else
            System.out.print("0 ");
    }
    System.out.println();
}
```

출력 결과는?

(A)
```
* * *
* * *
* * *
```
(B)
```
* 0 0
0 * 0
0 0 *
```
(C)
```
0 0 *
0 * 0
* 0 0
```
(D)
```
* 0 0
* 0 0
* 0 0
```

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`i == j`일 때 `*`, 아닐 때 `0`을 출력한다. 이것은 3x3 단위 행렬(identity matrix) 패턴이다. 대각선 위치(1,1), (2,2), (3,3)에만 `*`가 출력된다.
</details>

---

### 문제 64 (Unit 2 - 토픽 4.1) [E]

다음 중 무한 루프가 되는 코드는?

(A)
```java
for (int i = 0; i < 10; i++) { }
```
(B)
```java
int x = 10;
while (x > 0) { x--; }
```
(C)
```java
int x = 0;
while (x < 5) { x = x + 1; }
```
(D)
```java
int x = 1;
while (x > 0) { x++; }
```

<details>
<summary>정답 및 해설</summary>

**정답: (D)**

(A) `i`가 0에서 9까지 증가하며 10에서 종료. (B) `x`가 10에서 0까지 감소하며 0에서 종료. (C) `x`는 0, 1, 2, 3, 4, 5로 증가하다 `x < 5`가 거짓이 되어 종료. (D) `x`는 1에서 시작하여 계속 증가하므로 항상 `x > 0`이 `true`. 사실 `int` 오버플로우로 음수가 되면 종료될 수 있지만, 의도적으로는 무한 루프이다.
</details>

---

### 문제 65 (Unit 2 - 토픽 4.3) [M]

```java
String s = "Hello World";
String result = "";
for (int i = 0; i < s.length(); i++) {
    if (!s.substring(i, i + 1).equals(" "))
        result += s.substring(i, i + 1);
}
System.out.println(result);
```

출력 결과는?

(A) `Hello World`
(B) `HelloWorld`
(C) `Hello`
(D) `World`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

공백이 아닌 문자만 `result`에 추가한다. `" "`(공백)을 만나면 건너뛰므로 결과는 `"HelloWorld"`. 이 코드는 문자열에서 공백을 제거하는 알고리즘이다.
</details>

---

### 문제 66 (Unit 2 - 토픽 4.2) [H]

```java
int count = 0;
for (int i = 1; i <= 100; i++) {
    if (i % 3 == 0 && i % 5 == 0)
        count++;
}
System.out.println(count);
```

출력 결과는?

(A) `6`
(B) `33`
(C) `20`
(D) `47`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

3과 5의 공배수(즉, 15의 배수)를 센다. 1~100에서 15의 배수: 15, 30, 45, 60, 75, 90 → 6개. `100 / 15 = 6` (정수 나눗셈, 나머지 10은 버림).
</details>

---

### 문제 67 (Unit 2 - 토픽 4.4) [M]

```java
int sum = 0;
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        sum++;
    }
}
System.out.println(sum);
```

출력 결과는?

(A) `6`
(B) `9`
(C) `3`
(D) `12`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

외부 루프 3회 × 내부 루프 3회 = 총 9회 반복. 중첩 루프의 총 반복 횟수는 각 루프의 반복 횟수를 곱한 것이다.
</details>

---

### 문제 68 (Unit 4 - 토픽 4.2) [M]

```java
int[] arr = {3, 7, 2, 9, 5};
int max = arr[0];
int sum = 0;
for (int i = 0; i < arr.length; i++) {
    sum += arr[i];
    if (arr[i] > max)
        max = arr[i];
}
System.out.println(max + " " + sum);
```

출력 결과는?

(A) `9 26`
(B) `9 21`
(C) `7 26`
(D) `9 17`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

배열을 순회하면서 합계와 최댓값을 동시에 구한다. `sum = 3+7+2+9+5 = 26`. `max`는 초기값 3에서 시작하여 7로 갱신, 다시 9로 갱신되어 최종 9. 최종 출력: `9 26`. 이는 배열 탐색의 기본 알고리즘(합계, 최댓값 찾기)이다.
</details>

---

### 문제 69 (Unit 2 - 토픽 4.3) [H]

```java
String s = "abcde";
String result = "";
for (int i = s.length() - 1; i >= 0; i--) {
    result += s.substring(i, i + 1);
}
System.out.println(result);
```

출력 결과는?

(A) `abcde`
(B) `edcba`
(C) `edcb`
(D) `bcde`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

문자열을 역순으로 순회한다. `i`는 4에서 0까지 감소. `i=4`: `"e"`, `i=3`: `"d"`, `i=2`: `"c"`, `i=1`: `"b"`, `i=0`: `"a"`. `result = "edcba"`. 이것은 문자열 뒤집기의 기본 알고리즘이다.
</details>

---

### 문제 70 (Unit 2 - 토픽 4.2) [E]

```java
int sum = 0;
for (int i = 1; i <= 10; i++) {
    sum += i;
}
System.out.println(sum);
```

출력 결과는?

(A) `45`
(B) `55`
(C) `10`
(D) `100`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

1부터 10까지의 합: `1+2+3+4+5+6+7+8+9+10 = 55`. 가우스 공식으로 검증: `n(n+1)/2 = 10*11/2 = 55`.
</details>

---

### 문제 71 (Unit 2 - 토픽 4.1) [M]

```java
int n = 7;
int i = 2;
boolean isPrime = true;
while (i < n) {
    if (n % i == 0) {
        isPrime = false;
    }
    i++;
}
System.out.println(isPrime);
```

출력 결과는?

(A) `true`
(B) `false`
(C) 컴파일 에러
(D) 무한 루프

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

이 코드는 `n`이 소수인지 판별한다. `n = 7`에 대해 2~6으로 나누어 본다. `7 % 2 = 1`, `7 % 3 = 1`, `7 % 4 = 3`, `7 % 5 = 2`, `7 % 6 = 1`. 어떤 수로도 나누어떨어지지 않으므로 `isPrime`은 `true`로 유지된다. 7은 소수이다.
</details>

---

### 문제 72 (Unit 2 - 토픽 4.2) [H]

```java
int n = 5;
int result = 1;
for (int i = 1; i <= n; i++) {
    result *= i;
}
System.out.println(result);
```

출력 결과는?

(A) `15`
(B) `25`
(C) `120`
(D) `60`

<details>
<summary>정답 및 해설</summary>

**정답: (C)**

이 코드는 `5!` (팩토리얼)을 계산한다. `result = 1*1*2*3*4*5 = 120`. 더 정확히: `i=1`: `1*1=1`, `i=2`: `1*2=2`, `i=3`: `2*3=6`, `i=4`: `6*4=24`, `i=5`: `24*5=120`.
</details>

---

### 문제 73 (Unit 2 - 토픽 4.4) [H]

```java
int count = 0;
for (int i = 0; i < 4; i++) {
    for (int j = i; j < 4; j++) {
        count++;
    }
}
System.out.println(count);
```

출력 결과는?

(A) `16`
(B) `10`
(C) `6`
(D) `8`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

내부 루프의 시작이 `j = i`이므로 각 외부 반복에서의 내부 반복 횟수가 달라진다. `i=0`: j는 0,1,2,3 (4회). `i=1`: j는 1,2,3 (3회). `i=2`: j는 2,3 (2회). `i=3`: j는 3 (1회). 총 `4+3+2+1 = 10`.
</details>

---

### 문제 74 (Unit 2 - 토픽 4.3) [M]

```java
String s = "Java";
for (int i = 0; i < s.length(); i++) {
    System.out.print(s.substring(i) + " ");
}
```

출력 결과는?

(A) `J a v a `
(B) `Java ava va a `
(C) `a va ava Java `
(D) `Java Jav Ja J `

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`substring(i)`는 인덱스 `i`부터 끝까지의 부분 문자열을 반환한다. `i=0`: `"Java"`, `i=1`: `"ava"`, `i=2`: `"va"`, `i=3`: `"a"`. 출력: `Java ava va a `.
</details>

---

### 문제 75 (Unit 2 - 토픽 4.1) [M]

```java
int x = 1;
while (x < 100) {
    x *= 2;
}
System.out.println(x);
```

출력 결과는?

(A) `64`
(B) `128`
(C) `100`
(D) `256`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`x`는 2의 거듭제곱으로 증가: 1→2→4→8→16→32→64→128. `x = 64`일 때 `64 < 100`은 `true`이므로 한 번 더 실행하여 `x = 128`. `128 < 100`은 `false`이므로 루프 종료. **Off-by-one 주의**: 조건 확인은 루프 시작 시점이므로 `x`가 100을 넘는 첫 번째 값 128이 출력된다.
</details>

---

### 문제 76 (Unit 2 - 토픽 4.2) [E]

```java
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 2; j++) {
        System.out.print("X");
    }
}
```

`"X"`가 총 몇 번 출력되는가?

(A) `3`
(B) `5`
(C) `6`
(D) `8`

<details>
<summary>정답 및 해설</summary>

**정답: (C)**

외부 루프 3회 × 내부 루프 2회 = 총 6회. 중첩 루프에서 총 실행 횟수는 각 루프의 반복 횟수의 곱이다.
</details>

---

### 문제 77 (Unit 2 - 토픽 4.3) [H]

```java
String s = "aabbcc";
int count = 0;
for (int i = 0; i < s.length() - 1; i++) {
    if (s.substring(i, i + 1).equals(s.substring(i + 1, i + 2)))
        count++;
}
System.out.println(count);
```

출력 결과는?

(A) `1`
(B) `2`
(C) `3`
(D) `6`

<details>
<summary>정답 및 해설</summary>

**정답: (C)**

연속된 같은 문자 쌍을 센다. 인덱스별 비교:
- i=0: `"a"` == `"a"` → count++ (1)
- i=1: `"a"` == `"b"` → no
- i=2: `"b"` == `"b"` → count++ (2)
- i=3: `"b"` == `"c"` → no
- i=4: `"c"` == `"c"` → count++ (3)

`i < s.length() - 1`로 범위를 제한하여 `StringIndexOutOfBoundsException`을 방지한다. count = 3.
</details>

---

### 문제 78 (Unit 2 - 토픽 4.4) [H]

```java
String result = "";
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= i; j++) {
        result += i;
    }
    if (i < 3) result += " ";
}
System.out.println(result);
```

출력 결과는?

(A) `1 12 123`
(B) `1 22 333`
(C) `123 123 123`
(D) `1 2 3`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

외부 루프에서 `i`는 1, 2, 3. 내부 루프에서 `i`를 `j`번(1~`i`번) 반복 출력한다. 그리고 `i < 3`인 동안에만 공백을 덧붙여, 마지막 토큰 뒤에 공백이 남지 않게 한다.
- `i=1`: `j`는 1번 → `"1"` 추가, `i<3`이므로 공백 추가 → `"1 "`
- `i=2`: `j`는 2번 → `"22"` 추가, `i<3`이므로 공백 추가 → `"1 22 "`
- `i=3`: `j`는 3번 → `"333"` 추가, `i<3`이 거짓이므로 공백 미추가 → `"1 22 333"`
</details>

---

### 문제 79 (Unit 4 - 토픽 4.2) [M]

```java
int max = Integer.MIN_VALUE;
int[] arr = {3, 7, 2, 9, 1};
for (int i = 0; i < arr.length; i++) {
    if (arr[i] > max)
        max = arr[i];
}
System.out.println(max);
```

출력 결과는?

(A) `7`
(B) `9`
(C) `1`
(D) `3`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

배열에서 최댓값을 찾는 표준 알고리즘. `max`를 가능한 가장 작은 값(`Integer.MIN_VALUE`)으로 초기화한 후, 각 요소와 비교하며 더 큰 값을 저장한다. 배열의 최댓값은 9이다.
</details>

---

### 문제 80 (Unit 2 - 토픽 4.1) [H]

```java
int a = 48;
int b = 18;
while (b != 0) {
    int temp = b;
    b = a % b;
    a = temp;
}
System.out.println(a);
```

출력 결과는?

(A) `2`
(B) `6`
(C) `12`
(D) `18`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

이 코드는 **유클리드 호제법(Euclidean algorithm)** 으로 최대공약수(GCD)를 구한다.
- `a=48, b=18`: `temp=18`, `b=48%18=12`, `a=18`
- `a=18, b=12`: `temp=12`, `b=18%12=6`, `a=12`
- `a=12, b=6`: `temp=6`, `b=12%6=0`, `a=6`
- `b=0`이므로 루프 종료. `a = 6`.

`GCD(48, 18) = 6`. 검증: `48 = 6×8`, `18 = 6×3`.
</details>

---

## Unit 3: Class Creation (10문제)

---

### 문제 81 (Unit 3 - 토픽 3.1) [E]

다음 클래스에서 `main` 메서드의 출력 결과는?

```java
public class Dog {
    private String name;

    public Dog(String n) {
        name = n;
    }

    public String getName() {
        return name;
    }
}

// 다른 클래스의 main 메서드
Dog d = new Dog("Buddy");
System.out.println(d.name);
```

(A) `Buddy`
(B) `null`
(C) 컴파일 에러
(D) 런타임 에러

<details>
<summary>정답 및 해설</summary>

**정답: (C)**

`name`은 `private` 인스턴스 변수이므로 **클래스 외부에서 직접 접근할 수 없다**. `d.name`은 컴파일 에러를 발생시킨다. 외부에서 접근하려면 `d.getName()`처럼 public accessor 메서드를 사용해야 한다. `private`은 캡슐화(encapsulation)를 위한 접근 제어자로, 데이터를 보호하고 클래스 내부 구현을 숨기는 역할을 한다.
</details>

---

### 문제 82 (Unit 3 - 토픽 3.2) [E]

```java
public class Circle {
    private double radius;

    public Circle(double r) {
        radius = r;
    }

    public double getArea() {
        return Math.PI * radius * radius;
    }
}
```

다음 코드의 실행 결과는?

```java
Circle c = new Circle(5.0);
System.out.println(c.getArea() > 78 && c.getArea() < 79);
```

(A) `true`
(B) `false`
(C) 컴파일 에러
(D) `78.5`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

생성자 `Circle(double r)`에 `5.0`이 전달되어 `radius = 5.0`으로 초기화된다. `getArea()`는 `Math.PI * 5.0 * 5.0 = 78.5398...`을 반환한다. 이 값은 78보다 크고 79보다 작으므로 `true && true`는 `true`이다. 생성자의 매개변수(parameter)를 통해 인스턴스 변수를 초기화하는 기본적인 패턴이다.
</details>

---

### 문제 83 (Unit 3 - 토픽 3.1) [M]

다음 클래스를 보고, `main`에서 객체를 생성한 직후 각 인스턴스 변수의 기본값은?

```java
public class Student {
    private String name;
    private int age;
    private double gpa;
    private boolean enrolled;

    public Student() {
        // 빈 생성자
    }
}
```

```java
Student s = new Student();
```

(A) `name`은 `""`, `age`는 `0`, `gpa`는 `0.0`, `enrolled`는 `false`
(B) `name`은 `null`, `age`는 `0`, `gpa`는 `0.0`, `enrolled`는 `false`
(C) 모든 변수가 `null`
(D) 컴파일 에러 — 인스턴스 변수를 초기화하지 않았으므로

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

Java에서 인스턴스 변수는 **명시적으로 초기화하지 않으면 기본값을 갖는다**. `int`는 `0`, `double`은 `0.0`, `boolean`은 `false`, 참조 타입(`String` 등)은 `null`이다. 지역 변수(local variable)와 달리 인스턴스 변수는 초기화 없이 사용해도 컴파일 에러가 나지 않는다. (A)의 함정: `String`의 기본값은 빈 문자열 `""`이 아니라 `null`이다.
</details>

---

### 문제 84 (Unit 3 - 토픽 3.4) [M]

다음 중 **accessor 메서드**만을 모두 고른 것은?

```java
public class BankAccount {
    private double balance;
    private String owner;

    public double getBalance() {        // 메서드 I
        return balance;
    }

    public void deposit(double amount) { // 메서드 II
        balance += amount;
    }

    public String getOwner() {           // 메서드 III
        return owner;
    }

    public void setOwner(String name) {  // 메서드 IV
        owner = name;
    }
}
```

(A) I만
(B) I, III
(C) I, II, III
(D) I, III, IV

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

Accessor 메서드(getter)는 **인스턴스 변수의 값을 반환하되, 객체의 상태를 변경하지 않는** 메서드이다. 메서드 I(`getBalance`)과 III(`getOwner`)은 값을 return할 뿐 변경하지 않으므로 accessor이다. 메서드 II(`deposit`)는 `balance`를 변경하므로 mutator이고, 메서드 IV(`setOwner`)도 `owner`를 변경하므로 mutator(setter)이다.
</details>

---

### 문제 85 (Unit 3 - 토픽 3.5) [M]

```java
public class Counter {
    private int count;

    public Counter() {
        count = 0;
    }

    public void increment(int count) {
        count = count + 1;
    }

    public int getCount() {
        return count;
    }
}
```

다음 코드의 출력은?

```java
Counter c = new Counter();
c.increment(10);
c.increment(20);
System.out.println(c.getCount());
```

(A) `2`
(B) `0`
(C) `31`
(D) `12`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`increment` 메서드의 매개변수 이름이 `count`로, 인스턴스 변수 `count`와 **동일한 이름**이다. 메서드 내부에서 `count`는 **매개변수(지역 변수)**를 가리키므로, `count = count + 1`은 매개변수 값만 변경하고 인스턴스 변수 `this.count`는 전혀 변경되지 않는다. 따라서 `getCount()`는 초기값 `0`을 반환한다. 인스턴스 변수를 변경하려면 `this.count = this.count + 1;`로 작성해야 한다.
</details>

---

### 문제 86 (Unit 3 - 토픽 3.5) [E]

```java
public class Temperature {
    private double celsius;

    public Temperature(double c) {
        celsius = c;
    }

    public void setCelsius(double c) {
        celsius = c;
    }

    public double getFahrenheit() {
        return celsius * 9.0 / 5.0 + 32;
    }
}
```

다음 코드의 출력은?

```java
Temperature t = new Temperature(0);
t.setCelsius(100);
System.out.println(t.getFahrenheit());
```

(A) `32.0`
(B) `212.0`
(C) `100.0`
(D) `0.0`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

처음 `celsius`는 `0`으로 초기화되지만, `setCelsius(100)`이 호출되어 `celsius`가 `100`으로 변경된다. 이후 `getFahrenheit()`는 `100 * 9.0 / 5.0 + 32 = 180.0 + 32 = 212.0`을 반환한다. `setCelsius`는 mutator 메서드로 객체의 상태(인스턴스 변수)를 변경하고, `getFahrenheit`는 accessor 메서드로 계산된 값을 반환한다.
</details>

---

### 문제 87 (Unit 3 - 토픽 3.6) [H]

```java
public class Item {
    private static int nextId = 1;
    private int id;
    private String name;

    public Item(String name) {
        this.name = name;
        this.id = nextId;
        nextId++;
    }

    public int getId() {
        return id;
    }
}
```

다음 코드의 출력은?

```java
Item a = new Item("Apple");
Item b = new Item("Banana");
Item c = new Item("Cherry");
System.out.println(a.getId() + " " + b.getId() + " " + c.getId());
```

(A) `1 1 1`
(B) `1 2 3`
(C) `3 3 3`
(D) `0 1 2`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`nextId`는 `static` 변수로 **클래스 레벨**에 존재하며, 모든 인스턴스가 공유한다. 객체가 생성될 때마다 현재 `nextId`를 `id`에 대입한 후 `nextId`를 증가시킨다. 첫 번째 객체 `a`는 `id=1`(nextId→2), 두 번째 `b`는 `id=2`(nextId→3), 세 번째 `c`는 `id=3`(nextId→4). 각 객체의 `id`는 인스턴스 변수이므로 생성 시점의 값을 유지한다. (C)의 함정: `static`인 것은 `nextId`이지 `id`가 아니다.
</details>

---

### 문제 88 (Unit 3 - 토픽 3.6) [H]

다음 코드에서 컴파일 에러가 발생하는 줄은?

```java
public class MathHelper {
    private int value;

    public MathHelper(int v) {
        value = v;
    }

    public static int square(int x) {   // Line 1
        return x * x;                   // Line 2
    }

    public static int doubleValue() {   // Line 3
        return value * 2;               // Line 4
    }

    public int getValue() {             // Line 5
        return value;                   // Line 6
    }
}
```

(A) Line 1
(B) Line 4
(C) Line 5
(D) 컴파일 에러 없음

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`doubleValue()`는 `static` 메서드인데, `value`는 인스턴스 변수이다. **`static` 메서드는 특정 객체에 속하지 않으므로 인스턴스 변수에 접근할 수 없다.** Line 4에서 `value`를 참조하면 컴파일 에러가 발생한다. `static` 메서드는 `static` 변수와 다른 `static` 메서드만 직접 호출할 수 있다. 인스턴스 멤버에 접근하려면 객체 참조를 통해야 한다.
</details>

---

### 문제 89 (Unit 3 - 토픽 3.3) [M]

다음 Javadoc 주석을 보고, 이 메서드의 동작으로 올바른 것은?

```java
/**
 * 주어진 문자열에서 특정 문자의 등장 횟수를 반환한다.
 *
 * @param str 검색 대상 문자열 (null이 아님)
 * @param ch 찾을 문자
 * @return str에서 ch가 등장하는 횟수.
 *         ch가 str에 없으면 0을 반환한다.
 */
public int countChar(String str, char ch)
```

다음 중 `countChar("banana", 'a')`의 반환값은?

(A) `1`
(B) `2`
(C) `3`
(D) Javadoc만으로는 판단할 수 없으며, 구현에 따라 다르다

<details>
<summary>정답 및 해설</summary>

**정답: (C)**

Javadoc의 `@return`에 따르면 이 메서드는 `str`에서 `ch`가 **등장하는 횟수**를 반환한다. `"banana"`에서 `'a'`는 인덱스 1, 3, 5에 총 **3번** 등장한다. Javadoc 주석은 메서드의 **계약(contract)**을 명시하므로, 올바르게 구현된 메서드라면 `@return` 설명대로 동작해야 한다. (D)의 함정: AP CSA에서 Javadoc은 메서드의 동작 명세로 간주하며, 구현이 명세를 따른다고 가정한다.
</details>

---

### 문제 90 (Unit 3 - 토픽 3.1) [H]

다음 중 `Rectangle` 클래스의 올바른 구현은?

**요구사항:**
- `width`와 `height` 인스턴스 변수 (외부 접근 불가)
- 두 값을 받는 생성자
- 넓이를 반환하는 `getArea()` 메서드
- `width`를 변경하는 `setWidth()` 메서드

(A)
```java
public class Rectangle {
    public double width;
    public double height;
    public Rectangle(double w, double h) {
        width = w; height = h;
    }
    public double getArea() { return width * height; }
    public void setWidth(double w) { width = w; }
}
```

(B)
```java
public class Rectangle {
    private double width;
    private double height;
    public Rectangle(double w, double h) {
        width = w; height = h;
    }
    public double getArea() { return width * height; }
    public void setWidth(double w) { width = w; }
}
```

(C)
```java
public class Rectangle {
    private double width;
    private double height;
    public Rectangle(double w, double h) {
        width = w; height = h;
    }
    public double getArea() { return width * height; }
    public double setWidth(double w) { width = w; }
}
```

(D)
```java
public class Rectangle {
    private double width;
    private double height;
    public void Rectangle(double w, double h) {
        width = w; height = h;
    }
    public double getArea() { return width * height; }
    public void setWidth(double w) { width = w; }
}
```

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

(A) `width`와 `height`가 `public`이므로 "외부 접근 불가" 요구사항을 위반한다. (B) 모든 요구사항을 충족한다 — `private` 인스턴스 변수, 매개변수를 받는 생성자, `double`을 반환하는 accessor `getArea()`, `void`를 반환하는 mutator `setWidth()`. (C) `setWidth`의 반환 타입이 `double`인데 `return` 문이 없으므로 컴파일 에러이다. mutator는 일반적으로 `void`를 반환한다. (D) 생성자에 `void` 반환 타입을 선언하면 **생성자가 아니라 일반 메서드**가 된다. `new Rectangle(1, 2)` 호출 시 이 메서드는 실행되지 않아 변수가 기본값 `0.0`으로 남는다.
</details>

---

## Unit 4: Data Collections (32문제)

> 문제 68, 79는 배열(array)을 다루므로 Unit 4에 해당합니다. 해당 문제는 Unit 2 영역에 물리적으로 위치하지만 Unit 4로 분류됩니다.

---

### 문제 91 (Unit 4 - 토픽 4.1) [E]

다음 중 올바른 배열 선언 및 초기화는?

(A) `int[] arr = new int(5);`
(B) `int[] arr = new int[5];`
(C) `int arr[] = new int[];`
(D) `int arr = new int[5];`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

배열 생성 시 `new int[크기]` 형식을 사용한다. (A) 소괄호는 생성자 호출 문법이며 배열에는 사용 불가. (C) 크기를 지정하지 않으면 컴파일 에러. (D) 타입이 `int`이므로 배열 참조를 저장할 수 없다. `int[]` 또는 `int arr[]` 형태여야 한다.
</details>

---

### 문제 92 (Unit 4 - 토픽 4.2) [E]

```java
int[] nums = {10, 20, 30, 40, 50};
System.out.println(nums[2] + " " + nums.length);
```

출력 결과는?

(A) `20 5`
(B) `30 5`
(C) `30 4`
(D) `20 4`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

배열 인덱스는 0부터 시작하므로 `nums[2]`는 세 번째 원소 `30`이다. `nums.length`는 배열의 크기로 `5`이다. `.length`는 메서드가 아닌 필드이므로 괄호 없이 사용한다.
</details>

---

### 문제 93 (Unit 4 - 토픽 4.3) [M]

```java
int[] arr = {2, 4, 6, 8, 10};
int result = 0;
for (int i = 0; i < arr.length; i += 2) {
    result += arr[i];
}
System.out.println(result);
```

출력 결과는?

(A) `12`
(B) `18`
(C) `20`
(D) `30`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`i`는 0, 2, 4 순서로 증가한다(2씩 건너뛰기). `arr[0]=2`, `arr[2]=6`, `arr[4]=10`. `result = 2 + 6 + 10 = 18`. 루프 증감식이 `i++`가 아닌 `i += 2`임에 주의해야 한다.
</details>

---

### 문제 94 (Unit 4 - 토픽 4.3) [M]

```java
int[] vals = {5, 3, 8, 1, 7};
for (int val : vals) {
    val = val * 2;
}
System.out.println(vals[0] + " " + vals[2]);
```

출력 결과는?

(A) `10 16`
(B) `5 8`
(C) `10 8`
(D) `5 16`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

for-each 루프에서 `val`은 배열 원소의 **복사본**이다. `val = val * 2`는 지역 변수 `val`만 변경하고, 원래 배열 `vals`의 원소는 변경되지 않는다. 따라서 `vals[0]`은 여전히 `5`, `vals[2]`는 여전히 `8`이다. 이것은 for-each 루프의 핵심 제한 사항이다.
</details>

---

### 문제 95 (Unit 4 - 토픽 4.4) [H]

```java
String[] words = {"cat", "dog", "ant", "bat"};
String first = words[0];
for (String w : words) {
    if (w.compareTo(first) < 0) {
        first = w;
    }
}
System.out.println(first);
```

출력 결과는?

(A) `cat`
(B) `ant`
(C) `bat`
(D) `dog`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`compareTo`는 사전순(lexicographic) 비교를 한다. `first`는 `"cat"`으로 시작. `"cat".compareTo("cat") == 0` → 갱신 안 됨. `"dog".compareTo("cat") > 0` → 갱신 안 됨. `"ant".compareTo("cat") < 0` → `first = "ant"`. `"bat".compareTo("ant") > 0` → 갱신 안 됨. 최종적으로 사전순 가장 앞선 문자열 `"ant"`가 출력된다.
</details>

---

### 문제 96 (Unit 4 - 토픽 4.5) [M]

```java
int[] arr = {4, 1, 7, 3, 9, 2};
int min = arr[0];
int minIdx = 0;
for (int i = 1; i < arr.length; i++) {
    if (arr[i] < min) {
        min = arr[i];
        minIdx = i;
    }
}
System.out.println(minIdx);
```

출력 결과는?

(A) `1`
(B) `3`
(C) `5`
(D) `0`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

배열에서 최솟값의 인덱스를 찾는 알고리즘이다. `min=4, minIdx=0`으로 시작. `i=1`: `1<4` → `min=1, minIdx=1`. `i=2`: `7<1`? 아니오. `i=3`: `3<1`? 아니오. `i=4`: `9<1`? 아니오. `i=5`: `2<1`? 아니오. 최종 `minIdx = 1`. 최솟값 `1`은 인덱스 `1`에 위치한다.
</details>

---

### 문제 97 (Unit 4 - 토픽 4.5) [H]

```java
int[] arr = {3, 8, 1, 5, 2, 9, 4};
for (int i = 0; i < arr.length - 1; i++) {
    arr[i] = arr[i + 1];
}
arr[arr.length - 1] = 0;
System.out.println(arr[0] + " " + arr[5] + " " + arr[6]);
```

출력 결과는?

(A) `8 4 0`
(B) `8 9 4`
(C) `3 9 0`
(D) `8 9 0`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

이 코드는 배열을 **왼쪽으로 한 칸 시프트**하는 알고리즘이다. 각 원소가 오른쪽 이웃의 값으로 덮어써진다. 시프트 후 배열: `{8, 1, 5, 2, 9, 4, 4}`. 마지막 원소를 `0`으로 설정: `{8, 1, 5, 2, 9, 4, 0}`. `arr[0]=8`, `arr[5]=4`, `arr[6]=0`.
</details>

---

### 문제 98 (Unit 4 - 토픽 4.5) [M]

```java
int[] data = {10, 25, 30, 15, 20};
int target = 30;
int idx = -1;
for (int i = 0; i < data.length; i++) {
    if (data[i] == target) {
        idx = i;
    }
}
System.out.println(idx);
```

출력 결과는?

(A) `-1`
(B) `2`
(C) `3`
(D) `30`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

선형 탐색(linear search)으로 `target` 값 `30`을 찾는다. `data[2] == 30`이므로 `idx = 2`. 루프가 끝까지 돌기 때문에, 만약 동일한 값이 여러 개 있으면 **마지막** 인덱스가 저장된다. 여기서는 `30`이 한 번만 등장하므로 `idx = 2`.
</details>

---

### 문제 99 (Unit 4 - 토픽 4.6) [E]

```java
ArrayList<String> list = new ArrayList<String>();
list.add("A");
list.add("B");
list.add("C");
list.add(1, "X");
System.out.println(list);
```

출력 결과는?

(A) `[A, B, X, C]`
(B) `[A, X, B, C]`
(C) `[X, A, B, C]`
(D) `[A, B, C, X]`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`add(1, "X")`는 인덱스 1에 `"X"`를 삽입하고, 기존 원소들을 오른쪽으로 밀어낸다. 초기 리스트 `[A, B, C]`에서 인덱스 1에 삽입하면 `[A, X, B, C]`가 된다. `add(index, element)` 메서드는 기존 원소를 덮어쓰지 않고 끼워 넣는다는 점이 핵심이다.
</details>

---

### 문제 100 (Unit 4 - 토픽 4.6) [M]

```java
ArrayList<Integer> nums = new ArrayList<Integer>();
nums.add(10);
nums.add(20);
nums.add(30);
nums.set(1, 99);
nums.remove(0);
System.out.println(nums);
```

출력 결과는?

(A) `[99, 30]`
(B) `[10, 99]`
(C) `[20, 30]`
(D) `[99, 20]`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

단계별 추적: 초기 `[10, 20, 30]`. `set(1, 99)` → 인덱스 1의 값을 99로 교체: `[10, 99, 30]`. `remove(0)` → 인덱스 0 제거: `[99, 30]`. `set`은 기존 값을 **교체**하고, `remove`는 해당 인덱스의 원소를 제거한 뒤 나머지를 왼쪽으로 당긴다.
</details>

---

### 문제 101 (Unit 4 - 토픽 4.7) [H]

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(5);
list.add(10);
list.add(15);
list.add(20);
int sum = 0;
for (int i = 0; i < list.size(); i++) {
    if (list.get(i) % 10 == 0) {
        sum += list.remove(i);
    }
}
System.out.println(sum + " " + list.size());
```

출력 결과는?

(A) `30 2`
(B) `10 3`
(C) `10 2`
(D) `20 3`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

ArrayList에서 삭제 시 인덱스 이동에 주의해야 한다. `i=0`: `5 % 10 ≠ 0`. `i=1`: `10 % 10 == 0` → `remove(1)` 반환값 `10`, `sum=10`. 리스트: `[5, 15, 20]` (size=3). `i=2`: `list.get(2) = 20`, `20 % 10 == 0` → `remove(2)` 반환값 `20`, `sum=30`. 리스트: `[5, 15]` (size=2). `i=3`: `3 < 2` → false, 루프 종료. 주의: `15`는 인덱스가 밀려 건너뛰어졌지만 `15 % 10 ≠ 0`이므로 결과에 영향 없다. 출력: `30 2`.
</details>

---

### 문제 102 (Unit 4 - 토픽 4.8) [M]

```java
ArrayList<String> colors = new ArrayList<String>();
colors.add("red");
colors.add("blue");
colors.add("red");
colors.add("green");
String result = "";
for (String c : colors) {
    result += c.substring(0, 1);
}
System.out.println(result);
```

출력 결과는?

(A) `rbrg`
(B) `redblue`
(C) `rbg`
(D) `RBRG`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

for-each 루프로 ArrayList를 순회하며 각 문자열의 첫 글자를 `result`에 누적한다. `"red"→"r"`, `"blue"→"b"`, `"red"→"r"`, `"green"→"g"`. 결과: `"rbrg"`. `substring(0, 1)`은 인덱스 0부터 1 직전까지, 즉 첫 한 글자를 반환한다.
</details>

---

### 문제 103 (Unit 4 - 토픽 4.9) [M]

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(3);
list.add(6);
list.add(4);
list.add(6);
list.add(9);
int i = 0;
while (i < list.size()) {
    if (list.get(i) % 3 == 0) {
        list.remove(i);
    } else {
        i++;
    }
}
System.out.println(list);
```

출력 결과는?

(A) `[6, 4, 6]`
(B) `[4]`
(C) `[4, 6]`
(D) `[6, 4, 6, 9]`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

3의 배수를 모두 제거한다. 핵심: 제거 시 `i`를 증가시키지 않는다(다음 원소가 당겨져 오므로). `i=0`: `3%3==0` → 제거. 리스트: `[6,4,6,9]`. `i=0`: `6%3==0` → 제거. `[4,6,9]`. `i=0`: `4%3≠0` → `i=1`. `i=1`: `6%3==0` → 제거. `[4,9]`. `i=1`: `9%3==0` → 제거. `[4]`. `i=1`: `1 < 1` → false. 최종: `[4]`. 이 패턴은 삭제 중 순회의 올바른 방법이다.
</details>

---

### 문제 104 (Unit 4 - 토픽 4.9) [M]

```java
ArrayList<String> names = new ArrayList<String>();
names.add("Amy");
names.add("Bob");
names.add("Amy");
names.add("Dan");

for (int i = names.size() - 1; i >= 0; i--) {
    if (names.get(i).equals("Amy")) {
        names.remove(i);
    }
}
System.out.println(names);
```

출력 결과는?

(A) `[Bob, Amy, Dan]`
(B) `[Bob, Dan]`
(C) `[Amy, Bob, Dan]`
(D) `[Bob, Amy]`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

**뒤에서부터** 순회하며 삭제하는 패턴이다. 이 방법은 인덱스 이동 문제를 자연스럽게 해결한다. `i=3`: `"Dan"` ≠ `"Amy"`. `i=2`: `"Amy"` → 제거. `[Amy, Bob, Dan]`. `i=1`: `"Bob"` ≠ `"Amy"`. `i=0`: `"Amy"` → 제거. `[Bob, Dan]`. 역순 순회 삭제는 AP CSA에서 중요한 패턴이다.
</details>

---

### 문제 105 (Unit 4 - 토픽 4.10) [M]

```java
public static int search(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) {
            return i;
        }
    }
    return -1;
}
```

`search(new int[]{5, 12, 3, 12, 8}, 12)`를 호출하면 반환값은?

(A) `-1`
(B) `1`
(C) `3`
(D) `2`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

순차 탐색(sequential search)은 배열을 처음부터 끝까지 순서대로 확인한다. `12`는 인덱스 1과 3에 모두 존재하지만, `return`이 실행되면 즉시 메서드를 종료하므로 **처음 발견된** 인덱스 `1`을 반환한다. 순차 탐색의 시간 복잡도는 O(n)이다.
</details>

---

### 문제 106 (Unit 4 - 토픽 4.11) [M]

다음 코드는 어떤 정렬 알고리즘을 구현한 것인가?

```java
for (int i = 1; i < arr.length; i++) {
    int key = arr[i];
    int j = i - 1;
    while (j >= 0 && arr[j] > key) {
        arr[j + 1] = arr[j];
        j--;
    }
    arr[j + 1] = key;
}
```

(A) 선형 검색 (Linear Search)
(B) 선택 정렬 (Selection Sort)
(C) 삽입 정렬 (Insertion Sort)
(D) 병합 정렬 (Merge Sort)

<details>
<summary>정답 및 해설</summary>

**정답: (C)**

이것은 **삽입 정렬(Insertion Sort)** 이다. 핵심 특징: (1) `key = arr[i]`로 현재 원소를 저장, (2) 이미 정렬된 부분에서 `key`보다 큰 원소들을 오른쪽으로 밀어냄, (3) 빈 자리에 `key`를 삽입. 선택 정렬과의 차이: 선택 정렬은 미정렬 부분에서 최솟값을 **찾아서 교환**하고, 삽입 정렬은 원소를 **올바른 위치에 삽입**한다. (A) 선형 검색은 정렬 알고리즘이 아니라 탐색 알고리즘이며, (D) 병합 정렬은 분할 정복 기반의 재귀 구조라 형태가 다르다.
</details>

---

### 문제 107 (Unit 4 - 토픽 4.11) [H]

```java
int[] arr = {9, 5, 2, 7};
// 선택 정렬 1회전(pass) 수행
int minIdx = 0;
for (int j = 1; j < arr.length; j++) {
    if (arr[j] < arr[minIdx]) {
        minIdx = j;
    }
}
int temp = arr[0];
arr[0] = arr[minIdx];
arr[minIdx] = temp;
```

위 코드 실행 후 `arr`의 상태는?

(A) `{2, 5, 9, 7}`
(B) `{2, 5, 7, 9}`
(C) `{5, 9, 2, 7}`
(D) `{2, 9, 5, 7}`

<details>
<summary>정답 및 해설</summary>

**정답: (A)**

선택 정렬의 1회전은 (1) 전체에서 최솟값의 인덱스를 찾고, (2) 첫 번째 원소와 교환한다. `minIdx=0`으로 시작. `j=1`: `5<9` → `minIdx=1`. `j=2`: `2<5` → `minIdx=2`. `j=3`: `7<2`? 아니오. 최솟값은 `arr[2]=2`. 교환: `arr[0]`과 `arr[2]`를 교환. `{9,5,2,7}` → `{2,5,9,7}`. 선택 정렬 1회전은 최솟값만 올바른 위치에 놓고, 나머지 원소의 상대적 위치는 교환 외에 변하지 않는다.
</details>

---

### 문제 108 (Unit 4 - 토픽 4.12) [E]

```java
int[][] grid = new int[3][4];
System.out.println(grid.length + " " + grid[0].length);
```

출력 결과는?

(A) `4 3`
(B) `3 4`
(C) `12 3`
(D) `3 12`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`new int[3][4]`는 3행 4열의 2D 배열을 생성한다. `grid.length`는 **행의 수** = 3. `grid[0].length`는 **첫 번째 행의 열 수** = 4. 2D 배열에서 `배열.length`는 행 수, `배열[i].length`는 해당 행의 열 수임을 기억해야 한다.
</details>

---

### 문제 109 (Unit 4 - 토픽 4.12) [E]

```java
int[][] mat = {{1, 2, 3}, {4, 5, 6}};
System.out.println(mat[1][2] + mat[0][1]);
```

출력 결과는?

(A) `7`
(B) `8`
(C) `9`
(D) `11`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

`mat[1][2]`는 1행 2열 = `6`. `mat[0][1]`은 0행 1열 = `2`. `6 + 2 = 8`. 2D 배열 인덱스는 `[행][열]` 순서이며 모두 0부터 시작한다. 행렬로 보면: 행0 = `{1,2,3}`, 행1 = `{4,5,6}`.
</details>

---

### 문제 110 (Unit 4 - 토픽 4.13) [H]

```java
int[][] grid = {{1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}};
int sum = 0;
for (int c = 0; c < grid[0].length; c++) {
    for (int r = 0; r < grid.length; r++) {
        sum += grid[r][c];
        if (sum > 10) {
            System.out.println(sum);
            return;
        }
    }
}
```

출력 결과는?

(A) `10`
(B) `12`
(C) `15`
(D) `6`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

이것은 **열 우선(column-major)** 순회이다. 바깥 루프가 열(`c`), 안쪽 루프가 행(`r`)을 돈다. 순서: `grid[0][0]=1`(sum=1), `grid[1][0]=4`(sum=5), `grid[2][0]=7`(sum=12). `12 > 10`이므로 `12`를 출력하고 종료. 행 우선 순회였다면 `grid[0][0], grid[0][1], grid[0][2], grid[1][0]...` 순이었을 것이다.
</details>

---

### 문제 111 (Unit 4 - 토픽 4.14) [E]

다음 코드에서 빈칸에 들어갈 올바른 코드는?

```java
import java.util.Scanner;
import java.io.File;

Scanner sc = new Scanner(___________);
while (sc.hasNext()) {
    System.out.println(sc.nextLine());
}
sc.close();
```

(A) `"data.txt"`
(B) `new File("data.txt")`
(C) `File("data.txt")`
(D) `System.in("data.txt")`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

파일에서 데이터를 읽으려면 `Scanner`에 `File` 객체를 전달해야 한다. `new File("data.txt")`로 File 객체를 생성하여 Scanner 생성자에 넘긴다. (A) 문자열을 직접 전달하면 그 문자열 자체를 파싱하는 Scanner가 된다. (C) `new` 키워드 없이 객체 생성 불가. (D) `System.in`은 키보드 입력용이며 인자를 받지 않는다.
</details>

---

### 문제 112 (Unit 4 - 토픽 4.14) [M]

```java
// data.txt 내용:
// 10
// 20
// 30

Scanner sc = new Scanner(new File("data.txt"));
int total = 0;
while (sc.hasNext()) {
    total += sc.nextInt();
}
System.out.println(total);
sc.close();
```

출력 결과는?

(A) `10`
(B) `30`
(C) `60`
(D) 컴파일 에러

<details>
<summary>정답 및 해설</summary>

**정답: (C)**

`hasNext()`는 읽을 토큰이 더 있는지 확인하고, `nextInt()`는 다음 토큰을 정수로 읽는다. 파일에 `10`, `20`, `30`이 있으므로 세 번 반복하여 `total = 10 + 20 + 30 = 60`. AP CSA Quick Reference에 포함된 Scanner 메서드는 `hasNext()`, `nextInt()`, `nextDouble()`, `nextBoolean()`, `nextLine()`, `next()`, `close()`이며, `hasNext()` + `nextInt()` 조합이 파일의 모든 정수를 읽는 표준 패턴이다.
</details>

---

### 문제 113 (Unit 4 - 토픽 4.15) [M]

```java
ArrayList<Integer> scores = new ArrayList<Integer>();
scores.add(85);
scores.add(92);
scores.add(78);
scores.add(95);
scores.add(88);

double avg = 0;
for (int s : scores) {
    avg += s;
}
avg /= scores.size();

int count = 0;
for (int s : scores) {
    if (s > avg) {
        count++;
    }
}
System.out.println(count);
```

출력 결과는?

(A) `2`
(B) `3`
(C) `4`
(D) `1`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

먼저 평균을 구한다: `(85+92+78+95+88) / 5 = 438 / 5 = 87.6`. 평균 `87.6`보다 큰 점수: `85`(아니오), `92`(예), `78`(아니오), `95`(예), `88`(예). 총 3개. 데이터셋에서 평균보다 큰 원소의 개수를 구하는 것은 전형적인 데이터 처리 패턴이다.
</details>

---

### 문제 114 (Unit 4 - 토픽 4.16) [M]

```java
public static int mystery(int n) {
    if (n <= 1) {
        return n;
    }
    return mystery(n - 1) + mystery(n - 2);
}
```

`mystery(5)`의 반환값은?

(A) `3`
(B) `5`
(C) `8`
(D) `10`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

이것은 **피보나치 수열**의 재귀 구현이다. 추적:
- `mystery(5)` = `mystery(4)` + `mystery(3)`
- `mystery(4)` = `mystery(3)` + `mystery(2)`
- `mystery(3)` = `mystery(2)` + `mystery(1)` = `1 + 1 = 2`
- `mystery(2)` = `mystery(1)` + `mystery(0)` = `1 + 0 = 1`
- `mystery(4)` = `2 + 1 = 3`
- `mystery(5)` = `3 + 2 = 5`

피보나치 수열: 0, 1, 1, 2, 3, **5**, 8, ...
</details>

---

### 문제 115 (Unit 4 - 토픽 4.16) [H]

```java
public static String mystery(String s) {
    if (s.length() <= 1) {
        return s;
    }
    return mystery(s.substring(1)) + s.substring(0, 1);
}
```

`mystery("ABCD")`의 반환값은?

(A) `"ABCD"`
(B) `"DCBA"`
(C) `"BCDA"`
(D) `"DABC"`

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

이 재귀 메서드는 문자열을 **뒤집는다**. 추적:
- `mystery("ABCD")` = `mystery("BCD")` + `"A"`
- `mystery("BCD")` = `mystery("CD")` + `"B"`
- `mystery("CD")` = `mystery("D")` + `"C"`
- `mystery("D")` = `"D"` (base case)
- 역순으로 결합: `"D"` + `"C"` = `"DC"`, `"DC"` + `"B"` = `"DCB"`, `"DCB"` + `"A"` = `"DCBA"`

재귀 추적 시 호출 스택을 따라가며 반환값을 역순으로 결합하는 과정을 이해해야 한다.
</details>

---

## 난이도 분포 요약

| 난이도 | 문제 수 | 비율 |
|--------|---------|------|
| 쉬움 (E) | 33문제 | 29% |
| 보통 (M) | 59문제 | 52% |
| 어려움 (H) | 25문제 | 22% |

## Unit별 분포

| Unit | 문제 번호 | 문제 수 |
|------|-----------|---------|
| Unit 1: Using Objects and Methods | 1~4, 6~40 | 39문제 |
| Unit 2: Selection and Iteration | 41~67, 69~78, 80 | 38문제 |
| Unit 3: Class Creation | 81~90 | 10문제 |
| Unit 4: Data Collections | 68, 79, 91~120 | 32문제 |

## 주요 함정 체크리스트

- [ ] 정수 나눗셈 (문제 4, 13)
- [ ] 캐스팅 버림/truncation (문제 3, 9)
- [ ] `substring()` 범위 — endIndex 미포함 (문제 18, 22, 28, 32)
- [ ] `==` vs `equals()` (문제 19, 24, 29)
- [ ] String 불변성 (문제 21, 38)
- [ ] De Morgan의 법칙 (문제 43, 44, 48)
- [ ] Off-by-one 에러 (문제 58, 75)
- [ ] 단축 평가/short-circuit evaluation (문제 47, 51)
- [ ] `NullPointerException` (문제 23, 39)
- [ ] 중괄호 없는 if 범위 (문제 41, 42)
- [ ] Dangling else (문제 46)
- [ ] 부동소수점 비교 (문제 8, 49)
- [ ] Integer overflow (문제 15)
- [ ] private 접근 제어 — 외부 직접 접근 불가 (문제 81)
- [ ] 인스턴스 변수 기본값 — String은 null, int는 0 (문제 83)
- [ ] 매개변수와 인스턴스 변수 이름 충돌 — this 미사용 시 (문제 85)
- [ ] static 메서드에서 인스턴스 변수 접근 불가 (문제 88)
- [ ] 생성자에 void 반환 타입 → 일반 메서드 (문제 90)
- [ ] for-each 루프는 배열 원소 수정 불가 — 복사본만 변경 (문제 94)
- [ ] ArrayList remove 중 인덱스 이동 — 원소 건너뛰기 (문제 101, 103)
- [ ] 역순 순회 삭제 패턴 (문제 104)
- [ ] 2D 배열 행/열 혼동 — grid.length는 행, grid[0].length는 열 (문제 108)
- [ ] 열 우선(column-major) vs 행 우선(row-major) 순회 (문제 110)
- [ ] File/Scanner throws IOException 누락 (문제 111, 112)
- [ ] 재귀 base case 도달 경로 추적 (문제 114, 115)

---

## 보너스: 추가 File/Scanner + 재귀 MCQ (문제 116-120)

> 2025-26 신규 토픽 보강을 위한 추가 문제입니다.

---

### 문제 116 (Unit 4 - 토픽 4.14) [E]

다음 중 파일에서 데이터를 읽기 위해 Scanner를 생성하는 올바른 코드는?

**(A)**
```java
Scanner sc = new Scanner("data.txt");
```
**(B)**
```java
Scanner sc = new Scanner(new File("data.txt"));
```
**(C)**
```java
Scanner sc = Scanner.open("data.txt");
```
**(D)**
```java
Scanner sc = File.read("data.txt");
```

<details>
<summary>정답 및 해설</summary>

**정답: (B)**

- **(A)** `new Scanner("data.txt")`는 문자열 `"data.txt"` 자체를 입력으로 사용. 파일을 읽지 않음!
- **(B)** 정답. `new File("data.txt")`로 파일 객체를 만들고 Scanner에 전달.
- **(C), (D)** 존재하지 않는 메서드.

**주의**: `new Scanner(new File(...))` 사용 시 반드시 `throws IOException` 선언 필요.
</details>

---

### 문제 117 (Unit 4 - 토픽 4.14) [M]

파일 `nums.txt`의 내용이 다음과 같을 때:
```
5
10
15
```

다음 코드의 출력은?

```java
Scanner sc = new Scanner(new File("nums.txt"));
int total = 0;
while (sc.hasNext()) {
    total += sc.nextInt();
}
System.out.println(total);
```

**(A)** `30` **(B)** `15` **(C)** `510` **(D)** 컴파일 에러

<details>
<summary>정답 및 해설</summary>

**정답: (A) `30`**

- `nextInt()`로 5, 10, 15를 순서대로 읽고 합산: 5+10+15 = 30
- `hasNext()`는 읽을 토큰이 남아있는 동안 true
- **(C)** `"510"`: 문자열 연결이 아닌 정수 덧셈이므로 틀림
- **(D)**: `throws IOException`이 있으면 컴파일 에러 아님 (문제에서 메서드 선언은 생략)
</details>

---

### 문제 118 (Unit 4 - 토픽 4.14) [H]

파일 `mixed.txt`의 내용이 다음과 같을 때:
```
3
hello
world
```

다음 코드의 출력은?

```java
Scanner sc = new Scanner(new File("mixed.txt"));
int n = sc.nextInt();
String s = sc.nextLine();
System.out.println(n + "|" + s + "|");
```

**(A)** `3|hello|` **(B)** `3||` **(C)** `3| hello|` **(D)** 런타임 에러

<details>
<summary>정답 및 해설</summary>

**정답: (B) `3||`**

- `nextInt()`는 `3`을 읽지만 그 뒤의 개행문자(`\n`)를 남김
- `nextLine()`은 남은 개행문자까지만 읽어서 빈 문자열 `""` 반환
- 따라서 `s = ""`이고 출력은 `"3||"`

**이것은 AP CSA에서 가장 자주 나오는 Scanner 함정입니다.**
해결법: `nextInt()` 후 `sc.nextLine()`을 한 번 더 호출하여 개행 소비.
</details>

---

### 문제 119 (Unit 4 - 토픽 4.16) [M]

```java
public static int mystery(int n) {
    if (n <= 1) return n;
    return mystery(n - 1) + mystery(n - 2);
}
```

`mystery(6)`의 반환값은?

**(A)** `5` **(B)** `8` **(C)** `13` **(D)** `6`

<details>
<summary>정답 및 해설</summary>

**정답: (B) `8`**

피보나치 수열: mystery(0)=0, mystery(1)=1, mystery(2)=1, mystery(3)=2, mystery(4)=3, mystery(5)=5, mystery(6)=8

호출 트리:
```
m(6) = m(5) + m(4) = 5 + 3 = 8
m(5) = m(4) + m(3) = 3 + 2 = 5
m(4) = m(3) + m(2) = 2 + 1 = 3
m(3) = m(2) + m(1) = 1 + 1 = 2
m(2) = m(1) + m(0) = 1 + 0 = 1
```
</details>

---

### 문제 120 (Unit 4 - 토픽 4.16) [H]

```java
public static String mystery(String s) {
    if (s.length() <= 1) return s;
    return mystery(s.substring(1)) + s.substring(0, 1);
}
```

`mystery("ABCD")`의 반환값은?

**(A)** `"ABCD"` **(B)** `"DCBA"` **(C)** `"BCDA"` **(D)** `"DABC"`

<details>
<summary>정답 및 해설</summary>

**정답: (B) `"DCBA"`**

호출 추적:
```
mystery("ABCD") = mystery("BCD") + "A"
mystery("BCD")  = mystery("CD") + "B"
mystery("CD")   = mystery("D") + "C"
mystery("D")    = "D"  (base case)
```

역순 조립: `"D"` + `"C"` = `"DC"` + `"B"` = `"DCB"` + `"A"` = `"DCBA"`

이 재귀는 문자열을 **뒤집는** 알고리즘입니다.
</details>
- [ ] 재귀 호출 추적 — 호출 스택과 반환값 결합 순서 (문제 114, 115)
