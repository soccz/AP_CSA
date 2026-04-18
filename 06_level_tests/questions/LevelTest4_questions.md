# AP Computer Science A — Level Test 4

> **Purpose:** Diagnostic exam targeting AP CSA score of 5 (CED 2025-26, 4 Units)
> **Time:** Section I (50 min) + Section II (120 min) = 170 min total
> **Scoring:** MCQ 25 × 1 pt = 25 pts / FRQ 5 + 7 + 6 + 6 = 24 pts / **Total: 49 pts**

---

# Section I: Multiple Choice (25 Questions | 50 Minutes)

**Unit Distribution (2025-26 CED):** U1(4) · U2(6) · U3(4) · U4(11)
**Difficulty:** Easy 5 · Medium 12 · Hard 8

**Directions:** Determine the answer to each of the following questions or incomplete statements, using the available space for any necessary scratch work. Then decide which is the best of the choices given. Unless otherwise noted, assume that the classes listed in the Java Quick Reference have been imported where appropriate. Unless otherwise noted, assume that parameters in method calls are not `null` and that methods are called only when their preconditions are met.

---

### 1. [U1 · Easy]

Consider the following code segment.

```java
int a = 45;
int b = 10;
System.out.println(a % b + a / b);
```

What is printed as a result of executing this code segment?

(A) 4
(B) 5
(C) 9
(D) 4.5

---

### 2. [U1 · Medium]

Consider the following code segment.

```java
double x = 9.7;
int y = (int) x;
double z = y;
System.out.println(z);
```

What is printed as a result of executing this code segment?

(A) 9.7
(B) 10.0
(C) 9
(D) 9.0

---

### 3. [U1 · Medium]

Consider the following code segment.

```java
String s = "JAVA PROGRAM";
int space = s.indexOf(" ");
String first = s.substring(0, space);
String last = s.substring(space + 1);
System.out.println(last + " " + first);
```

What is printed as a result of executing this code segment?

(A) `"PROGRAM JAVA"`
(B) `"JAVA PROGRAM"`
(C) `" PROGRAM JAVA"`
(D) `"PROGRAMJAVA"`

---

### 4. [U2 · Medium]

Consider the following code segment.

```java
String word = "MISSISSIPPI";
int count = 0;
int pos = 0;
while (pos < word.length())
{
    if (word.substring(pos, pos + 1).equals("S"))
        count++;
    pos++;
}
System.out.println(count);
```

What is printed as a result of executing this code segment?

(A) 2
(B) 3
(C) 5
(D) 4

---

### 5. [U2 · Medium]

Consider the following code segment.

```java
int age = 16;
boolean hasLicense = false;
String result;
if (age >= 18)
    result = "adult";
else if (age >= 16 && hasLicense)
    result = "driver";
else if (age >= 16)
    result = "eligible";
else
    result = "minor";
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `"adult"`
(B) `"driver"`
(C) `"eligible"`
(D) `"minor"`

---

### 6. [U2 · Medium]

Consider the following code segment.

```java
int a = 5, b = 10, c = 3;
boolean result = (a < b && b > c) || !(a == c) && (b - a == c + 2);
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `true`
(B) `false`
(C) A compile-time error occurs.
(D) A runtime error occurs.

---

### 7. [U2 · Easy]

Consider the following code segment.

```java
int product = 1;
for (int i = 1; i <= 5; i++)
{
    product *= i;
}
System.out.println(product);
```

What is printed as a result of executing this code segment?

(A) 15
(B) 120
(C) 5
(D) 25

---

### 8. [U2 · Hard]

Consider the following code segment.

```java
int x = 256;
int count = 0;
while (x > 1)
{
    x /= 2;
    count++;
}
System.out.println(count);
```

What is printed as a result of executing this code segment?

(A) 7
(B) 8
(C) 9
(D) 256

---

### 9. [U3 · Easy]

Consider the following class.

```java
public class Timer
{
    private int seconds;

    public Timer()
    {
        seconds = 0;
    }

    public void tick()
    {
        seconds++;
    }

    public int getSeconds() { return seconds; }

    public String getTime()
    {
        return seconds / 60 + ":" + seconds % 60;
    }
}
```

The following code segment appears in a method in another class.

```java
Timer t = new Timer();
for (int i = 0; i < 75; i++)
{
    t.tick();
}
System.out.println(t.getTime());
```

