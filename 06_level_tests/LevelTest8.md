# AP Computer Science A — Level Test 8

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
int x = 10;
double y = x / 4;
System.out.println(y);
```

(A) 2.5
(B) 2.0
(C) 2
(D) 3.0

---

### 2. [U1 · 보통]

다음 코드의 출력은?

```java
int max = (int)(Math.random() * 6) + 1;
```

`max`의 가능한 값의 범위는?

(A) 0 ~ 5
(B) 1 ~ 6
(C) 0 ~ 6
(D) 1 ~ 7

---

### 3. [U1 · 어려움]

다음 코드의 출력은?

```java
int a = 5;
double b = a;
int c = (int) b;
a = a + 1;
System.out.println(a + " " + b + " " + c);
```

(A) `6 6.0 6`
(B) `6 5.0 6`
(C) `5 5.0 5`
(D) `6 5.0 5`

---

### 4. [U2 · 쉬움]

다음 코드의 출력은?

```java
String s = "HELLO";
System.out.println(s.equals("hello"));
System.out.println(s.substring(0, 1).equals("H"));
```

(A)
```
false
true
```

(B)
```
true
true
```

(C)
```
false
false
```

(D)
```
true
false
```

---

### 5. [U2 · 보통]

다음 코드의 출력은?

```java
int n = 1;
do {
    System.out.print(n + " ");
    n *= 2;
} while (n <= 16);
```

> **참고:** `do-while`은 AP 시험 범위 밖이지만 코드 추적 연습을 위해 포함.

(A) `1 2 4 8`
(B) `1 2 4 8 16 32`
(C) `2 4 8 16`
(D) `1 2 4 8 16`

---

### 6. [U2 · 어려움]
> **참고:** `String.split()`은 2025-26 AP Quick Reference에 추가되었지만, 일부 학생에게 생소할 수 있습니다.

다음 코드의 출력은?

```java
String s = "ab cd ef";
String[] parts = s.split(" ");
String result = "";
for (int i = parts.length - 1; i >= 0; i--)
{
    result += parts[i];
    if (i > 0) result += " ";
}
System.out.println(result);
```

(A) `"ef cd ab"`
(B) `"ab cd ef"`
(C) `"fedcba"`
(D) `"ef dc ba"`

---

### 7. [U2 · 보통]

다음 코드의 출력은?

```java
String s = "Hello World";
int count = 0;
for (int i = 0; i < s.length(); i++)
{
    String ch = s.substring(i, i + 1);
    if (ch.equals(ch.toUpperCase()) && !ch.equals(" "))
    {
        count++;
    }
}
System.out.println(count);
```

(A) 5
(B) 3
(C) 2
(D) 0

---

### 8. [U2 · 어려움]

> **참고:** 메서드 오버로딩(overloading)은 클래스 설계(Unit 5) 주제이지만, 메서드 호출 규칙 이해를 위해 포함했습니다.

다음 두 메서드 중 `add(3, 5)` 와 `add(3.0, 5)` 의 결과는?

```java
public static int add(int a, int b)
{
    return a + b;
}

