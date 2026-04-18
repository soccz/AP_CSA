# AP Computer Science A — Level Test 8

> **CED 2025-26 (4-Unit) 기준**
> U1 Using Objects and Methods · U2 Selection and Iteration · U3 Class Creation · U4 Data Collections
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
int a = 7, b = 2;
double c = a / b;
double d = (double) a / b;
System.out.println(c + " " + d);
```

What is printed?

(A) `3.5 3.5`
(B) `3 3.5`
(C) `3.0 3.5`
(D) `3.0 3.0`

---

### 2. [U1 · Medium]

```java
int x = 2;
int y = 3;
int result = (int) Math.pow(x, y) + 5;
System.out.println(result);
```

What is printed?

(A) `8`
(B) `13`
(C) `11`
(D) Compile-time error

---

### 3. [U1 · Medium]

```java
String s = "automation";
int len = s.length();
String result = s.substring(len - 4) + s.substring(0, 4);
System.out.println(result);
```

What is printed?

(A) `tionauto`
(B) `autotion`
(C) `tionatumat`
(D) `auto`

---

### 4. [U1 · Medium]

Consider the following expression, which generates a random integer:

```java
(int)(Math.random() * 10) + 5
```

What is the range of possible values (inclusive on both ends)?

(A) `0 to 14`
(B) `1 to 10`
(C) `5 to 15`
(D) `5 to 14`

---

### 5. [U1 · Hard]

```java
String s = "abracadabra";
int p1 = s.indexOf("ra");
String rest = s.substring(p1 + 2);
int p2 = rest.indexOf("ra");
int p3 = rest.indexOf("xyz");
System.out.println(p1 + " " + p2 + " " + p3);
```

What is printed?

(A) `2 5 -1`
(B) `2 9 -1`
(C) `2 5 0`
(D) `9 -1 -1`

---

### 6. [U2 · Easy]

```java
int count = 0;
for (int i = 1; i <= 10; i += 2) {
    count++;
}
System.out.println(count);
```

What is printed?

(A) `4`
(B) `10`
(C) `5`
(D) `6`

---

### 7. [U2 · Medium]

```java
int score = 75;
String grade = "F";
if (score >= 90) grade = "A";
else if (score >= 80) grade = "B";
else if (score >= 70) grade = "C";
else if (score >= 60) grade = "D";
System.out.println(grade + " " + (score >= 70));
```

What is printed?

(A) `F false`
(B) `C true`
(C) `B true`
(D) `C false`

---

### 8. [U2 · Medium]

```java
int n = 1;
int product = 1;
while (product < 50) {
    product *= 2;
    n++;
}
System.out.println(n + " " + product);
```

What is printed?

(A) `6 32`
(B) `6 64`
(C) `7 32`
(D) `7 64`

---

### 9. [U2 · Medium]

```java
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= i; j++) {
        System.out.print(j);
    }
    System.out.println();
}
```

What is printed?

(A)
```
1 / 11 / 111
```
(B)
```
1 / 12 / 123
```
(C)
```
123 / 123 / 123
```
(D)
```
3 / 23 / 123
```

(여기서 `/`는 줄바꿈을 의미합니다.)

---

### 10. [U2 · Hard]

```java
public static boolean check(int n) {
    System.out.print(n + " ");
    return n > 0;
}

public static void main(String[] args) {
    boolean result = check(5) || check(-3) && check(10);
    System.out.println(result);
}
```

What is printed?

(A) `5 -3 10 true`
(B) `5 -3 true`
(C) `5 true`
(D) `5 -3 10 false`

---

### 11. [U3 · Easy]

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
}
```

The following code is then executed:

```java
Point p = new Point(3, 7);
System.out.println(p.getX() + p.getY());
```

What is printed?

(A) `10`
(B) `3`
(C) `7`
(D) `37`

---

### 12. [U3 · Medium]

```java
public class Coin {
    private String face;
    public Coin(String f) { face = f; }
    public String toString() { return "[" + face + "]"; }
}
```

Given the following code in `main`:

