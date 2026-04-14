# AP Computer Science A — Level Test 1

> **목적:** AP CSA 5점(상위 25%) 도달 여부를 진단하는 고난이도 테스트
> **제한 시간:** Section I (30분) + Section II (30분) = 총 60분
> **배점:** MCQ 21문제 × 1점 = 21점 / FRQ Q1 7점 + Q2 6점 = 13점 / **총 34점**

---

# Section I: Multiple Choice (21 Questions | 30 Minutes)

**Unit 분포:** U1(3) · U2(6) · U3(3) · U4(9)
**난이도:** 쉬움 3 · 보통 8 · 어려움 10

**지시사항:** Assume that the classes listed in the Java Quick Reference have been imported where appropriate. Unless otherwise noted, assume that parameters in method calls are not `null` and that methods are called only when their preconditions are met.

---

### 1. [U1 · 쉬움]

Consider the following code segment.

```java
int x = 17;
int y = 5;
double result = (double)(x / y) + x % y;
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) 5.4
(B) 5.2
(C) 5.0
(D) 3.4

---

### 2. [U1 · 보통]

Consider the following code segment.

```java
int a = 29;
int b = 7;
int c = a % b % 3;
System.out.println(c);
```

What is printed as a result of executing this code segment?

(A) 0
(B) 1
(C) 2
(D) 3

---

### 3. [U1 · 어려움]

Consider the following code segment.

```java
int p = 100;
int q = 33;
double r = p / q;
double s = p % q;
double t = r + s;
System.out.println(t);
```

What is printed as a result of executing this code segment?

(A) 4.030303
(B) 3.03
(C) 4.0
(D) 4.03

---

### 4. [U2 · 쉬움]

Consider the following code segment.

```java
String word = "COMPUTER";
String sub = word.substring(3, 6);
System.out.println(sub);
```

What is printed as a result of executing this code segment?

(A) `"PUT"`
(B) `"MPU"`
(C) `"PUTE"`
(D) `"MPUT"`

---

### 5. [U2 · 보통]

Consider the following code segment.

```java
String msg = "examination";
int k = msg.indexOf("nation");
String part = msg.substring(0, k) + msg.substring(k + 3);
System.out.println(part);
```

What is printed as a result of executing this code segment?

(A) `"examtion"`
(B) `"examiation"`
(C) `"examion"`
(D) `"examiion"`

---

### 6. [U2 · 어려움]

Consider the following code segment.

```java
String s = "ABCDE";
String result = "";
for (int i = s.length() - 1; i >= 0; i--)
{
    result += s.substring(i, i + 1);
    if (s.indexOf(result) >= 0)
    {
        result = result.toUpperCase();
    }
    else
    {
        result = result.toLowerCase();
    }
}
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `"EDCBA"`
(B) `"EDcba"`
(C) `"Edcba"`
(D) `"edcba"`

---

### 7. [U2 · 어려움]
> **참고:** String 리터럴 풀(intern pool) 동작은 AP 시험에서 직접 출제되지 않지만, `==` vs `equals` 이해 심화를 위해 포함했습니다.

Consider the following code segment.

```java
String s1 = "java";
String s2 = s1.substring(0, 2) + s1.substring(2);
String s3 = "ja" + "va";
System.out.println(s1 == s2);
System.out.println(s1 == s3);
System.out.println(s1.equals(s2));
```

What is printed as a result of executing this code segment?

(A)
```
false
false
true
```

(B)
```
false
true
true
```

(C)
```
true
true
true
```

(D)
```
false
false
false
```

---

### 8. [U2 · 보통]

Consider the following code segment.

```java
String text = "Mississippi";
int count = 0;
int pos = text.indexOf("ss");
while (pos != -1)
{
    count++;
    pos = text.indexOf("ss", pos + 1);
}
System.out.println(count);
```

What is printed as a result of executing this code segment?

(A) 1
(B) 3
(C) 2
(D) 4

---

### 9. [U2 · 어려움]
> **참고:** `static` 키워드와 정적 변수는 AP CSA 시험 범위 밖이지만, 객체 vs 클래스 개념 이해를 위해 포함했습니다.

Consider the following class.

