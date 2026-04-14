# AP Computer Science A — Level Test 6

> **목적:** AP CSA 5점 도달 여부를 진단하는 고난이도 테스트
> **제한 시간:** Section I (30분) + Section II (30분) = 총 60분
> **배점:** MCQ 21문제 × 1점 = 21점 / FRQ Q1 7점 + Q2 6점 = 13점 / **총 34점**

---

# Section I: Multiple Choice (21 Questions | 30 Minutes)

**Unit 분포:** U1(3) · U2(6) · U3(3) · U4(9)
**난이도:** 쉬움 3 · 보통 8 · 어려움 10

**지시사항:** Assume that the classes listed in the Java Quick Reference have been imported where appropriate. Unless otherwise noted, assume that parameters in method calls are not `null` and that methods are called only when their preconditions are met.

---

### 1. [U1 · 쉬움]

다음 코드의 출력은?

```java
int a = -17;
int b = 5;
System.out.println(a % b);
```

(A) 3
(B) -3
(C) -2
(D) 2

---

### 2. [U1 · 보통]

다음 코드의 출력은?

```java
int x = 5;
double y = x + 2.0;
int z = (int)(y * 10) / 10;
System.out.println(z);
```

(A) 7.0
(B) 7
(C) 0
(D) 70

---

### 3. [U1 · 어려움]

다음 코드의 출력은?

```java
int a = 3;
int b = 4;
double c = a / b + (double) a / b;
System.out.println(c);
```

(A) 1.5
(B) 1.75
(C) 0
(D) 0.75

---

### 4. [U2 · 보통]

다음 코드의 출력은?

```java
String s = "Hello, World!";
String result = "";
for (int i = 0; i < s.length(); i++)
{
    String ch = s.substring(i, i + 1);
    if (!" ,.!".contains(ch))
    {
        result += ch;
    }
}
System.out.println(result);
```

(A) `"HelloWorld"`
(B) `"Hello World"`
(C) `"HelloWorld!"`
(D) `"Hello,World!"`

---

### 5. [U2 · 쉬움]

다음 코드의 출력은?

```java
String s = "programming";
System.out.println(s.substring(0, s.length()));
```

(A) `"programmin"`
(B) `"programming"`
(C) `"rogramming"`
(D) `StringIndexOutOfBoundsException`

---

### 6. [U2 · 어려움]

다음 코드의 출력은?

```java
int num = 0;
int n = 12345;
while (n > 0)
{
    num = num * 10 + n % 10;
    n /= 10;
}
System.out.println(num);
```

(A) 12345
(B) 15
(C) 54321
(D) 5

---

### 7. [U2 · 보통]

다음 코드의 출력은?

```java
String s = "banana";
int idx = s.indexOf("na");
System.out.println(idx + " " + s.indexOf("na", idx + 1));
```

(A) `2 4`
(B) `2 2`
(C) `3 5`
(D) `2 -1`

---

### 8. [U2 · 어려움]

다음 메서드의 `sort("banana")`에 대한 반환값에서 첫 번째 문자는?

```java
public static String sort(String s)
{
    for (int i = 0; i < s.length() - 1; i++)
    {
        for (int j = i + 1; j < s.length(); j++)
        {
            if (s.substring(j, j + 1).compareTo(s.substring(i, i + 1)) < 0)
            {
                String temp = s.substring(i, i + 1);
                s = s.substring(0, i) + s.substring(j, j + 1)
                    + s.substring(i + 1, j) + temp + s.substring(j + 1);
            }
        }
    }
    return s;
}
```

(A) `'z'`
(B) `'b'`
(C) `'n'`
(D) `'a'`

---

### 9. [U2 · 어려움]
> **참고:** `indexOf("")`의 동작은 AP 시험에 출제되지 않는 Java 세부사항이지만, String 메서드 심화 이해를 위해 포함했습니다.

다음 코드의 출력은?

