# AP Computer Science A — Level Test 10

> **목적:** AP CSA 5점 도달 여부를 진단하는 고난이도 테스트 — 최종 종합
> **제한 시간:** Section I (30분) + Section II (30분) = 총 60분
> **배점:** MCQ 21문제 × 1점 = 21점 / FRQ Q1 7점 + Q2 6점 = 13점 / **총 34점**

---

# Section I: Multiple Choice (21 Questions | 30 Minutes)

**Unit 분포:** U1(3) · U2(6) · U3(3) · U4(9)
**난이도:** 쉬움 2 · 보통 8 · 어려움 11

**지시사항:** Assume that the classes listed in the Java Quick Reference have been imported where appropriate. Unless otherwise noted, assume that parameters in method calls are not `null` and that methods are called only when their preconditions are met.

---

### 1. [U1 · 보통]

삼항 연산자(ternary expression)를 사용한 다음 코드를 살펴보세요.

```java
int x = 14;
int y = 20;
String result = (x > y) ? "A" : (x + y > 30) ? "B" : "C";
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `"A"`
(B) A compile-time error occurs
(C) `"C"`
(D) `"B"`

---

### 2. [U1 · 어려움]

Consider the following code segment.

```java
double val = Math.sqrt(50);
int rounded = (int)(val * 10) / 10;
System.out.println(rounded);
```

`Math.sqrt(50)`은 약 `7.0710678...`을 반환합니다.

What is printed as a result of executing this code segment?

(A) 7.0
(B) 0
(C) 70
(D) 7

---

### 3. [U1 · 어려움]

Consider the following code segment.

```java
int a = 100;
int b = a % 17 % 5 % 3;
System.out.println(b);
```

What is printed as a result of executing this code segment?

(A) 0
(B) 1
(C) 2
(D) 3

---

### 4. [U2 · 보통]

Consider the following code segment.

```java
String base = "CODE";
String result = "";
// charAt 대신 substring(i, i+1) (Quick Reference 준수)
for (int i = 0; i < base.length(); i++) {
    String ch = base.substring(i, i + 1);
    if ("AEIOU".indexOf(ch) >= 0) {
        result += "[" + ch + "]";
    } else {
        result += ch;
    }
}
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `"CODE"`
(B) `"[C]O[D]E"`
(C) `"C[O]D[E]"`
(D) `"C[O][D][E]"`

---

### 5. [U2 · 어려움]

다음은 while 루프로 do-while 동작을 시뮬레이션합니다.

```java
int n = 0;
boolean first = true;
while (first || n < 3) {
    first = false;
    n += 2;
}
System.out.println(n);
```

What is printed as a result of executing this code segment?

(A) 2
(B) 4
(C) 6
(D) 3

---

### 6. [U2 · 어려움]

Consider the following code segment.

```java
String word = "ABCDEFGH";
int left = 0;
int right = word.length() - 1;
String result = "";
while (left < right) {
    result += word.substring(left, left + 1) + word.substring(right, right + 1);
    left++;
    right--;
}
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `"AHBGCF"`
(B) `"ABCDHGFE"`
(C) `"AHBGCFD"`
(D) `"AHBGCFDE"`

---

### 7. [U2 · 쉬움]

Consider the following code segment.

```java
String s1 = "apple";
String s2 = "Apple";
int cmp = s1.compareTo(s2);
System.out.println(cmp > 0);
```

What is printed as a result of executing this code segment?

(A) `true`
(B) `false`
(C) `0`
(D) A run-time error occurs

---

### 8. [U2 · 어려움]

Consider the following code segment.

```java
String text = "abracadabra";
int count = 0;
int idx = text.indexOf("a");
while (idx != -1) {
    count++;
    idx = text.indexOf("a", idx + 1);
}
System.out.println(count);
```

What is printed as a result of executing this code segment?

(A) 4
(B) 3
(C) 6
(D) 5

---

### 9. [U2 · 어려움]

Consider the following code segment.

```java
String data = "[Name:Alice|Age:30|Score:95]";
int start = data.indexOf("Age:") + 4;
int end = data.indexOf("|", start);
String extracted = data.substring(start, end);
System.out.println(extracted);
```

What is printed as a result of executing this code segment?

(A) `"Age:30"`
(B) `"Age:30|Score:95"`
(C) `"30|Score:95]"`
(D) `"30"`

---

### 10. [U3 · 보통]

다음 boolean 표현식을 살펴보세요.

```java
boolean p = true, q = false, r = true;
boolean result = !(p && q) || (q && r);
```

`result`의 값은?

(A) 컴파일 에러
(B) `false`
(C) `true`
(D) 결정할 수 없음

---

### 11. [U3 · 어려움]

exclusive-or를 De Morgan의 법칙으로 표현한 다음 코드를 살펴보세요.

```java
boolean a = true, b = false;
boolean xor = (a || b) && !(a && b);
boolean deMorgan = (a || b) && (!a || !b);
System.out.println(xor == deMorgan);
```

What is printed as a result of executing this code segment?

(A) `true`
(B) `false`
(C) 컴파일 에러
(D) 결과는 `a`, `b` 값에 따라 달라진다

---

### 12. [U3 · 어려움]

Consider the following code segment.

```java
String str = null;
boolean result = (str != null && str.length() > 0);
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `true`
(B) `false`
(C) A `NullPointerException` is thrown
(D) 컴파일 에러