What is printed as a result of executing this code segment?

(A) `"0:75"`
(B) `"75:0"`
(C) `"1:15"`
(D) `"1:5"`

---

### 10. [U3 · Medium]

Consider the following class.

```java
public class Box
{
    private int length;
    private int width;
    private int height;

    public Box(int l, int w, int h)
    {
        length = l;
        width = w;
        height = h;
    }

    public int getVolume()
    {
        return length * width * height;
    }

    public int getSurfaceArea()
    {
        return 2 * (length * width + length * height + width * height);
    }

    public boolean fitsInside(Box other)
    {
        return this.length < other.length &&
               this.width < other.width &&
               this.height < other.height;
    }
}
```

The following code segment appears in a method in another class.

```java
Box b1 = new Box(3, 4, 5);
Box b2 = new Box(5, 6, 7);
System.out.println(b1.fitsInside(b2) + " " + b1.getVolume());
```

What is printed as a result of executing this code segment?

(A) `"true 60"`
(B) `"false 60"`
(C) `"true 94"`
(D) `"false 94"`

---

### 11. [U3 · Hard]

Consider the following class.

```java
public class Sequence
{
    private int current;
    private int step;

    public Sequence(int start, int step)
    {
        current = start;
        this.step = step;
    }

    public int getCurrent() { return current; }

    public int next()
    {
        current += step;
        return current;
    }
}
```

The following code segment appears in a method in another class.

```java
Sequence s = new Sequence(2, 3);
int total = s.getCurrent();
for (int i = 0; i < 4; i++)
{
    total += s.next();
}
System.out.println(total);
```

What is printed as a result of executing this code segment?

(A) 14
(B) 32
(C) 40
(D) 44

---

### 12. [U4 · Medium]

Consider the following code segment.

```java
int[] arr = {1, 2, 3, 4, 5, 6};
int result = 0;
for (int i = 0; i < arr.length; i++)
{
    if (arr[i] % 2 == 1)
        result += arr[i];
    else
        result -= arr[i];
}
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) 21
(B) -3
(C) 3
(D) -21

---

### 13. [U4 · Easy]

Consider the following code segment.

```java
int[] nums = new int[5];
for (int i = 0; i < nums.length; i++)
{
    nums[i] = (i + 1) * 2;
}
System.out.println(nums[3]);
```

What is printed as a result of executing this code segment?

(A) 4
(B) 6
(C) 10
(D) 8

---

### 14. [U4 · Hard]

Consider the following code segment.

```java
int[] arr = {3, 1, 4, 1, 5, 9, 2, 6};
int secondMax = Integer.MIN_VALUE;
int max = Integer.MIN_VALUE;
for (int val : arr)
{
    if (val > max)
    {
        secondMax = max;
        max = val;
    }
    else if (val > secondMax && val != max)
    {
        secondMax = val;
    }
}
System.out.println(secondMax);
```

What is printed as a result of executing this code segment?

(A) 4
(B) 5
(C) 9
(D) 6

---

### 15. [U4 · Easy]

Consider the following code segment.

```java
ArrayList<String> items = new ArrayList<String>();
items.add("pen");
items.add("book");
items.add("ruler");
items.remove(1);
System.out.println(items.size() + " " + items.get(1));
```

What is printed as a result of executing this code segment?

(A) `"2 ruler"`
(B) `"3 ruler"`
(C) `"2 book"`
(D) `"3 book"`

---

### 16. [U4 · Medium]

Consider the following code segment.

```java
ArrayList<Integer> nums = new ArrayList<Integer>();
for (int i = 0; i < 5; i++)
{
    nums.add(i * i);
}
System.out.println(nums);
```

What is printed as a result of executing this code segment?

(A) `[0, 1, 4, 9, 16]`
(B) `[1, 4, 9, 16, 25]`
(C) `[0, 2, 4, 6, 8]`
(D) `[0, 1, 2, 3, 4]`

---

### 17. [U4 · Hard]

Consider the following code segment.

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(3);
list.add(1);
list.add(3);
list.add(2);
list.add(1);
list.add(4);

int distinct = 0;
for (int i = 0; i < list.size(); i++)
{
    boolean isFirst = true;
    for (int j = 0; j < i; j++)
    {
        if (list.get(j).equals(list.get(i)))
            isFirst = false;
    }
    if (isFirst) distinct++;
}
System.out.println(distinct);
```

