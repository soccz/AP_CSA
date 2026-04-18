# AP Computer Science A — Mock Exam Set 5: Multiple Choice (42 Questions | 90 Minutes)

**Directions:** Determine the answer to each of the following questions or incomplete statements, using the available space for any necessary scratch work. Then decide which is the best of the choices given and fill in the corresponding circle on the answer sheet. A Java Quick Reference is provided as part of the exam.

> **Final Set**: Highest-frequency patterns. Real exam difficulty distribution.
> Easy (1 star) 25% / Medium (2 star) 50% / Hard (3 star) 25%

---

## Question 1 ★
What is printed as a result of executing the code segment?

```java
String s = "APCSA";
System.out.println(s.substring(2, 4) + s.substring(0, 1));
```

(A) `CSA`
(B) `CCA`
(C) `CA`
(D) `CSAA`

---

## Question 2 ★★
What is printed as a result of executing the code segment?

```java
int x = 17;
int y = 5;
System.out.println(x / y + "." + x % y);
```

(A) `3.2`
(B) `3.4`
(C) `3.17`
(D) `3.5`

---

## Question 3 ★★
What is printed as a result of executing the code segment?

```java
int[] arr = {3, 7, 2, 9, 4};
int result = arr[0];
for (int i = 1; i < arr.length; i++) {
    if (arr[i] > result) {
        result = arr[i];
    }
}
System.out.println(result);
```

(A) `2`
(B) `3`
(C) `9`
(D) `4`

---

## Question 4 ★
What is printed as a result of executing the code segment?

```java
boolean found = false;
int[] data = {4, 7, 2, 9};
for (int val : data) {
    if (val > 5) {
        found = true;
    }
}
System.out.println(found);
```

(A) `true`
(B) `false`
(C) `0`
(D) A compile-time error occurs

---

## Question 5 ★★★
What is printed as a result of executing the code segment?

```java
public static int mystery(int n) {
    if (n <= 1)
        return n;
    return mystery(n - 1) + mystery(n - 2);
}

System.out.println(mystery(6));
```

(A) `5`
(B) `8`
(C) `13`
(D) `21`

---

## Question 6 ★★
Which of the following is equivalent to `!(a > b && c <= d)`?

(A) `a > b || c <= d`
(B) `a <= b || c > d`
(C) `a <= b && c > d`
(D) `!(a > b) && !(c <= d)`

---

## Question 7 ★★
What is printed as a result of executing the code segment?

```java
ArrayList<String> list = new ArrayList<>();
list.add("A");
list.add("B");
list.add("C");
list.add("D");
list.remove(1);
list.add(1, "E");
System.out.println(list);
```

(A) `[A, E, C, D]`
(B) `[A, E, B, C, D]`
(C) `[E, A, C, D]`
(D) `[A, B, E, C, D]`

---

## Question 8 ★★★
What is printed as a result of executing the code segment?

```java
int[][] grid = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
int sum = 0;
for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[0].length; c++) {
        if (r == c) {
            sum += grid[r][c];
        }
    }
}
System.out.println(sum);
```

(A) `12`
(B) `15`
(C) `25`
(D) `45`

---

## Question 9 ★
Which of the following is a valid array declaration?

```java
// I
int[] arr = new int(5);
// II
int[] arr = new int[5];
// III
int arr[] = new int[];
// IV
int arr = new int[5];
```

(A) I only
(B) II only
(C) II and III
(D) I and IV

---

## Question 10 ★★
Which of the following best describes why the code does not work as intended?

The following method is intended to count the number of negative elements in an array.

```java
public static int countNeg(int[] arr) {
    int count = 0;
    for (int i = 0; i <= arr.length; i++) {
        if (arr[i] < 0) {
            count++;
        }
    }
    return count;
}
```

(A) The condition `i <= arr.length` should be `i < arr.length` to avoid an `ArrayIndexOutOfBoundsException`.
(B) The loop variable should start at `i = 1`.
(C) The condition `arr[i] < 0` should be `arr[i] <= 0`.
(D) `count++` should be `count += 1`.