---

### 13. [U4 · 어려움]

Kadane 알고리즘의 단순화된 버전입니다. 최대 부분 배열 합을 구합니다.

```java
int[] arr = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
int maxSoFar = arr[0];
int maxEndingHere = arr[0];
// Math.max 대신 if 비교 (Quick Reference 준수)
for (int i = 1; i < arr.length; i++) {
    int candidate = maxEndingHere + arr[i];
    if (arr[i] > candidate) {
        maxEndingHere = arr[i];
    } else {
        maxEndingHere = candidate;
    }
    if (maxEndingHere > maxSoFar) {
        maxSoFar = maxEndingHere;
    }
}
System.out.println(maxSoFar);
```

What is printed as a result of executing this code segment?

(A) 5
(B) 6
(C) 7
(D) 4

---

### 14. [U4 · 어려움]

두 개의 정렬된 `ArrayList`를 병합하는 코드입니다.

```java
ArrayList<Integer> a = new ArrayList<>(Arrays.asList(1, 3, 5, 7));
ArrayList<Integer> b = new ArrayList<>(Arrays.asList(2, 4, 6));
ArrayList<Integer> merged = new ArrayList<>();
int i = 0, j = 0;
while (i < a.size() && j < b.size()) {
    if (a.get(i) <= b.get(j)) {
        merged.add(a.get(i++));
    } else {
        merged.add(b.get(j++));
    }
}
while (i < a.size()) merged.add(a.get(i++));
while (j < b.size()) merged.add(b.get(j++));
System.out.println(merged);
```

What is printed as a result of executing this code segment?

(A) `[1, 2, 3, 4, 5, 6, 7]`
(B) `[1, 3, 5, 7, 2, 4, 6]`
(C) `[2, 4, 6, 1, 3, 5, 7]`
(D) `[1, 2, 3, 4, 5, 6]`

---

### 15. [U4 · 보통]

다음은 3×3 배열이 magic square인지 검사합니다. magic square는 모든 행, 열, 대각선의 합이 같습니다.

```java
int[][] grid = {
    {2, 7, 6},
    {9, 5, 1},
    {4, 3, 8}
};
int target = grid[0][0] + grid[0][1] + grid[0][2];
boolean magic = true;
// 행 검사
for (int r = 1; r < 3; r++) {
    int sum = 0;
    for (int c = 0; c < 3; c++) sum += grid[r][c];
    if (sum != target) magic = false;
}
// 열 검사
for (int c = 0; c < 3; c++) {
    int sum = 0;
    for (int r = 0; r < 3; r++) sum += grid[r][c];
    if (sum != target) magic = false;
}
System.out.println(target + " " + magic);
```

What is printed as a result of executing this code segment?

(A) `"15 true"`
(B) `"15 false"`
(C) `"21 true"`
(D) `"21 false"`

---

### 16. [U4 · 보통]

> **참고:** 메모이제이션은 AP 시험 범위 밖이지만, 재귀 호출 추적 능력을 테스트합니다.

다음 클래스의 `fib` 메서드를 사용합니다.

```java
public class FibMemo
{
    private static int[] memo = new int[10];

    static
    {
        Arrays.fill(memo, -1);
        memo[0] = 0;
        memo[1] = 1;
    }

    public static int fib(int n)
    {
        if (memo[n] != -1) return memo[n];
        memo[n] = fib(n - 1) + fib(n - 2);
        return memo[n];
    }
}
```

`FibMemo.fib(7)`를 호출했을 때 `fib` 메서드가 총 몇 번 호출됩니까? (최초 호출 포함)

(A) 7
(B) 11
(C) 13
(D) 25

---

### 17. [U4 · 어려움]

merge sort 과정을 추적합니다.

```
배열: [5, 2, 8, 1, 9, 3]
```

