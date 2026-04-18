# Java Quick Reference 한국어 상세 해설

> AP CSA 시험에서 제공되는 Java Quick Reference의 모든 클래스/메서드를 한국어로 해설한다.
> 각 메서드마다 **시그니처 → 설명 → 코드 예제 → 시험 주의점** 순서로 정리.

---

## 1. String Class

String은 **불변(immutable)** 객체이다. 모든 메서드는 원본을 변경하지 않고 새 String을 반환한다.

### `String(String str)`
**생성자** — 문자열 객체를 생성한다.

```java
String s1 = new String("Hello");
String s2 = "Hello"; // 리터럴 방식 (더 일반적)
```

> **시험 주의점**: `new String("Hello")`로 만든 것과 리터럴 `"Hello"`는 `equals()`로는 같지만, `==`로는 다를 수 있다.

---

### `int length()`
문자열의 **길이(문자 수)**를 반환한다.

```java
String s = "Hello";
s.length(); // 5

String empty = "";
empty.length(); // 0
```

> **시험 주의점**:
> - 배열은 `arr.length` (괄호 없음), String은 `s.length()` (괄호 있음!)
> - 마지막 문자의 인덱스는 `length() - 1`

---

### `String substring(int from, int to)`
인덱스 `from`부터 `to - 1`까지의 부분 문자열을 반환한다.

```java
String s = "ABCDE";
//          01234  ← 인덱스

s.substring(1, 3);  // "BC"  (인덱스 1, 2)
s.substring(0, 5);  // "ABCDE" (전체)
s.substring(2, 2);  // ""  (빈 문자열)
s.substring(0, 1);  // "A"  (첫 글자만)
```

> **시험 주의점 (매우 중요!)**:
> - `to`는 **미포함**! 범위는 `[from, to)` 이다.
> - `from == to`이면 빈 문자열 `""` 반환
> - `from < 0` 또는 `to > length()` 이면 `StringIndexOutOfBoundsException`

---

### `String substring(int from)`
인덱스 `from`부터 **끝까지** 부분 문자열을 반환한다.

```java
String s = "ABCDE";

s.substring(2);  // "CDE" (인덱스 2부터 끝까지)
s.substring(0);  // "ABCDE" (전체)
s.substring(5);  // "" (빈 문자열, length와 같으면 빈 문자열)
```

> **시험 주의점**: `substring(from)`은 `substring(from, length())`와 동일하다.

---

### `int indexOf(String str)`
문자열 `str`이 **처음 등장하는 인덱스**를 반환한다. 없으면 **-1**.

```java
String s = "ABCABC";

s.indexOf("B");    // 1
s.indexOf("BC");   // 1
s.indexOf("ABC");  // 0
s.indexOf("XYZ");  // -1 (없음)
s.indexOf("");     // 0 (빈 문자열은 항상 0)
```

> **시험 주의점**:
> - 못 찾으면 **-1 반환** (예외가 아님!)
> - 여러 번 등장하면 **첫 번째** 위치만 반환
> - 대소문자를 구분한다: `"abc".indexOf("A")` → `-1`

---

### `boolean equals(Object other)`
두 문자열의 **내용이 같은지** 비교한다.

```java
String a = new String("hello");
String b = new String("hello");
String c = "HELLO";

a.equals(b);  // true  (내용 비교)
a == b;       // false (주소 비교!)
a.equals(c);  // false (대소문자 다름)
```

> **시험 주의점 (가장 자주 출제!)**:
> - `==`는 **주소(참조)** 비교, `equals()`는 **값(내용)** 비교
> - String 비교는 **무조건 `equals()`** 사용
> - `null.equals(...)` 하면 NullPointerException → `"literal".equals(변수)` 패턴이 더 안전

---

### `int compareTo(String other)`
사전순(lexicographic) 비교. 결과는 **음수 / 0 / 양수**.

