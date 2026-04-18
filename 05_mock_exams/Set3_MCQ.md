# AP Computer Science A — Mock Exam Set 3: Multiple Choice
## 42 Questions | 90 Minutes

**Directions:** Determine the answer to each of the following questions or incomplete statements, using the available space for any necessary scratch work. Then decide which is the best of the choices given and fill in the corresponding circle on the answer sheet. A Java Quick Reference is provided as part of the exam.

> **Focus of this set: Code Analysis** — code tracing, loop/condition tracking, method call result prediction, recursive stack tracing, ArrayList state changes, 2D array traversal

---

### 1.
What is printed as a result of executing the code segment?
```java
int x = 17;
int y = 5;
System.out.println(x / y + " " + x % y);
```
(A) 3.4 2
(B) 3 2
(C) 3.4 2.0
(D) 3 2.0

---

### 2.
What is the value of `result` after the code segment executes?
```java
int result = 0;
for (int i = 1; i <= 4; i++) {
    for (int j = i; j <= 4; j++) {
        result++;
    }
}
```
(A) 8
(B) 10
(C) 12
(D) 16

---

### 3.
What is printed as a result of executing the code segment?
```java
String s = "COMPUTE";
System.out.println(s.substring(2, 5) + s.substring(0, 1));
```
(A) MPUTC
(B) MPUC
(C) COMPU
(D) PUTC

---

### 4.
What is printed as a result of executing the code segment?
```java
int a = 10;
int b = 3;
double c = (double) a / b;
System.out.println((int)(c * 10));
```
(A) 33
(B) 30
(C) 3
(D) 34

---

### 5.
Consider the following recursive method.

```java
public static int mystery(int n) {
    if (n <= 1) return 1;
    return n + mystery(n - 2);
}
```

What value is returned by the method call `mystery(5)`?

(A) 9
(B) 15
(C) 8
(D) 6

---

### 6.
What is printed as a result of executing the code segment?
```java
double a = Math.pow(2, 3);
double b = Math.sqrt(16);
double c = Math.abs(-7.5);
System.out.println((int)(a + b + c));
```
(A) 20
(B) 19.5
(C) 18
(D) 19

---

### 7.
What is printed as a result of executing the code segment?
```java
String s = "abcdef";
String result = "";
for (int i = s.length() - 1; i >= 0; i -= 2) {
    result += s.substring(i, i + 1);
}
System.out.println(result);
```
(A) fdb
(B) fed
(C) ace
(D) bdf

---

### 8.
How many times does the `while` loop execute in the following code segment?
```java
int n = 100;
int count = 0;
while (n > 1) {
    n /= 3;
    count++;
}
```
(A) 3
(B) 4
(C) 5
(D) 6

---

### 9.
What is the content of `list` after the code segment executes?
```java
ArrayList<Integer> list = new ArrayList<>();
list.add(5);
list.add(10);
list.add(15);
list.add(1, 20);
list.remove(2);
```
(A) [5, 20, 15]
(B) [5, 20, 10]
(C) [5, 15]
(D) [20, 5, 15]

---

### 10.
What is printed as a result of executing the code segment?
```java
int[][] grid = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
int sum = 0;
for (int r = 0; r < grid.length; r++) {
    sum += grid[r][grid.length - 1 - r];
}
System.out.println(sum);
```
(A) 12
(B) 15
(C) 18
(D) 6

---

### 11.
Consider the following method.

```java
public static String convert(String s) {
    String result = "";
    for (int i = 0; i < s.length(); i++) {
        String ch = s.substring(i, i + 1);
        if (ch.equals(" ")) {
            result += "_";
        } else {
            result += ch + ch;
        }
    }
    return result;
}
```

What is returned by the method call `convert("AB C")`?

(A) "AABBCC"
(B) "AB_C"
(C) "AABB_CC"
(D) "AABB_C"

---

### 12.
What is printed as a result of executing the code segment?
```java
int x = 7;
int y = 2;
double r = (double) x / y;
double p = Math.pow(2, 3);
System.out.println(r + " " + (int) p);
```
(A) 3.0 8
(B) 3.5 8.0
(C) 3 8
(D) 3.5 8

---

### 13.
Consider the following recursive method.

```java
public static void recur(int n) {
    if (n <= 0) return;
    System.out.print(n + " ");
    recur(n - 1);
    System.out.print(n + " ");
}
```

What is printed as a result of the method call `recur(4)`?

