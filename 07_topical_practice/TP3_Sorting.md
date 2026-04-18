# TP3: Sorting — Selection, Insertion, Merge (보강 세트)

> **CED 2025-26 토픽**: 4.15 Sorting Algorithms (Selection, Insertion), 4.17.C Recursive Sorting (Merge)
> **문항 수**: 10 MCQ (Hard 위주)
> **시간 권장**: 25분
> **목표 정답률**: 80% 이상

---

## CED 범위 준수 사항

- **4.17.C.1 EXCLUSION**: *"Sorting algorithms other than selection, insertion, and merge sort are outside the scope of the AP Computer Science A course and exam."*
  - **Bubble sort, Quick sort, Heap sort 모두 OUT**
- **4.15.A.1**: Selection sort와 insertion sort는 **반복형(iterative)**
- **4.15.A.2**: Selection sort는 **smallest 또는 largest** 선택 가능 (오름차순/내림차순 모두 IN)
- **4.17.C.1**: Merge sort는 **재귀형(recursive)**
- **EXCLUSION**: `Math.min/max`, `break`/`continue`, `ArrayList.contains/indexOf` 모두 사용 금지

---

## 출제 토픽 분포

| # | 토픽 | 핵심 |
|---|------|------|
| 1 | 4.15 Selection — 부분 진행 상태 | k-pass 후 배열 |
| 2 | 4.15 Selection — 비교 횟수 | n(n-1)/2 |
| 3 | 4.15 Selection — swap 횟수 | self-swap 회피 |
| 4 | 4.15 Insertion — 부분 진행 상태 | k-pass 후 배열 |
| 5 | 4.15 Insertion — shift 횟수 | inner while 동작 |
| 6 | 4.15 Insertion — 정렬된 입력 | best case 동작 |
| 7 | 4.17.C Merge — 재귀 호출 횟수 | call count |
| 8 | 4.17.C Merge — merge 단계 결과 | 두 정렬 부분 결합 |
| 9 | 4.17.C Merge — 재귀 깊이 | log₂n 직관 |
| 10 | 4.15 + 4.17.C — 알고리즘 비교 | best case 시나리오 |

**답안 분포**: A:3 / B:2 / C:3 / D:2

---

## 시험 안내

**Directions**: 다음 각 문항에 대해 가장 적절한 답을 고르시오. 별도 명시가 없는 한 Java Quick Reference의 클래스가 import되어 있다고 가정한다.

---

### 1. [CED 4.15 · Hard]

다음은 **선택 정렬(Selection Sort)** 코드이다 (CED 4.15.A.2 명시).

```java
int[] arr = {5, 3, 8, 1, 9, 6};
for (int i = 0; i < arr.length - 1; i++)
{
    int minIdx = i;
    for (int j = i + 1; j < arr.length; j++)
    {
        if (arr[j] < arr[minIdx]) minIdx = j;
    }
    int temp = arr[i];
    arr[i] = arr[minIdx];
    arr[minIdx] = temp;
}
```

외부 루프가 정확히 **2번 반복** (i=0, i=1 완료) 후 `arr`의 상태는?

(A) `{1, 3, 5, 6, 8, 9}`
(B) `{1, 3, 5, 8, 9, 6}`
(C) `{3, 1, 8, 5, 9, 6}`
(D) `{1, 3, 8, 5, 9, 6}`

---

### 2. [CED 4.15 + 2.12 · Hard]

다음은 선택 정렬에서 **비교 횟수**를 세는 메서드이다 (CED 2.12 statement execution count + 4.15 selection sort).

```java
public static int countComparisons(int[] arr)
{
    int comp = 0;
    for (int i = 0; i < arr.length - 1; i++)
    {
        int minIdx = i;
        for (int j = i + 1; j < arr.length; j++)
        {
            comp++;
            if (arr[j] < arr[minIdx]) minIdx = j;
        }
        int t = arr[i]; arr[i] = arr[minIdx]; arr[minIdx] = t;
    }
    return comp;
}
```

`int[] arr = {4, 2, 7, 1, 5};` (length=5) 호출 시 `countComparisons(arr)`의 반환값은?

(A) `5`
(B) `10`
(C) `15`
(D) `25`

---

### 3. [CED 4.15 · Hard]

다음은 선택 정렬에서 **실제 swap 횟수**를 세는 메서드이다. 동일 위치 swap(`minIdx == i`)은 카운트하지 않는다.

```java
public static int countSwaps(int[] arr)
{
    int swaps = 0;
    for (int i = 0; i < arr.length - 1; i++)
    {
        int minIdx = i;
        for (int j = i + 1; j < arr.length; j++)
        {
            if (arr[j] < arr[minIdx]) minIdx = j;
        }
        if (minIdx != i)
        {
            int t = arr[i]; arr[i] = arr[minIdx]; arr[minIdx] = t;
            swaps++;
        }
    }
    return swaps;
}
```

