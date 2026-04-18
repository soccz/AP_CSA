# AP Computer Science A — Level Test 2

> **Purpose:** Diagnostic exam targeting AP CSA score of 5
> **Time:** Section I (50 min) + Section II (90 min) = 140 min total
> **Scoring:** MCQ 25 × 1 pt = 25 pts / FRQ 5 + 7 + 6 + 6 = 24 pts / **Total: 49 pts**
> **CED:** AP CSA 2025-26 (4 Units: U1 Using Objects · U2 Selection/Iteration · U3 Class Creation · U4 Data Collections)

---

# Section I: Multiple Choice (25 Questions | 50 Minutes)

**Unit Distribution (CED 2025-26):** U1(3) · U2(6) · U3(4) · U4(12)
**Difficulty:** Easy 5 · Medium 12 · Hard 8

**Directions:** Determine the answer to each of the following questions or incomplete statements, using the available space for any necessary scratch work. Then decide which is the best of the choices given. Unless otherwise noted, assume that the classes listed in the Java Quick Reference have been imported where appropriate. Unless otherwise noted, assume that parameters in method calls are not `null` and that methods are called only when their preconditions are met.

---

### 1. [U1 · Medium]

Consider the following code segment.

```java
int a = 29;
int b = 8;
double result = (double) a / b;
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) 3.0
(B) 3.5
(C) 3.625
(D) 4.0

---

### 2. [U1 · Easy]

Consider the following code segment.

```java
int x = 100;
int y = 30;
System.out.println(x / y + " " + x % y);
```

What is printed as a result of executing this code segment?

(A) `"3 10"`
(B) `"3.33 10"`
(C) `"3 0"`
(D) `"3.33 0.1"`

---

### 3. [U1 · Medium]

Consider the following code segment.

```java
String s = "university";
String result = s.substring(0, 3) + s.substring(s.length() - 3);
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `"univer"`
(B) `"unity"`
(C) `"unisty"`
(D) `"uniity"`

---

### 4. [U2 · Medium]

Consider the following code segment.

```java
String word = "ABCDEFGHIJ";
String result = "";
for (int i = word.length() - 1; i >= 0; i -= 3)
{
    result += word.substring(i, i + 1);
}
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `"JHEB"`
(B) `"JGDA"`
(C) `"JHEA"`
(D) `"JGDB"`

---

### 5. [U2 · Easy]

Consider the following code segment.

```java
int temp = 75;
String weather;
if (temp >= 90)
    weather = "hot";
else if (temp >= 70)
    weather = "warm";
else if (temp >= 50)
    weather = "cool";
else
    weather = "cold";
System.out.println(weather);
```

What is printed as a result of executing this code segment?

(A) `"cold"`
(B) `"cool"`
(C) `"hot"`
(D) `"warm"`

---

### 6. [U2 · Medium]

Consider the following Boolean expression.

```java
!(x <= 5 || y > 3) && (x != 10)
```

Which of the following is equivalent to the expression above?

(A) `(x > 5 && y <= 3) && (x != 10)`
(B) `(x > 5 || y <= 3) && (x != 10)`
(C) `(x <= 5 && y > 3) || (x == 10)`
(D) `(x > 5 && y <= 3) || (x != 10)`

---

### 7. [U2 · Medium]

Consider the following code segment.

```java
int n = 5;
int result = 1;
for (int i = 1; i <= n; i++)
{
    result *= i;
}
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) 15
(B) 25
(C) 120
(D) 5

---

### 8. [U2 · Hard]

Consider the following code segment.

```java
String s = "ABCDE";
String result = "";
int left = 0;
int right = s.length() - 1;
while (left <= right)
{
    result += s.substring(left, left + 1) + s.substring(right, right + 1);
    left++;
    right--;
}
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `"AEBDCC"`
(B) `"AEBDC"`
(C) `"ABCDE"`
(D) `"EDCBA"`

---

### 9. [U3 · Medium]

Consider the following class.

```java
public class Temperature
{
    private double celsius;

