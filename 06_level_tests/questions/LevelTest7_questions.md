# AP Computer Science A — Level Test 7

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
System.out.println(3 + 4 + "=" + 3 + 4);
```

What is printed?

(A) `"7=7"`
(B) `"34=34"`
(C) `"7=34"`
(D) `"34=7"`

---

### 2. [U1 · Medium]

```java
double d = Math.sqrt(Math.pow(3, 2) + Math.pow(4, 2));
System.out.println(d);
```

What is printed?

(A) 5
(B) 5.0
(C) 25.0
(D) 7.0

---

### 3. [U1 · Medium]

```java
String s = "abcdef";
System.out.println(s.substring(1) + s.substring(1, 2));
```

What is printed?

(A) `"bc"`
(B) `"bcdef b"`
(C) `"bcdefab"`
(D) `"bcdefb"`

---

### 4. [U1 · Medium]

```java
int n = 5;
String s = "" + n + 2;
System.out.println(s.length());
```

What is printed?

(A) 1
(B) 2
(C) 3
(D) 7

---

### 5. [U1 · Hard]

```java
String s = "programming";
int i1 = s.indexOf("ram");
String tail = s.substring(i1 + 3);
int i2 = tail.indexOf("m");
System.out.println(i1 + " " + tail + " " + i2);
```

What is printed?

(A) `"4 ming 0"`
(B) `"4 ming -1"`
(C) `"1 ramming 0"`
(D) `"4 mming 1"`

---

### 6. [U2 · Easy]

```java
int n = 16;
int count = 0;
while (n > 1)
{
    n /= 2;
    count++;
}
System.out.println(count);
```

What is printed?

(A) 3
(B) 4
(C) 5
(D) 16

---

### 7. [U2 · Medium]

```java
int x = -5;
int y = 10;
if (x > 0 && y > 0 || x < y)
    System.out.println("A");
else
    System.out.println("B");
```

What is printed? (Recall: `&&` has higher precedence than `||`.)

(A) `"A"`
(B) `"B"`
(C) A compile-time error occurs.
(D) The result depends on operand evaluation order.

---

### 8. [U2 · Medium]

```java
int count = 0;
for (int i = 1; i <= 4; i++)
{
    for (int j = 1; j <= i; j++)
    {
        count++;
    }
}
System.out.println(count);
```

What is printed?

(A) 16
(B) 4
(C) 10
(D) 24

---

### 9. [U2 · Hard]

```java
int total = 0;
for (int i = 1; i <= 20; i++)
{
    if (i % 3 != 0)
        total += i;
}
System.out.println(total);
```

What is printed?

(A) 147
(B) 210
(C) 63
(D) 100

---

### 10. [U2 · Hard]

Which of the following Boolean expressions is equivalent to `!(x > 5) || !(y < 10)` for all integer values of `x` and `y`?

(A) `x > 5 && y < 10`
(B) `x <= 5 || y >= 10`
(C) `x <= 5 && y >= 10`
(D) `x < 5 || y > 10`

---

### 11. [U3 · Easy]

```java
public class Dog
{
    private String name;
    private int age;
    public Dog() { age = 0; }
    public String getName() { return name; }
    public int getAge() { return age; }
}
```

```java
Dog d = new Dog();
System.out.println(d.getName() + " " + d.getAge());
```

What is printed?

(A) `"null 0"`
(B) `" 0"`
(C) A compile-time error occurs.
(D) `"0 0"`

---

### 12. [U3 · Medium]

```java
public class Box
{
    private int size;
    public Box(int size)
    {
        size = size;
    }
    public int getSize() { return size; }
}
```

```java
Box b = new Box(10);
System.out.println(b.getSize());
```

What is printed?

(A) 10
(B) 0
(C) A compile-time error occurs.
(D) A `NullPointerException` occurs at runtime.

---

### 13. [U3 · Medium]

```java
public class Account
{
    private double balance;
    public Account(double b) { balance = b; }
    public boolean withdraw(double amount)
    {
        if (amount > balance)
            return false;
        balance -= amount;
        return true;
    }
    public double getBalance() { return balance; }
}
```

```java
Account a = new Account(100);
boolean r1 = a.withdraw(30);
boolean r2 = a.withdraw(80);
System.out.println(r1 + " " + r2 + " " + a.getBalance());
```

What is printed?

(A) `"true true 20.0"`
(B) `"true false 70.0"`
(C) `"true true -10.0"`
(D) `"false false 100.0"`

---

### 14. [U3 · Hard]

```java
public class Counter
{
    private int count;
    public Counter(int c) { count = c; }
    public void set(int c) { count = c; }
    public int get() { return count; }
}

