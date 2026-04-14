# AP Computer Science A — Level Test 9

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
int x = 5;
x++;
++x;
System.out.println(x);
```

(A) 5
(B) 6
(C) 7
(D) 8

---

### 2. [U1 · 보통]

다음 코드의 출력은?

```java
double x = 1.0 / 3 * 100;
int y = (int) x;
System.out.println(y);
```

(A) 33
(B) 34
(C) 0
(D) 100

---

### 3. [U1 · 어려움]

다음 코드에서 컴파일 에러가 발생하는 줄은?

```java
final int X = 10;       // Line 1
int y = X + 5;          // Line 2
X = 20;                 // Line 3
System.out.println(y);  // Line 4
```

(A) Line 1
(B) Line 2
(C) Line 3
(D) 에러 없음

---

### 4. [U2 · 쉬움]

다음 코드의 출력은?

```java
String s = "  Hello  ";
System.out.println(s.trim().length());
```

> **참고:** `trim()`은 AP 시험에 직접 나오지 않지만 문자열 메서드 이해를 테스트.

(A) 9
(B) 5
(C) 7
(D) 컴파일 에러

---

### 5. [U2 · 보통]

다음 코드의 출력은?

```java
String s = "a b c d e";
String result = "";
for (int i = 0; i < s.length(); i++)
{
    String ch = s.substring(i, i + 1);
    if (!ch.equals(" "))
    {
        result += ch;
    }
}
System.out.println(result);
```

(A) `"a b c d e"`
(B) `" "`
(C) `"a"`
(D) `"abcde"`

---

### 6. [U2 · 어려움]

다음 코드는 유클리드 호제법의 재귀 버전이다. `gcd(48, 18)`의 반환값은?

```java
public static int gcd(int a, int b)
{
    if (b == 0)
        return a;
    return gcd(b, a % b);
}
```

(A) 2
(B) 6
(C) 12
(D) 48

---

### 7. [U2 · 보통]

다음 코드의 출력은?

```java
String s = "Hello";
int boundary = s.length() - 1;
String first = s.substring(0, boundary);
String last = s.substring(boundary);
System.out.println(first + " " + last);
```

(A) `"Hel lo"`
(B) `"Hello "`
(C) `"Hell o"`
(D) `"He llo"`

---

### 8. [U2 · 어려움]

다음 코드의 출력은?

```java
String original = "aabbcc";
String modified = original;
modified = modified.substring(0, 2) + "XX" + modified.substring(4);
System.out.println(original + " " + modified);
```

(A) `"aaXXcc aaXXcc"`
(B) `"aabbcc aaXXcc"`
(C) `"aabbcc aabbcc"`
(D) 컴파일 에러

---

### 9. [U2 · 어려움]

다음 코드의 출력은?

```java
String s = "ABCDEF";
String result = "";
for (int i = 0; i < s.length(); i++)
{
    if (s.substring(i, i + 1).compareTo("D") < 0)
    {
        result += s.substring(i, i + 1);
    }
}
System.out.println(result);
```

(A) `"DEF"`
(B) `"ABCD"`
(C) `"ABC"`
(D) `"AB"`

---

### 10. [U3 · 보통]

다음 조건이 `true`가 되려면 `p`와 `q`는?

`(!p || q) && (p || !q)` 가 `true`가 되는 조합은 몇 가지인가?

(A) 1가지
(B) 2가지
(C) 3가지
(D) 4가지

---

### 11. [U3 · 어려움]

다음 코드의 출력은?

```java
String a = "cat";
String b = "dog";
int result = a.compareTo(b);
if (result < 0)
    System.out.println(-1);
else if (result > 0)
    System.out.println(1);
else
    System.out.println(0);
```

(A) -1
(B) 1
(C) 0
(D) 컴파일 에러

---

### 12. [U3 · 어려움]

다음 코드에서 `obj`가 `null`일 때 어떤 일이 발생하는가?

```java
Object obj = null;
if (obj != null && obj.toString().length() > 0)
{
    System.out.println("valid");
}
else
{
    System.out.println("invalid");
}
```

(A) `"valid"` 출력
(B) 컴파일 에러
(C) `NullPointerException`
(D) `"invalid"` 출력

---

### 13. [U4 · 쉬움]

다음 코드의 출력은?

```java
int[] arr = {7, 3, 9, 1, 5};
int[] evens = new int[arr.length];
int count = 0;
for (int val : arr)
{
    if (val % 2 == 0)
    {
        evens[count] = val;
        count++;
    }
}
System.out.println(count);
```

(A) 2
(B) 1
(C) 0
(D) 5

---

### 14. [U4 · 보통]

다음 코드의 출력은?

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(10);
list.add(20);
list.add(30);
list.add(40);

ArrayList<Integer> result = new ArrayList<Integer>();
for (int i = 0; i < list.size(); i++)
{
    if (list.get(i) % 20 == 0)
        result.add(list.get(i));
}
list.removeAll(result);
System.out.println(list);
```

