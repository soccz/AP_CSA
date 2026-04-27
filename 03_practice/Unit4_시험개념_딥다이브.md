# Unit 4 시험 개념 딥다이브
## Data Collections — 모든 시험 출제 개념의 메커니즘

> **Unit 4는 MCQ 30-40% + FRQ Q3(ArrayList, 5점) + FRQ Q4(2D Array, 6점)**로 시험 배점의 **절반 이상**을 차지한다. 배열·ArrayList 순회, 삭제 중 인덱스 처리, 검색 3종, 정렬 3종(SI/Insertion/Merge), 재귀 트레이싱, 파일 입력 — 이 7개 기둥을 **코드와 호출 스택까지 시각화할 수 있게 될 때까지** 파고든다.
>
> ⚠️ **재귀는 트레이싱만 출제** (CED 4.16 EXCLUSION). 여기서 작성 연습은 **이해용**이고, FRQ 답안에는 재귀를 쓰지 않는다.

---

## 목차

| # | 개념 | 출처 토픽 |
|---|------|---------|
| DD4.1 | 배열 선언·생성의 **3가지 문법**과 차이 | 4.1/4.3 |
| DD4.2 | 배열 default value + 생성 직후 상태 | 4.1/4.3 |
| DD4.3 | `arr.length` 필드의 특성 + 경계 | 4.1 |
| DD4.4 | **Indexed for** vs **Enhanced for** — 값 복사 메커니즘 | 4.3, 4.4 |
| DD4.5 | Enhanced for의 **값 복사 함정** — 왜 원소 변경이 반영 안 되는가 | 4.4 |
| DD4.6 | 표준 배열 알고리즘 — **조건 카운트, 존재 확인, for-all** | 4.5 |
| DD4.7 | 연속 쌍 순회 — `i < length - 1` 경계의 근거 | 4.5 |
| DD4.8 | Shift/Rotate — **뒤에서 앞으로** 이동의 이유 | 4.5 |
| DD4.9 | File 읽기 — `throws IOException` + `Scanner(File)` 관용 | 4.6 |
| DD4.10 | Wrapper class — autoboxing/unboxing의 경계 | 4.7 |
| DD4.11 | `ArrayList<E>` generic — **primitive 불가**의 이유 | 4.7, 4.8 |
| DD4.12 | ArrayList 6개 메서드 — 반환값과 인덱스 경계 정리 | 4.8 |
| DD4.13 | **삭제 중 순회** — index shift와 해결책 3가지 | 4.9, 4.10 |
| DD4.14 | 2D 배열 = **array of arrays** — 메모리 구조 | 4.11 |
| DD4.15 | `arr.length` vs `arr[0].length` — 행/열 규칙 | 4.11 |
| DD4.16 | Row-major vs Column-major — 중첩 루프 순서 | 4.12 |
| DD4.17 | Enhanced for on 2D — outer `int[]`, inner `int` | 4.12 |
| DD4.18 | **Linear search** — 경계 조건과 `-1` 관용 | 4.14 |
| DD4.19 | **Binary search** — mid 계산, 종료, log n의 근거 | 4.14, 4.17 |
| DD4.20 | **Selection sort** — 불변량과 swap 횟수 | 4.15 |
| DD4.21 | **Insertion sort** — 후진 이동 메커니즘 | 4.15 |
| DD4.22 | **Merge sort** — 분할·병합 트리와 O(n log n) 근거 | 4.17 |
| DD4.23 | **재귀 트레이싱** — call stack frame 시각화 | 4.16 |
| DD4.24 | Recursive vs Iterative Binary search — 시험 관점 | 4.17 |
| DD4.25 | FRQ Q3 (ArrayList) 템플릿 — 매년 출제 형식 |  |
| DD4.26 | FRQ Q4 (2D Array) 템플릿 — 매년 출제 형식 |  |

---

## DD4.1 배열 선언·생성의 3가지 문법과 차이

### 3가지 문법

```java
// 1. 크기만 지정 (default로 채워짐)
int[] arr1 = new int[5];                   // {0, 0, 0, 0, 0}

// 2. 초기화 리스트 (크기 자동)
int[] arr2 = {10, 20, 30, 40, 50};          // 크기 5

// 3. new + 리스트 (선언과 생성 분리 가능)
int[] arr3;
arr3 = new int[]{10, 20, 30, 40, 50};
```

### 시험 함정

```java
int[] arr;              // 선언만 — arr은 null
System.out.println(arr.length);   // NullPointerException!

int[] arr2 = new int[0];          // 크기 0 배열 (not null)
System.out.println(arr2.length);  // 0 (OK)
```

**null 배열**과 **빈 배열**은 다르다. null은 객체가 없음, 빈 배열은 크기 0인 객체.

### 선언 후 분리 대입 규칙

```java
int[] arr;
arr = {1, 2, 3};           // ← 컴파일 에러! 이 문법은 선언 때만 허용
arr = new int[]{1, 2, 3};  // OK
```

`{1, 2, 3}` 리터럴은 **선언과 동시에만** 허용. 나중에 대입할 때는 `new int[]{...}` 필요.

---

## DD4.2 배열 default value + 생성 직후 상태

### 표 (DD3.6 복습)

| 배열 타입 | 생성 직후 각 원소 |
|---------|-------------|
| `int[]` | `0` |
| `double[]` | `0.0` |
| `boolean[]` | `false` |
| `String[]`, `Object[]`, 사용자 정의 객체 배열 | `null` |

### 시험 출제 형태

```java
int[] a = new int[3];
System.out.println(a[1]);          // 0

String[] s = new String[2];
System.out.println(s[0]);          // null
System.out.println(s[0].length()); // NullPointerException
```

**참조 타입 배열**은 각 슬롯이 `null`로 초기화되므로, 메서드 호출 전 각 원소에 **실제 객체 할당** 필요:

```java
String[] names = new String[3];
names[0] = "Alice";
names[1] = "Bob";
names[2] = "Carol";
```

---

## DD4.3 `arr.length` 필드의 특성 + 경계

### 규칙 정리 (DD2.13 복습)

```java
arr.length       // 배열, 괄호 없음 (field)
s.length()       // String, 괄호 있음 (method)
list.size()      // ArrayList, 이름 다름
```

### 배열 `.length`의 특이점

배열의 `length`는 **final field**처럼 동작 — 크기는 생성 시 고정, 변경 불가.

```java
int[] arr = new int[5];
arr.length = 10;    // 컴파일 에러
```

### 시험 함정 — 인덱스 경계

```java
int[] arr = new int[5];  // 인덱스 유효 범위: 0~4

arr[5]       // ArrayIndexOutOfBoundsException
arr[-1]      // ArrayIndexOutOfBoundsException
arr[arr.length]     // 5번 인덱스 = AIOOBE
arr[arr.length-1]   // 4번 = 마지막 유효 인덱스
```

**관용**: `arr[arr.length - 1]`이 항상 마지막 원소.

---

## DD4.4 Indexed for vs Enhanced for — 값 복사 메커니즘

### 두 순회 방식

#### Indexed for
```java
for (int i = 0; i < arr.length; i++) {
    // arr[i]로 접근
    arr[i] = arr[i] * 2;    // 원소 변경 가능
}
```

#### Enhanced for
```java
for (int v : arr) {
    // v로 값에 접근
    System.out.println(v);
    // v = v * 2; ← 실제 원소는 안 바뀜 (DD4.5)
}
```

### 메커니즘 — Enhanced for는 **원소의 복사본**을 변수에 넣음

각 iteration 시작할 때 현재 원소의 **값을 복사**하여 변수에 할당. 변수를 바꿔도 원본 배열은 영향받지 않음.

### 선택 기준

| 상황 | 사용 |
|-----|-----|
| 배열/리스트 읽기만 | enhanced for (간결) |
| 인덱스 필요 | indexed for |
| 원소 변경 | **indexed for 필수** (enhanced는 변경 불가) |
| 역순 순회 | indexed for (`i = length-1; i >= 0; i--`) |

---

## DD4.5 Enhanced for의 값 복사 함정

### 시험 출제 형태
> ```java
> int[] arr = {1, 2, 3};
> for (int v : arr) {
>     v = v * 2;
> }
> System.out.println(arr[0]);   // ?
> ```
> → **1**. 2가 아님.

### 메커니즘 시각화

