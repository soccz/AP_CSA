# TP2: Searching — Linear + Binary 해설집

> **CED 2025-26 토픽**: 4.14 Searching, 4.17.B Recursive Searching
> **답안 분포**: A:2 / B:2 / C:2 / D:2

---

## 정답 요약

| # | 정답 | CED 토픽 | 핵심 |
|---|------|---------|------|
| 1 | **C** `3` | 4.14 — 1D Linear Search | 첫 일치 인덱스 반환 |
| 2 | **A** `2` | 4.14 — ArrayList<String> + `.equals()` | get + equals |
| 3 | **B** `2` | 4.14 — 2D 카운트 | 모든 행 검사 |
| 4 | **D** `5` | 4.14 — Reverse Linear | 끝→앞 순회 |
| 5 | **A** `5` | 4.17.B — Binary Search 인덱스 | (lo+hi)/2, ±1 갱신 |
| 6 | **C** `-3` | 4.17.B — 비교 횟수 (미발견) | 3회 후 -3 반환 |
| 7 | **B** `6` | 4.17.B — 재귀형 Binary | 4회 재귀 호출 |
| 8 | **D** `-1` | 4.17.B — 선행조건 위반 | 비정렬 → 잘못된 결과 |

---

## Section I: 문제별 상세 해설

---

### Q1. 정답: **(C) `3`**

📌 **출제 의도:** 가장 기본적인 **선형 검색** 패턴(처음부터 순회하며 첫 일치 인덱스 반환, 미발견 시 `-1`)을 추적할 수 있는지 테스트.

📎 **연계:** **CED 4.14.A.1**: *"Linear search algorithms are standard algorithms that check each element in order until the desired value is found or all elements in the array or ArrayList have been checked."* AP에서 매년 출제되는 표준 알고리즘.

> **핵심 개념: 선형 검색 골격**
> ```java
> for (int i = 0; i < arr.length; i++) {
>     if (arr[i] == target) return i;
> }
> return -1;
> ```
> - 시간 복잡도: O(n) — 최악의 경우 모든 원소 검사
> - **정렬 불필요** — 어떤 순서의 데이터에도 적용 가능
> - 첫 일치에서 즉시 종료 (`return`은 메서드 즉시 종료, `break`와 무관)

> **선행 지식:**
> - `arr.length` — 배열 크기 (괄호 없음)
> - `==` — primitive 비교 (int끼리)
> - `return` — 메서드 즉시 종료 (CED 3.5.A.4)
> - **`break` 사용 안 함** — CED 본문 미등장. `return`이 표준

**추적 (`target = 4`):**

| i | arr[i] | == 4? | 동작 |
|---|---|---|---|
| 0 | 7 | ✗ | 다음 |
| 1 | 3 | ✗ | 다음 |
| 2 | 9 | ✗ | 다음 |
| 3 | 4 | ✓ | **return 3** |

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `-1` | 일치 못 찾는다고 오해 | arr[3]=4가 정확히 일치, 인덱스 3 반환 |
| (B) `4` | target 값(4) 자체를 반환한다고 착각 | 메서드는 **인덱스**(위치)를 반환 |
| **(C) `3`** ✅ | 정답 | arr[3]에서 첫 일치 → 인덱스 3 |
| (D) `7` | arr.length 또는 첫 원소 값 | 7은 arr[0]이지만 일치값 아님 |

> ⚠️ **함정 1:** **인덱스 vs 값 혼동**. linear search는 **위치**(인덱스)를 반환, 값을 반환하는 게 아님. AP 단골 함정.

> ⚠️ **함정 2:** **`break` 사용 금지**. CED는 `break`/`continue`를 본문에 포함하지 않음. 조기 종료는 항상 `return`(메서드 안) 또는 flag 변수.

> ⚠️ **함정 3:** **정렬 불필요**. linear search는 어떤 순서의 데이터에도 작동. 정렬된 데이터에서는 binary search가 더 효율적이지만 linear도 정상 작동.

> 💡 **꿀팁 1:** **표준 골격 외우기**: `for (int i = 0; i < arr.length; i++) if (arr[i] == target) return i; return -1;`

