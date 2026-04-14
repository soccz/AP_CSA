# AP Computer Science A — Level Test 7

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
int a = 25;
int b = 7;
System.out.println(a / b + " " + a % b);
```

(A) `3 4`
(B) `3.57 4`
(C) `4 4`
(D) `3 3`

---

### 2. [U1 · 보통]

다음 코드의 출력은?

```java
double x = Math.pow(2, 10);
int y = (int) x;
System.out.println(y);
```

(A) 1024.0
(B) 1024
(C) 1023
(D) 컴파일 에러

---

### 3. [U1 · 어려움]

다음 코드의 출력은?

```java
int x = Math.abs(Integer.MIN_VALUE);
System.out.println(x > 0);
```

(A) `true`
(B) 컴파일 에러
(C) `false`
(D) 런타임 에러

---

### 4. [U2 · 쉬움]

다음 코드의 출력은?

```java
String s = "Hello";
System.out.println(s.substring(1, 2).equals(s.substring(1, 2)));
```

(A) `false`
(B) 컴파일 에러
(C) `"e"`
(D) `true`

---

### 5. [U2 · 보통]

다음 코드의 출력은?

```java
String s = "abcdef";
int count = 0;
for (int i = 0; i < s.length(); i++)
{
    String ch = s.substring(i, i + 1);
    if ("aeiou".indexOf(ch) >= 0)
    {
        count++;
    }
}
System.out.println(count);
```

(A) 2
(B) 1
(C) 3
(D) 0

---

### 6. [U2 · 어려움]

다음 코드의 출력은?

```java
int x = 100;
int sum = 0;
while (x > 0)
{
    if (x % 3 == 0)
    {
        sum += x;
        x -= 30;
    }
    else
    {
        x -= 7;
    }
}
System.out.println(sum);
```

(A) 90
(B) 198
(C) 150
(D) 192

---

### 7. [U2 · 보통]

다음 코드의 출력은?

```java
String s = "Java";
s = s.substring(0, 2) + s.substring(2).toUpperCase();
System.out.println(s);
```

(A) `"JAVA"`
(B) `"JaVA"`
(C) `"JaVa"`
(D) `"java"`

---

### 8. [U2 · 어려움]

다음 코드의 출력은?

```java
String s = "aabaa";
boolean isPalin = true;
for (int i = 0; i < s.length() / 2; i++)
{
    if (s.substring(i, i + 1).compareTo(s.substring(s.length() - 1 - i, s.length() - i)) != 0)
    {
        isPalin = false;
        break;
    }
}
System.out.println(isPalin);
```

> **참고:** `break`는 AP 시험 범위 밖이지만 코드 추적 연습을 위해 포함.

(A) `false`
(B) `StringIndexOutOfBoundsException`
(C) `true`
(D) 컴파일 에러

---

### 9. [U2 · 어려움]

다음 코드의 출력은?

```java
String s = "immutable";
String t = s;
s = s + "!";
System.out.println(s == t);
System.out.println(s.substring(0, 9).equals(t));
```

(A)
```
true
true
```
(B)
```
true
false
```
(C)
```
false
false
```
(D)
```
false
true
```

---

### 10. [U3 · 보통]

다음 코드에서 `search` 메서드의 반환값은?

```java
public static int search(int[] arr, int target)
{
    for (int i = 0; i < arr.length; i++)
    {
        if (arr[i] == target)
            return i;
    }
    return -1;
}
```

`search(new int[]{5, 3, 8, 3, 1}, 3)`의 반환값은?

(A) 1
(B) 3
(C) -1
(D) 2

---

### 11. [U3 · 어려움]

다음 두 표현이 논리적 대우(contrapositive) 관계인 것은?

원래 조건: `if (x > 0) then (y > 0)`

대우는?

(A) `if (y > 0) then (x > 0)`
(B) `if (x <= 0) then (y <= 0)`
(C) `if (y > 0) then (x <= 0)`
(D) `if (y <= 0) then (x <= 0)`

---

### 12. [U3 · 어려움]

다음 코드의 출력은?

```java
int[] arr = {3, -1, 4, -1, 5, -9};
boolean found = false;
int i = 0;
while (!found && i < arr.length)
{
    if (arr[i] < 0)
        found = true;
    i++;
}
System.out.println(found + " " + i);
```

(A) `true 1`
(B) `true 2`
(C) `false 6`
(D) `true 4`

---

### 13. [U4 · 쉬움]

다음 코드의 출력은?

```java
int[] arr = {1, 2, 3, 4, 5};
for (int i = 0; i < arr.length / 2; i++)
{
    int temp = arr[i];
    arr[i] = arr[arr.length - 1 - i];
    arr[arr.length - 1 - i] = temp;
}
System.out.println(Arrays.toString(arr));
```

(A) `[5, 4, 3, 2, 1]`
(B) `[1, 2, 3, 4, 5]`
(C) `[5, 2, 3, 4, 1]`
(D) `[5, 4, 3, 4, 5]`

---

### 14. [U4 · 보통]

다음 코드의 출력은?

```java
ArrayList<String> list = new ArrayList<String>();
list.add("a");
list.add("b");
list.add("c");
list.add("a");
list.remove("a");
System.out.println(list);
```

(A) `[b, c]`
(B) `[a, b, c]`
(C) `[b, c, a]`
(D) `[b, c, a, a]`

---

### 15. [U4 · 어려움]

다음 코드의 출력은?

```java
int[][] grid = {{1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}};
// Swap row 0 and row 2
int[] temp = grid[0];
grid[0] = grid[2];
grid[2] = temp;
System.out.println(grid[0][1] + " " + grid[2][1]);
```

(A) `2 8`
(B) `2 2`
(C) `8 8`
(D) `8 2`

---

### 16. [U4 · 보통]

다음 재귀 메서드에서 `remove("hello", 'l')` 의 반환값은?

```java
public static String remove(String s, char c)
{
    if (s.length() == 0)
        return "";
    if (s.substring(0, 1).equals("" + c))
        return remove(s.substring(1), c);
    return s.substring(0, 1) + remove(s.substring(1), c);
}
```

(A) `"hello"`
(B) `"heo"`
(C) `"helo"`
(D) `""`

---

### 17. [U4 · 어려움]

다음 insertion sort에서 `{4, 2, 7, 1}` 정렬 시 총 swap(shift) 횟수는?

```java
int[] arr = {4, 2, 7, 1};
int shifts = 0;
for (int i = 1; i < arr.length; i++)
{
    int key = arr[i];
    int j = i - 1;
    while (j >= 0 && arr[j] > key)
    {
        arr[j + 1] = arr[j];
        j--;
        shifts++;
    }
    arr[j + 1] = key;
}
System.out.println(shifts);
```

(A) 3
(B) 5
(C) 4
(D) 6

---

### 18. [U4 · 어려움]

다음 코드의 출력은?

```java
int[][] grid = {{1, 0, 0},
                {0, 1, 0},
                {0, 0, 1}};
