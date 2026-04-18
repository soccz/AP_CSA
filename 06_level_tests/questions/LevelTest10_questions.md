# AP Computer Science A — Level Test 10

> **CED 2025-26 (4-Unit) 기준**
> U1 Using Objects and Methods · U2 Selection and Iteration · U3 Class Creation · U4 Data Collections

> **Purpose:** Diagnostic exam targeting AP CSA score of 5
> **Time:** Section I (50 min) + Section II (120 min) = 170 min total
> **Scoring:** MCQ 25 × 1 pt = 25 pts / FRQ 5 + 7 + 6 + 6 = 24 pts / **Total: 49 pts**

---

# Section I: Multiple Choice (25 Questions | 50 Minutes)

**Unit Distribution:** U1(4) · U2(6) · U3(4) · U4(11)
**Difficulty:** Easy 5 · Medium 12 · Hard 8

---

### 1. [U1 · Easy]
```java
int a = 100, b = 7;
System.out.println(a / b + " r " + a % b);
```
(A) `"14 r 2"`  (B) `"14.28 r 2"`  (C) `"15 r 2"`  (D) `"14 r 0"`

---

### 2. [U1 · Medium]
```java
double x = (double)(15 / 4) + 15 % 4;
System.out.println(x);
```
(A) 6.75  (B) 6.0  (C) 7.0  (D) 6.5

---

### 3. [U1 · Easy]
```java
String a = "java";
String b = "JAVA";
String c = "java";
System.out.println(a.equals(b) + " " + a.equals(c));
```
(A) `"true true"`  (B) `"false true"`  (C) `"true false"`  (D) `"false false"`

---

### 4. [U1 · Medium]
```java
String word = "abcdef";
String result = "";
for (int i = 0; i < word.length(); i += 2)
{
    result += word.substring(i, i + 1);
}
System.out.println(result);
```
(A) `"ace"`  (B) `"abcdef"`  (C) `"bdf"`  (D) `"abc"`

---

### 5. [U2 · Medium]
```java
int score = 73;
String grade;
if (score >= 90) grade = "A";
else if (score >= 80) grade = "B";
else if (score >= 70) grade = "C";
else grade = "F";

boolean passed = !grade.equals("F");
System.out.println(grade + " " + passed);
```
(A) `"B true"`  (B) `"C false"`  (C) `"C true"`  (D) `"F true"`

---

### 6. [U2 · Medium]
```java
int x = 5;
boolean a = (x > 3);
boolean b = (x < 10);
boolean c = (x == 7);
System.out.println((a && b) || c);
System.out.println(a && (b || c));
```
What is printed?
(A)
```
true
true
```
(B)
```
true
false
```
(C)
```
false
true
```
(D)
```
false
false
```

---

### 7. [U2 · Medium]
```java
int sum = 0;
for (int i = 1; i <= 5; i++)
{
    sum += i * i;
}
System.out.println(sum);
```
(A) 15  (B) 25  (C) 55  (D) 30

---

### 8. [U2 · Hard]
```java
int a = 1, b = 1;
for (int i = 0; i < 8; i++)
{
    int temp = a + b;
    a = b;
    b = temp;
}
System.out.println(b);
```
(A) 21  (B) 34  (C) 55  (D) 89

---

### 9. [U3 · Easy]
```java
public class Message
{
    private String text;
    public Message(String t) { text = t; }
    public String getText() { return text; }
    public int getLength() { return text.length(); }
}
```
```java
Message m = new Message("Hello!");
System.out.println(m.getLength());
```
(A) 5  (B) 7  (C) Compile error  (D) 6

---

### 10. [U3 · Medium]
```java
public class Converter
{
    private double rate;
    public Converter(double r) { rate = r; }
    public double convert(double amount) { return amount * rate; }
    public double reverse(double amount) { return amount / rate; }
}
```
```java
Converter c = new Converter(1.5);
double x = c.convert(100);
double y = c.reverse(x);
System.out.println(x + " " + y);
```
(A) `"150.0 100.0"`  (B) `"100.0 66.67"`  (C) `"150.0 150.0"`  (D) `"100.0 100.0"`

