# AP Computer Science A — Mock Exam Set 4: Multiple Choice (42 Questions)

**Directions:** Determine the answer to each of the following questions or incomplete statements, using the available space for any necessary scratch work. Then decide which is the best of the choices given and fill in the corresponding circle on the answer sheet. A Java Quick Reference is provided as part of the exam.

> **Theme: Trap Questions**
> Difficulty: Easy 20% (8) / Medium 50% (21) / Hard 30% (13)

---

## Unit 1: Using Objects and Methods (8 Questions)

### Q1.
What is the result of calling `printInfo()`?

```java
public class Dog {
    private String name;
    public static void printInfo() {
        System.out.println(name);
    }
}
```

(A) It prints `null`
(B) It prints an empty string
(C) A compile-time error occurs because a non-static variable is referenced from a static context
(D) A run-time error occurs (NullPointerException)

---

### Q2.
What is printed as a result of executing the code segment?

```java
public class Counter {
    private static int count = 0;
    private int id;
    public Counter() {
        count++;
        id = count;
    }
    public static int getCount() { return count; }
    public int getId() { return id; }
}
```
```java
Counter c1 = new Counter();
Counter c2 = new Counter();
Counter c3 = new Counter();
c2 = null;
System.out.println(Counter.getCount());
```

(A) 2
(B) 3
(C) 0
(D) NullPointerException

---

### Q3.
What is the result of executing the code segment?

```java
String s = null;
System.out.println(s.length());
```

(A) 0
(B) A compile-time error occurs
(C) A run-time error occurs (NullPointerException)
(D) It prints `null`

---

### Q4.
What is printed as a result of executing the code segment?

```java
public class Point {
    private int x;
    private int y;
    public Point(int a, int b) { x = a; y = b; }
    public int getX() { return x; }
    public int getY() { return y; }
}
```
```java
Point p1 = new Point(3, 4);
Point p2 = new Point(3, 4);
System.out.println(p1.getX() == p2.getX() && p1.getY() == p2.getY());
```

(A) `true`
(B) `false`
(C) A compile-time error occurs
(D) A run-time error occurs

---

### Q5.
What is printed as a result of executing the code segment?

```java
public class Foo {
    private int x;
    public Foo(int x) { this.x = x; }
    public static Foo create() {
        Foo f = new Foo(10);
        return f;
    }
    public void change(Foo other) {
        other = new Foo(99);
    }
    public int getX() { return x; }
}
```
```java
Foo a = Foo.create();
Foo b = a;
a.change(b);
System.out.println(b.getX());
```

(A) 99
(B) 10
(C) 0
(D) NullPointerException

---

### Q6.
What is printed as a result of executing the code segment?

```java
public class Mystery {
    private int val;
    public Mystery() { val = 0; }
    public Mystery(int v) { val = v; }
    public static void swap(Mystery a, Mystery b) {
        Mystery temp = a;
        a = b;
        b = temp;
    }
    public int getVal() { return val; }
}
```
```java
Mystery m1 = new Mystery(5);
Mystery m2 = new Mystery(10);
Mystery.swap(m1, m2);
System.out.println(m1.getVal() + " " + m2.getVal());
```

(A) 10 5
(B) 5 10
(C) 5 5
(D) 10 10

---

### Q7.
Consider the following code segment.

```java
String s1 = "Java";
String s2 = new String("Java");
String s3 = s1;

System.out.print(s1 == s2);
System.out.print(" ");
System.out.print(s1 == s3);
System.out.print(" ");
System.out.print(s1.equals(s2));
```

What is printed?

(A) `false false true`
(B) `false true true`
(C) `true true true`
(D) `true false true`

---

### Q8.
Which of the following best describes why the code does not work as intended?

The following code is intended to allow external classes to read the `balance` field.

```java
public class Account {
    public double balance;
    public Account(double b) { balance = b; }
}
```

(A) The `balance` field should be `private` with a `public` getter method for proper encapsulation.
(B) The field type should be `int`, not `double`.
(C) A constructor cannot take a `double` parameter.
(D) The code works correctly and follows best practices.

---

## Unit 2: Selection and Iteration (13 Questions)

### Q9.
What is the range of possible values for `x`?

```java
int x = (int)(Math.random() * 6) + 1;
```

(A) 0 to 5
(B) 0 to 6
(C) 1 to 6
(D) 1 to 7

---

### Q10.
What is the range of possible values for `x`?

```java
int x = (int)(Math.random() * 6 + 1);
```