```
iteration 1:
  v ← arr[0] (값 1 복사)
  v = v * 2  → v가 2가 됨
  v와 arr[0]은 독립된 변수 — arr[0]은 여전히 1
```

v는 arr[0]의 "별칭"이 아니라 **값 복사본**. 수정해도 원본 무관.

### 객체 배열은 다른 동작

```java
Point[] points = { new Point(1, 2), new Point(3, 4) };
for (Point p : points) {
    p.setX(0);   // Point 객체의 필드 변경 (참조로)
}
System.out.println(points[0].getX());  // 0
```

`p`는 객체의 **참조 복사본**. p가 가리키는 객체와 points[0]이 가리키는 객체는 **같은 객체**. 그러므로 `p.setX(0)`는 원본 Point에 반영. (Pass-by-value 원리와 동일, DD3.9)

**주의**: `p = new Point(99, 99);`는 **반영 안 됨**. 참조 재대입이기 때문 (DD3.9와 동일).

### 시험 판별

- 원시 타입 배열 + 단순 대입 → 반영 안 됨
- 객체 배열 + 필드/setter 호출 → 반영됨
- 객체 배열 + 객체 교체 (`p = new ...`) → 반영 안 됨

---

## DD4.6 표준 배열 알고리즘 — 조건 카운트, 존재 확인, for-all

### 1. 조건 만족 개수 (Count)

```java
int count = 0;
for (int v : arr) {
    if (v > 0) count++;
}
```

### 2. 존재 확인 (Exists)

```java
boolean has = false;
for (int v : arr) {
    if (v > 0) {
        has = true;
        break;   // 발견 즉시 탈출 (단, break 사용 선호도 확인)
    }
}
// 또는 break 없이
boolean has = false;
for (int v : arr) {
    if (v > 0) has = true;
}
```

break 없어도 정답(전체 순회해도 결과 동일), 단 효율성은 break가 우수.

### 3. For-all (모든 원소 조건 만족)

```java
boolean allPositive = true;
for (int v : arr) {
    if (v <= 0) {
        allPositive = false;
    }
}
```

**핵심 차이**: 
- "존재" → 초기값 `false`, 하나라도 true면 true
- "for-all" → 초기값 `true`, 하나라도 false면 false

### 시험 함정 — 초기값

```java
// 모든 원소가 양수인가?
boolean all = false;   // ← 틀림! 초기값 true여야 함
for (int v : arr) {
    if (v > 0) all = true;   // 이 논리도 틀림 — 하나만 양수여도 true 반환
}

// 올바름
boolean all = true;
for (int v : arr) {
    if (v <= 0) all = false;   // 하나라도 조건 위반 → false
}
```

`for-all`은 "반례 찾기"로 접근. 반례를 만나면 false.

---

## DD4.7 연속 쌍 순회 — `i < length - 1` 경계의 근거

### 시험 출제 형태
> 배열에서 인접한 두 원소가 같은 경우의 수를 세라.

### 관용

```java
int count = 0;
for (int i = 0; i < arr.length - 1; i++) {
    if (arr[i] == arr[i + 1]) count++;
}
```

### 왜 `< length - 1`?

`arr[i + 1]`에 접근하려면 `i + 1 < length` → `i < length - 1`. 
`i = length - 1`이 되면 `arr[length]`는 AIOOBE.

### 시험 함정

```java
for (int i = 0; i < arr.length; i++) {   // ← 틀림!
    if (arr[i] == arr[i + 1]) ...         // 마지막 i에서 arr[length] 접근 → Exception
}
```

**경계 공식**: k개 연속 쌍을 보려면 `i <= arr.length - k` 또는 `i < arr.length - (k - 1)`.

---

## DD4.8 Shift/Rotate — 뒤에서 앞으로 이동의 이유

### 시험 출제 형태
> 배열을 오른쪽으로 1칸 shift하라 (`{1,2,3,4,5}` → `{?, 1, 2, 3, 4}`, 마지막은 사라짐).

### 올바른 순회 방향 — **뒤에서 앞으로**

```java
for (int i = arr.length - 1; i >= 1; i--) {
    arr[i] = arr[i - 1];
}
arr[0] = 0;   // 빈자리 채움
```

### 왜 뒤에서 앞으로?

**앞에서 뒤로** 하면:
```java
for (int i = 1; i < arr.length; i++) {
    arr[i] = arr[i - 1];
}
// {1, 2, 3, 4, 5}:
// i=1: arr[1] = arr[0] = 1 → {1,1,3,4,5}
// i=2: arr[2] = arr[1] = 1 → {1,1,1,4,5}
// i=3: arr[3] = arr[2] = 1 → {1,1,1,1,5}
// i=4: arr[4] = arr[3] = 1 → {1,1,1,1,1}
// 모두 같아짐!
```

**뒤에서 앞으로** 하면:
```java
// {1, 2, 3, 4, 5}:
// i=4: arr[4] = arr[3] = 4 → {1,2,3,4,4}
// i=3: arr[3] = arr[2] = 3 → {1,2,3,3,4}
// i=2: arr[2] = arr[1] = 2 → {1,2,2,3,4}
// i=1: arr[1] = arr[0] = 1 → {1,1,2,3,4}
// OK
```

### 왼쪽 shift (앞에서 뒤로)

```java
for (int i = 0; i < arr.length - 1; i++) {
    arr[i] = arr[i + 1];
}
arr[arr.length - 1] = 0;
```

원본이 덮어쓰이기 **전에** 사용하는 방향으로 순회. 규칙:
- 오른쪽 shift → 뒤에서 앞으로
- 왼쪽 shift → 앞에서 뒤로

---

## DD4.9 File 읽기 — `throws IOException` + `Scanner(File)` 관용

### 관용 코드

```java
import java.io.File;
import java.io.IOException;
import java.util.Scanner;

public static void readFile(String filename) throws IOException {
    Scanner sc = new Scanner(new File(filename));
    while (sc.hasNext()) {
        String word = sc.next();
        // 처리
    }
    sc.close();
}
```

### 핵심 규칙

1. **`throws IOException`**: `new Scanner(new File(...))`는 checked exception을 던질 수 있음 → 메서드 시그니처에 선언 필수
2. **`Scanner(System.in)` 금지** — 시험 EXCLUSION
3. **`sc.close()`**: 파일 닫기 (보통 요구됨)

### Scanner 메서드 (QR 명시)

| 메서드 | 반환 |
|-------|-----|
| `int nextInt()` | 다음 int |
| `double nextDouble()` | 다음 double |
| `boolean nextBoolean()` | 다음 boolean |
| `String next()` | 다음 토큰 (공백 구분) |
| `String nextLine()` | 다음 라인 전체 |
| `boolean hasNext()` | 읽을 게 남았나 |
| `void close()` | 닫기 |

### 시험 함정 — `throws` 누락

```java
public static void foo() {                    // ← throws 없음
    Scanner sc = new Scanner(new File("f"));   // 컴파일 에러!
}
```

File 읽기는 **반드시 `throws IOException`** 필요.

### 시험 함정 — `nextLine()` vs `next()`

- `next()`: 공백까지 한 단어
- `nextLine()`: 개행까지 전체 줄

`nextInt() + nextLine()` 조합의 버그:
```java
int n = sc.nextInt();      // 숫자 읽음, 다음 라인의 개행은 안 소비
String s = sc.nextLine();  // 빈 문자열 (개행만 소비됨)
```

해결: `sc.nextInt(); sc.nextLine();` (개행 한 번 더 소비).

---

## DD4.10 Wrapper class — autoboxing/unboxing의 경계

### Wrapper 클래스

| Primitive | Wrapper |
|-----------|--------|
| `int` | `Integer` |
| `double` | `Double` |
| `boolean` | `Boolean` |

### 사용 이유

- `ArrayList<int>` → **컴파일 에러**. ArrayList는 **객체만** 담을 수 있음
- `ArrayList<Integer>` → OK. Integer는 객체

### Autoboxing / Unboxing

```java
// Autoboxing: primitive → wrapper
Integer a = 5;                // 내부적으로 Integer.valueOf(5)

// Unboxing: wrapper → primitive
int b = a;                    // 내부적으로 a.intValue()

// ArrayList도 자동
ArrayList<Integer> list = new ArrayList<>();
list.add(5);                  // autoboxing: 5 → Integer
int first = list.get(0);      // unboxing: Integer → int
```