(A) 4 3 2 1 1 2 3 4
(B) 4 3 2 1
(C) 1 2 3 4
(D) 1 2 3 4 4 3 2 1

---

### 14.
What is printed as a result of executing the code segment?
```java
boolean a = true;
boolean b = false;
boolean c = true;
System.out.println((a || b) && (!c || b));
```
(A) true
(B) false
(C) A compile-time error occurs
(D) A run-time error occurs

---

### 15.
### Questions 15-17 refer to the following class.

```java
public class WordGame {
    private String word;

    public WordGame(String w) {
        word = w;
    }

    public String scramble() {
        String result = "";
        for (int i = word.length() - 1; i >= 0; i--) {
            result += word.substring(i, i + 1);
        }
        return result;
    }

    public String hint(int numChars) {
        if (numChars > word.length()) {
            numChars = word.length();
        }
        String h = word.substring(0, numChars);
        for (int i = numChars; i < word.length(); i++) {
            h += "_";
        }
        return h;
    }

    public boolean isGuessCorrect(String guess) {
        return word.equals(guess);
    }

    public int getLength() {
        return word.length();
    }
}
```

What is printed as a result of executing the code segment?

```java
WordGame game = new WordGame("HELLO");
System.out.println(game.scramble());
```

(A) "HELLO"
(B) "OLLEH"
(C) "LEHOL"
(D) "OLELH"

---

### 16.
What is printed as a result of executing the code segment?

```java
WordGame game = new WordGame("JAVA");
System.out.println(game.hint(2));
System.out.println(game.isGuessCorrect("java"));
```

(A) `JA__` and `true`
(B) `JA__` and `false`
(C) `JA` and `true`
(D) `JAVA` and `false`

---

### 17.
What is printed as a result of executing the code segment?

```java
WordGame game = new WordGame("AB");
System.out.println(game.hint(5));
System.out.println(game.scramble().equals(game.scramble()));
```

(A) `AB___` and `true`
(B) `AB` and `true`
(C) `AB` and `false`
(D) `AB___` and `false`

---

### 18.
What is printed as a result of executing the code segment?
```java
int[][] m = new int[3][4];
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 4; j++) {
        m[i][j] = i * 4 + j;
    }
}
System.out.println(m[2][1] + m[1][3]);
```
(A) 14
(B) 15
(C) 16
(D) 12

---

### 19.
Consider the following recursive method.

```java
public static int calc(int n) {
    if (n == 0) return 0;
    if (n == 1) return 1;
    return calc(n - 1) + calc(n - 2);
}
```

What value is returned by the method call `calc(6)`?

(A) 6
(B) 8
(C) 13
(D) 5

---

### 20.
What is printed as a result of executing the code segment?
```java
String[] words = {"cat", "bat", "rat", "hat"};
String result = "";
for (String w : words) {
    result += w.substring(0, 1);
}
System.out.println(result);
```
(A) "tttt"
(B) "cbrh"
(C) "catbatrathat"
(D) "cat bat rat hat"

---

### 21.
What is printed as a result of executing the code segment?
```java
String s = "computer";
int n = s.length();
n += 5;
n -= 2;
n *= 2;
System.out.println(n);
```
(A) 11
(B) 26
(C) 22
(D) 16

---

### 22.
What is the size of `list` after the code segment executes?
```java
ArrayList<Integer> list = new ArrayList<>();
for (int i = 0; i < 10; i++) {
    list.add(i * i);
}
for (int i = list.size() - 1; i >= 0; i--) {
    if (list.get(i) % 2 != 0) {
        list.remove(i);
    }
}
```
(A) 6
(B) 7
(C) 5
(D) 4

---

### 23.
What is printed as a result of executing the code segment?
```java
int n = 1234;
int reversed = 0;
while (n > 0) {
    reversed = reversed * 10 + n % 10;
    n /= 10;
}
System.out.println(reversed);
```
(A) 1234
(B) 432
(C) 43210
(D) 4321

---

### 24.
Consider the following class.

```java
public class Counter {
    private int value;

    public Counter() {
        value = 0;
        increment();
        increment();
        decrement();
    }

    public void increment() { value += 3; }
    public void decrement() { value -= 1; }
    public int getValue() { return value; }
}
```

What is the result of `new Counter().getValue()`?

(A) 1
(B) 4
(C) 5
(D) 3

---