merge sort가 완료된 후 **첫 번째 merge 단계**(크기 1인 원소들을 크기 2로 병합)의 결과로 만들어지는 부분 배열들은?

(A) `[5, 2] [1, 8] [3, 9]`
(B) `[2, 5] [1, 8] [9, 3]`
(C) `[2, 5] [1, 8] [3, 9]`
(D) `[2, 5, 8] [1, 3, 9]`

---

### 18. [U4 · 보통]
> **참고:** `retainAll()`은 AP Quick Reference에 없지만, ArrayList 조작 이해를 위해 포함했습니다.

Consider the following code segment.

```java
ArrayList<Integer> list1 = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5, 6));
ArrayList<Integer> list2 = new ArrayList<>(Arrays.asList(2, 4, 6, 8));
list1.retainAll(list2);
System.out.println(list1);
```

What is printed as a result of executing this code segment?

(A) `[1, 2, 3, 4, 5, 6, 8]`
(B) `[1, 3, 5]`
(C) `[2, 4, 6]`
(D) `[2, 4, 6, 8]`

---

### 19. [U4 · 보통]

2D 배열에서 왼쪽 위 `(0,0)`에서 오른쪽 아래 `(2,2)`까지 **오른쪽 또는 아래로만** 이동할 때 경로의 수는?

```java
// 3×3 격자
// (0,0) → (2,2), 오른쪽(R) 또는 아래(D)만 가능
```

(A) 4
(B) 6
(C) 8
(D) 9

---

### 20. [U4 · 쉬움]

배열을 오른쪽으로 k만큼 회전시키는 코드입니다.

```java
int[] arr = {1, 2, 3, 4, 5};
int k = 2;
int n = arr.length;
int[] rotated = new int[n];
for (int i = 0; i < n; i++) {
    rotated[(i + k) % n] = arr[i];
}
System.out.println(Arrays.toString(rotated));
```

What is printed as a result of executing this code segment?

(A) `[3, 4, 5, 1, 2]`
(B) `[4, 5, 1, 2, 3]`
(C) `[5, 1, 2, 3, 4]`
(D) `[2, 3, 4, 5, 1]`

---

### 21. [U4 · 보통]

정렬된 배열에서 target에 가장 가까운 원소를 이진 탐색으로 찾습니다.

```java
int[] arr = {1, 4, 7, 10, 15, 20};
int target = 12;
int lo = 0, hi = arr.length - 1;
while (lo < hi) {
    int mid = (lo + hi) / 2;
    if (arr[mid] < target) {
        lo = mid + 1;
    } else {
        hi = mid;
    }
}
// lo가 가리키는 위치와 그 왼쪽 중 더 가까운 것 선택
int closest;
if (lo > 0 && Math.abs(arr[lo - 1] - target) <= Math.abs(arr[lo] - target)) {
    closest = arr[lo - 1];
} else {
    closest = arr[lo];
}
System.out.println(closest);
```

What is printed as a result of executing this code segment?

(A) 7
(B) 15
(C) 10
(D) 12

---

# Section II: Free Response (2 Questions | 30 Minutes)

---

## Q1. PasswordValidator (7점)

다음 `PasswordValidator` 클래스는 비밀번호의 강도를 평가하고 규칙에 맞는 비밀번호를 생성하는 메서드를 포함합니다.

```java
public class PasswordValidator {

    /**
     * 비밀번호 강도를 평가합니다.
     * 판정 기준:
     *   - 길이가 8 이상
     *   - 대문자 포함
     *   - 소문자 포함
     *   - 숫자(digit) 포함
     * 0~1개 충족 → "weak", 2~3개 충족 → "medium", 4개 모두 충족 → "strong"
     *
     * @param password  평가할 비밀번호 (빈 문자열이 아님을 보장)
     * @return "weak", "medium", "strong" 중 하나
     */
    public String evaluateStrength(String password) {
        /* Part (a): 여기에 코드를 작성하세요 */
    }

    /**
     * 주어진 length 길이의 비밀번호를 생성합니다.
     * allowed 문자열의 문자를 순환(cycle)하여 비밀번호를 구성합니다.
     * 예: generatePassword(7, "abc") → "abcabca"
     *
     * @param length   생성할 비밀번호 길이 (1 이상)
     * @param allowed  사용할 문자 집합 (빈 문자열이 아님을 보장)
     * @return 생성된 비밀번호 문자열
     */
    public String generatePassword(int length, String allowed) {
        /* Part (b): 여기에 코드를 작성하세요 */
    }
}
```

### Part (a) — `evaluateStrength` (4점)

