# AP Computer Science A — Level Test 5

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
double x = 0.1 * 3;
System.out.println(x == 0.3);
```

(A) `true`
(B) `false`
(C) `0.3`
(D) 컴파일 에러

---

### 2. [U1 · 보통]

다음 코드의 출력은?

```java
int a = 7;
double b = (double) a / 2;
int c = (int) b;
System.out.println(b + " " + c);
```

(A) `3.5 3`
(B) `3.0 3`
(C) `3.5 4`
(D) `3.0 3.0`

---

### 3. [U1 · 어려움]
> **참고:** `long` 타입은 AP CSA 범위 밖이지만, 정수 오버플로와 타입 승격 이해를 위해 포함했습니다.

다음 코드의 출력은?

```java
int a = Integer.MAX_VALUE;
long b = a + 1;
System.out.println(b);
```

(A) `2147483648`
(B) 런타임 에러
(C) 컴파일 에러
(D) `-2147483648`

---

### 4. [U2 · 쉬움]

다음 코드의 출력은?

```java
String s = "Hello World";
String[] parts = s.split(" ");
System.out.println(parts[0].length());
```

(A) 5
(B) 6
(C) 11
(D) 2

---

### 5. [U2 · 보통]

다음 코드의 출력은?

```java
String s = "racecar";
boolean isPalin = true;
for (int i = 0; i < s.length() / 2; i++)
{
    if (!s.substring(i, i + 1).equals(s.substring(s.length() - 1 - i, s.length() - i)))
    {
        isPalin = false;
    }
}
System.out.println(isPalin);
```

(A) `true`
(B) `false`
(C) 컴파일 에러
(D) `StringIndexOutOfBoundsException`

---

### 6. [U2 · 어려움]

다음 코드의 출력은?

```java
String s = "abcdef";
String result = "";
for (int i = 0; i < s.length(); i += 2)
{
    result = s.substring(i, i + 1) + result;
}
System.out.println(result);
```

(A) `"ace"`
(B) `"bdf"`
(C) `"eca"`
(D) `"fdb"`

---

### 7. [U2 · 보통]

다음 코드의 출력은?

```java
String s = "Hello, World!";
int count = 0;
for (int i = 0; i < s.length(); i++)
{
    String ch = s.substring(i, i + 1);
    if (ch.compareTo("A") >= 0 && ch.compareTo("Z") <= 0)
    {
        count++;
    }
}
System.out.println(count);
```

(A) 2
(B) 3
(C) 10
(D) 0

---

### 8. [U2 · 어려움]

다음 코드의 출력은?

```java
int a = 48, b = 18;
while (b != 0)
{
    int temp = b;
    b = a % b;
    a = temp;
}
System.out.println(a);
```

(A) 2
(B) 6
(C) 12
(D) 18

---

### 9. [U2 · 어려움]

다음 코드의 출력은?

```java
String s = "aabbccdd";
String result = "";
for (int i = 0; i < s.length(); i++)
{
    String ch = s.substring(i, i + 1);
    if (result.indexOf(ch) == -1)
    {
        result += ch;
    }
}
System.out.println(result);
```

(A) `"aabbccdd"`
(B) `"abdc"`
(C) `"abcd"`
(D) `"dcba"`

---

### 10. [U3 · 보통]

다음 두 코드 조각 중 어떤 것이 항상 같은 결과를 내는가?

**Code I:**
```java
if (x > 0)
    return true;
else
    return false;
