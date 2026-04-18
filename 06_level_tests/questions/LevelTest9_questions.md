# AP Computer Science A — Level Test 9

> **CED 2025-26 (4-Unit) 기준**
> U1 Using Objects and Methods · U2 Selection and Iteration · U3 Class Creation · U4 Data Collections

> **Purpose:** Diagnostic exam targeting AP CSA score of 5
> **Time:** Section I (50 min) + Section II (120 min) = 170 min total
> **Scoring:** MCQ 25 × 1 pt = 25 pts / FRQ 5 + 7 + 6 + 6 = 24 pts / **Total: 49 pts**

---

# Section I: Multiple Choice (25 Questions | 50 Minutes)

**Unit Distribution:** U1(5) · U2(5) · U3(4) · U4(11)
**Difficulty:** Easy 5 · Medium 12 · Hard 8

---

### 1. [U1 · Easy]
```java
int x = 37, y = 10;
System.out.println(x / y + "." + x % y);
```
(A) `"3.7"`  (B) `"3.70"`  (C) `"3.10"`  (D) `"37"`

---

### 2. [U1 · Medium]
```java
int a = 5;
double b = a + 0.5;
int c = (int)(b * 2);
System.out.println(c);
```
(A) 10  (B) 11  (C) 10.0  (D) 12

---

### 3. [U1 · Medium]
```java
String s = "ABCDEFG";
String result = s.substring(2, 5) + s.substring(0, 2);
System.out.println(result);
```
(A) `"CDEAB"`  (B) `"ABCDE"`  (C) `"CDFAB"`  (D) `"CDAB"`

---

### 4. [U1 · Medium]
```java
String s = "hello";
String r = "";
for (int i = 0; i < s.length(); i++)
{
    r = s.substring(i, i + 1) + r;
}
System.out.println(r);
```
(A) `"hello"`  (B) `"oellh"`  (C) `"loleh"`  (D) `"olleh"`

---

### 5. [U2 · Easy]
```java
int n = 15;
if (n % 3 == 0 && n % 5 == 0)
    System.out.print("FizzBuzz");
else if (n % 3 == 0)
    System.out.print("Fizz");
else if (n % 5 == 0)
    System.out.print("Buzz");
else
    System.out.print(n);
```
(A) `"Fizz"`  (B) `"Buzz"`  (C) `"FizzBuzz"`  (D) `"15"`

---

### 6. [U2 · Medium]
```java
int a = 10, b = 20, c = 15;
boolean x = a < b;
boolean y = b > c;
boolean z = a + c > b;
System.out.println(!x || (y && z));
```
(A) `true`  (B) `false`  (C) A compile-time error occurs.  (D) A runtime error occurs.

---

### 7. [U2 · Medium]
```java
String s = "";
for (int r = 1; r <= 3; r++)
{
    for (int c = 1; c <= r; c++)
    {
        s += "*";
    }
    s += "\n";
}
System.out.print(s);
```
What pattern is printed?
(A)
```
***
***
***
```
(B)
```
***
**
*
```
(C)
```
*
**
***
```
(D) A compile-time error occurs.

---

### 8. [U2 · Hard]
```java
int x = 100;
int steps = 0;
while (x != 1)
{
    if (x % 2 == 0)
        x /= 2;
    else
        x = 3 * x + 1;
    steps++;
}
System.out.println(steps);
```

What is printed? (Collatz sequence for 100)

(A) 7  (B) 10  (C) 25  (D) 88

---

### 9. [U3 · Easy]
```java
public class Pet
{
    private String name;
    private String sound;
    public Pet(String n, String s) { name = n; sound = s; }
    public String speak() { return name + " says " + sound; }
}
```
```java
Pet p = new Pet("Rex", "Woof");
System.out.println(p.speak());
```
(A) `"Pet says Woof"`  (B) `"Rex Woof"`  (C) `"Rex says Woof"`  (D) Compile error

---

### 10. [U3 · Medium]
```java
public class Inventory
{
    private ArrayList<String> items;
    public Inventory() { items = new ArrayList<String>(); }
    public void add(String item) { items.add(item); }
    public String getAt(int idx) { return items.get(idx); }
    public int count() { return items.size(); }
    public String removeAt(int idx) { return items.remove(idx); }
    public String replace(int idx, String item) { return items.set(idx, item); }
}
```
```java
Inventory inv = new Inventory();
inv.add("sword"); inv.add("shield"); inv.add("potion");
String old = inv.replace(1, "bow");
String removed = inv.removeAt(0);
System.out.println(old + " " + removed + " " + inv.getAt(0));
```
(A) `"bow sword shield"`  (B) `"shield bow sword"`  (C) `"shield sword bow"`  (D) `"shield potion sword"`

