# AP Computer Science A — Mock Exam Set 1: Multiple Choice
## 42 Questions | 90 Minutes | 55% of Score

**Directions:** Determine the answer to each of the following questions or incomplete statements, using the available space for any necessary scratch work. Then decide which is the best of the choices given and fill in the corresponding circle on the answer sheet. A Java Quick Reference is provided as part of the exam.

---

### 1.
What is printed as a result of executing the code segment?

```java
int a = 17;
int b = 5;
double c = a / b;
System.out.println(c);
```

(A) `3.4`
(B) `3.0`
(C) `3`
(D) `3.4000000000000004`

---

### 2.
What is printed as a result of executing the code segment?

```java
int x = 10;
int y = 3;
System.out.println(x % y + x / y);
```

(A) `3`
(B) `4`
(C) `5`
(D) `6`

---

### 3.
What is printed as a result of executing the code segment?

```java
boolean flag;
int x = 10;
if (x > 5) {
    flag = true;
} else {
    flag = false;
}
System.out.println(flag);
```

(A) `true`
(B) `false`
(C) `0`
(D) A compile-time error occurs

---

### 4.
What is printed as a result of executing the code segment?

```java
double d = 2.9;
int n = (int) d;
System.out.println(n);
```

(A) `2`
(B) `3`
(C) `2.9`
(D) A compile-time error occurs

---

### 5.
What is printed as a result of executing the code segment?

```java
System.out.println(5 + 3 + "hello" + 5 + 3);
```

(A) `"53hello53"`
(B) `"8hello53"`
(C) `"8hello8"`
(D) `"53hello8"`

---

### 6.
What is printed as a result of executing the code segment?

```java
int a = 7;
int b = 2;
System.out.println((double) a / b);
```

(A) `3`
(B) `3.0`
(C) `3.5`
(D) A compile-time error occurs

---

### 7.
Which of the following is a valid variable declaration?

```java
// I
int 2ndPlace = 5;
// II
double my_score = 3.5;
// III
String class = "AP";
// IV
boolean isReady = true;
```

(A) I only
(B) II only
(C) II and IV only
(D) IV only

---

### 8.
What is printed as a result of executing the code segment?

```java
int x = Integer.MAX_VALUE;
x = x + 1;
System.out.println(x > 0);
```

(A) `true`
(B) `false`
(C) A compile-time error occurs
(D) A run-time error occurs

---

### 9.
What is printed as a result of executing the code segment?

```java
String s1 = "Hello";
String s2 = "Hello";
String s3 = new String("Hello");
System.out.println(s1 == s2);
System.out.println(s1 == s3);
```

(A) `true` `true`
(B) `true` `false`
(C) `false` `false`
(D) `false` `true`

---

### 10.
What is printed as a result of executing the code segment?

```java
String word = "Computer";
System.out.println(word.substring(3, 6));
```

(A) `"mpu"`
(B) `"put"`
(C) `"pute"`
(D) `"mput"`

---

### 11.
What is printed as a result of executing the code segment?

```java
String str = "AP Computer Science A";
int idx = str.indexOf("Science");
System.out.println(idx);
```

(A) `11`
(B) `12`
(C) `13`
(D) `14`

---

### 12.
What is printed as a result of executing the code segment?

```java
String a = "Java";
String b = a.toUpperCase();
System.out.println(a);
System.out.println(b);
```

(A) `JAVA` `JAVA`
(B) `Java` `JAVA`
(C) `Java` `Java`
(D) `JAVA` `Java`

---

### 13.
Consider the following method and method call.

```java
public static int mystery(String s) {
    int count = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s.substring(i, i + 1).equals("a")) {
            count++;
        }
    }
    return count;
}
// Call: mystery("banana")
```

What value is returned by the method call `mystery("banana")`?

(A) `2`
(B) `3`
(C) `4`
(D) `1`

---

### 14.
Which of the following code segments produces the same output as the code segment below?