public static double add(double a, int b)
{
    return a + b + 0.5;
}
```

(A) 컴파일 에러
(B) 8, 8.0
(C) 8.5, 8.5
(D) 8, 8.5

---

### 9. [U2 · 어려움]

다음 코드의 출력은?

```java
String result = "";
for (int r = 1; r <= 3; r++)
{
    for (int c = 1; c <= 3; c++)
    {
        if (r + c <= 4)
            result += "*";
        else
            result += " ";
    }
    result += "\n";
}
System.out.print(result);
```

(A)
```
***
**
*
```

(B)
```
***
***
*
```

(C)
```
***
** 
*  
```

(D)
```
*
**
***
```

---

### 10. [U3 · 보통]

다음 식에서 `x = 3, y = 7`일 때 결과는?

```java
boolean result = (x > 5) && (y > 5) || (x + y > 9);
```

(A) `true`
(B) `false`
(C) 컴파일 에러
(D) 결과를 알 수 없음

---

### 11. [U3 · 어려움]

다음 표현은 XOR(배타적 논리합)을 구현한다. `p = true, q = true`일 때 결과는?

```java
boolean xor = (p || q) && !(p && q);
```

(A) `true`
(B) `false`
(C) 컴파일 에러
(D) 런타임 에러

---

### 12. [U3 · 어려움]

다음 코드에서 몇 가지 입력 조합이 `"yes"`를 출력하는가?

```java
// a와 b는 각각 true 또는 false
if (a || !b)
{
    System.out.println("yes");
}
```

(A) 1가지
(B) 2가지
(C) 3가지
(D) 4가지

---

### 13. [U4 · 쉬움]

다음 코드의 출력은?

```java
int[] arr = {10, 20, 30, 40};
int[] freq = new int[5];
for (int val : arr)
{
    freq[val / 10]++;
}
System.out.println(freq[2]);
```

(A) 0
(B) 1
(C) 2
(D) 20

---

### 14. [U4 · 보통]

다음 코드의 출력은?

```java
ArrayList<String> list = new ArrayList<String>();
list.add("x");
list.add("y");
list.add("z");

for (int i = 0; i < list.size(); i++)
{
    list.set(i, list.get(i) + list.get(i));
}
System.out.println(list);
```

(A) `[xx, yy, zz]`
(B) `[x, y, z, x, y, z]`
(C) `[xy, yz, zx]`
(D) `[xxyyzz]`

---

### 15. [U4 · 어려움]

다음 코드의 출력은?

```java
int[][] grid = {{1, 2, 3, 4},
                {5, 6, 7, 8},
                {9, 10, 11, 12}};
int sum = 0;
for (int i = 0; i < Math.min(grid.length, grid[0].length); i++)
{
    sum += grid[i][grid[0].length - 1 - i];
}
System.out.println(sum);
```

(A) 18
(B) 20
(C) 21
(D) 15

---

### 16. [U4 · 보통]

다음 코드의 출력은?

```java
int[] arr = {5, 2, 8, 1, 9};
int secondMax = Integer.MIN_VALUE;
int max = Integer.MIN_VALUE;
for (int val : arr)
{
    if (val > max)
    {
        secondMax = max;
        max = val;
    }
    else if (val > secondMax)
    {
        secondMax = val;
    }
}
System.out.println(secondMax);
```

(A) 9
(B) 8
(C) 5
(D) 2

---

### 17. [U4 · 어려움]

다음 재귀 메서드에서 `convert(10, 2)` 의 반환값은?

```java
public static String convert(int n, int base)
{
    if (n < base)
        return "" + n;
    return convert(n / base, base) + (n % base);
}
```

(A) `"2"`
(B) `"10"`
(C) `"0101"`
(D) `"1010"`

---

### 18. [U4 · 어려움]

다음 코드의 출력은?

```java
int[] arr = {3, 1, 4, 1, 5, 9, 2, 6};
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

(A) 8
(B) 10
(C) 11
(D) 12

---

### 19. [U4 · 보통]

다음 코드의 출력은?

```java
int[] arr = {1, 2, 3, 4, 5};
int idx = (arr.length - 1 + 3) % arr.length;
System.out.println(arr[idx]);
```

(A) 3
(B) 4
(C) 1
(D) 5

---

### 20. [U4 · 어려움]

다음 코드의 출력은?

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(3);
list.add(1);
list.add(4);
list.add(1);
list.add(5);

// Bubble sort one pass
for (int i = 0; i < list.size() - 1; i++)
{
    if (list.get(i) > list.get(i + 1))
    {
        int temp = list.get(i);
        list.set(i, list.get(i + 1));
        list.set(i + 1, temp);
    }
}
System.out.println(list);
```

(A) `[3, 1, 1, 4, 5]`
(B) `[1, 1, 3, 4, 5]`
(C) `[1, 3, 4, 1, 5]`
(D) `[1, 3, 1, 4, 5]`

---

### 21. [U4 · 보통]

다음 코드의 출력은?

```java
int[][] grid = {{1, 1, 1},
                {2, 2, 2},
                {3, 3, 3}};
