# AP Computer Science A — Mock Exam Set 2: Multiple Choice

**Directions:** Determine the answer to each of the following questions or incomplete statements, using the available space for any necessary scratch work. Then decide which is the best of the choices given and fill in the corresponding circle on the answer sheet. A Java Quick Reference is provided as part of the exam.

> 42 Questions | 90 Minutes | 4 Choices (A-D)

---

## Unit 1: Primitive Types (8 Questions)

### Q1
What is printed as a result of executing the code segment?

```java
int a = 7;
int b = 2;
double c = (double)(a / b);
System.out.println(c);
```

(A) 3.5
(B) 3.0
(C) 3
(D) A compile-time error occurs

---

### Q2
Which of the following code segments compiles without error?

```java
// I
int x = 3.14;
// II
double y = 5;
// III
boolean z = 1;
// IV
int w = "7";
```

(A) I only
(B) II only
(C) II and IV
(D) I and III

---

### Q3
What is printed as a result of executing the code segment?

```java
int x = 13 % 5;
int y = -13 % 5;
System.out.println(x + " " + y);
```

(A) 3 3
(B) 3 -3
(C) 2 -2
(D) 3 2

---

### Q4
What is printed as a result of executing the code segment?

```java
int total = 7;
int count = 2;
double average = (double) total / count;
System.out.println(average);
```

(A) 3.0
(B) 3.5
(C) 4.0
(D) 3

---

### Q5
What is printed as a result of executing the code segment?

```java
double d = 2.9;
int k = (int) d;
System.out.println(k);
```

(A) 3
(B) 2
(C) 2.0
(D) A compile-time error occurs

---

### Q6
Consider the following three code segments.

```java
// I
int a = Integer.MAX_VALUE + 1;
// II
long b = (long) Integer.MAX_VALUE + 1;
// III
int c = Integer.MAX_VALUE;
c++;
```

Which of the code segments will cause integer overflow?

(A) I only
(B) I and III only
(C) II and III only
(D) I, II, and III

---

### Q7
What is printed as a result of executing the code segment?

```java
double result = 1 / 3 + 1.0 / 3;
System.out.println(result);
```

(A) 0.6666666666666666
(B) 0.3333333333333333
(C) 0
(D) 0.0

---

### Q8
What is the type of the result of the following expression?

```java
5 + 3.0 + 2
```

(A) `int`
(B) `double`
(C) `float`
(D) A compile-time error occurs

---

## Unit 2: Using Objects (13 Questions)

### Q9
What is printed as a result of executing the code segment?

```java
String s1 = "hello";
String s2 = "hello";
String s3 = new String("hello");
System.out.println((s1 == s2) + " " + (s1 == s3));
```

(A) true true
(B) true false
(C) false false
(D) false true

---

### Q10
What is printed as a result of executing the code segment?

```java
String str = "ABCDEFG";
System.out.println(str.substring(2, 5));
```

(A) CDE
(B) BCD
(C) BCDE
(D) CDEF

---

### Q11
What is printed as a result of executing the code segment?

```java
String word = "banana";
int idx = word.indexOf("na");
System.out.println(idx);
```

(A) 1
(B) 2
(C) 3
(D) 4

---

### Q12
What is printed as a result of executing the code segment?

```java
String s = "Hello";
s.toUpperCase();
s.concat(" World");
System.out.println(s);
```

(A) HELLO World
(B) HELLO
(C) Hello World
(D) Hello

---

### Q13
Consider the following code segment.

```java
String sentence = "The quick brown fox";
```

Which of the following method calls returns `-1`?

(A) `sentence.indexOf("quick")`
(B) `sentence.indexOf("fox")`
(C) `sentence.indexOf("cat")`
(D) `sentence.indexOf("The")`

---

### Q14
What is printed as a result of executing the code segment?

```java
String a = "3";
String b = "12";
System.out.println(a.compareTo(b));
```

Which of the following best describes the output?

(A) A negative integer
(B) 0
(C) A positive integer
(D) A compile-time error occurs

---

### Q15.
### Questions 15-17 refer to the following class.