```java
String s = "Hello World";
System.out.println(s.length());
```

(A) `System.out.println(s.substring(0).length());`
(B) `System.out.println(s.indexOf("d") + 1);`
(C) `System.out.println(s.indexOf(" ") + s.substring(6).length() + 1);`
(D) All of the above

---

### 15.
### Questions 15-17 refer to the following class.

```java
public class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        balance = initialBalance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public boolean withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            return true;
        }
        return false;
    }

    public double getBalance() {
        return balance;
    }
}
```

What is printed as a result of executing the code segment?

```java
BankAccount acct = new BankAccount(100.0);
acct.deposit(50.0);
acct.deposit(-20.0);
System.out.println(acct.getBalance());
```

(A) `130.0`
(B) `150.0`
(C) `100.0`
(D) `80.0`

---

### 16.
What is printed as a result of executing the code segment?

```java
BankAccount a = new BankAccount(200.0);
BankAccount b = a;
a.withdraw(50.0);
b.deposit(30.0);
System.out.println(a.getBalance());
```

(A) `150.0`
(B) `180.0`
(C) `200.0`
(D) `230.0`

---

### 17.
What is printed as a result of executing the code segment?

```java
BankAccount acct = new BankAccount(100.0);
boolean result1 = acct.withdraw(150.0);
boolean result2 = acct.withdraw(50.0);
System.out.println(result1 + " " + result2 + " " + acct.getBalance());
```

(A) `false true 50.0`
(B) `true true 0.0`
(C) `false false 100.0`
(D) `true false 50.0`

---

### 18.
What is printed as a result of executing the code segment?

```java
public class Pet {
    private String name;
    private int age;

    public Pet(int a) {
        age = a;
    }

    public String getName() { return name; }
}

Pet p = new Pet(3);
System.out.println(p.getName());
```

(A) A compile-time error occurs
(B) `""`
(C) `null`
(D) A run-time error occurs

---

### 19.
Which of the following best describes the result of executing the code segment?

```java
System.out.println(Math.abs(-7.5));
System.out.println((int)(Math.random() * 6) + 1);
```

(A) `7.5` followed by a random integer from 0 to 5
(B) `7.5` followed by a random integer from 1 to 6
(C) `7` followed by a random integer from 1 to 6
(D) `7.5` followed by a random integer from 0 to 6

---

### 20.
What is printed as a result of executing the code segment?

```java
String s1 = "apple";
String s2 = "banana";
System.out.println(s1.compareTo(s2) < 0);
```

(A) `true`
(B) `false`
(C) `0`
(D) A compile-time error occurs

---

### 21.
What is printed as a result of executing the code segment?

```java
int x = 15;
if (x > 10)
    System.out.print("A");
if (x > 5)
    System.out.print("B");
if (x > 20)
    System.out.print("C");
```

(A) `A`
(B) `AB`
(C) `ABC`
(D) `AC`

---

### 22.
Which of the following code segments produces the same output as the code segment below?

```java
int score = 85;
String grade;
if (score >= 90)
    grade = "A";
else if (score >= 80)
    grade = "B";
else if (score >= 70)
    grade = "C";
else
    grade = "F";
System.out.println(grade);
```

(A)
```java
String grade = (score >= 90) ? "A" : (score >= 80) ? "B" : (score >= 70) ? "C" : "F";
System.out.println(grade);
```
(B)
```java
String grade = "F";
if (score >= 70) grade = "C";
if (score >= 80) grade = "B";
if (score >= 90) grade = "A";
System.out.println(grade);
```
(C)
```java
String grade = "F";
if (score >= 90) grade = "A";
if (score >= 80) grade = "B";
if (score >= 70) grade = "C";
System.out.println(grade);
```
(D) Both (A) and (B)

---

### 23.
Consider the following code segment.

```java
String s = null;
```

Which of the following will NOT cause a `NullPointerException`?

