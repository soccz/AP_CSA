# AP CSA 5점 레벨 테스트 3 — 최종 관문

> **목적:** 3세트 중 가장 어려운 최종 테스트. 이 세트를 통과하면 5점 확정.
> **제한 시간:** Section I (30분) + Section II (30분) = 총 60분
> **배점:** MCQ 21문제 × 1점 = 21점 / FRQ Q1 7점 + Q2 6점 = 13점 / **총 34점**

---

# Section I: Multiple Choice (21문제 / 30분)

**Unit 분포:** U1(3) · U2(6) · U3(3) · U4(9)
**난이도:** 쉬움 2 · 보통 7 · 어려움 12

---

### Q1 (U1 · 쉬움)

다음 코드의 출력은?

```java
int a = 17;
int b = 5;
double result = (double)(a / b);
System.out.println(result);
```

(A) 3.4
(B) 3.0
(C) 3
(D) 컴파일 에러

---

### Q2 (U1 · 어려움)

다음 코드의 출력은?

```java
int a = 17;
int b = 5;
double r1 = (double) a / b;
double r2 = (double)(a / b);
double r3 = a / (double) b;
System.out.println(r1 == r3);
System.out.println(r1 == r2);
```

(A) true true
(B) true false
(C) false true
(D) false false

---

### Q3 (U1 · 보통)

다음 중 컴파일 에러가 발생하는 코드는?

```java
// I
int x = 5;
double y = x;

// II
double a = 3.7;
int b = a;

// III
int c = (int) 4.9;

// IV
String s = "5";
int d = Integer.parseInt(s);
```

(A) II만
(B) II, IV
(C) I, II
(D) II, III

---

### Q4 (U2 · 어려움)

다음 코드의 출력은?

```java
String s1 = "Apple";
String s2 = "apple";
int diff = s1.compareTo(s2);
System.out.println(diff < 0);
System.out.println(diff);
```

`'A'`의 ASCII 값은 65, `'a'`는 97이다.

(A) true -32
(B) false 32
(C) true -1
(D) false 1

---

### Q5 (U2 · 보통)

다음 코드의 출력은?

```java
String str = "ABCDEFGH";
String result = str.substring(2, 5) + str.substring(5);
System.out.println(result);
```

(A) "BCDEFGH"
(B) "CDEEFGH"
(C) "CDEFGH"
(D) "BCDEEFGH"

---

### Q6 (U2 · 어려움)

```java
public class Widget {
    private int count;

    public Widget() {
        count = 0;
    }

    public Widget(int c) {
        count = c;
    }
}
```

다음 코드가 있다. 만약 두 생성자를 모두 삭제하고 아래처럼 바꾸면 어떻게 되는가?

```java
public class Widget {
    private int count;

    public Widget(int c) {
        count = c;
    }
}

// 호출 코드
Widget w = new Widget();
```

(A) `count`가 0으로 초기화된다
(B) `count`가 초기화되지 않아 런타임 에러
(C) 컴파일 에러: 매개변수 없는 생성자가 존재하지 않음
(D) 기본 생성자가 자동 생성되어 정상 실행

---

### Q7 (U2 · 어려움)
> **참고:** `static` 메서드 제한은 AP CSA 범위 밖이지만, 메서드 호출 규칙 이해를 위해 포함했습니다.

```java
public class Tracker {
    private static int total = 0;
    private int id;

    public Tracker() {
        total++;
        id = total;
    }

    public static void printTotal() {
        System.out.println("Total: " + total);
        System.out.println("My ID: " + id);  // ← 이 줄
    }
}
```

위 코드에서 문제가 되는 부분은?

(A) `total`을 `static`으로 선언한 것
(B) `static` 메서드 `printTotal()`에서 인스턴스 변수 `id`에 접근
(C) 생성자에서 `static` 변수를 수정한 것
(D) 문제 없이 정상 컴파일됨

---

### Q8 (U2 · 보통)

```java
public class Point {
    private int x;
    private int y;

    public Point(int x, int y) {
        x = x;
        y = y;
    }

    public String toString() {
        return "(" + x + ", " + y + ")";
    }
}

Point p = new Point(3, 7);
System.out.println(p);
```

