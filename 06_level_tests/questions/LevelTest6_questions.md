# AP Computer Science A — Level Test 6

> **CED 2025-26 (4-Unit) 기준**
> U1 Using Objects · U2 Selection/Iteration · U3 Class Creation · U4 Data Collections
>
> **Purpose:** Diagnostic exam targeting AP CSA score of 5
> **Time:** Section I (50 min) + Section II (90 min) = 140 min total
> **Scoring:** MCQ 25 × 1 pt = 25 pts / FRQ 5 + 7 + 6 + 6 = 24 pts / **Total: 49 pts**

---

# Section I: Multiple Choice (25 Questions | 50 Minutes)

**Unit Distribution:** U1(5) · U2(5) · U3(4) · U4(11)
**Difficulty:** Easy 5 · Medium 12 · Hard 8

**Directions:** Determine the answer to each of the following questions or incomplete statements, using the available space for any necessary scratch work. Then decide which is the best of the choices given. Unless otherwise noted, assume that the classes listed in the Java Quick Reference have been imported where appropriate. Unless otherwise noted, assume that parameters in method calls are not `null` and that methods are called only when their preconditions are met.

---

### 1. [U1 · Easy]

```java
double x = 7.8;
int y = (int)(x + 0.5);
System.out.println(y);
```

What is printed?

(A) 7
(B) 8
(C) 9
(D) 7.8

---

### 2. [U1 · Medium]

```java
double result = Math.abs(-5) + Math.pow(2, 3);
System.out.println(result);
```

What is printed?

(A) 13
(B) 13.0
(C) 3
(D) A runtime error occurs.

---

### 3. [U1 · Medium]

```java
int a = 3;
int b = 4;
System.out.println("Sum: " + a + b);
```

What is printed?

(A) `"Sum: 34"`
(B) `"Sum: 7"`
(C) `"Sum: 3 + 4"`
(D) `"Sum: 3, 4"`

---

### 4. [U1 · Medium]

```java
String s = "hello";
s.substring(1, 4);
System.out.println(s);
```

What is printed?

(A) `"ell"`
(B) `"hello"`
(C) `""`
(D) A compile-time error occurs.

---

### 5. [U1 · Hard]

```java
String a = "Apple";
String b = "apple";
boolean r1 = a.equals(b);
boolean r2 = a.compareTo(b) < 0;
System.out.println(r1 + " " + r2);
```

What is printed? (Note: `'A'` has ASCII 65, `'a'` has ASCII 97.)

(A) `"true false"`
(B) `"false false"`
(C) `"false true"`
(D) `"true true"`

---

### 6. [U2 · Easy]

```java
int sum = 0;
for (int i = 10; i >= 2; i -= 2)
{
    sum += i;
}
System.out.println(sum);
```

What is printed?

(A) 25
(B) 30
(C) 55
(D) 20

---

### 7. [U2 · Medium]

```java
int x = 0;
int y = 5;
if (y > 0 || (10 / x) > 0)
    System.out.println("A");
else
    System.out.println("B");
```

What is printed?

(A) `"A"`
(B) `"B"`
(C) A runtime error (division by zero) occurs.
(D) A compile-time error occurs.

---

### 8. [U2 · Medium]

```java
int score = 85;
if (score >= 90)
    System.out.println("A");
else if (score >= 80)
    System.out.println("B");
if (score >= 70)
    System.out.println("C");
```

What is printed?

(A) `"A"` only
(B) `"B"` only
(C) `"B"` then `"C"` (on separate lines)
(D) `"C"` then `"B"` (on separate lines)

---

### 9. [U2 · Medium]

```java
int n = 1;
int count = 0;
while (n < 100)
{
    n *= 3;
    count++;
}
System.out.println(count + " " + n);
```

What is printed?

(A) `"4 81"`
(B) `"5 243"`
(C) `"4 243"`
(D) `"5 81"`

---

### 10. [U2 · Hard]

Which of the following Boolean expressions is equivalent to `(a && b) || (a && !b)` for all Boolean values of `a` and `b`?

(A) `a`
(B) `b`
(C) `a || b`
(D) `a && b`

---

### 11. [U3 · Easy]

```java
public class Point
{
    private int x;
    private int y;
    public Point(int x, int y) { this.x = x; this.y = y; }
    public int getX() { return x; }
    public int getY() { return y; }
    public void move(int dx, int dy) { x += dx; y += dy; }
}
```

```java
Point p = new Point(3, 4);
p.move(2, -1);
System.out.println(p.getX() + " " + p.getY());
```

What is printed?

(A) `"3 4"`
(B) `"5 3"`
(C) `"2 -1"`
(D) `"5 5"`

---

### 12. [U3 · Medium]