(A) 1 to 6
(B) 0 to 6
(C) 1 to 7
(D) 0 to 5

---

### Q11.
What is printed as a result of executing the code segment?

```java
double d = 7 / 2;
System.out.println(d);
```

(A) 3.5
(B) 3.0
(C) 3
(D) A compile-time error occurs

---

### Q12.
What is printed as a result of executing the code segment?

```java
int a = 17;
int b = 5;
System.out.println(a / b + " " + a % b);
```

(A) 3.4 2
(B) 3 2
(C) 3.0 2.0
(D) 3 2.0

---

### Q13.
What is printed as a result of executing the code segment?

```java
String s1 = "hello";
String s2 = "hello";
String s3 = new String("hello");
System.out.println((s1 == s2) + " " + (s1 == s3));
```

(A) true true
(B) false false
(C) true false
(D) false true

---

### Q14.
Which of the following best describes the result of executing the code segment?

```java
String a = "apple";
String b = "banana";
System.out.println(a.compareTo(b));
```

(A) It prints 0
(B) It prints a positive integer
(C) It prints a negative integer
(D) It throws an exception

---

### Q15.
### Questions 15-17 refer to the following class.

```java
public class Scoreboard {
    private int[][] scores;

    public Scoreboard(int[][] s) {
        scores = s;
    }

    public double getAverage(int row) {
        int sum = 0;
        for (int c = 0; c < scores[row].length; c++) {
            sum += scores[row][c];
        }
        return (double) sum / scores[row].length;
    }

    public int getHighest() {
        int max = scores[0][0];
        for (int r = 0; r < scores.length; r++) {
            for (int c = 0; c < scores[r].length; c++) {
                if (scores[r][c] > max) {
                    max = scores[r][c];
                }
            }
        }
        return max;
    }

    public int[] ranking() {
        double[] avgs = new double[scores.length];
        int[] rank = new int[scores.length];
        for (int i = 0; i < scores.length; i++) {
            avgs[i] = getAverage(i);
            rank[i] = i;
        }
        for (int i = 0; i < avgs.length - 1; i++) {
            for (int j = i + 1; j < avgs.length; j++) {
                if (avgs[j] > avgs[i]) {
                    double tempD = avgs[i]; avgs[i] = avgs[j]; avgs[j] = tempD;
                    int tempI = rank[i]; rank[i] = rank[j]; rank[j] = tempI;
                }
            }
        }
        return rank;
    }
}
```

What is printed as a result of executing the code segment?

```java
int[][] data = {{80, 90, 70}, {60, 100, 80}};
Scoreboard sb = new Scoreboard(data);
System.out.println(sb.getAverage(0));
```

(A) `80.0`
(B) `80`
(C) `240`
(D) `240.0`

---

### Q16.
What is printed as a result of executing the code segment?

```java
int[][] data = {{80, 90, 70}, {60, 100, 80}};
Scoreboard sb = new Scoreboard(data);
System.out.println(sb.getHighest());
```

(A) `90`
(B) `100`
(C) `80`
(D) `240`

---

### Q17.
What is printed as a result of executing the code segment?

```java
int[][] data = {{70, 70, 70}, {90, 90, 90}, {80, 80, 80}};
Scoreboard sb = new Scoreboard(data);
int[] rank = sb.ranking();
System.out.println(rank[0] + " " + rank[1] + " " + rank[2]);
```

(A) `0 1 2`
(B) `1 2 0`
(C) `2 1 0`
(D) `0 2 1`

---

### Q18.
What is printed as a result of executing the code segment?

```java
boolean a = true;
boolean b = false;
System.out.println(!a || b && a);
```

(A) true
(B) false
(C) A compile-time error occurs
(D) true true

---

### Q19.
What is printed as a result of executing the code segment?

```java
int x = 0;
while (x < 10) {
    x += 3;
}
System.out.println(x);
```

(A) 9
(B) 10
(C) 12
(D) 11

---

### Q20.
What is printed as a result of executing the code segment?

```java
int total = 0;
for (int i = 1; i <= 6; i++) {
    if (i % 3 != 0) {
        total += i;
    }
}
System.out.println(total);
```

(A) 12
(B) 21
(C) 9
(D) 15

---

### Q21.
What is the result of executing the code segment?

```java
int n = 1;
while (n != 50) {
    n += 3;
}
System.out.println(n);
```

(A) 50
(B) 52
(C) The loop runs forever (infinite loop)
(D) 49

---

