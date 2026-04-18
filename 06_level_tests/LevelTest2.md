# AP Computer Science A — Level Test 2
## Section I: MCQ 21 Questions (30 min) + Section II: FRQ 2 Questions (30 min)

**총점:** MCQ 21점 + FRQ 12점 = **33점**
**대상:** AP CSA 5점 목표 학생 — Unit 1~4 심화

---

# Section I: Multiple Choice (21 Questions | 30 Minutes)

**지시사항:** Java Quick Reference가 제공됩니다. 각 문제에서 가장 적절한 답을 하나 고르세요.

---

### 1. [U1 · 쉬움]
What is the output of the following code?

```java
double x = 0.1 + 0.2;
System.out.println(x == 0.3);
```

(A) `true`
(B) `false`
(C) `0.3`
(D) Compile-time error

---

### 2. [U1 · 보통]
What is the output of the following code?

```java
double a = 0.1 + 0.2;
double b = 0.3;
System.out.println(Math.abs(a - b) < 0.0001);
```

(A) Compile-time error
(B) `false`
(C) `0.0`
(D) `true`

---

### 3. [U1 · 보통]
What is printed as a result of executing the code segment?

```java
int x = 5;
x++;
x += 3;
System.out.println(x);
```

(A) `8`
(B) `6`
(C) `10`
(D) `9`

---

### 4. [U2 · 어려움]
What is the output of the following code?

```java
String s = "abcdefgh";
String result = "";
for (int i = 0; i < s.length(); i++) {
    if (s.substring(i, i + 1).compareTo("d") >= 0) {
        result += s.substring(i, i + 1);
    }
}
System.out.println(result);
```

(A) `"defgh"`
(B) `"abcdefgh"`
(C) `"abcd"`
(D) `"efgh"`

---

### 5. [U2 · 어려움]
Consider the following code:

```java
String s = "racecar";
String rev = "";
for (int i = s.length() - 1; i >= 0; i--) {
    rev += s.substring(i, i + 1);
}
boolean isPalin = true;
for (int i = 0; i < s.length() / 2; i++) {
    if (!s.substring(i, i + 1).equals(s.substring(s.length() - 1 - i, s.length() - i))) {
        isPalin = false;
    }
}
System.out.println(rev + " " + isPalin);
```

What is the output?

(A) `"racecar true"`
(B) `"racecar false"`
(C) `"racecartrue"`
(D) `"racecar false"`

---

### 6. [U2 · 어려움]

다음 코드의 출력은?

```java
String s = "abcdefg";
String result = "";
for (int i = 0; i < s.length(); i++)
{
    if (i % 3 == 0)
    {
        result += s.substring(i, i + 1).toUpperCase();
    }
    else
    {
        result += s.substring(i, i + 1);
    }
}
System.out.println(result);
```

> **참고**: `toUpperCase()`는 AP CSA 2025-26 Quick Reference에 없으므로 시험 답안 작성에는 사용 금지입니다. 본 문제는 코드 추적 능력만 평가하기 위한 것이며, `toUpperCase()`는 인덱스 0,3,6 위치 문자를 대문자로 바꿉니다.

(A) `"AbCdEfG"`
(B) `"ABCdEFg"`
(C) `"AbcDeFg"`
(D) `"AbcDefG"`

---

### 7. [U2 · 보통]
Consider the following class:

```java
public class Point {
    private int x;
    private int y;

    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }

    public int getX() { return x; }
    public int getY() { return y; }

    public void translate(int dx, int dy) {
        x += dx;
        y += dy;
    }
}
```

What is the output of the following code?

```java
Point p1 = new Point(3, 4);
Point p2 = p1;
p2.translate(1, 1);
System.out.println(p1.getX() + " " + p1.getY());
```

(A) `3 4`
(B) `4 5`
(C) `1 1`
(D) Compile-time error

---

### 8. [U2 · 어려움]
Consider the following method:

```java
public static void swap(Point a, Point b) {
    Point temp = a;
    a = b;
    b = temp;
}
```