### Quick Reference에 있는 wrapper 메서드

```java
Integer.MIN_VALUE            // int MIN = -2147483648
Integer.MAX_VALUE            // int MAX = 2147483647
Integer.parseInt("42")       // String → int
Double.parseDouble("3.14")   // String → double
```

### 시험 함정 — null unboxing

```java
Integer a = null;
int b = a;                   // NullPointerException! (unboxing 시도)
```

### 시험 함정 — Integer끼리의 `==` 비교

```java
Integer a = 100, b = 100;
Integer c = 200, d = 200;
System.out.println(a == b);    // true
System.out.println(c == d);    // false (!)
System.out.println(a.equals(b));    // true
System.out.println(c.equals(d));    // true
```

### 메커니즘 — Integer cache와 `==`의 참조 비교 (DD1.14 연결)

`Integer a = 100;`은 autoboxing으로 `Integer.valueOf(100)`을 호출한다. Java는 **[-128, 127] 범위의 Integer 객체를 내부 캐시**로 보관하며 재사용한다. 그래서:

- `100`은 캐시 범위 → `a`, `b`가 같은 Integer 객체를 가리킴 → `a == b`는 주소 비교 true
- `200`은 캐시 범위 밖 → 매 `valueOf` 호출마다 새 객체 생성 → `c`, `d`는 다른 객체 → `c == d`는 false

이는 Java 전체 룰이 아니라 **`Integer`, `Long` 등 wrapper의 특수 캐시**. AP CSA에는 덜 자주 등장하지만, Integer `==` 비교 문제가 나오면 이 원리로 즉답 가능.

### 시험 안전 규칙 — Integer 비교는 `.equals()` 또는 int로 unboxing

```java
// 위험
Integer a = 200, b = 200;
if (a == b) ...             // false!

// 안전
if (a.equals(b)) ...        // ✅
if (a.intValue() == b.intValue()) ...  // ✅ (명시적 unboxing)

// 자동 unboxing도 안전 (int끼리 == 값 비교)
int x = a, y = b;
if (x == y) ...             // ✅
```

**규칙**: **wrapper 객체끼리 비교는 `.equals()`**. String 비교와 동일 원리 (DD1.14).

### parseInt 예외

```java
Integer.parseInt("abc");     // NumberFormatException
Integer.parseInt("3.14");    // NumberFormatException (소수점 포함은 불가)
```

---

## DD4.11 `ArrayList<E>` generic — primitive 불가의 이유

### 제네릭 규칙

`ArrayList<E>`의 `E`에는 **참조 타입만** 가능.

```java
ArrayList<Integer> ok = new ArrayList<>();   // OK
ArrayList<int> nope = new ArrayList<>();     // 컴파일 에러
ArrayList<String> s = new ArrayList<>();     // OK
```

### 왜 primitive 불가?

Java의 ArrayList는 내부적으로 `Object[]`를 저장. 모든 원소를 `Object`로 취급해야 하는데, primitive는 Object가 아님. 따라서 wrapper만 가능.

### diamond operator `<>`

```java
ArrayList<String> list = new ArrayList<>();     // 권장 (타입 추론)
ArrayList<String> list = new ArrayList<String>();  // 같지만 장황
```

AP는 둘 다 인정.

### 다중 제네릭 — 중첩

```java
ArrayList<ArrayList<Integer>> grid = new ArrayList<>();
grid.add(new ArrayList<>());
grid.get(0).add(5);
```

FRQ에서 가끔 나옴.

---

## DD4.12 ArrayList 6개 메서드 — 반환값과 인덱스 경계

### QR 수록 6개 (이것만 출제)

| 메서드 | 반환 | 경계 | 주의 |
|-------|-----|-----|-----|
| `int size()` | int | — | 현재 원소 수 |
| `boolean add(E obj)` | `true` (항상) | — | 끝에 추가, 반환값은 거의 안 씀 |
| `void add(int i, E obj)` | void | `0 <= i <= size()` | i에 삽입, 뒤 원소들 밀림 |
| `E get(int i)` | E | `0 <= i < size()` | 인덱스 요소 반환 |
| `E set(int i, E obj)` | **이전 요소** | `0 <= i < size()` | 교체하고 이전 값 반환 |
| `E remove(int i)` | **제거된 요소** | `0 <= i < size()` | 제거하고 뒤 원소 당김 |

### 시험 단골 함정

#### 1. `add(int, E)`의 경계 — `i == size()` 허용

```java
ArrayList<String> list = new ArrayList<>();
list.add("A");           // size = 1
list.add(1, "B");        // OK (인덱스 1은 size와 동일 → 끝에 추가 효과)
list.add(3, "C");        // 에러! (size=2, 인덱스 3은 범위 밖)
```

`add(i, obj)`의 `i`는 `size()`까지 허용. 이것만 특수.

#### 2. `remove`가 반환하는 것

```java
ArrayList<String> list = new ArrayList<>();
list.add("A"); list.add("B"); list.add("C");
String r = list.remove(1);    // r = "B" (반환값은 제거된 요소)
// list = [A, C]
```

반환값을 "남은 요소 중 하나"나 "true/false"로 오인하면 함정.

#### 3. `set` 반환값

```java
String prev = list.set(0, "X");   // prev = 이전 인덱스 0 요소
```

이전 요소 반환. 새 요소 아님.

### EXCLUSION — 쓰지 말 것

- `list.isEmpty()` — QR 없음
- `list.contains(x)` — QR 없음
- `list.indexOf(x)` — QR 없음 (String의 indexOf와 혼동 주의)
- `list.clear()` — QR 없음

필요하면 직접 구현:
```java
// isEmpty() 대체
if (list.size() == 0) ...

// contains() 대체
boolean has = false;
for (int i = 0; i < list.size(); i++) {
    if (list.get(i).equals(target)) has = true;
}
```

### 시험 함정 — `list.remove(0)`은 **인덱스 0** 제거, 값 0 제거가 아님

```java
ArrayList<Integer> list = new ArrayList<>();
list.add(10);
list.add(20);
list.add(30);

list.remove(0);      // ← 인덱스 0의 원소(10) 제거, 리스트: [20, 30]
```

**주의**: AP CSA Quick Reference에 `remove(int index)`만 수록되어 있다. 그래서 시험 범위 내에서는 **항상 인덱스 기반**으로 동작. 

하지만 Java 표준 라이브러리에는 `remove(Object)`도 존재해 `list.remove(Integer.valueOf(10))`처럼 **값 기반** 제거도 가능. AP 답안에서는 이 형태를 쓰지 않으므로 헷갈리지 말 것.

### 값 기반 제거를 수동 구현해야 함

"리스트에서 값 10을 모두 제거하라" 같은 문제는:

```java
// 뒤에서 앞으로 순회하며 값 비교
for (int i = list.size() - 1; i >= 0; i--) {
    if (list.get(i) == 10) {       // Integer는 autoboxing으로 값 비교 가능
        list.remove(i);             // 인덱스 기반 제거
    }
}
```

Integer를 `==`로 비교하는 것은 DD4.10의 cache 함정에 주의 — [-128, 127] 밖이면 `.equals()` 또는 `.intValue()`로 비교해야 안전. 시험은 보통 작은 수 예시라 `==`로 OK.

**안전한 관용**:
```java
if (list.get(i).equals(10)) { ... }   // 항상 값 비교
```

### Array ↔ ArrayList 변환 관용구

FRQ에서 매개변수는 `int[]`인데 내부에서 ArrayList 기능이 필요하거나 반대 경우가 자주 등장.

#### Array → ArrayList

```java
int[] arr = {1, 2, 3, 4, 5};
ArrayList<Integer> list = new ArrayList<>();
for (int i = 0; i < arr.length; i++) {
    list.add(arr[i]);      // autoboxing: int → Integer
}
```

**관용**: `Arrays.asList(arr)` 같은 단축은 **QR에 없음**. 반드시 수동 루프.

#### ArrayList → Array

```java
ArrayList<Integer> list = new ArrayList<>();
list.add(10); list.add(20); list.add(30);

int[] arr = new int[list.size()];
for (int i = 0; i < list.size(); i++) {
    arr[i] = list.get(i);  // unboxing: Integer → int
}
```

**관용**: `list.toArray()` 같은 단축은 **QR에 없음**. 수동 루프.

