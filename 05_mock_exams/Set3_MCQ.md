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
int[] arr = {3, 7, 2, 8, 1};
int max = arr[0];
int idx = 0;
for (int i = 1; i < arr.length; i++) {
    if (arr[i] >= max) {
        max = arr[i];
        idx = i;
    }
}
System.out.println(idx);
```
(A) 3
(B) 4
(C) 8
(D) 1

---

### 7.
What is printed as a result of executing the code segment?
```java
String s = "abcdef";
String result = "";
for (int i = s.length() - 1; i >= 0; i -= 2) {
    result += s.charAt(i);
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
        if (s.charAt(i) != ' ')
            result += Character.toLowerCase(s.charAt(i));
        else
            result += "_";
    }
    return result;
}
```

What is returned by the method call `convert("Hello World")`?

(A) "hello_world"
(B) "Hello_World"
(C) "helloworld"
(D) "hello world"

---

### 12.
What is the content of `arr` after the code segment executes?
```java
int[] arr = {1, 2, 3, 4, 5};
for (int i = 0; i < arr.length / 2; i++) {
    int temp = arr[i];
    arr[i] = arr[arr.length - 1 - i];
    arr[arr.length - 1 - i] = temp;
}
```
(A) {5, 4, 3, 2, 1}
(B) {1, 2, 3, 4, 5}
(C) {5, 2, 3, 4, 1}
(D) {3, 2, 1, 4, 5}

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
(B) 16
(C) 15
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
    result += w.substring(0, 1).toUpperCase();
}
System.out.println(result);
```
(A) "CBRH"
(B) "cbrh"
(C) "Cat Bat Rat Hat"
(D) "catbatrathat"

---

### 21.
What is printed as a result of executing the code segment?
```java
int sum = 0;
for (int i = 1; i <= 100; i++) {
    if (i % 3 == 0 && i % 5 == 0) {
        sum++;
    }
}
System.out.println(sum);
```
(A) 6
(B) 7
(C) 5
(D) 33

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
(A) 5
(B) 6
(C) 7
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
(A) 4321
(B) 1234
(C) 432
(D) 43210

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
Which of the following best describes why the code does not work as intended?

The following code is intended to convert a string to uppercase and append " IS FUN".

```java
String str = "Java";
str.concat(" is fun");
str.toUpperCase();
System.out.println(str);
```

(A) `concat()` and `toUpperCase()` are not valid `String` methods.
(B) The `String` class does not allow modification; the return values of `concat()` and `toUpperCase()` are not reassigned to `str`.
(C) `toUpperCase()` should be called before `concat()`.
(D) The code works as intended and prints `"JAVA IS FUN"`.

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
ArrayList<Integer> nums = new ArrayList<>();
nums.add(4);
nums.add(7);
nums.add(2);
nums.add(9);
nums.add(1);