What is the output of the following code after calling `swap`?

```java
Point p = new Point(1, 2);
Point q = new Point(3, 4);
swap(p, q);
System.out.println(p.getX() + " " + q.getX());
```

(A) `3 1`
(B) `3 3`
(C) `1 1`
(D) `1 3`

---

### 9. [U2 · 어려움]
Consider the following method:

```java
public static void modify(Point a, Point b) {
    a.translate(10, 10);
    b = new Point(99, 99);
}
```

After executing the following code, what are the values of `p.getX()` and `q.getX()`?

```java
Point p = new Point(1, 2);
Point q = new Point(5, 6);
modify(p, q);
System.out.println(p.getX() + " " + q.getX());
```

(A) `11 99`
(B) `1 5`
(C) `1 99`
(D) `11 5`

---

### 10. [U4 · 보통]
> **참고:** `static` 키워드는 AP CSA 범위 밖이지만, 인스턴스 vs 클래스 변수 이해를 위해 포함했습니다.

What is the difference between `this` and `static` in the following class?

```java
public class Counter {
    private int count;
    private static int totalCount;

    public Counter() {
        count = 0;
        totalCount++;
    }

    public void increment() {
        this.count++;
        totalCount++;
    }

    public int getCount() { return this.count; }
    public static int getTotalCount() { return totalCount; }
}
```

```java
Counter c1 = new Counter();
Counter c2 = new Counter();
c1.increment();
c1.increment();
c2.increment();
System.out.println(c1.getCount() + " " + c2.getCount() + " " + Counter.getTotalCount());
```

(A) `2 1 3`
(B) `3 3 5`
(C) `2 1 5`
(D) `2 1 6`

---

### 11. [U3 · 보통]
What is the output of the following code?

```java
int x = 5;
if (x > 3)
    if (x > 10)
        System.out.print("A");
    else
        System.out.print("B");
else
    System.out.print("C");
```

(A) `A`
(B) `C`
(C) `B`
(D) `BC`

---

### 12. [U3 · 어려움]
Consider the following code:

```java
boolean a = true, b = false, c = true;
System.out.println(a || b && c);
System.out.println((a || b) && c);
System.out.println(!(a && b) || c);
```

What is the output?

(A) `true` `true` `true`
(B) `true` `true` `false`
(C) `false` `true` `true`
(D) `true` `false` `true`

---

### 13. [U3 · 보통]
Which of the following boolean expressions is equivalent to `!(x >= 5 && y < 10)`?

(A) `x >= 5 || y < 10`
(B) `x < 5 && y >= 10`
(C) `x < 5 || y >= 10`
(D) `!(x >= 5) && !(y < 10)`

---