int total = 0;
for (int r = 0; r < grid.length; r++)
{
    total += grid[r][0] * grid[0].length;
}
System.out.println(total);
```

(A) 9
(B) 6
(C) 18
(D) 12

---

# Section II: Free Response (2 Questions | 30 Minutes)

**지시사항:** Write your solutions in Java. You may assume all necessary imports.

---

## Question 1: ScoreProcessor (7 Points)

다음 `ScoreProcessor` 클래스는 정렬된 정수 배열을 처리하는 메서드를 제공합니다.

```java
public class ScoreProcessor
{
    /** Returns the median of a sorted array.
     *  If the array has an odd number of elements, returns the middle element.
     *  If even, returns the average of the two middle elements.
     *
     *  Examples:
     *    getMedian({1, 3, 5}) returns 3.0
     *    getMedian({2, 4, 6, 8}) returns 5.0
     *    getMedian({10}) returns 10.0
     *    getMedian({1, 2}) returns 1.5
     *
     *  Precondition: scores is sorted in ascending order, length >= 1.
     */
    public static double getMedian(int[] scores)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a new array containing only the elements of scores
     *  that are between low and high (inclusive).
     *
     *  Examples:
     *    removeOutliers({1, 5, 10, 50, 100}, 5, 50)
     *      returns {5, 10, 50}
     *    removeOutliers({3, 7, 9}, 1, 10)
     *      returns {3, 7, 9}
     *    removeOutliers({1, 2, 3}, 5, 10)
     *      returns {} (empty array)
     *
     *  Precondition: scores is not null, low <= high.
     */
    public static int[] removeOutliers(int[] scores, int low, int high)
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `getMedian` method.

### Part (b)

Complete the `removeOutliers` method. You must return a new array of the correct size.

---

## Question 2: Playlist (6 Points)

음악 재생 목록을 관리하는 `Playlist` 클래스를 작성하세요. `Song` 클래스가 별도로 제공됩니다.

```java
public class Song
{
    /** Returns the song's title. */
    public String getTitle() { /* implementation not shown */ }

    /** Returns the song's artist. */
    public String getArtist() { /* implementation not shown */ }

    /** Returns the song's duration in minutes. */
    public int getDuration() { /* implementation not shown */ }
}
```

다음 정보와 기능을 가지는 `Playlist` 클래스를 완성하세요.

| 항목 | 설명 |
|------|------|
| `name` | 재생목록 이름 (`String`). 생성 시 설정, 변경 불가. |
| `songs` | 노래 목록 (`ArrayList<Song>`). 생성 시 빈 리스트. |
| `Playlist(String name)` | 생성자. |
| `addSong(Song s)` | 노래를 목록 끝에 추가. |
| `removeSong(String title)` | 주어진 제목과 일치하는 **첫 번째** 노래를 제거. 제거 성공 시 `true`, 없으면 `false`. |
| `getTotalDuration()` | 모든 노래의 재생 시간 합(분). |
| `shuffle()` | 마지막 노래를 0 이상 `songs.size()-1` 미만의 랜덤 인덱스 위치에 삽입. 크기 1 이하이면 아무 동작 안 함. `(int)(Math.random() * (songs.size() - 1))` 사용. |
| `toString()` | `"Playlist: [name] ([size] songs, [duration] min)"` 형식. 예: `"Playlist: Chill (5 songs, 23 min)"` |

---
---

# 정답 및 채점

## Section I 정답표

| # | 정답 | Unit | 난이도 | 해설 |
|---|------|------|--------|------|
| 1 | B | U1 | 쉬움 | `10 / 4` = 2 (int 나눗셈). int 2를 double에 대입 → 2.0. |
| 2 | B | U1 | 보통 | `Math.random()` → [0.0, 1.0). `*6` → [0.0, 6.0). `(int)` → 0~5. `+1` → 1~6. |
| 3 | D | U1 | 어려움 | `b = a` (5→5.0). `c = (int) b` (5.0→5). `a = a + 1` (6). b와 c는 복사본이므로 변경 없음. `6 5.0 5`. |
| 4 | A | U2 | 쉬움 | `equals`는 대소문자 구분. `"HELLO" != "hello"` → `false`. `"H".equals("H")` → `true`. |
| 5 | D | U2 | 보통 | n: 1→2→4→8→16. 16≤16이므로 다음 반복: 16 출력, n=32. 32>16 종료. 출력: `1 2 4 8 16`. |
| 6 | A | U2 | 어려움 | parts = {"ab","cd","ef"}. 역순 연결: `"ef cd ab"`. |
| 7 | C | U2 | 보통 | 대문자이면서 공백 아닌 것: 'H', 'W' → 2개. |
| 8 | D | U2 | 어려움 | `add(3, 5)`: int 버전 → 8. `add(3.0, 5)`: double 버전 → 3.0 + 5 + 0.5 = 8.5. |
| 9 | C | U2 | 어려움 | r=1: c=1,2,3 → r+c=2,3,4 → 모두 ≤4 → `"***\n"`. r=2: c=1(3≤4→*), c=2(4≤4→*), c=3(5>4→ ) → `"** \n"`. r=3: c=1(4≤4→*), c=2(5>4→ ), c=3(6>4→ ) → `"*  \n"`. |
| 10 | A | U3 | 보통 | `&&`가 `\|\|`보다 우선. `(false && true) \|\| true` = `false \|\| true` = `true`. x+y=10>9. |
| 11 | B | U3 | 어려움 | `(true \|\| true) && !(true && true)` = `true && false` = `false`. XOR: 같으면 false. |
| 12 | C | U3 | 어려움 | `a \|\| !b`: (T,T)→T, (T,F)→T, (F,T)→F, (F,F)→T. 3가지. |
| 13 | B | U4 | 쉬움 | val/10: 10→1, 20→2, 30→3, 40→4. `freq[2]` = 1 (val=20일 때). |
| 14 | A | U4 | 보통 | 각 요소를 자신+자신으로 set. `[xx, yy, zz]`. |
| 15 | C | U4 | 어려움 | 반대각선: i=0: grid[0][3]=4, i=1: grid[1][2]=7, i=2: grid[2][1]=10. 합 = 4+7+10 = 21. |
| 16 | B | U4 | 보통 | val=5: max=5. val=2: 2<5. val=8: max=8, secondMax=5. val=1: 1<5. val=9: max=9, secondMax=8. → 8. |
| 17 | D | U4 | 어려움 | `convert(10, 2)` = `convert(5, 2) + "0"` = `convert(2, 2) + "1" + "0"` = `convert(1, 2) + "0" + "1" + "0"` = `"1" + "0" + "1" + "0"` = `"1010"`. |
| 18 | A | U4 | 어려움 | 역전쌍 세기. i=0(3): 3>1,3>1,3>2 → 3. i=1(1): 0. i=2(4): 4>1,4>2 → 2. i=3(1): 0. i=4(5): 5>2 → 1. i=5(9): 9>2,9>6 → 2. 총: 3+0+2+0+1+2 = 8. |
| 19 | A | U4 | 보통 | `(5 - 1 + 3) % 5` = `7 % 5` = 2. `arr[2]` = 3. |
| 20 | D | U4 | 어려움 | 한 번의 버블 소트 패스: (3,1)→swap→[1,3,4,1,5]. (3,4)→OK. (4,1)→swap→[1,3,1,4,5]. (4,5)→OK. 결과: [1,3,1,4,5]. |
| 21 | C | U4 | 보통 | 각 행의 첫 요소 × 열 수: 1*3 + 2*3 + 3*3 = 3+6+9 = 18. |

### Section I 최종 정답

| # | 정답 |
|---|------|
| 1 | B |
| 2 | B |
| 3 | D |
| 4 | A |
| 5 | D |
| 6 | A |
| 7 | C |
| 8 | D |
| 9 | C |
| 10 | A |
| 11 | B |
| 12 | C |
| 13 | B |
| 14 | A |
| 15 | C |
| 16 | B |
| 17 | D |
| 18 | A |
| 19 | A |
| 20 | D |
| 21 | C |

---

## Section II 채점기준

### Q1: ScoreProcessor (7점)

#### Part (a) — `getMedian` (4점)

**모범 답안:**
```java
public static double getMedian(int[] scores)
{
    int mid = scores.length / 2;
    if (scores.length % 2 == 1)
    {
        return (double) scores[mid];
    }
    else
    {
        return (scores[mid - 1] + scores[mid]) / 2.0;
    }
}
```

| 점수 | 기준 |
|------|------|
| +1 | 중간 인덱스 올바르게 계산 |
| +1 | 홀수 길이: 중간 요소 반환 |
| +1 | 짝수 길이: 두 중간 요소의 평균 반환 |
| +1 | double로 올바르게 반환 (2.0으로 나누기) (algorithm point) |

**감점 사항:**
- 짝수 길이에서 int 나눗셈 (2로 나눔): -1
- 인덱스 off-by-one: -1

---

#### Part (b) — `removeOutliers` (3점)

**모범 답안:**
```java
public static int[] removeOutliers(int[] scores, int low, int high)
{
    int count = 0;
    for (int s : scores)
    {
        if (s >= low && s <= high)
            count++;
    }

    int[] result = new int[count];
    int idx = 0;
    for (int s : scores)
    {
        if (s >= low && s <= high)
        {
            result[idx] = s;
            idx++;
        }
    }
    return result;
}
```

| 점수 | 기준 |
|------|------|
| +1 | 범위 내 요소 개수를 먼저 세기 (또는 ArrayList 사용) |
| +1 | 올바른 크기의 새 배열 생성 |
| +1 | 범위 내 요소만 복사하여 반환 |

**감점 사항:**
- 원본 배열 수정: -1
- 배열 크기 잘못 (빈 칸 남음): -1

---

### Q2: Playlist (6점)

**모범 답안:**
```java
public class Playlist
{
    private String name;
    private ArrayList<Song> songs;

    public Playlist(String name)
    {
        this.name = name;
        this.songs = new ArrayList<Song>();
    }

    public void addSong(Song s)
    {
        songs.add(s);
    }

    public boolean removeSong(String title)
    {
        for (int i = 0; i < songs.size(); i++)
        {
            if (songs.get(i).getTitle().equals(title))
            {
                songs.remove(i);
                return true;
            }
        }
        return false;
    }

    public int getTotalDuration()
    {
        int total = 0;
        for (Song s : songs)
        {
            total += s.getDuration();
        }
        return total;
    }

    public void shuffle()
    {
        if (songs.size() <= 1)
            return;
        int pos = (int)(Math.random() * (songs.size() - 1));
        Song last = songs.remove(songs.size() - 1);
        songs.add(pos, last);
    }

    public String toString()
    {
        return "Playlist: " + name + " (" + songs.size()
               + " songs, " + getTotalDuration() + " min)";
    }
}
```

| 점수 | 기준 |
|------|------|
| +1 | `private` 인스턴스 변수 + 생성자 (빈 ArrayList 초기화) |
| +1 | `addSong` + `removeSong` (첫 번째 일치만 제거, boolean 반환) |
| +1 | `getTotalDuration` (전체 합) |
| +1 | `shuffle` (마지막 노래를 랜덤 위치에 삽입, 크기 1 이하 처리) |
| +1 | `toString` 형식 일치 |
| +1 | 전체 클래스 구조 올바름 (algorithm point) |

**감점 사항:**
- `private` 누락: -1
- `removeSong`에서 모든 일치 제거 (첫 번째만이어야 함): -1
- `shuffle`에서 크기 1 이하 체크 누락: -1

---

## 점수 해석

| 총점 (34점 만점) | 예상 AP 점수 | 설명 |
|-----------------|-------------|------|
| 28–34 | **5** | 목표 달성. 실전에서도 5점 가능성 높음. |
| 21–27 | **4** | 기본기 탄탄하나 고난이도 문제에서 실수. 코드 tracing 연습 필요. |
| 14–20 | **3** | 핵심 개념은 이해하나 적용력 부족. Unit별 약점 집중 보완. |
| 0–13 | — | 추가 학습 필요. 기본 개념부터 재점검 권장. |