```java
"apple".compareTo("banana");  // 음수 (apple이 앞)
"banana".compareTo("apple");  // 양수 (banana가 뒤)
"apple".compareTo("apple");   // 0 (같음)
"Apple".compareTo("apple");   // 음수 (대문자가 소문자보다 앞, 유니코드 기준)
```

| 반환값 | 의미 |
|--------|------|
| **음수** | 호출 객체가 사전순으로 **앞** |
| **0** | 두 문자열이 **같음** |
| **양수** | 호출 객체가 사전순으로 **뒤** |

> **시험 주의점**:
> - 정확한 숫자값은 중요하지 않음. **부호(음/0/양)**만 판단하면 됨
> - 대문자는 소문자보다 앞 (A=65, a=97)
> - `"a".compareTo("b")` → 음수 = a가 b보다 앞

---

### `String[] split(String del)`
구분자 `del`로 문자열을 나누어 **String 배열**을 반환한다.

```java
String csv = "apple,banana,cherry";
String[] fruits = csv.split(",");
// fruits[0] = "apple"
// fruits[1] = "banana"
// fruits[2] = "cherry"

String sentence = "Hello World";
String[] words = sentence.split(" ");
// words[0] = "Hello"
// words[1] = "World"
```

> **시험 주의점**:
> - 구분자 자체는 결과에 포함되지 않음
> - 구분자가 정규식(regex)으로 해석됨 — 시험에서는 단순 문자열만 나옴
> - 결과는 `String[]` 배열이므로 `.length` (괄호 없음)로 크기 확인

---

## 2. Integer Class

### `Integer.MIN_VALUE`
`int` 타입의 **최솟값**: `-2147483648` (약 -21억)

```java
int min = Integer.MIN_VALUE; // -2147483648
```

### `Integer.MAX_VALUE`
`int` 타입의 **최댓값**: `2147483647` (약 21억)

```java
int max = Integer.MAX_VALUE; // 2147483647
```

> **시험 주의점**:
> - 최댓값/최솟값 초기화에 자주 사용됨
> - 예: 배열에서 최솟값 찾기 → `int min = Integer.MAX_VALUE;`로 초기화
> - `MAX_VALUE + 1`은 오버플로우로 `MIN_VALUE`가 됨 (시험에 나올 수 있음)

---

### `static int parseInt(String s)`
문자열을 `int`로 변환한다.

```java
int n = Integer.parseInt("42");   // 42
int m = Integer.parseInt("-7");   // -7
// Integer.parseInt("abc"); // NumberFormatException!
```

> **시험 주의점**: 숫자가 아닌 문자열을 넣으면 `NumberFormatException` 발생

---

## 3. Double Class

### `static double parseDouble(String s)`
문자열을 `double`로 변환한다.

```java
double d = Double.parseDouble("3.14");  // 3.14
double e = Double.parseDouble("42");    // 42.0
```

> **시험 주의점**: `parseInt`와 마찬가지로, 숫자가 아닌 문자열은 예외 발생

---

## 4. Math Class

모든 메서드가 `static`이므로 **`Math.메서드()`**로 호출한다. 객체 생성 불필요.

### `static int abs(int x)` / `static double abs(double x)`
**절댓값**을 반환한다.

```java
Math.abs(-5);    // 5
Math.abs(5);     // 5
Math.abs(-3.14); // 3.14
```

> **시험 주의점**: int 넣으면 int 반환, double 넣으면 double 반환 (오버로딩)

---

### `static double pow(double base, double exponent)`
`base`의 `exponent` 거듭제곱을 반환한다.

```java
Math.pow(2, 3);    // 8.0  (2의 3제곱)
Math.pow(3, 2);    // 9.0  (3의 2제곱)
Math.pow(4, 0.5);  // 2.0  (4의 제곱근)
Math.pow(2, -1);   // 0.5  (2의 -1제곱 = 1/2)
```