> 💡 **꿀팁 2:** **String/객체 검색**: `==` 대신 `.equals()` 사용 (Q2 참조). `==`는 참조 비교라 거의 항상 false.

> 💡 **꿀팁 3:** **시간 복잡도**: 평균 O(n/2), 최악 O(n). 큰 정렬 배열에서는 binary가 압도적으로 빠름 (Q5 참조).

---

### Q2. 정답: **(A) `2`**

📌 **출제 의도:** ArrayList 순회 + **String 비교는 `.equals()`** 라는 핵심 규칙을 적용할 수 있는지 테스트. `==`로 String 비교 시 거의 항상 false (참조 비교)인 함정 회피.

📎 **연계:** **CED 4.14.A.1** Linear search는 array 또는 **ArrayList**에 모두 적용. **CED 1.15.B.2** String 메서드: `.equals()` 명시. **CED 2.6.B.3** 객체 비교는 `.equals()`.

> **핵심 개념: ArrayList linear search + .equals()**
> ```java
> for (int i = 0; i < list.size(); i++) {
>     if (list.get(i).equals(target)) return i;
> }
> return -1;
> ```
> - `list.size()` — 원소 개수 (CED 4.8 ArrayList 6대 메서드 중 하나)
> - `list.get(i)` — i번 원소 반환
> - `.equals()` — 내용 비교 (참조 비교 `==`와 다름)

> **선행 지식:**
> - **`list.contains()` 사용 금지** — Quick Reference에 없음 (CED 4.8 명시 6 메서드 외)
> - **`list.indexOf()` 사용 금지** — 동일 이유
> - String은 reference 타입 → `==`는 메모리 주소 비교, `.equals()`만 내용 비교

**추적 (`target = "cherry"`):**

| i | list.get(i) | .equals("cherry")? |
|---|---|---|
| 0 | "apple" | false |
| 1 | "banana" | false |
| 2 | "cherry" | **true** → return 2 |

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `2`** ✅ | 정답 | "cherry"가 인덱스 2 |
| (B) `-1` | `==`로 비교 시 false라 미발견 | 코드는 `.equals()` 사용 — 정확히 작동 |
| (C) `3` | "date" 인덱스로 잘못 추적 | "cherry"는 2, "date"는 3 |
| (D) `1` | "banana" 인덱스 | 0-based라 banana=1 (target 아님) |

> ⚠️ **함정 1:** **`==`로 String 비교 = 거의 항상 false**. AP 단골 함정. 반드시 `.equals()`.

> ⚠️ **함정 2:** **`list.contains()` 사용 금지**. 일견 편리해 보이지만 Java Quick Reference에 없음. AP는 명시적 linear search 코드 출제.

> ⚠️ **함정 3:** **`list.size()` vs `list.length`**. `length`는 array에만 있음 (필드, 괄호 없음). ArrayList는 `size()` 메서드 (괄호 필수).

> 💡 **꿀팁 1:** **공식 ArrayList 6 메서드 (CED 4.8)**: `size`, `add(E)`, `add(int,E)`, `get`, `set`, `remove(int)`. `contains`/`indexOf`는 본 패턴으로 직접 구현.

> 💡 **꿀팁 2:** **String linear search 패턴**: 객체 비교는 항상 `.equals()`. 단, null 체크 필요 (`obj != null && obj.equals(target)`).

> 💡 **꿀팁 3:** **ArrayList vs Array 차이**:
> - Array: `arr[i]`, `arr.length`
> - ArrayList: `list.get(i)`, `list.size()`
> 두 표기 혼용 시 컴파일 에러.

---

### Q3. 정답: **(B) `2`**

📌 **출제 의도:** **2D 배열에서의 선형 검색**(CED 4.14.A.2) — 행을 하나씩 접근한 후 그 행에 linear search 적용. 본 문제는 첫 일치 종료가 아닌 **모든 일치 카운트** 변형.

📎 **연계:** **CED 4.14.A.2**: *"When applying linear search algorithms to 2D arrays, each row must be accessed then linear search applied to each row of the 2D array."* + **CED 4.13** 2D Array Algorithms (count having property).