```java
public class Counter
{
    private int count;
    public Counter() { count = 0; }
    public void increment() { count++; }
    public void incrementBy(int n)
    {
        for (int i = 0; i < n; i++)
            increment();
    }
    public int getCount() { return count; }
}
```

```java
Counter c = new Counter();
c.incrementBy(3);
c.increment();
c.incrementBy(2);
System.out.println(c.getCount());
```

What is printed?

(A) 0
(B) 3
(C) 6
(D) 5

---

### 13. [U3 · Medium]

```java
public class Timer
{
    private int seconds;
    public Timer() { seconds = 60; }
    public Timer(int s) { seconds = s; }
    public void tick()
    {
        if (seconds > 0)
            seconds--;
    }
    public int getSeconds() { return seconds; }
}
```

```java
Timer t1 = new Timer();
Timer t2 = new Timer(5);
for (int i = 0; i < 10; i++)
{
    t1.tick();
    t2.tick();
}
System.out.println(t1.getSeconds() + " " + t2.getSeconds());
```

What is printed?

(A) `"60 5"`
(B) `"50 -5"`
(C) `"50 0"`
(D) `"60 0"`

---

### 14. [U3 · Hard]

```java
public class Counter
{
    private int count;
    public Counter(int c) { count = c; }
    public int get() { return count; }
    public void inc() { count++; }
}
```

```java
Counter a = new Counter(5);
Counter b = a;
b.inc();
b.inc();
Counter c = new Counter(5);
c.inc();
System.out.println(a.get() + " " + b.get() + " " + c.get());
```

What is printed?

(A) `"5 7 6"`
(B) `"7 7 5"`
(C) `"5 5 5"`
(D) `"7 7 6"`

---

### 15. [U4 · Easy]

```java
int[] arr = {1, 2, 3, 4, 5};
int total = 0;
for (int n : arr)
{
    total += n;
}
System.out.println(total);
```

What is printed?

(A) 15
(B) 5
(C) 120
(D) 10

---

### 16. [U4 · Medium]

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(10);
list.add(20);
list.add(30);
list.add(40);
for (int i = list.size() - 1; i >= 0; i--)
{
    if (list.get(i) % 20 == 0)
        list.remove(i);
}
System.out.println(list);
```

What is printed?

(A) `[10, 30]`
(B) `[10, 20, 30]`
(C) `[20, 40]`
(D) `[10, 20, 30, 40]`

---

### 17. [U4 · Medium]

```java
ArrayList<String> list = new ArrayList<String>();
list.add("A");
list.add("B");
list.add("C");
list.add(1, "X");
list.add(3, "Y");
System.out.println(list);
```

What is printed?

(A) `[A, X, B, Y, C]`
(B) `[A, B, X, C, Y]`
(C) `[X, A, Y, B, C]`
(D) `[A, X, Y, B, C]`

---

### 18. [U4 · Hard]

```java
int[] arr = {1, 2, 3, 4, 5};
int first = arr[0];
for (int i = 0; i < arr.length - 1; i++)
{
    arr[i] = arr[i + 1];
}
arr[arr.length - 1] = first;
System.out.println(arr[0] + " " + arr[2] + " " + arr[4]);
```

What is printed?

(A) `"1 3 5"`
(B) `"5 3 1"`
(C) `"2 3 5"`
(D) `"2 4 1"`

---

### 19. [U4 · Medium]

```java
int[][] grid = {{1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}};
int col = 1;
int sum = 0;
for (int r = 0; r < grid.length; r++)
{
    sum += grid[r][col];
}
System.out.println(sum);
```

What is printed?

(A) 12
(B) 18
(C) 15
(D) 24

---

### 20. [U4 · Hard]

```java
int[][] grid = {{1, 2, 3, 4},
                {5, 6, 7, 8},
                {9, 10, 11, 12},
                {13, 14, 15, 16}};