    public Temperature(double celsius)
    {
        this.celsius = celsius;
    }

    public double getCelsius() { return celsius; }

    public double getFahrenheit()
    {
        return celsius * 9.0 / 5 + 32;
    }

    public void increase(double amount)
    {
        if (amount > 0)
            celsius += amount;
    }
}
```

The following code segment appears in a method in another class.

```java
Temperature t = new Temperature(0);
t.increase(100);
System.out.println(t.getFahrenheit());
```

What is printed as a result of executing this code segment?

(A) `100.0`
(B) `180.0`
(C) `212.0`
(D) `32.0`

---

### 10. [U3 · Easy]

Consider the following class.

```java
public class Pair
{
    private int first;
    private int second;

    public Pair(int a, int b)
    {
        first = a;
        second = b;
    }

    public int getFirst()  { return first; }
    public int getSecond() { return second; }

    public int getSum()    { return first + second; }
    public int getProduct(){ return first * second; }
}
```

The following code segment appears in a method in another class.

```java
Pair p = new Pair(3, 7);
System.out.println(p.getSum() + " " + p.getProduct());
```

What is printed as a result of executing this code segment?

(A) `"3 7"`
(B) `"10 10"`
(C) `"10 21"`
(D) `"21 10"`

---

### 11. [U3 · Hard]

Consider the following class.

```java
public class Counter
{
    private int count;
    private int limit;

    public Counter(int limit)
    {
        count = 0;
        this.limit = limit;
    }

    public int getCount() { return count; }

    public boolean increment()
    {
        if (count < limit)
        {
            count++;
            return true;
        }
        return false;
    }

    public void reset()
    {
        count = 0;
    }
}
```

The following code segment appears in a method in another class.

```java
Counter c = new Counter(3);
int total = 0;
while (c.increment())
{
    total += c.getCount();
}
System.out.println(total + " " + c.getCount());
```

What is printed as a result of executing this code segment?

(A) `"6 3"`
(B) `"3 3"`
(C) `"6 4"`
(D) `"10 4"`

---

### 12. [U4 · Medium]

Consider the following code segment.

```java
int[] arr = {10, 20, 30, 40, 50};
int sum = 0;
for (int i = 0; i < arr.length; i += 2)
{
    sum += arr[i];
}
System.out.println(sum);
```

What is printed as a result of executing this code segment?

(A) 60
(B) 80
(C) 150
(D) 90

---

### 13. [U4 · Easy]

Consider the following code segment.

```java
int[] nums = {5, 12, 3, 8, 15, 1};
int count = 0;
for (int val : nums)
{
    if (val > 5)
        count++;
}
System.out.println(count);
```

What is printed as a result of executing this code segment?

(A) 2
(B) 3
(C) 4
(D) 6

---

### 14. [U4 · Hard]

Consider the following code segment.

```java
int[][] grid = {{2, 5, 1, 3},
                {4, 6, 8, 7},
                {9, 2, 5, 4}};
int total = 0;
for (int r = 0; r < grid.length; r++)
{
    for (int c = 0; c < grid[r].length; c++)
    {
        if ((r + c) % 2 == 0)
            total += grid[r][c];
        else
            total -= grid[r][c];
    }
}
System.out.println(total);
```

What is printed as a result of executing this code segment?

(A) 2
(B) 4
(C) -4
(D) 56

---

### 15. [U4 · Medium]

Consider the following code segment.

```java
ArrayList<String> colors = new ArrayList<String>();
colors.add("red");
colors.add("green");
colors.add("blue");
colors.add("yellow");
colors.remove(1);
colors.add(1, "purple");
colors.set(3, "orange");
System.out.println(colors);
```

What is printed as a result of executing this code segment?

(A) `[red, purple, blue, orange]`
(B) `[red, purple, blue, yellow]`
(C) `[red, green, purple, orange]`
(D) `[red, purple, yellow, orange]`

---

### 16. [U4 · Easy]

Consider the following code segment.

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(10);
list.add(20);
list.add(30);
list.add(0, 5);
System.out.println(list.size() + " " + list.get(2));
```