```

**Code II:**
```java
return x > 0;
```

(A) I만 올바름
(B) II만 올바름
(C) I과 II 모두 동일한 결과
(D) 입력에 따라 다름

---

### 11. [U3 · 어려움]

다음 코드의 출력은?

```java
boolean p = true, q = false, r = true;
boolean result = p || q && r;
System.out.println(result);
```

위 결과와 다음 중 동일한 표현은?

(A) `(p || q) && r`
(B) `p && q || r`
(C) `(p && q) || r`
(D) `p || (q && r)`

---

### 12. [U3 · 어려움]

다음 코드의 출력은?

```java
int x = 8;
boolean a = (x > 5) && (x < 10);
boolean b = (x % 2 == 0) || (x > 20);
boolean c = !a && b;
boolean d = a || !b;
System.out.println(c + " " + d);
```

(A) `"true true"`
(B) `"false true"`
(C) `"true false"`
(D) `"false false"`

---

### 13. [U4 · 쉬움]

다음 코드의 출력은?

```java
int[] arr = {4, 7, 2, 9, 1};
int max = arr[0];
for (int val : arr)
{
    if (val > max)
        max = val;
}
System.out.println(max);
```

(A) 4
(B) 9
(C) 1
(D) 23

---

### 14. [U4 · 보통]

다음 코드의 출력은?

```java
ArrayList<Integer> a = new ArrayList<Integer>();
a.add(10);
a.add(20);
a.add(30);
ArrayList<Integer> b = new ArrayList<Integer>();
b.add(20);
b.add(40);

ArrayList<Integer> common = new ArrayList<Integer>();
for (int val : a)
{
    if (b.contains(val))
        common.add(val);
}
System.out.println(common);
```

> **참고**: `ArrayList.contains`는 AP CSA 2025-26 Quick Reference에 없으므로 시험 답안 작성 시 사용 금지입니다. 본 문제는 trace 학습용이며, 실제 작성 시에는 `for` 루프 + `equals`로 직접 선형 탐색하세요.

(A) `[10, 20, 30, 40]`
(B) `[10, 30]`
(C) `[20]`
(D) `[]`

---

### 15. [U4 · 어려움]

다음 코드의 출력은?

```java
int[][] grid = {{1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}};
int sum = 0;
for (int i = 0; i < grid.length; i++)
{
    sum += grid[i][grid.length - 1 - i];
}
System.out.println(sum);
```

(A) 15
(B) 13
(C) 12
(D) 18

---

### 16. [U4 · 보통]

다음 코드에서 selection sort의 **비교 횟수**는?

```java
int[] arr = {5, 3, 1, 4, 2};
int comparisons = 0;
for (int i = 0; i < arr.length - 1; i++)
{
    int minIdx = i;
    for (int j = i + 1; j < arr.length; j++)
    {
        comparisons++;
        if (arr[j] < arr[minIdx])
            minIdx = j;
    }
    int temp = arr[i];
    arr[i] = arr[minIdx];
    arr[minIdx] = temp;
}
System.out.println(comparisons);
```

(A) 5
(B) 15
(C) 10
(D) 20

---

### 17. [U4 · 어려움]
> **참고:** `Integer` 캐싱(-128~127)은 JVM 구현 세부사항으로 AP 시험에 출제되지 않지만, `==` vs `equals` 심화 이해를 위해 포함했습니다.

다음 코드의 출력은?

```java
Integer a = 127;
Integer b = 127;
Integer c = 128;
Integer d = 128;
System.out.println((a == b) + " " + (c == d));
```

(A) `true true`
(B) `false false`
(C) `false true`
(D) `true false`

---

### 18. [U4 · 어려움]

다음 재귀 메서드에서 `power(2, 5)` 호출 시 `power` 메서드가 총 몇 번 호출되는가? (최초 호출 포함)

```java
public static int power(int base, int exp)
{
    if (exp == 0)
        return 1;
    return base * power(base, exp - 1);
}
```

(A) 5
(B) 6
(C) 4
(D) 10

---

### 19. [U4 · 보통]

다음 코드의 출력은?

```java
int[] arr = {3, 1, 4, 1, 5};
int[] shifted = new int[arr.length];
for (int i = 0; i < arr.length; i++)
{
    shifted[(i + 2) % arr.length] = arr[i];
}
System.out.println(Arrays.toString(shifted));
```

(A) `[5, 1, 3, 1, 4]`
(B) `[4, 1, 5, 3, 1]`
(C) `[1, 5, 3, 1, 4]`
(D) `[1, 4, 3, 1, 5]`

---

### 20. [U4 · 어려움]

다음 코드의 출력은?

```java
int[] arr = {3, 1, 4, 1, 5, 9};
int count = 0;
for (int i = 0; i < arr.length - 1; i++)
{
    for (int j = i + 1; j < arr.length; j++)
    {
        if (arr[i] > arr[j])
            count++;
    }
}
System.out.println(count);
```

(A) 10
(B) 5
(C) 7
(D) 3

---

### 21. [U4 · 보통]

다음 코드의 출력은?

```java
int[][] grid = {{2, 4, 6},
                {1, 3, 5},
                {7, 8, 9}};
