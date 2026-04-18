# AP Computer Science A — Level Test 3

> **Purpose:** Diagnostic exam targeting AP CSA score of 5 (CED 2025-26, 4 Units)
> **Time:** Section I (50 min) + Section II (120 min) = 170 min total
> **Scoring:** MCQ 25 × 1 pt = 25 pts / FRQ 5 + 7 + 6 + 6 = 24 pts / **Total: 49 pts**

---

# Section I: Multiple Choice (25 Questions | 50 Minutes)

**Unit Distribution (2025-26 CED):** U1(5) · U2(5) · U3(4) · U4(11)
**Difficulty:** Easy 5 · Medium 12 · Hard 8

**Directions:** Determine the answer to each of the following questions or incomplete statements, using the available space for any necessary scratch work. Then decide which is the best of the choices given. Unless otherwise noted, assume that the classes listed in the Java Quick Reference have been imported where appropriate. Unless otherwise noted, assume that parameters in method calls are not `null` and that methods are called only when their preconditions are met.

---

### 1. [U1 · Easy]

Consider the following code segment.

```java
int p = 50;
int q = 12;
System.out.println(p / q + " R " + p % q);
```

What is printed as a result of executing this code segment?

(A) `"4 R 2"`
(B) `"4.16 R 2"`
(C) `"4 R 0"`
(D) `"50 R 12"`

---

### 2. [U1 · Medium]

Consider the following code segment.

```java
int a = 7;
int b = 3;
double c = a;
double result = c / b + a / b;
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) 4.333333333333333
(B) 4.666666666666666
(C) 4.333333333333334
(D) 4.666666666666667

---

### 3. [U1 · Easy]

Consider the following code segment.

```java
String s = "COMPUTER";
System.out.println(s.substring(3, 6) + s.length());
```

What is printed as a result of executing this code segment?

(A) `"PUT8"`
(B) `"PUTE8"`
(C) `"MPU8"`
(D) `"PUT6"`

---

### 4. [U2 · Medium]

Consider the following code segment.

```java
String word = "racecar";
boolean match = true;
for (int i = 0; i < word.length() / 2; i++)
{
    if (!word.substring(i, i + 1).equals(word.substring(word.length() - 1 - i, word.length() - i)))
        match = false;
}
System.out.println(match);
```

What is printed as a result of executing this code segment?

(A) `true`
(B) `false`
(C) A compile-time error occurs.
(D) A runtime error occurs.

---

### 5. [U2 · Medium]

Consider the following code segment.

```java
int x = 10;
int y = 20;
int z = 15;
String result;
if (x > y || z > y)
    result = "A";
else if (x < z && z < y)
    result = "B";
else
    result = "C";
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `"C"`
(B) `"A"`
(C) Nothing is printed because of a compile-time error.
(D) `"B"`

---

### 6. [U2 · Hard]

Consider the following Boolean expression where `n` is an `int`.

```java
!(n >= 1 && n <= 100)
```

Which of the following is equivalent to the expression above?

(A) `n < 1 && n > 100`
(B) `n >= 1 || n <= 100`
(C) `n > 1 && n < 100`
(D) `n < 1 || n > 100`

---

### 7. [U2 · Medium]

Consider the following code segment.

```java
int result = 0;
for (int i = 1; i <= 4; i++)
{
    for (int j = 1; j <= 3; j++)
    {
        result += i * j;
    }
}
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) 30
(B) 60
(C) 12
(D) 24

---

### 8. [U2 · Hard]

Consider the following code segment.

```java
int n = 7;
int count = 0;
while (n > 0)
{
    if (n % 2 == 1)
        count++;
    n /= 2;
}
System.out.println(count);
```

What is printed as a result of executing this code segment?

(A) 1
(B) 2
(C) 3
(D) 7

---

### 9. [U3 · Easy]

Consider the following class.

```java
public class Circle
{
    private double radius;

    public Circle(double r)
    {
        radius = r;
    }

    public double getArea()
    {
        return Math.PI * radius * radius;
    }