int count = 0;
for (int r = 0; r < grid.length; r++)
{
    for (int c = 0; c < grid[0].length; c++)
    {
        if (grid[r][c] == 1)
        {
            // Count non-zero neighbors (4 directions)
            if (r > 0 && grid[r-1][c] == 1) count++;
            if (r < grid.length-1 && grid[r+1][c] == 1) count++;
            if (c > 0 && grid[r][c-1] == 1) count++;
            if (c < grid[0].length-1 && grid[r][c+1] == 1) count++;
        }
    }
}
System.out.println(count);
```

(A) 3
(B) 6
(C) 2
(D) 0

---

### 19. [U4 · 보통]

다음 코드의 출력은?

```java
int[] arr1 = {1, 2, 3};
int[] arr2 = {4, 5, 6};
int[] arr3 = new int[6];

for (int i = 0; i < arr1.length; i++)
    arr3[i] = arr1[i];
for (int i = 0; i < arr2.length; i++)
    arr3[arr1.length + i] = arr2[i];

System.out.println(Arrays.toString(arr3));
```

(A) `[1, 2, 3, 4, 5, 6]`
(B) `[4, 5, 6, 1, 2, 3]`
(C) `[1, 4, 2, 5, 3, 6]`
(D) `[0, 0, 0, 0, 0, 0]`

---

### 20. [U4 · 어려움]

다음 코드의 출력은?

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(1);
list.add(3);
list.add(5);
list.add(7);
list.add(9);

ArrayList<Integer> result = new ArrayList<Integer>();
for (int val : list)
{
    if (val >= 3 && val <= 7)
        result.add(val);
}
System.out.println(result);
```

(A) `[1, 3, 5, 7, 9]`
(B) `[1, 9]`
(C) `[3, 5, 7]`
(D) `[5]`

---

### 21. [U4 · 보통]

다음 코드에서 두 배열이 같은 내용인지 확인하는 메서드의 반환값은?