> **핵심 개념: 2D 선형 검색 패턴**
> ```java
> for (int r = 0; r < grid.length; r++) {
>     for (int c = 0; c < grid[r].length; c++) {
>         // 검사
>     }
> }
> ```
> - 외부 루프 = 행, 내부 루프 = 열
> - 행 단위로 linear search 적용 = 결국 모든 셀 방문
> - 변형: 첫 일치 반환 / 모든 일치 카운트 / 최댓값 등

> **선행 지식:**
> - `grid.length` — 행 수
> - `grid[r].length` — r행의 열 수 (직사각형이면 모든 행 동일)
> - **EXCLUSION (CED 4.11)**: 비직사각형 2D 배열 OUT — 항상 직사각형 가정

**추적 (`target = 5`):**

```
grid:
  c=0  c=1  c=2
r=0:  3    1    4    ← 일치 없음
r=1:  1    5    9    ← (1,1) 일치 → count = 1
r=2:  2    6    5    ← (2,2) 일치 → count = 2
```

| 셀 | 값 | == 5? | count |
|---|---|---|---|
| 시작 | — | — | 0 |
| (0,0) | 3 | ✗ | 0 |
| (0,1) | 1 | ✗ | 0 |
| (0,2) | 4 | ✗ | 0 |
| (1,0) | 1 | ✗ | 0 |
| (1,1) | 5 | ✓ | 1 |
| (1,2) | 9 | ✗ | 1 |
| (2,0) | 2 | ✗ | 1 |
| (2,1) | 6 | ✗ | 1 |
| (2,2) | 5 | ✓ | 2 |

`return 2` → 출력: `2`

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `0` | 5가 grid에 없다고 오해 | grid[1][1]과 grid[2][2]에 정확히 존재 |
| **(B) `2`** ✅ | 정답 | 5가 두 셀에 등장 |
| (C) `1` | 첫 일치 후 종료한다고 오해 | 본 코드는 `return` 안에 없음 — 모든 셀 검사 후 카운트 |
| (D) `3` | 추가 셀을 잘못 카운트 | 정확히 2개만 일치 |

> ⚠️ **함정 1:** **첫 일치 종료 vs 모든 카운트** 구별. 첫 일치 종료는 `if (...) return ...;`, 모든 카운트는 `if (...) count++;` (return 없음).

> ⚠️ **함정 2:** **`grid.length` vs `grid[0].length`**. 행 수와 열 수 혼동 시 인덱스 오류 또는 IndexOutOfBoundsException.

> ⚠️ **함정 3:** **비직사각형 가정 금지**. CED 4.11 EXCLUSION으로 직사각형만 출제. 따라서 `grid[r].length` ≡ `grid[0].length`.

> 💡 **꿀팁 1:** **2D linear search 변형 골격**:
> - 첫 일치: `if (...) return new int[]{r, c};`
> - 모든 카운트: `if (...) count++;`
> - 모든 위치 수집: `if (...) result.add(...);` (ArrayList 사용)

> 💡 **꿀팁 2:** **CED 4.13 표준 알고리즘**: min/max, sum/avg, "count having property", consecutive pairs, duplicates 검사 — 모두 2D 순회 + 조건 검사 패턴.

> 💡 **꿀팁 3:** **row-major vs column-major**: 본 코드는 row-major (외부 = 행). column-major는 외부 = 열, 내부 = 행. AP에서 둘 다 출제 가능.

---

### Q4. 정답: **(D) `5`**

📌 **출제 의도:** **역방향 선형 검색**(CED 4.14.A.1: *"begin the search process from either end"*)을 추적하면서, 마지막 인덱스부터 시작해 첫 일치를 찾는 동작을 이해할 수 있는지 테스트.

📎 **연계:** **CED 4.14.A.1** 명시: linear search는 **양 끝 어느 쪽에서든** 시작 가능. 정방향과 역방향은 일치값이 여러 개일 때 결과가 다를 수 있음.