`evaluateStrength` 메서드를 작성하세요.

**예시:**

| 호출 | 반환값 |
|------|--------|
| `evaluateStrength("ab")` | `"weak"` |
| `evaluateStrength("Hello123")` | `"strong"` |
| `evaluateStrength("ABCDEFGH")` | `"medium"` |
| `evaluateStrength("abcDEF")` | `"medium"` |

### Part (b) — `generatePassword` (3점)

`generatePassword` 메서드를 작성하세요.

**예시:**

| 호출 | 반환값 |
|------|--------|
| `generatePassword(7, "abc")` | `"abcabca"` |
| `generatePassword(5, "XY")` | `"XYXYX"` |
| `generatePassword(3, "Hello")` | `"Hel"` |

---

## Q2. EventScheduler (6점)

다음은 일정 관리 시스템의 일부입니다. `Event` 클래스는 이미 정의되어 있습니다.

```java
public class Event {
    private int start;
    private int end;
    private String name;

    public Event(int start, int end, String name) {
        this.start = start;
        this.end = end;
        this.name = name;
    }

    public int getStart() { return start; }
    public int getEnd() { return end; }
    public String getName() { return name; }
}
```

```java
import java.util.ArrayList;

public class EventScheduler {
    private ArrayList<Event> events;  // 시작 시간 기준 오름차순 정렬됨

    public EventScheduler(ArrayList<Event> events) {
        this.events = events;
    }

    /**
     * 겹치는 이벤트를 제거합니다.
     * 두 이벤트가 겹칠 때 (이전 이벤트의 end > 다음 이벤트의 start):
     *   - 더 일찍 끝나는 이벤트를 유지합니다.
     *   - 끝나는 시간이 같으면 앞에 있는(먼저 나오는) 이벤트를 유지합니다.
     * events 리스트를 직접 수정합니다.
     */
    public void resolveConflicts() {
        /* Part (a): 여기에 코드를 작성하세요 */
    }

    /**
     * 이벤트들 사이의 빈 시간대를 반환합니다.
     * resolveConflicts()가 이미 호출되어 겹치는 이벤트가 없다고 가정합니다.
     * 반환 형식: "시작-끝" (예: "9-10", "14-17")
     *
     * @param dayStart  하루의 시작 시각 (예: 8)
     * @param dayEnd    하루의 끝 시각 (예: 18)
     * @return 빈 시간대 문자열의 ArrayList
     */
    public ArrayList<String> getFreeSlots(int dayStart, int dayEnd) {
        /* Part (b): 여기에 코드를 작성하세요 */
    }
}
```

### Part (a) — `resolveConflicts` (4점)

`resolveConflicts` 메서드를 작성하세요.

**예시:**

`events` 리스트가 다음과 같을 때:

| 인덱스 | name | start | end |
|--------|------|-------|-----|
| 0 | "Meeting" | 9 | 11 |
| 1 | "Call" | 10 | 12 |
| 2 | "Lunch" | 12 | 13 |
| 3 | "Review" | 12 | 14 |

- "Meeting"(9-11)과 "Call"(10-12)이 겹침 → "Meeting"이 더 일찍 끝남(11 < 12) → "Call" 제거
- "Meeting"(9-11)과 "Lunch"(12-13): 11 > 12가 아니므로 겹치지 않음
- "Lunch"(12-13)와 "Review"(12-14): 13 > 12 → 겹침 → "Lunch"가 더 일찍 끝남(13 < 14) → "Review" 제거

결과: `["Meeting"(9-11), "Lunch"(12-13)]`

### Part (b) — `getFreeSlots` (2점)

`getFreeSlots` 메서드를 작성하세요.

**예시:**

`resolveConflicts()` 후 events = `["Meeting"(9-11), "Lunch"(12-13)]`, `dayStart=8`, `dayEnd=17`일 때:

반환값: `["8-9", "11-12", "13-17"]`

---

# Answer Key

---

## Section I: MCQ 정답 및 해설

---

### 1. 정답: **(D)**

**해설:** `x > y` → `14 > 20` → `false`. 따라서 두 번째 삼항이 평가됩니다. `x + y > 30` → `34 > 30` → `true` → `"B"`가 반환됩니다. 중첩 삼항 연산자는 오른쪽에서 왼쪽으로 결합하지만, 첫 번째 조건이 `false`이므로 `:` 뒤의 표현식이 평가되고, 거기서 다시 `true`이므로 `"B"`가 선택됩니다.

---

### 2. 정답: **(D)**