#### String 버전

```java
// String[] → ArrayList<String>
String[] arr = {"a", "b", "c"};
ArrayList<String> list = new ArrayList<>();
for (int i = 0; i < arr.length; i++) list.add(arr[i]);

// ArrayList<String> → String[]
String[] arr2 = new String[list.size()];
for (int i = 0; i < list.size(); i++) arr2[i] = list.get(i);
```

### 언제 Array, 언제 ArrayList?

| 상황 | 선택 |
|-----|-----|
| 크기 고정, 빠른 접근 | Array |
| 요소 추가·제거 빈번 | ArrayList |
| FRQ 지문이 `int[]` 지시 | Array |
| FRQ 지문이 `ArrayList<E>` 지시 | ArrayList |

FRQ에서는 **지문의 타입을 그대로 따르는 게 원칙**.

### 변환 시 autoboxing 함정

```java
// null이 든 ArrayList unboxing
ArrayList<Integer> list = new ArrayList<>();
list.add(null);
int x = list.get(0);   // NullPointerException!
```

---

## DD4.13 삭제 중 순회 — index shift와 해결책 3가지

### 시험 출제 형태
> 다음 코드의 결과는?
> ```java
> ArrayList<Integer> list = new ArrayList<>();
> list.add(1); list.add(2); list.add(2); list.add(3);
> for (int i = 0; i < list.size(); i++) {
>     if (list.get(i) == 2) list.remove(i);
> }
> ```
> → list = [1, 2, 3] (하나의 2만 제거됨, 왜?)

### 메커니즘 — remove 시 **인덱스 shift**

```
초기:   [1, 2, 2, 3]
i=0: list.get(0) = 1, 삭제 안 함
i=1: list.get(1) = 2, remove(1) → [1, 2, 3]  (뒤 원소가 당겨짐)
     이제 원래 list[2]였던 2가 list[1]로 이동했지만
     i는 다음 반복에서 2로 증가
i=2: list.get(2) = 3, 삭제 안 함
종료: [1, 2, 3]
```

원래 list[2]에 있던 `2`가 list[1]로 **당겨졌는데** i는 증가해서 그 원소를 **건너뛴다**. 결과 하나의 2만 삭제됨.

### 해결책 1 — 삭제 시 `i--`

```java
for (int i = 0; i < list.size(); i++) {
    if (list.get(i) == 2) {
        list.remove(i);
        i--;            // ← 같은 인덱스 다시 체크
    }
}
```

### 해결책 2 — 뒤에서 앞으로 순회

```java
for (int i = list.size() - 1; i >= 0; i--) {
    if (list.get(i) == 2) list.remove(i);
}
```

인덱스 shift가 **아직 처리하지 않은** 부분에 영향을 주지 않음. 가장 안전.

### 해결책 3 — 새 리스트 생성

```java
ArrayList<Integer> result = new ArrayList<>();
for (int i = 0; i < list.size(); i++) {
    if (list.get(i) != 2) result.add(list.get(i));
}
list = result;
```

원본 순회하며 유지할 요소만 새 리스트에. 명확하지만 메모리 사용.

### 시험 함정 — Enhanced for + remove

```java
for (Integer v : list) {
    if (v == 2) list.remove(v);    // ConcurrentModificationException!
}
```

Enhanced for에서 리스트 구조 변경 → **ConcurrentModificationException** (런타임 에러). 반드시 indexed for를 써야 한다.

### FRQ Q3 핵심

Q3는 거의 매년 ArrayList에서 조건에 맞는 요소를 제거/교체. **삭제 중 순회**를 올바르게 처리하는 것이 1점 획득의 핵심.

### 통합 원리 — DD4.8(shift/rotate)과 DD4.13(삭제 중 순회)은 **같은 규칙**

두 문제의 본질은 동일하다:

> **"배열/리스트를 수정하며 순회할 때는 **아직 처리 안 한 영역에 영향을 주지 않는 방향**으로 순회한다."**

### 두 맥락 나란히 보기

#### 오른쪽 shift (DD4.8)
```
{1, 2, 3, 4, 5} → {_, 1, 2, 3, 4}
- 순회 방향: 뒤에서 앞으로
- 이유: 앞에서 뒤로 가면 덮어쓴 값을 다시 읽어 버그
```

#### ArrayList 삭제 (DD4.13)
```
[1, 2, 2, 3] → [1, 3]  (2 제거)
- 순회 방향: 뒤에서 앞으로 (또는 i--)
- 이유: 앞에서 뒤로 가면 index shift로 원소를 건너뛰어 버그
```

### 원리 일반화 — "파괴적 순회"의 3규칙

1. **삭제**: 뒤에서 앞으로 순회 (또는 삭제 후 i--)
2. **오른쪽 shift/삽입**: 뒤에서 앞으로 순회
3. **왼쪽 shift**: 앞에서 뒤로 순회 (이번엔 반대 — 이미 읽은 원소만 덮기 때문)

**공통 원칙**: "읽기 전에 쓰면 안 된다". 순회 방향을 선택할 때 **덮어쓰는 대상이 아직 안 읽은 원소가 아닌지** 확인.

### 시험 판별 — 어느 방향?

```
Q: 루프가 arr[i]를 덮어쓰면서 arr[?]를 읽는가?
   만약 arr[i-1] 또는 이전 인덱스를 읽음 → 앞에서 뒤로 OK
   만약 arr[i+1] 또는 이후 인덱스를 읽음 → 뒤에서 앞으로 필수
Q: ArrayList의 remove로 크기가 줄어드는가?
   YES → 뒤에서 앞으로 또는 i-- 필수
```

이 두 질문만 체크하면 **"삭제 중 순회"와 "shift"가 하나의 유형**으로 보인다. 시험에서 새 변형이 나와도 이 원리로 분류 가능.

---

## DD4.14 2D 배열 = array of arrays — 메모리 구조

### 선언·생성

```java
int[][] grid = new int[3][4];           // 3행 4열, 모두 0
int[][] grid2 = {
    {1, 2, 3, 4},
    {5, 6, 7, 8},
    {9, 10, 11, 12}
};
```

### 메모리 시각화

```
grid (외부 배열) → [row0 참조] ────→ [1, 2, 3, 4]
                    [row1 참조] ────→ [5, 6, 7, 8]
                    [row2 참조] ────→ [9, 10, 11, 12]
```

Java의 2D 배열은 **"배열의 배열"**. 외부 배열 각 원소가 내부 배열(행)의 참조.

### 접근

```java
grid[0][0];    // 1 (0행 0열)
grid[2][3];    // 12 (2행 3열)
grid[i][j];    // i행 j열
```

**규칙**: `[행][열]` 순서. 첫 인덱스 = 행, 둘째 = 열.

### 비직사각형(jagged) 2D 배열 — EXCLUSION

Java는 각 행이 다른 길이인 배열을 허용하지만 **AP CSA는 직사각형만 출제** (CED 4.11 EXCLUSION).

```java
int[][] jagged = new int[3][];
jagged[0] = new int[2];     // 0행: 2열
jagged[1] = new int[5];     // 1행: 5열 — AP 범위 밖
```

시험에서는 **항상 `grid[0].length`가 모든 행의 열 개수**라고 가정할 수 있다.

---

## DD4.15 `arr.length` vs `arr[0].length` — 행/열 규칙

### 규칙

```java
int[][] grid = new int[3][4];

grid.length;        // 3 (행 수 = 외부 배열 크기)
grid[0].length;     // 4 (열 수 = 내부 배열 크기)
```

### 암기 문구

> **"점 첫 번째(외부)가 행, 점 두 번째(내부)가 열."**

### 시험 단골 함정

```java
int rows = grid[0].length;    // ← 틀림! 이건 열 개수
int cols = grid.length;       // ← 틀림! 이건 행 개수

int rows = grid.length;       // ✅
int cols = grid[0].length;    // ✅
```

`grid[0].length`는 **"0번째 행의 길이"** = 그 행의 열 개수.

---

## DD4.16 Row-major vs Column-major — 중첩 루프 순서

### 두 순회 순서

#### Row-major (기본)
```java
for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[0].length; c++) {
        System.out.print(grid[r][c] + " ");
    }
    System.out.println();
}
```

출력 순서: grid[0][0], grid[0][1], ..., grid[0][cols-1], grid[1][0], ...
→ 한 행 전체를 먼저, 다음 행으로.