int min = Integer.MAX_VALUE;
for (int n : nums) {
    if (n < min) min = n;
}
nums.remove(nums.indexOf(min));
System.out.println(nums);
```
(A) [4, 7, 2, 9]
(B) [7, 2, 9, 1]
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
What is the state of `arr` after the code segment executes? (One pass of bubble sort)
```java
int[] arr = {5, 3, 8, 1, 2};
for (int i = 0; i < arr.length - 1; i++) {
    if (arr[i] > arr[i + 1]) {
        int temp = arr[i];
        arr[i] = arr[i + 1];
        arr[i + 1] = temp;
    }
}
```
(A) {3, 5, 1, 2, 8}
(B) {1, 2, 3, 5, 8}
(C) {3, 5, 8, 1, 2}
(D) {5, 3, 1, 2, 8}

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
(A) [blue, green, blue]
(B) [blue, green, red, blue]
(C) [red, blue, green, blue]
(D) [blue, green]

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
        char c = s.charAt(i);
        int cnt = 0;
        while (i < s.length() && s.charAt(i) == c) {
            cnt++;
            i++;
        }
        result += "" + c + cnt;
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
int[] arr = {10, 20, 30, 40, 50};
int sum = 0;
for (int i = 0; i < arr.length; i += 2) {
    arr[i] = arr[i] / 10;
}
for (int val : arr) {
    sum += val;
}
System.out.println(sum);
```
(A) 66
(B) 69
(C) 150
(D) 15

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
(B) [6, 12, 18, 100]
(C) [6, 12, 18]
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
    return mystery(s.substring(1)) + s.charAt(0);
}
```

What is returned by the method call `mystery("abcd")`?

(A) "abcd"
(B) "dcba"
(C) "bcda"
(D) "dabc"

---

## 정답표

| 번호 | 정답 | Unit | 토픽 | 해설 |
|------|------|------|------|------|
| 1 | B | U1 | 정수 나눗셈과 나머지 | `17/5`는 정수 나눗셈으로 3, `17%5`는 2 |
| 2 | B | U4 | 중첩 루프 카운팅 | i=1→j 4회, i=2→3회, i=3→2회, i=4→1회 = 10 |
| 3 | B | U2 | String.substring() | `substring(2,5)` = "MPU" (인덱스2,3,4), `substring(0,1)` = "C" → "MPUC" |
| 4 | A | U1 | 형변환과 정수 캐스팅 | `(double)10/3`=3.333..., ×10=33.333..., `(int)` 캐스팅→33 |
| 5 | A | U4 | 재귀 호출 추적 | mystery(5)=5+mystery(3)=5+3+mystery(1)=5+3+1=9 |
| 6 | A | U4 | 배열 최대값 인덱스 | 최대값 8의 인덱스는 3 |
| 7 | A | U2 | String 역순 접근 | i=5→'f', i=3→'d', i=1→'b' → "fdb" |
| 8 | B | U4 | while 루프 추적 | 100→33→11→3→1, n=1이면 n>1 거짓이므로 종료. 4회 실행 |
| 9 | A | U3 | ArrayList add/remove | [5]→[5,10]→[5,10,15]→[5,20,10,15]→인덱스2 제거→[5,20,15] |
| 10 | B | U4 | 2D 배열 반대 대각선 | grid[0][2]=3, grid[1][1]=5, grid[2][0]=7 → 합=15 |
| 11 | A | U2 | 문자열 변환 | 공백→'_', 나머지→소문자 → "hello_world" |
| 12 | A | U4 | 배열 뒤집기 | i=0: 1↔5, i=1: 2↔4 → {5,4,3,2,1} |
| 13 | A | U4 | 재귀 출력 순서 | 재귀 전 4 3 2 1, 재귀 후 1 2 3 4 → "4 3 2 1 1 2 3 4" |
| 14 | B | U1 | 논리 연산자 | (true\|\|false)=true, (!true\|\|false)=false, true&&false=false |
| 15 | B | U2 | WordGame 클래스 이해 | `scramble()`은 문자열을 역순으로 반환. "HELLO" → "OLLEH" |
| 16 | B | U2 | 메서드 호출 결과 추적 | `hint(2)` → "JA" + "__" = "JA__". `isGuessCorrect("java")` → "JAVA".equals("java") = false (대소문자 구분) |
| 17 | B | U2 | 엣지 케이스 | `hint(5)` → numChars가 word.length(2)보다 크므로 2로 조정. "AB" 반환(밑줄 없음). `scramble()`="BA", 두 번 호출해도 동일 → "BA".equals("BA") = true |
| 18 | B | U4 | 2D 배열 인덱싱 | m[2][1]=9, m[1][3]=7, 합=16 |
| 19 | B | U4 | 피보나치 재귀 | calc(6)=calc(5)+calc(4)=5+3=8 |
| 20 | A | U2 | String 메서드 조합 | 각 첫 글자 대문자: C+B+R+H = "CBRH" |
| 21 | A | U4 | 루프+조건 카운팅 | 15의 배수: 15,30,45,60,75,90 = 6개 |
| 22 | A | U3 | ArrayList 역순 삭제 | i²: 0,1,4,9,16,25,36,49,64,81. 홀수(1,9,25,49,81) 5개 제거 → 5개 남음 |
| 23 | A | U4 | 정수 역순 | 매 반복 마지막 자릿수 추출하여 조합 → 4321 |
| 24 | C | U2 | 생성자와 메서드 | increment()×2=+6, decrement()×1=-1, 최종=5 |
| 25 | A | U4 | 2D 배열 열 순회 | 열0: 1,0,1 / 열1: 0,1,1 / 열2: 1,0,0 — 모든 열에 0 존재 → count=0 |
| 26 | A | U4 | 이진 탐색 | {1,3,5,7,9,11,13}에서 7은 인덱스 3 |
| 27 | B | U2 | String 불변성 에러 식별 | concat/toUpperCase 결과를 재할당하지 않아 원본 불변. String은 immutable이므로 반환값을 다시 할당해야 함. |
| 28 | B | U1 | 중첩 if-else | x=5>3→내부: 5>10 거짓→"B" 출력. 이후 "D" 출력 → "BD" |
| 29 | A | U3 | ArrayList 최소값 제거 | min=1, indexOf(1)=4, remove(4)→인덱스4 제거 → [4,7,2,9] |
| 30 | A | U4 | 2D 상삼각 합산 | i<j인 원소: mat[0][1]=3, mat[0][2]=8, mat[1][2]=2 → 합=13 |
| 31 | A | U4 | 재귀 거듭제곱 | power(3,4)→half=power(3,2)→half=power(3,1)=3→3×3=9→9×9=81 |
| 32 | A | U4 | 1패스 버블정렬 | 5>3교환→[3,5,8,1,2], 5<8패스, 8>1교환→[3,5,1,8,2], 8>2교환→[3,5,1,2,8] |
| 33 | A | U2 | 회문 판별 | "racecar"는 회문 → true |
| 34 | C | U4 | 소수 카운팅 | 2,3,5,7,11,13,17,19 = 8개 |
| 35 | A | U3 | ArrayList while 삭제 | red 제거 시 인덱스 증가 안 함 → [blue, green, blue] |
| 36 | C | U4 | 2D 대각선 패턴 | grid[1][2]=2, grid[2][1]=2, grid[0][3]=2, grid[3][0]=2 → 합=8 |
| 37 | A | U2 | 문자열 압축 | 연속 문자 카운트: a2 b3 c2 a2 → "a2b3c2a2" |
| 38 | D | U2 | == vs equals 동치 코드 | 원본은 `true` 출력. (A) 리터럴 "hello" == "hello"는 pool에서 같은 참조이므로 true. (B) .equals()로 내용 비교이므로 true. (C) new String끼리 ==는 false. (A)와 (B) 모두 true. |
| 39 | B | U4 | 배열 수정 후 합산 | arr={1,20,3,40,5}, 합=69 |
| 40 | B | U3 | ArrayList 참조 전달 | 참조 전달이므로 원본 수정: ×2 후 100 추가 → [6,12,18,100] |
| 41 | D | U4 | 동치 코드 | 마지막 행 합: 9+10+11+12=42, 42/4=10 (정수 나눗셈). 세 보기 모두 동일한 결과 10을 출력. |
| 42 | B | U4 | 재귀 문자열 뒤집기 | mystery("bcd")+'a'→mystery("cd")+'b'+'a'→..."dcba" |