**해설:** `Math.sqrt(50)` ≈ `7.0710678`. `val * 10` ≈ `70.710678`. `(int)(70.710678)` = `70` (소수 버림). `70 / 10` = `7` (int끼리 나눗셈이므로 정수 결과). `rounded`는 `int`형이므로 `7`이 출력됩니다. `(int)`캐스팅이 `val * 10` 전체에 적용된 뒤 int 나눗셈이 수행되는 점이 핵심입니다.

---

### 3. 정답: **(A)**

**해설:** `%` 연산자는 왼쪽에서 오른쪽으로 결합합니다. `100 % 17 = 15` (100 = 17×5 + 15). `15 % 5 = 0` (15 = 5×3). `0 % 3 = 0`. 최종 결과는 `0`입니다.

---

### 4. 정답: **(C)**

**해설:** `"AEIOU".indexOf(ch)`를 사용하여 모음 여부를 판단합니다.
- `'C'`: indexOf → `-1` → else → `"C"`
- `'O'`: indexOf → `4` (≥ 0) → if → `"[O]"`
- `'D'`: indexOf → `-1` → else → `"D"`
- `'E'`: indexOf → `1` (≥ 0) → if → `"[E]"`

결과: `"C[O]D[E]"`.

---

### 5. 정답: **(B)**

**해설:**
- 반복 1: `first=true` → 조건 충족, `first=false`, `n=0+2=2`
- 반복 2: `first=false`, `n<3` → `2<3=true` → 조건 충족, `n=2+2=4`
- 반복 3: `first=false`, `n<3` → `4<3=false` → 루프 종료

`n = 4`가 출력됩니다.

---

### 6. 정답: **(D)**

**해설:** `word = "ABCDEFGH"` (길이 8), `left=0`, `right=7`.
- left=0, right=7: `"A" + "H"` → `"AH"`, left=1, right=6
- left=1, right=6: `"B" + "G"` → `"BG"`, left=2, right=5
- left=2, right=5: `"C" + "F"` → `"CF"`, left=3, right=4
- left=3, right=4: `"D" + "E"` → `"DE"`, left=4, right=3 → `4 < 3` 거짓 → 종료

결과: `"AHBGCFDE"`. 양 끝에서 중앙으로 수렴하며 문자를 쌍으로 결합하는 two-pointer 패턴입니다.

---

### 7. 정답: **(A)**

**해설:** `"apple".compareTo("Apple")`은 첫 문자 `'a'`(97)와 `'A'`(65)를 비교합니다. `97 - 65 = 32 > 0`이므로 `cmp > 0`은 `true`입니다. `compareTo`는 대소문자를 구별하며, 소문자가 대문자보다 유니코드 값이 큽니다.

---

### 8. 정답: **(D)**

**해설:** `"abracadabra"`에서 `'a'`의 위치: 인덱스 0, 3, 5, 7, 10. 총 **5개**입니다. `indexOf`를 루프에서 사용하여 특정 문자의 출현 횟수를 세는 표준 패턴입니다.

---

### 9. 정답: **(D)**

**해설:** `"[Name:Alice|Age:30|Score:95]"`에서:
- `indexOf("Age:")` → 인덱스 12 (`[`=0, `N`=1, ..., `|`=11, `A`=12)
- `start = 12 + 4 = 16` → `'3'`의 위치
- `indexOf("|", 16)` → 인덱스 18 (두 번째 `|`)
- `substring(16, 18)` → `"30"`

두 번째 매개변수를 가진 `indexOf`가 특정 위치 이후부터 검색하는 점이 핵심입니다.

---

### 10. 정답: **(C)**

**해설:** `!(p && q) || (q && r)` = `!(true && false) || (false && true)` = `!false || false` = `true || false` = `true`. `&&`가 `||`보다 우선순위가 높고, `!`가 가장 높습니다.

---

### 11. 정답: **(A)**

**해설:** `!(a && b)`와 `(!a || !b)`는 De Morgan의 법칙에 의해 동치입니다. 따라서 `xor`과 `deMorgan`은 항상 같은 값을 가지며, `a`와 `b`의 어떤 조합에서도 `xor == deMorgan`은 `true`입니다. 이 동치성은 `a`, `b` 값에 무관하게 성립합니다 — 선택지 (D)는 함정입니다.

---

### 12. 정답: **(B)**

**해설:** `str != null`이 `false`이므로 `&&`의 short-circuit 평가에 의해 `str.length()`는 호출되지 않습니다. 전체 표현식은 `false`가 됩니다. `NullPointerException`이 발생하지 않는 이유는 `&&` 연산자가 왼쪽이 `false`일 때 오른쪽을 평가하지 않기 때문입니다.

