# TP4: Recursion 심화 (보강 세트)

> **CED 2025-26 토픽**: 4.16 Recursion, 4.17.A Recursive Traversal of String/Array/ArrayList
> **문항 수**: 8 MCQ (Hard 위주)
> **시간 권장**: 25분
> **목표 정답률**: 80% 이상

---

## CED 범위 준수 사항

- **4.16 EXCLUSION**: *"Writing recursive code is outside the scope of the AP Computer Science A course and exam."*
  - **트레이싱(추적)만 출제 가능, 작성 요구 불가**
- **4.16.A.1**: 재귀 메서드는 최소 1개의 base case + 1개의 recursive call
- **4.16.A.2**: 각 재귀 호출은 자체 local variable / parameter
- **4.16.A.3**: 재귀 ↔ 반복 변환 가능
- **4.17.A.1**: 재귀로 String, array, ArrayList 순회 가능
- **EXCLUSION**: `Math.min/max`, `break`/`continue`, **`String.charAt` (Quick Reference 없음)**, `ArrayList.contains/indexOf` 모두 사용 금지
- 단일 문자 추출은 **`s.substring(i, i+1)`** 사용 (CED 1.15.B.3 명시 관용구)

---

## 출제 토픽 분포

| # | 토픽 | 핵심 |
|---|------|------|
| 1 | 4.16 — 자릿수 합 재귀 | n%10 + recurse(n/10) |
| 2 | 4.16 — 곱셈 재귀 (n-2 감소) | n * recurse(n-2) |
| 3 | 4.17.A — String 역순 (재귀) | substring + 결합 |
| 4 | 4.17.A — String 문자 카운트 | substring + equals |
| 5 | 4.17.A — Array 합 (재귀) | arr[idx] + recurse(idx+1) |
| 6 | 4.16 — 다중 재귀 호출 (Fibonacci) | f(n-1) + f(n-2) |
| 7 | 4.16 + 2.12 — 재귀 호출 횟수 | call count for fib |
| 8 | 4.17.A — ArrayList 카운트 (재귀) | get + 조건 + recurse |

**답안 분포**: A:2 / B:2 / C:2 / D:2

---

## 시험 안내

**Directions**: 다음 각 문항에 대해 가장 적절한 답을 고르시오. 별도 명시가 없는 한 Java Quick Reference의 클래스가 import되어 있다고 가정한다.

---

### 1. [CED 4.16 · Hard]

다음은 **재귀로 자릿수 합**을 계산하는 메서드이다.

```java
public static int sumDigits(int n)
{
    if (n == 0) return 0;
    return n % 10 + sumDigits(n / 10);
}
```

다음 호출의 결과는?

```java
int result = sumDigits(7421);
System.out.println(result);
```

(A) `14`
(B) `21`
(C) `4`
(D) `7421`

---

### 2. [CED 4.16 · Hard]

다음 재귀 메서드의 동작을 추적하시오.

```java
public static int mystery(int n)
{
    if (n <= 1) return 1;
    return n * mystery(n - 2);
}
```

다음 호출의 결과는?

```java
int result = mystery(7);
System.out.println(result);
```

(A) `35`
(B) `5040`
(C) `105`
(D) `21`

---

### 3. [CED 4.17.A · Hard]

다음은 **재귀로 String 역순 생성**(CED 4.17.A.1: *"Recursion can be used to traverse String objects"*)을 하는 메서드이다.

```java
public static String reverse(String s)
{
    if (s.length() <= 1) return s;
    return reverse(s.substring(1)) + s.substring(0, 1);
}
```

다음 호출의 결과는?

```java
String result = reverse("STAR");
System.out.println(result);
```

(A) `"STAR"`
(B) `"RATS"`
(C) `"TARS"`
(D) `"ARTS"`

---

### 4. [CED 4.17.A · Hard]

다음은 **재귀로 String 내 특정 문자의 개수**를 세는 메서드이다 (CED 1.15.B.3 단일 문자 추출 관용구 사용).

```java
public static int countChar(String s, String c)
{
    if (s.length() == 0) return 0;
    int rest = countChar(s.substring(1), c);
    if (s.substring(0, 1).equals(c)) return 1 + rest;
    return rest;
}
```

다음 호출의 결과는?

```java
int result = countChar("banana", "a");
System.out.println(result);
```

(A) `1`
(B) `6`
(C) `2`
(D) `3`

---

### 5. [CED 4.17.A · Hard]

다음은 **재귀로 배열 원소 합**을 계산하는 메서드이다 (CED 4.17.A.1: array 순회).

```java
public static int sumArr(int[] arr, int idx)
{
    if (idx >= arr.length) return 0;
    return arr[idx] + sumArr(arr, idx + 1);
}
```

다음 호출의 결과는?

```java
int[] data = {3, 1, 4, 1, 5, 9};
int result = sumArr(data, 0);
System.out.println(result);
```

(A) `13`
(B) `9`
(C) `23`
(D) `3`

---

### 6. [CED 4.16 · Hard]

다음은 **다중 재귀 호출**(한 호출에서 자기 자신을 두 번 호출)을 하는 메서드이다.

```java
public static int f(int n)
{
    if (n <= 1) return n;
    return f(n - 1) + f(n - 2);
}
```

다음 호출의 결과는?

```java
int result = f(6);
System.out.println(result);
```

(A) `8`
(B) `5`
(C) `13`
(D) `21`

---

### 7. [CED 4.16 + 2.12 · Hard]

Q6의 메서드 `f`가 `f(5)` 호출 시 **`f` 메서드는 총 몇 번 호출되는가?** (초기 호출 포함, base case에서 return하는 호출도 포함)

힌트: 재귀 호출 트리를 그리고 모든 노드 카운트.

```java
public static int f(int n)
{
    if (n <= 1) return n;
    return f(n - 1) + f(n - 2);
}
```

(A) `5`
(B) `8`
(C) `9`
(D) `15`

---

### 8. [CED 4.17.A · Hard]

다음은 **재귀로 ArrayList 내 양수 원소 개수**를 세는 메서드이다 (CED 4.17.A.1: ArrayList 순회).

```java
public static int countPositive(ArrayList<Integer> list, int idx)
{
    if (idx >= list.size()) return 0;
    int rest = countPositive(list, idx + 1);
    if (list.get(idx) > 0) return 1 + rest;
    return rest;
}
```

다음 호출의 결과는?

```java
ArrayList<Integer> nums = new ArrayList<Integer>();
nums.add(3); nums.add(-1); nums.add(5); nums.add(-2);
nums.add(4); nums.add(-3); nums.add(7);
int result = countPositive(nums, 0);
System.out.println(result);
```

(A) `7`
(B) `4`
(C) `3`
(D) `10`

---

**END OF TP4**
