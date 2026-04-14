# AP Computer Science A — Level Test 4

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
int a = 14;
int b = 4;
a += b;
b *= 2;
System.out.println(a + " " + b);
```

(A) `14 8`
(B) `18 4`
(C) `18 8`
(D) `56 8`

---

### 2. [U1 · 보통]
> **참고:** `byte` 타입은 AP CSA 범위 밖이지만, 형변환 개념 심화를 위해 포함했습니다.

다음 코드의 출력은?

```java
int x = 130;
byte b = (byte) x;
System.out.println(b);
```

(A) 130
(B) -126
(C) 0
(D) 컴파일 에러

---

### 3. [U1 · 어려움]

다음 코드의 출력은?

```java
int a = Integer.MAX_VALUE;
int b = a + 1;
System.out.println(b == Integer.MIN_VALUE);
```

(A) 컴파일 에러
(B) `false`
(C) `true`
(D) 런타임 에러

---

### 4. [U2 · 쉬움]

다음 코드의 출력은?

```java
String[] parts = "one,two,three".split(",");
System.out.println(parts.length + " " + parts[1]);
```

(A) `3 two`
(B) `3 one`
(C) `2 two`
(D) `13 ,`

---

### 5. [U2 · 보통]

다음 코드의 출력은?

```java
int n = 1;
int count = 0;
while (n < 100)
{
    n *= 3;
    count++;
}
System.out.println(count + " " + n);
```

(A) `4 81`
(B) `5 81`
(C) `4 243`
(D) `5 243`

---

### 6. [U2 · 어려움]

다음 코드의 출력은?

```java
String result = "";
for (int i = 1; i <= 4; i++)
{
    for (int j = 1; j <= i; j++)
    {
        result += "*";
    }
    result += "\n";
}
System.out.print(result);
```

(A)
```
*
***
*****
*******
```

(B)
```
****
***
**
*
```

(C)
```
*
**
***
****
```

(D)
```
****
****
****
****
```

---

### 7. [U2 · 보통]

다음 코드의 출력은?

```java
String s1 = "HELLO";
String s2 = "HELP";
System.out.println(s1.compareTo(s2));
```

다음 중 올바른 것은?

(A) 양수
(B) 음수
(C) 0
(D) 컴파일 에러

---

### 8. [U2 · 어려움]

다음 코드의 출력은?

```java
String s = "abcabc";
String result = "";
int pos = s.indexOf("bc", 0);
while (pos != -1)
{
    result += pos + " ";
    pos = s.indexOf("bc", pos + 1);
}
System.out.println(result.trim());
```

(A) `1 4`
(B) `1`
(C) `1 3 4`
(D) `1 2 4`

---

### 9. [U2 · 어려움]

다음 메서드가 있다.

```java
public static String build(int n)
{
    String s = "";
    for (int i = 0; i < n; i++)
    {
        if (i % 2 == 0)
            s += (char)('A' + i);
        else
            s += (char)('a' + i);
    }
    return s;
}
```

`build(6)`의 반환값은?

(A) `"AcEgIk"`
(B) `"ABCDEF"`
(C) `"AbcDef"`
(D) `"AbCdEf"`

---

### 10. [U3 · 보통]

다음 코드의 출력은?

```java
int x = 12;
int y = 5;
boolean a = (x > 10) && (y > 3);
boolean b = (x < 10) || (y < 3);
boolean c = !a || b;
System.out.println(a + " " + b + " " + c);
```

(A) `false true true`
(B) `true false true`
(C) `true false false`
(D) `true true true`

---

### 11. [U3 · 어려움]

다음 조건들 중 `!(p && !q)` 와 논리적으로 동치인 것은?

(A) `!p && q`
(B) `!p || q`
(C) `p || !q`
(D) `p && !q`

---

### 12. [U3 · 어려움]

다음 코드의 출력은?

```java
int[] arr = {5, 0, 3, 0, 7};
int i = 0;
while (i < arr.length && arr[i] != 0)
{
    System.out.print(arr[i] + " ");
    i++;
}
System.out.print("done");
```

(A) `5 0 3 0 7 done`
(B) `done`
(C) `5 3 7 done`
(D) `5 done`

---

### 13. [U4 · 쉬움]

다음 코드의 출력은?

```java
int[] arr = {10, 20, 30, 40, 50};
int temp = arr[0];
arr[0] = arr[4];
arr[4] = temp;
System.out.println(arr[0] + " " + arr[4]);
```

(A) `50 50`
(B) `10 50`
(C) `50 10`
(D) `10 10`

---

### 14. [U4 · 보통]

다음 코드의 출력은?

```java
int[] arr = {2, 4, 6, 8, 10};
int[] copy = arr;
copy[2] = 99;
System.out.println(arr[2]);
```

(A) 6
(B) 99
(C) 0
(D) 컴파일 에러

---

### 15. [U4 · 어려움]

다음 코드는 insertion sort를 수행한다. 2번째 패스(i = 2)까지 완료한 후 배열 상태는?

```java
int[] arr = {5, 3, 8, 1, 4};
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