### 25.
What is printed as a result of executing the code segment?
```java
int[][] grid = {{1, 0, 1}, {0, 1, 0}, {1, 1, 0}};
int count = 0;
for (int c = 0; c < grid[0].length; c++) {
    boolean allOne = true;
    for (int r = 0; r < grid.length; r++) {
        if (grid[r][c] == 0) {
            allOne = false;
        }
    }
    if (allOne) count++;
}
System.out.println(count);
```
(A) 0
(B) 1
(C) 2
(D) 3

---

### 26.
Consider the following method and sorted array.

```java
public static int search(int[] arr, int target) {
    int lo = 0, hi = arr.length - 1;
    while (lo <= hi) {
        int mid = (lo + hi) / 2;
        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) lo = mid + 1;
        else hi = mid - 1;
    }
    return -1;
}
// arr = {1, 3, 5, 7, 9, 11, 13}
```

What value is returned by the method call `search(arr, 7)`?

(A) 3
(B) 4
(C) 7
(D) -1

---

### 27.
What is printed as a result of executing the code segment?

```java
String s = "abcdefg";
int p = s.indexOf("d");
String left = s.substring(0, p);
String right = s.substring(p + 1);
System.out.println(right + left);
```

(A) "abcefg"
(B) "efgdabc"
(C) "defgabc"
(D) "efgabc"

---

### 28.
What is printed as a result of executing the code segment?
```java
int x = 5;
if (x > 3) {
    if (x > 10) {
        System.out.print("A");
    } else {
        System.out.print("B");
    }
} else {
    System.out.print("C");
}
System.out.print("D");
```
(A) "AD"
(B) "BD"
(C) "CD"
(D) "B"

---

### 29.
What is printed as a result of executing the code segment?
```java
ArrayList<Integer> nums = new ArrayList<Integer>();
nums.add(4);
nums.add(7);
nums.add(2);
nums.add(9);
nums.add(1);

int min = nums.get(0);
int minIdx = 0;
for (int i = 1; i < nums.size(); i++) {
    if (nums.get(i) < min) {
        min = nums.get(i);
        minIdx = i;
    }
}
nums.remove(minIdx);
System.out.println(nums);
```
(A) [7, 2, 9, 1]
(B) [4, 7, 2, 9]
(C) [4, 7, 9, 1]
(D) [4, 7, 2, 9, 1]

---

### 30.
What is printed as a result of executing the code segment?
```java
int[][] mat = {{5, 3, 8}, {1, 7, 2}, {6, 4, 9}};
int total = 0;
for (int i = 0; i < mat.length; i++) {
    for (int j = 0; j < mat[0].length; j++) {
        if (i < j) total += mat[i][j];
    }
}
System.out.println(total);
```
(A) 13
(B) 15
(C) 17
(D) 21

---

### 31.
Consider the following recursive method.

```java
public static int power(int base, int exp) {
    if (exp == 0) return 1;
    if (exp % 2 == 0) {
        int half = power(base, exp / 2);
        return half * half;
    }
    return base * power(base, exp - 1);
}
```

What value is returned by the method call `power(3, 4)`?

(A) 81
(B) 12
(C) 27
(D) 64

---

### 32.
What is the state of `arr` after the code segment executes? (One pass of selection sort — finds the minimum in the unsorted portion and swaps it to the front.)
```java
int[] arr = {5, 3, 8, 1, 2};
int minIdx = 0;
for (int j = 1; j < arr.length; j++) {
    if (arr[j] < arr[minIdx]) {
        minIdx = j;
    }
}
int temp = arr[0];
arr[0] = arr[minIdx];
arr[minIdx] = temp;
```
(A) {1, 2, 3, 5, 8}
(B) {3, 5, 8, 1, 2}
(C) {1, 3, 8, 5, 2}
(D) {1, 5, 8, 3, 2}

---

### 33.
What is printed as a result of executing the code segment?
```java
String s = "racecar";
boolean isPalin = true;
for (int i = 0; i < s.length() / 2; i++) {
    if (!(s.substring(i, i + 1).equals(s.substring(s.length() - 1 - i, s.length() - i)))) {
        isPalin = false;
    }
}
System.out.println(isPalin);
```

(A) true
(B) false
(C) A compile-time error occurs
(D) A run-time error occurs

---

### 34.
What is printed as a result of executing the code segment?
```java
int count = 0;
for (int i = 2; i <= 20; i++) {
    boolean prime = true;
    for (int j = 2; j < i; j++) {
        if (i % j == 0) {
            prime = false;
        }
    }
    if (prime) count++;
}
System.out.println(count);
```