public static void replace(Counter c)
{
    c = new Counter(100);
}

public static void modify(Counter c)
{
    c.set(200);
}
```

The following code appears in another method:

```java
Counter a = new Counter(5);
replace(a);
int v1 = a.get();
modify(a);
int v2 = a.get();
System.out.println(v1 + " " + v2);
```

What is printed?

(A) `"100 200"`
(B) `"5 5"`
(C) `"100 5"`
(D) `"5 200"`

---

### 15. [U4 · Easy]

```java
int[] arr = new int[5];
for (int i = 0; i < arr.length; i++)
{
    arr[i] = i * i;
}
System.out.println(arr[3]);
```

What is printed?

(A) 9
(B) 3
(C) 6
(D) 4

---

### 16. [U4 · Medium]

```java
ArrayList<Integer> list = new ArrayList<Integer>();
for (int i = 1; i <= 5; i++)
{
    list.add(i);
}
list.set(2, list.get(0) + list.get(4));
System.out.println(list);
```

What is printed?

(A) `[1, 2, 3, 4, 5]`
(B) `[6, 2, 6, 4, 5]`
(C) `[1, 2, 6, 4, 5]`
(D) `[1, 2, 6, 4, 6]`

---

### 17. [U4 · Medium]

```java
int[][] grid = {{1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}};
int maxRowSum = 0;
for (int r = 0; r < grid.length; r++)
{
    int sum = 0;
    for (int c = 0; c < grid[r].length; c++)
    {
        sum += grid[r][c];
    }
    if (sum > maxRowSum)
        maxRowSum = sum;
}
System.out.println(maxRowSum);
```

What is printed?

(A) 45
(B) 15
(C) 24
(D) 9

---

### 18. [U4 · Hard]

The following code sums the elements on the outer border of a 4 × 4 grid.

```java
int[][] grid = {{1, 2, 3, 4},
                {5, 6, 7, 8},
                {9, 10, 11, 12},
                {13, 14, 15, 16}};
int sum = 0;
for (int c = 0; c < grid[0].length; c++)
{
    sum += grid[0][c] + grid[grid.length - 1][c];
}
for (int r = 1; r < grid.length - 1; r++)
{
    sum += grid[r][0] + grid[r][grid[0].length - 1];
}
System.out.println(sum);
```

What is printed?

(A) 136
(B) 100
(C) 102
(D) 50

---

### 19. [U4 · Medium]

```java
int[] arr = {3, 7, 2, 8, 4, 8, 1};
int maxVal = arr[0];
int maxIdx = 0;
for (int i = 1; i < arr.length; i++)
{
    if (arr[i] > maxVal)
    {
        maxVal = arr[i];
        maxIdx = i;
    }
}
System.out.println(maxVal + " " + maxIdx);
```

What is printed?

(A) `"8 5"`
(B) `"8 3"`
(C) `"8 1"`
(D) `"7 1"`

---

### 20. [U4 · Hard]

```java
int[][] mat = {{1, 2, 3, 6},
               {4, 5, 6, 9},
               {2, 4, 6, 8},
               {3, 5, 7, 5}};
int matchCount = 0;
for (int r = 0; r < mat.length; r++)
{
    int sum = 0;
    for (int c = 0; c < mat[r].length; c++) sum += mat[r][c];
    int avg = sum / mat[r].length;
    for (int c = 0; c < mat[r].length; c++)
    {
        if (mat[r][c] == avg) matchCount++;
    }
}
System.out.println(matchCount);
```

What is printed?

(A) 1
(B) 2
(C) 3
(D) 4

---

### 21. [U4 · Easy]

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(10);
list.add(20);
list.add(30);
list.add(0, 5);
System.out.println(list.size() + " " + list.get(2));
```

What is printed?

(A) `"3 20"`
(B) `"4 30"`
(C) `"3 30"`
(D) `"4 20"`

---

### 22. [U4 · Medium]

```java
int[] arr = new int[5];
arr[0] = 1;
for (int i = 1; i < arr.length; i++)
{
    arr[i] = arr[i - 1] * 2;
}
System.out.println(arr[0] + " " + arr[2] + " " + arr[4]);
```

What is printed?

(A) `"0 0 0"`
(B) `"2 8 32"`
(C) `"1 4 16"`
(D) `"1 2 5"`

---

### 23. [U4 · Hard]