int sum = 0;
for (int i = 0; i < grid.length; i++)
{
    sum += grid[i][i] + grid[i][grid.length - 1 - i];
}
System.out.println(sum);
```

What is printed?

(A) 34
(B) 62
(C) 136
(D) 68

---

### 21. [U4 · Easy]

```java
int[] a = {10, 20, 30};
int[] b = new int[a.length];
for (int i = 0; i < a.length; i++)
{
    b[i] = a[i];
}
a[0] = 100;
System.out.println(a[0] + " " + b[0]);
```

What is printed?

(A) `"10 10"`
(B) `"100 100"`
(C) `"100 10"`
(D) `"10 100"`

---

### 22. [U4 · Medium]

```java
int[] arr = {5, 3, 7, 3, 9, 3};
int target = 3;
int first = -1;
int last = -1;
for (int i = 0; i < arr.length; i++)
{
    if (arr[i] == target)
    {
        if (first == -1)
            first = i;
        last = i;
    }
}
System.out.println(first + " " + last);
```

What is printed?

(A) `"0 5"`
(B) `"1 3"`
(C) `"-1 -1"`
(D) `"1 5"`

---

### 23. [U4 · Hard]

```java
int[] arr = {3, 1, 4, 1, 5, 9, 2, 6, 5, 3};
int newHighs = 1;
int maxSoFar = arr[0];
for (int i = 1; i < arr.length; i++)
{
    if (arr[i] > maxSoFar)
    {
        newHighs++;
        maxSoFar = arr[i];
    }
}
System.out.println(newHighs);
```

What is printed?

(A) 3
(B) 5
(C) 10
(D) 4

---

### 24. [U4 · Medium]

```java
public static int sumDigits(int n)
{
    if (n == 0)
        return 0;
    return n % 10 + sumDigits(n / 10);
}
```

What does `sumDigits(247)` return?

(A) 11
(B) 247
(C) 10
(D) 13

---

### 25. [U4 · Hard]

```java
public static int fib(int n)
{
    if (n <= 1)
        return n;
    return fib(n - 1) + fib(n - 2);
}
```

Consider a counter that increments by 1 at the start of each call to `fib`. How many times is `fib` called (including the initial call) when `fib(4)` is executed?

(A) 5
(B) 7
(C) 9
(D) 11

---

# Section II: Free Response (4 Questions | 90 Minutes)

**Directions:** SHOW ALL YOUR WORK. REMEMBER THAT PROGRAM SEGMENTS ARE TO BE WRITTEN IN JAVA.

---

## Question 1: TextProcessor (5 Points)

```java
public class TextProcessor
{
    /** Returns the number of vowels in text.
     *  Vowels are the lowercase letters: a, e, i, o, u.
     *  Uppercase letters and other characters are NOT counted.
     *
     *  Examples:
     *    countVowels("hello")     → 2   (e, o)
     *    countVowels("RHYTHM")    → 0   (all uppercase, no lowercase vowels)
     *    countVowels("AEIOU")     → 0   (uppercase, not counted)
     *    countVowels("aeiou")     → 5
     *    countVowels("")          → 0
     */
    public static int countVowels(String text)
    { /* to be implemented in Part (a) */ }

    /** Returns text with all lowercase vowels (a, e, i, o, u) removed.
     *  Other characters (including uppercase vowels) are preserved.
     *
     *  Examples:
     *    removeVowels("hello")       → "hll"
     *    removeVowels("Programming") → "Prgrmmng"
     *    removeVowels("xyz")         → "xyz"
     *    removeVowels("")            → ""
     */
    public static String removeVowels(String text)
    { /* to be implemented in Part (b) */ }
}
```

### Part (a) (2 points)
Complete the `countVowels` method.

### Part (b) (3 points)
Complete the `removeVowels` method. You may, but are not required to, call `countVowels`.

---

## Question 2: Inventory (7 Points)

The `Product` class has been provided and is shown below.

```java
public class Product
{
    private String name;
    private double price;
    private int quantity;

    public Product(String n, double p, int q)
    {
        name = n;
        price = p;
        quantity = q;
    }

    public String getName()    { return name; }
    public double getPrice()   { return price; }
    public int getQuantity()   { return quantity; }

    /** Decreases quantity by n.
     *  Precondition: n <= quantity (never sells below zero)
     */
    public void sellUnits(int n) { quantity -= n; }
}
```

Write the complete `Inventory` class. The `Inventory` class should have:
- a `private ArrayList<Product>` field to hold the products
- a **no-argument** constructor that initializes the list to an empty `ArrayList`
- the public methods specified in Part (a) and Part (b) below

### Part (a) (4 points)

Implement the following three methods:

- `public void addProduct(Product p)` — adds `p` to the inventory.
- `public double getTotalValue()` — returns the sum of `price * quantity` across all products. Returns `0.0` if the inventory is empty.
- `public ArrayList<Product> findLowStock(int threshold)` — returns a new `ArrayList<Product>` containing every product whose quantity is **strictly less than** `threshold`, in the same order as they appear in the inventory.

### Part (b) (3 points)

Implement:

- `public int sellProduct(String name, int count)` — finds the first product whose `getName()` equals `name`, then:
  - If the product has **at least** `count` units available, calls `sellUnits(count)` on it and returns `count`.
  - If the product has **fewer than** `count` units available, sells **all** remaining units (by calling `sellUnits` with the available quantity) and returns the actual number of units sold.
  - If no product with that name exists, returns `0` and makes no changes.

---

## Question 3: Transcript (6 Points)

A school maintains a student's transcript using a list of `Course` objects. Each `Course` has a course code (`String`), credit count (`int`), GPA earned (`double`), and a passed flag (`boolean`). The `Course` class is **partial declaration** — only the parts you may use are shown.

```java
public class Course
{
    private String code;
    private int credits;
    private double gpa;
    private boolean passed;