출력은?

(A) (3, 7)
(B) (null, null)
(C) (0, 0)
(D) 컴파일 에러

---

### Q9 (U2 · 어려움)
> **참고:** null 언박싱(unboxing)은 AP CSA 범위 밖이지만, wrapper 클래스 이해를 위해 포함했습니다.

```java
Integer a = null;
int b = a;
System.out.println(b);
```

위 코드의 실행 결과는?

(A) 0
(B) null
(C) 컴파일 에러
(D) NullPointerException

---

### Q10 (U3 · 어려움)

다음 코드의 출력은?

```java
boolean p = true;
boolean q = false;
boolean r = true;

if (!(p && q) || r) {
    if (!p || q) {
        System.out.println("A");
    } else {
        System.out.println("B");
    }
} else {
    System.out.println("C");
}
```

(A) A
(B) B
(C) C
(D) 아무것도 출력되지 않음

---

### Q11 (U3 · 보통)

다음 두 조건식이 동치인 것은?

```
원본: !(a > 5 && b <= 10)
```

(A) `a > 5 || b <= 10`
(B) `!(a > 5) && !(b <= 10)`
(C) `a <= 5 && b > 10`
(D) `a <= 5 || b > 10`

---

### Q12 (U3 · 어려움)

다음 `for` 루프와 동치인 `while` 루프는?

```java
for (int i = 10; i >= 1; i -= 3) {
    System.out.print(i + " ");
}
```

(A)
```java
int i = 10;
while (i >= 1) {
    System.out.print(i + " ");
    i -= 3;
}
```

(B)
```java
int i = 10;
while (i > 1) {
    System.out.print(i + " ");
    i -= 3;
}
```

(C)
```java
int i = 10;
while (i >= 1) {
    i -= 3;
    System.out.print(i + " ");
}
```

(D)
```java
int i = 10;
while (i >= 0) {
    System.out.print(i + " ");
    i = i - 3;
}
```

---

### Q13 (U4 · 쉬움)

```java
int count = 0;
for (int i = 0; i < 5; i++) {
    for (int j = 0; j < 3; j++) {
        count++;
    }
}
System.out.println(count);
```

(A) 8
(B) 5
(C) 12
(D) 15

---

### Q14 (U4 · 어려움)

```java
int count = 0;
for (int i = 0; i < 4; i++) {
    for (int j = 0; j <= i; j++) {
        for (int k = j; k < 3; k++) {
            count++;
        }
    }
}
System.out.println(count);
```

이 코드의 출력은?

(A) 12
(B) 16
(C) 18
(D) 20

---

### Q15 (U4 · 어려움)

```java
public static int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}
```

`fib(6)`을 호출할 때, `fib` 메서드가 총 몇 번 호출되는가? (최초 `fib(6)` 호출 포함)

(A) 13
(B) 15
(C) 21
(D) 25

---

### Q16 (U4 · 어려움)

다음 배열에 Selection Sort를 오름차순으로 적용한다. **3 pass(패스) 완료 후** 배열 상태는?

초기: `{8, 3, 6, 1, 5, 2, 7, 4}`

(A) `{1, 2, 3, 8, 6, 5, 7, 4}`
(B) `{1, 2, 3, 6, 5, 8, 7, 4}`
(C) `{1, 2, 3, 8, 5, 6, 7, 4}`
(D) `{1, 3, 6, 8, 5, 2, 7, 4}`

---

### Q17 (U4 · 어려움)

정렬된 배열 `{2, 5, 8, 12, 16, 23, 38, 56, 72, 91}`에서 Binary Search로 `target = 20`을 찾는다. 표준 알고리즘(low=0, high=length-1, mid=(low+high)/2)을 사용할 때, 탐색 종료 시 `low`와 `high`의 값은?

(A) low = 4, high = 5
(B) low = 5, high = 5
(C) low = 5, high = 4
(D) low = 6, high = 5

---

### Q18 (U4 · 보통)

```java
ArrayList<String> list = new ArrayList<String>();
list.add("A");      // [A]
list.add("B");      // [A, B]
list.add("C");      // [A, B, C]
list.add(1, "D");   // ?
list.set(2, "E");   // ?
list.remove(0);     // ?
System.out.println(list);
```