> **핵심 개념: 역방향 선형 검색**
> ```java
> for (int i = arr.length - 1; i >= 0; i--) {
>     if (arr[i] == target) return i;
> }
> return -1;
> ```
> - 시작: `arr.length - 1` (마지막 인덱스)
> - 종료: `i >= 0` (0 포함)
> - 감소: `i--`
> - **여러 일치 중 가장 큰 인덱스** 반환 (정방향과 반대)

> **선행 지식:**
> - 역방향 for 루프: `i = N-1; i >= 0; i--`
> - target = 5, 일치 위치: 인덱스 1, 3, 5
> - 역방향이면 i=5가 먼저 발견 → return 5

**추적 (`target = 5`, arr = {2, 5, 8, 5, 3, 5, 1}):**

| i | arr[i] | == 5? | 동작 |
|---|---|---|---|
| 6 | 1 | ✗ | 다음 |
| 5 | 5 | ✓ | **return 5** |

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `1` | 정방향 검색으로 잘못 추적 (첫 5는 인덱스 1) | 본 코드는 **역방향** — 마지막 일치(5)를 먼저 찾음 |
| (B) `3` | 중간 일치만 본 경우 | 가장 큰 인덱스(5)부터 검사 → 즉시 반환 |
| (C) `-1` | 일치 없다고 오해 | 5가 여러 위치에 존재 |
| **(D) `5`** ✅ | 정답 | 역방향 검색에서 i=5가 첫 일치 |

> ⚠️ **함정 1:** **방향 무시**. 정방향이라고 가정하면 답이 1. 코드의 `i = arr.length - 1; i >= 0; i--` 부분을 정확히 읽어야 함.

> ⚠️ **함정 2:** **종료 조건 `i >= 0`**. `i > 0`으로 잘못 쓰면 인덱스 0 검사 안 함 → 만약 일치값이 인덱스 0에만 있으면 -1 반환 (버그).

> ⚠️ **함정 3:** **역방향 시작점**. `arr.length`가 아닌 `arr.length - 1`. `arr.length`로 시작하면 IndexOutOfBoundsException.

> 💡 **꿀팁 1:** **언제 역방향 선형 검색?**: "마지막 일치 찾기", "역순 처리 (스택 같은 LIFO)", "끝쪽 데이터가 자주 검색될 때" 등.

> 💡 **꿀팁 2:** **표준 역방향 패턴**: `for (int i = arr.length - 1; i >= 0; i--)`. 이 관용구를 외우면 다양한 변형(역순 출력, 역순 누적 등)에 응용 가능.

> 💡 **꿀팁 3:** **여러 일치값 처리**: 정방향 = 첫 일치 (가장 작은 인덱스), 역방향 = 마지막 일치 (가장 큰 인덱스). 사양에 따라 선택.

---

### Q5. 정답: **(A) `5`**

📌 **출제 의도:** **반복형 이진 검색**의 한 사이클(`mid` 계산 → 비교 → 절반 제거)을 정확히 추적할 수 있는지 테스트. CED 4.17.B.3: 반복/재귀 모두 IN.

📎 **연계:** **CED 4.17.B.1**: *"Data must be in sorted order to use the binary search algorithm. Binary search starts at the middle of a sorted array or ArrayList and eliminates half of the array or ArrayList in each recursive call until the desired value is found or all elements have been eliminated."*

> **핵심 개념: Binary Search 한 사이클**
> 1. `mid = (lo + hi) / 2` — 정수 나눗셈
> 2. `arr[mid] == target` → 찾음, 종료
> 3. `arr[mid] < target` → target은 오른쪽 → `lo = mid + 1`
> 4. `arr[mid] > target` → target은 왼쪽 → `hi = mid - 1`
> 5. `lo > hi` → 종료, `return -1`

> **선행 지식:**
> - **선행조건**: 배열 **반드시 정렬** (Q8 함정 참조)
> - 시간 복잡도: O(log n) — 매 사이클마다 절반 제거
> - **±1 갱신 필수**: `lo = mid + 1`, `hi = mid - 1` (mid는 이미 검사)
> - **`Math.max/min` 사용 금지** — Quick Reference에 없음 (본 코드는 정상)

**추적 (`target = 11`, arr = {1, 3, 5, 7, 9, 11, 13}):**