```java
public class Counter
{
    private static int totalCount = 0;
    private int myCount;

    public Counter()
    {
        totalCount++;
        myCount = totalCount;
    }

    public static int getTotalCount()
    {
        return totalCount;
    }

    public int getMyCount()
    {
        return myCount;
    }
}
```

The following code segment appears in a method in another class.

```java
Counter c1 = new Counter();
Counter c2 = new Counter();
Counter c3 = new Counter();
System.out.println(c1.getMyCount() + " " + Counter.getTotalCount());
```

What is printed as a result of executing this code segment?

(A) `1 1`
(B) `3 3`
(C) `1 3`
(D) `0 3`

---

### 10. [U3 · 보통]

Consider the following code segment.

```java
boolean a = true;
boolean b = false;
boolean c = true;

if (a || b && c)
{
    System.out.print("X");
}
if ((a || b) && c)
{
    System.out.print("Y");
}
if (a || (b && c))
{
    System.out.print("Z");
}
```

What is printed as a result of executing this code segment?

(A) `"XYZ"`
(B) `"XZ"`
(C) `"YZ"`
(D) `"XY"`

---

### 11. [U3 · 어려움]

Consider the following code segment.

```java
int x = 5;
int y = 10;
boolean result = !(x > 3 && y < 15) || (x == 5 && !(y != 10));
System.out.println(result);
```

Which of the following is equivalent to the expression assigned to `result`?

(A) `(x <= 3 || y >= 15) || (x == 5 && y == 10)`
(B) `(x <= 3 && y >= 15) || (x == 5 && y == 10)`
(C) `(x <= 3 || y >= 15) && (x == 5 || y == 10)`
(D) `(x > 3 || y < 15) && (x == 5 && y == 10)`

---

### 12. [U3 · 어려움]

Consider the following code segment.

```java
int n = 0;
int x = 7;
if (x > 5 || ++n > 0)
{
    System.out.print(n + " ");
}
if (x < 5 && ++n > 0)
{
    System.out.print(n + " ");
}
if (x < 5 || ++n > 0)
{
    System.out.print(n);
}
```

What is printed as a result of executing this code segment?

(A) `"0 0 1"`
(B) `"0 1"`
(C) `"0 1 1"`
(D) `"0 1 2"`

---

### 13. [U4 · 쉬움]

Consider the following code segment.

```java
int[] arr = {3, 7, 2, 8, 1};
int sum = 0;
for (int val : arr)
{
    if (val % 2 != 0)
    {
        sum += val;
    }
}
System.out.println(sum);
```

What is printed as a result of executing this code segment?

(A) 10
(B) 21
(C) 11
(D) 13

---

### 14. [U4 · 보통]

Consider the following code segment.

```java
int[][] grid = {{1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}};
int total = 0;
for (int c = 0; c < grid[0].length; c++)
{
    for (int r = 0; r < grid.length; r++)
    {
        if (r == c)
        {
            total += grid[r][c];
        }
    }
}
System.out.println(total);
```

What is printed as a result of executing this code segment?

(A) 45
(B) 25
(C) 12
(D) 15

---

### 15. [U4 · 어려움]

Consider the following code segment.

```java
int[][] mat = {{10, 20, 30},
               {40, 50, 60},
               {70, 80, 90}};
String output = "";
for (int c = 0; c < mat[0].length; c++)
{
    for (int r = mat.length - 1; r >= 0; r--)
    {
        output += mat[r][c] + " ";
    }
}
System.out.println(output.trim());
```

What is printed as a result of executing this code segment?

(A) `"70 40 10 80 50 20 90 60 30"`
(B) `"10 20 30 40 50 60 70 80 90"`
(C) `"30 60 90 20 50 80 10 40 70"`
(D) `"70 80 90 40 50 60 10 20 30"`

---

### 16. [U4 · 보통]

Consider the following code segment.

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(5);
list.add(3);
list.add(8);
list.add(3);
list.add(6);

for (int i = list.size() - 1; i >= 0; i--)
{
    if (list.get(i) == 3)
    {
        list.remove(i);
    }
}
System.out.println(list);
```

What is printed as a result of executing this code segment?

(A) `[5, 8, 6]`
(B) `[5, 3, 8, 6]`
(C) `[5, 8, 3, 6]`
(D) An `IndexOutOfBoundsException` is thrown.

---

### 17. [U4 · 어려움]

Consider the following code segment.

```java
ArrayList<String> words = new ArrayList<String>();
words.add("cat");
words.add("dog");
words.add("cat");
words.add("bird");
words.add("cat");