```java
Coin c = new Coin("Heads");
System.out.println(c);
System.out.println("Flip: " + c);
```

What is printed?

(A)
```
Heads
Flip: Heads
```
(B)
```
[Heads]
Flip: Coin@1a2b3c
```
(C)
```
Coin@1a2b3c
Flip: Coin@1a2b3c
```
(D)
```
[Heads]
Flip: [Heads]
```

---

### 13. [U3 · Medium]

```java
public class Account {
    private int balance;
    public Account(int b) { balance = b; }
    public int deposit(int amt) {
        balance += amt;
        return balance;
    }
    public int getBalance() { return balance; }
}
```

The following code is then executed:

```java
Account a = new Account(100);
int x = a.deposit(50);
int y = a.deposit(30);
System.out.println(x + " " + y + " " + a.getBalance());
```

What is printed?

(A) `100 100 100`
(B) `150 180 180`
(C) `50 30 180`
(D) `150 180 100`

---

### 14. [U3 · Hard]

```java
public class Box {
    private int[] items;

    public Box(int[] arr) {
        items = arr;
    }

    public Box(Box other) {
        items = other.items;
    }

    public void set(int i, int v) {
        items[i] = v;
    }

    public int get(int i) {
        return items[i];
    }
}
```

The following code is then executed:

```java
int[] a = {1, 2, 3};
Box b1 = new Box(a);
Box b2 = new Box(b1);
b2.set(0, 99);
System.out.println(b1.get(0) + " " + a[0]);
```

What is printed?

(A) `1 1`
(B) `99 1`
(C) `99 99`
(D) `1 99`

---

### 15. [U4 · Easy]

```java
int[] arr = {3, 7, 2, 8, 5};
int max = arr[0];
for (int n : arr) {
    if (n > max) max = n;
}
System.out.println(max);
```

What is printed?

(A) `8`
(B) `3`
(C) `7`
(D) `25`

---

### 16. [U4 · Medium]

```java
ArrayList<String> list = new ArrayList<>();
list.add("a");
list.add("b");
list.add("c");
list.add("d");
String x = list.remove(1);
System.out.println(x + " " + list);
```

What is printed?

(A) `a [b, c, d]`
(B) `1 [a, c, d]`
(C) `b [a, b, c, d]`
(D) `b [a, c, d]`

---

### 17. [U4 · Medium]

```java
int[][] m = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
int total = 0;
for (int j = 0; j < m[1].length; j++) {
    total += m[1][j];
}
System.out.println(total);
```

What is printed?

(A) `6`
(B) `15`
(C) `12`
(D) `24`

---

### 18. [U4 · Hard]

```java
int[][] m = {
    {1, 2, 9},
    {4, 4, 4},
    {1, 5, 9}
};
int count = 0;
for (int i = 0; i < m.length; i++) {
    int sum = 0;
    for (int j = 0; j < m[i].length; j++) sum += m[i][j];
    double avg = sum / 3.0;
    for (int j = 0; j < m[i].length; j++) {
        if (m[i][j] > avg) count++;
    }
}
System.out.println(count);
```

What is printed?

(A) `0`
(B) `1`
(C) `2`
(D) `3`

---

### 19. [U4 · Medium]

```java
int[] src = {1, 2, 3, 4, 5};
ArrayList<Integer> list = new ArrayList<>();
for (int i = src.length - 1; i >= 0; i--) {
    if (src[i] % 2 == 0) {
        list.add(0, src[i]);
    }
}
System.out.println(list);
```

What is printed?

(A) `[2, 4]`
(B) `[4, 2]`
(C) `[2, 4, 5]`
(D) `[1, 3, 5]`

---

### 20. [U4 · Hard]

The following code performs **selection sort** (CED 4.15) on an array.

```java
int[] arr = {7, 2, 9, 4, 1};
for (int i = 0; i < arr.length - 1; i++) {
    int minIdx = i;
    for (int j = i + 1; j < arr.length; j++) {
        if (arr[j] < arr[minIdx]) {
            minIdx = j;
        }
    }
    int temp = arr[i];
    arr[i] = arr[minIdx];
    arr[minIdx] = temp;
}
```