    public double getCircumference()
    {
        return 2 * Math.PI * radius;
    }
}
```

Which of the following best describes the purpose of the `radius` instance variable?

(A) It is used to store the area of the circle.
(B) It stores the state of the `Circle` object and is accessible from any class.
(C) It stores the state of the `Circle` object and is only accessible within the `Circle` class.
(D) It is a local variable used only in the constructor.

---

### 10. [U3 · Medium]

Consider the following class.

```java
public class Wallet
{
    private double cash;
    private int cards;

    public Wallet(double cash, int cards)
    {
        this.cash = cash;
        this.cards = cards;
    }

    public double getCash() { return cash; }
    public int getCards()   { return cards; }

    public void addCash(double amount)
    {
        cash += amount;
    }

    public boolean removeCard()
    {
        if (cards > 0)
        {
            cards--;
            return true;
        }
        return false;
    }
}
```

The following code segment appears in a method in another class.

```java
Wallet w = new Wallet(20.0, 2);
w.addCash(15.0);
w.removeCard();
w.removeCard();
w.removeCard();
System.out.println(w.getCash() + " " + w.getCards());
```

What is printed as a result of executing this code segment?

(A) `"20.0 0"`
(B) `"35.0 -1"`
(C) `"35.0 0"`
(D) `"35.0 2"`

---

### 11. [U3 · Hard]

Consider the following class.

```java
public class Matrix
{
    private int rows;
    private int cols;

    public Matrix(int r, int c)
    {
        rows = r;
        cols = c;
    }

    public int getRows() { return rows; }
    public int getCols() { return cols; }

    public boolean isSquare()
    {
        return rows == cols;
    }

    public Matrix transpose()
    {
        return new Matrix(cols, rows);
    }

    public boolean canMultiply(Matrix other)
    {
        return this.cols == other.rows;
    }
}
```

The following code segment appears in a method in another class.

```java
Matrix m1 = new Matrix(3, 4);
Matrix m2 = m1.transpose();
System.out.println(m2.getRows() + " " + m2.getCols());
System.out.println(m1.canMultiply(m2));
```

What is printed as a result of executing this code segment?

(A)
```
3 4
false
```

(B)
```
4 3
true
```

(C)
```
4 3
false
```

(D)
```
3 4
true
```

---

### 12. [U4 · Medium]

Consider the following code segment.

```java
int[] arr = {10, 20, 30, 40, 50};
for (int i = 0; i < arr.length - 1; i++)
{
    arr[i] = arr[i + 1];
}
arr[arr.length - 1] = arr[0];
```

What are the contents of `arr` after the code segment executes?

(A) `{20, 30, 40, 50, 10}`
(B) `{20, 30, 40, 50, 20}`
(C) `{10, 20, 30, 40, 10}`
(D) `{50, 10, 20, 30, 40}`

---

### 13. [U4 · Easy]

Consider the following code segment.

```java
int[] nums = {2, 4, 6, 8, 10};
int sum = 0;
for (int n : nums)
{
    sum += n;
}
System.out.println(sum / nums.length);
```

What is printed as a result of executing this code segment?

(A) 5
(B) 30
(C) 6.0
(D) 6

---

### 14. [U4 · Hard]

Consider the following code segment.

```java
int[][] mat = {{1, 4, 7, 2},
               {5, 2, 5, 8},
               {7, 6, 3, 9},
               {2, 8, 9, 6}};
int mismatches = 0;
for (int r = 0; r < mat.length; r++)
{
    for (int c = r + 1; c < mat[r].length; c++)
    {
        if (mat[r][c] != mat[c][r])
            mismatches++;
    }
}
System.out.println(mismatches);
```

What is printed as a result of executing this code segment?

(A) 0
(B) 1
(C) 2
(D) 4

---

### 15. [U4 · Easy]

Consider the following code segment.

```java
ArrayList<String> fruits = new ArrayList<String>();
fruits.add("apple");
fruits.add("banana");
fruits.add("cherry");
System.out.println(fruits.get(1));
```

What is printed as a result of executing this code segment?

(A) `"apple"`
(B) `"banana"`
(C) `"cherry"`
(D) An `IndexOutOfBoundsException` is thrown.

---

### 16. [U4 · Medium]

Consider the following code segment.

```java
ArrayList<Integer> list = new ArrayList<Integer>();
for (int i = 1; i <= 5; i++)
{
    list.add(i * 10);
}
list.add(2, 99);
list.remove(4);
System.out.println(list);
```

What is printed as a result of executing this code segment?

(A) `[10, 20, 99, 30, 50]`
(B) `[10, 20, 99, 30, 40]`
(C) `[10, 20, 99, 40, 50]`
(D) `[10, 99, 20, 30, 50]`

---

### 17. [U4 · Hard]

Consider the following code segment.

```java
ArrayList<String> words = new ArrayList<String>();
words.add("ant");
words.add("bat");
words.add("ant");
words.add("cat");
words.add("ant");

