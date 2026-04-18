# AP Computer Science A — Level Test 5

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

### 1. [U1 · Medium]

```java
int a = 19;
int b = 6;
System.out.println(a / b * b + a % b);
```

What is printed?

(A) 19
(B) 18
(C) 20
(D) 17

---

### 2. [U1 · Easy]

```java
double x = 3;
double y = 2;
System.out.println(x / y);
```

What is printed?

(A) 1
(B) 1.0
(C) 1.5
(D) 2.0

---

### 3. [U1 · Medium]

```java
String s = "hamburger";
System.out.println(s.substring(3, 8));
```

What is printed?

(A) `"burge"`
(B) `"burger"`
(C) `"burg"`
(D) `"mburge"`

---

### 4. [U1 · Medium]

```java
String s = "ABCBA";
boolean result = s.substring(0, 2).equals(s.substring(3));
System.out.println(result);
```

What is printed?

(A) `true`
(B) A compile-time error occurs.
(C) A runtime error occurs.
(D) `false`

---

### 5. [U2 · Easy]

```java
int n = 42;
if (n % 2 == 0)
    System.out.print("even ");
if (n > 40)
    System.out.print("big ");
if (n < 50)
    System.out.print("small");
```

What is printed?

(A) `"even "`
(B) `"even big "`
(C) `"even big small"`
(D) `"big small"`

---

### 6. [U2 · Medium]

Which of the following Boolean expressions is equivalent to `!(p || q)`?

(A) `!p || !q`
(B) `!p && !q`
(C) `p && q`
(D) `!p || q`

---

### 7. [U2 · Medium]

```java
String result = "";
for (int i = 5; i >= 1; i--)
{
    result += i;
}
System.out.println(result);
```

What is printed?

(A) `"12345"`
(B) `"54321"`
(C) `"5"`
(D) `"15"`

---

### 8. [U2 · Hard]

```java
int sum = 0;
for (int i = 1; i <= 100; i++)
{
    if (i % 3 == 0 && i % 5 == 0)
        sum += i;
}
System.out.println(sum);
```

What is printed?

(A) 315
(B) 735
(C) 2418
(D) 225

---

### 9. [U3 · Medium]

```java
public class Fraction
{
    private int num;
    private int den;

    public Fraction(int n, int d) { num = n; den = d; }
    public double getValue() { return (double) num / den; }

    public Fraction add(Fraction other)
    {
        int newNum = this.num * other.den + other.num * this.den;
        int newDen = this.den * other.den;
        return new Fraction(newNum, newDen);
    }
}
```

```java
Fraction f1 = new Fraction(1, 2);
Fraction f2 = new Fraction(1, 3);
Fraction f3 = f1.add(f2);
System.out.println(f3.getValue());
```

What is printed?

(A) `0.3333333333333333`
(B) `0.5`
(C) `1.0`
(D) `0.8333333333333334`

---

### 10. [U3 · Easy]

```java
public class Light
{
    private boolean on;

    public Light() { on = false; }

    public void toggle() { on = !on; }
    public boolean isOn() { return on; }
}
```

```java
Light lamp = new Light();
lamp.toggle();
lamp.toggle();
lamp.toggle();
System.out.println(lamp.isOn());
```

What is printed?

(A) `true`
(B) `false`
(C) A compile-time error occurs.
(D) A runtime error occurs.

---

### 11. [U3 · Hard]

```java
public class StringSet
{
    private ArrayList<String> items;

    public StringSet() { items = new ArrayList<String>(); }

    public boolean add(String s)
    {
        for (int i = 0; i < items.size(); i++)
        {
            if (items.get(i).equals(s)) return false;
        }
        items.add(s);
        return true;
    }

    public int size() { return items.size(); }
}
```

```java
StringSet set = new StringSet();
System.out.println(set.add("a"));
System.out.println(set.add("b"));
System.out.println(set.add("a"));
System.out.println(set.size());
```

What is printed?

(A)
```
true
true
true
3
```

(B)
```
true
true
false
2
```

(C)
```
false
false
false
0
```

(D)
```
true
true
false
3
```

---

### 12. [U4 · Medium]

```java
int[] arr = {1, 2, 3, 4, 5};
for (int i = 1; i < arr.length; i++)
{
    arr[i] += arr[i - 1];
}
System.out.println(arr[4]);
```

What is printed?

(A) 5
(B) 10
(C) 15
(D) 9

---

### 13. [U4 · Easy]

```java
int[] arr = {10, 20, 30, 40, 50};
System.out.println(arr[arr.length - 1] - arr[0]);
```