---

### 11. [U3 · Hard]
```java
public class Builder
{
    private String result;
    public Builder() { result = ""; }
    public Builder append(String s) { result += s; return this; }
    public Builder prepend(String s) { result = s + result; return this; }
    public String build() { return result; }
}
```
```java
Builder b = new Builder();
String s = b.append("B").prepend("A").append("C").build();
System.out.println(s);
```
(A) `"ACB"`  (B) `"BAC"`  (C) `"ABC"`  (D) `"BCA"`

---

### 12. [U4 · Medium]
```java
int[] arr = {1, 2, 3, 4, 5};
for (int i = arr.length - 1; i > 0; i--) {
    arr[i] = arr[i - 1];
}
arr[0] = 0;
System.out.println(arr[0] + " " + arr[2] + " " + arr[4]);
```
(A) `"1 3 5"`  (B) `"0 2 4"`  (C) `"0 1 4"`  (D) `"0 3 4"`

---

### 13. [U4 · Easy]
```java
int[] arr = {1, 2, 3, 4, 5};
int[] copy = new int[arr.length];
for (int i = 0; i < arr.length; i++)
    copy[i] = arr[i];
copy[0] = 99;
System.out.println(arr[0] + " " + copy[0]);
```
(A) `"99 99"`  (B) `"1 1"`  (C) `"99 1"`  (D) `"1 99"`

---

### 14. [U4 · Hard]
```java
int[] arr = {1, 3, 2, 3, 1, 3, 2};
int mode = arr[0];
int maxCount = 0;
for (int i = 0; i < arr.length; i++) {
    int count = 0;
    for (int j = 0; j < arr.length; j++) {
        if (arr[j] == arr[i]) count++;
    }
    if (count > maxCount) {
        maxCount = count;
        mode = arr[i];
    }
}
System.out.println(mode + " " + maxCount);
```
(A) `"1 2"`  (B) `"3 3"`  (C) `"2 3"`  (D) `"3 7"`

---

### 15. [U4 · Easy]
```java
ArrayList<String> list = new ArrayList<String>();
list.add("one"); list.add("two"); list.add("three");
String old = list.set(1, "TWO");
System.out.println(old + " " + list.get(1) + " " + list.size());
```
(A) `"two TWO 3"`  (B) `"TWO two 3"`  (C) `"two TWO 4"`  (D) `"TWO TWO 3"`

---

### 16. [U4 · Medium]
```java
ArrayList<Integer> list = new ArrayList<Integer>();
for (int i = 0; i < 5; i++) list.add(i);
// list = [0, 1, 2, 3, 4]
for (int i = 0; i < list.size() / 2; i++)
{
    int temp = list.get(i);
    list.set(i, list.get(list.size() - 1 - i));
    list.set(list.size() - 1 - i, temp);
}
System.out.println(list);
```
(A) `[4, 3, 2, 1, 0]`  (B) `[0, 1, 2, 3, 4]`  (C) `[4, 1, 2, 3, 0]`  (D) `[0, 4, 2, 1, 3]`

---

### 17. [U4 · Hard]
```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(1); list.add(2); list.add(3); list.add(4); list.add(5);

ArrayList<Integer> result = new ArrayList<Integer>();
while (list.size() > 0)
{
    result.add(list.remove(list.size() - 1));
}
System.out.println(result);
```
(A) `[1, 2, 3, 4, 5]`  (B) `[5, 4, 3, 2, 1]`  (C) `[5, 1, 4, 2, 3]`  (D) `[]`

---