> **참고:** `removeAll`은 AP Quick Reference에 없지만 코드 추적 연습 포함.

(A) `[10, 30]`
(B) `[20, 40]`
(C) `[10, 20, 30, 40]`
(D) `[]`

---

### 15. [U4 · 어려움]

다음 코드의 출력은?

```java
int[][] grid = {{1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}};
int[][] rotated = new int[3][3];
for (int r = 0; r < 3; r++)
{
    for (int c = 0; c < 3; c++)
    {
        rotated[c][2 - r] = grid[r][c];
    }
}
System.out.println(rotated[0][0] + " " + rotated[0][2] + " " + rotated[2][0]);
```

(A) `7 1 9`
(B) `1 7 3`
(C) `3 9 1`
(D) `7 1 3`

---

### 16. [U4 · 보통]

다음 재귀 메서드의 `isPalindrome("abcba")` 반환값은?

```java
public static boolean isPalindrome(String s)
{
    if (s.length() <= 1)
        return true;
    if (!s.substring(0, 1).equals(s.substring(s.length() - 1)))
        return false;
    return isPalindrome(s.substring(1, s.length() - 1));
}
```

(A) 컴파일 에러
(B) `false`
(C) `StackOverflowError`
(D) `true`

---

### 17. [U4 · 어려움]

다음 insertion sort에서 `{5, 2, 4, 6, 1, 3}` 정렬 시 **i = 3** (네 번째 요소 6 처리) 후 배열 상태는?

```java
int[] arr = {5, 2, 4, 6, 1, 3};
for (int i = 1; i < arr.length; i++)
{
    int key = arr[i];
    int j = i - 1;
    while (j >= 0 && arr[j] > key)
    {
        arr[j + 1] = arr[j];
        j--;
    }
    arr[j + 1] = key;
}
```

(A) `{2, 4, 5, 6, 1, 3}`
(B) `{1, 2, 4, 5, 6, 3}`
(C) `{2, 4, 5, 1, 6, 3}`
(D) `{2, 5, 4, 6, 1, 3}`

---

### 18. [U4 · 어려움]

다음 코드의 출력은?

```java
int[][] grid = {{5, 3, 1},
                {2, 8, 4},
                {7, 6, 9}};
// Find saddle point: minimum in its row AND maximum in its column
for (int r = 0; r < grid.length; r++)
{
    for (int c = 0; c < grid[0].length; c++)
    {
        boolean rowMin = true;
        boolean colMax = true;
        for (int k = 0; k < grid[0].length; k++)
        {
            if (grid[r][k] < grid[r][c])
                rowMin = false;
        }
        for (int k = 0; k < grid.length; k++)
        {
            if (grid[k][c] > grid[r][c])
                colMax = false;
        }
        if (rowMin && colMax)
            System.out.println(grid[r][c]);
    }
}
```

(A) 5
(B) 7
(C) 9
(D) 출력 없음

---

### 19. [U4 · 보통]

다음 코드의 출력은?

```java
int[] arr = {1, 2, 3, 4, 5};
int[] prefix = new int[arr.length];
prefix[0] = arr[0];
for (int i = 1; i < arr.length; i++)
{
    prefix[i] = prefix[i - 1] + arr[i];
}
System.out.println(prefix[3]);
```

(A) 4
(B) 10
(C) 6
(D) 15

---

### 20. [U4 · 어려움]

다음 코드의 출력은?

```java
int[] arr = {4, 2, 7, 1, 3};
int count = 0;
for (int i = 0; i < arr.length; i++)
{
    for (int j = i + 1; j < arr.length; j++)
    {
        if (arr[i] > arr[j])
            count++;
    }
}
System.out.println(count);
```

(A) 3
(B) 4
(C) 5
(D) 6

---