(A) `if (s != null && s.length() > 0) { }`
(B) `if (s.length() > 0 && s != null) { }`
(C) `if (s != null || s.length() > 0) { }`
(D) `if (s.length() > 0 || s != null) { }`

---

### 24.
What is printed as a result of executing the code segment?

```java
boolean a = true;
boolean b = false;
System.out.println(a && !b);
System.out.println(!a || b);
```

(A) `true` `false`
(B) `false` `true`
(C) `true` `true`
(D) `false` `false`

---

### 25.
Which of the following best describes why the code does not work as intended?

The following method is intended to return `true` if `x` is between 10 and 20 inclusive, and `false` otherwise.

```java
public static boolean inRange(int x) {
    return (x >= 10 || x <= 20);
}
```

(A) The `||` operator should be `&&`
(B) The `>=` and `<=` operators should be `>` and `<`
(C) The method should use `if-else` instead of `return`
(D) The code works as intended

---

### 26.
What is printed as a result of executing the code segment?

```java
int n = 0;
while (n < 5) {
    n++;
    if (n == 3)
        continue;
    System.out.print(n + " ");
}
```

(A) `1 2 3 4 5 `
(B) `1 2 4 5 `
(C) `0 1 2 4 `
(D) `1 2 3 4 `

---

### 27.
What is printed as a result of executing the code segment?

```java
for (int i = 10; i >= 1; i -= 3) {
    System.out.print(i + " ");
}
```

(A) `10 7 4 1 `
(B) `10 7 4 `
(C) `10 8 5 2 `
(D) `10 7 4 1 -2 `

---

### 28.
What is printed as a result of executing the code segment?

```java
String word = "ABCDEF";
String result = "";
for (int i = word.length() - 1; i >= 0; i -= 2) {
    result += word.substring(i, i + 1);
}
System.out.println(result);
```

(A) `"FDB"`
(B) `"ACE"`
(C) `"FEDCBA"`
(D) `"FDA"`

---

### 29.
Consider the following code segment, which is intended to print each digit of `n`.

```java
int n = 4573;
while (n > 0) {
    System.out.print(_____ + " ");
    n = n / 10;
}
```

Which of the following should replace the blank so that the code works as intended?

(A) `n / 10`
(B) `n % 10`
(C) `n % 100`
(D) `n - 10`

---

### 30.
What is printed as a result of executing the code segment?

```java
int sum = 0;
for (int i = 1; i <= 100; i++) {
    if (i % 3 == 0 && i % 5 == 0)
        sum++;
}
System.out.println(sum);
```

(A) `6`
(B) `7`
(C) `33`
(D) `20`

---

### 31.
What is printed as a result of executing the code segment?

```java
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= i; j++) {
        System.out.print("* ");
    }
    System.out.println();
}
```

(A)
```
* * *
* *
*
```
(B)
```
*
* *
* * *
```
(C)
```
* * *
* * *
* * *
```
(D)
```
*
*
*
```

---

### 32.
What is printed as a result of executing the code segment?

```java
int[][] grid = {{1, 2, 3}, {4, 5, 6}};
int total = 0;
for (int[] row : grid) {
    for (int val : row) {
        if (val % 2 == 0)
            total += val;
    }
}
System.out.println(total);
```

(A) `6`
(B) `9`
(C) `12`
(D) `21`

---

### 33.
What is printed as a result of executing the code segment?

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(10);
list.add(20);
list.add(30);
list.add(1, 15);
list.remove(2);
System.out.println(list);
```

(A) `[10, 15, 30]`
(B) `[10, 15, 20]`
(C) `[10, 20, 30]`
(D) `[15, 10, 30]`

---

### 34.
Which of the following best describes why the code does not work as intended?

The following code is intended to remove all even numbers from the `ArrayList`.

```java
ArrayList<Integer> nums = new ArrayList<Integer>();
nums.add(1); nums.add(2); nums.add(3); nums.add(4); nums.add(5);