### 18. [U4 · Medium]
```java
int[][] grid = new int[3][3];
for (int r = 0; r < 3; r++)
    for (int c = 0; c < 3; c++)
        grid[r][c] = (r + 1) * (c + 1);
System.out.println(grid[2][2] + " " + grid[0][2]);
```
(A) `"4 2"`  (B) `"6 3"`  (C) `"9 3"`  (D) `"9 2"`

---

### 19. [U4 · Hard]
```java
int[][] mat = {{1, 2, 3},
               {4, 5, 6},
               {7, 8, 9}};
boolean magic = true;
int targetSum = mat[0][0] + mat[0][1] + mat[0][2]; // = 6
for (int r = 1; r < mat.length; r++)
{
    int rowSum = 0;
    for (int c = 0; c < mat[0].length; c++)
        rowSum += mat[r][c];
    if (rowSum != targetSum)
        magic = false;
}
System.out.println(magic);
```
(A) `true`  (B) A compile-time error occurs.  (C) A runtime error occurs.  (D) `false`

---

### 20. [U2 · Medium]
```java
int a = -5;
int b = 3;
int c = -8;
int high = a;
if (b > high) high = b;
if (c > high) high = c;
int low = a;
if (b < low) low = b;
if (c < low) low = c;
System.out.println(high + " " + low);
```
(A) `"-5 3"`  (B) `"-8 3"`  (C) `"3 -5"`  (D) `"3 -8"`

---

### 21. [U2 · Medium]
```java
int count = 0;
int sum = 0;
for (int i = 1; i <= 10; i++) {
    if (i % 2 == 0) {
        sum += i;
    } else {
        count++;
    }
}
System.out.println(count + " " + sum);
```
(A) `"5 25"`  (B) `"5 30"`  (C) `"10 30"`  (D) `"5 55"`

---

### 22. [U3 · Hard]
```java
public class Counter
{
    private int count;
    private int max;
    public Counter(int m) { count = 0; max = m; }
    public boolean increment()
    {
        if (count < max) {
            count++;
            return true;
        }
        return false;
    }
    public int getCount() { return count; }
}
```
```java
Counter c = new Counter(3);
int success = 0;
for (int i = 0; i < 5; i++) {
    if (c.increment()) success++;
}
System.out.println(c.getCount() + " " + success);
```
(A) `"5 5"`  (B) `"3 5"`  (C) `"3 3"`  (D) `"5 3"`

---

### 23. [U4 · Hard]
```java
int[][] mat = {
    {3, 7, 1},
    {5, 4, 2},
    {6, 1, 5}
};
int bestRow = 0;
int bestMin = mat[0][0];
for (int c = 1; c < mat[0].length; c++) {
    if (mat[0][c] < bestMin) bestMin = mat[0][c];
}
for (int r = 1; r < mat.length; r++) {
    int rowMin = mat[r][0];
    for (int c = 1; c < mat[r].length; c++) {
        if (mat[r][c] < rowMin) rowMin = mat[r][c];
    }
    if (rowMin > bestMin) {
        bestMin = rowMin;
        bestRow = r;
    }
}
System.out.println(bestRow + " " + bestMin);
```
(A) `"0 1"`  (B) `"1 2"`  (C) `"2 5"`  (D) `"2 1"`

---

### 24. [U4 · Medium]
```java
public static void printReverse(int[] arr, int idx)
{
    if (idx >= arr.length) return;
    printReverse(arr, idx + 1);
    System.out.print(arr[idx] + " ");
}
```
```java
int[] data = {10, 20, 30};
printReverse(data, 0);
```
What is printed?
(A) `"10 20 30 "`  (B) `"30 "`  (C) Nothing  (D) `"30 20 10 "`

---

### 25. [U4 · Hard]

The following recursive method finds the maximum value in `arr[0..n-1]` (CED 4.16).

```java
public static int findMax(int[] arr, int n)
{
    if (n == 1) return arr[0];
    int prevMax = findMax(arr, n - 1);
    if (arr[n - 1] > prevMax) return arr[n - 1];
    return prevMax;
}
```
```java
int[] data = {4, 8, 1, 9, 3, 6, 2};
System.out.println(findMax(data, data.length));
```
(A) 4  (B) 6  (C) 8  (D) 9