(A) 6
(B) 7
(C) 8
(D) 9

---

### 35.
What is printed as a result of executing the code segment?
```java
ArrayList<String> list = new ArrayList<>();
list.add("red");
list.add("blue");
list.add("green");
list.add("red");
list.add("blue");

int i = 0;
while (i < list.size()) {
    if (list.get(i).equals("red")) {
        list.remove(i);
    } else {
        i++;
    }
}
System.out.println(list);
```
(A) [blue, green, red, blue]
(B) [red, blue, green, blue]
(C) [blue, green]
(D) [blue, green, blue]

---

### 36.
What is printed as a result of executing the code segment?
```java
int[][] grid = new int[4][4];
for (int i = 0; i < 4; i++) {
    for (int j = 0; j < 4; j++) {
        if (i == j) grid[i][j] = 1;
        else if (i + j == 3) grid[i][j] = 2;
    }
}
System.out.println(grid[1][2] + grid[2][1] + grid[0][3] + grid[3][0]);
```
(A) 4
(B) 6
(C) 8
(D) 2

---

### 37.
Consider the following method.

```java
public static String compress(String s) {
    String result = "";
    int i = 0;
    while (i < s.length()) {
        String c = s.substring(i, i + 1);
        int cnt = 0;
        while (i < s.length() && s.substring(i, i + 1).equals(c)) {
            cnt++;
            i++;
        }
        result += c + cnt;
    }
    return result;
}
```

What is returned by the method call `compress("aabbbccaa")`?

(A) "a2b3c2a2"
(B) "a4b3c2"
(C) "aabbbccaa"
(D) "a2b3c2a1"

---

### 38.
Which of the following code segments produces the same output as the code segment below?

```java
String obj1 = new String("hello");
String obj2 = new String("hello");
System.out.println(obj1.equals(obj2));
```

(A)
```java
System.out.println("hello" == "hello");
```
(B)
```java
System.out.println("hello".equals(new String("hello")));
```
(C)
```java
System.out.println(obj1 == obj2);
```
(D) Both (A) and (B)

---

### 39.
What is printed as a result of executing the code segment?
```java
String s = "AP-CSA-EXAM";
String[] parts = s.split("-");
String result = parts[2] + parts[0] + parts[1];
System.out.println(result + " (" + result.length() + ")");
```
(A) APCSAEXAM (9)
(B) CSAEXAMAP (9)
(C) EXAM-AP-CSA (11)
(D) EXAMAPCSA (9)

---

### 40.
Consider the following method.

```java
public static void process(ArrayList<Integer> data) {
    for (int i = 0; i < data.size(); i++) {
        data.set(i, data.get(i) * 2);
    }
    data.add(100);
}
```

What is the content of `list` after executing `process(list)`, given `list` is initially `[3, 6, 9]`?

(A) [3, 6, 9]
(B) [6, 12, 18]
(C) [6, 12, 18, 100]
(D) [3, 6, 9, 100]

---

### 41.
Which of the following code segments produces the same output as the code segment below?

```java
int[][] board = {
    {1, 2, 3, 4},
    {5, 6, 7, 8},
    {9, 10, 11, 12}
};
int sum = 0;
for (int j = 0; j < board[0].length; j++) {
    sum += board[board.length - 1][j];
}
System.out.println(sum / board[0].length);
```

(A)
```java
int sum = 0;
for (int val : board[2]) {
    sum += val;
}
System.out.println(sum / 4);
```
(B)
```java
System.out.println((9 + 10 + 11 + 12) / 4);
```
(C)
```java
int avg = 0;
for (int j = 0; j < 4; j++) {
    avg += board[2][j];
}
System.out.println(avg / board[0].length);
```
(D) All of the above

---

### 42.
Consider the following recursive method.

```java
public static String mystery(String s) {
    if (s.length() <= 1) return s;
    return mystery(s.substring(1)) + s.substring(0, 1);
}
```

What is returned by the method call `mystery("abcd")`?

(A) "abcd"
(B) "bcda"
(C) "dcba"
(D) "dabc"

---

## 정답표

> Unit 매핑: CED 2025-26 4-Unit 체계 — U1 (Using Objects and Methods 1.1-1.15), U2 (Selection and Iteration 2.1-2.12), U3 (Class Creation 3.1-3.9), U4 (Data Collections 4.1-4.17, recursion 포함)