What is printed as a result of executing this code segment?

(A) 3
(B) 4
(C) 5
(D) 6

---

### 18. [U4 · Medium]

Consider the following code segment.

```java
int[][] grid = {{5, 10, 15},
                {20, 25, 30},
                {35, 40, 45}};
int sum = 0;
for (int c = 0; c < grid[0].length; c++)
{
    sum += grid[grid.length - 1][c];
}
System.out.println(sum);
```

What is printed as a result of executing this code segment?

(A) 30
(B) 120
(C) 45
(D) 225

---

### 19. [U4 · Hard]

Consider the following code segment.

```java
int[][] mat = {{1, 2, 3},
               {4, 5, 6},
               {7, 8, 9}};
int[][] result = new int[3][3];
for (int r = 0; r < 3; r++)
{
    for (int c = 0; c < 3; c++)
    {
        result[c][r] = mat[r][c];
    }
}
System.out.println(result[0][2] + " " + result[2][0]);
```

What is printed as a result of executing this code segment?

(A) `"9 1"`
(B) `"3 7"`
(C) `"1 9"`
(D) `"7 3"`

---

### 20. [U1 · Medium]

Consider the following code segment.

```java
System.out.println(1 + 2 + "abc" + 3 + 4);
```

What is printed as a result of executing this code segment?

(A) `"12abc34"`
(B) `"3abc7"`
(C) `"3abc34"`
(D) `"1 2 abc 3 4"`

---

### 21. [U2 · Medium]

Consider the following code segment.

```java
int[] arr = {1, 2, 3, 4};
for (int x : arr)
{
    x = x * 10;
}
int sum = 0;
for (int v : arr)
{
    sum += v;
}
System.out.println(sum);
```

What is printed as a result of executing this code segment?

(A) 100
(B) 0
(C) 40
(D) 10

---

### 22. [U3 · Hard]

Consider the following class.

```java
public class Account
{
    private double balance;
    private String owner;

    public Account()
    {
        this.balance = 100.0;
        this.owner = "Default";
    }

    public Account(String owner)
    {
        this.owner = owner;
    }

    public double getBalance() { return balance; }
    public String getOwner()   { return owner; }
}
```

The following code segment appears in a method in another class.

```java
Account a = new Account();
Account b = new Account("Alice");
System.out.println(a.getBalance() + " " + b.getBalance() + " " + b.getOwner());
```

What is printed as a result of executing this code segment?

(A) `"100.0 100.0 Alice"`
(B) `"100.0 0.0 Alice"`
(C) `"0.0 0.0 Alice"`
(D) A compile-time error occurs.

---

### 23. [U4 · Hard]

Consider the following code segment.

```java
int[][] grid = {{1, 2, 3, 4},
                {5, 6, 7, 8},
                {9, 10, 11, 12}};
int sum = 0;
for (int c = 0; c < grid[0].length; c++)
{
    sum += grid[0][c];
    sum += grid[grid.length - 1][c];
}
for (int r = 1; r < grid.length - 1; r++)
{
    sum += grid[r][0];
    sum += grid[r][grid[0].length - 1];
}
System.out.println(sum);
```

What is printed as a result of executing this code segment?

(A) 13
(B) 52
(C) 65
(D) 78

---

### 24. [U4 · Medium]

Consider the following method.

```java
public static int sumDigits(int n)
{
    if (n < 10)
        return n;
    return n % 10 + sumDigits(n / 10);
}
```

What value is returned by the call `sumDigits(9876)`?

(A) 9
(B) 24
(C) 30
(D) 6

---

### 25. [U4 · Hard]

Consider the following method.

```java
public static int countPaths(int r, int c)
{
    if (r == 0 || c == 0)
        return 1;
    return countPaths(r - 1, c) + countPaths(r, c - 1);
}
```

What value is returned by the call `countPaths(3, 2)`?

(A) 5
(B) 6
(C) 10
(D) 3

---

# Section II: Free Response (4 Questions | 120 Minutes)

**Directions:** SHOW ALL YOUR WORK. REMEMBER THAT PROGRAM SEGMENTS ARE TO BE WRITTEN IN JAVA.

Write your solutions in Java. You may assume all necessary imports. Assume that the code provided compiles and works correctly. You may write helper methods if you wish.