What is printed as a result of executing this code segment?

(A) `"3 30"`
(B) `"4 20"`
(C) `"4 30"`
(D) `"3 20"`

---

### 17. [U4 · Hard]

Consider the following code segment.

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(4);
list.add(4);
list.add(3);
list.add(2);
list.add(4);

for (int i = 0; i < list.size(); i++)
{
    if (list.get(i) == 4)
    {
        list.remove(i);
    }
}
System.out.println(list);
```

What is printed as a result of executing this code segment?

(A) `[3, 2]`
(B) `[3, 2, 4]`
(C) `[4, 3, 2, 4]`
(D) `[4, 3, 2]`

---

### 18. [U4 · Medium]

Consider the following code segment.

```java
int[][] grid = {{1, 2, 3, 4},
                {5, 6, 7, 8},
                {9, 10, 11, 12}};
int sum = 0;
for (int r = 0; r < grid.length; r++)
{
    sum += grid[r][grid[0].length - 1];
}
System.out.println(sum);
```

What is printed as a result of executing this code segment?

(A) 12
(B) 24
(C) 15
(D) 78

---

### 19. [U4 · Hard]

Consider the following code segment.

```java
int[][] mat = {{3, 1, 4},
               {1, 5, 9},
               {2, 6, 5}};
int total = 0;
for (int r = 0; r < mat.length; r++)
{
    for (int c = 0; c < mat[0].length; c++)
    {
        if (r == c || r + c == mat.length - 1)
            total += mat[r][c];
    }
}
System.out.println(total);
```

What is printed as a result of executing this code segment?

(A) 13
(B) 22
(C) 20
(D) 19

---

### 20. [U2 · Hard]

Consider the following code segment.

```java
String s = null;
int count = 0;
if (s != null && s.length() > 0)
{
    count++;
}
if (s == null || s.length() == 0)
{
    count++;
}
System.out.println(count);
```

What is printed as a result of executing this code segment?

(A) 0
(B) 1
(C) 2
(D) A `NullPointerException` is thrown.

---

### 21. [U4 · Medium]

Consider the following code segment.

```java
int[] a = {1, 2, 3};
int[] b = a;
b[0] = 99;

int[] c = new int[a.length];
for (int i = 0; i < a.length; i++)
{
    c[i] = a[i];
}
c[1] = 88;

System.out.println(a[0] + " " + a[1] + " " + b[1] + " " + c[2]);
```

What is printed as a result of executing this code segment?

(A) `"1 2 2 3"`
(B) `"99 88 88 3"`
(C) `"99 2 2 3"`
(D) `"99 88 2 3"`

---

### 22. [U3 · Hard]

Consider the following class.

```java
public class Account
{
    private int balance;
    private int limit;

    public Account(int balance, int limit)
    {
        this.balance = balance;
        limit = limit;
    }

    public int getBalance() { return balance; }
    public int getLimit()   { return limit; }
}
```

The following code segment appears in a method in another class.

```java
Account a = new Account(100, 500);
System.out.println(a.getBalance() + " " + a.getLimit());
```

What is printed as a result of executing this code segment?

(A) `"100 500"`
(B) `"100 0"`
(C) `"0 500"`
(D) A compile-time error occurs.

---

### 23. [U4 · Hard]

Consider the following code segment.

```java
int[][] mat = { {2, 4, 6},
                {1, 3, 5},
                {8, 7, 9} };