> **시험 주의점 (자주 출제!)**:
> - **항상 `double`을 반환**한다! `int`에 직접 대입 불가
> - `int result = Math.pow(2, 3);` → **컴파일 에러!**
> - `int result = (int) Math.pow(2, 3);` → OK (명시적 캐스팅 필요)

---

### `static double sqrt(double x)`
**제곱근**을 반환한다.

```java
Math.sqrt(16);   // 4.0
Math.sqrt(2);    // 1.4142135623730951
Math.sqrt(0);    // 0.0
```

> **시험 주의점**: 반환 타입은 `double`. 음수를 넣으면 `NaN` 반환.

---

### `static double random()`
**0.0 이상 1.0 미만**의 난수를 반환한다.

```java
Math.random();  // 예: 0.7234... (범위: [0.0, 1.0))
```

**자주 쓰는 패턴:**

```java
// 0 ~ 9 정수
int n = (int)(Math.random() * 10);

// 1 ~ 6 정수 (주사위)
int dice = (int)(Math.random() * 6) + 1;

// a ~ b 정수 (a 이상 b 이하)
int rand = (int)(Math.random() * (b - a + 1)) + a;
```

> **시험 주의점**:
> - `1.0`은 **포함되지 않음!** 범위는 `[0.0, 1.0)`
> - `(int)` 캐스팅은 소수점 **버림** (반올림 아님)
> - `(int)(Math.random() * 10)` → 0~9 (10은 나올 수 없음)
> - 괄호 위치 중요: `(int)Math.random() * 10` → 항상 0! (먼저 int 캐스팅하면 0이 됨)

---

## 5. ArrayList Class

`java.util.ArrayList`를 import해야 사용 가능. 크기가 자동으로 조절되는 리스트.

> **기본 원칙**: ArrayList는 **객체만** 저장 가능. 기본형은 autoboxing으로 자동 변환.
> - `ArrayList<Integer>` O, `ArrayList<int>` X

### `int size()`
리스트의 **요소 개수**를 반환한다.

```java
ArrayList<String> list = new ArrayList<>();
list.size(); // 0

list.add("A");
list.add("B");
list.size(); // 2
```

> **시험 주의점**:
> - 배열은 `.length` (괄호 없음), ArrayList는 `.size()` (괄호 있음!)
> - String은 `.length()` (괄호 있음) — 셋 다 다르니 혼동 주의

---

### `boolean add(E obj)`
리스트 **끝에** 요소를 추가한다. 항상 `true` 반환.

```java
ArrayList<String> list = new ArrayList<>();
list.add("A"); // list: ["A"]
list.add("B"); // list: ["A", "B"]
list.add("C"); // list: ["A", "B", "C"]
```

> **시험 주의점**: 반환값은 항상 `true`이므로 시험에서 반환값을 물을 일은 거의 없음

---

### `void add(int index, E obj)`
지정한 인덱스에 요소를 **삽입**한다. 기존 요소들은 **뒤로 밀린다**.

```java
ArrayList<String> list = new ArrayList<>();
list.add("A");
list.add("C");
// list: ["A", "C"]

list.add(1, "B"); // 인덱스 1에 "B" 삽입
// list: ["A", "B", "C"]  (C가 뒤로 밀림)
```

> **시험 주의점**:
> - 반환 타입이 `void` (값을 반환하지 않음!)
> - `add(E obj)`와 `add(int index, E obj)` 두 가지 오버로딩을 구분
> - 삽입 후 뒤쪽 요소들의 인덱스가 **1씩 증가**

---

### `E get(int index)`
지정한 인덱스의 요소를 **반환**한다.

```java
ArrayList<String> list = new ArrayList<>();
list.add("A");
list.add("B");

list.get(0); // "A"
list.get(1); // "B"
// list.get(2); // IndexOutOfBoundsException!
```

> **시험 주의점**:
> - 유효 인덱스: `0` ~ `size() - 1`
> - 배열은 `arr[i]`, ArrayList는 `list.get(i)` — 대괄호 사용 불가!

---