```java
String s = "abcde";
System.out.println(s.indexOf(""));
```

(A) -1
(B) 0
(C) 컴파일 에러
(D) `StringIndexOutOfBoundsException`

---

### 10. [U3 · 보통]

다음 진리표를 완성할 때, `p && (!p || q)` 에서 `p = true`, `q = false`일 때의 값은?

(A) `true`
(B) 컴파일 에러
(C) 정의되지 않음
(D) `false`

---

### 11. [U3 · 어려움]

다음 표현을 간소화한 것은?

`(a || b) && (a || !b)`

(A) `a`
(B) `b`
(C) `a && b`
(D) `a || b`

---

### 12. [U3 · 어려움]

다음 코드에서 `NullPointerException`이 발생하지 않는 이유는?

```java
String s = null;
boolean result = (s == null) || (s.length() == 0);
System.out.println(result);
```

(A) `s.length()`가 null에 대해 0을 반환하므로
(B) `||`의 short-circuit: `s == null`이 true이므로 오른쪽을 평가하지 않음
(C) `null`은 길이 0인 String과 같으므로
(D) 실제로 `NullPointerException`이 발생함

---

### 13. [U4 · 쉬움]

다음 코드의 출력은?

```java
int[] arr = {1, 2, 3, 4, 5};
int[] copy = new int[arr.length];
for (int i = 0; i < arr.length; i++)
{
    copy[i] = arr[i];
}
copy[0] = 99;
System.out.println(arr[0] + " " + copy[0]);
```

(A) `99 99`
(B) `99 1`
(C) `1 99`
(D) `1 1`

---

### 14. [U4 · 보통]

다음 코드의 출력은?

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(5);
list.add(10);
list.add(15);
list.add(20);

int idx = 0;
while (idx < list.size())
{
    if (list.get(idx) > 10)
    {
        list.add(idx, list.get(idx) - 10);
        idx += 2;
    }
    else
    {
        idx++;
    }
}
System.out.println(list);
```

(A) `[5, 10, 5, 15, 10, 20]`
(B) `[5, 10, 15, 5, 20, 10]`
(C) 무한 루프
(D) `[5, 10, 5, 15, 20]`

---

### 15. [U4 · 어려움]

다음 코드의 출력은?

```java
int[][] grid = {{1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}};
int[][] transposed = new int[grid[0].length][grid.length];
for (int r = 0; r < grid.length; r++)
{
    for (int c = 0; c < grid[0].length; c++)
    {
        transposed[c][r] = grid[r][c];
    }
}
System.out.println(transposed[1][2]);
```

(A) 4
(B) 6
(C) 8
(D) 2

---

### 16. [U4 · 보통]

다음 코드의 출력은?

```java
int[] arr = {3, 1, 4, 1, 5};
for (int val : arr)
{
    val = val * 2;
}
System.out.println(arr[2]);
```

(A) 8
(B) 컴파일 에러
(C) 0
(D) 4

---

### 17. [U4 · 어려움]

다음 재귀 메서드에서 `factorial(0)` 호출 시 반환값은?

```java
public static int factorial(int n)
{
    if (n <= 0)
        return 1;
    return n * factorial(n - 1);
}
```

(A) 0
(B) -1
(C) `StackOverflowError`
(D) 1

---

### 18. [U4 · 어려움]

다음 코드에서 정렬된 ArrayList에 올바른 위치에 삽입하는 결과는?

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(2);
list.add(5);
list.add(8);
list.add(12);

int val = 7;
int pos = 0;
while (pos < list.size() && list.get(pos) < val)
{
    pos++;
}
list.add(pos, val);
System.out.println(list);
```

(A) `[2, 5, 8, 12, 7]`
(B) `[2, 5, 8, 7, 12]`
(C) `[7, 2, 5, 8, 12]`
(D) `[2, 5, 7, 8, 12]`

---

### 19. [U4 · 보통]

다음 코드의 출력은?