| 반복 | lo | hi | mid | arr[mid] | 비교 | 갱신 |
|---|---|---|---|---|---|---|
| 시작 | 0 | 6 | — | — | — | — |
| 1 | 0 | 6 | (0+6)/2 = 3 | 7 | 7<11 | lo = 4 |
| 2 | 4 | 6 | (4+6)/2 = 5 | 11 | **11==11** | **return 5** |

`println(5)` → 출력: `5`

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `5`** ✅ | 정답 | arr[5] = 11에서 일치 → 인덱스 5 |
| (B) `4` | mid 계산 실수 (`(4+6)/2 = 5`인데 4로 잘못 추측) | 정수 나눗셈으로 5 |
| (C) `11` | target 값(11) 자체를 반환한다고 오해 | 인덱스 반환 (5) |
| (D) `-1` | binary search가 11을 못 찾는다고 오해 | 정렬된 배열 + 11 존재 → 정확히 발견 |

> ⚠️ **함정 1:** **인덱스 vs 값 혼동**. linear search Q1과 동일 함정. binary search도 **위치**(인덱스) 반환.

> ⚠️ **함정 2:** **mid 계산 정수 나눗셈**. `(0+6)/2 = 3`, `(4+6)/2 = 5`. 부동소수점 아님.

> ⚠️ **함정 3:** **±1 갱신 누락**. `lo = mid` (±1 없이)로 쓰면 무한 루프 위험. 본 코드는 정확히 ±1 적용.

> 💡 **꿀팁 1:** **표준 binary search 골격 (반복형)**:
> ```java
> int lo = 0, hi = arr.length - 1;
> while (lo <= hi) {
>     int mid = (lo + hi) / 2;
>     if (arr[mid] == target) return mid;
>     else if (arr[mid] < target) lo = mid + 1;
>     else hi = mid - 1;
> }
> return -1;
> ```

> 💡 **꿀팁 2:** **시간 복잡도 직관**: n=7원소 → 최대 3회 (log₂8 = 3). n=1024 → 10회. linear search(최대 1024)와 비교 압도적.

> 💡 **꿀팁 3:** **CED 4.17.B.2**: *"Binary search is typically more efficient than linear search."* 출제 가능 개념 문제.

---

### Q6. 정답: **(C) `-3`**

📌 **출제 의도:** Binary search의 **미발견 케이스 trace** + 비교 횟수 추적. `lo > hi`가 되어 루프 종료될 때까지의 **사이클 수**를 셀 수 있는지 테스트.

📎 **연계:** **CED 4.17.B.1** "all elements have been eliminated" — 미발견 시 종료. **CED 2.12 Informal Run-Time Analysis** (statement execution count)와 결합.

> **핵심 개념: 미발견 케이스의 종료 조건**
> - 매 사이클마다 `lo` 또는 `hi` 갱신
> - `lo > hi` 되면 검색 범위 비어 종료
> - 각 사이클에서 `mid` 한 번 비교 → 비교 횟수 = 사이클 수
> - 본 문제: 양수 = 발견 시 횟수, 음수 = 미발견 시 음의 횟수

**추적 (`target = 6`, arr = {1, 3, 5, 7, 9, 11, 13}):**

| 반복 | lo | hi | mid | arr[mid] | 비교 | steps | 갱신 |
|---|---|---|---|---|---|---|---|
| 시작 | 0 | 6 | — | — | — | 0 | — |
| 1 | 0 | 6 | 3 | 7 | 7>6 | **1** | hi = 2 |
| 2 | 0 | 2 | 1 | 3 | 3<6 | **2** | lo = 2 |
| 3 | 2 | 2 | 2 | 5 | 5<6 | **3** | lo = 3 |
| 종료 | 3 | 2 | — | — | lo>hi | — | exit |

`return -steps = -3` → 출력: `-3`

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `-1` | 표준 binary search의 미발견 반환값 `-1`이라 오해 | 본 코드는 **음수 횟수** 반환 (수정된 binary search) |
| (B) `3` | 비교 횟수만 본 경우 (음수 부호 빠뜨림) | 미발견이라 음수 부호 적용: `-3` |
| **(C) `-3`** ✅ | 정답 | 3 사이클 후 미발견 → -3 |
| (D) `0` | 루프 한 번도 안 돈다고 오해 | lo=0, hi=6으로 시작 → 정상 진입 |