## Unit 3: Class Creation (6 Questions)

### Q22.
What is printed as a result of executing the code segment?

```java
int[] arr = new int[5];
System.out.println(arr[0]);
```

(A) A compile-time error occurs
(B) 0
(C) null
(D) ArrayIndexOutOfBoundsException

---

### Q23.
What is printed as a result of executing the code segment?

```java
int[][] grid = new int[3][4];
System.out.println(grid.length + " " + grid[0].length);
```

(A) 4 3
(B) 3 4
(C) 12 4
(D) 3 3

---

### Q24.
What is printed as a result of executing the code segment?

```java
int[][] arr = { {1, 2, 3}, {4, 5, 6} };
int sum = 0;
for (int r = 0; r < arr[0].length; r++) {
    for (int c = 0; c < arr.length; c++) {
        sum += arr[c][r];
    }
}
System.out.println(sum);
```

(A) 21
(B) ArrayIndexOutOfBoundsException
(C) 15
(D) 6

---

### Q25.
What is printed as a result of executing the code segment?

```java
String[] names = {"Alice", "Bob", "Carol"};
System.out.println(names.length);
```

(A) 2
(B) 3
(C) A compile-time error occurs because `size()` should be used instead
(D) 0

---

### Q26.
What is the result of executing the code segment?

```java
int[] arr = {10, 20, 30, 40, 50};
for (int i = 0; i <= arr.length; i++) {
    System.out.print(arr[i] + " ");
}
```

(A) 10 20 30 40 50
(B) 10 20 30 40 50 followed by an ArrayIndexOutOfBoundsException
(C) An ArrayIndexOutOfBoundsException occurs and nothing is printed
(D) 10 20 30 40

---

### Q27.
What is printed as a result of executing the code segment?

```java
int[][] grid = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
int sum = 0;
for (int c = 0; c < grid[0].length; c++) {
    sum += grid[grid.length - 1][c];
}
System.out.println(sum);
```

(A) 6
(B) 15
(C) 24
(D) 45

---

## Unit 4: Data Collections (15 Questions)

### Q28.
What is printed as a result of executing the code segment?

```java
ArrayList<Integer> list = new ArrayList<>();
list.add(1);
list.add(2);
list.add(3);
list.remove(1);
System.out.println(list);
```

(A) [1, 3]
(B) [2, 3]
(C) [1, 2]
(D) [1, 2, 3]

---

### Q29.
What is printed as a result of executing the code segment?

```java
ArrayList<Integer> list = new ArrayList<>();
list.add(1);
list.add(2);
list.add(3);
list.remove(Integer.valueOf(1));
System.out.println(list);
```

(A) [2, 3]
(B) [1, 3]
(C) [1, 2]
(D) [1, 2, 3]

---

### Q30.
What is printed as a result of executing the code segment?

```java
ArrayList<String> words = new ArrayList<>();
words.add("cat");
words.add("dog");
words.add("bird");
System.out.println(words.size() + " " + words.get(1));
```

(A) 3 dog
(B) 3 cat
(C) 2 dog
(D) 3 bird

---

### Q31.
What is printed as a result of executing the code segment?

```java
ArrayList<String> list = new ArrayList<>();
list.add("A");
list.add("B");
list.add("C");
list.add("B");
for (int i = 0; i < list.size(); i++) {
    if (list.get(i).equals("B")) {
        list.remove(i);
    }
}
System.out.println(list);
```

(A) [A, C]
(B) [A, C, B]
(C) [A, B, C]
(D) IndexOutOfBoundsException

---

### Q32.
What is returned by the method call `mystery(4)`?

```java
public static int mystery(int n) {
    if (n == 0)
        return 1;
    return 2 * mystery(n - 1);
}
```

(A) 8
(B) 4
(C) 16
(D) StackOverflowError

---

### Q33.
After one pass of selection sort (ascending) on the array `{5, 8, 1, 3, 7}`, what is the array state?

```java
int[] arr = {5, 8, 1, 3, 7};
// One pass: find minimum in arr[0..4], swap with arr[0]
```

(A) {1, 5, 8, 3, 7}
(B) {1, 8, 5, 3, 7}
(C) {5, 1, 8, 3, 7}
(D) {1, 3, 5, 8, 7}

---

### Q34.
What is printed as a result of executing the code segment?

```java
int[][] grid = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
int sum = 0;
for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[0].length; c++) {
        if (r == 0 || r == grid.length - 1 || c == 0 || c == grid[0].length - 1) {
            sum += grid[r][c];
        }
    }
}
System.out.println(sum);
```

