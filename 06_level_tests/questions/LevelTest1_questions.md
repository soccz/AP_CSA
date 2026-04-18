# AP Computer Science A — Level Test 1

> **Purpose:** Diagnostic exam targeting AP CSA score of 5
> **Time:** Section I (50 min) + Section II (90 min) = 140 min total
> **Scoring:** MCQ 25 × 1 pt = 25 pts / FRQ 5 + 7 + 6 + 6 = 24 pts / **Total: 49 pts**
> **CED:** AP CSA 2025-26 (4 Units: U1 Using Objects · U2 Selection/Iteration · U3 Class Creation · U4 Data Collections)

---

# Section I: Multiple Choice (25 Questions | 50 Minutes)

**Unit Distribution (CED 2025-26):** U1(4) · U2(5) · U3(4) · U4(12)
**Difficulty:** Easy 5 · Medium 12 · Hard 8

**Directions:** Determine the answer to each of the following questions or incomplete statements, using the available space for any necessary scratch work. Then decide which is the best of the choices given. Unless otherwise noted, assume that the classes listed in the Java Quick Reference have been imported where appropriate. Unless otherwise noted, assume that parameters in method calls are not `null` and that methods are called only when their preconditions are met.

---

### 1. [U1 · Easy]

Consider the following code segment.

```java
int a = 23;
int b = 7;
double result = a / b + a % b;
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) 5.0
(B) 5.285714
(C) 3.0
(D) 8.0

---

### 2. [U1 · Medium]

Consider the following code segment.

```java
int x = 14;
int y = 4;
double result = (double)(x / y) + (double)(x % y);
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) 5.5
(B) 3.5
(C) 6.0
(D) 5.0

---

### 3. [U1 · Medium]

Consider the following code segment.

```java
String word = "programming";
int k = word.indexOf("gram");
String result = word.substring(0, k) + word.substring(k + 4);
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `"proging"`
(B) `"proing"`
(C) `"proamming"`
(D) `"proming"`

---

### 4. [U2 · Medium]

Consider the following code segment.

```java
String s = "ABCDEFGH";
String result = "";
for (int i = 0; i < s.length(); i += 2)
{
    result += s.substring(i, i + 1);
}
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `"ABCD"`
(B) `"ACEG"`
(C) `"BDFH"`
(D) `"ABCDEFGH"`

---

### 5. [U2 · Medium]

Consider the following code segment.

```java
int x = 15;
int y = 8;
String result;
if (x > 10 && y < 5)
    result = "A";
else if (x > 10 || y < 5)
    result = "B";
else
    result = "C";
System.out.println(result);
```

What is printed as a result of executing this code segment?

(A) `"A"`
(B) `"B"`
(C) `"C"`
(D) Nothing is printed because of a compile-time error.

---

### 6. [U2 · Hard]

Consider the following Boolean expression.

```java
!(a > 0 && b < 10) || (a == 0)
```

Which of the following is equivalent to the expression above?

(A) `(a <= 0 || b >= 10) || (a == 0)`
(B) `(a <= 0 && b >= 10) || (a == 0)`
(C) `(a > 0 || b < 10) && (a == 0)`
(D) `(a <= 0 || b >= 10) && (a != 0)`

---

### 7. [U2 · Easy]

Consider the following code segment.

```java
int sum = 0;
for (int i = 1; i <= 10; i++)
{
    if (i % 2 == 0)
        sum += i;
}
System.out.println(sum);
```

What is printed as a result of executing this code segment?

(A) 20
(B) 25
(C) 30
(D) 55

---

### 8. [U2 · Medium]

Consider the following code segment.

```java
int count = 0;
for (int i = 1; i <= 5; i++)
{
    for (int j = 1; j <= i; j++)
    {
        count++;
    }
}
System.out.println(count);
```

What is printed as a result of executing this code segment?

(A) 5
(B) 10
(C) 15
(D) 25

---

### 9. [U3 · Easy]

Consider the following class.

```java
public class Dog
{
    private String name;
    private int age;

    public Dog(String name, int age)
    {
        this.name = name;
        this.age = age;
    }

    public String getName() { return name; }
    public int getAge() { return age; }

    public void haveBirthday()
    {
        age++;
    }
}
```