(A) [A, D, E]
(B) [D, B, C]
(C) [D, E, C]
(D) [D, E]

---

### Q19 (U4 · 어려움)

```java
int[][] grid = {
    {1, 2, 3, 4},
    {5, 6, 7, 8},
    {9, 10, 11, 12},
    {13, 14, 15, 16}
};

int sum = 0;
for (int i = 0; i < grid.length; i++) {
    sum += grid[i][i];
    sum += grid[i][grid.length - 1 - i];
}
System.out.println(sum);
```

(A) 68
(B) 34
(C) 52
(D) 64

---

### Q20 (U4 · 보통)

```java
int[][] matrix = new int[3][4];
int val = 1;
for (int c = 0; c < matrix[0].length; c++) {
    for (int r = 0; r < matrix.length; r++) {
        matrix[r][c] = val;
        val++;
    }
}
System.out.println(matrix[1][2]);
```

(A) 7
(B) 8
(C) 6
(D) 5

---

### Q21 (U4 · 보통)

다음 코드에서 `mystery` 메서드의 반환값으로 올바른 것은?

```java
public static int mystery(int[] arr) {
    int result = arr[0];
    for (int i = 1; i < arr.length; i++) {
        if (arr[i] % 2 == 0 && arr[i] > result) {
            result = arr[i];
        }
    }
    return result;
}

// 호출: mystery(new int[]{3, 8, 1, 12, 5, 6, 9})
```

(A) 12
(B) 9
(C) 8
(D) 6

---

# Section I 정답 및 해설

<details>
<summary>정답 보기 (클릭)</summary>

### Q1: **(B) 3.0**
`a / b`가 먼저 정수 나눗셈으로 `3`이 되고, 그 후 `(double)`로 캐스팅하여 `3.0`.

### Q2: **(B) true false**
- `r1 = (double)17 / 5 = 3.4`
- `r2 = (double)(17/5) = (double)3 = 3.0`
- `r3 = 17 / (double)5 = 3.4`
- `r1 == r3` → true, `r1 == r2` → false

### Q3: **(A) II만**
`double a = 3.7; int b = a;`는 narrowing conversion으로 명시적 캐스트 없이 불가 → 컴파일 에러. I은 widening(OK), III은 명시적 캐스트(OK), IV는 `parseInt` 메서드(OK).

### Q4: **(A) true -32**
`compareTo`는 첫 번째 다른 문자의 차이를 반환. `'A' - 'a' = 65 - 97 = -32`. 음수이므로 `diff < 0`은 `true`.

### Q5: **(C) "CDEFGH"**
- `substring(2, 5)` → "CDE"
- `substring(5)` → "FGH"
- 결합: "CDEFGH"

### Q6: **(C) 컴파일 에러: 매개변수 없는 생성자가 존재하지 않음**
매개변수가 있는 생성자를 정의하면 Java는 더 이상 기본 생성자를 자동 생성하지 않는다. `new Widget()`은 컴파일 에러.

### Q7: **(B) static 메서드에서 인스턴스 변수 id에 접근**
`static` 메서드는 특정 인스턴스에 속하지 않으므로 인스턴스 변수 `id`에 직접 접근할 수 없다. 컴파일 에러 발생.

### Q8: **(C) (0, 0)**
`x = x`와 `y = y`는 매개변수 자기 자신에 대입하는 것이므로 인스턴스 변수 `this.x`, `this.y`는 `int`의 기본값인 `0`으로 남는다.

### Q9: **(D) NullPointerException**
`Integer a = null`을 `int b = a`로 unboxing할 때, `null`을 unbox하려고 하면 `NullPointerException` 발생. 컴파일 에러는 아님(autoboxing 문법은 유효).

### Q10: **(B) B**
- `p && q` = `true && false` = `false`
- `!(false)` = `true`
- `true || r` = `true` → 외부 if 진입
- `!p` = `false`, `!p || q` = `false || false` = `false` → else 분기
- 출력: "B"