```java
int[] arr = {2, 4, 6, 8};
int target = 5;
int lo = 0, hi = arr.length - 1;
while (lo <= hi)
{
    int mid = (lo + hi) / 2;
    if (arr[mid] < target)
        lo = mid + 1;
    else if (arr[mid] > target)
        hi = mid - 1;
    else
        break;
}
System.out.println(lo);
```

(A) 1
(B) 2
(C) 3
(D) -1

---

### 20. [U4 · 어려움]

다음 코드의 출력은?

```java
int[][] grid = {{1, 0, 1},
                {0, 1, 0},
                {1, 0, 1}};
int count = 0;
for (int r = 0; r < grid.length; r++)
{
    for (int c = 0; c < grid[0].length; c++)
    {
        if (grid[r][c] == 1 && (r + c) % 2 == 0)
        {
            count++;
        }
    }
}
System.out.println(count);
```

(A) 3
(B) 4
(C) 5
(D) 9

---

### 21. [U4 · 보통]

다음 코드의 출력은?

```java
ArrayList<String> list = new ArrayList<String>();
list.add("a");
list.add("b");
list.add("c");
list.set(1, "z");
list.add(1, "y");
System.out.println(list);
```

(A) `[a, y, z, c]`
(B) `[a, z, y, c]`
(C) `[a, y, b, c]`
(D) `[y, a, z, c]`

---

# Section II: Free Response (2 Questions | 30 Minutes)

**지시사항:** Write your solutions in Java. You may assume all necessary imports.

---

## Question 1: NumberConverter (7 Points)

다음 `NumberConverter` 클래스는 숫자를 변환하는 메서드를 제공합니다.

```java
public class NumberConverter
{
    /** Returns a String representing the binary form of a positive integer n.
     *
     *  Examples:
     *    toBinary(13) returns "1101"
     *    toBinary(1) returns "1"
     *    toBinary(8) returns "1000"
     *    toBinary(255) returns "11111111"
     *
     *  Precondition: n > 0
     */
    public static String toBinary(int n)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns the sum of the digits in the string numStr.
     *  numStr may start with a '-' for negative numbers; the '-' is ignored.
     *  Leading zeros are allowed.
     *
     *  Examples:
     *    sumOfDigits("1234") returns 10
     *    sumOfDigits("-1234") returns 10
     *    sumOfDigits("007") returns 7
     *    sumOfDigits("9") returns 9
     *
     *  Precondition: numStr is a valid integer string (optional '-' followed
     *  by one or more digits).
     */
    public static int sumOfDigits(String numStr)
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `toBinary` method.

### Part (b)

Complete the `sumOfDigits` method. You must use at least one `String` method.

---

## Question 2: Gradebook (6 Points)

다음 `Gradebook` 클래스는 학생 목록을 관리합니다. `Student` 클래스가 별도로 제공됩니다.

```java
public class Student
{
    /** Returns the student's name. */
    public String getName() { /* implementation not shown */ }

    /** Returns the student's average score (0.0 ~ 100.0). */
    public double getAverage() { /* implementation not shown */ }

    /** Adds bonus points to the student's total score.
     *  This may change the student's average.
     */
    public void addBonus(int points) { /* implementation not shown */ }
}

public class Gradebook
{
    private ArrayList<Student> students;

    /** Constructs a Gradebook with the given list of students.
     *  Precondition: students is not null and has at least one element.
     */
    public Gradebook(ArrayList<Student> students)
    {
        this.students = students;
    }

    /** Returns an ArrayList of names of students whose average is
     *  greater than or equal to cutoff.
     *  The names appear in the same order as in students.
     *
     *  Examples:
     *    If students has averages [85.0, 72.5, 91.3, 60.0]
     *    and cutoff is 75.0, returns names at indices 0 and 2.
     */
    public ArrayList<String> getTopStudents(double cutoff)
    {
        /* to be implemented in Part (a) */
    }