The following code segment appears in a method in another class.

```java
Dog d = new Dog("Max", 3);
d.haveBirthday();
d.haveBirthday();
System.out.println(d.getName() + " " + d.getAge());
```

What is printed as a result of executing this code segment?

(A) `"Max 3"`
(B) `"Max 4"`
(C) `"Max 5"`
(D) A compile-time error occurs.

---

### 10. [U3 · Medium]

Consider the following class.

```java
public class BankAccount
{
    private double balance;

    public BankAccount(double initial)
    {
        balance = initial;
    }

    public double getBalance() { return balance; }

    public void deposit(double amount)
    {
        if (amount > 0)
            balance += amount;
    }

    public boolean withdraw(double amount)
    {
        if (amount > 0 && amount <= balance)
        {
            balance -= amount;
            return true;
        }
        return false;
    }
}
```

The following code segment appears in a method in another class.

```java
BankAccount acct = new BankAccount(200.0);
acct.deposit(50.0);
acct.withdraw(100.0);
acct.withdraw(200.0);
acct.deposit(-30.0);
System.out.println(acct.getBalance());
```

What is printed as a result of executing this code segment?

(A) `150.0`
(B) `120.0`
(C) `-80.0`
(D) `200.0`

---

### 11. [U3 · Hard]

Consider the following class.

```java
public class Point
{
    private int x;
    private int y;

    public Point(int x, int y)
    {
        this.x = x;
        this.y = y;
    }

    public int getX() { return x; }
    public int getY() { return y; }

    public double distanceTo(Point other)
    {
        int dx = this.x - other.x;
        int dy = this.y - other.y;
        return Math.sqrt(dx * dx + dy * dy);
    }
}
```

The following code segment appears in a method in another class.

```java
Point p1 = new Point(1, 2);
Point p2 = new Point(4, 6);
Point p3 = p1;
System.out.println(p1 == p3);
System.out.println(p1.distanceTo(p2));
```

What is printed as a result of executing this code segment?

(A)
```
false
5.0
```

(B)
```
false
7.0
```

(C)
```
true
7.0
```

(D)
```
true
5.0
```

---

### 12. [U4 · Easy]

Consider the following code segment.

```java
int[] arr = {3, 7, 2, 8, 5};
int total = 0;
for (int val : arr)
{
    total += val;
}
System.out.println(total);
```

What is printed as a result of executing this code segment?

(A) 5
(B) 20
(C) 25
(D) 8

---

### 13. [U4 · Medium]

Consider the following code segment.

```java
int[] arr = {4, 1, 7, 3, 9, 2};
int min = arr[0];
for (int i = 1; i < arr.length; i++)
{
    if (arr[i] < min)
    {
        min = arr[i];
    }
}
System.out.println(min);
```

What is printed as a result of executing this code segment?

(A) 4
(B) 1
(C) 2
(D) 9

---

### 14. [U4 · Hard]

Consider the following code segment.

```java
int[] arr = {1, 2, 2, 3, 3, 3, 1, 4, 4};
int maxRun = 1;
int run = 1;
for (int i = 1; i < arr.length; i++)
{
    if (arr[i] == arr[i - 1])
    {
        run++;
        if (run > maxRun)
            maxRun = run;
    }
    else
    {
        run = 1;
    }
}
System.out.println(maxRun);
```

What is printed as a result of executing this code segment?

(A) 2
(B) 3
(C) 4
(D) 9

---

### 15. [U4 · Easy]

Consider the following code segment.

```java
ArrayList<String> list = new ArrayList<String>();
list.add("red");
list.add("blue");
list.add("green");
list.add(1, "yellow");
System.out.println(list);
```

What is printed as a result of executing this code segment?

(A) `[yellow, red, blue, green]`
(B) `[red, blue, yellow, green]`
(C) `[red, yellow, blue, green]`
(D) `[red, blue, green, yellow]`

---

### 16. [U4 · Medium]

Consider the following code segment.