---

# Section II: Free Response (4 Questions | 120 Minutes)

## Question 1: NumberFormatter (5 Points)
```java
public class NumberFormatter
{
    /** Returns str padded with leading zeros to reach width.
     *  If str.length() >= width, return str unchanged.
     *  padLeft("42", 5) → "00042"
     *  padLeft("hello", 3) → "hello" */
    public static String padLeft(String str, int width) { /* Part (a) */ }

    /** Returns a formatted time string "HH:MM:SS" from total seconds.
     *  formatTime(3661) → "01:01:01"
     *  formatTime(90) → "00:01:30" */
    public static String formatTime(int totalSeconds) { /* Part (b) */ }
}
```

## Question 2: Warehouse (7 Points)

A warehouse manages its inventory using a list of `Item` objects. Each `Item` has a unique id (`String`), a quantity (`int`), and a unit price (`double`). The `Item` class is **partial declaration** — only the parts you may use are shown.

```java
public class Item
{
    private String id;
    private int qty;
    private double price;

    public Item(String id, int qty, double price)
    {
        this.id = id; this.qty = qty; this.price = price;
    }

    public String getId()    { return id; }
    public int getQty()      { return qty; }
    public double getPrice() { return price; }

    // ... other methods not shown ...
}
```

Write the **complete** `Warehouse` class. The class must support the following:

1. A `private` field storing an `ArrayList<Item>` named `items` — the items currently in stock.
2. A no-argument constructor that initializes `items` to an empty list.
3. A method `void addItem(Item it)` that appends `it` to `items`.
4. A method `double totalValue()` that returns the **sum of `getQty() * getPrice()`** across all items in `items`. If the warehouse is empty, return `0.0`.

Write the full class including the field, constructor, and the two methods.

**Example:**

```java
Warehouse w = new Warehouse();
w.addItem(new Item("A101", 5, 4.00));   // 5 × 4.00 = 20.00
w.addItem(new Item("B202", 3, 12.50));  // 3 × 12.50 = 37.50
w.addItem(new Item("C303", 10, 1.25));  // 10 × 1.25 = 12.50
```

- `w.totalValue()` returns `70.00` (20.00 + 37.50 + 12.50).
- An empty `Warehouse` returns `0.0` from `totalValue()`.

## Question 3: Election (6 Points)

An election system tracks individual votes using a `Vote` class. Each `Vote` has a candidate name (`String`), a weight (`int` — some votes count more, e.g., delegate votes), and a validity flag (`boolean`). The `Vote` class is **partial declaration** — only the parts you may use are shown.

```java
public class Vote
{
    private String candidate;
    private int weight;
    private boolean valid;

    public Vote(String c, int w, boolean v)
    {
        candidate = c; weight = w; valid = v;
    }

    public String getCandidate() { return candidate; }
    public int getWeight()       { return weight; }
    public boolean isValid()     { return valid; }

    // ... other methods not shown ...
}
```

The `Election` class stores votes in an `ArrayList<Vote>` and supports analytics.

```java
public class Election
{
    /** The votes in this election. Not null. May be empty. */
    private ArrayList<Vote> votes;

    public Election(ArrayList<Vote> v) { votes = v; }

    /** Returns the total weight of valid votes for the given candidate.
     *  Returns 0 if no valid votes match. */
    public int totalWeightFor(String candidate)
    {
        /* Part (a) */
    }

    /** Returns the average weight of valid votes for the given candidate.
     *  Precondition: at least one valid vote exists for candidate. */
    public double averageWeightFor(String candidate)
    {
        /* Part (b) */
    }

    // ... other methods not shown ...
}
```

### Part (a) [3 points]

