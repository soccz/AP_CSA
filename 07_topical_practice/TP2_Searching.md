# TP2: Searching — Linear + Binary (보강 세트)

> **CED 2025-26 토픽**: 4.14 Searching Algorithms (Linear), 4.17.B Recursive Searching and Sorting (Binary)
> **문항 수**: 8 MCQ (Hard 위주)
> **시간 권장**: 20분
> **목표 정답률**: 80% 이상

---

## CED 범위 준수 사항

- **4.14 EXCLUSION**: Linear/Binary 외 검색 OUT (Quick Reference 명시)
- **4.17.B.3**: Binary search는 **반복(iterative) 또는 재귀(recursive)** 모두 IN
- **4.17 EXCLUSION**: Selection/Insertion/Merge 외 정렬 OUT (정렬은 TP3에서 다룸)
- **EXCLUSION**: `Math.min/max`, `break`/`continue`, `ArrayList.contains/indexOf` 모두 사용 금지

---

## 출제 토픽 분포

| # | 토픽 | 핵심 |
|---|------|------|
| 1 | 4.14 — 1D Linear Search | 첫 일치 인덱스 반환 |
| 2 | 4.14 — ArrayList<String> Linear Search | `.equals()` 비교 |
| 3 | 4.14 — 2D Linear (행별 카운트) | 모든 일치 카운트 |
| 4 | 4.14 — Reverse Linear Search | "either end" (CED 4.14.A.1) |
| 5 | 4.17.B — Binary Search (반복형) | 정렬 배열 인덱스 반환 |
| 6 | 4.17.B — Binary Search 비교 횟수 | not-found 시 음수 반환 |
| 7 | 4.17.B — Binary Search 재귀형 | 재귀 트레이싱 |
| 8 | 4.17.B — 비정렬 배열 적용 | 선행조건 위반 시 결과 |

**답안 분포**: A:2 / B:2 / C:2 / D:2

---

## 시험 안내

**Directions**: 다음 각 문항에 대해 가장 적절한 답을 고르시오. 별도 명시가 없는 한 Java Quick Reference의 클래스가 import되어 있다고 가정한다.

---

### 1. [CED 4.14 · Hard]

다음은 **선형 검색(Linear Search)** 메서드이다.

```java
public static int linearSearch(int[] arr, int target)
{
    for (int i = 0; i < arr.length; i++)
    {
        if (arr[i] == target) return i;
    }
    return -1;
}
```

다음 호출의 결과는?

```java
int[] arr = {7, 3, 9, 4, 8, 2, 5};
int result = linearSearch(arr, 4);
System.out.println(result);
```

(A) `-1`
(B) `4`
(C) `3`
(D) `7`

---

### 2. [CED 4.14 · Hard]

다음은 `ArrayList<String>`에서 **String을 선형 검색**하는 메서드이다.

```java
public static int findString(ArrayList<String> list, String target)
{
    for (int i = 0; i < list.size(); i++)
    {
        if (list.get(i).equals(target)) return i;
    }
    return -1;
}
```

다음 호출의 결과는?

```java
ArrayList<String> list = new ArrayList<String>();
list.add("apple");
list.add("banana");
list.add("cherry");
list.add("date");
int idx = findString(list, "cherry");
System.out.println(idx);
```

(A) `2`
(B) `-1`
(C) `3`
(D) `1`

---

### 3. [CED 4.14 · Hard]

다음은 **2D 배열에서 target과 일치하는 모든 셀의 개수**를 카운트하는 메서드이다 (CED 4.14.A.2: *"applying linear search to 2D arrays, each row must be accessed then linear search applied"*).

```java
public static int countMatches(int[][] grid, int target)
{
    int count = 0;
    for (int r = 0; r < grid.length; r++)
    {
        for (int c = 0; c < grid[r].length; c++)
        {
            if (grid[r][c] == target) count++;
        }
    }
    return count;
}
```

다음 호출의 결과는?

```java
int[][] grid = {
    {3, 1, 4},
    {1, 5, 9},
    {2, 6, 5}
};
int result = countMatches(grid, 5);
System.out.println(result);
```

(A) `0`
(B) `2`
(C) `1`
(D) `3`