```java
public class ShoppingCart {
    private ArrayList<Double> prices;

    public ShoppingCart() {
        prices = new ArrayList<Double>();
    }

    public void addItem(double price) {
        if (price > 0) {
            prices.add(price);
        }
    }

    public double getTotal() {
        double sum = 0;
        for (double p : prices) {
            sum += p;
        }
        return sum;
    }

    public int removeExpired(double maxPrice) {
        int removed = 0;
        for (int i = prices.size() - 1; i >= 0; i--) {
            if (prices.get(i) > maxPrice) {
                prices.remove(i);
                removed++;
            }
        }
        return removed;
    }

    public int getItemCount() {
        return prices.size();
    }
}
```

What is printed as a result of executing the code segment?

```java
ShoppingCart cart = new ShoppingCart();
cart.addItem(5.99);
cart.addItem(12.50);
cart.addItem(-3.00);
cart.addItem(8.75);
System.out.println(cart.getItemCount() + " " + cart.getTotal());
```

(A) `4 24.24`
(B) `3 27.24`
(C) `3 24.24`
(D) `4 27.24`

---

### Q16.
What is printed as a result of executing the code segment?

```java
ShoppingCart cart = new ShoppingCart();
cart.addItem(5.00);
cart.addItem(15.00);
cart.addItem(8.00);
cart.addItem(20.00);
cart.addItem(3.00);
int removed = cart.removeExpired(10.00);
System.out.println(removed + " " + cart.getTotal());
```

(A) `2 16.0`
(B) `3 16.0`
(C) `2 51.0`
(D) `2 35.0`

---

### Q17.
What is printed as a result of executing the code segment?

```java
ShoppingCart cart1 = new ShoppingCart();
cart1.addItem(10.00);
cart1.addItem(20.00);
ShoppingCart cart2 = cart1;
cart2.addItem(30.00);
System.out.println(cart1.getItemCount() + " " + cart1.getTotal());
```

(A) `2 30.0`
(B) `3 60.0`
(C) `3 30.0`
(D) `2 60.0`

---

### Q18
What is printed as a result of executing the code segment?

```java
String str = null;
if (str != null && str.length() > 0) {
    System.out.println("Not empty");
} else {
    System.out.println("Empty or null");
}
```

(A) Not empty
(B) Empty or null
(C) NullPointerException
(D) A compile-time error occurs

---

### Q19
Consider the following code segment, which is intended to check whether a `String` is a palindrome.

```java
String word = "racecar";
int len = word.length();
boolean isPalindrome = true;
for (int i = 0; i < len / 2; i++) {
    if (/* blank */) {
        isPalindrome = false;
    }
}
```

Which of the following should replace `/* blank */` so that the code works as intended?

(A) `word.substring(i, i+1) != word.substring(len-1-i, len-i)`
(B) `word.charAt(i) != word.charAt(len - 1 - i)`
(C) `word.charAt(i) != word.charAt(len - i)`
(D) `word.substring(i) != word.substring(len - 1 - i)`

---

### Q20
Consider the following code segment.

```java
String s = "hello world";
int space = s.indexOf(" ");
String first = s.substring(0, space);
String second = s.substring(space + 1);
System.out.println(first + "-" + second);
```

What is printed?

(A) `"hello-world"`
(B) `"hello- world"`
(C) `" hello-world"`
(D) `"hello -world"`

---

### Q21
What is printed as a result of executing the code segment?

```java
String s = "Java";
s = s + " " + s.length();
System.out.println(s);
```

(A) Java 4
(B) Java Java
(C) Java 8
(D) A compile-time error occurs

---

## Unit 3: Boolean Expressions and if Statements (6 Questions)

### Q22
What is printed as a result of executing the code segment?

```java
int x = 5;
if (x > 3)
    if (x > 10)
        System.out.println("A");
    else
        System.out.println("B");
else
    System.out.println("C");
```

(A) A
(B) B
(C) C
(D) Nothing is printed

---

### Q23
Which of the following is equivalent to `!(a && !b)` by De Morgan's Law?

(A) `!a && b`
(B) `!a || b`
(C) `a || !b`
(D) `a && b`

---

### Q24
Which of the following best describes why the code does not work as intended?

The following method is intended to return the letter grade for a given score. However, it does not always produce the correct result.