### Q11: **(D) a <= 5 || b > 10**
De Morgan의 법칙: `!(A && B)` = `!A || !B`
- `!(a > 5)` = `a <= 5`
- `!(b <= 10)` = `b > 10`
- 결과: `a <= 5 || b > 10`

### Q12: **(A)**
`for` 루프와 동치인 `while` 변환: 초기화 → 조건 → 본문 → 증감 순서 유지. (A)가 정확히 이 구조를 따른다.
- for 출력: `10 7 4 1`
- (A) while 출력: `10 7 4 1` ✓
- (B) `i > 1`이므로 `1`을 출력하지 않음: `10 7 4` ✗
- (C) 증감이 출력 전에 와서 순서 틀림: `7 4 1 -2` ✗
- (D) `i >= 0`이므로 -2까지 출력: `10 7 4 1 -2` ✗

### Q13: **(D) 15**
외부 5회 × 내부 3회 = 15.

### Q14: **(D) 20**

| i | j 범위 (0~i) | 각 j에서 k 실행 횟수 (k=j..2) | 소계 |
|---|-------------|-------------------------------|------|
| 0 | j=0 | 3 | 3 |
| 1 | j=0, j=1 | 3 + 2 | 5 |
| 2 | j=0, j=1, j=2 | 3 + 2 + 1 | 6 |
| 3 | j=0, j=1, j=2, j=3 | 3 + 2 + 1 + 0 | 6 |

총합: 3 + 5 + 6 + 6 = **20**

### Q15: **(D) 25**

호출 트리를 그리면:
- `fib(6)` → `fib(5)` + `fib(4)`
- `fib(5)` → `fib(4)` + `fib(3)`
- ...

각 `fib(n)`의 총 호출 횟수를 `T(n)`이라 하면:
- T(0) = 1, T(1) = 1
- T(n) = T(n-1) + T(n-2) + 1

T(2) = 1+1+1 = 3, T(3) = 3+1+1 = 5, T(4) = 5+3+1 = 9, T(5) = 9+5+1 = 15, T(6) = 15+9+1 = **25**

### Q16: **(C) {1, 2, 3, 8, 5, 6, 7, 4}**

Selection Sort (오름차순): 각 패스에서 남은 부분의 최솟값을 찾아 앞으로 swap.

- 초기: `{8, 3, 6, 1, 5, 2, 7, 4}`
- Pass 1: index 0~7에서 최소 = 1(index 3) → swap(0,3) → `{1, 3, 6, 8, 5, 2, 7, 4}`
- Pass 2: index 1~7에서 최소 = 2(index 5) → swap(1,5) → `{1, 2, 6, 8, 5, 3, 7, 4}`
- Pass 3: index 2~7에서 최소 = 3(index 5) → swap(2,5) → `{1, 2, 3, 8, 5, 6, 7, 4}`

### Q17: **(C) low = 5, high = 4**

배열: `{2, 5, 8, 12, 16, 23, 38, 56, 72, 91}` (인덱스 0~9), target = 20

| 단계 | low | high | mid | arr[mid] | 비교 |
|------|-----|------|-----|----------|------|
| 1 | 0 | 9 | 4 | 16 | 20>16, low=5 |
| 2 | 5 | 9 | 7 | 56 | 20<56, high=6 |
| 3 | 5 | 6 | 5 | 23 | 20<23, high=4 |

low(5) > high(4) → 종료. **low = 5, high = 4**

### Q18: **(C) [D, E, C]**
- `add("A")` → [A]
- `add("B")` → [A, B]
- `add("C")` → [A, B, C]
- `add(1, "D")` → [A, D, B, C]
- `set(2, "E")` → [A, D, E, C]
- `remove(0)` → [D, E, C]

### Q19: **(A) 68**
주대각선: grid[0][0]=1, grid[1][1]=6, grid[2][2]=11, grid[3][3]=16 → 합 34
반대각선: grid[0][3]=4, grid[1][2]=7, grid[2][1]=10, grid[3][0]=13 → 합 34
총합: 34 + 34 = **68**

주의: 4×4에서 주대각선과 반대각선이 교차하는 점이 없으므로(짝수 크기) 중복 없음.