int i = 0;
while (i < words.size())
{
    if (words.get(i).equals("cat"))
    {
        words.remove(i);
    }
    else
    {
        i++;
    }
}
System.out.println(words);
```

What is printed as a result of executing this code segment?

(A) `[dog, bird]`
(B) `[dog, cat, bird]`
(C) `[dog, cat, bird, cat]`
(D) An `IndexOutOfBoundsException` is thrown.

---

### 18. [U4 · 어려움]

Consider the following method.

```java
public static int mystery(int n)
{
    if (n <= 1)
        return 1;
    return mystery(n - 1) + mystery(n - 2);
}
```

How many times is the method `mystery` called in total (including the initial call) when `mystery(6)` is executed?

(A) 6
(B) 8
(C) 13
(D) 25

---

### 19. [U4 · 어려움]

Consider the following code segment that performs selection sort on an array.

```java
int[] arr = {9, 3, 7, 1, 5, 2};

// Selection sort (ascending)
for (int i = 0; i < arr.length - 1; i++)
{
    int minIdx = i;
    for (int j = i + 1; j < arr.length; j++)
    {
        if (arr[j] < arr[minIdx])
        {
            minIdx = j;
        }
    }
    int temp = arr[i];
    arr[i] = arr[minIdx];
    arr[minIdx] = temp;
}
```

What is the state of the array after **exactly 2 passes** of the outer loop (i.e., after `i = 0` and `i = 1` have completed)?

(A) `{1, 2, 7, 9, 5, 3}`
(B) `{1, 2, 7, 3, 5, 9}`
(C) `{1, 2, 9, 7, 5, 3}`
(D) `{1, 2, 3, 7, 5, 9}`

---

### 20. [U4 · 보통]

Consider the following code segment that performs a binary search on a sorted array.

```java
int[] data = {2, 5, 8, 12, 16, 23, 38, 56, 72, 91};
int target = 20;
int lo = 0, hi = data.length - 1;
int comparisons = 0;

while (lo <= hi)
{
    int mid = (lo + hi) / 2;
    comparisons++;
    if (data[mid] == target)
    {
        break;
    }
    else if (data[mid] < target)
    {
        lo = mid + 1;
    }
    else
    {
        hi = mid - 1;
    }
}
System.out.println(comparisons);
```

> **참고**: 이 코드의 `break`는 AP 시험 범위 밖이지만, 코드 추적 연습을 위해 포함했습니다.

What is printed as a result of executing this code segment?

(A) 2
(B) 3
(C) 4
(D) 5

---

### 21. [U4 · 보통]

Consider the following method.

```java
public static int process(int[][] grid)
{
    int count = 0;
    for (int r = 0; r < grid.length; r++)
    {
        for (int c = 0; c < grid[0].length; c++)
        {
            if (r > 0 && grid[r][c] > grid[r - 1][c])
            {
                count++;
            }
            if (c > 0 && grid[r][c] > grid[r][c - 1])
            {
                count++;
            }
        }
    }
    return count;
}
```

What value is returned by `process` when passed the following 2D array?

```
{{3, 1, 4},
 {1, 5, 9},
 {2, 6, 5}}
```

(A) 4
(B) 5
(C) 6
(D) 8

---

# Section II: Free Response (2 Questions | 30 Minutes)

**지시사항:** Write your solutions in Java. You may assume all necessary imports. Assume that the code provided in the question compiles and works correctly. You may write helper methods if you wish.

---

## Question 1: Text Analyzer (7 Points)

다음 `TextAnalyzer` 클래스는 문자열을 분석하여 특정 패턴을 감지하는 메서드를 제공합니다.

```java
public class TextAnalyzer
{
    private String text;

    /** Constructs a TextAnalyzer with the given text.
     *  Precondition: text is not null and has length > 0.
     */
    public TextAnalyzer(String text)
    {
        this.text = text;
    }