int i = 0;
while (i < words.size())
{
    if (words.get(i).equals("ant"))
    {
        words.remove(i);
    }
    else
    {
        i++;
    }
}
System.out.println(words);
```

What is printed as a result of executing this code segment?

(A) `[bat, cat]`
(B) `[bat, ant, cat]`
(C) `[bat, cat, ant]`
(D) An `IndexOutOfBoundsException` is thrown.

---

### 18. [U4 · Medium]

Consider the following code segment.

```java
int[][] grid = {{1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}};
int sum = 0;
for (int r = 0; r < grid.length; r++)
{
    for (int c = 0; c < grid[0].length; c++)
    {
        if (r < c)
            sum += grid[r][c];
    }
}
System.out.println(sum);
```

What is printed as a result of executing this code segment?

(A) 15
(B) 11
(C) 26
(D) 45

---

### 19. [U4 · Medium]

Consider the following code segment.

```java
int[][] mat = new int[4][4];
for (int r = 0; r < 4; r++)
{
    for (int c = 0; c < 4; c++)
    {
        if (r == c)
            mat[r][c] = 1;
        else
            mat[r][c] = 0;
    }
}
int sum = 0;
for (int[] row : mat)
{
    for (int val : row)
    {
        sum += val;
    }
}
System.out.println(sum);
```

What is printed as a result of executing this code segment?

(A) 0
(B) 16
(C) 10
(D) 4

---

### 20. [U1 · Medium]

Consider the following code segment.

```java
String s = "Hello";
String t = "World";
s.substring(0, 3);
String u = t.substring(1, 4);
String r = s + " " + u;
System.out.println(s + " " + t + " " + r);
```

What is printed as a result of executing this code segment?

(A) `"Hello World Hello orl"`
(B) `"Hel World Hel orl"`
(C) `"Hello orl Hello orl"`
(D) `"Hel orl Hel orl"`

---

### 21. [U1 · Hard]

Consider the following code segment.

```java
String a = new String("Hi");
String b = new String("Hi");
String c = a;

int count = 0;
if (a == b) count++;
if (a == c) count++;
if (a.equals(b)) count++;
if (a.equals(c)) count++;
if (b.equals(c)) count++;
System.out.println(count);
```

What is printed as a result of executing this code segment?

(A) 2
(B) 3
(C) 4
(D) 5

---

### 22. [U3 · Medium]

Consider the following class.

```java
public class Counter
{
    private static int total = 0;
    private int id;

    public Counter()
    {
        total++;
        id = total;
    }

    public int getId() { return id; }
    public static int getTotal() { return total; }
}
```

The following code segment appears in a method in another class.

```java
Counter a = new Counter();
Counter b = new Counter();
Counter c = new Counter();
System.out.println(a.getId() + " " + b.getId() + " " + c.getId() + " " + Counter.getTotal());
```

What is printed as a result of executing this code segment?

(A) `"1 1 1 1"`
(B) `"1 2 3 3"`
(C) `"3 3 3 3"`
(D) `"1 2 3 6"`

---

### 23. [U4 · Hard]

Consider the following code segment.

```java
int[][] grid = {{3, 7, 2, 5},
                {8, 1, 9, 4},
                {6, 5, 3, 7}};