### `E set(int index, E obj)`
지정한 인덱스의 요소를 **교체**하고, **이전 값을 반환**한다.

```java
ArrayList<String> list = new ArrayList<>();
list.add("A");
list.add("B");
list.add("C");

String old = list.set(1, "X"); // old = "B", list: ["A", "X", "C"]
```

> **시험 주의점**:
> - **이전 값을 반환**한다! (반환값을 활용하는 문제가 나올 수 있음)
> - 리스트 크기는 변하지 않음 (추가/삭제가 아닌 교체)

---

### `E remove(int index)`
지정한 인덱스의 요소를 **삭제**하고, **삭제된 값을 반환**한다. 뒤쪽 요소들이 **앞으로 밀린다**.

```java
ArrayList<String> list = new ArrayList<>();
list.add("A");
list.add("B");
list.add("C");
// list: ["A", "B", "C"]

String removed = list.remove(1); // removed = "B", list: ["A", "C"]
// "C"의 인덱스가 2에서 1로 변경됨!
```

> **시험 주의점 (FRQ Q3 핵심!)**:
> - **삭제된 값을 반환**한다!
> - 삭제 후 뒤쪽 요소의 인덱스가 **1씩 감소**
> - 루프에서 삭제할 때 인덱스 조정 필수:
>
> ```java
> // 방법 1: 뒤에서부터 순회
> for (int i = list.size() - 1; i >= 0; i--) {
>     if (조건) list.remove(i);
> }
>
> // 방법 2: 삭제 시 인덱스 보정
> for (int i = 0; i < list.size(); i++) {
>     if (조건) {
>         list.remove(i);
>         i--; // 인덱스 보정
>     }
> }
> ```

---

## 6. File Class

### `File(String pathname)`
파일 경로로 File 객체를 생성한다.

```java
File f = new File("data.txt");
```

> **시험 주의점**: File 객체를 만드는 것 자체가 파일을 생성하는 것은 아님. Scanner에 전달하여 읽기에 사용.

---

## 7. Scanner Class

`java.util.Scanner`를 import해야 사용 가능. 입력을 읽는 클래스.

> **CED EXCLUSION (시험 범위 밖):** 키보드 입력(`System.in`)은 시험 범위 밖이다. AP CSA 시험에서 Scanner는 **파일 입력(`new Scanner(new File(...))`)**만 출제된다. `new Scanner(System.in)`을 사용하는 코드는 시험에 나오지 않는다.

### `Scanner(File f)`
파일에서 입력을 읽는 Scanner를 생성한다.

```java
Scanner sc = new Scanner(new File("data.txt"));
```

> **시험 주의점**: 파일 입출력 시 메서드 선언부에 `throws IOException`이 필요. AP CSA에서는 `throws IOException` 방식만 사용 (try-catch는 시험 범위 밖)

---

### `int nextInt()`
다음 정수를 읽어 반환한다.

```java
Scanner sc = new Scanner(new File("data.txt"));
// 파일 내용: 42 17
int a = sc.nextInt(); // 42
int b = sc.nextInt(); // 17
```

---

### `double nextDouble()`
다음 실수를 읽어 반환한다.

```java
double d = sc.nextDouble(); // 3.14
```

---

### `boolean nextBoolean()`
다음 boolean 값을 읽어 반환한다.

```java
boolean b = sc.nextBoolean(); // true 또는 false
```

---

### `String nextLine()`
**줄 전체**를 읽어 반환한다 (줄바꿈 문자까지 소비).

```java
Scanner sc = new Scanner(new File("data.txt"));
// 파일 내용:
// Hello World
// Java is fun
String line1 = sc.nextLine(); // "Hello World"
String line2 = sc.nextLine(); // "Java is fun"
```