What is printed?

(A) 0
(B) 10
(C) 50
(D) 40

---

### 14. [U4 · Hard]

```java
int[][] mat = {{3, 7, 7, 2},
               {5, 8, 4, 8},
               {2, 6, 6, 6}};
int totalMaxPositions = 0;
for (int r = 0; r < mat.length; r++)
{
    int rowMax = mat[r][0];
    for (int c = 1; c < mat[r].length; c++)
    {
        if (mat[r][c] > rowMax) rowMax = mat[r][c];
    }
    for (int c = 0; c < mat[r].length; c++)
    {
        if (mat[r][c] == rowMax) totalMaxPositions++;
    }
}
System.out.println(totalMaxPositions);
```

What is printed?

(A) 3
(B) 5
(C) 7
(D) 12

---

### 15. [U4 · Easy]

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(15);
list.add(10);
list.add(25);
list.add(30);
int count = 0;
for (int v : list)
{
    if (v > 20) count++;
}
System.out.println(count);
```

What is printed?

(A) 1
(B) 2
(C) 3
(D) 4

---

### 16. [U4 · Medium]

```java
ArrayList<String> words = new ArrayList<String>();
words.add("dog");
words.add("ant");
words.add("bee");
words.add("cat");

String result = words.get(0);
for (int i = 1; i < words.size(); i++)
{
    if (words.get(i).compareTo(result) < 0)
    {
        result = words.get(i);
    }
}
System.out.println(result);
```

What is printed?

(A) `"dog"`
(B) `"ant"`
(C) `"bee"`
(D) `"cat"`

---

### 17. [U4 · Hard]

```java
ArrayList<Integer> a = new ArrayList<Integer>();
a.add(1); a.add(2); a.add(3);
ArrayList<Integer> b = a;
b.add(4);
a.remove(0);
System.out.println(a.size() + " " + b.size());
```

What is printed?

(A) `"3 4"`
(B) `"2 4"`
(C) `"3 3"`
(D) `"2 3"`

---

### 18. [U4 · Medium]

```java
int[][] grid = new int[3][4];
int val = 1;
for (int r = 0; r < 3; r++)
{
    for (int c = 0; c < 4; c++)
    {
        grid[r][c] = val;
        val++;
    }
}
System.out.println(grid[1][2]);
```

What is printed?

(A) 6
(B) 7
(C) 8
(D) 5

---

### 19. [U4 · Hard]

```java
int[][] mat = {{1, 0, 0},
               {0, 1, 0},
               {0, 0, 1}};
int[][] result = new int[3][3];
for (int r = 0; r < 3; r++)
{
    for (int c = 0; c < 3; c++)
    {
        for (int k = 0; k < 3; k++)
        {
            result[r][c] += mat[r][k] * mat[k][c];
        }
    }
}
System.out.println(result[0][0] + " " + result[1][1] + " " + result[2][2]);
```

What is printed?

(A) `"0 0 0"`
(B) `"2 2 2"`
(C) `"3 3 3"`
(D) `"1 1 1"`

---

### 20. [U1 · Medium]

Consider the following code segment.

```java
String s = "ABCDE";
System.out.println(s.substring(s.length() - 2) + s.indexOf("F"));
```

What is printed as a result of executing this code segment?

(A) `"DE-1"`
(B) `"DE0"`
(C) A runtime error occurs.
(D) `"ABC-1"`

---

### 21. [U2 · Medium]

Consider the following code segment.

```java
int a = 17;
int b = 5;
int count = 0;
while (a >= b)
{
    a -= b;
    count++;
}
System.out.println(count + " " + a);
```

What is printed as a result of executing this code segment?

(A) `"3 2"`
(B) `"4 -3"`
(C) `"2 7"`
(D) `"3 17"`

---

### 22. [U3 · Hard]

Consider the following class.

```java
public class Roster
{
    private ArrayList<String> names;

    public Roster()
    {
        names = new ArrayList<String>();
        names.add("Alice");
        names.add("Bob");
    }

    public ArrayList<String> getNames() { return names; }
    public int size() { return names.size(); }
}
```

The following code segment appears in a method in another class.

```java
Roster r = new Roster();
ArrayList<String> ref = r.getNames();
ref.add("Charlie");
ref.add("Dave");
System.out.println(r.size());
```

What is printed as a result of executing this code segment?

(A) 2
(B) 3
(C) 4
(D) A compile-time error occurs.

---

### 23. [U4 · Hard]

Consider the following code segment.

```java
int[][] mat = {{1, 2, 3, 4},
               {5, 5, 6, 7},
               {2, 4, 6, 8}};