### 21. [U4 · 보통]

다음 코드의 출력은?

```java
ArrayList<String> a = new ArrayList<String>();
a.add("x");
a.add("y");
a.add("z");

ArrayList<String> b = new ArrayList<String>();
b.add("y");
b.add("z");
b.add("w");

ArrayList<String> common = new ArrayList<String>();
for (String s : a)
{
    for (String t : b)
    {
        if (s.equals(t) && !common.contains(s))
        {
            common.add(s);
        }
    }
}
System.out.println(common);
```

(A) `[x, w]`
(B) `[x, y, z, w]`
(C) `[y, z]`
(D) `[y]`

---

# Section II: Free Response (2 Questions | 30 Minutes)

**지시사항:** Write your solutions in Java. You may assume all necessary imports.

---

## Question 1: DateChecker (7 Points)

다음 `DateChecker` 클래스는 날짜의 유효성을 검사하는 메서드를 제공합니다.

```java
public class DateChecker
{
    /** Returns true if the given date is valid.
     *  Month is 1-12. Day depends on the month.
     *  February has 28 days, or 29 in a leap year.
     *  Leap year: divisible by 4, except centuries (divisible by 100)
     *  unless also divisible by 400.
     *
     *  Examples:
     *    isValidDate(2, 29, 2024) returns true  (2024 is a leap year)
     *    isValidDate(2, 29, 1900) returns false  (1900 is NOT a leap year)
     *    isValidDate(2, 29, 2000) returns true   (2000 IS a leap year)
     *    isValidDate(4, 31, 2023) returns false   (April has 30 days)
     *    isValidDate(13, 1, 2023) returns false   (invalid month)
     *    isValidDate(1, 0, 2023) returns false    (invalid day)
     *
     *  Precondition: year > 0
     */
    public static boolean isValidDate(int month, int day, int year)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns the absolute number of days between two dates
     *  in the same non-leap year.
     *  Uses cumulative day-of-year calculation.
     *
     *  Examples:
     *    daysBetween(1, 1, 3, 1) returns 59
     *      (Jan has 31, Feb has 28 → day 1 to day 60 → 59 days)
     *    daysBetween(6, 15, 6, 15) returns 0
     *    daysBetween(12, 31, 1, 1) returns 364
     *
     *  Precondition: both dates are valid in a non-leap year.
     */
    public static int daysBetween(int m1, int d1, int m2, int d2)
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `isValidDate` method.

### Part (b)

Complete the `daysBetween` method. You may write a helper method to compute the day-of-year.

---

## Question 2: HeatMap (6 Points)

다음 `HeatMap` 클래스는 2D double 배열을 분석합니다.

```java
public class HeatMap
{
    private double[][] grid;

    /** Constructs a HeatMap with the given 2D array.
     *  Precondition: grid is rectangular, at least 1×1.
     */
    public HeatMap(double[][] grid)
    {
        this.grid = grid;
    }