> **시험 주의점 (중요!)**:
> - `nextInt()` 후 `nextLine()`을 호출하면, 남은 줄바꿈 문자를 읽어서 빈 문자열을 반환!
> - 해결: `nextInt()` 후 `nextLine()`을 한 번 더 호출하여 줄바꿈 소비
>
> ```java
> int n = sc.nextInt();
> sc.nextLine(); // 줄바꿈 소비 (버림)
> String s = sc.nextLine(); // 실제 다음 줄 읽기
> ```

> **CED EXCLUSION (시험 범위 밖):** CED p.106에 따르면 "Writing or analyzing code that uses both nextLine and other Scanner methods on the same input source is outside the scope." 즉, nextInt() 후 nextLine() 혼용 문제는 **시험에 나오지 않는다.** 실무에서는 알아두면 좋지만 시험 준비에서는 신경 쓰지 않아도 된다.

---

### `String next()`
다음 **토큰(단어)**을 읽어 반환한다 (공백 기준).

```java
Scanner sc = new Scanner(new File("data.txt"));
// 파일 내용: Hello World
String word1 = sc.next(); // "Hello"
String word2 = sc.next(); // "World"
```

> **시험 주의점**:
> - `next()`는 공백까지만 읽음, `nextLine()`은 줄 전체를 읽음
> - `next()`는 앞의 공백을 건너뜀

---

### `boolean hasNext()`
읽을 토큰이 **남아있는지** 확인한다.

```java
Scanner sc = new Scanner(new File("data.txt"));
while (sc.hasNext()) {
    String word = sc.next();
    System.out.println(word);
}
```

> **시험 주의점**: 파일 끝까지 읽을 때 `while (sc.hasNext())` 패턴으로 자주 사용

---

### `hasNextInt()` / `hasNextDouble()` / `hasNextBoolean()` / `hasNextLine()`

> ❌ **CED EXCLUSION (시험 범위 밖)**: AP CSA 2025-26 Java Quick Reference에는 **`hasNext()` 한 가지만** 등재되어 있다. `hasNextInt`, `hasNextDouble`, `hasNextBoolean`, `hasNextLine` 등 **타입별 변형은 시험 범위 밖**이며 시험 답안에 사용하면 안 된다.
>
> 자세한 검증 근거는 `/mnt/20t/study/AP_CSA/공식_시험범위_검증.md` §5.7을 참조.

**시험 답안 패턴**: 파일 끝까지 읽을 때는 항상 `while (sc.hasNext())` 만 사용한다. 파일 내용의 타입(int/double/String)을 알고 있다고 가정하고 적절한 `nextInt() / nextDouble() / nextLine() / next()` 를 호출하면 된다.

```java
// 시험 범위 안 — hasNext() + 알맞은 nextXxx() 조합
Scanner sc = new Scanner(new File("numbers.txt"));
int sum = 0;
while (sc.hasNext()) {        // hasNextInt() ❌ → hasNext() ✅
    sum += sc.nextInt();
}
sc.close();
```

---

### `void close()`
Scanner를 닫고 관련 리소스를 해제한다.

```java
Scanner sc = new Scanner(new File("data.txt"));
// ... 읽기 작업 ...
sc.close();
```

> **시험 주의점**: 사용 후 `close()`를 호출하는 것이 좋은 습관이지만, 시험에서 이것 때문에 감점되는 경우는 드뭄

---

## 8. Object Class

모든 Java 클래스의 **최상위 부모 클래스**. 모든 클래스가 이 메서드들을 상속받는다.

### `boolean equals(Object other)`
두 객체가 **같은지** 비교한다.

```java
Object a = new Object();
Object b = new Object();
a.equals(b); // false (기본 구현은 == 과 동일, 주소 비교)

// String 등은 내용 비교를 함
String s1 = new String("hi");
String s2 = new String("hi");
s1.equals(s2); // true (String의 equals()는 내용 비교)
```

> **시험 주의점**:
> - Object의 기본 `equals()`는 `==`와 동일 (주소 비교)
> - String, Integer 등의 `equals()`는 **값 비교**로 동작
> - 직접 만든 클래스의 `equals()`는 기본적으로 주소 비교 (커스텀 작성은 시험 범위 밖)