```java
int[][] m = {{1, 2, 3},
             {4, 5, 6}};
int[][] t = new int[m[0].length][m.length];
for (int r = 0; r < m.length; r++)
{
    for (int c = 0; c < m[0].length; c++)
    {
        t[c][r] = m[r][c];
    }
}
System.out.println(t.length + " " + t[0].length + " " + t[1][0]);
```

What is printed?

(A) `"2 3 4"`
(B) `"3 2 4"`
(C) `"3 2 2"`
(D) `"2 3 2"`

---

### 24. [U4 · Medium]

```java
public static int mystery(int n)
{
    if (n <= 0)
        return 0;
    return n + mystery(n - 2);
}
```

What is returned by `mystery(7)`?

(A) 12
(B) 28
(C) 0
(D) 16

---

### 25. [U4 · Hard]

```java
public static int maxOf(int[] arr, int n)
{
    if (n == 1)
        return arr[0];
    int rest = maxOf(arr, n - 1);
    if (arr[n - 1] > rest)
        return arr[n - 1];
    return rest;
}
```

For `arr = {3, 7, 2, 8, 5}`, what is returned by `maxOf(arr, 5)`?

(A) 5
(B) 7
(C) 8
(D) 25

---

# Section II: Free Response (4 Questions | 90 Minutes)

**Directions:** SHOW ALL YOUR WORK. REMEMBER THAT PROGRAM SEGMENTS ARE TO BE WRITTEN IN JAVA.

---

## Question 1: WordProcessor (5 Points)

```java
public class WordProcessor
{
    /** Returns the number of words in list whose length is
     *  greater than or equal to minLen.
     *  Returns 0 if list is empty.
     *
     *  Examples (minLen = 4):
     *    countLong(["hi", "tree", "banana"], 4)    → 2   ("tree", "banana")
     *    countLong(["a", "b", "c"], 4)             → 0
     *    countLong([], 4)                          → 0
     */
    public static int countLong(ArrayList<String> list, int minLen)
    { /* to be implemented in Part (a) */ }

    /** Returns the LONGEST word in list that starts with prefix.
     *  If multiple words tie for the longest length, returns the FIRST
     *  such word (the earliest one in list).
     *  Returns "" if no word in list starts with prefix.
     *
     *  A word w "starts with" prefix p if the first p.length() characters
     *  of w are exactly equal to p. If w.length() < p.length(), then w
     *  does NOT start with p.
     *
     *  Examples:
     *    longestStartingWith(["apple", "ant", "application", "banana"], "ap")
     *      → "application"
     *    longestStartingWith(["car", "cart", "cargo"], "car")
     *      → "cargo"   ("cargo" has length 5; "cart" has length 4)
     *    longestStartingWith(["cat", "dog"], "z")           → ""
     *    longestStartingWith([], "ap")                      → ""
     */
    public static String longestStartingWith(ArrayList<String> list, String prefix)
    { /* to be implemented in Part (b) */ }
}
```

### Part (a) (2 points)
Complete `countLong`.

### Part (b) (3 points)
Complete `longestStartingWith`.

---

## Question 2: Playlist (7 Points)

The `Song` class has been provided:

```java
public class Song
{
    private String title;
    private int durationSeconds;
    private int playCount;

    public Song(String t, int d)
    {
        title = t;
        durationSeconds = d;
        playCount = 0;
    }

    public String getTitle()         { return title; }
    public int getDurationSeconds()  { return durationSeconds; }
    public int getPlayCount()        { return playCount; }

    /** Increases playCount by 1. */
    public void play()               { playCount++; }
}
```

Write the complete `Playlist` class. The `Playlist` class must have:
- a `private ArrayList<Song>` field
- a **no-argument** constructor that initializes the list to an empty `ArrayList`
- the public methods specified in Part (a) and Part (b) below

### Part (a) (4 points)

Implement the following three methods:

- `public void addSong(Song s)` — adds `s` to the playlist.
- `public int getTotalDuration()` — returns the sum of `getDurationSeconds()` across all songs. Returns `0` if the playlist is empty.
- `public Song mostPlayed()` — returns the song with the **largest** `getPlayCount()`. If multiple songs tie for the maximum play count, returns the **first** such song in the playlist. Returns `null` if the playlist is empty.

### Part (b) (3 points)

Implement:

- `public void playAll()` — calls `play()` on every song in the playlist.
- `public int trim(int maxSongs)` — if the playlist currently has more than `maxSongs` songs, removes all songs **after** the first `maxSongs` songs (keeping the first `maxSongs` songs in their original order). Returns the number of songs that were removed. If the playlist already has `maxSongs` or fewer songs, the method does nothing and returns `0`.
  - **Precondition:** `maxSongs >= 0`.