> ⚠️ **함정 1:** **비교 횟수 = 사이클 수 = `mid` 평가 횟수**. 본 코드 `steps++`이 매 사이클 처음에 위치 → 정확히 사이클 수.

> ⚠️ **함정 2:** **미발견 종료 조건 `lo > hi`**. while 조건은 `lo <= hi`. 마지막 검사에서 `lo` 또는 `hi`가 갱신되어 `lo > hi`가 되면 종료.

> ⚠️ **함정 3:** **부호 빠뜨림**. 발견 시 양수, 미발견 시 음수. (B) 3은 부호 빠뜨린 흔한 실수.

> 💡 **꿀팁 1:** **검산 — 절반 제거 추적**: 7원소 → mid=3 → 3원소(0~2 또는 4~6) → mid=1 또는 5 → 1원소 → mid → 0원소. 미발견은 보통 `⌈log₂(n+1)⌉` 비교.

> 💡 **꿀팁 2:** **이런 변형 패턴**: 발견/미발견 정보를 **하나의 반환값**에 인코딩 (음수=미발견, 양수=발견 인덱스 등). AP 시험에 종종 등장.

> 💡 **꿀팁 3:** **비교 횟수 vs 인덱스**: 본 코드는 횟수 반환. 인덱스 반환하려면 `return mid` (Q5 골격). 두 변형 모두 binary search 표준 응용.

---

### Q7. 정답: **(B) `6`**

📌 **출제 의도:** **재귀형 binary search**(CED 4.17.B.3 명시 IN-스코프)를 추적할 수 있는지 테스트. 재귀 호출 트리를 정확히 펼쳐 base case 도달까지 추적.

📎 **연계:** **CED 4.17.B.3**: *"The binary search algorithm can be written either iteratively or recursively."* + **CED 4.16** Recursion (트레이싱만 IN, 작성 OUT — 본 문제는 주어진 코드의 트레이싱).

> **핵심 개념: 재귀형 binary search**
> ```java
> if (lo > hi) return -1;       // base: 미발견
> int mid = (lo + hi) / 2;
> if (arr[mid] == target) return mid;
> if (arr[mid] < target)
>     return bSearch(arr, target, mid + 1, hi);   // 우측 재귀
> return bSearch(arr, target, lo, mid - 1);       // 좌측 재귀
> ```
> - 반복형과 동일 로직, 매개변수로 `lo`/`hi` 전달
> - 발견 시 `mid` 반환, 미발견 시 `-1` 반환
> - 호출 깊이 = 비교 횟수

> **선행 지식:**
> - 재귀 호출은 **자체 local variable**(lo, hi, mid) 보유 (CED 4.16.A.2)
> - **CED 4.16 EXCLUSION**: writing recursive code OUT, **트레이싱은 IN**
> - 본 문제는 주어진 코드의 결과 추적 → 정상 출제 범위

**추적 (`target = 14`, arr = {2, 4, 6, 8, 10, 12, 14, 16, 18, 20}):**

```
bSearch(arr, 14, 0, 9):
  mid = (0+9)/2 = 4, arr[4] = 10
  10 < 14 → return bSearch(arr, 14, 5, 9)

  bSearch(arr, 14, 5, 9):
    mid = (5+9)/2 = 7, arr[7] = 16
    16 > 14 → return bSearch(arr, 14, 5, 6)

    bSearch(arr, 14, 5, 6):
      mid = (5+6)/2 = 5, arr[5] = 12
      12 < 14 → return bSearch(arr, 14, 6, 6)

      bSearch(arr, 14, 6, 6):
        mid = (6+6)/2 = 6, arr[6] = 14
        14 == 14 → return 6  ✓
```

각 재귀 호출이 호출자에게 6을 그대로 반환 → 최종 6.

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `14` | target 값 자체 반환이라 오해 | 인덱스 반환 (6) |
| **(B) `6`** ✅ | 정답 | arr[6] = 14에서 발견 → 인덱스 6 |
| (C) `-1` | base case의 `-1` 반환이라 오해 | 발견되었으므로 mid 반환 |
| (D) `7` | 추적 중간의 mid (7) 값 혼동 | 최종 발견 위치는 6, 7은 중간 단계 |