#### Column-major
```java
for (int c = 0; c < grid[0].length; c++) {
    for (int r = 0; r < grid.length; r++) {
        System.out.print(grid[r][c] + " ");
    }
    System.out.println();
}
```

출력 순서: grid[0][0], grid[1][0], ..., grid[rows-1][0], grid[0][1], ...
→ 한 열 전체를 먼저, 다음 열로.

### 시험 출제 형태

```java
int[][] g = {{1,2,3}, {4,5,6}};
for (int c = 0; c < g[0].length; c++) {
    for (int r = 0; r < g.length; r++) {
        System.out.print(g[r][c]);
    }
}
```

출력: `142536` (column-major: 1행 0열, 2행 0열, 1행 1열, 2행 1열, ...).

### 시험 관용

- 외부 루프 변수 = row → row-major
- 외부 루프 변수 = column → column-major

변수 이름(i, j)로 판단하지 말고 **무엇이 외부냐**로 판단.

---

## DD4.17 Enhanced for on 2D — outer `int[]`, inner `int`

### 관용 코드

```java
int[][] grid = {{1,2,3}, {4,5,6}};

for (int[] row : grid) {       // outer: 행(1D 배열)
    for (int v : row) {         // inner: 값(int)
        System.out.print(v + " ");
    }
}
```

### 메커니즘

2D 배열은 "배열의 배열"이므로:
- 외부 iteration: 각 **행 (1D 배열)**
- 내부 iteration: 각 행의 **원소 (int)**

### 시험 출제 형태

```java
// row-major 합계
int sum = 0;
for (int[] row : grid) {
    for (int v : row) {
        sum += v;
    }
}
```

간결해서 FRQ Q4 모범 답안. 단, **원소 변경은 indexed for로** (DD4.5 enhanced for 값 복사 함정).

### 행 길이가 다를 때 (AP 범위 밖)

Enhanced for는 각 행 길이를 자동 처리. `row.length`가 행마다 달라도 각자 순회. AP는 직사각만 출제하니 이 장점은 시험에서 중요하지 않음.

---

## DD4.18 Linear search — 경계 조건과 `-1` 관용

### 기본 구현

```java
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) return i;
    }
    return -1;
}
```

### 핵심 규칙

- 찾으면: **첫 발견 인덱스** 반환
- 못 찾으면: **-1** 반환

### 객체 검색 시 `.equals()`

```java
public static int find(String[] arr, String target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i].equals(target)) return i;   // == 금지!
    }
    return -1;
}
```

### ArrayList 버전

```java
public static int find(ArrayList<String> list, String target) {
    for (int i = 0; i < list.size(); i++) {
        if (list.get(i).equals(target)) return i;
    }
    return -1;
}
```

**EXCLUSION**: `list.indexOf(target)`는 QR 없음. 위 수동 구현 필수.

### 복잡도

- 최악: O(n) — 끝까지 못 찾는 경우
- 평균: O(n)
- 최선: O(1) — 첫 원소가 target

---

## DD4.19 Binary search — mid 계산, 종료, log n 근거

### 기본 구현 (iterative)

```java
public static int binarySearch(int[] arr, int target) {
    int low = 0;
    int high = arr.length - 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}
```

### 핵심 규칙

1. **정렬된 배열에만** 작동
2. `mid = (low + high) / 2`
3. target이 mid보다 크면 오른쪽 절반 (`low = mid + 1`)
4. 작으면 왼쪽 절반 (`high = mid - 1`)
5. `low > high`가 되면 **못 찾음** → -1

### 시험 트레이싱 (단골)

```
arr = {2, 5, 8, 12, 16, 23, 38}, target = 23

iter 1: low=0, high=6, mid=3, arr[3]=12 < 23 → low=4
iter 2: low=4, high=6, mid=5, arr[5]=23 == 23 → return 5
```

시험은 이렇게 단계별 `low, high, mid, arr[mid]`를 추적시킨다.

### 왜 O(log n)?

각 단계마다 탐색 범위가 **반씩 줄어듬**. n → n/2 → n/4 → ... → 1. 단계 수 = `log₂ n`.

### mid 계산 주의

`(low + high) / 2`는 **integer overflow 위험** (low+high가 MAX_VALUE 초과 시). 안전한 형태:
```java
int mid = low + (high - low) / 2;
```

하지만 AP CSA에서는 보통 `(low + high) / 2`를 쓴다 — 배열 크기가 작아 overflow 무관.

### 종료 조건 함정

```java
while (low < high)   // ← 틀림! low == high인 마지막 원소를 건너뜀
while (low <= high)  // ✅
```

### Linear vs Binary search — 언제 어느 것? 통합 조건표

두 검색 알고리즘을 따로 배우지 말고 **적용 조건과 성능**으로 통합해서 본다.

| 조건 | Linear (DD4.18) | Binary (DD4.19) |
|-----|---------------|---------------|
| **배열 정렬 필요?** | ❌ 불요 | ✅ **필수** (안 되어 있으면 오답 가능) |
| **시간 복잡도** | O(n) | O(log n) |
| **구현 난이도** | 간단 | 중간 (경계 조건 주의) |
| **평균 비교 횟수** (n=1000) | 500 | 10 |
| **못 찾음 반환** | -1 | -1 |
| **AP 시험 출제 형태** | 구현·트레이싱 모두 OK | 트레이싱 자주, 구현 가끔 |

### 판별 플로우 (시험 지문 읽을 때)

```
Q1. 배열이 "정렬되어 있다"고 명시됐는가?
    YES → binary search 사용 가능 → Q2로
    NO → **반드시 linear search** (binary는 틀린 결과 가능)

Q2. 성능이 중요하다고 명시? (n이 큼, O(log n) 언급)
    YES → binary search 권장
    NO → 둘 다 가능 (linear가 간단)

Q3. 구현해야 하나 (FRQ)? 트레이싱만 하면 되나 (MCQ)?
    FRQ 구현 → linear가 버그 덜 생김 (단, 지문이 binary 요구하면 binary)
    MCQ 트레이싱 → 지문의 코드 그대로 따라가기
```

### 함정 — 정렬 안 된 배열에 binary search

```java
int[] arr = {5, 3, 8, 1, 9};   // 정렬 안 됨
int idx = binarySearch(arr, 3);  // 결과 미정 — 운 좋으면 맞고 보통 -1
```

Binary search는 **정렬 전제**가 깨지면 `-1` 반환하거나 **아예 틀린 인덱스** 반환. 시험은 정렬 여부를 명시한다.

### 2D 배열에서의 검색

AP CSA는 2D 배열에 **linear search만** 적용. 보통 **row별로 순차 검색**.

```java
public static int[] find2D(int[][] grid, int target) {
    for (int r = 0; r < grid.length; r++) {
        for (int c = 0; c < grid[0].length; c++) {
            if (grid[r][c] == target) {
                return new int[]{r, c};
            }
        }
    }
    return new int[]{-1, -1};   // 못 찾음
}
```

2D에 binary search는 AP 범위 밖.

### ArrayList 검색

```java
// Linear
public static int find(ArrayList<String> list, String target) {
    for (int i = 0; i < list.size(); i++) {
        if (list.get(i).equals(target)) return i;
    }
    return -1;
}
```

ArrayList에 binary search는 지문에서 "정렬된 ArrayList"라고 명시되고 `get(i)`으로 중간 접근하는 형태로 출제. 형태는 array binary search와 동일.

---

## DD4.20 Selection sort — 불변량과 swap 횟수

### 알고리즘

```java
public static void selectionSort(int[] arr) {
    for (int i = 0; i < arr.length - 1; i++) {
        int minIdx = i;
        for (int j = i + 1; j < arr.length; j++) {
            if (arr[j] < arr[minIdx]) minIdx = j;
        }
        // swap arr[i] and arr[minIdx]
        int tmp = arr[i];
        arr[i] = arr[minIdx];
        arr[minIdx] = tmp;
    }
}
```

### 메커니즘 — 매 반복마다 미정렬 구간에서 **최솟값을 찾아 맨 앞으로**