```java
public static boolean arraysEqual(int[] a, int[] b)
{
    if (a.length != b.length)
        return false;
    for (int i = 0; i < a.length; i++)
    {
        if (a[i] != b[i])
            return false;
    }
    return true;
}
```

`arraysEqual(new int[]{1, 2, 3}, new int[]{1, 2, 3})`의 반환값은?

(A) `false`
(B) `true`
(C) 컴파일 에러
(D) 런타임 에러

---

# Section II: Free Response (2 Questions | 30 Minutes)

**지시사항:** Write your solutions in Java. You may assume all necessary imports.

---

## Question 1: StringEncoder (7 Points)

다음 `StringEncoder` 클래스는 문자열을 인코딩하는 메서드를 제공합니다.

```java
public class StringEncoder
{
    /** Applies a Caesar cipher shift to all uppercase letters in text.
     *  Each uppercase letter is shifted by the given amount (wrapping
     *  from Z back to A). Non-uppercase characters are unchanged.
     *
     *  Examples:
     *    caesarShift("HELLO", 3) returns "KHOOR"
     *    caesarShift("XYZ", 3) returns "ABC"
     *    caesarShift("HELLO WORLD", 1) returns "IFMMP XPSME"
     *    caesarShift("abc", 5) returns "abc"   (lowercase unchanged)
     *
     *  Precondition: text is not null, shift >= 0
     */
    public static String caesarShift(String text, int shift)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a run-length encoded version of the string s.
     *  Each character is followed by its consecutive count.
     *
     *  Examples:
     *    runLengthEncode("aaabbc") returns "a3b2c1"
     *    runLengthEncode("a") returns "a1"
     *    runLengthEncode("aaa") returns "a3"
     *    runLengthEncode("abcd") returns "a1b1c1d1"
     *
     *  Precondition: s is not null and has length >= 1.
     */
    public static String runLengthEncode(String s)
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `caesarShift` method. You may use `charAt` and casting between `char` and `int`.

**Hint:** `'A'` has value 65, `'Z'` has value 90. To shift a character: `(char)('A' + (ch - 'A' + shift) % 26)`.

### Part (b)

Complete the `runLengthEncode` method.

---

## Question 2: GameBoard (6 Points)

다음 `GameBoard` 클래스는 2D 정수 배열 기반의 게임 보드를 분석합니다.

```java
public class GameBoard
{
    private int[][] board;

    /** Constructs a GameBoard with the given 2D array.
     *  Precondition: board is rectangular with at least 1 row and 1 column.
     */
    public GameBoard(int[][] board)
    {
        this.board = board;
    }

    /** Returns the number of non-zero neighbors of the cell at (row, col).
     *  Neighbors include all 8 surrounding cells (horizontal, vertical,
     *  and diagonal). Cells on the border have fewer neighbors.
     *
     *  Example grid:
     *    {{0, 1, 0},
     *     {1, 1, 1},
     *     {0, 1, 0}}
     *
     *    countNeighbors(1, 1) returns 4
     *      (neighbors at (0,1), (1,0), (1,2), (2,1) are non-zero)
     *    countNeighbors(0, 0) returns 3
     *      (neighbors: (0,1)=1, (1,0)=1, (1,1)=1 → 3 non-zero)
     *
     *  Precondition: 0 <= row < board.length, 0 <= col < board[0].length
     */
    public int countNeighbors(int row, int col)
    {
        /* to be implemented in Part (a) */
    }