(A) 45
(B) 15
(C) 40
(D) 25

---

### Q35.
What is printed as a result of executing the code segment?

```java
ArrayList<Integer> list = new ArrayList<>();
list.add(10);
list.add(20);
list.add(30);
list.add(40);
list.add(1, 15);
list.remove(3);
System.out.println(list.get(2));
```

(A) 30
(B) 20
(C) 15
(D) 40

---

### Q36.
What is the result of calling `mystery(5)`?

```java
public static int mystery(int n) {
    if (n == 0)
        return 0;
    return n + mystery(n - 2);
}
```

(A) Returns 15
(B) Returns 9
(C) StackOverflowError
(D) Returns 5

---

### Q37.
What is the result of calling `factorial(5)`?

```java
public static int factorial(int n) {
    return n * factorial(n - 1);
}
```

(A) Returns 120
(B) Returns 0
(C) StackOverflowError
(D) A compile-time error occurs

---

### Q38.
What value is returned by the method call `sum(4)`?

```java
public static int sum(int n) {
    if (n <= 0)
        return 0;
    return n + sum(n - 1);
}
```

(A) 10
(B) 4
(C) 0
(D) StackOverflowError

---

### Q39.
A binary search is performed on the sorted array for the target value `10`. Which elements are compared to the target before the value is found?

```java
int[] arr = {2, 4, 6, 8, 10, 12, 14};
// Standard binary search: lo = 0, hi = arr.length - 1
```

(A) 8, 12, 10
(B) 8, 10
(C) 6, 10
(D) 8, 12, 14, 10

---

### Q40.
What is printed as a result of executing the code segment?

```java
ArrayList<Integer> nums = new ArrayList<>();
nums.add(10);
nums.add(20);
nums.add(30);
nums.set(1, 99);
System.out.println(nums.get(1));
```

(A) 20
(B) 99
(C) 10
(D) IndexOutOfBoundsException

---

### Q41.
What is returned by the method call `build(4)`?

```java
public static String build(int n) {
    if (n <= 0)
        return "";
    return build(n - 1) + "*";
}
```

(A) "***"
(B) StackOverflowError
(C) ""
(D) "****"

---

### Q42.
Consider the following recursive method.

```java
public static String mystery(String s) {
    if (s.length() <= 1)
        return s;
    return mystery(s.substring(1)) + s.substring(0, 1);
}
```

What is returned by the method call `mystery("ABCD")`?

(A) "ABCD"
(B) "DCBA"
(C) "BCD"
(D) StackOverflowError

---

---

# 정답표