---

## Question 3: SensorLog (6 Points)

A weather monitoring system records temperature readings using a `Reading` class. Each `Reading` has a location name (`String`), a temperature value (`double`), and a validity flag (`boolean` — false if the sensor was malfunctioning). The `Reading` class is **partial declaration** — only the parts you may use are shown.

```java
public class Reading
{
    private String location;
    private double temperature;
    private boolean valid;

    public Reading(String loc, double t, boolean v)
    {
        location = loc; temperature = t; valid = v;
    }

    public String getLocation()    { return location; }
    public double getTemperature() { return temperature; }
    public boolean isValid()       { return valid; }

    // ... other methods not shown ...
}
```

The `SensorLog` class stores readings in an `ArrayList<Reading>` and supports analytics.

```java
public class SensorLog
{
    /** The readings in this log. Not null. May be empty. */
    private ArrayList<Reading> readings;

    public SensorLog(ArrayList<Reading> r) { readings = r; }

    /** Returns the count of valid readings at the given location.
     *  Returns 0 if no valid readings match. */
    public int countValidAt(String location)
    {
        /* Part (a) */
    }

    /** Returns the average temperature of valid readings at the given location
     *  whose temperature is in the inclusive range [minTemp, maxTemp].
     *  Precondition: at least one valid reading at location is in the range. */
    public double averageTempInRange(String location, double minTemp, double maxTemp)
    {
        /* Part (b) */
    }

    // ... other methods not shown ...
}
```

### Part (a) [3 points]

Write the `countValidAt` method. Iterate through `readings` and return the **count** of readings that are **both** valid (`isValid()` returns `true`) **and** for the matching `location` (use `.equals()` for String comparison).

**Example:** Suppose `readings` contains the following:

| index | location | temperature | valid |
|-------|----------|-------------|-------|
| 0     | "Seoul"  | 22.5        | true  |
| 1     | "Tokyo"  | 18.0        | true  |
| 2     | "Seoul"  | 99.9        | false |
| 3     | "Seoul"  | 24.0        | true  |
| 4     | "Tokyo"  | 19.5        | true  |

- `countValidAt("Seoul")` returns `2` (rows 0, 3 — row 2 is invalid).
- `countValidAt("Tokyo")` returns `2` (rows 1, 4).
- `countValidAt("Paris")` returns `0` (no matches).

Complete method `countValidAt`:

```java
public int countValidAt(String location)
{

}
```

### Part (b) [3 points]

Write the `averageTempInRange` method. Return, as a `double`, the **average** of `getTemperature()` for readings that are **all three**: valid, at the matching `location`, and within `[minTemp, maxTemp]`. You may assume the precondition holds.

**Examples (using the table above):**

- `averageTempInRange("Seoul", 20.0, 30.0)` returns the average of `{22.5, 24.0}` = `23.25`.
- `averageTempInRange("Tokyo", 0.0, 100.0)` returns the average of `{18.0, 19.5}` = `18.75`.

Complete method `averageTempInRange`:

```java
public double averageTempInRange(String location, double minTemp, double maxTemp)
{

}
```

---

## Question 4: SeatingChart (6 Points)

```java
public class SeatingChart
{
    private String[][] seats;  // a null value means the seat is empty

    /** Constructs a seating chart with rows × cols seats, all empty (null).
     *  Precondition: rows > 0 and cols > 0
     */
    public SeatingChart(int rows, int cols)
    {
        seats = new String[rows][cols];
    }

    /** Returns the number of empty seats — the number of null entries in seats. */
    public int emptyCount()
    { /* to be implemented in Part (a) */ }

    /** Assigns name to the FIRST empty seat found, scanning row-by-row:
     *  row 0 left-to-right, then row 1 left-to-right, and so on.
     *  Returns true if the name was assigned; returns false if every seat
     *  was already occupied (no empty seats), in which case no change is made.
     *
     *  Example: on an empty 2 × 3 chart, assign("Alice") places "Alice"
     *  at seats[0][0] and returns true. A subsequent assign("Bob") places
     *  "Bob" at seats[0][1] and returns true.
     */
    public boolean assign(String name)
    { /* to be implemented in Part (a) */ }

    /** Returns true if row r has NO empty (null) seats; otherwise returns false.
     *  Precondition: 0 <= r < seats.length
     */
    public boolean rowFull(int r)
    { /* to be implemented in Part (b) */ }
}
```

### Part (a) (4 points)
Complete `emptyCount` (2 pts) and `assign` (2 pts).

### Part (b) (2 points)
Complete `rowFull`.