> ⚠️ **함정 1:** **반환값 전파**. 재귀 호출의 반환값이 호출자의 반환값이 됨 (`return bSearch(...)`). base case의 값이 위로 전달됨.

> ⚠️ **함정 2:** **base case 위치**. `if (lo > hi) return -1;`이 함수 맨 위. 잊으면 무한 재귀 → StackOverflowError.

> ⚠️ **함정 3:** **재귀 vs 반복 동일성**. CED 4.17.B.3 명시: 두 형태는 **결과 동일**. 코드 형태만 다름. 본 문제는 재귀형이지만 결과는 반복형 binary search와 같음.

> 💡 **꿀팁 1:** **재귀 트리 그리기**: 위에서 아래로 들여쓰기로 호출 stack 표시. base case 도달 후 unwinding. AP 시험 정석 추적법.

> 💡 **꿀팁 2:** **CED 4.16 EXCLUSION 재확인**: 재귀 코드 **작성**은 OUT이지만 **트레이싱은 IN**. AP MCQ에서 재귀 코드 주고 결과 묻는 문제는 정상.

> 💡 **꿀팁 3:** **recursive vs iterative 선택**:
> - 재귀: 코드 짧고 읽기 쉬움
> - 반복: 메모리 효율 (스택 프레임 없음)
> - AP는 둘 다 출제 → 두 형태 모두 트레이싱 가능해야 함

---

### Q8. 정답: **(D) `-1`**

📌 **출제 의도:** Binary search의 **선행조건 위반** 시 어떤 결과가 나오는지 이해. CED 4.17.B.1 명시: *"Data must be in sorted order to use the binary search algorithm."* — 위반 시 잘못된 결과 (오답이지만 예외는 아님).

📎 **연계:** **CED 4.17.B.1** 선행조건 + **CED 1.8** precondition 개념. AP에서 알고리즘의 precondition 위반 시 결과를 묻는 문제는 단골.

> **핵심 개념: 선행조건 위반의 결과**
> - Binary search는 **정렬 가정** 하에 절반 제거를 정당화
> - 비정렬 배열에 적용하면 **검색 범위가 잘못 좁혀짐**
> - 결과: 값이 존재해도 **`-1`** 반환 (또는 잘못된 인덱스 반환)
> - **예외(Exception)는 발생하지 않음** — 그냥 "잘못된" 결과
> - "입력이 잘못되어 결과도 잘못된" 케이스 (Garbage in, garbage out)

> **선행 지식:**
> - precondition (CED 1.8.A.2): 메서드가 의도대로 동작하기 위해 만족해야 할 조건
> - precondition 미체크 → 메서드 책임 아님 → 호출자 책임
> - binary search precondition: "정렬된 배열"

**추적 (`target = 9`, arr = {5, 3, 8, 1, 9, 6, 2} — NOT sorted):**

| 반복 | lo | hi | mid | arr[mid] | 비교 | 갱신 |
|---|---|---|---|---|---|---|
| 시작 | 0 | 6 | — | — | — | — |
| 1 | 0 | 6 | 3 | 1 | 1<9 | lo = 4 |
| 2 | 4 | 6 | 5 | 6 | 6<9 | lo = 6 |
| 3 | 6 | 6 | 6 | 2 | 2<9 | lo = 7 |
| 종료 | 7 | 6 | — | — | lo>hi | exit, return -1 |

**중요**: 9는 인덱스 4에 **실제로 존재**하지만, 비정렬이라 검색 경로가 9를 만나지 못하고 종료 → `-1` 반환.

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `4` | 9의 실제 위치(인덱스 4)를 반환한다고 오해 | binary search는 그 위치를 발견 못함 (비정렬) |
| (B) `9` | target 값(9) 자체 반환이라 오해 | 인덱스를 반환, 또한 미발견 |
| (C) Compile error | 비정렬이면 컴파일러가 거부한다고 오해 | 컴파일러는 sortedness 검증 안 함. precondition은 **프로그래머의 책임** |
| **(D) `-1`** ✅ | 정답 | 비정렬이라 9를 만나지 못하고 lo > hi 도달 → -1 |