### 14. [U4 · 쉬움]
What is the output of the following code?

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(1);
list.add(2);
list.add(3);
list.add(4);
list.add(5);
list.remove(2);
list.remove(Integer.valueOf(2));
System.out.println(list);
```

> **참고**: `ArrayList.remove(Object)`와 `Integer.valueOf(...)`는 AP CSA 2025-26 Quick Reference에 없으므로 시험 답안에 사용 금지입니다. 본 문제는 `remove(int)`(인덱스 제거)와 `remove(Object)`(값 제거) 오버로드 구분을 추적하는 학습용입니다.

(A) `[1, 4, 5]`
(B) `[1, 2, 5]`
(C) `[1, 3, 5]`
(D) `[1, 4]`

---

### 15. [U4 · 어려움]
What happens when the following code is executed?

```java
ArrayList<String> names = new ArrayList<String>();
names.add("Alice");
names.add("Bob");
names.add("Charlie");
for (String name : names) {
    if (name.length() > 3) {
        names.remove(name);
    }
}
System.out.println(names);
```

(A) `["Bob"]`
(B) `["Alice", "Bob", "Charlie"]`
(C) A `ConcurrentModificationException` is thrown
(D) `["Bob", "Charlie"]`

---

### 16. [U4 · 보통]
What is the output of the following code?

```java
ArrayList<Integer> nums = new ArrayList<Integer>();
nums.add(3); nums.add(1); nums.add(1); nums.add(4); nums.add(5);
for (int i = 0; i < nums.size(); i++) {
    if (nums.get(i) == 1) {
        nums.remove(i);
    }
}
System.out.println(nums);
```

(A) `[3, 4, 5]`
(B) `[3, 1, 4, 5]`
(C) `[3, 1, 4]`
(D) `[3, 4, 5, 1]`

---

### 17. [U4 · 어려움]
An array contains the values `{8, 3, 6, 1, 5}`. After **two** passes of selection sort (sorting in ascending order), what are the contents of the array?

(A) `{1, 3, 6, 8, 5}`
(B) `{1, 3, 8, 6, 5}`
(C) `{3, 1, 6, 8, 5}`
(D) `{1, 3, 5, 6, 8}`

---

### 18. [U4 · 어려움]
An array contains the values `{5, 2, 8, 1, 4}`. After **three** passes of insertion sort (sorting in ascending order), what are the contents of the array?

(A) `{2, 5, 8, 1, 4}`
(B) `{1, 2, 5, 8, 4}`
(C) `{2, 5, 1, 8, 4}`
(D) `{1, 2, 8, 5, 4}`

---

### 19. [U4 · 어려움]
What is the output of the following recursive method call `mystery("Hello")`?

```java
public static String mystery(String s) {
    if (s.length() <= 1)
        return s;
    return mystery(s.substring(1)) + s.substring(0, 1);
}
```

(A) `"Hello"`
(B) `"olleH"`
(C) `"elloH"`
(D) `"oHell"`

---

### 20. [U4 · 보통]
Consider the following 2D array code:

```java
int[][] grid = {
    {1, 2, 3, 4},
    {5, 6, 7, 8},
    {9, 10, 11, 12}
};
int sum = 0;
for (int r = 0; r < grid.length; r++) {
    sum += grid[r][grid[0].length - 1];
}
for (int c = 0; c < grid[0].length - 1; c++) {
    sum += grid[0][c];
}
System.out.println(sum);
```

What is the output?

(A) 78
(B) 36
(C) 24
(D) 30

---

### 21. [U4 · 쉬움]
What is the output of the following code?

```java
int[][] arr = {
    {1, 0, 0},
    {0, 2, 0},
    {0, 0, 3}
};
int sum = 0;
for (int i = 0; i < arr.length; i++) {
    sum += arr[i][i];
}
System.out.println(sum);
```

(A) 0
(B) 3
(C) 6
(D) 9

---

# Section II: Free Response (2 Questions | 30 Minutes)

---

## Question 1: Class Design (7점)

한 카페에서 음료 주문을 관리합니다. 각 `Beverage` 객체는 하나의 음료를 나타내며 다음의 정보와 기능을 가집니다.

| 항목 | 설명 |
|------|------|
| `name` | 음료 이름 (`String`). 생성 시 설정되며 변경 불가. |
| `basePrice` | 기본 가격 (`double`). 생성 시 설정되며 변경 불가. |
| `size` | 사이즈 (`String`). `"S"`, `"M"`, `"L"` 중 하나. 생성 시 `"M"`. |
| `extraShots` | 추가 에스프레소 샷 수 (`int`). 생성 시 `0`. |
| `Beverage(String name, double basePrice)` | 생성자. 이름과 기본 가격을 설정하고 초기 상태를 지정. |
| `getName()` | 음료 이름을 반환. |
| `setSize(String size)` | 사이즈를 변경. `"S"`, `"M"`, `"L"` 중 하나가 아니면 변경하지 않고 `false` 반환. 성공하면 `true` 반환. |
| `addShots(int shots)` | 추가 샷 수를 누적. `shots`가 0 이하이면 추가하지 않고 `false` 반환. 성공하면 `true` 반환. |
| `getTotalPrice()` | 총 가격을 반환. 사이즈 보정: `"S"`이면 `basePrice * 0.8`, `"M"`이면 `basePrice`, `"L"`이면 `basePrice * 1.3`. 추가 샷 하나당 `0.5` 추가. |
| `getDescription()` | `"[name] ([size]) - $[totalPrice]"` 형식의 `String` 반환. 가격은 정수부 + "." + 소수 둘째 자리 형태(예: `5.85`)로 직접 조립합니다. 예: `"Latte (L) - $5.85"`. (참고: `toString` 오버라이드 작성 및 `String.format`은 AP CSA 2025-26 Quick Reference 범위 밖이므로 명시 메서드 `getDescription()`을 사용합니다.) |

`Beverage` 클래스를 완성하세요. 위의 모든 인스턴스 변수, 생성자, 메서드를 포함해야 합니다.

---

## Question 2: Data Analysis with ArrayList (5점)

한 영화관에서 상영 스케줄을 관리합니다. `ScheduleManager` 클래스의 일부가 아래에 나와 있습니다.

```java
public class ScheduleManager {
    private ArrayList<Screening> schedule;