```
{5, 3, 8, 1, 9}
i=0: 미정렬 [5,3,8,1,9] 최소 = 1 (인덱스 3), swap arr[0]↔arr[3]
     → {1, 3, 8, 5, 9}
i=1: 미정렬 [3,8,5,9] 최소 = 3 (인덱스 1, 그대로)
     → {1, 3, 8, 5, 9}
i=2: 미정렬 [8,5,9] 최소 = 5 (인덱스 3), swap arr[2]↔arr[3]
     → {1, 3, 5, 8, 9}
i=3: 미정렬 [8,9] 최소 = 8 (인덱스 3, 그대로)
     → {1, 3, 5, 8, 9}
```

### 시험 트레이싱 체크리스트

- 각 i 반복 후 배열 상태 기록
- swap이 발생했는가 (swap 횟수 종종 출제)
- 내부 루프가 `j = i + 1`부터 시작 (이미 i 앞은 정렬됨)

### 불변량 (Invariant)

> **i번 반복 후: 첫 i개 원소는 정렬되었고 전체에서 가장 작은 i개**.

이게 selection sort의 핵심. 종종 "k번 후의 상태"를 묻는 문제가 나옴.

### 복잡도

- 비교 횟수: n(n-1)/2 (항상 동일) → **O(n²)**
- swap 횟수: 최대 n-1회 (비교적 적음)

---

## DD4.21 Insertion sort — 후진 이동 메커니즘

### 알고리즘

```java
public static void insertionSort(int[] arr) {
    for (int i = 1; i < arr.length; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
```

### 메커니즘 — 현재 원소를 **정렬된 앞부분의 올바른 위치에 삽입**

```
{5, 3, 8, 1, 9}
i=1: key=3, 앞 [5]
     3 < 5 → 5 한 칸 뒤로, 3을 [0]에 삽입
     → {3, 5, 8, 1, 9}
i=2: key=8, 앞 [3,5]
     8 > 5 → 그대로
     → {3, 5, 8, 1, 9}
i=3: key=1, 앞 [3,5,8]
     1 < 8 → 8 뒤로, 1 < 5 → 5 뒤로, 1 < 3 → 3 뒤로, [0]에 1
     → {1, 3, 5, 8, 9}
i=4: key=9, 앞 [1,3,5,8]
     9 > 8 → 그대로
     → {1, 3, 5, 8, 9}
```

### 시험 트레이싱 함정

Selection과 달리 **swap 횟수가 아니라 "shift 횟수"가 중요**. 각 반복에서 얼마나 많이 뒤로 미는가.

### 불변량

> **i번 반복 후: 첫 i+1개 원소는 자기들끼리 정렬됨 (but 최종 위치는 아닐 수 있음).**

Selection과 차이:
- Selection: 각 i번 후 i개가 **최종 위치**
- Insertion: 각 i번 후 i+1개가 **서로 정렬**되지만 이후 요소가 더 작으면 밀려날 수 있음

### 복잡도

- 최악: O(n²) (역순 정렬 배열)
- 최선: O(n) (이미 정렬된 배열)
- 평균: O(n²)

Insertion은 "거의 정렬된" 배열에서 selection보다 빠르다.

---

## DD4.22 Merge sort — 분할·병합 트리와 O(n log n) 근거

### 재귀 구현

```java
public static void mergeSort(int[] arr, int left, int right) {
    if (left >= right) return;                 // Base
    int mid = (left + right) / 2;
    mergeSort(arr, left, mid);                 // 왼쪽 정렬
    mergeSort(arr, mid + 1, right);            // 오른쪽 정렬
    merge(arr, left, mid, right);              // 병합
}

public static void merge(int[] arr, int left, int mid, int right) {
    int[] temp = new int[right - left + 1];
    int i = left, j = mid + 1, k = 0;
    while (i <= mid && j <= right) {
        if (arr[i] <= arr[j]) {
            temp[k] = arr[i];
            k++;
            i++;
        } else {
            temp[k] = arr[j];
            k++;
            j++;
        }
    }
    while (i <= mid) {
        temp[k] = arr[i];
        k++;
        i++;
    }
    while (j <= right) {
        temp[k] = arr[j];
        k++;
        j++;
    }
    for (int t = 0; t < temp.length; t++) {
        arr[left + t] = temp[t];
    }
}
```

> ⚠️ **`temp[k++] = arr[i++]` 같은 표현식 내부 `++` 사용은 CED 1.6 EXCLUSION**이다. 위 코드는 분리 형태로 작성했다.

### 재귀 호출 트리 (8개 원소 예)

```
mergeSort(0, 7)
├── mergeSort(0, 3)
│   ├── mergeSort(0, 1)
│   │   ├── mergeSort(0, 0) ← base
│   │   └── mergeSort(1, 1) ← base
│   │   merge(0, 0, 1)
│   └── mergeSort(2, 3)
│       ├── mergeSort(2, 2) ← base
│       └── mergeSort(3, 3) ← base
│       merge(2, 2, 3)
│   merge(0, 1, 3)
└── mergeSort(4, 7)
    ├── mergeSort(4, 5)
    │   ├── mergeSort(4, 4) ← base
    │   └── mergeSort(5, 5) ← base
    │   merge(4, 4, 5)
    └── mergeSort(6, 7)
        ├── mergeSort(6, 6) ← base
        └── mergeSort(7, 7) ← base
        merge(6, 6, 7)
    merge(4, 5, 7)
merge(0, 3, 7)
```

### O(n log n) 근거 — 레벨별 시각화

**왜 log n 레벨인가**: n개를 반씩 나누면 1이 될 때까지 `log₂ n`번 나눠야 한다. (n=8이면 8→4→2→1, 총 3번 = log₂ 8)

**왜 레벨당 n인가**: 각 레벨에서 merge는 **해당 레벨의 모든 원소를 한 번씩** 비교·복사한다. 총 합치면 n개.

### 레벨별 다이어그램 (n=8 예)

```
Level 0 (입력):        [8][4][2][7][1][3][6][5]        — 8 원소
                        ↓ 분할
Level 1:               [8,4,2,7]    [1,3,6,5]          — 4+4 = 8 원소
                        ↓
Level 2:              [8,4]  [2,7]  [1,3]  [6,5]       — 2+2+2+2 = 8 원소
                        ↓
Level 3 (base):       [8][4][2][7][1][3][6][5]         — 각자 1개

병합 시 (아래→위):
Level 3 merge:        [4,8][2,7][1,3][5,6]              — 각 pair 2 비교·복사 × 4 = 8 작업
Level 2 merge:        [2,4,7,8]  [1,3,5,6]              — 각 4 비교·복사 × 2 = 8 작업
Level 1 merge:        [1,2,3,4,5,6,7,8]                 — 8 비교·복사 = 8 작업

총 작업 = 8 × 3 레벨 = 24 = n × log₂ n
```

**핵심**: 매 병합 레벨에서 **모든 n개 원소가 정확히 한 번씩 비교·복사**된다. 레벨 수는 `log₂ n`. 총 작업 = `n × log₂ n` = **O(n log n)**.

### 왜 n²이 아닌가 (selection/insertion과 비교)

Selection/Insertion은 각 원소에 대해 n번씩 비교하므로 `n × n = n²`. Merge는 각 원소를 log n 레벨에서만 다루므로 `n × log n`. 이 차이가 n=1000일 때:
- n² = 1,000,000
- n log n ≈ 1000 × 10 = 10,000

**100배 빠름**. Merge sort가 대규모 데이터에 유리한 이유.

### 시험 판별 한 문장

> "**반씩 쪼개고 합친다 → log n 레벨, 레벨당 n 작업 → n log n**."

### 시험 트레이싱

```
{38, 27, 43, 3, 9, 82, 10, 15}
분할: {38,27,43,3} {9,82,10,15}
      {38,27}{43,3} {9,82}{10,15}
      {38}{27}{43}{3} {9}{82}{10}{15}  (크기 1 = 자동 정렬)
병합 (아래→위):
  {38}+{27}={27,38}  {43}+{3}={3,43}  {9}+{82}={9,82}  {10}+{15}={10,15}
  {27,38}+{3,43}={3,27,38,43}  {9,82}+{10,15}={9,10,15,82}
  {3,27,38,43}+{9,10,15,82}={3,9,10,15,27,38,43,82}
```

---

## DD4.23 재귀 트레이싱 — call stack frame 시각화

### 재귀 작성 금지 (EXCLUSION)