### Q20: **(B) 8**
Column-major 순서로 채움:

|     | c=0 | c=1 | c=2 | c=3 |
|-----|-----|-----|-----|-----|
| r=0 | 1   | 4   | 7   | 10  |
| r=1 | 2   | 5   | 8   | 11  |
| r=2 | 3   | 6   | 9   | 12  |

`matrix[1][2]` = **8**

### Q21: **(A) 12**
`result`는 `arr[0]=3`으로 시작. 짝수이면서 `result`보다 큰 값을 찾는다:
- 8: 짝수, 8>3 → result=8
- 1: 홀수
- 12: 짝수, 12>8 → result=12
- 5: 홀수
- 6: 짝수, 6>12 아님
- 9: 홀수

최종 result = 12. 단, `arr[0]=3`은 홀수이지만 초기값으로 설정된다는 점에 주의. 짝수 조건과 무관하게 초기값은 `arr[0]`.

---

</details>

---

# Section II: Free Response (2문제 / 30분)

---

## FRQ Q1: TextAnalyzer (7 points)

문자열을 분석하여 특정 패턴을 처리하는 클래스를 작성한다.

```java
public class TextAnalyzer {

    /**
     * Part (a)
     *
     * 문자열 str에서 연속으로 같은 문자가 k번 이상 반복되는 구간의 개수를 반환한다.
     * 예를 들어, str = "aabbbaacccc"이고 k = 3이면,
     * 연속 반복 구간은: "aa"(2번), "bbb"(3번), "aa"(2번), "cccc"(4번)
     * 이 중 k=3 이상인 것은 "bbb"와 "cccc" → 2를 반환.
     *
     * str = "aabbb"이고 k = 2이면,
     * "aa"(2번), "bbb"(3번) → 둘 다 2 이상 → 2를 반환.
     *
     * str이 빈 문자열이면 0을 반환한다.
     *
     * Precondition: str != null, k >= 1
     */
    public static int countLongRuns(String str, int k) {
        /* Part (a): 여기에 구현 */
    }

    /**
     * Part (b)
     *
     * 문자열 text에서 startTag와 endTag 사이에 있는 내용을 모두 추출하여
     * 하나의 문자열로 이어 붙여 반환한다. 각 추출 내용 사이에 구분자 sep를 넣는다.
     *
     * 예: text = "Hello [world] and [Java]!", startTag = "[", endTag = "]", sep = "-"
     *     반환: "world-Java"
     *
     * 예: text = "no tags here", startTag = "[", endTag = "]", sep = ","
     *     반환: "" (빈 문자열)
     *
     * 예: text = "<a>one</a>between<a>two</a>", startTag = "<a>", endTag = "</a>", sep = "+"
     *     반환: "one+two"
     *
     * 태그가 중첩되지 않는다고 가정한다.
     * startTag 뒤에 endTag가 반드시 존재한다고 가정한다.
     *
     * Precondition: text != null, startTag.length() > 0, endTag.length() > 0
     */
    public static String extractBetween(String text, String startTag, String endTag, String sep) {
        /* Part (b): 여기에 구현 */
    }
}
```

---

### Q1 채점 기준 (Scoring Guidelines)

#### Part (a): `countLongRuns` — 4 points

| 포인트 | 기준 | 설명 |
|--------|------|------|
| +1 | 연속 같은 문자 구간 식별 | 현재 문자와 다음/이전 문자 비교하여 run 경계 판단 |
| +1 | 각 run의 길이 계산 | run 길이를 정확히 세는 로직 (카운터 사용) |
| +1 | k와 비교하여 카운트 | run 길이 ≥ k일 때만 결과 카운트 증가 |
| +1 | 경계 조건 처리 | 빈 문자열 처리, 마지막 run 처리 누락 없음 |

**모범 답안:**

<details>
<summary>Part (a) 모범 답안 보기</summary>

```java
public static int countLongRuns(String str, int k) {
    if (str.length() == 0) return 0;

    int count = 0;
    int runLength = 1;

    for (int i = 1; i < str.length(); i++) {
        // charAt 대신 substring(i, i+1) 사용 (Quick Reference 준수)
        if (str.substring(i, i + 1).equals(str.substring(i - 1, i))) {
            runLength++;
        } else {
            if (runLength >= k) {
                count++;
            }
            runLength = 1;
        }
    }
    // 마지막 run 체크
    if (runLength >= k) {
        count++;
    }

    return count;
}
```