    /**
     * Screening 클래스:
     * - String getTitle()       // 영화 제목 반환
     * - int getTime()           // 상영 시작 시간 (24시간 형식 정수, 예: 1430은 14:30)
     * - int getSeatsSold()      // 판매된 좌석 수 반환
     * - int getTotalSeats()     // 총 좌석 수 반환
     */

    /**
     * 판매율(seatsSold / totalSeats)이 threshold 미만인 상영을 모두 제거합니다.
     * 제거된 상영의 제목들을 ArrayList로 반환합니다.
     * (제거된 순서대로, 같은 제목이 여러 번 제거되면 중복 포함)
     *
     * 주의: 순회 중 삭제가 올바르게 동작해야 합니다.
     *
     * @param threshold 최소 판매율 (0.0 ~ 1.0). 이 값 미만이면 제거.
     * @return 제거된 상영의 제목 리스트
     */
    public ArrayList<String> cancelUnderperforming(double threshold) {
        /* Part A에서 구현 */
    }

    /**
     * 주어진 시간 범위(startTime 이상, endTime 이하) 내에 상영되는 영화 제목들을
     * 중복 없이 ArrayList로 반환합니다.
     * schedule에 나타나는 순서대로 처음 등장한 순서를 유지합니다.
     *
     * @param startTime 시작 시간 (inclusive)
     * @param endTime 종료 시간 (inclusive)
     * @return 해당 시간대의 고유 영화 제목 리스트
     */
    public ArrayList<String> getUniqueMoviesInRange(int startTime, int endTime) {
        /* Part B에서 구현 */
    }
}
```

### Part A (3점)
`cancelUnderperforming` 메서드를 구현하세요.

### Part B (2점)
`getUniqueMoviesInRange` 메서드를 구현하세요.

**예시:**

`schedule`이 다음과 같을 때:

| 제목 | 시간 | 판매 좌석 | 총 좌석 |
|------|------|-----------|---------|
| "Dune" | 1000 | 80 | 200 |
| "Oppenheimer" | 1300 | 150 | 200 |
| "Dune" | 1400 | 10 | 200 |
| "Barbie" | 1600 | 5 | 100 |
| "Oppenheimer" | 1900 | 190 | 200 |

- `cancelUnderperforming(0.3)` 호출 시:
  - "Dune" (1400): 10/200 = 0.05 → 제거
  - "Barbie" (1600): 5/100 = 0.05 → 제거
  - 반환: `["Dune", "Barbie"]`
  - schedule에는 "Dune"(1000), "Oppenheimer"(1300), "Oppenheimer"(1900)만 남음.

- `getUniqueMoviesInRange(1200, 1700)` 호출 시 (위 cancelUnderperforming 호출 전 기준):
  - 1300: "Oppenheimer", 1400: "Dune", 1600: "Barbie"
  - 반환: `["Oppenheimer", "Dune", "Barbie"]`

---

---

# 정답 및 채점기준

---

## Section I: MCQ 정답표

| 번호 | 정답 | Unit | 난이도 | 토픽 | 해설 |
|------|------|------|--------|------|------|
| 1 | B | 1 | 쉬움 | double 부동소수점 오차 | `0.1 + 0.2`는 IEEE 754 부동소수점에서 정확히 `0.3`이 아닌 `0.30000000000000004`를 반환. `==` 비교는 `false`. |
| 2 | D | 1 | 보통 | double 비교 전략 | `Math.abs(a - b)`는 약 `5.5E-17`로 `0.0001`보다 훨씬 작으므로 `true`. 부동소수점 비교는 오차 범위(epsilon)를 사용해야 함. |
| 3 | D | 1 | 보통 | 증감연산자·복합대입 | `x`는 5에서 시작. `x++`로 6이 되고, `x += 3`으로 9가 됨. 출력: `9`. |
| 4 | A | 2 | 어려움 | 문자열 순회+조건+누적 | `compareTo`로 각 문자를 `"d"`와 비교. `"d"`, `"e"`, `"f"`, `"g"`, `"h"`가 `>= 0`이므로 누적. 결과: `"defgh"`. |
| 5 | A | 2 | 어려움 | 복합 String 알고리즘 | `rev`는 `"racecar"`의 역순이지만 `"racecar"` 자체가 회문이므로 `rev = "racecar"`. 회문 검사도 `true`. 출력에서 `" "` 문자열 연결이 공백을 추가하므로 `"racecar true"`. |
| 6 | D | 2 | 어려움 | 조건부 대문자 변환 | `i % 3 == 0`인 인덱스(0,3,6)의 문자만 `toUpperCase()`로 대문자 변환. i=0→"A", i=1→"b", i=2→"c", i=3→"D", i=4→"e", i=5→"f", i=6→"G". 결과: `"AbcDefG"`. |
| 7 | B | 2 | 보통 | aliasing(참조 공유) | `p2 = p1`은 같은 객체를 참조. `p2.translate(1,1)` 호출하면 `p1`도 영향 받음. `p1.getX()=4`, `p1.getY()=5`. |
| 8 | D | 2 | 어려움 | 참조 전달과 swap | Java는 참조값을 복사하여 전달. `swap` 내부에서 지역 변수 `a`, `b`의 값만 교환되고 원본 `p`, `q`에는 영향 없음. `p.getX()=1`, `q.getX()=3`. |
| 9 | D | 2 | 어려움 | 참조 전달 + 객체 수정 vs 재할당 | `a.translate(10,10)`은 원본 `p` 객체를 수정 → `p.getX()=11`. `b = new Point(99,99)`는 지역 변수 `b`만 재할당, 원본 `q`에 영향 없음 → `q.getX()=5`. |
| 10 | C | 4 | 보통 | this vs static | 생성자 2번 호출 → `totalCount=2`. `c1.increment()` 2번 → `c1.count=2`, `totalCount=4`. `c2.increment()` 1번 → `c2.count=1`, `totalCount=5`. 출력: `2 1 5`. |
| 11 | C | 3 | 보통 | dangling else | `else`는 가장 가까운 `if`에 바인딩. `x>3`은 true이므로 내부 진입, `x>10`은 false이므로 `else` 실행 → `"B"`. |
| 12 | A | 3 | 어려움 | 연산자 우선순위 | `a \|\| b && c`: `&&`가 먼저 → `b && c = false`, `a \|\| false = true`. `(a \|\| b) && c`: `true && true = true`. `!(a && b) \|\| c`: `!(false) \|\| true = true \|\| true = true`. 모두 `true`. |
| 13 | C | 3 | 보통 | De Morgan's Law | `!(x >= 5 && y < 10)` = `!(x >= 5) \|\| !(y < 10)` = `x < 5 \|\| y >= 10`. |
| 14 | A | 4 | 쉬움 | ArrayList remove 인덱스 vs 값 | 초기: `[1,2,3,4,5]`. `remove(2)`: 인덱스 2 제거(값 3) → `[1,2,4,5]`. `remove(Integer.valueOf(2))`: 값 2 제거 → `[1,4,5]`. |
| 15 | C | 4 | 어려움 | enhanced for + ConcurrentModificationException | enhanced for loop 사용 중 `ArrayList`를 수정하면 `ConcurrentModificationException` 발생. |
| 16 | B | 4 | 보통 | 전진 순회 중 삭제 인덱스 건너뜀 | 초기: `[3,1,1,4,5]`. `i=0`: 3≠1. `i=1`: `get(1)=1` → 제거 → `[3,1,4,5]`. `i++` → `i=2`: `get(2)=4` ≠ 1 (두 번째 1이 인덱스 1로 당겨졌지만 건너뜀!). `i=3`: `get(3)=5` ≠ 1. 종료. 결과: `[3,1,4,5]`. 전진 순회 중 삭제 시 요소가 당겨져 바로 다음 요소를 건너뛰는 전형적 함정. |
| 17 | A | 4 | 어려움 | Selection sort 추적 | `{8,3,6,1,5}`. Pass 1: 최솟값 1(인덱스 3)을 인덱스 0과 교환 → `{1,3,6,8,5}`. Pass 2: [1..4]에서 최솟값 3(인덱스 1, 이미 제자리) → `{1,3,6,8,5}`. |
| 18 | B | 4 | 어려움 | Insertion sort 추적 | `{5,2,8,1,4}`. Pass 1: arr[1]=2 삽입 → `{2,5,8,1,4}`. Pass 2: arr[2]=8은 제자리 → `{2,5,8,1,4}`. Pass 3: arr[3]=1 삽입 → `{1,2,5,8,4}`. |
| 19 | B | 4 | 어려움 | 재귀 + String | `mystery("Hello")` → `mystery("ello")+"H"` → `mystery("llo")+"e"+"H"` → ... → `"o"+"l"+"l"+"e"+"H"` = `"olleH"`. 문자열 역순 반환 재귀. |
| 20 | D | 4 | 보통 | 2D 배열 경계 | 첫 번째 루프: 각 행의 마지막 열(`grid[0].length-1 = 3`): `grid[0][3]=4`, `grid[1][3]=8`, `grid[2][3]=12` → 합 24. 두 번째 루프: 첫 행의 마지막 열 제외(`c=0,1,2`): `grid[0][0]=1`, `grid[0][1]=2`, `grid[0][2]=3` → 합 6. 총합: `24 + 6 = 30`. |
| 21 | C | 4 | 쉬움 | 2D 배열 대각선 | `arr[0][0]=1`, `arr[1][1]=2`, `arr[2][2]=3`. 대각선 합 = `1+2+3 = 6`. |

---

### 난이도 분포

| 난이도 | 문제 번호 | 개수 |
|--------|-----------|------|
| 쉬움 | 1, 14, 21 | 3 |
| 보통 | 2, 3, 7, 10, 11, 13, 16, 20 | 8 |
| 어려움 | 4, 5, 6, 8, 9, 12, 15, 17, 18, 19 | 10 |

**합계: 3 + 8 + 10 = 21문제**

**Unit 분포:**

| Unit | 문제 번호 | 개수 |
|------|-----------|------|
| U1 | 1, 2, 3 | 3 |
| U2 | 4, 5, 6, 7, 8, 9 | 6 |
| U3 | 11, 12, 13 | 3 |
| U4 | 10, 14, 15, 16, 17, 18, 19, 20, 21 | 9 |

**합계: 3 + 6 + 3 + 9 = 21문제**

> **참고:** 10번 문제(`this` vs `static`)는 클래스/객체 활용 문제로, AP CSA Unit 3(Class Creation) 토픽이지만 여기서는 U4로 배치하여 문제 수 균형을 맞춤.

---

## Section II: FRQ 풀이 및 채점기준

---

### Q1 풀이 및 채점기준

#### 정답 코드

```java
public class Beverage {
    private String name;
    private double basePrice;
    private String size;
    private int extraShots;