> **CED 4.16**: "Writing recursive code is outside the scope of the AP Computer Science A course and exam." 
> 학생은 주어진 재귀를 **추적**할 수 있어야 한다. 작성은 요구되지 않는다.

### Call stack frame 시각화 — 팩토리얼

```java
public static int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
```

`factorial(4)` 호출 시 call stack:

```
─ factorial(1) → return 1
─ factorial(2) → 2 * factorial(1) = 2 * 1 = 2 → return 2
─ factorial(3) → 3 * factorial(2) = 3 * 2 = 6 → return 6
─ factorial(4) → 4 * factorial(3) = 4 * 6 = 24 → return 24
```

**각 frame은 자신의 로컬 변수와 매개변수를 독립적으로 보유.** 위쪽 frame이 return되면 아래쪽 frame의 계산이 이어짐.

### 피보나치 트레이싱 (여러 분기)

```java
public static int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}
```

`fib(4)` 호출 트리:

```
fib(4)
├── fib(3)
│   ├── fib(2)
│   │   ├── fib(1) → 1
│   │   └── fib(0) → 0
│   │   → 1 + 0 = 1
│   └── fib(1) → 1
│   → 1 + 1 = 2
└── fib(2)
    ├── fib(1) → 1
    └── fib(0) → 0
    → 1 + 0 = 1
→ 2 + 1 = 3
```

`fib(4) = 3`.

### 시험 유형 — **"fib(5)의 결과는?"** 또는 **"재귀 호출 총 횟수는?"**

재귀 호출 횟수 세는 문제도 자주 나옴. 세 가지 사고 전략을 정리:

#### 전략 1 — 작은 n 직접 트레이싱 (가장 안전)

n이 5-6 이하면 트리를 그려 leaf 수를 센다:

```
fib(4) 호출 트리 (위 참조)
잎(return 지점) 개수 = 호출 총 횟수 - 내부 노드 수

fib(4)
├── fib(3) ──── fib(2) ── fib(1) [leaf]
│   │          └── fib(0) [leaf]
│   └── fib(1) [leaf]
└── fib(2) ── fib(1) [leaf]
    └── fib(0) [leaf]

총 호출: fib(4), fib(3), fib(2)×2, fib(1)×3, fib(0)×2 = 9번
```

**세는 방법**: 트리의 **모든 노드 수 = 호출 횟수** (root 포함).

#### 전략 2 — 점화식 (빠르게 중간값 아는 경우)

`fib(n)`의 호출 횟수를 `T(n)`이라 하면:
- T(0) = 1, T(1) = 1 (base case — 호출 1번)
- T(n) = 1 + T(n-1) + T(n-2) (자신 1번 + 두 재귀)

이 자체가 피보나치 형태. T(n) 표를 미리 만들어 두면:

| n | fib(n) | T(n) 호출 횟수 |
|---|-------|-----------|
| 0 | 0 | 1 |
| 1 | 1 | 1 |
| 2 | 1 | 3 |
| 3 | 2 | 5 |
| 4 | 3 | 9 |
| 5 | 5 | 15 |
| 6 | 8 | 25 |

규칙: `T(n) = T(n-1) + T(n-2) + 1`.

#### 전략 3 — 판별용 관찰

피보나치처럼 **두 번 재귀**하면 호출 횟수가 지수적(`O(2^n)`)으로 증가한다. 반면:
- `factorial(n)`: 한 번 재귀 → 호출 `n+1`번 (선형)
- `binarySearchRecursive`: 반씩 줄임 → 호출 `log₂ n + 1`번 이하 (로그)

**시험 관찰**: n=10일 때 호출 횟수가 **10 수준이면 선형 재귀**, **수십~수백 수준이면 피보나치식 이중 재귀**, **수 수준이면 binary search식 분할**.

### 시험 단골 질문 정리

| 질문 유형 | 접근법 |
|---------|-----|
| "fib(5) 값은?" | 직접 트레이싱: fib(5) = 5 |
| "fib(5) 호출 총 횟수?" | T(5) = 15 (표 참조) |
| "factorial(n) 호출 횟수?" | n+1 (base case까지 포함) |
| "사용자 정의 재귀 — k번 호출?" | 작은 인자로 트레이싱 → 패턴 찾기 |
| "Binary search recursive — 호출 횟수?" | `⌊log₂ n⌋ + 1` 이하 (정렬 배열 크기 n) |

### String 재귀

```java
public static String reverse(String s) {
    if (s.length() <= 1) return s;
    return reverse(s.substring(1)) + s.substring(0, 1);
}
```

`reverse("abc")`:
```
reverse("abc") = reverse("bc") + "a"
              = (reverse("c") + "b") + "a"
              = ("c" + "b") + "a"
              = "cb" + "a"
              = "cba"
```

### 시험 트레이싱 전략

1. Base case 확인
2. 인자가 어떻게 작아지는지 파악
3. 각 frame의 반환값을 **가장 깊은 곳부터** 계산
4. 표나 트리로 정리

---

## DD4.24 Recursive vs Iterative Binary search — 시험 관점

### Recursive 버전

```java
public static int bsearch(int[] arr, int target, int low, int high) {
    if (low > high) return -1;
    int mid = (low + high) / 2;
    if (arr[mid] == target) return mid;
    else if (arr[mid] < target) return bsearch(arr, target, mid + 1, high);
    else return bsearch(arr, target, low, mid - 1);
}
```

호출: `bsearch(arr, 23, 0, arr.length - 1);`

### 시험에서 재귀 vs 반복 비교

| 관점 | Iterative | Recursive |
|-----|-----------|-----------|
| 출제 형태 | 트레이싱 + **작성 OK** | **트레이싱만** |
| 공간 복잡도 | O(1) | O(log n) — call stack |
| 시간 복잡도 | 동일 O(log n) | 동일 O(log n) |

### 시험 함정 — 재귀 종료 조건

```java
if (low > high) return -1;   // ✅
if (low >= high) return -1;  // ← 틀림: low=high=target 위치인 경우 놓침
```

**동일한 규칙**: `low > high`일 때 종료, `low == high`일 때도 한 번 더 체크.

### Merge sort는 오직 재귀 (AP 수준)

Iterative merge sort도 존재하지만 AP는 재귀 버전만 다룬다. **재귀 트레이싱**만 요구.

---

## DD4.25 FRQ Q3 (ArrayList) 템플릿 — 매년 출제 형식

### 형식

> 주어진 ArrayList에서 **조건에 맞는 요소를 찾아** 카운트/제거/변환.

### 표준 템플릿 — 조건 카운트

```java
public static int countPositive(ArrayList<Integer> list) {
    int count = 0;
    for (int i = 0; i < list.size(); i++) {
        if (list.get(i) > 0) count++;
    }
    return count;
}
```

### 표준 템플릿 — 조건 필터링 (제거)

```java
public static void removeNegative(ArrayList<Integer> list) {
    for (int i = list.size() - 1; i >= 0; i--) {   // 뒤에서 앞으로
        if (list.get(i) < 0) list.remove(i);
    }
}
```

### 표준 템플릿 — 조건 변환

```java
public static ArrayList<Integer> doublePositive(ArrayList<Integer> list) {
    ArrayList<Integer> result = new ArrayList<>();
    for (int i = 0; i < list.size(); i++) {
        int v = list.get(i);
        if (v > 0) result.add(v * 2);
    }
    return result;
}
```

### 체크리스트

- [ ] 제거 시 **뒤에서 앞으로** 또는 `i--`
- [ ] Enhanced for + remove **금지** (CME)
- [ ] `.contains()`, `.isEmpty()`, `.clear()` 등 QR 외 메서드 **사용 금지**
- [ ] 반환 타입 정확
- [ ] 빈 리스트 처리

---

## DD4.26 FRQ Q4 (2D Array) 템플릿 — 매년 출제 형식

### 형식

> 주어진 2D 배열에서 **조건 검색, 값 계산, 행/열 처리**.

### 표준 템플릿 — 전체 합

```java
public static int sum(int[][] grid) {
    int total = 0;
    for (int r = 0; r < grid.length; r++) {
        for (int c = 0; c < grid[0].length; c++) {
            total += grid[r][c];
        }
    }
    return total;
}
```

### 표준 템플릿 — 특정 조건 개수

```java
public static int countAbove(int[][] grid, int threshold) {
    int count = 0;
    for (int r = 0; r < grid.length; r++) {
        for (int c = 0; c < grid[0].length; c++) {
            if (grid[r][c] > threshold) count++;
        }
    }
    return count;
}
```