---

## Question 11 ★★
What is printed as a result of executing the code segment?

```java
String word = "racecar";
String reversed = "";
for (int i = word.length() - 1; i >= 0; i--) {
    reversed += word.substring(i, i + 1);
}
System.out.println(reversed.equals(word));
```

(A) `true`
(B) `false`
(C) `racecar`
(D) A compile-time error occurs

---

## Question 12 ★★★
After two passes of selection sort (ascending order) on the array `{8, 3, 5, 1, 9, 2}`, the array state is:

(A) `{1, 2, 5, 8, 9, 3}`
(B) `{1, 2, 5, 3, 9, 8}`
(C) `{1, 2, 8, 3, 9, 5}`
(D) `{1, 3, 5, 2, 9, 8}`

---

## Question 13 ★★
What is printed as a result of executing the code segment?

```java
int a = 5, b = 10, c = 15;
if (a < b && b < c) {
    if (a + b > c) {
        System.out.println("X");
    } else {
        System.out.println("Y");
    }
} else {
    System.out.println("Z");
}
```

(A) `X`
(B) `Y`
(C) `Z`
(D) Nothing is printed

---

## Question 14 ★★
Which of the following is equivalent to `!(x != 0 || y == 5)`?

(A) `x != 0 && y == 5`
(B) `x == 0 && y != 5`
(C) `x == 0 || y != 5`
(D) `x != 0 || y != 5`

---

### Questions 15-17 refer to the following class.

```java
public class MusicPlaylist {
    private ArrayList<String> songs;
    private ArrayList<Integer> durations;

    public MusicPlaylist() {
        songs = new ArrayList<String>();
        durations = new ArrayList<Integer>();
    }

    public void addSong(String title, int seconds) {
        songs.add(title);
        durations.add(seconds);
    }

    public int getTotalDuration() {
        int total = 0;
        for (int d : durations) {
            total += d;
        }
        return total;
    }

    public ArrayList<String> filterByMinDuration(int minSeconds) {
        ArrayList<String> result = new ArrayList<String>();
        for (int i = 0; i < songs.size(); i++) {
            if (durations.get(i) >= minSeconds) {
                result.add(songs.get(i));
            }
        }
        return result;
    }

    public String shuffle() {
        if (songs.size() == 0) return "";
        int idx = (int)(Math.random() * songs.size());
        return songs.get(idx);
    }

    public int getSongCount() {
        return songs.size();
    }
}
```

## Question 15 ★★
What is printed as a result of executing the code segment?

```java
MusicPlaylist pl = new MusicPlaylist();
pl.addSong("Imagine", 183);
pl.addSong("Yesterday", 125);
pl.addSong("Bohemian", 354);
System.out.println(pl.getSongCount() + " " + pl.getTotalDuration());
```

(A) `3 662`
(B) `3 354`
(C) `2 662`
(D) `3 183`

---

## Question 16 ★★
What is printed as a result of executing the code segment?

```java
MusicPlaylist pl = new MusicPlaylist();
pl.addSong("Short", 60);
pl.addSong("Medium", 180);
pl.addSong("Long", 300);
pl.addSong("Epic", 420);
ArrayList<String> filtered = pl.filterByMinDuration(200);
System.out.println(filtered);
```

(A) `[Short, Medium]`
(B) `[Long, Epic]`
(C) `[Medium, Long, Epic]`
(D) `[Short]`

---

## Question 17 ★★★
What is printed as a result of executing the code segment?

```java
MusicPlaylist pl = new MusicPlaylist();
System.out.println(pl.getTotalDuration());
System.out.println(pl.shuffle());
System.out.println(pl.filterByMinDuration(100).size());
```

(A) `0`, `""`, and `0`
(B) A run-time error occurs on `shuffle()`
(C) `0`, `null`, and `0`
(D) A compile-time error occurs

---