After the **outer loop has completed exactly 2 iterations** (`i = 0` and `i = 1` finished), what is the contents of `arr`?

(A) `{1, 2, 4, 7, 9}`
(B) `{1, 2, 4, 9, 7}`
(C) `{2, 7, 9, 4, 1}`
(D) `{1, 2, 9, 4, 7}`

---

### 21. [U4 · Easy]

```java
ArrayList<Integer> list = new ArrayList<>();
list.add(5);
list.add(10);
list.add(15);
list.remove(1);
list.add(0, 20);
System.out.println(list.size() + " " + list.get(0));
```

What is printed?

(A) `3 5`
(B) `3 20`
(C) `2 20`
(D) `2 5`

---

### 22. [U4 · Medium]

```java
int[][] m = {
    {1, 2},
    {3, 4}
};
for (int i = 0; i < m.length; i++) {
    for (int j = 0; j < m[0].length; j++) {
        m[i][j] *= 2;
    }
}
int total = 0;
for (int[] row : m) {
    for (int v : row) total += v;
}
System.out.println(total);
```

What is printed?

(A) `20`
(B) `10`
(C) `40`
(D) `4`

---

### 23. [U4 · Hard]

```java
int[][] m = {
    {4, 1, 7},
    {9, 3, 2},
    {5, 8, 6}
};
int maxRow = 0, maxCol = 0;
for (int i = 0; i < m.length; i++) {
    for (int j = 0; j < m[i].length; j++) {
        if (m[i][j] > m[maxRow][maxCol]) {
            maxRow = i;
            maxCol = j;
        }
    }
}
System.out.println(maxRow + " " + maxCol);
```

What is printed?

(A) `2 1`
(B) `0 2`
(C) `1 0`
(D) `9 1`

---

### 24. [U4 · Medium]

```java
public static int power(int base, int exp) {
    if (exp == 0) return 1;
    return base * power(base, exp - 1);
}
```

What is returned by the call `power(3, 4)`?

(A) `27`
(B) `81`
(C) `12`
(D) `243`

---

### 25. [U4 · Hard]

The following method performs **binary search** (CED 4.17). It returns the **number of comparisons** performed when the target is found, or `-1` if not found.

```java
public static int binarySearch(int[] arr, int target) {
    int low = 0;
    int high = arr.length - 1;
    int count = 0;
    while (low <= high) {
        int mid = (low + high) / 2;
        count++;
        if (arr[mid] == target) return count;
        if (arr[mid] < target) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}
```

Given the **sorted** array:

```java
int[] arr = {2, 5, 8, 11, 14, 17, 20, 23, 26};
int result = binarySearch(arr, 17);
```

What is the value of `result`?

(A) `1`
(B) `2`
(C) `4`
(D) `3`

---

# Section II: Free Response (4 Questions | 90 Minutes)

**Total: 24 points (5 + 7 + 6 + 6)**

**Directions:** Show all your work. Remember that program segments are to be written in Java. Notes:
- Assume that the classes listed in the Java Quick Reference have been imported where appropriate.
- Unless otherwise noted, assume that parameters in method calls are not `null` and that methods are called only when their preconditions are satisfied.
- In writing solutions for each question, you may use any of the accessible methods that are listed in classes defined in that question. Writing significant amounts of code that can be replaced by a call to one of these methods will not receive full credit.

---

## FRQ Q1: GradeBook (5 Points)

A `GradeBook` class stores a fixed list of integer grades (0-100) and supports simple analytics.

```java
public class GradeBook {
    /** The grades array, with grades[i] representing the i-th grade. Not null. */
    private int[] grades;

    /** Constructs a GradeBook from the given array of grades. */
    public GradeBook(int[] g) {
        grades = g;
    }

    /** Returns the number of grades >= threshold. */
    public int countPassing(int threshold) {
        /* Part (a) */
    }

    /**
     * Returns a new array of the same length as grades, where each element is
     * the corresponding grade plus bonus, but capped at 100.
     * The underlying grades field is NOT modified.
     */
    public int[] addBonus(int bonus) {
        /* Part (b) */
    }

    // ... other methods not shown ...
}
```