    public Course(String c, int cr, double g, boolean p)
    {
        code = c; credits = cr; gpa = g; passed = p;
    }

    public String getCode()   { return code; }
    public int getCredits()   { return credits; }
    public double getGpa()    { return gpa; }
    public boolean isPassed() { return passed; }

    // ... other methods not shown ...
}
```

The `Transcript` class stores courses in an `ArrayList<Course>` and supports analytics.

```java
public class Transcript
{
    /** The courses in this transcript. Not null. May be empty. */
    private ArrayList<Course> courses;

    public Transcript(ArrayList<Course> c) { courses = c; }

    /** Returns the total credits of passed courses.
     *  Returns 0 if no courses are passed. */
    public int totalPassedCredits()
    {
        /* Part (a) */
    }

    /** Returns the average GPA of passed courses whose credit count is
     *  in the inclusive range [minCredits, maxCredits].
     *  Precondition: at least one passed course meets the criteria. */
    public double averageGpaInRange(int minCredits, int maxCredits)
    {
        /* Part (b) */
    }

    // ... other methods not shown ...
}
```

### Part (a) [3 points]

Write the `totalPassedCredits` method. Iterate through `courses` and return the **sum of `getCredits()`** for courses that are passed (`isPassed()` returns `true`). If no courses are passed (or the transcript is empty), return `0`.

**Example:** Suppose `courses` contains the following:

| index | code     | credits | gpa | passed |
|-------|----------|---------|-----|--------|
| 0     | "CS101"  | 4       | 3.7 | true   |
| 1     | "MATH200"| 3       | 2.0 | false  |
| 2     | "ENG110" | 3       | 4.0 | true   |
| 3     | "PHY150" | 4       | 3.3 | true   |
| 4     | "HIST100"| 2       | 1.5 | false  |

- `totalPassedCredits()` returns `11` (CS101 4 + ENG110 3 + PHY150 4 = 11).

Complete method `totalPassedCredits`:

```java
public int totalPassedCredits()
{

}
```

### Part (b) [3 points]

Write the `averageGpaInRange` method. Return, as a `double`, the **average** of `getGpa()` for courses that are **both** passed AND whose `getCredits()` is in the inclusive range `[minCredits, maxCredits]`. You may assume the precondition holds (at least one such course exists), so divide-by-zero need not be handled.

**Examples (using the table above):**

- `averageGpaInRange(3, 4)` returns the average of `{3.7, 4.0, 3.3}` (CS101, ENG110, PHY150 all passed and have 3-4 credits), i.e., `(3.7 + 4.0 + 3.3) / 3 = 3.6666...`.
- `averageGpaInRange(4, 4)` returns the average of `{3.7, 3.3}` (CS101 and PHY150), i.e., `3.5`.

Complete method `averageGpaInRange`:

```java
public double averageGpaInRange(int minCredits, int maxCredits)
{

}
```

---

## Question 4: Grid (6 Points)

```java
public class Grid
{
    private int[][] data;

    /** Precondition: data is a non-empty rectangular 2D array. */
    public Grid(int[][] data) { this.data = data; }

    /** Returns the sum of every element in data. */
    public int sumAll()
    { /* to be implemented in Part (a) */ }

    /** Returns true if EVERY element in row r equals v.
     *  Returns false if any element in row r differs from v.
     *  Precondition: 0 <= r < data.length
     *
     *  Examples (for data = {{1,1,1}, {2,2,2}, {1,2,3}}):
     *    rowAllEqual(0, 1) → true
     *    rowAllEqual(1, 2) → true
     *    rowAllEqual(1, 1) → false
     *    rowAllEqual(2, 1) → false
     */
    public boolean rowAllEqual(int r, int v)
    { /* to be implemented in Part (a) */ }

    /** Returns the index of the row with the LARGEST sum.
     *  If multiple rows share the maximum sum, returns the SMALLEST such index
     *  (the first one encountered).
     *
     *  Example: for data = {{1,1,1}, {5,5,5}, {2,2,2}, {5,5,5}}
     *    Row sums are [3, 15, 6, 15]. Max is 15, first at index 1.
     *    maxRowIndex() → 1
     */
    public int maxRowIndex()
    { /* to be implemented in Part (b) */ }
}
```

### Part (a) (4 points)
Complete `sumAll` (2 pts) and `rowAllEqual` (2 pts).

### Part (b) (2 points)
Complete `maxRowIndex`. You may, but are not required to, call any method you wrote in Part (a).