    /** Returns the number of times the character sequence target
     *  appears in text. Overlapping occurrences are counted.
     *  For example, if text is "aaaa" and target is "aa",
     *  the method returns 3 (positions 0, 1, and 2).
     *
     *  Precondition: target is not null and has length > 0.
     */
    public int countOverlapping(String target)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a new string where every sequence of consecutive
     *  duplicate characters in text is replaced by a single
     *  occurrence of that character.
     *  For example, if text is "aabbcccaab", the method returns "abcab".
     *  If text is "abcde", the method returns "abcde".
     */
    public String removeDuplicates()
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `countOverlapping` method.

**Examples:**
| `text` | `target` | Return value |
|--------|----------|-------------|
| `"aaaa"` | `"aa"` | `3` |
| `"abcabc"` | `"abc"` | `2` |
| `"hello"` | `"xyz"` | `0` |
| `"abababab"` | `"aba"` | `3` |

### Part (b)

Complete the `removeDuplicates` method. You must use at least one `String` method (`substring`, `indexOf`, `charAt`, `length`, or `equals`) in your solution.

**Examples:**
| `text` | Return value |
|--------|-------------|
| `"aabbcccaab"` | `"abcab"` |
| `"abcde"` | `"abcde"` |
| `"zzz"` | `"z"` |
| `"aAbBcC"` | `"aAbBcC"` |

---

## Question 2: Grid Regions (6 Points)

다음 `GridAnalyzer` 클래스는 2D 정수 배열을 분석합니다. 배열에서 주어진 임계값(threshold) 이상인 값들로 이루어진 영역을 처리합니다.

```java
public class GridAnalyzer
{
    private int[][] grid;

    /** Constructs a GridAnalyzer with the given 2D array.
     *  Precondition: grid is rectangular (all rows have the same length)
     *  and has at least one row and one column.
     */
    public GridAnalyzer(int[][] grid)
    {
        this.grid = grid;
    }

    /** Returns true if the value at position (row, col) is a
     *  "local peak" — meaning it is strictly greater than all of
     *  its horizontal and vertical neighbors (up, down, left, right).
     *  A cell on the border of the grid has fewer neighbors.
     *
     *  Precondition: 0 <= row < grid.length,
     *                0 <= col < grid[0].length
     */
    public boolean isLocalPeak(int row, int col)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a new 2D array of the same dimensions as grid
     *  where each element is:
     *    - 1 if the corresponding element in grid is a local peak
     *      (as determined by isLocalPeak)
     *    - 0 otherwise
     *
     *  The original grid is not modified.
     */
    public int[][] getPeakMap()
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `isLocalPeak` method.

**Example grid:**
```
{{3, 7, 2},
 {5, 9, 4},
 {1, 6, 8}}
```

| Call | Return value | Explanation |
|------|-------------|-------------|
| `isLocalPeak(1, 1)` | `true` | 9 > 7, 9 > 5, 9 > 4, 9 > 6 |
| `isLocalPeak(0, 1)` | `false` | 7 > 3, 7 > 2 이지만 7 < 9 → `false` |
| `isLocalPeak(2, 2)` | `true` | 8 > 4, 8 > 6 (only 2 neighbors) |

### Part (b)

Complete the `getPeakMap` method. You must call `isLocalPeak` in your solution.

**Example:** For the grid above, `getPeakMap()` returns:
```
{{0, 0, 0},
 {0, 1, 0},
 {0, 0, 1}}
```

---
---

# 정답 및 채점

## Section I 정답표

| # | 정답 | Unit | 난이도 | 해설 |
|---|------|------|--------|------|
| 1 | C | U1 | 쉬움 | `(double)(17/5)` = `(double)(3)` = `3.0`. `17 % 5` = `2`. `3.0 + 2` = `5.0`. |
| 2 | B | U1 | 보통 | `29 % 7` = `1`. `1 % 3` = `1`. |
| 3 | C | U1 | 어려움 | `100 / 33` = `3` (int → double = `3.0`). `100 % 33` = `1` (int → double = `1.0`). `3.0 + 1.0` = `4.0`. |
| 4 | A | U2 | 쉬움 | `"COMPUTER".substring(3, 6)` → index 3='P', 4='U', 5='T' → `"PUT"`. |
| 5 | D | U2 | 보통 | `indexOf("nation")` = 5. `substring(0,5)` = `"exami"`. `substring(8)` = `"ion"`. 결과: `"examiion"`. |
| 6 | D | U2 | 어려움 | i=4→result="E", `indexOf("E")`≥0→"E". i=3→"ED", `indexOf("ED")`=-1→"ed". 이후 계속 indexOf=-1→소문자 변환. 최종: `"edcba"`. |
| 7 | B | U2 | 어려움 | `s2`는 `substring`으로 생성한 새 객체→`==` false. `s3="ja"+"va"`는 컴파일 타임 상수→리터럴 풀 공유→`==` true. `equals`는 true. |
| 8 | C | U2 | 보통 | `indexOf("ss",0)`=2, `indexOf("ss",3)`=5, `indexOf("ss",6)`=-1 → count=2. |
| 9 | C | U2 | 어려움 | 객체 3개 생성 후 `totalCount`=3. `c1.myCount`=1 (생성 당시 값). → `"1 3"`. |
| 10 | A | U3 | 보통 | `&&`가 `\|\|`보다 우선순위 높음. 세 조건 모두 `true` → `"XYZ"`. |
| 11 | A | U3 | 어려움 | De Morgan: `!(A && B)` = `!A \|\| !B`. `!(x > 3 && y < 15)` = `(x <= 3 \|\| y >= 15)`. 이를 두 번째 부분과 결합하면 (A). |
| 12 | B | U3 | 어려움 | Short-circuit: 첫 if에서 `x>5` true→`++n` 스킵, n=0 출력. 둘째 if에서 `x<5` false→`++n` 스킵. 셋째 if에서 `x<5` false→`++n` 평가, n=1 출력. → `"0 1"`. |
| 13 | C | U4 | 쉬움 | 홀수: 3 + 7 + 1 = 11. |
| 14 | D | U4 | 보통 | `r == c`인 대각선만 합산: 1 + 5 + 9 = 15. |
| 15 | A | U4 | 어려움 | column-major, 행은 아래→위. c=0: 70,40,10. c=1: 80,50,20. c=2: 90,60,30. |
| 16 | A | U4 | 보통 | 뒤에서부터 삭제→인덱스 밀림 없음. 3 두 개 모두 제거 → `[5, 8, 6]`. |
| 17 | A | U4 | 어려움 | while 루프에서 삭제 시 i 미증가. "cat" 3개 모두 제거 → `[dog, bird]`. |
| 18 | D | U4 | 어려움 | 피보나치 재귀. T(n)=T(n-1)+T(n-2)+1. T(0)=T(1)=1, T(2)=3, T(3)=5, T(4)=9, T(5)=15, T(6)=25. |
| 19 | B | U4 | 어려움 | Pass 1: min=1(idx 3), swap→{1,3,7,9,5,2}. Pass 2: min=2(idx 5), swap→{1,2,7,9,5,3}. |
| 20 | B | U4 | 보통 | mid=4(16<20)→lo=5. mid=7(56>20)→hi=6. mid=5(23>20)→hi=4. lo>hi 종료. 비교 3회. |
| 21 | D | U4 | 보통 | 각 셀에서 위·왼쪽 이웃보다 클 때 count++. 총 8. |

### Section I 최종 정답 (정리)

| # | 정답 | Unit | 난이도 |
|---|------|------|--------|
| 1 | C | U1 | 쉬움 |
| 2 | B | U1 | 보통 |
| 3 | C | U1 | 어려움 |
| 4 | A | U2 | 쉬움 |
| 5 | D | U2 | 보통 |
| 6 | D | U2 | 어려움 |
| 7 | B | U2 | 어려움 |
| 8 | C | U2 | 보통 |
| 9 | C | U2 | 어려움 |
| 10 | A | U3 | 보통 |
| 11 | A | U3 | 어려움 |
| 12 | B | U3 | 어려움 |
| 13 | C | U4 | 쉬움 |
| 14 | D | U4 | 보통 |
| 15 | A | U4 | 어려움 |
| 16 | A | U4 | 보통 |
| 17 | A | U4 | 어려움 |
| 18 | D | U4 | 어려움 |
| 19 | B | U4 | 어려움 |
| 20 | B | U4 | 보통 |
| 21 | D | U4 | 보통 |

---

## Section II 채점기준

### Q1: TextAnalyzer (7점)

#### Part (a) — `countOverlapping` (4점)

**모범 답안:**
```java
public int countOverlapping(String target)
{
    int count = 0;
    for (int i = 0; i <= text.length() - target.length(); i++)
    {
        if (text.substring(i, i + target.length()).equals(target))
        {
            count++;
        }
    }
    return count;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 루프 범위가 올바름 (`i <= text.length() - target.length()` 또는 동등 조건) |
| +1 | `substring`을 사용하여 `target` 길이만큼 추출 |
| +1 | `.equals()`로 문자열 비교 (`==` 사용 시 감점) |
| +1 | `count`를 올바르게 누적하고 반환 |

**감점 사항:**
- `==` 대신 `.equals()` 미사용: -1
- 루프 범위 off-by-one: -1
- `i += target.length()` (overlapping 미지원): Part (a) 의도 불일치, 최대 2점

---

#### Part (b) — `removeDuplicates` (3점)

**모범 답안:**
```java
public String removeDuplicates()
{
    String result = text.substring(0, 1);
    for (int i = 1; i < text.length(); i++)
    {
        if (!text.substring(i, i + 1).equals(text.substring(i - 1, i)))
        {
            result += text.substring(i, i + 1);
        }
    }
    return result;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 첫 문자를 결과에 포함 (또는 이전 문자 추적 변수 초기화) |
| +1 | 인접한 문자를 올바르게 비교 |
| +1 | 다를 때만 결과에 추가하고 올바르게 반환 |

**감점 사항:**
- String 메서드 미사용 (char 배열만 사용 등): -1
- 빈 문자열 반환 또는 첫 문자 누락: -1

---

### Q2: GridAnalyzer (6점)

#### Part (a) — `isLocalPeak` (4점)

**모범 답안:**
```java
public boolean isLocalPeak(int row, int col)
{
    int val = grid[row][col];

    if (row > 0 && grid[row - 1][col] >= val)
        return false;
    if (row < grid.length - 1 && grid[row + 1][col] >= val)
        return false;
    if (col > 0 && grid[row][col - 1] >= val)
        return false;
    if (col < grid[0].length - 1 && grid[row][col + 1] >= val)
        return false;

    return true;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 4방향 이웃 중 존재하는 이웃만 검사 (경계 체크) |
| +1 | 위/아래 이웃 비교 올바름 |
| +1 | 좌/우 이웃 비교 올바름 |
| +1 | "strictly greater than" 조건 정확 (`>=`로 false 반환 또는 `>`로 true 확인) |

**감점 사항:**
- 경계 체크 누락 (`ArrayIndexOutOfBoundsException` 가능): -2
- `>=` 대신 `>` 비교 (같은 값을 peak으로 판정): -1
- 대각선 이웃까지 검사 (문제 조건 위반): -1

---

#### Part (b) — `getPeakMap` (2점)

**모범 답안:**
```java
public int[][] getPeakMap()
{
    int[][] peakMap = new int[grid.length][grid[0].length];
    for (int r = 0; r < grid.length; r++)
    {
        for (int c = 0; c < grid[0].length; c++)
        {
            if (isLocalPeak(r, c))
            {
                peakMap[r][c] = 1;
            }
        }
    }
    return peakMap;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 올바른 크기의 새 2D 배열 생성 및 반환 |
| +1 | `isLocalPeak` 호출하여 peak이면 1, 아니면 0 설정 |

**감점 사항:**
- `isLocalPeak` 미호출 (로직 직접 재구현): -1
- 원본 `grid` 수정: -1

---

## 점수 해석

| 총점 (34점 만점) | 예상 AP 점수 | 설명 |
|-----------------|-------------|------|
| 28–34 | **5** | 목표 달성. 실전에서도 5점 가능성 높음. |
| 21–27 | **4** | 기본기 탄탄하나 고난이도 문제에서 실수. 코드 tracing 연습 필요. |
| 14–20 | **3** | 핵심 개념은 이해하나 적용력 부족. Unit별 약점 집중 보완. |
| 0–13 | — | 추가 학습 필요. 기본 개념부터 재점검 권장. |