### 표준 템플릿 — 최댓값 위치

```java
public static int[] findMax(int[][] grid) {
    int maxR = 0, maxC = 0;
    for (int r = 0; r < grid.length; r++) {
        for (int c = 0; c < grid[0].length; c++) {
            if (grid[r][c] > grid[maxR][maxC]) {
                maxR = r;
                maxC = c;
            }
        }
    }
    return new int[]{maxR, maxC};
}
```

### 표준 템플릿 — 행 합

```java
public static int rowSum(int[][] grid, int row) {
    int sum = 0;
    for (int c = 0; c < grid[0].length; c++) {
        sum += grid[row][c];
    }
    return sum;
}
```

### 표준 템플릿 — 열 합

```java
public static int colSum(int[][] grid, int col) {
    int sum = 0;
    for (int r = 0; r < grid.length; r++) {
        sum += grid[r][col];
    }
    return sum;
}
```

### 체크리스트

- [ ] `grid.length` = 행, `grid[0].length` = 열 (혼동 주의)
- [ ] 중첩 for의 **외부가 row**이면 row-major
- [ ] 직사각형 가정 (AP 범위)
- [ ] 빈 grid, 1×n grid 등 엣지 처리

---

## 부록 Ω: 횡단 원리 — "참조 복사" 하나로 5맥락 통합

Unit 1-4 전체에서 가장 많이 재등장하는 개념이 **"reference를 복사할 때 객체는 공유된다"** 원리다. 이 하나의 원리가 **다섯 가지 다른 시험 유형**으로 나타난다. 학생이 이 통합을 체화하면 새로운 변형에도 "이 유형이네" 하고 즉답 가능.

### 원리 (한 줄)

> **Java에서 참조 타입 변수에 `=`로 대입하면 객체 자체가 아니라 주소(참조)만 복사된다. 두 변수는 같은 객체를 공유하며, 한쪽을 통한 변경은 다른 쪽에도 보인다.**

### 다섯 맥락

| # | 맥락 | DD | 증상 |
|---|-----|-----|-----|
| 1 | **Aliasing (직접 대입)** | DD1.2 | `int[] b = a; b[0] = 9;` 하면 `a[0]`도 9 |
| 2 | **메서드 매개변수 (pass-by-value지만)** | DD3.9 | 메서드 안에서 객체 필드/원소 변경 → 호출자에게 반영 |
| 3 | **생성자/getter의 저장·반환** | DD3.10, DD3.18 | this.field = param 또는 return field 그대로 하면 외부와 내부 공유 |
| 4 | **Enhanced for의 객체 원소** | DD4.5 | `for (Point p : arr)` 안에서 `p.setX(0)`은 반영, `p = new...`는 반영 안 됨 |
| 5 | **ArrayList 삭제 중 순회** | DD4.13 | remove로 인덱스가 shift → 같은 리스트를 두 방식으로 참조하다 충돌 (ConcurrentModificationException)|

### 단일 원리로 통합

다섯 경우 모두 "같은 객체를 가리키는 두 참조가 생긴 상태에서, 어느 한쪽을 통한 **변경**이 다른 쪽에서도 보인다"가 본질. 변경의 주체(메서드, 외부 변수, 루프 변수, 반환값 사용자)만 바뀔 뿐 **메커니즘은 동일**.

### 사고 흐름도 — "이 코드 실행 후 원본은 바뀌나?"

```
Q1. 참조 타입인가? (int/double/boolean이면 → 바뀌지 않음, 종료)
    YES → Q2

Q2. 객체 자체가 immutable인가? (String, Integer, Double이면 → 바뀌지 않음, 종료)
    NO → Q3

Q3. 해당 참조를 통해 "재대입"만 했는가? (p = new X)
    YES → 원본 바뀌지 않음 (DD3.9 swap 예와 같음)
    NO → Q4

Q4. 참조를 통해 "객체 내부 상태 변경"을 했는가? (p.setX, arr[0] = 9, list.add)
    YES → 원본 **바뀐다**
```

### 대표 시험 유형 5가지

#### 유형 A — aliasing (DD1.2)
```java
int[] a = {1, 2, 3};
int[] b = a;
b[0] = 9;
// a[0]? → 9
```

#### 유형 B — 메서드 변경 (DD3.9)
```java
public static void fill(int[] arr) {
    for (int i = 0; i < arr.length; i++) arr[i] = 0;
}
int[] x = {5, 5, 5};
fill(x);
// x? → {0, 0, 0}
```

#### 유형 C — getter 구멍 (DD3.18)
```java
public class Box {
    private ArrayList<Integer> list = new ArrayList<>();
    public ArrayList<Integer> getList() { return list; }
}
Box b = new Box();
b.getList().add(99);
// b 내부 list? → [99] (외부가 수정했지만 내부에 반영)
```

#### 유형 D — enhanced for 객체 변경 (DD4.5)
```java
Point[] arr = { new Point(1,1), new Point(2,2) };
for (Point p : arr) {
    p.setX(0);
}
// arr[0].getX()? → 0
```

#### 유형 E — 2D 배열 행 공유 (DD4.14 확장)
```java
int[] row = {1, 2, 3};
int[][] grid = new int[3][];
grid[0] = row;
grid[1] = row;   // 같은 행 두 번 참조
grid[0][0] = 99;
// grid[1][0]? → 99 (같은 행 공유!)
```

### 시험 체화 공식

> **"참조 대입 = 주소 복사 = 같은 객체 공유 = 한쪽 변경이 다른 쪽에도 보임"**

이 공식 한 문장이 Unit 1-4 전 범위에 걸친 "참조 관련" MCQ·FRQ 트레이싱 문제의 **공통 답 생성기**.

---

## 부록 A: Unit 4 시험 빈출 Top 10

1. FRQ Q3 ArrayList 조건 처리 (5점)
2. FRQ Q4 2D Array 처리 (6점)
3. 삭제 중 인덱스 shift 트레이싱 (13)
4. Selection/Insertion/Merge sort 중간 상태 (20, 21, 22)
5. Linear/Binary search 트레이싱 (18, 19)
6. 재귀 함수 결과·호출 횟수 (23)
7. Enhanced for 값 복사 함정 (5)
8. `arr.length` vs `arr[0].length` 혼동 (15)
9. ArrayList 메서드 반환값 (12)
10. File 읽기 관용 (`throws`, `Scanner(File)`) (9)

---

## 부록 B: Unit 4 **코드 작성 허용 규칙** 최종 요약

### 허용 (작성 OK)

- 1D, 2D 배열 생성·순회·수정
- ArrayList 6개 메서드 사용
- Linear search, Binary search (iterative)
- Selection sort, Insertion sort (iterative)
- File Scanner 읽기

### 추적만 (작성 금지)

- **재귀 메서드** 전체 (4.16 EXCLUSION)
- Merge sort (재귀 기반)
- Recursive binary search

### 전면 금지 (EXCLUSION)

- Bubble sort, Quick sort 등 SI/Merge 외 정렬
- 선형/이진 외 검색
- HashMap, HashSet, LinkedList 등 다른 Collection
- 비직사각형 2D 배열
- Scanner(System.in) 키보드 입력
- ArrayList.contains, isEmpty, clear 등 QR 외 메서드

---

## 검증 — L1 완료 체크리스트

- [x] 1D 배열: 생성·접근·순회·값 복사 함정 (DD4.1-4.8)
- [x] File I/O: throws/Scanner(File) 관용 (DD4.9)
- [x] Wrapper/ArrayList: generic·boxing·메서드·삭제 중 순회 (DD4.10-4.13)
- [x] 2D: 메모리 구조·행열 규칙·row/col-major·enhanced for (DD4.14-4.17)
- [x] 검색: linear/binary — 정확한 경계와 O(log n) 근거 (DD4.18-4.19)
- [x] 정렬: selection/insertion/merge — 불변량·트레이싱·복잡도 (DD4.20-4.22)
- [x] 재귀: call stack 시각화 + EXCLUSION 경계 (DD4.23-4.24)
- [x] FRQ Q3/Q4: 매년 형식별 템플릿 (DD4.25-4.26)
- [x] EXCLUSION 엄수: bubble/quick sort, HashMap, 비직사각형 금지 명시