### Part (a) [2 points]

Write the `countPassing` method. The method should return the count of elements in `grades` that are greater than or equal to the given `threshold`.

**Example:**
- If `grades = {85, 60, 92, 55, 78}` and `threshold = 70`, then `countPassing(70)` returns `3` (the grades 85, 92, and 78).

Complete method `countPassing`:

```java
public int countPassing(int threshold) {

}
```

### Part (b) [3 points]

Write the `addBonus` method. The method should return a new `int[]` array of the same length as `grades`, where each element equals the corresponding grade plus `bonus`, but **capped at 100** (so no element in the returned array exceeds 100). The original `grades` array must **not** be modified.

**Example:**
- If `grades = {85, 60, 92, 55, 78}` and `bonus = 15`, then `addBonus(15)` returns `{100, 75, 100, 70, 93}` (85+15=100 cap, 60+15=75, 92+15=100 cap, 55+15=70, 78+15=93).

Complete method `addBonus`:

```java
public int[] addBonus(int bonus) {

}
```

---

## FRQ Q2: Library (7 Points)

A `Library` keeps a collection of `Book` objects and supports basic operations.

```java
public class Book {
    private String title;
    private int pages;

    public Book(String t, int p) {
        title = t;
        pages = p;
    }

    public String getTitle() { return title; }
    public int getPages()    { return pages; }
}
```

### Part (a) [4 points]

Write the **complete** `Library` class. The class must support the following:

1. A private field storing an `ArrayList<Book>` — the books currently in the library.
2. A no-argument constructor that initializes the field to an empty list.
3. A method `void addBook(Book b)` that appends `b` to the list.
4. A method `int totalPages()` that returns the sum of `getPages()` values across all books in the library. If the library is empty, return `0`.

Write the full class including the field, constructor, and the two methods `addBook` and `totalPages`.

**Example:**
- Starting with an empty `Library lib`, after `lib.addBook(new Book("A", 100)); lib.addBook(new Book("B", 250));`, then `lib.totalPages()` returns `350`.

### Part (b) [3 points]

Add a method `int removeShort(int minPages)` to the `Library` class that removes every book whose `getPages() < minPages` and returns the number of books removed. The relative order of remaining books must be preserved.

**Examples:**
- If the library contains books with pages `[100, 50, 300, 80, 450]` and `minPages = 100`, after calling `removeShort(100)`, the library contains books with pages `[100, 300, 450]` and the method returns `2`.
- If no books qualify for removal, the library is unchanged and the method returns `0`.

Complete method `removeShort`:

```java
public int removeShort(int minPages) {

}
```

---

## FRQ Q3: Inventory (6 Points)

A store tracks its products using a list of `Item` objects. Each item has a name, a price, and an availability flag. The `Item` class is **partial declaration** — only the parts you may use are shown.

```java
public class Item {
    /** The display name of the item. Not null. */
    private String name;
    /** The unit price of the item, in dollars. Always >= 0. */
    private double price;
    /** Whether the item is currently in stock. */
    private boolean available;

    public Item(String n, double p, boolean a) {
        name = n;
        price = p;
        available = a;
    }

    public String getName()      { return name; }
    public double getPrice()     { return price; }
    public boolean isAvailable() { return available; }

    // ... other methods not shown ...
}
```

The `Inventory` class stores items in an `ArrayList<Item>` and supports basic analytics.

```java
public class Inventory {
    /** The items in this inventory. Not null. May be empty. */
    private ArrayList<Item> items;

    public Inventory(ArrayList<Item> i) {
        items = i;
    }

    /** Returns the number of available items whose price is at most maxPrice. */
    public int countAffordable(double maxPrice) {
        /* Part (a) */
    }

    /**
     * Returns the average price of available items whose price is in the
     * inclusive range [minPrice, maxPrice].
     * Precondition: at least one available item lies in the range.
     */
    public double averagePriceInRange(double minPrice, double maxPrice) {
        /* Part (b) */
    }

    // ... other methods not shown ...
}
```