---

## Question 1: WordAnalyzer (5 Points)

This question involves analyzing words.

```java
public class WordAnalyzer
{
    /** Returns the number of times ch appears in word.
     *  Precondition: word is not null; ch has length 1
     *
     *  Examples:
     *    charCount("banana", "a")  → 3
     *    charCount("hello", "l")   → 2
     *    charCount("hello", "z")   → 0
     */
    public static int charCount(String word, String ch)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns the most frequent character in word.
     *  If there is a tie, the character that appears first in
     *  word is returned.
     *  Precondition: word is not null and has length >= 1
     *
     *  Examples:
     *    mostFrequent("banana") → "a"
     *    mostFrequent("abcabc") → "a"
     *    mostFrequent("hello")  → "l"
     */
    public static String mostFrequent(String word)
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `charCount` method.

### Part (b)

Complete the `mostFrequent` method. You should call `charCount` in your solution.

---

## Question 2: Library (7 Points)

A `Book` is represented by the following class.

```java
public class Book
{
    private String title;
    private String author;
    private boolean checkedOut;

    public Book(String title, String author)
    {
        this.title = title;
        this.author = author;
        this.checkedOut = false;
    }

    public String getTitle()     { return title; }
    public String getAuthor()    { return author; }
    public boolean isCheckedOut(){ return checkedOut; }

    public void checkOut()  { checkedOut = true; }
    public void returnBook(){ checkedOut = false; }
}
```

Write the complete `Library` class. Your implementation must include:

- A private `ArrayList<Book>` instance variable
- A no-argument constructor
- All methods described below

### Part (a)

- `addBook(Book b)` — Adds the book to the library.
- `findBook(String title)` — Returns the `Book` with the given title, or `null`.
- `getAvailableBooks()` — Returns an `ArrayList<Book>` of all books that are NOT checked out.

### Part (b)

- `getBooksByAuthor(String author)` — Returns an `ArrayList<Book>` of books by the author.
- `checkOutBook(String title)` — Finds the book, checks it out if available, returns `true`. If not found or already checked out, returns `false`.

---

## Question 3: ArrayShifter (6 Points)

```java
public class ArrayShifter
{
    private int[] data;

    public ArrayShifter(int[] data)
    {
        this.data = data;
    }

    /** Shifts all elements in data one position to the right.
     *  The last element wraps to index 0.
     *
     *  Example:
     *    data (before) = {1, 2, 3, 4, 5}
     *    shiftRight()
     *    data (after)  = {5, 1, 2, 3, 4}
     */
    public void shiftRight()
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a new array containing only elements at even indices.
     *
     *  Example:
     *    data = {10, 20, 30, 40, 50}
     *    getEvenIndexed() → {10, 30, 50}
     */
    public int[] getEvenIndexed()
    {
        /* to be implemented in Part (a) */
    }

    /** Reverses the elements in data in-place.
     *
     *  Example:
     *    data (before) = {1, 2, 3, 4, 5}
     *    reverse()
     *    data (after)  = {5, 4, 3, 2, 1}
     */
    public void reverse()
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete `shiftRight` and `getEvenIndexed`.

### Part (b)

Complete `reverse`.

---

## Question 4: Scoreboard (6 Points)

```java
public class Scoreboard
{
    private int[][] scores;  // scores[player][round]

    /** Constructs a Scoreboard.
     *  Precondition: scores is rectangular, at least 1 player and 1 round.
     */
    public Scoreboard(int[][] scores)
    {
        this.scores = scores;
    }

    /** Returns the total score for the given player (row index).
     *
     *  Example:
     *    scores = {{10, 20, 30},
     *              {15, 25, 35}}
     *    getPlayerTotal(0) → 60
     */
    public int getPlayerTotal(int player)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns the index of the player with the highest total score.
     *  Ties broken by first occurrence.
     */
    public int getWinner()
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a new 2D array of the same dimensions where each
     *  score is replaced by the cumulative total up to that round.
     *
     *  Example:
     *    scores = {{10, 20, 30},
     *              {15, 25, 35}}
     *    getCumulativeScores() →
     *    {{10, 30, 60},
     *     {15, 40, 75}}
     */
    public int[][] getCumulativeScores()
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete `getPlayerTotal` and `getWinner`.

### Part (b)

Complete `getCumulativeScores`.