---

### 13. 정답: **(B)**

**해설:** Kadane 알고리즘 추적:

| i | arr[i] | maxEndingHere | maxSoFar |
|---|--------|---------------|----------|
| 0 | -2 | -2 | -2 |
| 1 | 1 | max(1, -1) = 1 | 1 |
| 2 | -3 | max(-3, -2) = -2 | 1 |
| 3 | 4 | max(4, 2) = 4 | 4 |
| 4 | -1 | max(-1, 3) = 3 | 4 |
| 5 | 2 | max(2, 5) = 5 | 5 |
| 6 | 1 | max(1, 6) = 6 | 6 |
| 7 | -5 | max(-5, 1) = 1 | 6 |
| 8 | 4 | max(4, 5) = 5 | 6 |

최대 부분 배열은 `[4, -1, 2, 1]` (합 = 6)입니다.

---

### 14. 정답: **(A)**

**해설:** 두 정렬된 리스트를 병합하는 표준 merge 알고리즘입니다. 두 포인터가 각각의 리스트를 순회하면서 더 작은 원소를 먼저 추가합니다. 결과: `[1, 2, 3, 4, 5, 6, 7]`.

---

### 15. 정답: **(A)**

**해설:** 주어진 3×3 배열은 고전적인 magic square입니다.
- 행: 2+7+6=15, 9+5+1=15, 4+3+8=15
- 열: 2+9+4=15, 7+5+3=15, 6+1+8=15

`target = 15`, 모든 행과 열의 합이 15이므로 `magic = true`. 출력: `"15 true"`.
(참고: 코드는 대각선 검사를 포함하지 않지만, 이 배열은 대각선도 15입니다.)

---

### 16. 정답: **(C)**

**해설:** 메모이제이션으로 각 `fib(n)`은 처음 한 번만 계산되고, 이후 호출은 memo에서 즉시 반환됩니다.

호출 순서 (들여쓰기 = 재귀 깊이):
1. `fib(7)` → memo에 없음
2. `fib(6)` → memo에 없음
3. `fib(5)` → memo에 없음
4. `fib(4)` → memo에 없음
5. `fib(3)` → memo에 없음
6. `fib(2)` → memo에 없음
7. `fib(1)` → memo hit → return 1
8. `fib(0)` → memo hit → return 0 → memo[2]=1
9. `fib(1)` → memo hit → return 1 → memo[3]=2
10. `fib(2)` → memo hit → return 1 → memo[4]=3
11. `fib(3)` → memo hit → return 2 → memo[5]=5
12. `fib(4)` → memo hit → return 3 → memo[6]=8
13. `fib(5)` → memo hit → return 5 → memo[7]=13

총 **13번** 호출됩니다.

---

### 17. 정답: **(C)**

**해설:** merge sort에서 배열 `[5, 2, 8, 1, 9, 3]`은 먼저 인접한 원소 쌍으로 분할됩니다: `(5,2)`, `(8,1)`, `(9,3)`. 첫 번째 merge 단계에서 각 쌍을 정렬하여 병합합니다:
- `[5, 2]` → `[2, 5]`
- `[8, 1]` → `[1, 8]`
- `[9, 3]` → `[3, 9]`

---

### 18. 정답: **(C)**

**해설:** `retainAll`은 두 컬렉션의 **교집합**만 유지합니다. `{1,2,3,4,5,6} ∩ {2,4,6,8} = {2,4,6}`. `list1`이 직접 수정되어 `[2, 4, 6]`만 남습니다.

---

### 19. 정답: **(B)**

**해설:** `(0,0)`에서 `(2,2)`까지 도달하려면 오른쪽(R) 2번, 아래(D) 2번 = 총 4번 이동해야 합니다. 경로의 수는 4번의 이동 중 R 2번의 위치를 선택하는 조합: C(4,2) = 4!/(2!×2!) = **6**가지입니다.

---

### 20. 정답: **(B)**

**해설:** `rotated[(i+k) % n] = arr[i]`로 각 원소의 새 위치를 계산합니다:
- `i=0`: `rotated[(0+2)%5]` = `rotated[2]` = 1
- `i=1`: `rotated[(1+2)%5]` = `rotated[3]` = 2
- `i=2`: `rotated[(2+2)%5]` = `rotated[4]` = 3
- `i=3`: `rotated[(3+2)%5]` = `rotated[0]` = 4
- `i=4`: `rotated[(4+2)%5]` = `rotated[1]` = 5

결과: `[4, 5, 1, 2, 3]`. 오른쪽으로 2칸 회전하면 마지막 2개 원소 `{4,5}`가 앞으로 이동합니다.