```java
public static String getGrade(int score) {
    String grade = "";
    if (score >= 70) grade = "C";
    if (score >= 80) grade = "B";
    if (score >= 90) grade = "A";
    return grade;
}
```

For example, `getGrade(75)` correctly returns `"C"`, but there is still a problem.

(A) The method never returns `"F"` for scores below 70.
(B) The method should use `else if` instead of separate `if` statements.
(C) The condition `score >= 90` should be `score > 90`.
(D) The method returns the wrong grade for scores of 80 or above.

---

### Q25
Which of the following correctly checks whether `x` is between 10 and 20 inclusive?

(A) `10 <= x <= 20`
(B) `x >= 10 && x <= 20`
(C) `x >= 10 || x <= 20`
(D) `x > 10 && x < 20`

---

### Q26
What is printed as a result of executing the code segment?

```java
double a = 0.1 + 0.2;
double b = 0.3;
if (a == b)
    System.out.println("Equal");
else
    System.out.println("Not Equal");
```

(A) Always prints "Equal"
(B) Always prints "Not Equal"
(C) Varies between runs
(D) A compile-time error occurs

---

### Q27
Which of the following is equivalent to `!(x > 5 || y < 3)`?

(A) `x > 5 && y < 3`
(B) `x <= 5 && y >= 3`
(C) `x <= 5 || y >= 3`
(D) `x < 5 && y > 3`

---

## Unit 4: Iteration, Arrays, ArrayList, 2D Arrays, Recursion, Classes (15 Questions)

### Q28
What is printed as a result of executing the code segment?

```java
int sum = 0;
for (int i = 1; i <= 10; i++) {
    if (i % 3 == 0)
        continue;
    sum += i;
}
System.out.println(sum);
```

(A) 55
(B) 37
(C) 18
(D) 33

---

### Q29
Which of the following best describes why the code does not work as intended?

The following code is intended to double every element in the array.

```java
int[] arr = {2, 4, 6, 8, 10};
for (int val : arr) {
    val = val * 2;
}
System.out.println(arr[2]);
```

(A) The enhanced for loop variable `val` is a copy of the array element, so assigning to `val` does not modify the original array.
(B) The condition `val * 2` causes integer overflow.
(C) The enhanced for loop does not iterate over all elements.
(D) The code works as intended and prints `12`.

---

### Q30
What is printed as a result of executing the code segment?

```java
ArrayList<Integer> list = new ArrayList<>();
list.add(10);
list.add(20);
list.add(30);
list.add(40);

for (int i = 0; i < list.size(); i++) {
    if (list.get(i) == 20 || list.get(i) == 30) {
        list.remove(i);
    }
}
System.out.println(list);
```

(A) [10, 40]
(B) [10, 30, 40]
(C) [10, 20, 40]
(D) [10, 40, 40]

---

### Q31
What is printed as a result of executing the code segment?

```java
int[][] grid = new int[3][4];
int count = 0;
for (int c = 0; c < grid[0].length; c++) {
    for (int r = 0; r < grid.length; r++) {
        grid[r][c] = count++;
    }
}
System.out.println(grid[1][2]);
```

(A) 6
(B) 7
(C) 5
(D) 8

---

### Q32
Consider the following recursive method.

```java
public static int mystery(int n) {
    if (n <= 1)
        return 1;
    return n + mystery(n - 2);
}
```

What value is returned by the method call `mystery(5)`?

(A) 9
(B) 15
(C) 6
(D) 5

---

### Q33
What is printed as a result of executing the code segment?

```java
int n = 128;
int count = 0;
while (n > 1) {
    n /= 2;
    count++;
}
System.out.println(count);
```

(A) 6
(B) 7
(C) 8
(D) 128

---

### Q34
What is printed as a result of executing the code segment?

```java
int[] arr = {5, 3, 8, 1, 9, 2};
int max = arr[0];
int maxIdx = 0;
for (int i = 1; i < arr.length; i++) {
    if (arr[i] >= max) {
        max = arr[i];
        maxIdx = i;
    }
}
System.out.println(maxIdx);
```

(A) 4
(B) 5
(C) 9
(D) 2

---

### Q35
What is printed as a result of executing the code segment?