---

### 11. [U3 · Hard]
```java
public class Matrix2x2
{
    private int a, b, c, d; // [[a,b],[c,d]]
    public Matrix2x2(int a, int b, int c, int d) { this.a=a; this.b=b; this.c=c; this.d=d; }
    public int determinant() { return a * d - b * c; }
    public Matrix2x2 multiply(Matrix2x2 other)
    {
        return new Matrix2x2(
            a*other.a + b*other.c, a*other.b + b*other.d,
            c*other.a + d*other.c, c*other.b + d*other.d);
    }
}
```
```java
Matrix2x2 m = new Matrix2x2(1, 2, 3, 4);
Matrix2x2 r = m.multiply(m);
System.out.println(r.determinant());
```
(A) -4  (B) -2  (C) 0  (D) 4

---

### 12. [U4 · Easy]
```java
int[] arr = {5, 10, 15};
arr[1] = arr[0] + arr[2];
System.out.println(arr[1]);
```
(A) 10  (B) 20  (C) 15  (D) 25

---

### 13. [U4 · Medium]
```java
int[] a = {1, 2, 3};
int[] b = a;
b[0] = 99;
System.out.println(a[0]);
```
(A) 0  (B) 1  (C) Compile error  (D) 99

---

### 14. [U4 · Hard]
```java
int[] arr = {3, 7, 2, 7, 5, 6};
int max = arr[0];
int second = -1;
for (int i = 1; i < arr.length; i++) {
    if (arr[i] > max) {
        second = max;
        max = arr[i];
    } else if (arr[i] < max && arr[i] > second) {
        second = arr[i];
    }
}
System.out.println(max + " " + second);
```
(A) `"7 5"`  (B) `"7 6"`  (C) `"7 7"`  (D) `"6 7"`

---

### 15. [U4 · Easy]
```java
ArrayList<Integer> nums = new ArrayList<Integer>();
nums.add(3); nums.add(8); nums.add(5); nums.add(2); nums.add(9);
int count = 0;
for (int n : nums)
{
    if (n > 4) count++;
}
System.out.println(count);
```
(A) 5  (B) 2  (C) 3  (D) 0

---

### 16. [U4 · Medium]
```java
ArrayList<String> list = new ArrayList<String>();
list.add("a"); list.add("b"); list.add("c"); list.add("d"); list.add("e");
ArrayList<String> sub = new ArrayList<String>();
for (int i = list.size() - 1; i >= 0; i -= 2)
    sub.add(list.get(i));
System.out.println(sub);
```
(A) `[e, c, a]`  (B) `[a, c, e]`  (C) `[e, d, c]`  (D) `[d, b]`

---

### 17. [U4 · Hard]
```java
ArrayList<Integer> list = new ArrayList<Integer>();
for (int i = 0; i < 6; i++) list.add(i);
// list = [0, 1, 2, 3, 4, 5]
for (int i = 0; i < 3; i++)
{
    int val = list.remove(0);
    list.add(val);
}
System.out.println(list);
```
(A) `[0, 1, 2, 3, 4, 5]`  (B) `[2, 1, 0, 3, 4, 5]`  (C) `[3, 4, 5, 0, 1, 2]`  (D) `[5, 4, 3, 0, 1, 2]`

---

### 18. [U4 · Medium]
```java
String[][] grid = {{"X", "O", "X"},
                   {"O", "X", "O"},
                   {"X", "O", "X"}};
int count = 0;
for (int r = 0; r < grid.length; r++)
    for (int c = 0; c < grid[0].length; c++)
        if (grid[r][c].equals("X")) count++;
System.out.println(count);
```
(A) 4  (B) 5  (C) 3  (D) 9

---

### 19. [U4 · Hard]
```java
int[][] m = {{1, 0}, {0, 1}};
int[][] n = {{3, 4}, {5, 6}};
int[][] result = new int[2][2];
for (int r = 0; r < 2; r++)
    for (int c = 0; c < 2; c++)
        for (int k = 0; k < 2; k++)
            result[r][c] += m[r][k] * n[k][c];
System.out.println(result[0][0] + " " + result[1][1]);
```
(A) `"3 6"`  (B) `"1 1"`  (C) `"4 5"`  (D) `"0 0"`