(A) `{1, 3, 5, 8, 4}`
(B) `{3, 5, 8, 1, 4}`
(C) `{3, 5, 1, 8, 4}`
(D) `{1, 3, 5, 4, 8}`

---

### 16. [U4 · 보통]

다음 코드의 출력은?

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(10);
list.add(20);
list.add(30);
list.add(1, 15);
list.add(3, 25);
System.out.println(list);
```

(A) `[10, 15, 20, 30, 25]`
(B) `[15, 10, 20, 25, 30]`
(C) `[10, 15, 20, 25, 30]`
(D) `[10, 15, 25, 20, 30]`

---

### 17. [U4 · 어려움]

다음 코드의 출력은?

```java
int[][] grid = {{1, 2, 3, 4},
                {5, 6, 7, 8},
                {9, 10, 11, 12}};
int sum = 0;
for (int c = 0; c < grid[0].length; c++)
{
    for (int r = 0; r < grid.length; r++)
    {
        sum += grid[r][c];
    }
}
System.out.println(sum);
```

(A) 45
(B) 26
(C) 15
(D) 78

---

### 18. [U4 · 어려움]

다음 메서드가 있다.

```java
public static String mystery(String s)
{
    if (s.length() <= 1)
        return s;
    return mystery(s.substring(1)) + s.substring(0, 1);
}
```

`mystery("CODE")`의 반환값은?

(A) `"CODE"`
(B) `"CDOE"`
(C) `"ODEC"`
(D) `"EDOC"`

---

### 19. [U4 · 보통]

다음 코드의 출력은?

```java
int[] arr = {1, 2, 3, 4, 5};
int last = arr[arr.length - 1];
for (int i = arr.length - 1; i > 0; i--)
{
    arr[i] = arr[i - 1];
}
arr[0] = last;
System.out.println(Arrays.toString(arr));
```

(A) `[5, 1, 2, 3, 4]`
(B) `[2, 3, 4, 5, 1]`
(C) `[1, 1, 2, 3, 4]`
(D) `[5, 5, 5, 5, 5]`

---

### 20. [U4 · 어려움]

다음 코드의 출력은?

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(1);
list.add(2);
list.add(3);
list.add(4);
list.add(5);

for (int i = 0; i < list.size(); i++)
{
    if (list.get(i) % 2 == 0)
    {
        list.remove(i);
    }
}
System.out.println(list);
```

(A) `[1, 3, 5]`
(B) `[1, 3, 4, 5]`
(C) `[1, 2, 3, 5]`
(D) `[1, 3, 5, 4]`

---

### 21. [U4 · 보통]

다음 코드에서 merge sort의 merge 단계가 실행된다. 두 정렬된 부분을 합친 결과는?

```java
int[] left = {2, 5, 8};
int[] right = {1, 4, 9};
```

merge 결과 배열의 3번째 요소(index 2)는?

(A) 4
(B) 5
(C) 3
(D) 8

---

# Section II: Free Response (2 Questions | 30 Minutes)

**지시사항:** Write your solutions in Java. You may assume all necessary imports. Assume that the code provided in the question compiles and works correctly. You may write helper methods if you wish.

---