```java
ArrayList<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");
names.add("Charlie");
names.add(1, "Diana");
names.set(3, "Eve");
System.out.println(names);
```

(A) [Alice, Diana, Bob, Eve]
(B) [Alice, Diana, Bob, Charlie]
(C) [Diana, Alice, Bob, Eve]
(D) [Alice, Diana, Charlie, Eve]

---

### Q36
Which of the following code segments produces the same output as the code segment below?

```java
String[] words = {"cat", "bat", "rat", "hat"};
String result = "";
for (String w : words) {
    result += w.substring(0, 1);
}
System.out.println(result);
```

(A)
```java
String result = "";
for (int i = 0; i < words.length; i++) {
    result += words[i].charAt(0);
}
System.out.println(result);
```
(B)
```java
String result = "" + words[0].charAt(0) + words[1].charAt(0)
              + words[2].charAt(0) + words[3].charAt(0);
System.out.println(result);
```
(C)
```java
String result = "";
for (String w : words) {
    result = w.substring(0, 1) + result;
}
System.out.println(result);
```
(D) Both (A) and (B)

---

### Q37
What is printed as a result of executing the code segment?

```java
int[][] mat = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
int sum = 0;
for (int i = 0; i < mat.length; i++) {
    sum += mat[i][i];
}
System.out.println(sum);
```

(A) 12
(B) 15
(C) 45
(D) 6

---

### Q38
Consider the following recursive method.

```java
public static void trace(String s) {
    if (s.length() <= 1) {
        System.out.print(s);
        return;
    }
    System.out.print(s.charAt(0));
    trace(s.substring(2));
    System.out.print(s.charAt(1));
}
```

What is printed as a result of the method call `trace("ABCD")`?

(A) ABCD
(B) ACDB
(C) ABDC
(D) ADCB

---

### Q39
Consider the following class.

```java
public class Dog {
    private String name;
    private int age;

    public Dog(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String toString() {  // Line A
        return name + " (" + age + ")";
    }
}
```

Which of the following causes a compile-time error?

```java
Dog d = new Dog("Buddy", 3);
System.out.println(d.name);  // Line B
System.out.println(d);       // Line C
```

(A) Line A
(B) Line B
(C) Line C
(D) No error occurs

---

### Q40
What is printed as a result of executing the code segment?

```java
ArrayList<Integer> nums = new ArrayList<>();
for (int i = 0; i < 5; i++) {
    nums.add(i * 10);
}
// nums = [0, 10, 20, 30, 40]

for (int i = nums.size() - 1; i >= 0; i--) {
    if (nums.get(i) % 20 == 0) {
        nums.remove(i);
    }
}
System.out.println(nums);
```

(A) [10, 30]
(B) [10, 30, 40]
(C) [0, 10, 30]
(D) [10, 30, 50]

---

### Q41
Which of the following best describes why the code does not work as intended?

The following method is intended to count the number of lines in a file, but does not compile.

```java
public static int countLines(String filename) {
    Scanner sc = new Scanner(new File(filename));
    int count = 0;
    while (sc.hasNextLine()) {
        sc.nextLine();
        count++;
    }
    sc.close();
    return count;
}
```

(A) `Scanner` does not have a `hasNextLine()` method.
(B) `new File(filename)` is not valid Java syntax.
(C) `new Scanner(new File(filename))` can throw a checked exception (`FileNotFoundException`) that must be declared or caught.
(D) `sc.close()` causes a compile-time error.

---

### Q42
What is printed as a result of executing the code segment?

```java
int[][] board = new int[4][4];
for (int r = 0; r < 4; r++) {
    for (int c = 0; c < 4; c++) {
        if (r == c || r + c == 3)
            board[r][c] = 1;
    }
}
int total = 0;
for (int[] row : board) {
    for (int val : row) {
        total += val;
    }
}
System.out.println(total);
```

(A) 6
(B) 8
(C) 7
(D) 4

---

## 정답표