`int[] arr = {3, 1, 4, 1, 5, 9};` 호출 시 `countSwaps(arr)`의 반환값은?

(A) `5`
(B) `2`
(C) `3`
(D) `0`

---

### 4. [CED 4.15 · Hard]

다음은 **삽입 정렬(Insertion Sort)** 코드이다 (CED 4.15.A.3 명시).

```java
int[] arr = {5, 2, 4, 6, 1, 3};
for (int i = 1; i < arr.length; i++)
{
    int key = arr[i];
    int j = i - 1;
    while (j >= 0 && arr[j] > key)
    {
        arr[j + 1] = arr[j];
        j--;
    }
    arr[j + 1] = key;
}
```

외부 루프가 정확히 **3번 반복** (i=1, 2, 3 완료) 후 `arr`의 상태는?

(A) `{2, 4, 5, 6, 1, 3}`
(B) `{1, 2, 3, 4, 5, 6}`
(C) `{2, 5, 4, 6, 1, 3}`
(D) `{2, 4, 5, 1, 6, 3}`

---

### 5. [CED 4.15 · Hard]

다음은 삽입 정렬에서 **shift(원소 이동) 횟수**를 세는 메서드이다.

```java
public static int countShifts(int[] arr)
{
    int shifts = 0;
    for (int i = 1; i < arr.length; i++)
    {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key)
        {
            arr[j + 1] = arr[j];
            shifts++;
            j--;
        }
        arr[j + 1] = key;
    }
    return shifts;
}
```

`int[] arr = {3, 1, 4, 1, 5};` 호출 시 `countShifts(arr)`의 반환값은?

(A) `1`
(B) `2`
(C) `3`
(D) `4`

---

### 6. [CED 4.15 · Hard]

Q5의 `countShifts` 메서드를 **이미 정렬된** 배열에 적용한다.

```java
int[] arr = {1, 2, 3, 4, 5};   // 이미 오름차순 정렬됨
int result = countShifts(arr);
System.out.println(result);
```

출력은?

(A) `0`
(B) `4`
(C) `5`
(D) `10`

---

### 7. [CED 4.17.C · Hard]

다음은 **병합 정렬(Merge Sort)** 의 재귀 구조이다 (CED 4.17.C.2: *"Merge sort repeatedly divides an array into smaller subarrays..."*).

```java
public static void mergeSort(int[] arr, int lo, int hi)
{
    if (lo >= hi) return;          // base case
    int mid = (lo + hi) / 2;
    mergeSort(arr, lo, mid);
    mergeSort(arr, mid + 1, hi);
    merge(arr, lo, mid, hi);       // 두 정렬된 절반을 합침
}
```

`int[] arr = new int[4];` (length=4) 에 대해 `mergeSort(arr, 0, 3)`을 호출하면 `mergeSort` 메서드는 **총 몇 번** 호출되는가? (초기 호출 포함, base case에서 return하는 호출도 포함)

(A) `3`
(B) `5`
(C) `7`
(D) `4`

---

### 8. [CED 4.17.C · Hard]

병합 정렬의 **merge 단계**(CED 4.17.C.2)는 두 개의 정렬된 부분 배열을 하나의 정렬된 배열로 결합한다. 두 부분 배열의 앞 원소를 비교해 작은 쪽을 결과에 추가하는 방식.

다음 두 정렬된 부분 배열을 merge하면 결과는?

```
left  = {1, 4, 7}
right = {2, 5, 8}
```

(A) `{1, 4, 7, 2, 5, 8}`
(B) `{1, 2, 4, 5, 7, 8}`
(C) `{2, 5, 8, 1, 4, 7}`
(D) `{1, 4, 2, 5, 7, 8}`

---

### 9. [CED 4.17.C + 2.12 · Hard]

Q7의 `mergeSort` 코드에서, `int[] arr = new int[8];` (length=8) 에 대해 `mergeSort(arr, 0, 7)`을 초기 호출했을 때 **재귀 호출의 최대 깊이**(가장 깊은 base case까지 쌓이는 stack frame의 개수, 초기 호출은 깊이 1)는?

(A) `4`
(B) `8`
(C) `3`
(D) `7`

---

### 10. [CED 4.15 + 4.17.C · Hard]

세 정렬 알고리즘의 **best case 시간 복잡도**(이미 정렬되어 있을 때 동작)를 비교하라. 어떤 알고리즘이 **이미 정렬된 입력에서 가장 효율적**인가?

(A) Selection sort — 항상 모든 원소 비교가 같으므로 가장 단순
(B) Merge sort — 항상 O(n log n)으로 일관됨
(C) 셋 다 동일 — 정렬 알고리즘은 입력에 무관하게 같은 비용
(D) Insertion sort — 이미 정렬된 입력에서는 inner while이 즉시 종료되어 O(n)

---

**END OF TP3**