</details>

#### Part (b): `extractBetween` — 3 points

| 포인트 | 기준 | 설명 |
|--------|------|------|
| +1 | indexOf로 startTag/endTag 위치 탐색 | `indexOf`를 사용하여 태그 위치를 올바르게 찾음 |
| +1 | substring으로 내용 추출 | startTag 끝~endTag 시작 사이의 부분 문자열 추출 |
| +1 | 반복 처리 + 구분자 | 모든 태그 쌍을 순회하며 sep를 정확히 삽입 (첫 항목 앞에는 sep 없음) |

**모범 답안:**

<details>
<summary>Part (b) 모범 답안 보기</summary>

```java
public static String extractBetween(String text, String startTag, String endTag, String sep) {
    String result = "";
    int pos = 0;

    while (text.indexOf(startTag, pos) != -1) {
        int start = text.indexOf(startTag, pos) + startTag.length();
        int end = text.indexOf(endTag, start);
        String content = text.substring(start, end);

        if (result.length() > 0) {
            result += sep;
        }
        result += content;

        pos = end + endTag.length();
    }

    return result;
}
```

</details>

#### Q1 무시할 오류 (Errors to Ignore)
- 세미콜론 누락
- 중괄호 위치/스타일
- `str.charAt(i)` 대신 의미가 명확한 유사 표현
- 지역 변수 선언 시 타입 오류 (의도가 명확한 경우)
- `length()` 대신 `length` 사용 (String에서)

---

## FRQ Q2: GridCollector (6 points)

2D 정수 배열에서 특정 조건을 만족하는 원소를 ArrayList에 수집하는 클래스를 작성한다.

```java
import java.util.ArrayList;

public class GridCollector {

    /**
     * 2D 배열 grid에서 "peak" 원소를 column-major 순서로 ArrayList에 담아 반환한다.
     *
     * "peak" 원소란: 상하좌우 인접한 모든 원소보다 strictly 큰 원소.
     * 경계에 있는 원소는 존재하는 이웃만 비교한다.
     * (예: 모서리 원소는 이웃이 2개, 가장자리 원소는 3개, 내부 원소는 4개)
     *
     * column-major 순서: 열(column)을 0부터 순서대로, 각 열 안에서는 행(row)을 0부터 순서대로.
     *
     * 예:
     * grid = {{5, 2, 8},
     *          {1, 9, 3},
     *          {4, 6, 7}}
     *
     * - grid[0][0]=5: 이웃 2,1 → 5>2, 5>1 → peak ✓
     * - grid[1][0]=1: 이웃 5,4 → 1<5 → peak ✗
     * - grid[2][0]=4: 이웃 1,6 → 4>1 but 4<6 → peak ✗
     * - grid[0][1]=2: 이웃 5,9,8 → 2<5 → peak ✗
     * - grid[1][1]=9: 이웃 2,1,6,3 → 9>all → peak ✓
     * - grid[2][1]=6: 이웃 9,4,7 → 6<9 → peak ✗
     * - grid[0][2]=8: 이웃 2,3 → 8>2, 8>3 → peak ✓
     * - grid[1][2]=3: 이웃 8,9,7 → 3<8 → peak ✗
     * - grid[2][2]=7: 이웃 6,3 → 7>6, 7>3 → peak ✓
     *
     * column-major 순서로 반환: [5, 9, 8, 7]
     *
     * Precondition: grid는 null이 아니고, grid.length >= 1, grid[0].length >= 1
     *               모든 행의 길이가 같다.
     */
    public static ArrayList<Integer> findPeaks(int[][] grid) {
        /* 여기에 구현 */
    }
}
```

---

### Q2 채점 기준 (Scoring Guidelines)