## Question 1: WordProcessor (7 Points)

다음 `WordProcessor` 클래스는 문자열을 가공하는 메서드를 제공합니다.

```java
public class WordProcessor
{
    /** Returns the number of vowel groups in the given word.
     *  A vowel group is a maximal consecutive sequence of vowels (a, e, i, o, u,
     *  case-insensitive).
     *
     *  Examples:
     *    countVowelGroups("beautiful") returns 3
     *      (groups: "eau", "i", "u")
     *    countVowelGroups("rhythm") returns 0
     *    countVowelGroups("aeiou") returns 1
     *    countVowelGroups("hello") returns 2
     *      (groups: "e", "o")
     *
     *  Precondition: word is not null and has length > 0.
     */
    public static int countVowelGroups(String word)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns an abbreviated version of the given sentence.
     *  Each word (separated by single spaces) is abbreviated as follows:
     *    - If the word has more than 3 characters, keep only the first
     *      and last character.
     *    - Otherwise, keep the word as is.
     *  The abbreviated words are joined by single spaces.
     *
     *  Examples:
     *    abbreviate("computer science is fun")
     *      returns "cr se is fn"
     *    abbreviate("I am a student")
     *      returns "I am a st"
     *    abbreviate("hi") returns "hi"
     *    abbreviate("java") returns "ja"
     *
     *  Precondition: sentence is not null, has length > 0, and contains
     *  no leading/trailing spaces or consecutive spaces.
     */
    public static String abbreviate(String sentence)
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `countVowelGroups` method.

### Part (b)

Complete the `abbreviate` method. You must use the `split` method of `String` in your solution.

---

## Question 2: MatrixOperator (6 Points)

다음 `MatrixOperator` 클래스는 2D 정수 배열(정사각 행렬)을 분석합니다.

```java
public class MatrixOperator
{
    private int[][] matrix;

    /** Constructs a MatrixOperator with the given square matrix.
     *  Precondition: matrix is square (rows == cols), has at least 1 row.
     */
    public MatrixOperator(int[][] matrix)
    {
        this.matrix = matrix;
    }

    /** Returns true if the matrix is symmetric.
     *  A matrix is symmetric if matrix[r][c] == matrix[c][r]
     *  for all valid r and c.
     *
     *  Example:
     *    {{1, 2, 3},
     *     {2, 5, 4},
     *     {3, 4, 9}}   → true
     *
     *    {{1, 2, 3},
     *     {4, 5, 6},
     *     {7, 8, 9}}   → false
     */
    public boolean isSymmetric()
    {
        /* to be implemented in Part (a) */
    }