| # | 정답 | Unit | 토픽 | 난이도 | 해설 |
|---|------|------|------|--------|------|
| 1 | C | U1 | 1.10 Calling Class Methods (static 메서드에서 instance 변수 접근 불가) | ★★☆ | `printInfo()`는 static 메서드이므로 instance 변수 `name`에 접근할 수 없다. 컴파일 에러 발생. |
| 2 | B | U1 | 1.10 Calling Class Methods (static counter) | ★★☆ | `c2 = null`은 참조만 끊을 뿐 static 변수 `count`에 영향 없음. 3개 객체가 생성되었으므로 count=3. |
| 3 | C | U1 | 1.15 String Manipulation (null 참조 메서드 호출) | ★★☆ | `null` 참조에 `.length()` 호출 시 NullPointerException 발생. 컴파일은 통과한다. |
| 4 | A | U1 | 1.14 Calling Instance Methods (객체 필드 비교) | ★☆☆ | `getX()`와 `getY()`로 int 값을 비교. `3==3 && 4==4` → `true`. |
| 5 | B | U1 | 1.13 Object Creation and Storage (참조 재할당 vs 객체 변경) | ★★★ | `change()` 메서드 안에서 `other = new Foo(99)`는 로컬 매개변수만 재할당. 원래 `b`가 가리키는 객체는 변하지 않음. |
| 6 | B | U1 | 1.13 Object Creation and Storage (참조 매개변수 swap 함정) | ★★★ | Java에서 메서드 매개변수로 참조를 swap해도 호출자의 참조는 바뀌지 않음. 로컬 변수만 교환됨. |
| 7 | B | U1 | 1.15 String Manipulation (== vs .equals() 비교) | ★★☆ | `s1 == s2`는 false (new로 별도 객체 생성), `s1 == s3`는 true (같은 참조), `s1.equals(s2)`는 true (같은 내용). |
| 8 | A | U1 | 1.12 Objects: Instances of Classes (캡슐화 에러 식별) | ★★☆ | public 필드는 외부에서 직접 수정 가능하여 캡슐화 위반. private + getter가 올바른 패턴. |
| 9 | C | U2 | 2.1 Algorithms with Selection (Math.random 범위) | ★★☆ | `Math.random()`은 [0.0, 1.0) → `*6`하면 [0.0, 6.0) → `(int)` 캐스트하면 0~5 → `+1`하면 1~6. |
| 10 | A | U2 | 2.1 Algorithms with Selection (Math.random 괄호 위치) | ★★★ | `Math.random()*6+1` → [1.0, 7.0) → `(int)` 캐스트하면 1~6. (D) 0~5는 `(int)(Math.random()*6)` 범위이므로 틀림. |
| 11 | B | U2 | 2.2 Boolean Expressions (정수 나눗셈 결과 트레이싱) | ★★★ | `7/2`는 정수 나눗셈으로 3. 이것이 double에 대입되면 3.0. |
| 12 | B | U2 | 2.2 Boolean Expressions (정수 나눗셈과 나머지) | ★★☆ | `17/5 = 3` (정수), `17%5 = 2`. 출력은 `3 2`. |
| 13 | C | U2 | 2.10 Implementing String Algorithms (== vs equals 트레이싱) | ★★☆ | `s1`과 `s2`는 String pool에서 같은 객체 참조 → `==` true. `s3`는 `new`로 생성한 별도 객체 → `==` false. |
| 14 | C | U2 | 2.10 Implementing String Algorithms (compareTo 해석) | ★★★ | `"apple".compareTo("banana")` → 'a'-'b' = -1 (음수). 사전순으로 apple이 banana 앞이므로 음수 반환. |
| 15 | A | U2 | 2.11 Nested Iteration (2D 배열 행 평균 추적) | ★★★ | `getAverage(0)`: sum=80+90+70=240, 240/3=80.0 (double 캐스팅). |
| 16 | B | U2 | 2.11 Nested Iteration (max 알고리즘 트레이싱) | ★★★ | 전체 배열에서 최대값 탐색. 80,90,70,60,100,80 중 최대는 100. |
| 17 | B | U2 | 2.9 Implementing Iteration Algorithms (정렬 변형 추적) | ★★★ | 행0 평균=70, 행1 평균=90, 행2 평균=80. 내림차순 정렬: 행1(90) > 행2(80) > 행0(70). rank=[1,2,0]. |
| 18 | B | U2 | 2.5 Compound Boolean Expressions (논리 연산자 우선순위) | ★★☆ | `&&`가 `\|\|`보다 우선. `!a = false`, `b && a = false`. `false \|\| false = false`. |
| 19 | C | U2 | 2.7 while Loops (종료 시점) | ★★★ | x: 0→3→6→9→12. x=12일 때 `12<10` false → 루프 종료. 출력은 12. |
| 20 | A | U2 | 2.8 for Loops + 2.3 if Statements (분기 누적) | ★★☆ | i=1,2 → total=1+2=3, i=3 (3의 배수) skip, i=4,5 → total=3+4+5=12, i=6 (3의 배수) skip. 결과: 12. |
| 21 | C | U2 | 2.7 while Loops (무한루프 함정) | ★★★ | n은 1→4→7→10→...→49→52→55→... n은 절대 50이 되지 않음. 무한루프. |
| 22 | B | U3 | 3.4 Constructors (인스턴스 변수 기본값) | ★★☆ | int 배열은 0으로 초기화됨. (3.4.A.5 기본값 규칙: int=0, double=0.0, boolean=false, reference=null) |
| 23 | B | U3 | 3.3 Anatomy of a Class (배열 length 필드 접근) | ★★★ | `grid.length`=행 수(3), `grid[0].length`=열 수(4). 자주 혼동되는 함정. |
| 24 | A | U3 | 3.5 Methods (2D 배열 열 우선 순회 추적) | ★★★ | 외부 루프가 `arr[0].length`(열=3), 내부 루프가 `arr.length`(행=2). 열 우선 순회. `arr[0][0]+arr[1][0]+arr[0][1]+arr[1][1]+arr[0][2]+arr[1][2]` = 1+4+2+5+3+6 = 21. 범위 초과 없음. |
| 25 | B | U3 | 3.3 Anatomy of a Class (배열 length vs ArrayList size) | ★★☆ | 배열은 `.length` (필드, 괄호 없음). `size()`는 ArrayList. 3개 원소이므로 3. |
| 26 | B | U3 | 3.5 Methods (off-by-one 경계 오류) | ★★★ | `i <= arr.length`에서 i=5일 때 `arr[5]` 접근 → ArrayIndexOutOfBoundsException. 그 전까지 0~4 인덱스는 정상 출력. |
| 27 | C | U3 | 3.5 Methods (마지막 행 인덱스 계산) | ★★☆ | `grid.length - 1` = 2 (마지막 행). 마지막 행 {7, 8, 9}의 합: 7+8+9 = 24. |
| 28 | A | U4 | 4.8 ArrayList Methods (remove(int) 인덱스) | ★★★ | `remove(1)`은 인덱스 1의 원소(=2)를 제거. 결과: [1, 3]. |
| 29 | A | U4 | 4.8 ArrayList Methods (remove(Object) 값) | ★★★ | `remove(Integer.valueOf(1))`은 값 1을 제거. 결과: [2, 3]. |
| 30 | A | U4 | 4.8 ArrayList Methods (size + get) | ★★☆ | size()=3, get(1)은 인덱스 1 → "dog". |
| 31 | A | U4 | 4.10 Implementing ArrayList Algorithms (순회 중 삭제 함정) | ★★★ | i=1에서 첫 "B" 삭제 → [A,C,B], size=3. i=2에서 "B" 삭제 → [A,C], size=2. i=3≥2 종료. 결과: [A,C]. |
| 32 | C | U4 | 4.16 Recursion (거듭제곱 추적) | ★★☆ | `mystery(4)=2*mystery(3)=2*2*mystery(2)=2*2*2*mystery(1)=2*2*2*2*mystery(0)=2*2*2*2*1=16`. |
| 33 | B | U4 | 4.15 Sorting Algorithms (Selection Sort 1회 pass) | ★★★ | arr[0..4]에서 최솟값=1(인덱스2), arr[0]과 swap → {1,8,5,3,7}. |
| 34 | C | U4 | 4.13 Implementing 2D Array Algorithms (테두리 합) | ★★★ | 테두리 원소: 1+2+3+4+6+7+8+9=40. 중앙 5는 테두리가 아님. |
| 35 | B | U4 | 4.8 ArrayList Methods (add(int,E) + remove 추적) | ★★★ | [10,20,30,40]→add(1,15)→[10,15,20,30,40]→remove(3)→[10,15,20,40]. get(2)=20. |
| 36 | C | U4 | 4.16 Recursion (base case 미도달) | ★★★ | `mystery(5)` → 5+mystery(3) → 3+mystery(1) → 1+mystery(-1) → -1+mystery(-3)... n이 0이 되지 않으므로 무한 재귀 → StackOverflowError. |
| 37 | C | U4 | 4.16 Recursion (base case 없음) | ★★★ | base case가 전혀 없음. `factorial(5)` → `5*factorial(4)` → ... → `1*factorial(0)` → `0*factorial(-1)` → 무한 재귀 → StackOverflowError. |
| 38 | A | U4 | 4.16 Recursion (재귀 합) | ★★☆ | `sum(4)=4+sum(3)=4+3+sum(2)=4+3+2+sum(1)=4+3+2+1+sum(0)=4+3+2+1+0=10`. |
| 39 | A | U4 | 4.17 Recursive Searching (Binary Search 추적) | ★★★ | lo=0,hi=6,mid=3→arr[3]=8<10→lo=4. lo=4,hi=6,mid=5→arr[5]=12>10→hi=4. lo=4,hi=4,mid=4→arr[4]=10 발견. 비교: 8,12,10. |
| 40 | B | U4 | 4.8 ArrayList Methods (set) | ★★☆ | `set(1, 99)`는 인덱스 1의 값을 99로 교체. `get(1)` = 99. |
| 41 | D | U4 | 4.16 Recursion (재귀 문자열 생성) | ★★☆ | `build(4)=build(3)+"*"=build(2)+"**"=build(1)+"***"=build(0)+"****"=""+"****"="****"`. |
| 42 | B | U4 | 4.16 Recursion (재귀 문자열 뒤집기, substring) | ★★★ | `mystery("ABCD")` = mystery("BCD")+"A" = (mystery("CD")+"B")+"A" = ((mystery("D")+"C")+"B")+"A" = "D"+"C"+"B"+"A" = "DCBA". |