for (int n : nums) {
    if (n % 2 == 0) nums.remove(Integer.valueOf(n));
}
```

(A) The enhanced for loop does not allow modification of the list during iteration, causing a `ConcurrentModificationException`.
(B) `Integer.valueOf(n)` does not correctly match the list elements.
(C) The condition `n % 2 == 0` should be `n % 2 != 0`.
(D) The code works as intended.

---

### 35.
What is printed as a result of executing the code segment?

```java
int[] arr = {5, 12, 8, 3, 17, 6};
int max = arr[0];
for (int i = 1; i < arr.length; i++) {
    if (arr[i] > max)
        max = arr[i];
}
System.out.println(max);
```

(A) `5`
(B) `6`
(C) `12`
(D) `17`

---

### 36.
What is printed as a result of executing the code segment?

```java
int[] arr = {1, 2, 3, 4, 5};
for (int i = 0; i < arr.length / 2; i++) {
    int temp = arr[i];
    arr[i] = arr[arr.length - 1 - i];
    arr[arr.length - 1 - i] = temp;
}
System.out.println(java.util.Arrays.toString(arr));
```

(A) `[5, 4, 3, 2, 1]`
(B) `[1, 2, 3, 4, 5]`
(C) `[5, 2, 3, 4, 1]`
(D) `[5, 4, 3, 4, 5]`

---

### 37.
What is printed as a result of executing the code segment?

```java
int[][] matrix = new int[3][4];
System.out.println(matrix.length + " " + matrix[0].length);
```

(A) `4 3`
(B) `3 4`
(C) `12 4`
(D) `3 12`

---

### 38.
Consider the following recursive method.

```java
public static int mystery(int n) {
    if (n <= 0)
        return 0;
    if (n % 2 == 0)
        return mystery(n - 1) + n;
    return mystery(n - 1);
}
```

What value is returned by the method call `mystery(7)`?

(A) `7`
(B) `6`
(C) `12`
(D) `28`

---

### 39.
Consider the array below. After one pass of selection sort (ascending order), the array state is:

```java
int[] arr = {8, 3, 5, 1, 9, 2};
```

Each pass finds the minimum value in the unsorted portion and swaps it with the current position.

(A) `{1, 3, 5, 8, 9, 2}`
(B) `{1, 8, 3, 5, 9, 2}`
(C) `{3, 5, 1, 8, 9, 2}`
(D) `{1, 2, 3, 5, 8, 9}`

---

### 40.
Which of the following code segments produces the same output as the code segment below?

```java
ArrayList<String> words = new ArrayList<String>();
words.add("banana");
words.add("Apple");
words.add("cherry");
Collections.sort(words);
System.out.println(words);
```

(A)
```java
String[] arr = {"banana", "Apple", "cherry"};
Arrays.sort(arr);
System.out.println(Arrays.toString(arr));
```
(B)
```java
ArrayList<String> w = new ArrayList<>();
w.add("Apple"); w.add("banana"); w.add("cherry");
System.out.println(w);
```
(C)
```java
ArrayList<String> w = new ArrayList<>();
w.add("apple"); w.add("banana"); w.add("cherry");
System.out.println(w);
```
(D) Both (A) and (B)

---

### 41.
Consider the following recursive method.

```java
public static int mystery(int n) {
    if (n <= 1)
        return 1;
    return n * mystery(n - 1);
}
```

What value is returned by the method call `mystery(5)`?

(A) `5`
(B) `15`
(C) `120`
(D) `24`

---

### 42.
Consider the following recursive method.

```java
public static void recur(int n) {
    if (n < 10) {
        System.out.print(n);
        return;
    }
    System.out.print(n % 10);
    recur(n / 10);
}
```

What is printed as a result of the method call `recur(12345)`?

(A) `12345`
(B) `54321`
(C) `5`
(D) `1`

---

## 정답표

| 번호 | 정답 | Unit | 토픽 | 해설 |
|------|------|------|------|------|
| 1 | B | 1 | 1.3 | `17 / 5`는 정수 나눗셈으로 `3`이 되고, `double`에 저장되므로 `3.0` 출력. |
| 2 | B | 1 | 1.3 | `10 % 3 = 1`, `10 / 3 = 3` (정수 나눗셈), 합은 `4`. |
| 3 | A | 1 | 1.2 | `x > 5`이므로 `flag = true`. 코드 기반 문제로 변경. |
| 4 | A | 1 | 1.4 | `(int)` 캐스팅은 소수점 이하를 버림(truncate). `2.9` → `2`. |
| 5 | B | 1 | 1.3 | 왼쪽부터 평가: `5+3=8`, `"8"+"hello"="8hello"`, `"8hello"+"5"="8hello5"`, `+"3"="8hello53"`. |
| 6 | C | 1 | 1.4 | `(double) a`로 `a`가 `7.0`이 되어 `7.0 / 2 = 3.5`. |
| 7 | C | 1 | 1.2 | `2ndPlace`는 숫자로 시작하여 불가. `my_score`는 합법적(밑줄 허용). `class`는 예약어. `isReady`도 합법. II와 IV만 올바름. |
| 8 | B | 1 | 1.3 | `Integer.MAX_VALUE + 1`은 오버플로우로 `Integer.MIN_VALUE`(음수)가 됨. `> 0`은 `false`. |
| 9 | B | 2 | 2.6 | `s1 == s2`는 문자열 리터럴 풀에서 같은 참조, `s1 == s3`는 `new`로 다른 객체. |
| 10 | B | 2 | 2.7 | `substring(3, 6)`은 인덱스 3~5: `"put"`. |
| 11 | B | 2 | 2.7 | `"AP Computer Science A"`에서 `"Science"`는 인덱스 12부터 시작. `"AP Computer "`이 12글자. |
| 12 | B | 2 | 2.7 | `String`은 불변(immutable). `toUpperCase()`는 새 문자열 반환. 원본 `a`는 변하지 않음. |
| 13 | B | 2 | 2.7 | `"banana"`에서 `"a"`는 인덱스 1, 3, 5에 위치. 총 3개. |
| 14 | D | 2 | 2.7 | (A) `s.substring(0)`은 원본과 동일하므로 length=11. (B) `indexOf("d")=10`, 10+1=11. (C) `indexOf(" ")=5`, `s.substring(6)`="World"(길이5), 5+5+1=11. 모두 11을 출력. |
| 15 | B | 2 | 2.2 | `deposit(50.0)` → 잔액 150. `deposit(-20.0)` → amount<=0이므로 무시. 최종 잔액 `150.0`. |
| 16 | B | 2 | 2.3 | `b = a`는 같은 객체를 참조. `withdraw(50)` → 150, `deposit(30)` → 180. `a.getBalance()` = `180.0`. |
| 17 | A | 2 | 2.5 | `withdraw(150.0)` → 잔액 100보다 크므로 false, 잔액 불변. `withdraw(50.0)` → true, 잔액 50.0. |
| 18 | C | 2 | 2.3 | `String name`은 생성자에서 초기화되지 않아 기본값 `null`이 됨. |
| 19 | B | 2 | 2.9 | `Math.abs(-7.5) = 7.5`. `Math.random()`은 [0, 1) 범위이므로 `(int)(... * 6)`은 0~5, `+1`하면 1~6. |
| 20 | A | 2 | 2.7 | `"apple".compareTo("banana")`는 음수 반환 (사전순으로 앞). `< 0`은 `true`. |
| 21 | B | 3 | 3.1 | 독립적인 `if`문 3개. `15 > 10` → A, `15 > 5` → B, `15 > 20` → 실패. 출력: `"AB"`. |
| 22 | D | 3 | 3.2 | (A)는 삼항 연산자로 동일한 if-else if 로직. (B)는 아래부터 덮어쓰기로 동일 결과. (C)는 score=85일 때 마지막 `if(>=70)`에서 C로 덮어써버림 → 오답. (A)와 (B) 모두 올바름. |
| 23 | A | 3 | 3.5 | `&&`는 왼쪽이 false면 오른쪽을 평가하지 않음. `s != null`이 false이므로 `s.length()` 호출 안 함. |
| 24 | A | 3 | 3.5 | `a && !b = true && true = true`. `!a || b = false || false = false`. |
| 25 | A | 3 | 3.6 | `||`를 사용하면 모든 정수에 대해 true가 됨 (어떤 수든 10 이상이거나 20 이하). `&&`를 써야 범위 검사가 됨. |
| 26 | B | 3 | 3.7 | `continue`는 현재 반복의 나머지를 건너뜀. `n==3`일 때 출력 건너뜀. 결과: `1 2 4 5 `. |
| 27 | A | 4 | 4.2 | `i`: 10, 7, 4, 1, -2(종료). 출력: `10 7 4 1 `. |
| 28 | A | 4 | 4.3 | `i`: 5→`F`, 3→`D`, 1→`B`. 결과: `"FDB"`. |
| 29 | B | 4 | 4.2 | `n % 10`은 마지막 자릿수를 추출. `4573 % 10 = 3`, `457 % 10 = 7`, ... |
| 30 | A | 4 | 4.2 | 1~100에서 3과 5의 공배수(15의 배수): 15, 30, 45, 60, 75, 90. 총 6개. |
| 31 | B | 4 | 4.4 | `i=1`: `*`, `i=2`: `* *`, `i=3`: `* * *`. 삼각형 패턴. |
| 32 | C | 4 | 4.9 | 짝수: 2, 4, 6. 합: `2 + 4 + 6 = 12`. |
| 33 | A | 4 | 4.11 | `add(1, 15)`: 인덱스 1에 15 삽입 → `[10, 15, 20, 30]`. `remove(2)`: 인덱스 2 제거(20) → `[10, 15, 30]`. |
| 34 | A | 4 | 4.11 | enhanced for문에서 리스트를 수정하면 `ConcurrentModificationException` 발생. 뒤에서부터 인덱스로 제거해야 안전. |
| 35 | D | 4 | 4.5 | 배열 전체를 순회하며 최대값 탐색. 최대값은 `17`. |
| 36 | A | 4 | 4.5 | 양쪽 끝에서 교환하여 배열 반전. `[1,2,3,4,5]` → `[5,4,3,2,1]`. `Arrays.toString()`은 `[]` 형식으로 출력. |
| 37 | B | 4 | 4.8 | `matrix.length = 3`(행 수), `matrix[0].length = 4`(열 수). |
| 38 | C | 4 | 4.16 | 재귀 추적: `mystery(7)`→`mystery(6)`→`mystery(5)+6`→…→`mystery(0)+2+4+6`. 짝수만 합산: `2+4+6=12`. |
| 39 | A | 4 | 4.14 | 선택 정렬 첫 패스: 전체에서 최솟값 `1`(인덱스 3)을 찾아 인덱스 0의 `8`과 교환 → `{1, 3, 5, 8, 9, 2}`. |
| 40 | D | 4 | 4.11 | `Collections.sort()`는 유니코드 기준 정렬. 대문자가 소문자보다 앞. 결과: `[Apple, banana, cherry]`. (A)와 (B) 모두 같은 결과를 생성. |
| 41 | C | 4 | 4.12 | `5 * 4 * 3 * 2 * 1 = 120`. 팩토리얼 재귀. |
| 42 | B | 4 | 4.12 | 마지막 자릿수부터 출력 후 재귀: `5`, `4`, `3`, `2`, `1`. 결과: `"54321"`. |