| # | 정답 | Unit | 토픽 | 해설 |
|---|------|------|------|------|
| 1 | B | 1 | 정수 나눗셈 + 캐스팅 | `a / b`는 `7 / 2 = 3` (정수 나눗셈). 이후 `(double)3`은 `3.0`. `(double)`을 나눗셈 전에 적용해야 3.5가 됨. |
| 2 | B | 1 | 타입 변환 | `double y = 5;`는 int→double 자동 확대(widening) 변환으로 합법. 나머지는 축소 변환이거나 타입 불일치. |
| 3 | B | 1 | 나머지 연산자 | Java에서 `%` 결과의 부호는 피제수(왼쪽 피연산자)를 따름. `13 % 5 = 3`, `-13 % 5 = -3`. |
| 4 | B | 1 | 정수 나눗셈 + 캐스팅 순서 | `(double) total`이 먼저 평가되어 7.0이 됨. `7.0 / 2` = `3.5`. 캐스팅이 나눗셈보다 먼저 적용되는 것이 핵심. |
| 5 | B | 1 | double→int 캐스팅 | `(int)` 캐스팅은 소수점 이하를 버림(truncation). `2.9` → `2`. 반올림이 아님. |
| 6 | B | 1 | 정수 오버플로우 | I: `MAX_VALUE + 1`은 오버플로우 발생. II: `(long)` 캐스팅 후 덧셈이므로 안전. III: `c++`도 오버플로우 발생. |
| 7 | B | 1 | 정수 나눗셈 혼합 | `1 / 3 = 0` (정수 나눗셈), `1.0 / 3 ≈ 0.333...`. 합은 약 `0.333...`. |
| 8 | B | 1 | 자동 타입 승격 | `5 + 3.0`에서 5가 double로 승격 → `8.0 + 2` → `10.0`. 결과는 `double`. |
| 9 | B | 2 | == vs equals, String pool | `s1`, `s2`는 String pool의 같은 객체 → `==` true. `s3`는 `new`로 별도 객체 생성 → `==` false. |
| 10 | A | 2 | substring 범위 | `substring(2, 5)`는 인덱스 2부터 4까지(5 미포함). "ABCDEFG"에서 인덱스 2='C', 3='D', 4='E' → "CDE". |
| 11 | B | 2 | indexOf | "banana"에서 "na"가 처음 나타나는 위치는 인덱스 2 (b=0, a=1, n=2). |
| 12 | D | 2 | String 불변성 | `toUpperCase()`와 `concat()`은 새 String을 반환하지만 `s`에 재할당하지 않음. `s`는 원래 "Hello" 유지. |
| 13 | C | 2 | indexOf 반환값 -1 | "cat"은 문자열에 없으므로 `indexOf("cat")`는 `-1` 반환. |
| 14 | C | 2 | compareTo 사전순 | `"3".compareTo("12")`: '3'(코드 51) vs '1'(코드 49) → 양수. 숫자의 크기가 아닌 문자 코드 비교. |
| 15 | B | 2 | ShoppingCart 클래스 이해 | `addItem(-3.00)`은 price <= 0이므로 무시. 3개 아이템(5.99+12.50+8.75=27.24) 추가. |
| 16 | A | 2 | removeExpired 메서드 추적 | maxPrice=10.00보다 큰 15.00과 20.00이 제거됨(2개). 남은 합: 5+8+3=16.0. |
| 17 | B | 2 | 참조 공유 | `cart2 = cart1`은 같은 객체 참조. `cart2.addItem(30.00)`은 원본도 변경. 3개 아이템, 합 60.0. |
| 18 | B | 2 | 단축 평가 | `str != null`이 false이므로 `&&` 단축 평가로 `str.length()`를 실행하지 않음. NullPointerException 발생 안 함. |
| 19 | B | 2 | charAt vs substring | `charAt()`은 char 비교(`!=` 사용 가능). (A)는 `!=`로 String 비교하므로 참조 비교가 됨. (C)는 인덱스 오류. |
| 20 | A | 2 | indexOf + substring | `indexOf(" ")`는 5 반환. `substring(0,5)` = "hello", `substring(6)` = "world". 결과: "hello-world". |
| 21 | A | 2 | String 연결 | `s.length()`는 "Java"의 길이 4. `"Java" + " " + 4` → `"Java 4"`. length()는 원래 s 기준. |
| 22 | B | 3 | dangling else | `else`는 가장 가까운 `if`와 짝을 이룸. `x > 3` true, `x > 10` false → "B" 출력. |
| 23 | B | 3 | De Morgan's Law | `!(a && !b)` = `!a || !!b` = `!a || b`. |
| 24 | A | 3 | if vs else-if 에러 식별 | 현재 코드는 독립 `if`문이라 score<70일 때 `grade`가 빈 문자열. `"F"`를 반환하는 조건이 없음. |
| 25 | B | 3 | 복합 조건 | (A)는 Java 문법 에러. (C)는 모든 수에 대해 true. (D)는 10과 20을 포함하지 않음. |
| 26 | B | 3 | 부동소수점 비교 | `0.1 + 0.2`는 부동소수점 오차로 정확히 `0.3`이 아님. `==` 비교는 false. |
| 27 | B | 3 | De Morgan's Law | `!(x > 5 || y < 3)` = `!(x > 5) && !(y < 3)` = `x <= 5 && y >= 3`. |
| 28 | B | 4 | for 루프 + continue | 1+2+4+5+7+8+10 = 37. `i=3,6,9`일 때 continue로 건너뜀. |
| 29 | A | 4 | enhanced for 배열 수정 불가 | enhanced for의 `val`은 배열 요소의 복사본. `val = val * 2`는 배열을 변경하지 않음. |
| 30 | B | 4 | ArrayList remove 인덱스 밀림 | i=1에서 20 제거 → list=[10,30,40], size=3. i=2에서 40 검사(30이 아닌 40). 30은 건너뜀. |
| 31 | B | 4 | 2D array column-major | column-major 순서: (0,0)=0,(1,0)=1,(2,0)=2,(0,1)=3,(1,1)=4,(2,1)=5,(0,2)=6,(1,2)=7. `grid[1][2]=7`. |
| 32 | A | 4 | 재귀 tracing | `mystery(5)` = 5 + `mystery(3)` = 5 + 3 + `mystery(1)` = 5 + 3 + 1 = 9. |
| 33 | B | 4 | while 루프 | 128→64→32→16→8→4→2→1, 7번 나눔. |
| 34 | A | 4 | 배열 최대값 | `>=` 사용이지만 최대값 9는 한 번만 등장. 인덱스 4에서 9. |
| 35 | A | 4 | ArrayList add/set | 초기 [Alice, Bob, Charlie]. `add(1, "Diana")` → [Alice, Diana, Bob, Charlie]. `set(3, "Eve")` → [Alice, Diana, Bob, Eve]. |
| 36 | D | 4 | 동치 코드 | 원본은 각 단어의 첫 글자 추출: "cbrh". (A)는 charAt(0)으로 동일. (B)는 수동으로 동일. (C)는 역순 "hbrc". (A)와 (B) 모두 올바름. |
| 37 | B | 4 | 2D 배열 대각선 | 대각선 원소: mat[0][0]=1, mat[1][1]=5, mat[2][2]=9. 합 = 15. |
| 38 | B | 4 | 재귀 + String | `trace("ABCD")`: print 'A' → `trace("CD")` → print 'B'. `trace("CD")`: print 'C' → `trace("")` → print 'D'. `trace("")`: length 0 ≤ 1이므로 print "" 후 return. 출력 순서: A → C → D → B = "ACDB". |
| 39 | B | 4 | 접근 제어자 private | `name`은 `private`이므로 외부 클래스에서 `d.name` 직접 접근 불가. Line B에서 컴파일 에러. |
| 40 | A | 4 | ArrayList 역순 삭제 | 역순으로 삭제하면 인덱스 밀림 문제 없음. 0, 20, 40이 `% 20 == 0`이므로 제거 → [10, 30]. |
| 41 | C | 4 | File/Scanner throws | `new Scanner(new File(...))`에서 `FileNotFoundException`(checked exception) 발생 가능. 이것이 `throws IOException` 필요 이유. |
| 42 | B | 4 | 2D 배열 패턴 | 주대각선(`r==c`): (0,0),(1,1),(2,2),(3,3) = 4개. 반대각선(`r+c==3`): (0,3),(1,2),(2,1),(3,0) = 4개. 4x4에서 두 조건 동시 만족 점 없음 → 총 8. |

---

*End*