```java
ArrayList<Integer> nums = new ArrayList<Integer>();
nums.add(5);
nums.add(10);
nums.add(15);
nums.add(20);
nums.set(2, 99);
nums.remove(0);
System.out.println(nums);
```

What is printed as a result of executing this code segment?

(A) `[10, 99, 20]`
(B) `[10, 15, 20]`
(C) `[5, 10, 99, 20]`
(D) `[5, 99, 15, 20]`

---

### 17. [U4 · Hard]

Consider the following code segment.

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(3);
list.add(1);
list.add(4);
list.add(1);
list.add(5);

for (int i = list.size() - 1; i >= 0; i--)
{
    if (list.get(i) < 3)
    {
        list.remove(i);
    }
}
System.out.println(list);
```

What is printed as a result of executing this code segment?

(A) `[3, 4, 5]`
(B) `[3, 1, 4, 5]`
(C) `[3, 4, 1, 5]`
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
    sum += grid[r][r];
}
System.out.println(sum);
```

What is printed as a result of executing this code segment?

(A) 12
(B) 15
(C) 45
(D) 6

---

### 19. [U4 · Hard]

Consider the following code segment.

```java
int[][] mat = {{2, 4, 6},
               {1, 3, 5},
               {9, 7, 8}};
int count = 0;
for (int c = 0; c < mat[0].length; c++)
{
    int colMax = mat[0][c];
    for (int r = 1; r < mat.length; r++)
    {
        if (mat[r][c] > colMax)
            colMax = mat[r][c];
    }
    if (colMax > 6)
        count++;
}
System.out.println(count);
```

What is printed as a result of executing this code segment?

(A) 1
(B) 2
(C) 3
(D) 0

---

### 20. [U1 · Medium]

Consider the following code segment.

```java
double sum = 0.0;
for (int i = 0; i < 10; i++)
{
    sum += 0.1;
}
System.out.println(sum == 1.0);
System.out.println(Math.abs(sum - 1.0) < 0.000001);
```

What is printed as a result of executing this code segment?

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
false
```

(D)
```
false
true
```

---

### 21. [U4 · Medium]

Consider the following code segment.

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(2);
list.add(2);
list.add(2);
list.add(3);
for (int i = 0; i < list.size(); i++)
{
    if (list.get(i) == 2)
    {
        list.remove(i);
    }
}
System.out.println(list);
```

What is printed as a result of executing this code segment?

(A) `[]`
(B) `[2, 3]`
(C) `[3]`
(D) An `IndexOutOfBoundsException` is thrown.

---

### 22. [U3 · Hard]

Consider the following class.

```java
public class Box
{
    private int value;

    public Box(int v)
    {
        value = v;
    }

    public int getValue() { return value; }
    public void setValue(int v) { value = v; }
}
```

The following method appears in another class.

```java
public static void modify(Box a, Box b)
{
    a.setValue(99);
    b = new Box(99);
}
```

The following code segment appears in another method in the same class.

```java
Box p = new Box(1);
Box q = new Box(2);
modify(p, q);
System.out.println(p.getValue() + " " + q.getValue());
```

What is printed as a result of executing this code segment?

(A) `1 2`
(B) `99 99`
(C) `99 2`
(D) `1 99`

---

### 23. [U4 · Hard]

Consider the following code segment.

```java
int[][] grid = { {1, 2, 3, 4},
                 {5, 6, 7, 8},
                 {9, 10, 11, 12},
                 {13, 14, 15, 16} };
int sum = 0;
for (int i = 0; i < grid.length; i++)
{
    sum += grid[i][grid[0].length - 1 - i];
}
System.out.println(sum);
```

What is printed as a result of executing this code segment?

(A) 34
(B) 30
(C) 38
(D) 40

---

### 24. [U4 · Medium]

Consider the following method.

```java
public static int mystery(int n)
{
    if (n < 10)
        return n;
    return n % 10 + mystery(n / 10);
}
```

What value is returned by the call `mystery(1234)`?

(A) 1
(B) 4
(C) 1234
(D) 10

---

### 25. [U4 · Hard]

Consider the following method.