| 번호 | 정답 | Unit | 토픽 | 해설 |
|------|------|------|------|------|
| 1 | B | U1 | 1.3 Expressions (정수 나눗셈/나머지) | `17/5`는 정수 나눗셈으로 3, `17%5`는 2 → "3 2" |
| 2 | B | U2 | 2.11 Nested Iteration | i=1→j 4회, i=2→3회, i=3→2회, i=4→1회 = 10 |
| 3 | B | U1 | 1.15 String.substring | `substring(2,5)` = "MPU" (인덱스2,3,4), `substring(0,1)` = "C" → "MPUC" |
| 4 | A | U1 | 1.5 Casting | `(double)10/3`=3.333..., ×10=33.333..., `(int)` 캐스팅→33 |
| 5 | A | U4 | 4.16 Recursion (트레이싱) | mystery(5)=5+mystery(3)=5+3+mystery(1)=5+3+1=9 |
| 6 | D | U1 | 1.11 Math 메서드 | `pow(2,3)`=8.0, `sqrt(16)`=4.0, `abs(-7.5)`=7.5 → 합=19.5, `(int)`=19 |
| 7 | A | U2 | 2.10 String 알고리즘 (역순) | i=5→"f", i=3→"d", i=1→"b" (substring으로 추출) → "fdb" |
| 8 | B | U2 | 2.7 while Loops | 100→33→11→3→1, n=1이면 n>1 거짓이므로 종료. 4회 실행 |
| 9 | A | U4 | 4.8 ArrayList add/remove | [5]→[5,10]→[5,10,15]→add(1,20)→[5,20,10,15]→remove(2)→[5,20,15] |
| 10 | B | U4 | 4.13 2D Array Algorithms (반대 대각선) | grid[0][2]=3, grid[1][1]=5, grid[2][0]=7 → 합=15 |
| 11 | C | U2 | 2.10 String 알고리즘 (substring 트레이싱) | "AB C": A→AA, B→BB, " "→"_", C→CC → "AABB_CC" |
| 12 | D | U1 | 1.5 Casting + 1.11 Math | `(double)7/2`=3.5, `Math.pow(2,3)`=8.0, `(int)`=8 → "3.5 8" |
| 13 | A | U4 | 4.16 Recursion (트레이싱) | 재귀 전 출력: 4,3,2,1, 재귀 후 출력: 1,2,3,4 → "4 3 2 1 1 2 3 4" |
| 14 | B | U2 | 2.5 Compound Boolean | (true\|\|false)=true, (!true\|\|false)=false, true&&false=false |
| 15 | B | U3 | 3.3 Anatomy of a Class + 3.5 Methods | `scramble()`은 문자열을 역순으로 반환. "HELLO" → "OLLEH" |
| 16 | B | U3 | 3.5 Methods (instance method 결과 추적) | `hint(2)` → "JA"+"__"="JA__"; `isGuessCorrect("java")` → "JAVA".equals("java")=false |
| 17 | B | U3 | 3.5 Methods (엣지 케이스 추적) | `hint(5)`: numChars(5)>length(2) → 2로 조정 → "AB". `scramble()`="BA" 두 번 동일 → equals=true |
| 18 | C | U4 | 4.11 2D Array Indexing | m[2][1]=2*4+1=9, m[1][3]=1*4+3=7 → 합=16 |
| 19 | B | U4 | 4.16 Recursion (피보나치 트레이싱) | calc(6)=calc(5)+calc(4)=5+3=8 |
| 20 | B | U2 | 2.10 String 알고리즘 (substring 모음) | 각 단어의 첫 글자: c+b+r+h = "cbrh" |
| 21 | A | U1 | 1.6 Compound Assignment | `length()`=8, +=5→13, -=2→11, *=2→22 |
| 22 | C | U2 | 2.9 표준 알고리즘 (frequency count) | i² = 0,1,4,9,16,25,36,49,64,81. 홀수(1,9,25,49,81) 5개 제거 → 5개 남음 |
| 23 | D | U2 | 2.9 자릿수 추출 표준 알고리즘 | 매 반복 마지막 자릿수 추출하여 조합 → 4321 |
| 24 | C | U3 | 3.4 Constructors + 3.5 Methods | 생성자 내 increment×2=+6, decrement×1=-1, 최종=5 |
| 25 | A | U4 | 4.12 2D Traversals (열 순회) | 열0: {1,0,1}/열1: {0,1,1}/열2: {1,0,0} — 모든 열에 0 존재 → count=0 |
| 26 | A | U4 | 4.17.B Binary Search | {1,3,5,7,9,11,13}에서 7은 인덱스 3 |
| 27 | D | U1 | 1.15 String (substring + indexOf) | indexOf("d")=3, left="abc", right="efg" → "efg"+"abc"="efgabc" |
| 28 | B | U2 | 2.4 Nested if | x=5>3→내부: 5>10 거짓→"B" 출력. 이후 "D" → "BD" |
| 29 | B | U4 | 4.10 ArrayList Linear Search | min=1, minIdx=4 (linear search loop), remove(4) → [4,7,2,9] |
| 30 | A | U4 | 4.13 2D Array Algorithms (상삼각) | i<j인 원소: mat[0][1]=3, mat[0][2]=8, mat[1][2]=2 → 합=13 |
| 31 | A | U4 | 4.16 Recursion (거듭제곱 트레이싱) | power(3,4)→half=power(3,2)→half=power(3,1)=3→3×3=9, 9×9=81 |
| 32 | C | U4 | 4.15 Selection Sort (1 pass) | min=arr[3]=1, swap with arr[0]=5 → {1,3,8,5,2} |
| 33 | A | U2 | 2.10 String 알고리즘 (회문) | "racecar"는 회문 → true |
| 34 | C | U2 | 2.11 Nested Iteration (소수 카운트) | 2,3,5,7,11,13,17,19 = 8개 |
| 35 | D | U4 | 4.10 ArrayList while 삭제 | red 제거 시 인덱스 증가 안 함 → [blue, green, blue] |
| 36 | C | U4 | 4.13 2D Array Algorithms (대각선) | grid[1][2]=2, grid[2][1]=2, grid[0][3]=2, grid[3][0]=2 → 합=8 |
| 37 | A | U2 | 2.10 String 알고리즘 (압축) | 연속 substring 카운트: a2 b3 c2 a2 → "a2b3c2a2" |
| 38 | D | U1 | 1.15 String.equals vs == | (A) 리터럴 풀에서 동일 참조 → true. (B) equals는 내용 비교 → true. (C) new String끼리 == → false. (A)와 (B) 모두 true. |
| 39 | D | U2 | 2.10 String 알고리즘 (split + 결합) | split("-") → ["AP","CSA","EXAM"], parts[2]+parts[0]+parts[1]="EXAMAPCSA" (length=9) |
| 40 | C | U3 | 3.6 Passing References | 참조 전달이므로 원본 수정: ×2 후 100 추가 → [6,12,18,100] |
| 41 | D | U4 | 4.13 2D Array Algorithms | 마지막 행 합 9+10+11+12=42, 42/4=10. 세 보기 모두 10 출력 |
| 42 | C | U4 | 4.16 Recursion (문자열 뒤집기 트레이싱) | mystery("bcd")+"a" → mystery("cd")+"b"+"a" → ... → "dcba" |