---

### `String toString()`
객체의 **문자열 표현**을 반환한다.

```java
Object obj = new Object();
obj.toString(); // "java.lang.Object@1a2b3c" (클래스명@해시코드)

// MCQ 트레이싱 예시 — 이미 오버라이드된 toString의 출력 결과 묻기는 ✅ 시험 범위 안
class Student {
    private String name;
    private int grade;

    public String toString() {        // ⚠️ 학생이 직접 작성하는 것은 OUT — 문제 코드에 등장만 가능
        return name + " (Grade " + grade + ")";
    }
}

Student s = new Student("Kim", 11);
System.out.println(s);  // "Kim (Grade 11)" — println(객체)이 자동으로 toString() 호출 (1.15.A.5, IN)
```

> ❌ **CED EXCLUSION (시험 범위 밖) — 작성 금지**: AP CSA 2025-26에서 학생이 **`toString()` / `equals()` 오버라이드를 직접 작성**하는 것은 시험 범위 밖이다 (CED 1.15, 2.6 EXCLUSION).
>
> | 시나리오 | 시험 범위 | 근거 |
> |---|---|---|
> | 이미 작성된 `toString` 오버라이드 클래스를 보여주고 `println` 결과 묻기 (트레이싱) | ✅ IN | 1.15.A.5 |
> | FRQ에서 학생에게 `toString` 오버라이드 작성 요구 | ❌ OUT | 1.15 EXCLUSION |
> | 표시용 메서드를 학생이 작성해야 할 때 | `getInfo()`, `getDescription()` 등 **명시적 이름**으로 정의 후 호출 | — |
>
> 자세한 검증 근거는 `/mnt/20t/study/AP_CSA/공식_시험범위_검증.md` §5.8, §8을 참조.

> **시험 주의점**:
> - `System.out.println(객체)`는 자동으로 `toString()` 호출 (트레이싱 IN — 출력 결과 묻기는 출제 가능)
> - `"문자열" + 객체`도 자동으로 `toString()` 호출 (트레이싱 IN)
> - 기본 `toString()`은 `클래스명@해시코드` 형태로 출력됨 (유용하지 않음)
> - **학생이 `toString()` 메서드를 직접 작성하는 것은 2025-26 시험 범위 밖**(CED 1.15 EXCLUSION). FRQ Q2 클래스 설계 문제에서 표시용 메서드가 필요하면 `getInfo()`, `getDescription()` 등 **명시적 이름**으로 작성한 뒤 `obj.getInfo()` 형태로 명시적으로 호출한다. `@Override`, `extends`, `super` 모두 시험 범위 밖.

---

## 한눈에 보는 요약표

### 크기/길이 구하기
| 대상 | 문법 | 괄호 |
|------|------|------|
| 배열 `int[]` | `arr.length` | **없음** |
| String | `s.length()` | **있음** |
| ArrayList | `list.size()` | **있음** |
| 2D 배열 행 수 | `arr.length` | **없음** |
| 2D 배열 열 수 | `arr[0].length` | **없음** |

### 요소 접근
| 대상 | 문법 |
|------|------|
| 배열 | `arr[i]` |
| String의 문자 | `s.substring(i, i+1)` |
| ArrayList | `list.get(i)` |
| 2D 배열 | `arr[r][c]` |

### 비교
| 대상 | 같은지 | 순서 비교 |
|------|--------|-----------|
| 기본형 (int, double) | `==` | `<`, `>`, `<=`, `>=` |
| String | `.equals()` | `.compareTo()` |
| 객체 | `.equals()` | 해당 없음 (Comparable 구현 시 가능) |

---

> 이 문서를 시험 전에 반복해서 읽고, 특히 **시험 주의점** 부분을 집중적으로 복습하자.
> Quick Reference에 있는 내용이므로 시험 중에도 참고할 수 있지만, 미리 익혀두면 시간을 크게 절약할 수 있다.