```java
public static String mystery(String s)
{
    if (s.length() <= 1)
        return s;
    return mystery(s.substring(1)) + s.substring(0, 1);
}
```

What value is returned by the call `mystery("ABCD")`?

(A) `"ABCD"`
(B) `"BCDA"`
(C) `"DABC"`
(D) `"DCBA"`

---

# Section II: Free Response (4 Questions | 120 Minutes)

**Directions:** SHOW ALL YOUR WORK. REMEMBER THAT PROGRAM SEGMENTS ARE TO BE WRITTEN IN JAVA.

Write your solutions in Java. You may assume all necessary imports. Assume that the code provided compiles and works correctly. You may write helper methods if you wish.

---

## Question 1: ScoreAnalyzer (5 Points)

This question involves analyzing and processing an array of test scores.

```java
public class ScoreAnalyzer
{
    /** Returns the average of the values in scores.
     *  Precondition: scores.length > 0
     *
     *  Example:
     *    scores = {85, 92, 78, 90, 88}
     *    getAverage(scores) → 86.6
     */
    public static double getAverage(int[] scores)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a String grade based on the given numeric score.
     *    90 and above → "A"
     *    80–89        → "B"
     *    70–79        → "C"
     *    60–69        → "D"
     *    below 60     → "F"
     *
     *  Example:
     *    getGrade(85) → "B"
     *    getGrade(92) → "A"
     *    getGrade(55) → "F"
     */
    public static String getGrade(int score)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns an array of String grades corresponding to each score
     *  in scores. The grade at index k of the returned array corresponds
     *  to the score at index k of scores.
     *
     *  Precondition: scores.length > 0
     *
     *  Example:
     *    scores = {85, 92, 78, 55}
     *    getGrades(scores) → {"B", "A", "C", "F"}
     */
    public static String[] getGrades(int[] scores)
    {
        /* to be implemented in Part (b) */
    }

    /** Returns the number of scores in scores that are strictly above
     *  the average of all scores.
     *
     *  Precondition: scores.length > 0
     *
     *  Example:
     *    scores = {85, 92, 78, 90, 88}
     *    average = 86.6
     *    countAboveAverage(scores) → 3   (92, 90, 88 are above 86.6)
     */
    public static int countAboveAverage(int[] scores)
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `getAverage` method and the `getGrade` method.

### Part (b)

Complete the `getGrades` method and the `countAboveAverage` method. You may call `getAverage` and `getGrade` regardless of whether you completed Part (a).

---

## Question 2: MusicPlaylist (7 Points)

A `Song` is represented by the following class.

```java
public class Song
{
    private String title;
    private String artist;
    private int duration; // in seconds

    /** Constructs a Song with the given title, artist, and duration. */
    public Song(String title, String artist, int duration)
    {
        this.title = title;
        this.artist = artist;
        this.duration = duration;
    }

    public String getTitle()    { return title; }
    public String getArtist()   { return artist; }
    public int getDuration()    { return duration; }
}
```

Write the complete `MusicPlaylist` class. Your implementation must include:

- A private `ArrayList<Song>` instance variable
- A no-argument constructor that initializes an empty playlist
- All methods described below

### Part (a)

Write the following methods for the `MusicPlaylist` class.

- `addSong(Song s)` — Adds the given song to the end of the playlist.
- `getTotalDuration()` — Returns the total duration (in seconds) of all songs in the playlist.
- `getSongByTitle(String title)` — Returns the first `Song` with the given title, or `null` if no such song exists.

**Example:**

| Playlist contents | Method call | Return value |
|---|---|---|
| [("Hello", "Adele", 295), ("Shape", "Ed", 234), ("Hello", "Lionel", 302)] | `getTotalDuration()` | `831` |
| [("Hello", "Adele", 295), ("Shape", "Ed", 234), ("Hello", "Lionel", 302)] | `getSongByTitle("Hello").getArtist()` | `"Adele"` |
| [("Hello", "Adele", 295), ("Shape", "Ed", 234)] | `getSongByTitle("Bye")` | `null` |

### Part (b)

Write the following methods for the `MusicPlaylist` class.

- `getSongsByArtist(String artist)` — Returns a new `ArrayList<Song>` containing all songs by the given artist, in the same order they appear in the playlist. Returns an empty list if no songs match.
- `removeLongSongs(int maxDuration)` — Removes all songs with duration strictly greater than `maxDuration` from the playlist. Returns the number of songs removed.

**Example:**

| Playlist contents (before) | Method call | Return | Playlist (after) |
|---|---|---|---|
| [("Hello","Adele",295), ("Shape","Ed",234), ("Sky","Adele",228)] | `getSongsByArtist("Adele")` | titles: ["Hello","Sky"] | unchanged |
| [("Hello","Adele",295), ("Shape","Ed",234), ("Sky","Adele",228)] | `removeLongSongs(250)` | `1` | [("Shape","Ed",234), ("Sky","Adele",228)] |

---

## Question 3: NumberList (6 Points)

This question involves operations on an `ArrayList` of integers.

```java
public class NumberList
{
    private ArrayList<Integer> nums;