---

### 21. 정답: **(C)**

**해설:** 이진 탐색 추적 (`target = 12`):

| 단계 | lo | hi | mid | arr[mid] | 동작 |
|------|----|----|-----|----------|------|
| 1 | 0 | 5 | 2 | 7 | 7 < 12 → lo = 3 |
| 2 | 3 | 5 | 4 | 15 | 15 ≥ 12 → hi = 4 |
| 3 | 3 | 4 | 3 | 10 | 10 < 12 → lo = 4 |
| 종료 | 4 | 4 | — | — | lo == hi |

`lo = 4`, `arr[4] = 15`. `lo > 0`이므로 왼쪽 비교: `|arr[3] - 12| = |10 - 12| = 2`, `|arr[4] - 12| = |15 - 12| = 3`. `2 ≤ 3` → `closest = arr[3] = 10`.

---

## Section II: FRQ 모범 답안 및 채점 기준

---

## Q1. PasswordValidator — 모범 답안

### Part (a) — `evaluateStrength` (4점)

```java
public String evaluateStrength(String password) {
    int criteria = 0;

    if (password.length() >= 8) {
        criteria++;
    }

    boolean hasUpper = false;
    boolean hasLower = false;
    boolean hasDigit = false;

    // charAt 대신 substring(i, i+1) + compareTo 알파벳/숫자 범위 (Quick Reference 준수)
    for (int i = 0; i < password.length(); i++) {
        String ch = password.substring(i, i + 1);
        if (ch.compareTo("A") >= 0 && ch.compareTo("Z") <= 0) {
            hasUpper = true;
        }
        if (ch.compareTo("a") >= 0 && ch.compareTo("z") <= 0) {
            hasLower = true;
        }
        if (ch.compareTo("0") >= 0 && ch.compareTo("9") <= 0) {
            hasDigit = true;
        }
    }

    if (hasUpper) criteria++;
    if (hasLower) criteria++;
    if (hasDigit) criteria++;

    if (criteria >= 4) {
        return "strong";
    } else if (criteria >= 2) {
        return "medium";
    } else {
        return "weak";
    }
}
```

> ⚠️ **Quick Reference 준수:** `Character.isUpperCase()`, `Character.isLowerCase()`, `Character.isDigit()`, `charAt()`은 모두 AP CSA Java Quick Reference에 포함되어 있지 않으므로 시험에서는 사용 금지. 위 모범답안처럼 `substring(i, i+1)`로 한 글자 String을 얻고 `compareTo`로 알파벳/숫자 범위를 비교하는 패턴이 표준이다.

#### 채점 기준 (4점)

| 포인트 | 기준 |
|--------|------|
| +1 | 길이 기준(`password.length() >= 8`)을 올바르게 판정 |
| +1 | 문자열을 순회하며 대문자/소문자/숫자 여부를 각각 판별 |
| +1 | 충족 기준 수를 정확히 카운트 |
| +1 | 카운트에 따라 `"weak"`, `"medium"`, `"strong"`을 올바르게 반환 |

#### 감점 사항

| 감점 | 사유 |
|------|------|
| -1 | 기준 경계값 오류 (예: 0~1을 medium으로 판정) |
| -1 | 루프 없이 첫 문자만 검사 |
| -1 | 존재하지 않는 메서드 호출 또는 메서드 시그니처를 잘못 사용 |
| -1 | 반환값 철자 오류 (`"Weak"` 등 대소문자 다름) |

---

### Part (b) — `generatePassword` (3점)

```java
public String generatePassword(int length, String allowed) {
    String result = "";
    // charAt 대신 substring(idx, idx+1) (Quick Reference 준수)
    for (int i = 0; i < length; i++) {
        int idx = i % allowed.length();
        result += allowed.substring(idx, idx + 1);
    }
    return result;
}
```

#### 채점 기준 (3점)

| 포인트 | 기준 |
|--------|------|
| +1 | `length`번 반복하는 루프 구성 |
| +1 | `i % allowed.length()`로 순환 인덱스 계산 |
| +1 | 문자를 올바르게 연결하여 반환 |

#### 감점 사항

| 감점 | 사유 |
|------|------|
| -1 | `%` 대신 조건문으로 인덱스 리셋 시 off-by-one 에러 |
| -1 | `allowed.length()` 대신 `length`를 나눗셈에 사용 |
| -1 | 반환하지 않거나 빈 문자열 반환 |

---

## Q2. EventScheduler — 모범 답안

### Part (a) — `resolveConflicts` (4점)