int sum = 0;
for (int c = 0; c < mat[0].length; c++)
{
    for (int r = c; r < mat.length; r++)
    {
        sum += mat[r][c];
    }
}
System.out.println(sum);
```

What is printed as a result of executing this code segment?

(A) 25
(B) 30
(C) 35
(D) 45

---

### 24. [U4 · Medium]

Consider the following method.

```java
public static int compute(int n)
{
    if (n <= 1)
        return 1;
    return n * compute(n - 1);
}
```

What value is returned by the call `compute(5)`?

(A) 5
(B) 15
(C) 120
(D) 25

---

### 25. [U4 · Hard]

Consider the following method.

```java
public static int mystery(int[] arr, int lo, int hi)
{
    if (lo == hi)
        return arr[lo];
    int mid = (lo + hi) / 2;
    int left = mystery(arr, lo, mid);
    int right = mystery(arr, mid + 1, hi);
    if (left > right)
        return left;
    return right;
}
```

What value is returned by the following call?

```java
int[] data = {3, 7, 2, 9, 5};
mystery(data, 0, data.length - 1);
```

(A) 3
(B) 7
(C) 9
(D) 5

---

# Section II: Free Response (4 Questions | 120 Minutes)

**Directions:** SHOW ALL YOUR WORK. REMEMBER THAT PROGRAM SEGMENTS ARE TO BE WRITTEN IN JAVA.

Write your solutions in Java. You may assume all necessary imports. Assume that the code provided compiles and works correctly. You may write helper methods if you wish.

---

## Question 1: StringProcessor (5 Points)

This question involves processing strings using the six AP Java Quick Reference String methods only (`length`, `substring(int)`, `substring(int, int)`, `indexOf(String)`, `equals(Object)`, `compareTo(String)`).

```java
public class StringProcessor
{
    /** Returns the number of lowercase vowels (a, e, i, o, u) in str.
     *  Uppercase letters are NOT counted.
     *
     *  Precondition: str is not null
     *
     *  Examples:
     *    countVowels("hello world") → 3   (e, o, o)
     *    countVowels("rhythm")      → 0
     *    countVowels("Apple")       → 1   (only lowercase 'e'; 'A' not counted)
     */
    public static int countVowels(String str)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a new string with all consecutive duplicate characters
     *  reduced to a single character.
     *
     *  Precondition: str is not null and has length >= 1
     *
     *  Examples:
     *    removeConsecutiveDuplicates("aabbcc")    → "abc"
     *    removeConsecutiveDuplicates("abcabc")    → "abcabc"
     *    removeConsecutiveDuplicates("aaabbbccc") → "abc"
     *    removeConsecutiveDuplicates("hello")     → "helo"
     */
    public static String removeConsecutiveDuplicates(String str)
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a) — 2 Points

Complete the `countVowels` method. Use `substring(i, i + 1)` to extract each single-character string and `equals` to compare to each vowel.

### Part (b) — 3 Points

Complete the `removeConsecutiveDuplicates` method. Build the result string by appending each character only when it differs from the previous one.

---

## Question 2: StudentRoster (7 Points)

A `Student` is represented by the following class.

```java
public class Student
{
    private String name;
    private int grade;    // 9, 10, 11, or 12
    private double gpa;   // 0.0 to 4.0

    public Student(String name, int grade, double gpa)
    {
        this.name = name;
        this.grade = grade;
        this.gpa = gpa;
    }

    public String getName()  { return name; }
    public int getGrade()    { return grade; }
    public double getGpa()   { return gpa; }
}
```

Write the complete `StudentRoster` class. Your implementation must include:

- A private `ArrayList<Student>` instance variable
- A no-argument constructor that initializes an empty roster
- All methods described below

### Part (a)

Write the following methods for the `StudentRoster` class.

- `addStudent(Student s)` — Adds the given student to the end of the roster.
- `getHonorRoll()` — Returns a new `ArrayList<Student>` containing all students with a GPA of 3.5 or higher, in the same order they appear in the roster.
- `getAverageGpa()` — Returns the average GPA of all students in the roster.
  *Precondition:* The roster has at least one student.

**Example:**

| Roster contents | Method call | Return value |
|---|---|---|
| [("Alice",10,3.8), ("Bob",11,3.2), ("Carol",10,3.9)] | `getHonorRoll()` | names: ["Alice","Carol"] |
| [("Alice",10,3.8), ("Bob",11,3.2), ("Carol",10,3.9)] | `getAverageGpa()` | `3.633...` |