## Question 18 ★★
What is printed as a result of executing the code segment?

```java
String[] names = {"Kim", "Lee", "Park", "Choi"};
for (int i = 0; i < names.length - 1; i++) {
    if (names[i].compareTo(names[i + 1]) > 0) {
        System.out.print(names[i] + " ");
    }
}
```

(A) `Lee Park`
(B) `Park`
(C) `Lee Park Choi`
(D) `Kim Lee Park`

---

## Question 19 ★★
Which of the following best describes why the code does not work as intended?

The following code is intended to read the **entire first line** of the file `data.txt`, but instead only reads the first word of that line.

```java
import java.util.Scanner;
import java.io.File;
import java.io.FileNotFoundException;

public static String readFirstLine() throws FileNotFoundException {
    Scanner sc = new Scanner(new File("data.txt"));
    String line = sc.next();
    sc.close();
    return line;
}
```

(A) `Scanner` does not have a `next()` method.
(B) `sc.next()` reads only the next whitespace-delimited token; `sc.nextLine()` should be used to read the entire line.
(C) `sc.next()` always returns `null`.
(D) The code works as intended and reads the full line.

---

## Question 20 ★★
What is printed as a result of executing the code segment?

```java
ArrayList<Integer> nums = new ArrayList<>();
for (int i = 1; i <= 5; i++) {
    nums.add(i * 10);
}
for (int i = nums.size() - 1; i >= 0; i--) {
    if (nums.get(i) % 20 == 0) {
        nums.remove(i);
    }
}
System.out.println(nums);
```

(A) `[10, 30, 50]`
(B) `[10, 20, 30, 40, 50]`
(C) `[10, 30]`
(D) `[30, 50]`

---