### Part (a) [3 points]

Write the `countAffordable` method. Return the count of items in `items` that are **both** available (`isAvailable()` returns `true`) **and** have a price (`getPrice()`) less than or equal to `maxPrice`.

**Example:** Suppose `items` contains the following:

| index | name   | price | available |
|-------|--------|-------|-----------|
| 0     | "Pen"  | 1.50  | true      |
| 1     | "Book" | 12.00 | false     |
| 2     | "Mug"  | 8.75  | true      |
| 3     | "Lamp" | 25.00 | true      |
| 4     | "Cap"  | 9.99  | true      |

- `countAffordable(10.00)` returns `3` (Pen, Mug, Cap — all available and ≤ $10.00; Book is unavailable; Lamp exceeds $10.00).
- `countAffordable(1.00)` returns `0`.

Complete method `countAffordable`:

```java
public int countAffordable(double maxPrice) {

}
```

### Part (b) [3 points]

Write the `averagePriceInRange` method. Return, as a `double`, the average price of items that are **available** AND whose price is in the inclusive range `[minPrice, maxPrice]`. You may assume the precondition holds (at least one such item exists), so you do not need to handle a divide-by-zero case.

**Example (using the table above):**
- `averagePriceInRange(5.00, 20.00)` returns the average of `{8.75, 9.99}` (Mug and Cap; Book is unavailable; Lamp is out of range; Pen is out of range), i.e., `9.37` (approximately).

Complete method `averagePriceInRange`:

```java
public double averagePriceInRange(double minPrice, double maxPrice) {

}
```

---

## FRQ Q4: ScoreGrid (6 Points)

A `ScoreGrid` stores test scores for a class of students in a 2D array. Rows represent students (0-indexed), columns represent tests (0-indexed). Every row has the same length.

```java
public class ScoreGrid {
    /** scores[i][j] is the score of student i on test j. Not null, rectangular. */
    private int[][] scores;

    /** Constructs a ScoreGrid from the given 2D array. */
    public ScoreGrid(int[][] s) {
        scores = s;
    }

    /** Returns the sum of all scores for the student at studentIdx. */
    public int studentTotal(int studentIdx) {
        /* Part (a1) */
    }

    /** Returns the average score on the test at testIdx. Returns a double. */
    public double classAverage(int testIdx) {
        /* Part (a2) */
    }

    /** Returns the index of the student with the highest total score.
     *  In case of ties, return the smallest such index. */
    public int topStudentIdx() {
        /* Part (b) */
    }
}
```

### Part (a) [3 points]

Write both `studentTotal` (1.5 pts) and `classAverage` (1.5 pts).

- `studentTotal(int studentIdx)` returns the sum of all elements in row `studentIdx` of `scores`.
- `classAverage(int testIdx)` returns the **average** (as a `double`) of all elements in column `testIdx` of `scores`. You may assume `scores` has at least one row.

**Example:** Given
```java
int[][] s = {
    {80, 90, 70},
    {85, 95, 80},
    {75, 65, 85}
};
ScoreGrid g = new ScoreGrid(s);
```
- `g.studentTotal(1)` returns `260` (85+95+80)
- `g.classAverage(0)` returns `80.0` ((80+85+75)/3.0)

Complete methods `studentTotal` and `classAverage`:

```java
public int studentTotal(int studentIdx) {

}

public double classAverage(int testIdx) {

}
```

### Part (b) [3 points]

Write `topStudentIdx`. Return the index of the student whose total score across all tests is the highest. If multiple students are tied for the highest total, return the **smallest** such index.

You may assume `scores` has at least one row.

**Examples (using `s` above):**
- Student 0 total = 240, Student 1 total = 260, Student 2 total = 225.
- `g.topStudentIdx()` returns `1`.

If two students tie with total 260, return the one with the smaller row index.

**Note:** You may call `studentTotal` from this method if helpful.

Complete method `topStudentIdx`:

```java
public int topStudentIdx() {

}
```

---

**END OF TEST**