| 포인트 | 기준 | 설명 |
|--------|------|------|
| +1 | Column-major 순회 | 외부 루프가 열, 내부 루프가 행 (c → r 순서) |
| +1 | 이웃 비교 로직 | 상하좌우 최대 4방향 이웃과 비교 |
| +1 | 경계 조건 처리 | `r-1 >= 0`, `r+1 < rows`, `c-1 >= 0`, `c+1 < cols` 등 범위 체크 |
| +1 | strictly greater 판정 | 모든 존재하는 이웃보다 strictly 클 때만 peak |
| +1 | ArrayList에 올바르게 추가 | `ArrayList<Integer>` 생성 및 `add()` 사용 |
| +1 | 올바른 반환 | 올바른 ArrayList 반환, 빈 경우 빈 리스트 반환 |

**모범 답안:**

<details>
<summary>Q2 모범 답안 보기</summary>

```java
public static ArrayList<Integer> findPeaks(int[][] grid) {
    ArrayList<Integer> peaks = new ArrayList<Integer>();
    int rows = grid.length;
    int cols = grid[0].length;

    for (int c = 0; c < cols; c++) {
        for (int r = 0; r < rows; r++) {
            boolean isPeak = true;

            if (r > 0 && grid[r][c] <= grid[r - 1][c]) {
                isPeak = false;
            }
            if (r < rows - 1 && grid[r][c] <= grid[r + 1][c]) {
                isPeak = false;
            }
            if (c > 0 && grid[r][c] <= grid[r][c - 1]) {
                isPeak = false;
            }
            if (c < cols - 1 && grid[r][c] <= grid[r][c + 1]) {
                isPeak = false;
            }

            if (isPeak) {
                peaks.add(grid[r][c]);
            }
        }
    }

    return peaks;
}
```

</details>

#### Q2 무시할 오류 (Errors to Ignore)
- 세미콜론 누락
- `ArrayList<Integer>` 대신 `ArrayList<int>` (의도 명확 시)
- 중괄호 스타일
- `grid.length` / `grid[0].length` 접근 시 사소한 표기 오류
- 지역 변수명 차이 (의미가 명확한 경우)

---

# 채점 및 점수 해석

## Section I 점수 계산
- 21문제 중 맞힌 개수 × 1점 = MCQ 점수 (21점 만점)

## Section II 점수 계산
- Q1: Part (a) 4점 + Part (b) 3점 = 7점
- Q2: 6점
- FRQ 합계: 13점 만점

## 총점
- **총 34점 만점**
- 환산: (내 점수 / 34) × 100 = 백분율

---

### 레벨 테스트 3 점수 해석

| 백분율 | 판정 |
|--------|------|
| 85%+ (29/34 이상) | 5점 확정. 최고난도 통과 — 시험 당일 자신감 유지 |
| 75-84% (26-28/34) | 5점 유력. 틀린 문제 유형만 빠르게 복습 |
| 65-74% (22-25/34) | 4-5점 경계. 약점 패턴 분석 후 집중 보완 |
| 65% 미만 | 핵심 개념 재점검 필요 |

---

### 3세트 종합 점수 해석

3세트(LevelTest 1, 2, 3)를 모두 푼 후 종합:

| 3세트 평균 | 판정 |
|-----------|------|
| 80%+ | 5점 확실. 시험 당일 컨디션 관리만 하면 됨 |
| 70-79% | 5점 가능하지만 약점 보완 필요 |
| 60-69% | 4점 예상. 5점을 위해 약점 Unit 집중 복습 |
| 60% 미만 | 기본 개념 재학습 필요 |

---

### Unit별 약점 분석표

이 테스트에서 틀린 문제를 아래 표에 체크하여 약점 Unit을 파악하세요.

| Unit | 문제 번호 | 틀린 문제 | 복습 필요 토픽 |
|------|----------|-----------|---------------|
| U1 | Q1, Q2, Q3 | | 캐스팅 순서, 타입 변환 |
| U2 | Q4, Q5, Q6, Q7, Q8, Q9 | | compareTo, 생성자, static, autoboxing |
| U3 | Q10, Q11, Q12 | | 논리연산, De Morgan, for↔while 변환 |
| U4 | Q13~Q21 | | 중첩루프, 재귀, 정렬, 탐색, 2D배열, ArrayList |