## Question 21 ★★★
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
Counter a = new Counter();
Counter b = new Counter();
Counter c = new Counter();
System.out.println(Counter.getCount() + " " + b.getId());
```

(A) `3 3`
(B) `3 2`
(C) `2 2`
(D) `3 1`

---

## Question 22 ★★
What is printed as a result of executing the code segment?

```java
int count = 0;
for (int i = 0; i < 10; i++) {
    if (i % 3 == 0 || i % 5 == 0) {
        count++;
    }
}
System.out.println(count);
```

(A) `4`
(B) `5`
(C) `6`
(D) `7`

---

## Question 23 ★
Which of the following code segments correctly accesses a `private` instance variable from outside the class?

```java
public class Box {
    private int width;
    public Box(int w) { width = w; }
    public int getWidth() { return width; }
}
```

(A) `Box b = new Box(5); System.out.println(b.width);`
(B) `Box b = new Box(5); System.out.println(b.getWidth());`
(C) `Box b = new Box(5); System.out.println(Box.width);`
(D) `Box b = new Box(5); System.out.println(width);`

---

## Question 24 ★★★
What is printed as a result of executing the code segment?

```java
int[][] mat = new int[3][4];
for (int r = 0; r < mat.length; r++) {
    for (int c = 0; c < mat[0].length; c++) {
        mat[r][c] = r * mat[0].length + c + 1;
    }
}
System.out.println(mat[2][3] + " " + mat[1][0]);
```

(A) `12 5`
(B) `11 4`
(C) `12 4`
(D) `11 5`

---

## Question 25 ★★
Which of the following best describes why the code does not work as intended?

The following constructor is intended to initialize the fields `x` and `y` with the parameter values, but after construction both fields remain `0`.

```java
public class Point {
    private int x;
    private int y;
    public Point(int x, int y) {
        x = x;
        y = y;
    }
}
```

(A) The assignments `x = x` and `y = y` assign the parameters to themselves instead of to the instance variables. `this.x = x` and `this.y = y` should be used.
(B) The parameter names should be changed to `a` and `b`.
(C) The fields should be declared as `public`.
(D) Both (A) and (B) would fix the problem.

---

## Question 26 ★★
What is printed as a result of executing the code segment?

```java
String s1 = "hello";
String s2 = new String("hello");
System.out.println(s1 == s2);
System.out.println(s1.equals(s2));
```

(A) `true` `true`
(B) `false` `true`
(C) `true` `false`
(D) `false` `false`

---

## Question 27 ★★
Which of the following code segments correctly implements a binary search for `target` in a sorted array `arr`?

(A)
```java
int lo = 0, hi = arr.length - 1;
while (lo <= hi) {
    int mid = (lo + hi) / 2;
    if (arr[mid] == target) return mid;
    else if (arr[mid] < target) lo = mid + 1;
    else hi = mid - 1;
}
return -1;
```
(B)
```java
int lo = 0, hi = arr.length;
while (lo < hi) {
    int mid = (lo + hi) / 2;
    if (arr[mid] == target) return mid;
    else if (arr[mid] < target) lo = mid;
    else hi = mid;
}
return -1;
```
(C)
```java
for (int i = 0; i < arr.length; i++) {
    if (arr[i] == target) return i;
}
return -1;
```
(D) Both (A) and (C) always return the correct result

---

## Question 28 ★★
What is printed as a result of executing the code segment?

```java
int x = 100;
while (x > 1) {
    System.out.print(x + " ");
    x /= 3;
}
```

(A) `100 33 11 3 1`
(B) `100 33 11 3`
(C) `100 33 11`
(D) `100 33 11 3 1 0`

---

## Question 29 ★★★
Consider the following sorted array and binary search for the value `7`.

```java
int[] arr = {1, 3, 5, 7, 9, 11, 13, 15};
```

Which elements are compared to the target before the value is found?

(A) `9, 3, 5, 7`
(B) `9, 5, 7`
(C) `7`
(D) `9, 3, 7`

---

## Question 30 ★
Which of the following best describes the range of values returned by `Math.random()`?

(A) `0.0 <= x < 1.0`
(B) `0.0 <= x <= 1.0`
(C) `0 <= x < 10`
(D) `1 <= x <= 10`

---

## Question 31 ★★
What is printed as a result of executing the code segment?

```java
ArrayList<String> words = new ArrayList<>();
words.add("cat");
words.add("dog");
words.add("cat");
words.add("bird");
int i = 0;
while (i < words.size()) {
    if (words.get(i).equals("cat")) {
        words.remove(i);
    } else {
        i++;
    }
}
System.out.println(words);
```

(A) `[dog, bird]`
(B) `[dog, cat, bird]`
(C) `[cat, dog, cat, bird]`
(D) `IndexOutOfBoundsException`

---

## Question 32 ★★★
What is printed as a result of executing the code segment?

```java
int[][] grid = {{1, 2}, {3, 4}, {5, 6}};
int sum = 0;
for (int r = 0; r < grid.length; r++) {
    sum += grid[r][1];
}
System.out.println(sum);
```

(A) `6`
(B) `9`
(C) `12`
(D) `21`

---

## Question 33 ★★
What is printed as a result of executing the code segment?

```java
int[] data = {4, 7, 2, 9, 1, 5};
int min = data[0];
int minIdx = 0;
for (int i = 1; i < data.length; i++) {
    if (data[i] < min) {
        min = data[i];
        minIdx = i;
    }
}
System.out.println(minIdx);
```

(A) `1`
(B) `2`
(C) `4`
(D) `5`

---

## Question 34 ★★
Which of the following is equivalent to `!(p || !q)`?

(A) `!p && q`
(B) `!p || q`
(C) `p && !q`
(D) `p || q`

---

## Question 35 ★★★
Which of the following code segments correctly creates a `Scanner` to read from a file?

```java
import java.util.Scanner;
import java.io.File;
import java.io.FileNotFoundException;
```

(A) `Scanner sc = new Scanner(new File("data.txt"));`
(B) `Scanner sc = new Scanner("data.txt");`
(C) `Scanner sc = Scanner.open("data.txt");`
(D) `Scanner sc = new File("data.txt").scanner();`

---

## Question 36 ★★
What is printed as a result of executing the code segment?

```java
String str = "Histogram";
int idx = str.indexOf("gram");
System.out.println(idx);
```

(A) `4`
(B) `5`
(C) `6`
(D) `-1`

---

## Question 37 ★
Which of the following operations CANNOT be performed using an enhanced for loop?

(A) Printing all elements of an array
(B) Finding the maximum value of an array
(C) Changing the value of a specific element by index
(D) Computing the sum of all elements

---

## Question 38 ★★★
What is printed as a result of executing the code segment?

```java
ArrayList<String> words = new ArrayList<>();
words.add("Hi");
words.add("Hello");
words.add("No");
words.add("World");
for (int i = words.size() - 1; i >= 0; i--) {
    if (words.get(i).length() < 4) {
        words.remove(i);
    }
}
System.out.println(words);
```

(A) `[Hi, Hello, No, World]`
(B) `[Hello, World]`
(C) `[Hello, No, World]`
(D) `IndexOutOfBoundsException`

---

## Question 39 ★★
Which of the following best describes the relationship when class `Library` has a field `Book[] collection`?

(A) Inheritance (is-a)
(B) Composition (has-a)
(C) Delegation
(D) Dependency

---

## Question 40 ★★
Which of the following code segments produces the same output as the code segment below?

```java
public static double average(int[] arr) {
    int sum = 0;
    for (int val : arr) {
        sum += val;
    }
    return (double) sum / arr.length;
}
// Called with: average(new int[]{10, 20, 30})
```

(A)
```java
double sum = 0;
for (int val : arr) { sum += val; }
return sum / arr.length;
```
(B)
```java
int sum = 0;
for (int val : arr) { sum += val; }
return sum / (double) arr.length;
```
(C)
```java
int sum = 0;
for (int val : arr) { sum += val; }
return 1.0 * sum / arr.length;
```
(D) All of the above

---

## Question 41 ★★
What is printed as a result of executing the code segment?

```java
int[] arr = {3, 1, 4, 1, 5};
int sum = 0;
for (int val : arr) {
    sum += val;
}
System.out.println((double) sum / arr.length);
```

(A) `2`
(B) `2.0`
(C) `2.8`
(D) `3.0`

---

## Question 42 ★★
After one pass of insertion sort (i=1) on the array `{5, 3, 8, 1, 6}`, the array state is:

(A) `{3, 5, 8, 1, 6}`
(B) `{1, 3, 5, 8, 6}`
(C) `{1, 5, 3, 8, 6}`
(D) `{3, 5, 1, 8, 6}`

---

# 정답표

| # | 정답 | Unit | 토픽 (CED) | 난이도 | 해설 |
|---|------|------|-----------|--------|------|
| 1 | A | Unit 1 | 1.15 String 메서드 (substring) | ★ | `substring(2,4)` → `"CS"`, `substring(0,1)` → `"A"` → `"CSA"` |
| 2 | A | Unit 1 | 1.3 Expressions (정수 나눗셈 + 문자열 연결) | ★★ | `17/5`=`3`(정수), `17%5`=`2`, `"3"+"."+"2"` = `"3.2"` |
| 3 | C | Unit 4 | 4.2 Array Standard Algorithms (max) | ★★ | 순회하며 최댓값 갱신 → 최종 `9` |
| 4 | A | Unit 2 | 2.7-2.8 반복문 (enhanced for + boolean) | ★ | 7과 9가 5보다 크므로 found=true |
| 5 | B | Unit 4 | 4.16 Recursion 트레이싱 (피보나치) | ★★★ | `f(0)=0, f(1)=1, f(2)=1, f(3)=2, f(4)=3, f(5)=5, f(6)=8` |
| 6 | B | Unit 2 | 2.5-2.6 De Morgan 법칙 | ★★ | `!(A&&B)` = `!A||!B` → `a<=b || c>d` |
| 7 | A | Unit 4 | 4.8 ArrayList 메서드 (remove/add) | ★★ | `remove(1)`→`[A,C,D]`, `add(1,"E")`→`[A,E,C,D]` |
| 8 | B | Unit 4 | 4.12-4.13 2D 배열 대각선 합 | ★★★ | `r==c`인 원소: `1+5+9`=`15` |
| 9 | B | Unit 4 | 4.1 1D 배열 선언 문법 | ★ | `new int[5]`가 올바른 문법 |
| 10 | A | Unit 4 | 4.3 배열 순회 경계 오류 식별 | ★★ | `<=`→`ArrayIndexOutOfBoundsException`. `<`로 수정 |
| 11 | A | Unit 2 | 2.10 String 알고리즘 (역순/회문) | ★★ | `"racecar"` 뒤집어도 동일 → `true` |
| 12 | A | Unit 4 | 4.15 Selection Sort 트레이싱 | ★★★ | Pass1: min=1(idx3), swap(0,3)→`{1,3,5,8,9,2}`. Pass2: idx1~5에서 min=2(idx5), swap(1,5)→`{1,2,5,8,9,3}` |
| 13 | B | Unit 2 | 2.4 Nested if | ★★ | `5<10&&10<15`→`true`. `5+10=15`, `15>15`→`false` → `"Y"` |
| 14 | B | Unit 2 | 2.5-2.6 De Morgan 법칙 | ★★ | `!(A||B)` = `!A&&!B` → `x==0 && y!=5` |
| 15 | A | Unit 4 | 4.8-4.9 ArrayList 클래스 사용 | ★★ | 3곡 추가. 합계: 183+125+354=662 |
| 16 | B | Unit 4 | 4.10 ArrayList 알고리즘 (필터링) | ★★ | minSeconds=200 이상: "Long"(300), "Epic"(420). 결과: [Long, Epic] |
| 17 | A | Unit 4 | 4.8-4.10 ArrayList 엣지 케이스 (size==0) | ★★★ | 빈 playlist: getTotalDuration()=0, shuffle()는 size==0이면 "" 반환, filterByMinDuration(100).size()=0 |
| 18 | B | Unit 2 | 2.10 String 알고리즘 (compareTo 순회) | ★★ | `"Kim"<"Lee"`, `"Lee"<"Park"`, `"Park">"Choi"` → `Park` 출력 |
| 19 | B | Unit 4 | 4.6 Scanner 파일 입력 (next vs nextLine) | ★★ | `next()`는 토큰 단위 읽기. `nextLine()`이 한 줄 전체 읽기 |
| 20 | A | Unit 4 | 4.10 ArrayList 역순 제거 패턴 | ★★ | 20의 배수(20,40) 제거 → `[10,30,50]` |
| 21 | B | Unit 3 | 3.7 Class Variables (static) | ★★★ | static `count`는 3개 객체 생성 후 3. `b`는 두 번째로 생성되어 id=2. 출력: `3 2` |
| 22 | B | Unit 2 | 2.5+2.8 복합 조건 + for 루프 | ★★ | i=0(0%3=0), 3(3%3=0), 5(5%5=0), 6(6%3=0), 9(9%3=0) → 5개 |
| 23 | B | Unit 3 | 3.8 Scope and Access (캡슐화) | ★ | `private` → `public` getter로 접근 |
| 24 | A | Unit 4 | 4.11 2D 배열 인덱싱 | ★★★ | `mat[2][3]`=`2*4+3+1`=`12`, `mat[1][0]`=`1*4+0+1`=`5` |
| 25 | A | Unit 3 | 3.9 `this` 키워드 (shadowing) | ★★ | 근본 원인은 `x = x`가 매개변수를 자기 자신에게 대입하는 것(shadowing). `this.x = x`로 수정하면 해결 |
| 26 | B | Unit 1 | 1.15 String == vs equals | ★★ | `==`는 참조(다름), `equals()`는 내용(같음) |
| 27 | A | Unit 4 | 4.17 Binary Search 구현 식별 | ★★ | (A)는 올바른 binary search. (B)는 lo=mid/hi=mid로 무한루프 가능. (C)는 linear search |
| 28 | B | Unit 2 | 2.7 while 루프 트레이싱 | ★★ | `100→33→11→3→1(종료)`. 1은 `>1` 불만족으로 미출력 |
| 29 | C | Unit 4 | 4.17 Binary Search 트레이싱 | ★★★ | 배열 idx 0~7. mid=(0+7)/2=3, arr[3]=7 → 한 번에 찾음. 비교 원소: 7만 |
| 30 | A | Unit 1 | 1.11 Math.random() 범위 | ★ | `0.0 <= x < 1.0` |
| 31 | A | Unit 4 | 4.10 ArrayList 조건부 제거 (while+조건부 i++) | ★★ | while+조건부 i++ 패턴으로 모든 `"cat"` 제거 → `[dog,bird]` |
| 32 | C | Unit 4 | 4.12 2D 배열 열 합산 | ★★★ | grid[r][1]만 합산: 2+4+6=12 |
| 33 | C | Unit 4 | 4.2 Array Standard Algorithms (min 인덱스) | ★★ | 최솟값 `1`은 인덱스 `4` |
| 34 | A | Unit 2 | 2.5-2.6 De Morgan 법칙 | ★★ | `!(p||!q)` = `!p && !!q` = `!p && q` |
| 35 | A | Unit 4 | 4.6 Scanner + File 생성 | ★★★ | `Scanner(String)`은 문자열 자체를 소스로 사용. 파일은 `File` 객체 필요 |
| 36 | B | Unit 1 | 1.15 String indexOf | ★★ | `"Histogram"`: H(0)i(1)s(2)t(3)o(4)g(5)r(6)a(7)m(8). `"gram"` = g(5)r(6)a(7)m(8) → `indexOf` = `5` |
| 37 | C | Unit 4 | 4.4 Enhanced for 제한 | ★ | for-each는 인덱스 접근 불가 → 특정 위치 원소 변경 불가 |
| 38 | B | Unit 4 | 4.10 ArrayList 역순 조건부 삭제 | ★★★ | 역순 순회로 length<4인 "Hi"(2), "No"(2) 삭제. 결과: [Hello, World] |
| 39 | B | Unit 3 | 3.6 객체 참조를 필드로 보유 (has-a) | ★★ | 필드로 다른 클래스 배열 보유 = has-a (composition). 상속(is-a)은 범위 외 |
| 40 | D | Unit 1 | 1.5 Casting (double 캐스팅 동치 표현) | ★★ | 캐스팅/타입변경 세 방법 모두 `(double)sum/arr.length`와 동일한 결과 |
| 41 | C | Unit 1 | 1.5 Casting + 1.3 평균 계산 | ★★ | sum=3+1+4+1+5=14, 14.0/5=2.8 |
| 42 | A | Unit 4 | 4.15 Insertion Sort 트레이싱 | ★★ | i=1: `3`을 `5` 앞에 삽입 → `{3,5,8,1,6}` |

---

## 최종 정답 요약

| # | 답 | # | 답 | # | 답 | # | 답 | # | 답 | # | 답 |
|---|-----|---|-----|---|-----|---|-----|---|-----|---|-----|
| 1 | A | 8 | B | 15 | A | 22 | B | 29 | C | 36 | B |
| 2 | A | 9 | B | 16 | B | 23 | B | 30 | A | 37 | C |
| 3 | C | 10 | A | 17 | A | 24 | A | 31 | A | 38 | B |
| 4 | A | 11 | A | 18 | B | 25 | A | 32 | C | 39 | B |
| 5 | B | 12 | A | 19 | B | 26 | B | 33 | C | 40 | D |
| 6 | B | 13 | B | 20 | A | 27 | A | 34 | A | 41 | C |
| 7 | A | 14 | B | 21 | B | 28 | B | 35 | A | 42 | A |