    /** Constructs a NumberList from the given ArrayList.
     *  Precondition: nums has at least one element.
     */
    public NumberList(ArrayList<Integer> nums)
    {
        this.nums = nums;
    }

    /** Returns true if nums contains the value target, false otherwise.
     *
     *  Example:
     *    nums = [3, 7, 1, 9, 4]
     *    contains(7) → true
     *    contains(5) → false
     */
    public boolean contains(int target)
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a new ArrayList containing only the even numbers
     *  from nums, in the same order they appear in nums.
     *
     *  Example:
     *    nums = [3, 8, 1, 6, 5, 2]
     *    getEvens() → [8, 6, 2]
     */
    public ArrayList<Integer> getEvens()
    {
        /* to be implemented in Part (a) */
    }

    /** Removes all duplicate values from nums, keeping only the
     *  first occurrence of each value. The relative order of
     *  remaining elements is preserved.
     *
     *  Example:
     *    nums (before) = [3, 1, 4, 1, 5, 3, 2, 4]
     *    removeDuplicates()
     *    nums (after)  = [3, 1, 4, 5, 2]
     */
    public void removeDuplicates()
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `contains` method and the `getEvens` method.

### Part (b)

Complete the `removeDuplicates` method. You may call `contains` regardless of whether you completed Part (a).

---

## Question 4: ImageProcessor (6 Points)

This question involves operations on a two-dimensional array of integers representing pixel brightness values (0–255).

```java
public class ImageProcessor
{
    private int[][] pixels;

    /** Constructs an ImageProcessor with the given 2D pixel array.
     *  Precondition: pixels is rectangular and has at least one row and one column.
     *                All values are in the range 0–255.
     */
    public ImageProcessor(int[][] pixels)
    {
        this.pixels = pixels;
    }

    /** Returns a new 2D array that is the horizontal flip of pixels.
     *  Each row is reversed left-to-right.
     *  The original pixels array is not modified.
     *
     *  Example:
     *    {{10, 20, 30},        {{30, 20, 10},
     *     {40, 50, 60},   →     {60, 50, 40},
     *     {70, 80, 90}}         {90, 80, 70}}
     */
    public int[][] flipHorizontal()
    {
        /* to be implemented in Part (a) */
    }

    /** Returns a new 2D array where each pixel is replaced by the
     *  average of itself and its horizontal and vertical neighbors
     *  (up, down, left, right). For border/corner elements, only
     *  existing neighbors are included. Integer division is used.
     *  The original pixels array is not modified.
     *
     *  Example (3×3):
     *    {{100, 200, 100},
     *     {200,  50, 200},
     *     {100, 200, 100}}
     *
     *  For pixel (0,0) value 100:
     *    neighbors: right=200, below=200
     *    average = (100 + 200 + 200) / 3 = 166
     *
     *  For pixel (1,1) value 50:
     *    neighbors: above=200, below=200, left=200, right=200
     *    average = (50 + 200 + 200 + 200 + 200) / 5 = 170
     */
    public int[][] blur()
    {
        /* to be implemented in Part (b) */
    }
}
```

### Part (a)

Complete the `flipHorizontal` method.

### Part (b)

Complete the `blur` method.