### Unit 분포 (CED 2025-26)
| Unit | 문항 수 | 비율 | CED 기준 | 합치 |
|------|---------|------|---------|------|
| U1 (Using Objects and Methods) | 8 | 19.0% | 15-25% | OK |
| U2 (Selection and Iteration) | 13 | 31.0% | 25-35% | OK |
| U3 (Class Creation) | 5 | 11.9% | 10-18% | OK |
| U4 (Data Collections) | 16 | 38.1% | 30-40% | OK |
| 합계 | 42 | 100.0% | | |

**문항 매핑 요약:**
- **U1 (8)**: Q1, Q3, Q4, Q6, Q12, Q21, Q27, Q38
- **U2 (13)**: Q2, Q7, Q8, Q11, Q14, Q20, Q22, Q23, Q28, Q33, Q34, Q37, Q39
- **U3 (5)**: Q15, Q16, Q17, Q24, Q40
- **U4 (16)**: Q5, Q9, Q10, Q13, Q18, Q19, Q25, Q26, Q29, Q30, Q31, Q32, Q35, Q36, Q41, Q42

### 정답 분포
| 정답 | 개수 | 비율 |
|------|------|------|
| A | 12 | 28.6% |
| B | 13 | 31.0% |
| C | 9 | 21.4% |
| D | 8 | 19.0% |
| 합계 | 42 | 100.0% |