    /** Returns an ArrayList of coordinate strings "r,c" where
     *  grid[r][c] > threshold AND all existing direct neighbors
     *  (up, down, left, right) are also > threshold.
     *  Coordinates are in row-major order.
     *
     *  Example grid:
     *    {{9.0, 8.5, 2.0},
     *     {8.0, 9.5, 7.5},
     *     {3.0, 8.0, 7.0}}
     *
     *    threshold = 7.0:
     *    - (0,0)=9.0>7: neighbors (0,1)=8.5>7 ✓, (1,0)=8.0>7 ✓ → hotspot
     *    - (0,1)=8.5>7: neighbor (0,2)=2.0 ≤ 7 → NOT hotspot
     *    - (1,1)=9.5>7: neighbors 8.5,8.0,7.5,8.0 all >7 → hotspot
     *    Result: ["0,0", "1,1"]
     */
    public ArrayList<String> findHotspot(double threshold)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns the average of all values in the rectangular region
     *  from (r1, c1) to (r2, c2) inclusive.
     *
     *  Example: for the grid above,
     *    averageRegion(0, 0, 1, 1) returns (9.0+8.5+8.0+9.5)/4 = 8.75
     *
     *  Precondition: 0 <= r1 <= r2 < grid.length,
     *                0 <= c1 <= c2 < grid[0].length
     */
    public double averageRegion(int r1, int c1, int r2, int c2)
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `findHotspot` method.

### Part (b)

Complete the `averageRegion` method.

---
---

# 정답 및 채점

## Section I 정답표

| # | 정답 | Unit | 난이도 | 해설 |
|---|------|------|--------|------|
| 1 | C | U1 | 쉬움 | x=5 → x++=6 → ++x=7. |
| 2 | A | U1 | 보통 | `1.0/3` = 0.3333... `*100` = 33.333... `(int)` = 33. |
| 3 | C | U1 | 어려움 | `final` 변수는 재할당 불가. Line 3에서 컴파일 에러. |
| 4 | B | U2 | 쉬움 | `trim()`은 앞뒤 공백 제거. `"Hello"` → 길이 5. |
| 5 | D | U2 | 보통 | 공백 제거. `"abcde"`. |
| 6 | B | U2 | 어려움 | `gcd(48,18)` → `gcd(18,12)` → `gcd(12,6)` → `gcd(6,0)` → 6. |
| 7 | C | U2 | 보통 | boundary=4. `substring(0,4)` = `"Hell"`. `substring(4)` = `"o"`. `"Hell o"`. |
| 8 | B | U2 | 어려움 | String은 불변. `modified`에 새 문자열 할당. `original`은 그대로. `"aabbcc aaXXcc"`. |
| 9 | C | U2 | 어려움 | `compareTo("D") < 0`: A(65)<D(68)✓, B(66)<D✓, C(67)<D✓, D(68)<D✗. → `"ABC"`. |
| 10 | B | U3 | 보통 | `(!p\|\|q)&&(p\|\|!q)`: (T,T)→T, (T,F)→F, (F,T)→F, (F,F)→T. 2가지. |
| 11 | A | U3 | 어려움 | `"cat".compareTo("dog")`: 'c'(99) < 'd'(100) → 음수 → -1 출력. |
| 12 | D | U3 | 어려움 | Short-circuit: `obj != null` false → `&&` 오른쪽 미평가 → `"invalid"`. |
| 13 | C | U4 | 쉬움 | 짝수 없음 (7,3,9,1,5 모두 홀수). count = 0. |
| 14 | A | U4 | 보통 | 20의 배수: 20, 40. `removeAll` → [10, 30]. |
| 15 | A | U4 | 어려움 | 90도 회전: `rotated[c][2-r] = grid[r][c]`. rotated[0][0]=grid[2][0]=7. rotated[0][2]=grid[0][0]=1. rotated[2][0]=grid[2][2]=9. `"7 1 9"`. |
| 16 | D | U4 | 보통 | "abcba": a==a✓ → "bcb": b==b✓ → "c": 길이1→true. 회문. `true`. |
| 17 | A | U4 | 어려움 | i=1: key=2, 5>2→shift, {5,5,4,6,1,3}, arr[0]=2→{2,5,4,6,1,3}. i=2: key=4, 5>4→shift, {2,5,5,6,1,3}, arr[1]=4→{2,4,5,6,1,3}. i=3: key=6, 5<6→shift 없음. {2,4,5,6,1,3}. |
| 18 | D | U4 | 어려움 | saddle point(행 최솟값이면서 열 최댓값) 검사. Row 0 min=1→열2 max=9≠1. Row 1 min=2→열0 max=7≠2. Row 2 min=6→열1 max=8≠6. saddle point 없음 → 출력 없음. |
| 19 | B | U4 | 보통 | prefix: [1, 3, 6, 10, 15]. prefix[3] = 10. |
| 20 | D | U4 | 어려움 | 역전쌍: i=0(4): 4>2,4>1,4>3 → 3. i=1(2): 2>1 → 1. i=2(7): 7>1,7>3 → 2. i=3(1): 0. 총 = 3+1+2+0 = 6. |
| 21 | C | U4 | 보통 | a∩b: "y", "z". `[y, z]`. |

### Section I 최종 정답

| # | 정답 |
|---|------|
| 1 | C |
| 2 | A |
| 3 | C |
| 4 | B |
| 5 | D |
| 6 | B |
| 7 | C |
| 8 | B |
| 9 | C |
| 10 | B |
| 11 | A |
| 12 | D |
| 13 | C |
| 14 | A |
| 15 | A |
| 16 | D |
| 17 | A |
| 18 | D |
| 19 | B |
| 20 | D |
| 21 | C |

---

## Section II 채점기준

### Q1: DateChecker (7점)

#### Part (a) — `isValidDate` (4점)

**모범 답안:**
```java
public static boolean isValidDate(int month, int day, int year)
{
    if (month < 1 || month > 12 || day < 1)
        return false;

    int[] daysInMonth = {0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};

    // Leap year check
    if (month == 2)
    {
        boolean leap = (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);
        if (leap)
            return day <= 29;
        else
            return day <= 28;
    }

    return day <= daysInMonth[month];
}
```

| 점수 | 기준 |
|------|------|
| +1 | month 범위(1-12)와 day >= 1 검사 |
| +1 | 각 월의 일수를 올바르게 구분 (30일/31일) |
| +1 | 윤년 판별 (4의 배수 + 100의 배수 예외 + 400의 배수 예외의 예외) |
| +1 | 2월의 윤년/비윤년 일수 올바르게 처리 (algorithm point) |

**감점 사항:**
- 윤년 조건 불완전 (400 규칙 누락): -1
- 4, 6, 9, 11월의 30일 구분 누락: -1

---

#### Part (b) — `daysBetween` (3점)

**모범 답안:**
```java
public static int daysBetween(int m1, int d1, int m2, int d2)
{
    int[] daysInMonth = {0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};

    int day1 = d1;
    for (int i = 1; i < m1; i++)
        day1 += daysInMonth[i];

    int day2 = d2;
    for (int i = 1; i < m2; i++)
        day2 += daysInMonth[i];

    return Math.abs(day2 - day1);
}
```

| 점수 | 기준 |
|------|------|
| +1 | 각 날짜의 day-of-year를 올바르게 계산 |
| +1 | 두 값의 차이 계산 |
| +1 | 절대값으로 반환 |

**감점 사항:**
- day-of-year 계산 off-by-one: -1
- 절대값 미적용: -1

---

### Q2: HeatMap (6점)

#### Part (a) — `findHotspot` (4점)

**모범 답안:**
```java
public ArrayList<String> findHotspot(double threshold)
{
    ArrayList<String> result = new ArrayList<String>();
    for (int r = 0; r < grid.length; r++)
    {
        for (int c = 0; c < grid[0].length; c++)
        {
            if (grid[r][c] > threshold)
            {
                boolean allNeighbors = true;
                if (r > 0 && grid[r-1][c] <= threshold) allNeighbors = false;
                if (r < grid.length-1 && grid[r+1][c] <= threshold) allNeighbors = false;
                if (c > 0 && grid[r][c-1] <= threshold) allNeighbors = false;
                if (c < grid[0].length-1 && grid[r][c+1] <= threshold) allNeighbors = false;

                if (allNeighbors)
                    result.add(r + "," + c);
            }
        }
    }
    return result;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 2D 배열 전체 순회 |
| +1 | 셀 자체가 threshold 초과인지 검사 |
| +1 | 4방향 이웃 검사 + 경계 처리 (존재하는 이웃만) |
| +1 | 조건 충족 시 좌표를 "r,c" 형식으로 추가 + 반환 (algorithm point) |

**감점 사항:**
- 경계 체크 누락: -1
- `>` 대신 `>=` 사용: -1

---

#### Part (b) — `averageRegion` (2점)

**모범 답안:**
```java
public double averageRegion(int r1, int c1, int r2, int c2)
{
    double sum = 0;
    int count = 0;
    for (int r = r1; r <= r2; r++)
    {
        for (int c = c1; c <= c2; c++)
        {
            sum += grid[r][c];
            count++;
        }
    }
    return sum / count;
}
```

| 점수 | 기준 |
|------|------|
| +1 | (r1,c1)부터 (r2,c2)까지 올바르게 순회 + 합산 |
| +1 | 요소 수로 나누어 평균 반환 (double 나눗셈) |

**감점 사항:**
- int 나눗셈: -1
- inclusive 범위 오류: -1

---

## 점수 해석

| 총점 (34점 만점) | 예상 AP 점수 | 설명 |
|-----------------|-------------|------|
| 28–34 | **5** | 목표 달성. 실전에서도 5점 가능성 높음. |
| 21–27 | **4** | 기본기 탄탄하나 고난이도 문제에서 실수. 코드 tracing 연습 필요. |
| 14–20 | **3** | 핵심 개념은 이해하나 적용력 부족. Unit별 약점 집중 보완. |
| 0–13 | — | 추가 학습 필요. 기본 개념부터 재점검 권장. |