> ⚠️ **함정 1:** **컴파일러는 precondition 검증 안 함**. "정렬되어야 함"은 메서드 명세에 적힌 약속일 뿐. 위반 시 결과만 잘못됨, 컴파일/런타임 에러 없음.

> ⚠️ **함정 2:** **"값이 존재 = 반환된다"는 가정**. 비정렬이면 binary search가 값을 못 찾을 수 있음. linear search와 다른 점.

> ⚠️ **함정 3:** **다른 입력에서는 다른 결과**. 비정렬 배열 + binary search 조합은 **결정적이지 않음** — 입력 순서에 따라 다른 잘못된 결과 가능. 항상 -1 보장 안 됨.

> 💡 **꿀팁 1:** **CED 4.17.B.1 인용 외우기**: *"Data must be in sorted order to use the binary search algorithm."* AP 개념 문제 단골.

> 💡 **꿀팁 2:** **precondition 검사**: "내가 호출 전에 보장해야 함"이 precondition. 호출 후 보장은 postcondition. 비유: 자판기에 동전 넣고 버튼 누르기 전 = precondition, 음료 나오는 것 = postcondition.

> 💡 **꿀팁 3:** **Linear vs Binary 선택**:
> - Linear: 정렬 무관, 어떤 데이터든 OK, O(n)
> - Binary: 정렬 필수, O(log n)
> - 비정렬 데이터 → linear 사용 (또는 정렬 후 binary)

---

## 종합 정리

### 4.14 Linear Search 핵심 골격
```java
// 1D
for (int i = 0; i < arr.length; i++) {
    if (arr[i] == target) return i;
}
return -1;

// ArrayList<String> (.equals 사용)
for (int i = 0; i < list.size(); i++) {
    if (list.get(i).equals(target)) return i;
}
return -1;

// 2D (행별 적용)
for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[r].length; c++) {
        if (grid[r][c] == target) /* 처리 */;
    }
}

// 역방향
for (int i = arr.length - 1; i >= 0; i--) {
    if (arr[i] == target) return i;
}
return -1;
```

### 4.17.B Binary Search 핵심 골격
```java
// 반복형
int lo = 0, hi = arr.length - 1;
while (lo <= hi) {
    int mid = (lo + hi) / 2;
    if (arr[mid] == target) return mid;
    else if (arr[mid] < target) lo = mid + 1;
    else hi = mid - 1;
}
return -1;

// 재귀형
public static int bSearch(int[] arr, int t, int lo, int hi) {
    if (lo > hi) return -1;
    int mid = (lo + hi) / 2;
    if (arr[mid] == t) return mid;
    if (arr[mid] < t) return bSearch(arr, t, mid + 1, hi);
    return bSearch(arr, t, lo, mid - 1);
}
```

### 흔한 함정 모음
1. **인덱스 vs 값 혼동** (Q1, Q5, Q7): linear/binary search 모두 **인덱스** 반환
2. **String 비교 `==` 사용** (Q2): 반드시 `.equals()`
3. **정방향 vs 역방향 혼동** (Q4): 시작 인덱스로 판별
4. **mid 계산 정수 나눗셈** (Q5, Q7): `(lo+hi)/2`는 정수
5. **±1 갱신 필수** (Q5, Q6, Q7): `lo = mid + 1`, `hi = mid - 1` (그렇지 않으면 무한 루프)
6. **선행조건 위반의 결과** (Q8): 비정렬 + binary = 잘못된 결과 (예외 아님)

### EXCLUSION 재확인
- **`break`/`continue` 미사용** ✓ — 본 코드들 모두 `return`만 사용
- **`Math.min/max` 미사용** ✓ — `if` 비교만 사용
- **`ArrayList.contains/indexOf` 미사용** ✓ — 명시적 linear search 코드
- **Linear/Binary 외 검색 OUT** (CED 4.17.B.2) ✓ — 본 세트는 두 알고리즘만