### Part (b)

Write the following methods for the `StudentRoster` class.

- `getStudentsByGrade(int grade)` — Returns a new `ArrayList<Student>` containing all students in the given grade, in the same order they appear in the roster. Returns an empty list if no students match.
- `removeGraduates()` — Removes all students in grade 12 from the roster. Returns the number of students removed.

**Example:**

| Roster contents (before) | Method call | Return | Roster (after) |
|---|---|---|---|
| [("Alice",10,3.8), ("Bob",12,3.2), ("Carol",12,3.9)] | `removeGraduates()` | `2` | [("Alice",10,3.8)] |

---

## Question 3: InventoryTracker (6 Points)

This question involves tracking inventory quantities.

```java
public class InventoryTracker
{
    private int[] quantities;

    /** Constructs an InventoryTracker with the given quantities array.
     *  Precondition: quantities has at least one element.
     *                All values are >= 0.
     */
    public InventoryTracker(int[] quantities)
    {
        this.quantities = quantities;
    }

    /** Returns the index of the item with the largest quantity.
     *  If there is a tie, the index of the first such item is returned.
     *
     *  Example:
     *    quantities = {15, 42, 8, 42, 23}
     *    getMostStocked() → 1
     */
    public int getMostStocked()
    {
        /* to be implemented in Part (a) */
    }

    /** Returns an array indicating whether each item is "low stock."
     *  An item is low stock if its quantity is less than threshold.
     *  The returned array has the same length as quantities.
     *
     *  Example:
     *    quantities = {5, 20, 3, 15, 0}
     *    getLowStock(10) → {true, false, true, false, true}
     */
    public boolean[] getLowStock(int threshold)
    {
        /* to be implemented in Part (a) */
    }

    /** Restocks all items that have quantity 0 by setting their
     *  quantity to restockAmount. Returns the number of items restocked.
     *
     *  Example:
     *    quantities (before) = {5, 0, 3, 0, 10}
     *    restockEmpty(20)
     *    quantities (after)  = {5, 20, 3, 20, 10}
     *    returns 2
     */
    public int restockEmpty(int restockAmount)
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `getMostStocked` method and the `getLowStock` method.

### Part (b)

Complete the `restockEmpty` method.

---

## Question 4: SeatingChart (6 Points)

This question involves operations on a two-dimensional array representing a seating chart. Each element is a student name (`String`), or `null` if the seat is empty.

```java
public class SeatingChart
{
    private String[][] seats;

    /** Constructs a SeatingChart with the given 2D array.
     *  Precondition: seats is rectangular and has at least one row and one column.
     */
    public SeatingChart(String[][] seats)
    {
        this.seats = seats;
    }

    /** Returns the number of empty seats (null entries) in the chart.
     *
     *  Example:
     *    {{"Alice", null,   "Bob" },
     *     {null,    "Carol", null  }}
     *    countEmpty() → 3
     */
    public int countEmpty()
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a one-dimensional array containing the number of
     *  occupied seats in each column. The length of the returned
     *  array equals the number of columns.
     *
     *  Example:
     *    {{"Alice", null,   "Bob" },
     *     {null,    "Carol", null  }}
     *    seatsPerColumn() → {1, 1, 1}
     */
    public int[] seatsPerColumn()
    {
        /* to be implemented in Part (a) */
    }

    /** Moves all students in the chart one seat to the right within
     *  their row (column index increases by 1). Students in the last
     *  column wrap around to column 0 of the same row.
     *  Empty seats shift accordingly.
     *
     *  Example:
     *    Before:
     *    {{"Alice", "Bob",  null },
     *     {null,    "Carol","Dan"}}
     *
     *    After rotateRight():
     *    {{null,   "Alice", "Bob" },
     *     {"Dan",  null,   "Carol"}}
     */
    public void rotateRight()
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `countEmpty` method and the `seatsPerColumn` method.

### Part (b)

Complete the `rotateRight` method.