---

### 20. [U1 · Medium]
```java
String a = "banana";
String b = "apple";
String c = "cherry";
int x = a.compareTo(b);
int y = b.compareTo(c);
System.out.println((x > 0) + " " + (y < 0));
```
(A) `"true true"`  (B) `"true false"`  (C) `"false true"`  (D) `"false false"`

---

### 21. [U2 · Medium]
```java
int[][] grid = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
int target = 5;
int row = -1, col = -1;
for (int r = 0; r < grid.length; r++)
{
    for (int c = 0; c < grid[r].length; c++)
    {
        if (grid[r][c] == target)
        {
            row = r;
            col = c;
        }
    }
}
System.out.println(row + " " + col);
```
(A) `"0 0"`  (B) `"1 1"`  (C) `"1 4"`  (D) `"-1 -1"`

---

### 22. [U3 · Hard]
```java
public class Point
{
    private int[] coords;
    public Point(int x, int y) { coords = new int[]{x, y}; }
    public Point(Point other) { coords = other.coords; }
    public int getX() { return coords[0]; }
    public void setX(int x) { coords[0] = x; }
}
```
```java
Point p1 = new Point(3, 4);
Point p2 = new Point(p1);
p2.setX(99);
System.out.println(p1.getX() + " " + p2.getX());
```
(A) `"3 4"`  (B) `"3 99"`  (C) `"99 4"`  (D) `"99 99"`

---

### 23. [U4 · Hard]
```java
int[][] mat = {
    {1, 5, 2, 8, 3},
    {4, 6, 4, 7, 1},
    {3, 2, 9, 1, 5}
};
int count = 0;
for (int r = 0; r < mat.length; r++) {
    for (int c = 1; c < mat[r].length - 1; c++) {
        if (mat[r][c] > mat[r][c-1] && mat[r][c] > mat[r][c+1]) {
            count++;
        }
    }
}
System.out.println(count);
```
(A) 4  (B) 5  (C) 6  (D) 7

---

### 24. [U4 · Medium]
```java
public static boolean isEven(int n)
{
    if (n == 0) return true;
    if (n == 1) return false;
    return isEven(n - 2);
}
```
What is returned by `isEven(7)`?
(A) `true`  (B) Stack overflow  (C) Compile error  (D) `false`

---

### 25. [U4 · Hard]
```java
public static int flatten(int[][] grid)
{
    return flattenHelper(grid, 0, 0);
}
private static int flattenHelper(int[][] g, int r, int c)
{
    if (r >= g.length) return 0;
    if (c >= g[0].length) return flattenHelper(g, r + 1, 0);
    return g[r][c] + flattenHelper(g, r, c + 1);
}
```
```java
int[][] grid = {{1, 2}, {3, 4}};
System.out.println(flatten(grid));
```
(A) 3  (B) 4  (C) 7  (D) 10

---

# Section II: Free Response (4 Questions | 120 Minutes)

## Question 1: RomanNumeral (5 Points)
```java
public class RomanNumeral
{
    /** Returns the integer value of a single Roman digit: I=1,V=5,X=10,L=50,C=100,D=500,M=1000 */
    public static int romanDigitValue(String digit) { /* Part (a) */ }
    /** Returns the integer value of a Roman numeral string.
     *  If a smaller value precedes a larger, subtract it (e.g. IV=4) */
    public static int romanToInt(String roman) { /* Part (b) */ }
}
```

## Question 2: Restaurant (7 Points)

A restaurant manages its menu using a list of `MenuItem` objects. Each `MenuItem` has a name, a price, and a category (e.g., `"appetizer"`, `"main"`, `"dessert"`). The `MenuItem` class is **partial declaration** — only the parts you may use are shown.

```java
public class MenuItem
{
    private String name;
    private double price;
    private String category;

    public MenuItem(String n, double p, String c)
    {
        name = n; price = p; category = c;
    }

    public String getName()     { return name; }
    public double getPrice()    { return price; }
    public String getCategory() { return category; }

    // ... other methods not shown ...
}
```

Write the **complete** `Restaurant` class. The class must support the following:

1. A `private` field storing an `ArrayList<MenuItem>` named `items` — the menu items currently offered.
2. A no-argument constructor that initializes `items` to an empty list.
3. A method `void addItem(MenuItem m)` that appends `m` to `items`.
4. A method `double totalPriceInCategory(String category)` that returns the **sum of prices** of all items in `items` whose `getCategory()` equals the given `category` parameter. If no items match, return `0.0`.