```java
public void resolveConflicts() {
    int i = 0;
    while (i < events.size() - 1) {
        Event current = events.get(i);
        Event next = events.get(i + 1);

        if (current.getEnd() > next.getStart()) {
            // 겹침 발생 — 더 늦게 끝나는 이벤트 제거
            if (current.getEnd() <= next.getEnd()) {
                // current가 더 일찍 끝나거나 같음 → next 제거
                events.remove(i + 1);
            } else {
                // next가 더 일찍 끝남 → current 제거
                events.remove(i);
            }
        } else {
            i++;
        }
    }
}
```

#### 채점 기준 (4점)

| 포인트 | 기준 |
|--------|------|
| +1 | 인접한 이벤트 쌍을 순회하는 올바른 루프 구조 |
| +1 | `current.getEnd() > next.getStart()`로 겹침을 올바르게 판단 |
| +1 | 더 일찍 끝나는 이벤트를 유지하고 나머지를 제거하는 로직 |
| +1 | `remove` 후 인덱스를 증가시키지 않아 연속 충돌을 올바르게 처리 |

#### 감점 사항

| 감점 | 사유 |
|------|------|
| -1 | 겹침 조건에서 `>=` 사용 (end == start는 겹치지 않음) |
| -1 | `remove` 후 `i++` 하여 원소를 건너뜀 |
| -1 | for-each 루프에서 `remove` 호출 → `ConcurrentModificationException` |
| -1 | 끝나는 시간이 같을 때 뒤의 이벤트를 유지 (사양 위반) |

---

### Part (b) — `getFreeSlots` (2점)

```java
public ArrayList<String> getFreeSlots(int dayStart, int dayEnd) {
    ArrayList<String> free = new ArrayList<>();
    int current = dayStart;

    for (int i = 0; i < events.size(); i++) {
        if (current < events.get(i).getStart()) {
            free.add(current + "-" + events.get(i).getStart());
        }
        current = events.get(i).getEnd();
    }

    if (current < dayEnd) {
        free.add(current + "-" + dayEnd);
    }

    return free;
}
```

#### 채점 기준 (2점)

| 포인트 | 기준 |
|--------|------|
| +1 | 이벤트 사이의 빈 시간을 올바르게 식별하여 `"시작-끝"` 형식으로 추가 |
| +1 | `dayStart` 이전의 빈 시간과 마지막 이벤트 이후 `dayEnd`까지의 빈 시간 처리 |

#### 감점 사항

| 감점 | 사유 |
|------|------|
| -1 | 첫 이벤트 전의 빈 시간(`dayStart` ~ 첫 이벤트 시작)을 누락 |
| -1 | 마지막 이벤트 후의 빈 시간(마지막 이벤트 끝 ~ `dayEnd`)을 누락 |
| -1 | 문자열 형식 오류 (예: `"-"` 누락, 정수를 문자열로 변환하지 않음) |

---

# 점수 해석표

| 점수 범위 | 예상 AP 등급 | 해석 |
|-----------|-------------|------|
| **28 – 34** | **5** | 시험 준비 완료. 모든 핵심 개념을 확실히 이해하고 있습니다. |
| **21 – 27** | **4** | 대부분의 개념을 이해하지만 일부 고급 주제에서 보완이 필요합니다. |
| **14 – 20** | **3** | 기본 개념은 이해하나 응용력과 코드 추적 능력에 보완이 필요합니다. |
| **0 – 13** | **—** | 핵심 개념부터 다시 복습이 필요합니다. |

---

### 난이도별 자가 진단

| 영역 | 만점 | 내 점수 | 보완 필요 |
|------|------|---------|-----------|
| 쉬움 MCQ (2문제) | 2 | ___ / 2 | |
| 보통 MCQ (8문제) | 8 | ___ / 8 | |
| 어려움 MCQ (11문제) | 11 | ___ / 11 | |
| FRQ Q1 (PasswordValidator) | 7 | ___ / 7 | |
| FRQ Q2 (EventScheduler) | 6 | ___ / 6 | |
| **총점** | **34** | ___ / 34 | |

---

### Unit별 자가 진단

| Unit | 문제 번호 | 만점 | 내 점수 |
|------|-----------|------|---------|
| U1: Primitive Types | 1, 2, 3 | 3 | ___ / 3 |
| U2: Using Objects | 4, 5, 6, 7, 8, 9 | 6 | ___ / 6 |
| U3: Boolean / if | 10, 11, 12 | 3 | ___ / 3 |
| U4: Iteration + Array | 13–21 | 9 | ___ / 9 |
| FRQ | Q1, Q2 | 13 | ___ / 13 |