int count = 0;
for (int r = 0; r < mat.length; r++)
{
    boolean isSorted = true;
    for (int c = 0; c < mat[0].length - 1; c++)
    {
        if (mat[r][c] >= mat[r][c + 1])
        {
            isSorted = false;
        }
    }
    if (isSorted)
    {
        count++;
    }
}
System.out.println(count);
```

What is printed as a result of executing this code segment?

(A) 0
(B) 1
(C) 2
(D) 3

---

### 24. [U4 · Medium]

```java
public static int gcd(int a, int b)
{
    if (b == 0)
        return a;
    return gcd(b, a % b);
}
```

What value is returned by `gcd(48, 18)`?

(A) 2
(B) 3
(C) 6
(D) 18

---

### 25. [U4 · Hard]

```java
public static boolean isPalindrome(String s)
{
    if (s.length() <= 1)
        return true;
    if (!s.substring(0, 1).equals(s.substring(s.length() - 1)))
        return false;
    return isPalindrome(s.substring(1, s.length() - 1));
}
```

For which of the following calls does the method make exactly 3 total calls (including the initial call)?

(A) `isPalindrome("abc")`
(B) `isPalindrome("aba")`
(C) `isPalindrome("abcdef")`
(D) `isPalindrome("abcba")`

---

# Section II: Free Response (4 Questions | 120 Minutes)

**Directions:** SHOW ALL YOUR WORK. REMEMBER THAT PROGRAM SEGMENTS ARE TO BE WRITTEN IN JAVA.

---

## Question 1: TextStats (5 Points)

```java
public class TextStats
{
    /** Returns the number of words in text.
     *  Words are separated by single spaces. No leading/trailing spaces.
     *  Precondition: text has at least one word
     *
     *  Examples:
     *    wordCount("hello world")   → 2
     *    wordCount("one")           → 1
     *    wordCount("a b c d")       → 4
     */
    public static int wordCount(String text)
    { /* to be implemented in Part (a) */ }

    /** Returns the longest word in text.
     *  If tied, return the first.
     *  Precondition: text has at least one word, words separated by spaces
     */
    public static String longestWord(String text)
    { /* to be implemented in Part (b) */ }
}
```

### Part (a)
Complete `wordCount`.

### Part (b)
Complete `longestWord`. You may use `wordCount` if helpful.

---

## Question 2: ParkingLot (7 Points)

```java
public class Car
{
    private String plate;
    private int hours;

    public Car(String plate, int hours) { this.plate = plate; this.hours = hours; }
    public String getPlate() { return plate; }
    public int getHours() { return hours; }
}
```

Write the complete `ParkingLot` class with:
- `private ArrayList<Car>` + no-arg constructor
- Part (a): `addCar(Car c)`, `findCar(String plate)` (returns Car or null), `getTotalRevenue(int ratePerHour)` (sum of hours × rate)
- Part (b): `getCarsOverLimit(int maxHours)` (ArrayList of cars exceeding maxHours), `removeCarByPlate(String plate)` (removes and returns true, or false)

---

## Question 3: GradeBook (6 Points)

```java
public class GradeBook
{
    private int[] grades;
    public GradeBook(int[] grades) { this.grades = grades; }

    /** Returns count of grades in range [low, high] inclusive */
    public int countInRange(int low, int high)
    { /* Part (a) */ }

    /** Returns a new array with grades curved: each grade += curve,
     *  but capped at 100 */
    public int[] applyCurve(int curve)
    { /* Part (a) */ }

    /** Returns the median grade. If even length, returns average of
     *  two middle values (int division). Assumes grades is sorted. */
    public int getMedian()
    { /* Part (b) */ }
}
```

### Part (a): Complete `countInRange` and `applyCurve`.
### Part (b): Complete `getMedian`.

---

## Question 4: TreasureMap (6 Points)

```java
public class TreasureMap
{
    private boolean[][] map;  // true = treasure

    public TreasureMap(boolean[][] map) { this.map = map; }

    /** Returns total number of treasures */
    public int countTreasures()
    { /* Part (a) */ }

    /** Returns a 1D array where element i is the count of treasures in row i */
    public int[] treasuresPerRow()
    { /* Part (a) */ }

    /** Returns true if any row has more treasures than any other row.
     *  Returns false if all rows have the same count. */
    public boolean hasUnevenDistribution()
    { /* Part (b) */ }
}
```

### Part (a): Complete `countTreasures` and `treasuresPerRow`.
### Part (b): Complete `hasUnevenDistribution`. May call `treasuresPerRow`.