int borderSum = 0;
for (int c = 0; c < grid[0].length; c++)
{
    borderSum += grid[0][c];
    borderSum += grid[grid.length - 1][c];
}
for (int r = 1; r < grid.length - 1; r++)
{
    borderSum += grid[r][0];
    borderSum += grid[r][grid[0].length - 1];
}
System.out.println(borderSum);
```

(A) 48
(B) 45
(C) 39
(D) 42

---

# Section II: Free Response (2 Questions | 30 Minutes)

**지시사항:** Write your solutions in Java. You may assume all necessary imports.

---

## Question 1: SequenceAnalyzer (7 Points)

다음 `SequenceAnalyzer` 클래스는 정수 배열을 분석하는 메서드를 제공합니다.

```java
public class SequenceAnalyzer
{
    /** Returns the length of the longest strictly increasing
     *  consecutive subsequence in arr.
     *
     *  Examples:
     *    longestIncreasingRun({3, 5, 7, 2, 4, 6, 8, 1}) returns 4
     *      (the run 2, 4, 6, 8)
     *    longestIncreasingRun({5, 4, 3, 2, 1}) returns 1
     *    longestIncreasingRun({1, 2, 3, 4, 5}) returns 5
     *    longestIncreasingRun({7}) returns 1
     *
     *  Precondition: arr is not null and has length >= 1.
     */
    public static int longestIncreasingRun(int[] arr)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a compressed string representation of arr where
     *  consecutive duplicate values are shown as "valuexcount".
     *  Each group is separated by a single space.
     *
     *  Examples:
     *    compressSequence({1, 1, 1, 2, 2, 3}) returns "1x3 2x2 3x1"
     *    compressSequence({5}) returns "5x1"
     *    compressSequence({4, 4, 4, 4}) returns "4x4"
     *    compressSequence({1, 2, 3}) returns "1x1 2x1 3x1"
     *
     *  Precondition: arr is not null and has length >= 1.
     */
    public static String compressSequence(int[] arr)
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `longestIncreasingRun` method.

### Part (b)

Complete the `compressSequence` method.

---

## Question 2: BankAccount (6 Points)

은행 계좌를 관리하는 `BankAccount` 클래스를 작성하세요. 다음 정보와 기능을 가집니다.

| 항목 | 설명 |
|------|------|
| `owner` | 계좌 소유자 이름 (`String`). 생성 시 설정, 변경 불가. |
| `balance` | 잔액 (`double`). 생성 시 0.0. |
| `transactionCount` | 총 거래 횟수 (`int`). 생성 시 0. |
| `BankAccount(String owner)` | 생성자. 소유자 이름 설정, 초기 상태 지정. |
| `getBalance()` | 현재 잔액을 반환. |
| `deposit(double amount)` | 입금. `amount`가 0 이하이면 아무 동작 없이 `false` 반환. 성공 시 잔액 증가, 거래 횟수 증가, `true` 반환. |
| `withdraw(double amount)` | 출금. `amount`가 0 이하이거나 잔액보다 크면 아무 동작 없이 `false` 반환. 성공 시 잔액 감소, 거래 횟수 증가, `true` 반환. |
| `getStatement()` | `"[owner]: $[balance] ([transactionCount] transactions)"` 형식 반환. 잔액은 소수점 둘째 자리까지. 예: `"Alice: $150.00 (3 transactions)"` |

`BankAccount` 클래스를 완성하세요. 위의 모든 인스턴스 변수, 생성자, 메서드를 포함해야 합니다.

---
---

# 정답 및 채점

## Section I 정답표

| # | 정답 | Unit | 난이도 | 해설 |
|---|------|------|--------|------|
| 1 | B | U1 | 쉬움 | 부동소수점 오차. `0.1 * 3`은 정확히 0.3이 아님. `==` 비교는 `false`. |
| 2 | A | U1 | 보통 | `(double) 7 / 2` = `3.5`. `(int) 3.5` = `3`. 출력: `3.5 3`. |
| 3 | D | U1 | 어려움 | `a + 1`은 int 연산으로 먼저 수행. `Integer.MAX_VALUE + 1` → 오버플로 → `-2147483648`. 이 값이 long에 대입. |
| 4 | A | U2 | 쉬움 | `"Hello World".split(" ")` → `{"Hello", "World"}`. `parts[0].length()` = 5. |
| 5 | A | U2 | 보통 | `"racecar"`는 회문. 각 위치 비교가 모두 일치. `true`. |
| 6 | C | U2 | 어려움 | i=0: `"a"+""` = `"a"`. i=2: `"c"+"a"` = `"ca"`. i=4: `"e"+"ca"` = `"eca"`. |
| 7 | A | U2 | 보통 | `compareTo("A") >= 0 && compareTo("Z") <= 0`은 대문자 A-Z 범위 확인. `"Hello, World!"`에서 대문자는 "H"와 "W" 2개. count = 2. |
| 8 | B | U2 | 어려움 | 유클리드 호제법. 48,18 → 18,12 → 12,6 → 6,0. GCD = 6. |
| 9 | C | U2 | 어려움 | 중복 제거. `indexOf`가 -1인 문자만 추가. `"abcd"`. |
| 10 | C | U3 | 보통 | 두 코드 모두 `x > 0`이면 `true`, 아니면 `false`를 반환. 완전히 동일. |
| 11 | D | U3 | 어려움 | `&&`가 `||`보다 우선순위 높음. `p || (q && r)` = `true || false` = `true`. (D)가 동일한 표현. |
| 12 | B | U3 | 어려움 | a = (8>5 && 8<10) = true. b = (0==0 \|\| 8>20) = true. c = !true && true = false. d = true \|\| !true = true. 출력: `"false true"`. |
| 13 | B | U4 | 쉬움 | 배열 최댓값. max = 4 → 7 → 9. 출력: 9. |
| 14 | C | U4 | 보통 | a와 b의 공통 요소. 20만 공통. `[20]`. |
| 15 | A | U4 | 어려움 | 반대각선(anti-diagonal): grid[0][2]=3, grid[1][1]=5, grid[2][0]=7. 합 = 15. |
| 16 | C | U4 | 보통 | n=5: 비교 횟수 = 4+3+2+1 = 10. |
| 17 | D | U4 | 어려움 | Java는 -128~127 Integer를 캐시. 127은 캐시 범위 → `==` true. 128은 캐시 밖 → 새 객체 → `==` false. |
| 18 | B | U4 | 어려움 | `power(2,5)` → `power(2,4)` → `power(2,3)` → `power(2,2)` → `power(2,1)` → `power(2,0)`. 총 6회. |
| 19 | C | U4 | 보통 | i=0→idx2, i=1→idx3, i=2→idx4, i=3→idx0, i=4→idx1. shifted = {1, 5, 3, 1, 4}. |
| 20 | D | U4 | 어려움 | 역전쌍(inversions) 세기. i=0(3): 3>1✓, 3>1✓ → 2. i=2(4): 4>1✓ → 1. 나머지 0. 총 count = 3. |
| 21 | D | U4 | 보통 | 테두리: 첫행 2+4+6=12, 마지막행 7+8+9=24, 중간행 양쪽 1+5=6. 합 = 42. |

### Section I 최종 정답

| # | 정답 |
|---|------|
| 1 | B |
| 2 | A |
| 3 | D |
| 4 | A |
| 5 | A |
| 6 | C |
| 7 | A |
| 8 | B |
| 9 | C |
| 10 | C |
| 11 | D |
| 12 | B |
| 13 | B |
| 14 | C |
| 15 | A |
| 16 | C |
| 17 | D |
| 18 | B |
| 19 | C |
| 20 | D |
| 21 | D |

---

## Section II 채점기준

### Q1: SequenceAnalyzer (7점)

#### Part (a) — `longestIncreasingRun` (4점)

**모범 답안:**
```java
public static int longestIncreasingRun(int[] arr)
{
    int maxLen = 1;
    int currLen = 1;
    for (int i = 1; i < arr.length; i++)
    {
        if (arr[i] > arr[i - 1])
        {
            currLen++;
        }
        else
        {
            currLen = 1;
        }
        if (currLen > maxLen)
        {
            maxLen = currLen;
        }
    }
    return maxLen;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 배열을 순회하며 인접 요소를 비교하는 루프 |
| +1 | 증가할 때 현재 길이 증가, 아닐 때 리셋 |
| +1 | 최대 길이를 올바르게 추적 |
| +1 | 올바른 값 반환 (algorithm point) |

**감점 사항:**
- `>=` 사용 (strictly increasing이 아님): -1
- 길이 1인 배열에서 오류: -1

---

#### Part (b) — `compressSequence` (3점)

**모범 답안:**
```java
public static String compressSequence(int[] arr)
{
    String result = "";
    int count = 1;
    for (int i = 1; i < arr.length; i++)
    {
        if (arr[i] == arr[i - 1])
        {
            count++;
        }
        else
        {
            if (result.length() > 0)
                result += " ";
            result += arr[i - 1] + "x" + count;
            count = 1;
        }
    }
    if (result.length() > 0)
        result += " ";
    result += arr[arr.length - 1] + "x" + count;
    return result;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 연속 동일 요소를 카운트하는 루프 |
| +1 | 그룹이 끝날 때 `"valuexcount"` 형식으로 추가 |
| +1 | 마지막 그룹 처리 + 공백 구분 + 올바른 반환 |

**감점 사항:**
- 마지막 그룹 누락: -1
- 구분자(공백) 오류: -1

---

### Q2: BankAccount (6점)

**모범 답안:**
```java
public class BankAccount
{
    private String owner;
    private double balance;
    private int transactionCount;

    public BankAccount(String owner)
    {
        this.owner = owner;
        this.balance = 0.0;
        this.transactionCount = 0;
    }

    public double getBalance()
    {
        return balance;
    }

    public boolean deposit(double amount)
    {
        if (amount <= 0)
            return false;
        balance += amount;
        transactionCount++;
        return true;
    }

    public boolean withdraw(double amount)
    {
        if (amount <= 0 || amount > balance)
            return false;
        balance -= amount;
        transactionCount++;
        return true;
    }

    public String getStatement()
    {
        // String.format은 Quick Reference 범위 밖이므로 정수/소수 분리 후 수동 조립
        int dollars = (int) balance;
        int cents = (int) ((balance - dollars) * 100 + 0.5);  // 소수 둘째 자리 반올림
        String centStr = "" + cents;
        if (cents < 10)
        {
            centStr = "0" + cents;
        }
        return owner + ": $" + dollars + "." + centStr
               + " (" + transactionCount + " transactions)";
    }
}
```

| 점수 | 기준 |
|------|------|
| +1 | `private` 인스턴스 변수 3개 (올바른 타입) |
| +1 | 생성자: 파라미터 설정 + 초기값 |
| +1 | `deposit`: 유효성 검사 + 잔액 증가 + 거래 횟수 증가 |
| +1 | `withdraw`: 유효성 검사 (amount ≤ 0 또는 잔액 부족) + 잔액 감소 + 거래 횟수 증가 |
| +1 | `getBalance()` 올바르게 반환 |
| +1 | `getStatement()` 형식에 맞는 문자열 반환 |

**감점 사항:**
- `private` 누락: -1
- `withdraw`에서 잔액 부족 체크 누락: -1
- `getStatement` 형식 불일치: -1
- boolean 반환값 누락/오류: -1

---

## 점수 해석

| 총점 (34점 만점) | 예상 AP 점수 | 설명 |
|-----------------|-------------|------|
| 28–34 | **5** | 목표 달성. 실전에서도 5점 가능성 높음. |
| 21–27 | **4** | 기본기 탄탄하나 고난이도 문제에서 실수. 코드 tracing 연습 필요. |
| 14–20 | **3** | 핵심 개념은 이해하나 적용력 부족. Unit별 약점 집중 보완. |
| 0–13 | — | 추가 학습 필요. 기본 개념부터 재점검 권장. |