int maxVal = grid[0][0];
int maxR = 0;
int maxC = 0;
for (int r = 0; r < grid.length; r++)
{
    for (int c = 0; c < grid[r].length; c++)
    {
        if (grid[r][c] > maxVal)
        {
            maxVal = grid[r][c];
            maxR = r;
            maxC = c;
        }
    }
}
System.out.println(maxR + "," + maxC + ":" + maxVal);
```

What is printed as a result of executing this code segment?

(A) `"0,1:7"`
(B) `"1,0:8"`
(C) `"1,2:9"`
(D) `"2,3:7"`

---

### 24. [U4 · Medium]

Consider the following method.

```java
public static int fibonacci(int n)
{
    if (n <= 1)
        return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}
```

What value is returned by the call `fibonacci(6)`?

(A) 5
(B) 6
(C) 8
(D) 13

---

### 25. [U4 · Hard]

Consider the following method.

```java
public static void printPattern(int n)
{
    if (n <= 0)
        return;
    printPattern(n - 1);
    System.out.print(n + " ");
    printPattern(n - 1);
}
```

Which of the following is printed by the call `printPattern(3)`?

(A) `"3 2 1 "`
(B) `"1 2 3 2 1 "`
(C) `"3 2 1 2 3 "`
(D) `"1 2 1 3 1 2 1 "`

---

# Section II: Free Response (4 Questions | 120 Minutes)

**Directions:** SHOW ALL YOUR WORK. REMEMBER THAT PROGRAM SEGMENTS ARE TO BE WRITTEN IN JAVA.

Write your solutions in Java. You may assume all necessary imports. Assume that the code provided compiles and works correctly. You may write helper methods if you wish.

---

## Question 1: StringInspector (5 Points)

This question involves inspecting strings using **only** the six AP CSA Java Quick Reference String methods: `length()`, `substring(int)`, `substring(int, int)`, `indexOf(String)`, `equals(Object)`, and `compareTo(String)`.

```java
public class StringInspector
{
    /** Returns true if the first n characters of str are all the same.
     *  Returns false if n > str.length() or if any of the first n
     *  characters differs from the first character.
     *
     *  Precondition: n >= 1; str is not null
     *
     *  Examples:
     *    hasRepeatingStart("aaabcd", 3) → true
     *    hasRepeatingStart("aaabcd", 4) → false  (4th char 'b' differs)
     *    hasRepeatingStart("hello", 1)  → true   (length-1 prefix is trivially uniform)
     *    hasRepeatingStart("abc", 5)    → false  (n exceeds length)
     */
    public static boolean hasRepeatingStart(String str, int n)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns the number of non-overlapping occurrences of sub in str.
     *  After each match, the search continues from the position
     *  immediately after the matched substring.
     *
     *  Precondition: str and sub are not null; sub.length() >= 1
     *
     *  Examples:
     *    countOccurrences("abababab", "ab") → 4
     *    countOccurrences("aaaa", "aa")     → 2   (non-overlapping: "aa"|"aa")
     *    countOccurrences("hello world", "l") → 3
     *    countOccurrences("abcdef", "xyz")  → 0
     */
    public static int countOccurrences(String str, String sub)
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a) — 2 Points

Complete the `hasRepeatingStart` method. Use `substring(i, i+1)` to extract each character and `equals` to compare to the first character.

### Part (b) — 3 Points

Complete the `countOccurrences` method. Use `indexOf(String)` (which returns `-1` when not found) and `substring(int)` to continue searching after each match.

---

## Question 2: GroceryStore (7 Points)

A `Product` is represented by the following class.

```java
public class Product
{
    private String name;
    private double price;
    private int quantity;

    public Product(String name, double price, int quantity)
    {
        this.name = name;
        this.price = price;
        this.quantity = quantity;
    }

    public String getName()    { return name; }
    public double getPrice()   { return price; }
    public int getQuantity()   { return quantity; }

    public void restock(int amount)
    {
        quantity += amount;
    }

    public boolean sell(int amount)
    {
        if (amount <= quantity)
        {
            quantity -= amount;
            return true;
        }
        return false;
    }
}
```

Write the complete `GroceryStore` class. Your implementation must include:

- A private `ArrayList<Product>` instance variable
- A no-argument constructor that initializes an empty store
- All methods described below