    /** Adds the given bonus points to every student, then returns
     *  the number of students whose average changed from below 60
     *  to 60 or above as a result.
     *
     *  A student "changed" only if:
     *    - their average was < 60 BEFORE addBonus, AND
     *    - their average is >= 60 AFTER addBonus.
     *
     *  Precondition: points > 0
     */
    public int curveAll(int points)
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `getTopStudents` method.

### Part (b)

Complete the `curveAll` method.

---
---

# 정답 및 채점

## Section I 정답표

| # | 정답 | Unit | 난이도 | 해설 |
|---|------|------|--------|------|
| 1 | C | U1 | 쉬움 | Java에서 `-17 % 5` = `-2`. 나머지의 부호는 피제수의 부호를 따름. |
| 2 | B | U1 | 보통 | `y = 5 + 2.0 = 7.0`. `(int)(7.0 * 10)` = 70. `70 / 10` = 7 (int 나눗셈). |
| 3 | D | U1 | 어려움 | `3 / 4` = 0 (int). `(double) 3 / 4` = 0.75. `0 + 0.75` = 0.75. |
| 4 | A | U2 | 보통 | 공백, 쉼표, 점, 느낌표를 제거. `"HelloWorld"`. |
| 5 | B | U2 | 쉬움 | `substring(0, length)` = 전체 문자열. `"programming"`. |
| 6 | C | U2 | 어려움 | 숫자 뒤집기. 12345 → 54321. |
| 7 | A | U2 | 보통 | `"banana".indexOf("na")` = 2. `indexOf("na", 3)` = 4. 출력: `"2 4"`. |
| 8 | D | U2 | 어려움 | 버블 정렬로 문자열 정렬. `"banana"` → `"aaabnn"`. 첫 문자는 `'a'`. |
| 9 | B | U2 | 어려움 | `indexOf("")`는 항상 0을 반환. 빈 문자열은 모든 위치에 존재. |
| 10 | D | U3 | 보통 | `p = true, q = false`: `!p = false`, `!p || q = false`. `p && false = false`. |
| 11 | A | U3 | 어려움 | 분배법칙: `(a || b) && (a || !b)` = `a || (b && !b)` = `a || false` = `a`. |
| 12 | B | U3 | 어려움 | `||` short-circuit: 왼쪽이 `true`면 오른쪽 미평가. `s.length()` 호출 안 됨. |
| 13 | C | U4 | 쉬움 | 값 복사(deep copy). `copy[0]` 변경은 `arr[0]`에 영향 없음. `1 99`. |
| 14 | A | U4 | 보통 | idx=0: 5≤10, idx=1. idx=1: 10≤10, idx=2. idx=2: 15>10, add(2,5)→[5,10,5,15,20], idx=4. idx=4: 20>10, add(4,10)→[5,10,5,15,10,20], idx=6. 종료. |
| 15 | C | U4 | 어려움 | `transposed[c][r] = grid[r][c]`. `transposed[1][2]` = `grid[2][1]` = 8. |
| 16 | D | U4 | 보통 | enhanced for loop의 `val`은 복사본. 원본 배열 변경 안 됨. `arr[2]` = 4. |
| 17 | D | U4 | 어려움 | `factorial(0)`: `0 <= 0` → return 1. |
| 18 | D | U4 | 어려움 | pos: 0→1→2 (list.get(2)=8 ≥ 7 → 종료). `add(2, 7)` → `[2, 5, 7, 8, 12]`. |
| 19 | B | U4 | 보통 | lo=0,hi=3 → mid=1(4<5) → lo=2. lo=2,hi=3 → mid=2(6>5) → hi=1. lo=2>hi=1 → 종료. `lo` = 2. |
| 20 | C | U4 | 어려움 | grid[r][c]==1인 위치: (0,0),(0,2),(1,1),(2,0),(2,2). 모두 r+c가 짝수. count = 5. |
| 21 | A | U4 | 보통 | 초기: [a,b,c]. `set(1,"z")` → [a,z,c]. `add(1,"y")` → [a,y,z,c]. |

### Section I 최종 정답

| # | 정답 |
|---|------|
| 1 | C |
| 2 | B |
| 3 | D |
| 4 | A |
| 5 | B |
| 6 | C |
| 7 | A |
| 8 | D |
| 9 | B |
| 10 | D |
| 11 | A |
| 12 | B |
| 13 | C |
| 14 | A |
| 15 | C |
| 16 | D |
| 17 | D |
| 18 | D |
| 19 | B |
| 20 | C |
| 21 | A |

---

## Section II 채점기준

### Q1: NumberConverter (7점)

#### Part (a) — `toBinary` (4점)

**모범 답안:**
```java
public static String toBinary(int n)
{
    String result = "";
    while (n > 0)
    {
        result = (n % 2) + result;
        n /= 2;
    }
    return result;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 반복적으로 n을 2로 나누는 루프 |
| +1 | `n % 2`로 각 자릿수 추출 |
| +1 | 결과 문자열을 올바른 순서로 구성 (앞에 붙이기) |
| +1 | 올바른 값 반환 (algorithm point) |

**감점 사항:**
- 결과가 역순 (뒤에 붙이기): -1
- `n == 0`일 때 빈 문자열 반환 (precondition에 의해 n > 0이므로 감점 아님)

---

#### Part (b) — `sumOfDigits` (3점)

**모범 답안:**
```java
public static int sumOfDigits(String numStr)
{
    int sum = 0;
    for (int i = 0; i < numStr.length(); i++)
    {
        String ch = numStr.substring(i, i + 1);
        if (!ch.equals("-"))
        {
            sum += Integer.parseInt(ch);
        }
    }
    return sum;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 문자열을 순회하는 루프 |
| +1 | `-` 부호를 건너뛰고 숫자만 처리 |
| +1 | 각 자릿수를 정수로 변환하여 합산 + 반환 |

**감점 사항:**
- String 메서드 미사용: -1
- `-` 처리 누락: -1

---

### Q2: Gradebook (6점)

#### Part (a) — `getTopStudents` (4점)

**모범 답안:**
```java
public ArrayList<String> getTopStudents(double cutoff)
{
    ArrayList<String> result = new ArrayList<String>();
    for (Student s : students)
    {
        if (s.getAverage() >= cutoff)
        {
            result.add(s.getName());
        }
    }
    return result;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 새 ArrayList 생성 |
| +1 | students를 순회하는 루프 |
| +1 | `getAverage() >= cutoff` 조건으로 필터 |
| +1 | `getName()`으로 이름 추가 + 올바르게 반환 |

---

#### Part (b) — `curveAll` (2점)

**모범 답안:**
```java
public int curveAll(int points)
{
    int count = 0;
    for (Student s : students)
    {
        double before = s.getAverage();
        s.addBonus(points);
        double after = s.getAverage();
        if (before < 60 && after >= 60)
        {
            count++;
        }
    }
    return count;
}
```

| 점수 | 기준 |
|------|------|
| +1 | addBonus 전후로 평균을 비교 |
| +1 | before < 60 AND after >= 60인 경우만 카운트 + 반환 |

**감점 사항:**
- `addBonus` 호출 전에 before를 저장하지 않음: -1
- 전체 학생에게 addBonus 미호출: -1

---

## 점수 해석

| 총점 (34점 만점) | 예상 AP 점수 | 설명 |
|-----------------|-------------|------|
| 28–34 | **5** | 목표 달성. 실전에서도 5점 가능성 높음. |
| 21–27 | **4** | 기본기 탄탄하나 고난이도 문제에서 실수. 코드 tracing 연습 필요. |
| 14–20 | **3** | 핵심 개념은 이해하나 적용력 부족. Unit별 약점 집중 보완. |
| 0–13 | — | 추가 학습 필요. 기본 개념부터 재점검 권장. |