Write the full class including the field, constructor, and the two methods.

**Example:**

```java
Restaurant r = new Restaurant();
r.addItem(new MenuItem("Soup", 6.00, "appetizer"));
r.addItem(new MenuItem("Steak", 25.00, "main"));
r.addItem(new MenuItem("Salad", 8.50, "appetizer"));
r.addItem(new MenuItem("Cake", 7.00, "dessert"));
```

- `r.totalPriceInCategory("appetizer")` returns `14.50` (Soup + Salad)
- `r.totalPriceInCategory("dessert")` returns `7.00` (Cake)
- `r.totalPriceInCategory("drink")` returns `0.0` (no matches)

## Question 3: Playlist (6 Points)

A music app tracks songs using a `Song` class. Each `Song` has a title, a duration in seconds, and a "liked" flag. The `Song` class is **partial declaration** — only the parts you may use are shown.

```java
public class Song
{
    private String title;
    private int durationSeconds;
    private boolean liked;

    public Song(String t, int d, boolean l)
    {
        title = t; durationSeconds = d; liked = l;
    }

    public String getTitle()        { return title; }
    public int getDurationSeconds() { return durationSeconds; }
    public boolean isLiked()        { return liked; }

    // ... other methods not shown ...
}
```

The `Playlist` class stores songs in an `ArrayList<Song>` and supports basic analytics.

```java
public class Playlist
{
    /** The songs in this playlist. Not null. May be empty. */
    private ArrayList<Song> songs;

    public Playlist(ArrayList<Song> s) { songs = s; }

    /** Returns the total duration (in seconds) of all liked songs.
     *  Returns 0 if no songs are liked. */
    public int totalLikedDuration()
    {
        /* Part (a) */
    }

    /** Returns the average duration (as a double) of songs whose duration
     *  is between minSeconds and maxSeconds (inclusive on both ends).
     *  Precondition: at least one song meets the criteria. */
    public double averageDurationInRange(int minSeconds, int maxSeconds)
    {
        /* Part (b) */
    }

    // ... other methods not shown ...
}
```

### Part (a) [3 points]

Write the `totalLikedDuration` method. Iterate through `songs` and return the **sum of `getDurationSeconds()`** values for songs that are liked (`isLiked()` returns `true`). If no songs are liked (or the playlist is empty), return `0`.

**Example:** Suppose `songs` contains the following:

| index | title       | duration | liked |
|-------|-------------|----------|-------|
| 0     | "Sunrise"   | 180      | true  |
| 1     | "Dawn"      | 240      | false |
| 2     | "Twilight"  | 200      | true  |
| 3     | "Midnight"  | 300      | true  |
| 4     | "Eclipse"   | 150      | false |

- `totalLikedDuration()` returns `680` (Sunrise 180 + Twilight 200 + Midnight 300 = 680).

Complete method `totalLikedDuration`:

```java
public int totalLikedDuration()
{

}
```

### Part (b) [3 points]

Write the `averageDurationInRange` method. Return, as a `double`, the **average** of `getDurationSeconds()` values for songs whose duration is in the inclusive range `[minSeconds, maxSeconds]`. You may assume the precondition holds (at least one song qualifies), so divide-by-zero need not be handled.

**Example (using the table above):**

- `averageDurationInRange(160, 220)` returns the average of `{180, 200}` (Sunrise and Twilight; Eclipse 150 is below range; others are above), i.e., `190.0`.
- `averageDurationInRange(0, 1000)` returns `(180+240+200+300+150) / 5.0 = 214.0`.

Complete method `averageDurationInRange`:

```java
public double averageDurationInRange(int minSeconds, int maxSeconds)
{

}
```

## Question 4: ConnectFour (6 Points)
```java
public class ConnectFour
{
    private int[][] board; // 0=empty, 1=player1, 2=player2. board[0] is top row.
    public ConnectFour(int rows, int cols) { board = new int[rows][cols]; }
    /** Drops piece into column c for player. Piece falls to lowest empty row.
     *  Returns row placed, or -1 if full. */
    public int dropPiece(int c, int player) { /* Part (a) */ }
    /** Returns true if player has 4 in a row horizontally in any row */
    public boolean checkHorizontalWin(int player) { /* Part (b) */ }
}
```