### Part (a)

Write the following methods for the `GroceryStore` class.

- `addProduct(Product p)` — Adds the given product to the store.
- `getProduct(String name)` — Returns the `Product` with the given name, or `null` if not found.
- `getTotalValue()` — Returns the total value of all products (sum of price × quantity for each product).

**Example:**

| Store contents | Method call | Return value |
|---|---|---|
| [("Milk", 3.50, 10), ("Bread", 2.00, 5), ("Eggs", 4.00, 8)] | `getTotalValue()` | `77.0` |
| [("Milk", 3.50, 10), ("Bread", 2.00, 5)] | `getProduct("Bread").getPrice()` | `2.0` |

### Part (b)

Write the following methods for the `GroceryStore` class.

- `getExpensiveProducts(double minPrice)` — Returns a new `ArrayList<Product>` of all products with price >= `minPrice`.
- `removeOutOfStock()` — Removes all products with quantity 0. Returns the number removed.

**Example:**

| Store contents (before) | Method call | Return | Store (after) |
|---|---|---|---|
| [("Milk",3.50,10), ("Bread",2.00,0), ("Eggs",4.00,0)] | `removeOutOfStock()` | `2` | [("Milk",3.50,10)] |

---

## Question 3: StatTracker (6 Points)

This question involves operations on an array of integers representing game scores.

```java
public class StatTracker
{
    private int[] scores;

    /** Constructs a StatTracker with the given scores.
     *  Precondition: scores has at least one element.
     */
    public StatTracker(int[] scores)
    {
        this.scores = scores;
    }

    /** Returns the range of scores (max - min).
     *
     *  Example:
     *    scores = {72, 85, 90, 68, 95}
     *    getRange() → 27   (95 - 68)
     */
    public int getRange()
    {
        /* to be implemented in Part (a) */
    }

    /** Returns an array of the same length as scores where each
     *  element is the difference between the score and the average.
     *  Uses double arithmetic for the average but int for the result
     *  (truncation is fine).
     *
     *  Example:
     *    scores = {70, 80, 90}
     *    average = 80.0
     *    getDeviations() → {-10, 0, 10}
     */
    public int[] getDeviations()
    {
        /* to be implemented in Part (a) */
    }

    /** Returns true if the scores array is sorted in non-decreasing
     *  order, false otherwise.
     *
     *  Examples:
     *    {10, 20, 30, 30, 40} → true
     *    {10, 20, 15, 30}     → false
     *    {5}                  → true
     */
    public boolean isSorted()
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `getRange` method and the `getDeviations` method.

### Part (b)

Complete the `isSorted` method.

---

## Question 4: HeatMap (6 Points)

This question involves analyzing a 2D array of temperature readings.

```java
public class HeatMap
{
    private double[][] temps;

    /** Constructs a HeatMap with the given temperature grid.
     *  Precondition: temps is rectangular with at least 1 row and 1 column.
     */
    public HeatMap(double[][] temps)
    {
        this.temps = temps;
    }

    /** Returns the average temperature across the entire grid.
     *
     *  Example:
     *    {{70.0, 72.0},
     *     {68.0, 74.0}}
     *    getOverallAverage() → 71.0
     */
    public double getOverallAverage()
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a 1D array containing the average temperature of
     *  each row. The length of the returned array equals the
     *  number of rows.
     *
     *  Example:
     *    {{70.0, 72.0, 74.0},
     *     {80.0, 82.0, 84.0}}
     *    getRowAverages() → {72.0, 82.0}
     */
    public double[] getRowAverages()
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a new 2D boolean array of the same dimensions where
     *  each element is true if the corresponding temperature is
     *  above the overall average, false otherwise.
     *
     *  Example:
     *    {{70.0, 72.0},     overall avg = 71.0
     *     {68.0, 74.0}}
     *
     *    getHotSpots() →
     *    {{false, true},
     *     {false, true}}
     */
    public boolean[][] getHotSpots()
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `getOverallAverage` method and the `getRowAverages` method.

### Part (b)

Complete the `getHotSpots` method. You may call `getOverallAverage` regardless of whether you completed Part (a).