    /** Returns the index of the row with the largest sum.
     *  If there is a tie, returns the smallest index.
     *
     *  Example:
     *    {{1, 2, 3},    row 0 sum = 6
     *     {4, 5, 6},    row 1 sum = 15
     *     {7, 8, 0}}    row 2 sum = 15
     *    → returns 1 (first row with max sum)
     */
    public int getRowWithMaxSum()
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `isSymmetric` method.

### Part (b)

Complete the `getRowWithMaxSum` method.

---
---

# 정답 및 채점

## Section I 정답표

| # | 정답 | Unit | 난이도 | 해설 |
|---|------|------|--------|------|
| 1 | C | U1 | 쉬움 | `a += b` → `a = 14 + 4 = 18`. `b *= 2` → `b = 4 * 2 = 8`. 출력: `18 8`. |
| 2 | B | U1 | 보통 | `byte`는 -128~127 범위. 130은 범위 초과 → 오버플로. 130 - 256 = -126. |
| 3 | C | U1 | 어려움 | `Integer.MAX_VALUE + 1`은 정수 오버플로 → `Integer.MIN_VALUE`. `b == Integer.MIN_VALUE`는 `true`. |
| 4 | A | U2 | 쉬움 | `"one,two,three".split(",")` → `{"one", "two", "three"}`. `length` = 3, `parts[1]` = `"two"`. |
| 5 | D | U2 | 보통 | n: 1→3→9→27→81→243. 243 ≥ 100이므로 루프 종료. count = 5, n = 243. |
| 6 | C | U2 | 어려움 | i=1: `"*\n"`, i=2: `"**\n"`, i=3: `"***\n"`, i=4: `"****\n"`. 삼각형 패턴. |
| 7 | B | U2 | 보통 | `"HELLO".compareTo("HELP")`: 'L'(76) vs 'P'(80) → 76 - 80 = -4. 음수. |
| 8 | A | U2 | 어려움 | pos=1 (`"bc"` at index 1), 다음 `indexOf("bc", 2)` = 4. 다음 `indexOf("bc", 5)` = -1. 출력: `"1 4"`. |
| 9 | D | U2 | 어려움 | i=0(짝수): `'A'+0`='A'. i=1(홀수): `'a'+1`='b'. i=2(짝수): `'A'+2`='C'. i=3(홀수): `'a'+3`='d'. i=4(짝수): `'A'+4`='E'. i=5(홀수): `'a'+5`='f'. → `"AbCdEf"`. |
| 10 | C | U3 | 보통 | a = `true && true` = `true`. b = `false || false` = `false`. c = `!true || false` = `false || false` = `false`. |
| 11 | B | U3 | 어려움 | De Morgan: `!(p && !q)` = `!p || !!q` = `!p || q`. |
| 12 | D | U3 | 어려움 | Short-circuit: `arr[0]` = 5 ≠ 0 → 출력 5. `arr[1]` = 0이므로 `arr[i] != 0` false → 루프 종료. 출력: `"5 done"`. |
| 13 | C | U4 | 쉬움 | swap: arr[0]과 arr[4] 교환. arr[0]=50, arr[4]=10. 출력: `"50 10"`. |
| 14 | B | U4 | 보통 | `copy = arr`는 참조 복사. `copy[2] = 99` → `arr[2]`도 99. |
| 15 | B | U4 | 어려움 | i=1: key=3, 5>3이므로 shift → {5,5,8,1,4}, arr[0]=3 → {3,5,8,1,4}. i=2: key=8, 5<8이므로 shift 없음 → {3,5,8,1,4}. |
| 16 | C | U4 | 보통 | 초기: [10,20,30]. `add(1,15)` → [10,15,20,30]. `add(3,25)` → [10,15,20,25,30]. |
| 17 | D | U4 | 어려움 | 전체 합: 1+2+...+12 = 78. column-first든 row-first든 전체 합은 동일. |
| 18 | D | U4 | 어려움 | 재귀적 문자열 뒤집기. `mystery("CODE")` = `mystery("ODE") + "C"` = `mystery("DE") + "O" + "C"` = `mystery("E") + "D" + "O" + "C"` = `"E" + "D" + "O" + "C"` = `"EDOC"`. |
| 19 | A | U4 | 보통 | 오른쪽 회전: 마지막 원소를 앞으로. {1,2,3,4,5} → {5,1,2,3,4}. |
| 20 | A | U4 | 어려움 | i=0: get(0)=1, 홀수 → i=1. i=1: get(1)=2, 짝수 → remove(1) → [1,3,4,5], i=2. i=2: get(2)=4, 짝수 → remove(2) → [1,3,5], i=3. size=3 → 종료. 결과: [1,3,5]. remove 후 인덱스 밀림이 있으나, 이 데이터에서는 짝수가 인접하지 않아 모두 제거됨. |
| 21 | A | U4 | 보통 | merge: 1,2,4,5,8,9. index 2 → 4. |

### Section I 최종 정답

| # | 정답 |
|---|------|
| 1 | C |
| 2 | B |
| 3 | C |
| 4 | A |
| 5 | D |
| 6 | C |
| 7 | B |
| 8 | A |
| 9 | D |
| 10 | C |
| 11 | B |
| 12 | D |
| 13 | C |
| 14 | B |
| 15 | B |
| 16 | C |
| 17 | D |
| 18 | D |
| 19 | A |
| 20 | A |
| 21 | A |

---

## Section II 채점기준

### Q1: WordProcessor (7점)

#### Part (a) — `countVowelGroups` (4점)

**모범 답안:**
```java
public static int countVowelGroups(String word)
{
    String vowels = "aeiouAEIOU";
    int count = 0;
    boolean inGroup = false;

    for (int i = 0; i < word.length(); i++)
    {
        String ch = word.substring(i, i + 1);
        if (vowels.indexOf(ch) >= 0)
        {
            if (!inGroup)
            {
                count++;
                inGroup = true;
            }
        }
        else
        {
            inGroup = false;
        }
    }
    return count;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 문자열 전체를 순회하는 루프 |
| +1 | 각 문자가 모음인지 올바르게 판별 (대소문자 모두) |
| +1 | boolean 플래그 등으로 "그룹의 시작"만 카운트 |
| +1 | count를 올바르게 누적하고 반환 (algorithm point) |

**감점 사항:**
- 대소문자 구분 못함: -1
- 모든 모음 개별 카운트 (그룹이 아님): 최대 2점
- 모음 목록 불완전 ('u' 누락 등): -1

---

#### Part (b) — `abbreviate` (3점)

**모범 답안:**
```java
public static String abbreviate(String sentence)
{
    String[] words = sentence.split(" ");
    String result = "";
    for (int i = 0; i < words.length; i++)
    {
        if (i > 0)
            result += " ";
        if (words[i].length() > 3)
            result += words[i].substring(0, 1) + words[i].substring(words[i].length() - 1);
        else
            result += words[i];
    }
    return result;
}
```

| 점수 | 기준 |
|------|------|
| +1 | `split(" ")`으로 단어 분리 |
| +1 | 길이 > 3인 단어를 첫 글자 + 마지막 글자로 축약 |
| +1 | 단어들을 공백으로 연결하여 올바르게 반환 |

**감점 사항:**
- `split` 미사용: -1
- 공백 처리 오류 (앞뒤 여분 공백): -1

---

### Q2: MatrixOperator (6점)

#### Part (a) — `isSymmetric` (4점)

**모범 답안:**
```java
public boolean isSymmetric()
{
    for (int r = 0; r < matrix.length; r++)
    {
        for (int c = r + 1; c < matrix.length; c++)
        {
            if (matrix[r][c] != matrix[c][r])
                return false;
        }
    }
    return true;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 중첩 루프로 행렬 순회 |
| +1 | `matrix[r][c]`와 `matrix[c][r]` 비교 |
| +1 | 불일치 발견 시 즉시 `false` 반환 |
| +1 | 모든 쌍이 일치하면 `true` 반환 (algorithm point) |

**감점 사항:**
- 대각선 위만 검사하지 않고 전체 검사해도 OK (중복 검사일 뿐 오류 아님)
- `==` 대신 `equals` 사용 (int 비교이므로 `==`이 맞지만 감점 없음)

---

#### Part (b) — `getRowWithMaxSum` (2점)

**모범 답안:**
```java
public int getRowWithMaxSum()
{
    int maxSum = Integer.MIN_VALUE;
    int maxRow = 0;
    for (int r = 0; r < matrix.length; r++)
    {
        int sum = 0;
        for (int c = 0; c < matrix[r].length; c++)
        {
            sum += matrix[r][c];
        }
        if (sum > maxSum)
        {
            maxSum = sum;
            maxRow = r;
        }
    }
    return maxRow;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 각 행의 합을 올바르게 계산 |
| +1 | 최대 합의 행 인덱스를 추적하고 반환 (tie 시 첫 번째) |

**감점 사항:**
- `>=` 사용으로 tie 시 마지막 인덱스 반환: -1
- 합 계산 시 초기화 누락 (sum을 매 행 초기화 안 함): -1

---

## 점수 해석

| 총점 (34점 만점) | 예상 AP 점수 | 설명 |
|-----------------|-------------|------|
| 28–34 | **5** | 목표 달성. 실전에서도 5점 가능성 높음. |
| 21–27 | **4** | 기본기 탄탄하나 고난이도 문제에서 실수. 코드 tracing 연습 필요. |
| 14–20 | **3** | 핵심 개념은 이해하나 적용력 부족. Unit별 약점 집중 보완. |
| 0–13 | — | 추가 학습 필요. 기본 개념부터 재점검 권장. |