Write the `totalWeightFor` method. Iterate through `votes` and return the **sum of `getWeight()`** for votes that are **both** valid (`isValid()` returns `true`) **and** for the matching `candidate` (use `.equals()` for String comparison). If no votes match, return `0`.

**Example:** Suppose `votes` contains the following:

| index | candidate | weight | valid |
|-------|-----------|--------|-------|
| 0     | "Alice"   | 3      | true  |
| 1     | "Bob"     | 2      | true  |
| 2     | "Alice"   | 1      | false |
| 3     | "Alice"   | 5      | true  |
| 4     | "Bob"     | 4      | true  |

- `totalWeightFor("Alice")` returns `8` (3 + 5; the invalid vote of weight 1 is excluded).
- `totalWeightFor("Bob")` returns `6` (2 + 4).
- `totalWeightFor("Carol")` returns `0` (no votes match).

Complete method `totalWeightFor`:

```java
public int totalWeightFor(String candidate)
{

}
```

### Part (b) [3 points]

Write the `averageWeightFor` method. Return, as a `double`, the average of `getWeight()` values for votes that are **both** valid **and** for the matching `candidate`. You may assume the precondition holds (at least one such vote exists), so divide-by-zero need not be handled.

**Examples (using the table above):**

- `averageWeightFor("Alice")` returns `4.0` (average of {3, 5} = (3+5)/2).
- `averageWeightFor("Bob")` returns `3.0` (average of {2, 4}).

Complete method `averageWeightFor`:

```java
public double averageWeightFor(String candidate)
{

}
```

## Question 4: SeatingChart (6 Points)

A theater tracks occupancy with a 2D `int` array where `0` = empty seat and `1` = occupied seat. Rows and columns are 0-indexed. Every row has the same length (rectangular grid).

```java
public class SeatingChart
{
    /** seats[r][c] = 0 if empty, 1 if occupied. Not null, rectangular. */
    private int[][] seats;

    public SeatingChart(int[][] s) { seats = s; }

    /** Returns the number of empty seats (cells equal to 0) in the row at rowIdx. */
    public int countEmptyInRow(int rowIdx)
    {
        /* Part (a) */
    }

    /** Returns the index of the column that has the MOST empty seats.
     *  In case of ties, returns the smallest such column index. */
    public int columnWithMostEmpty()
    {
        /* Part (b) */
    }
}
```

### Part (a) [3 points]

Write the `countEmptyInRow` method. Return the number of cells equal to `0` (empty seats) in the row at index `rowIdx`. You may assume `rowIdx` is a valid row index.

**Example:** Given
```java
int[][] s = {
    {0, 1, 0, 1, 0},   // row 0: 3 empty
    {1, 1, 1, 0, 1},   // row 1: 1 empty
    {0, 0, 0, 0, 0}    // row 2: 5 empty
};
SeatingChart c = new SeatingChart(s);
```

- `c.countEmptyInRow(0)` returns `3`
- `c.countEmptyInRow(1)` returns `1`
- `c.countEmptyInRow(2)` returns `5`

Complete method `countEmptyInRow`:

```java
public int countEmptyInRow(int rowIdx)
{

}
```

### Part (b) [3 points]

Write the `columnWithMostEmpty` method. Return the index of the column that contains the most empty seats (cells equal to `0`). If multiple columns are tied for the most empty seats, return the **smallest** such column index. You may assume the chart has at least one column.

**Example (using `s` above):**

| column | empty count |
|--------|-------------|
| 0      | 2 (rows 0, 2) |
| 1      | 1 (row 2)     |
| 2      | 2 (rows 0, 2) |
| 3      | 1 (row 2)     |
| 4      | 2 (rows 0, 2) |

- `c.columnWithMostEmpty()` returns `0` (columns 0, 2, 4 are tied at 2 empty seats; return the smallest, 0).

Complete method `columnWithMostEmpty`:

```java
public int columnWithMostEmpty()
{

}
```