    /** Checks if any row, column, or diagonal (both main and anti-diagonal) of the square board
     *  contains all the same non-zero value.
     *  Returns that value if found, or 0 if no such line exists.
     *  If multiple lines qualify, return any qualifying value.
     *
     *  Example:
     *    {{1, 2, 0},
     *     {1, 1, 0},
     *     {1, 0, 1}}
     *    → returns 1 (column 0 is all 1s)
     *
     *    {{1, 2, 3},
     *     {4, 5, 6},
     *     {7, 8, 9}}
     *    → returns 0 (no complete line)
     *
     *  Precondition: board is square.
     */
    public int hasWinner()
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `countNeighbors` method.

### Part (b)

Complete the `hasWinner` method. Check rows, columns, and both main diagonals.

---
---

# 정답 및 채점

## Section I 정답표

| # | 정답 | Unit | 난이도 | 해설 |
|---|------|------|--------|------|
| 1 | A | U1 | 쉬움 | `25 / 7` = 3, `25 % 7` = 4. |
| 2 | B | U1 | 보통 | `Math.pow(2, 10)` = 1024.0. `(int) 1024.0` = 1024. |
| 3 | C | U1 | 어려움 | `Integer.MIN_VALUE`의 절대값은 int 범위 초과 → 오버플로 → `Integer.MIN_VALUE` (음수). `x > 0`은 `false`. |
| 4 | D | U2 | 쉬움 | `equals`는 내용 비교 → `"e".equals("e")` = `true`. |
| 5 | A | U2 | 보통 | 모음: a(idx 0), e(idx 4). count = 2. |
| 6 | D | U2 | 어려움 | x=100: 100%3=1≠0 → x=93. 93%3=0 → sum=93, x=63. 63%3=0 → sum=156, x=33. 33%3=0 → sum=189, x=3. 3%3=0 → sum=192, x=-27. 종료. sum=192. |
| 7 | B | U2 | 보통 | `s.substring(2)` = `"va"`. `"va".toUpperCase()` = `"VA"`. `"Ja" + "VA"` = `"JaVA"`. |
| 8 | C | U2 | 어려움 | `"aabaa"`: i=0: `"a"` vs `"a"` OK. i=1: `"a"` vs `"a"` OK. 루프 종료(length/2=2). 회문. `true`. |
| 9 | D | U2 | 어려움 | `s = s + "!"`는 새 객체. `s == t` → `false`. `s.substring(0, 9)` = `"immutable"`, `t` = `"immutable"`. `equals` → `true`. |
| 10 | A | U3 | 보통 | 첫 번째 3의 인덱스 반환. index 1. |
| 11 | D | U3 | 어려움 | 대우: `if P then Q`의 대우는 `if !Q then !P`. `if (y <= 0) then (x <= 0)`. |
| 12 | B | U3 | 어려움 | i=0: arr[0]=3 ≥ 0, i=1. i=1: arr[1]=-1 < 0, found=true, i=2. 루프 종료. `"true 2"`. |
| 13 | A | U4 | 쉬움 | 배열 뒤집기. {1,2,3,4,5} → {5,4,3,2,1}. |
| 14 | C | U4 | 보통 | `remove("a")`는 첫 번째 "a"만 제거. [b, c, a]. |
| 15 | D | U4 | 어려움 | 2D 배열에서 행은 참조. row 0과 row 2를 swap. `grid[0]`은 이제 {7,8,9}. `grid[0][1]`=8, `grid[2][1]`=2. |
| 16 | B | U4 | 보통 | 재귀적으로 'l' 제거. "hello" → "h" + remove("ello",'l') → "h" + "e" + remove("llo",'l') → "he" + remove("lo",'l') → "he" + remove("o",'l') → "he" + "o" = "heo". |
| 17 | C | U4 | 어려움 | i=1: key=2, 4>2 shift(1회) → {4,4,7,1}, arr[0]=2 → {2,4,7,1}. i=2: key=7, 4<7 shift 없음. i=3: key=1, 7>1 shift(1), 4>1 shift(1), 2>1 shift(1) → 3회. 총: 1+0+3 = 4. |
| 18 | D | U4 | 어려움 | 단위행렬. 각 1의 4방향 이웃은 모두 0. count = 0. |
| 19 | A | U4 | 보통 | 두 배열 연결. [1,2,3,4,5,6]. |
| 20 | C | U4 | 어려움 | 3 이상 7 이하: 3, 5, 7. `[3, 5, 7]`. |
| 21 | B | U4 | 보통 | 원소별 비교. 모두 같으므로 `true`. |

### Section I 최종 정답

| # | 정답 |
|---|------|
| 1 | A |
| 2 | B |
| 3 | C |
| 4 | D |
| 5 | A |
| 6 | D |
| 7 | B |
| 8 | C |
| 9 | D |
| 10 | A |
| 11 | D |
| 12 | B |
| 13 | A |
| 14 | C |
| 15 | D |
| 16 | B |
| 17 | C |
| 18 | D |
| 19 | A |
| 20 | C |
| 21 | B |

---

## Section II 채점기준

### Q1: StringEncoder (7점)

#### Part (a) — `caesarShift` (4점)

**모범 답안:**
```java
public static String caesarShift(String text, int shift)
{
    String result = "";
    for (int i = 0; i < text.length(); i++)
    {
        char ch = text.charAt(i);
        if (ch >= 'A' && ch <= 'Z')
        {
            ch = (char)('A' + (ch - 'A' + shift) % 26);
        }
        result += ch;
    }
    return result;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 문자열을 순회하는 루프 |
| +1 | 대문자('A'-'Z')만 변환, 나머지는 그대로 |
| +1 | shift 후 % 26으로 wrap-around 처리 |
| +1 | 올바른 결과 문자열 반환 (algorithm point) |

**감점 사항:**
- wrap-around 누락 (Z 이후 처리 안 함): -1
- 소문자도 변환: -1 (문제 조건 위반)

---

#### Part (b) — `runLengthEncode` (3점)

**모범 답안:**
```java
public static String runLengthEncode(String s)
{
    String result = "";
    int count = 1;
    for (int i = 1; i < s.length(); i++)
    {
        if (s.substring(i, i + 1).equals(s.substring(i - 1, i)))
        {
            count++;
        }
        else
        {
            result += s.substring(i - 1, i) + count;
            count = 1;
        }
    }
    result += s.substring(s.length() - 1) + count;
    return result;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 연속 동일 문자를 카운트하는 루프 |
| +1 | 그룹 끝날 때 "문자+카운트" 형식으로 추가 |
| +1 | 마지막 그룹 처리 + 올바르게 반환 |

---

### Q2: GameBoard (6점)

#### Part (a) — `countNeighbors` (4점)

**모범 답안:**
```java
public int countNeighbors(int row, int col)
{
    int count = 0;
    for (int r = row - 1; r <= row + 1; r++)
    {
        for (int c = col - 1; c <= col + 1; c++)
        {
            if (r >= 0 && r < board.length && c >= 0 && c < board[0].length
                && !(r == row && c == col))
            {
                if (board[r][c] != 0)
                {
                    count++;
                }
            }
        }
    }
    return count;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 8방향 이웃을 검사하는 루프/조건 |
| +1 | 경계 체크 (인덱스 범위 확인) |
| +1 | 자기 자신 제외 (`!(r == row && c == col)`) |
| +1 | non-zero 카운트 + 올바른 반환 |

**감점 사항:**
- 자기 자신 포함: -1
- 4방향만 검사 (대각선 누락): -1
- 경계 체크 누락: -1

---

#### Part (b) — `hasWinner` (2점)

**모범 답안:**
```java
public int hasWinner()
{
    int n = board.length;

    // Check rows
    for (int r = 0; r < n; r++)
    {
        if (board[r][0] != 0)
        {
            boolean allSame = true;
            for (int c = 1; c < n; c++)
            {
                if (board[r][c] != board[r][0])
                    allSame = false;
            }
            if (allSame) return board[r][0];
        }
    }

    // Check columns
    for (int c = 0; c < n; c++)
    {
        if (board[0][c] != 0)
        {
            boolean allSame = true;
            for (int r = 1; r < n; r++)
            {
                if (board[r][c] != board[0][c])
                    allSame = false;
            }
            if (allSame) return board[0][c];
        }
    }

    // Check main diagonal
    if (board[0][0] != 0)
    {
        boolean allSame = true;
        for (int i = 1; i < n; i++)
        {
            if (board[i][i] != board[0][0])
                allSame = false;
        }
        if (allSame) return board[0][0];
    }

    // Check anti-diagonal
    if (board[0][n - 1] != 0)
    {
        boolean allSame = true;
        for (int i = 1; i < n; i++)
        {
            if (board[i][n - 1 - i] != board[0][n - 1])
                allSame = false;
        }
        if (allSame) return board[0][n - 1];
    }

    return 0;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 행, 열, 대각선 중 하나 이상을 검사하며 non-zero 체크 |
| +1 | 모든 방향(행+열+양 대각선) 올바르게 검사 + 값 반환 또는 0 반환 |

**감점 사항:**
- 대각선 검사 누락: -1
- non-zero 체크 누락 (0으로 가득 찬 행을 winner로 판정): -1

---

## 점수 해석

| 총점 (34점 만점) | 예상 AP 점수 | 설명 |
|-----------------|-------------|------|
| 28–34 | **5** | 목표 달성. 실전에서도 5점 가능성 높음. |
| 21–27 | **4** | 기본기 탄탄하나 고난이도 문제에서 실수. 코드 tracing 연습 필요. |
| 14–20 | **3** | 핵심 개념은 이해하나 적용력 부족. Unit별 약점 집중 보완. |
| 0–13 | — | 추가 학습 필요. 기본 개념부터 재점검 권장. |