---

### 4. [CED 4.14 · Hard]

다음은 **역방향 선형 검색** 메서드이다 (CED 4.14.A.1: *"Linear search algorithms can begin the search process from either end of the array or ArrayList"*).

```java
public static int reverseLinear(int[] arr, int target)
{
    for (int i = arr.length - 1; i >= 0; i--)
    {
        if (arr[i] == target) return i;
    }
    return -1;
}
```

다음 호출의 결과는?

```java
int[] arr = {2, 5, 8, 5, 3, 5, 1};
int result = reverseLinear(arr, 5);
System.out.println(result);
```

(A) `1`
(B) `3`
(C) `-1`
(D) `5`

---

### 5. [CED 4.17.B · Hard]

다음은 **반복형 이진 검색(Iterative Binary Search)** 메서드이다.

```java
public static int binarySearch(int[] arr, int target)
{
    int lo = 0;
    int hi = arr.length - 1;
    while (lo <= hi)
    {
        int mid = (lo + hi) / 2;
        if (arr[mid] == target) return mid;
        if (arr[mid] < target) lo = mid + 1;
        else hi = mid - 1;
    }
    return -1;
}
```

다음 호출의 결과는? (배열은 **정렬되어 있음**)

```java
int[] arr = {1, 3, 5, 7, 9, 11, 13};
int result = binarySearch(arr, 11);
System.out.println(result);
```

(A) `5`
(B) `4`
(C) `11`
(D) `-1`

---

### 6. [CED 4.17.B · Hard]

다음은 이진 검색에 **비교 횟수**를 함께 반환하는 메서드이다. 발견 시 양수 횟수, 미발견 시 **음수 횟수**를 반환한다.

```java
public static int countSteps(int[] arr, int target)
{
    int lo = 0;
    int hi = arr.length - 1;
    int steps = 0;
    while (lo <= hi)
    {
        int mid = (lo + hi) / 2;
        steps++;
        if (arr[mid] == target) return steps;
        if (arr[mid] < target) lo = mid + 1;
        else hi = mid - 1;
    }
    return -steps;
}
```

다음 호출의 결과는?

```java
int[] arr = {1, 3, 5, 7, 9, 11, 13};
int result = countSteps(arr, 6);
System.out.println(result);
```

(A) `-1`
(B) `3`
(C) `-3`
(D) `0`

---

### 7. [CED 4.17.B · Hard]

다음은 **재귀형 이진 검색**(CED 4.17.B.3: *"The binary search algorithm can be written either iteratively or recursively"*)이다.

```java
public static int bSearch(int[] arr, int target, int lo, int hi)
{
    if (lo > hi) return -1;
    int mid = (lo + hi) / 2;
    if (arr[mid] == target) return mid;
    if (arr[mid] < target) return bSearch(arr, target, mid + 1, hi);
    return bSearch(arr, target, lo, mid - 1);
}
```

다음 호출의 결과는? (배열은 **정렬되어 있음**)

```java
int[] arr = {2, 4, 6, 8, 10, 12, 14, 16, 18, 20};
int result = bSearch(arr, 14, 0, 9);
System.out.println(result);
```

(A) `14`
(B) `6`
(C) `-1`
(D) `7`

---

### 8. [CED 4.17.B · Hard]

이진 검색의 **선행조건**(CED 4.17.B.1: *"Data must be in sorted order to use the binary search algorithm"*)을 위반한 사례.

```java
public static int binarySearch(int[] arr, int target)
{
    int lo = 0;
    int hi = arr.length - 1;
    while (lo <= hi)
    {
        int mid = (lo + hi) / 2;
        if (arr[mid] == target) return mid;
        if (arr[mid] < target) lo = mid + 1;
        else hi = mid - 1;
    }
    return -1;
}
```

다음 호출의 결과는? (배열이 **정렬되어 있지 않음에 주의**)

```java
int[] arr = {5, 3, 8, 1, 9, 6, 2};   // NOT sorted
int result = binarySearch(arr, 9);   // 9는 인덱스 4에 존재
System.out.println(result);
```

(A) `4`
(B) `9`
(C) `Compile error`
(D) `-1`

---

**END OF TP2**