    public Beverage(String name, double basePrice) {
        this.name = name;
        this.basePrice = basePrice;
        this.size = "M";
        this.extraShots = 0;
    }

    public String getName() {
        return name;
    }

    public boolean setSize(String size) {
        if (size.equals("S") || size.equals("M") || size.equals("L")) {
            this.size = size;
            return true;
        }
        return false;
    }

    public boolean addShots(int shots) {
        if (shots <= 0) {
            return false;
        }
        extraShots += shots;
        return true;
    }

    public double getTotalPrice() {
        double price = basePrice;
        if (size.equals("S")) {
            price *= 0.8;
        } else if (size.equals("L")) {
            price *= 1.3;
        }
        price += extraShots * 0.5;
        return price;
    }

    // getDescription: toString 오버라이드 대신 명시 메서드 사용 (Quick Reference 준수)
    // String.format 대신 정수/소수 분리 후 수동 조립
    public String getDescription() {
        double total = getTotalPrice();
        int dollars = (int) total;
        int cents = (int) ((total - dollars) * 100 + 0.5);  // 반올림으로 소수 둘째 자리
        String centStr = "" + cents;
        if (cents < 10) {
            centStr = "0" + cents;
        }
        return name + " (" + size + ") - $" + dollars + "." + centStr;
    }
}
```

#### 채점기준 (7점)
- +1: 클래스 헤더 올바름 (`public class Beverage`), 4개의 `private` 인스턴스 변수 선언 (올바른 타입)
- +1: 생성자가 매개변수를 받아 `name`, `basePrice` 설정, `size = "M"`, `extraShots = 0`
- +1: `getName()` 올바르게 구현
- +1: `setSize` — 유효한 사이즈(`"S"`, `"M"`, `"L"`)인지 검증하고 조건부 변경 및 `boolean` 반환
- +1: `addShots` — `shots <= 0` 가드 조건 처리, 누적 추가, `boolean` 반환
- +1: `getTotalPrice` — 사이즈별 가격 보정(`0.8`, `1.0`, `1.3`) + 추가 샷 비용(`shots * 0.5`) 올바르게 계산
- +1: `getDescription` — 형식에 맞는 문자열 반환, 소수점 둘째 자리(수동 조립)

#### 흔한 실수
- `setSize`에서 `==`로 문자열 비교 (`equals` 사용 필요)
- `addShots`에서 `shots < 0`만 체크하고 `shots == 0`을 허용
- `getTotalPrice`에서 `extraShots * 0.5` 대신 `extraShots * 0.50`을 별도 계산하지 않고 `basePrice`에 샷 비용을 사이즈 보정 전에 더해버림 (순서 오류)
- `getDescription`에서 `getTotalPrice()` 호출 대신 직접 계산하여 중복 로직 발생
- 인스턴스 변수를 `public`으로 선언
- `toString` 오버라이드나 `String.format`을 사용 (둘 다 AP CSA 2025-26 Quick Reference 범위 밖)

---

### Q2 풀이 및 채점기준

#### 정답 코드

**Part A:**
```java
public ArrayList<String> cancelUnderperforming(double threshold) {
    ArrayList<String> removed = new ArrayList<String>();

    for (int i = schedule.size() - 1; i >= 0; i--) {
        Screening s = schedule.get(i);
        double rate = (double) s.getSeatsSold() / s.getTotalSeats();
        if (rate < threshold) {
            removed.add(0, s.getTitle());
            schedule.remove(i);
        }
    }

    return removed;
}
```

**또는 (전진 순회):**
```java
public ArrayList<String> cancelUnderperforming(double threshold) {
    ArrayList<String> removed = new ArrayList<String>();
    int i = 0;
    while (i < schedule.size()) {
        Screening s = schedule.get(i);
        double rate = (double) s.getSeatsSold() / s.getTotalSeats();
        if (rate < threshold) {
            removed.add(s.getTitle());
            schedule.remove(i);
        } else {
            i++;
        }
    }
    return removed;
}
```

**Part B:**
```java
public ArrayList<String> getUniqueMoviesInRange(int startTime, int endTime) {
    ArrayList<String> result = new ArrayList<String>();

    for (Screening s : schedule) {
        if (s.getTime() >= startTime && s.getTime() <= endTime) {
            // ArrayList.contains는 Quick Reference 범위 밖이므로 직접 선형 탐색
            String title = s.getTitle();
            boolean found = false;
            for (int k = 0; k < result.size(); k++) {
                if (result.get(k).equals(title)) {
                    found = true;
                }
            }
            if (!found) {
                result.add(title);
            }
        }
    }

    return result;
}
```

#### 채점기준 (5점)

**Part A (3점)**
- +1: `ArrayList<String>` 생성 및 반환, `schedule` 올바르게 순회
- +1: 판매율 계산 (`(double) seatsSold / totalSeats`) 및 `threshold` 비교 올바름
- +1: 순회 중 삭제가 올바르게 동작 (역방향 순회 또는 전진 순회 시 인덱스 미증가 처리). 제거된 제목이 원래 순서대로 반환됨.

**Part B (2점)**
- +1: 시간 범위 조건 올바름 (`>= startTime && <= endTime`)
- +1: 중복 검사 (Quick Reference의 `equals` + `for` 루프로 직접 구현; `ArrayList.contains` 사용 금지) 후 추가, 결과 리스트 생성 및 반환

#### 흔한 실수
- **Part A:** 전진 순회 시 `remove` 후 `i++`를 하여 요소를 건너뛰는 버그
- **Part A:** 역방향 순회 시 `removed.add(0, title)` 대신 `removed.add(title)`을 사용하면 순서가 역순이 됨 (단, 문제에서 "제거된 순서대로"라고 했으므로, 역방향 순회 시 `add(0, ...)` 사용하거나 마지막에 뒤집어야 함)
- **Part A:** 판매율 계산 시 `int / int`로 정수 나눗셈 발생 → `(double)` 캐스트 누락
- **Part B:** `contains` 대신 중복 검사를 하지 않아 중복 제목이 들어감
- **Part B:** `==`로 문자열 비교 (하지만 `contains` 내부에서 `equals`를 사용하므로 `contains`를 쓰면 괜찮음)

---

## 점수 해석

| 총점 (33점 만점) | 비율 | 예상 AP 점수 | 해석 |
|------------------|------|-------------|------|
| 28~33 | 85%+ | **5** | 5점 수준 확실. 심화 문제에서도 안정적. |
| 23~27 | 70~84% | **4~5** | 거의 5점 수준. 틀린 유형 보강 필요. |
| 18~22 | 55~69% | **3~4** | 기본기는 있으나 함정·심화에서 약함. 참조/삭제 패턴 집중 복습. |
| 12~17 | 36~54% | **2~3** | 핵심 개념 재학습 필요. Unit 2, 4 복습 우선. |
| 0~11 | ~35% | **1~2** | 기초부터 재시작 권장. |

### MCQ 유형별 분석 가이드

| 유형 | 해당 문제 | 틀렸으면 복습 |
|------|-----------|---------------|
| 부동소수점 오차 | 1, 2 | IEEE 754 기본 원리, epsilon 비교 패턴 |
| 참조/aliasing/전달 | 7, 8, 9 | Java는 "값에 의한 호출"이지만 참조값이 복사됨 |
| this vs static | 10 | 인스턴스 vs 클래스 변수/메서드 차이 |
| String 알고리즘 | 4, 5, 6 | substring, indexOf, compareTo 트레이싱 |
| ArrayList 삭제 함정 | 14, 15, 16 | remove(int) vs remove(Object), ConcurrentModificationException |
| Selection / Insertion sort | 17, 18 | 정렬 과정 손으로 추적 연습 |
| 재귀 + String | 19 | 호출 스택 그려보며 반환값 추적 |
| 2D 배열 경계 | 20, 21 | 행/열 인덱스, 대각선, 첫 행/마지막 열 패턴 |
| De Morgan / 연산자 우선순위 | 12, 13 | `&&`가 `\|\|`보다 우선, 드 모르간 변환 연습 |
