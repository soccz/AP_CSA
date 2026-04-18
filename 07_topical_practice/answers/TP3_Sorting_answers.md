# TP3: Sorting — Selection, Insertion, Merge 해설집

> **CED 2025-26 토픽**: 4.15 Sorting (Selection/Insertion), 4.17.C Merge Sort
> **답안 분포**: A:3 / B:2 / C:3 / D:2

---

## 정답 요약

| # | 정답 | CED 토픽 | 핵심 |
|---|------|---------|------|
| 1 | **D** `{1, 3, 8, 5, 9, 6}` | 4.15.A.2 Selection 부분 진행 | 2 pass 후 |
| 2 | **B** `10` | 4.15 + 2.12 비교 횟수 | n(n-1)/2 = 5·4/2 |
| 3 | **C** `3` | 4.15 swap 횟수 | self-swap 회피 |
| 4 | **A** `{2, 4, 5, 6, 1, 3}` | 4.15.A.3 Insertion 부분 진행 | 3 pass 후 |
| 5 | **C** `3` | 4.15 shift 횟수 | inner while 동작 |
| 6 | **A** `0` | 4.15 best case | 정렬된 입력 → shift 0 |
| 7 | **C** `7` | 4.17.C 재귀 호출 수 | 1+2+4 |
| 8 | **B** `{1, 2, 4, 5, 7, 8}` | 4.17.C merge 단계 | 두 정렬 결합 |
| 9 | **A** `4` | 4.17.C 재귀 깊이 | log₂8 + 1 |
| 10 | **D** Insertion sort | 4.15 + 4.17.C 비교 | nearly-sorted O(n) |

---

## Section I: 문제별 상세 해설

---

### Q1. 정답: **(D) `{1, 3, 8, 5, 9, 6}`**

📌 **출제 의도:** **선택 정렬의 한 외부 반복 = "한 단계 진행"** 의미를 정확히 추적할 수 있는지 테스트. 핵심: (1) 매 외부 반복에서 미정렬 부분의 최솟값을 찾고 (2) 정렬 부분의 다음 자리(`i`)와 swap, (3) **정렬되는 것은 왼쪽부터 한 칸씩만**.

📎 **연계:** **CED 4.15.A.2**: *"Selection sort repeatedly selects the smallest (or largest) element from the unsorted portion of the list and swaps it into its correct (and final) position in the sorted portion of the list."*

> **핵심 개념: Selection Sort의 한 외부 반복(pass i)**
> 1. 미정렬 부분 `arr[i..length-1]`에서 **최솟값 인덱스 `minIdx`** 찾기
> 2. `arr[i]`와 `arr[minIdx]` swap (본 코드는 `minIdx == i`여도 실행되어 self-swap)
> 3. 결과: `arr[0..i]` 정렬 완료
>
> 외부 루프 `n-1`번이면 전체 정렬 끝.

> **선행 지식:**
> - **`Math.min` 사용 금지** — Quick Reference에 없음. `if (arr[j] < arr[minIdx]) minIdx = j;`로 직접 구현.
> - 매 pass 비교 횟수: `n-1, n-2, ..., 1` (Q2 참조)
> - swap 표준 관용구: `int t = arr[i]; arr[i] = arr[minIdx]; arr[minIdx] = t;`

**Pass-by-pass 추적 (`arr = {5, 3, 8, 1, 9, 6}`, 외부 2회):**

**Pass 1 (i=0):** 미정렬 = arr[0..5]

| j | arr[j] | arr[minIdx] | minIdx 갱신? |
|---|---|---|---|
| 시작 | — | — | minIdx=0 (arr[0]=5) |
| 1 | 3 | 5 | minIdx ← 1 (3<5) |
| 2 | 8 | 3 | 그대로 (8>3) |
| 3 | 1 | 3 | minIdx ← 3 (1<3) |
| 4 | 9 | 1 | 그대로 |
| 5 | 6 | 1 | 그대로 |

→ swap arr[0]↔arr[3]: `{5,3,8,1,9,6}` → **`{1, 3, 8, 5, 9, 6}`**

**Pass 2 (i=1):** 미정렬 = arr[1..5] = {3, 8, 5, 9, 6}

| j | arr[j] | arr[minIdx] | minIdx 갱신? |
|---|---|---|---|
| 시작 | — | — | minIdx=1 (arr[1]=3) |
| 2 | 8 | 3 | 그대로 |
| 3 | 5 | 3 | 그대로 |
| 4 | 9 | 3 | 그대로 |
| 5 | 6 | 3 | 그대로 |

→ swap arr[1]↔arr[1] (self-swap, 변화 없음): **`{1, 3, 8, 5, 9, 6}`**

**최종 (외부 2회 후): `{1, 3, 8, 5, 9, 6}`** ✓

**참고 — 모든 pass 진행 시:**

| pass | 후 arr 상태 |
|---|---|
| Pass 1 (i=0) | `{1, 3, 8, 5, 9, 6}` |
| Pass 2 (i=1) | `{1, 3, 8, 5, 9, 6}` ← **본 문제 정답** |
| Pass 3 (i=2) | `{1, 3, 5, 8, 9, 6}` ← (B) |
| Pass 4 (i=3) | `{1, 3, 5, 6, 9, 8}` |
| Pass 5 (i=4) | `{1, 3, 5, 6, 8, 9}` ← (A) 완전 정렬 |

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `{1, 3, 5, 6, 8, 9}` | 완전 정렬 | 외부 5회 모두 진행. 본 문제는 2회만 |
| (B) `{1, 3, 5, 8, 9, 6}` | 3 pass 후 | 한 pass 더 진행 (i=2까지) |
| (C) `{3, 1, 8, 5, 9, 6}` | 첫 swap 잘못 | 인접 swap (bubble처럼) — selection은 minIdx와 i swap |
| **(D) `{1, 3, 8, 5, 9, 6}`** ✅ | 정답 | Pass 1: 1→앞, Pass 2: self-swap (변화 없음) |

> ⚠️ **함정 1:** **"정렬 코드 = 완전 정렬 결과"** 단축 추론. 본 문제는 부분 진행. pass 단위로 끊어 추적 필요.

> ⚠️ **함정 2:** **Self-swap**. minIdx == i면 swap 실행되지만 결과 변화 없음. 가드(`if minIdx != i`) 없는 본 코드도 정상 동작.

> ⚠️ **함정 3:** **Selection ≠ Bubble**. Selection은 한 pass에 한 번 swap (minIdx와 i). Bubble은 인접 비교 + 다회 swap. **Bubble sort는 CED 4.17.C EXCLUSION**으로 출제 안 됨.

> 💡 **꿀팁 1:** **k pass 후 상태**: `arr[0..k-1]` 정렬 완료, `arr[k..n-1]` 미정렬.

> 💡 **꿀팁 2:** **Selection sort 일반 패턴**: "미정렬 부분에서 min/max 찾기 + i 자리와 swap". `n-1` pass면 충분.

> 💡 **꿀팁 3:** **CED 4.15 vs 4.17 정렬 구분**:
> - 4.15 (반복형): Selection, Insertion
> - 4.17.C (재귀형): Merge sort
> - **OUT**: bubble, quick, heap 등

---

### Q2. 정답: **(B) `10`**

📌 **출제 의도:** Selection sort의 **비교 횟수 공식** `n(n-1)/2`를 trace로 도출할 수 있는지 테스트. CED 2.12 Informal Run-Time Analysis (statement execution count)와 결합.

📎 **연계:** **CED 2.12.A.1**: *"A statement execution count indicates the number of times a statement is executed by the program. Statement execution counts are often calculated informally through tracing and analysis of the iterative statements."*

> **핵심 개념: Selection sort 비교 횟수**
> ```
> 외부 i = 0: inner j = 1, 2, ..., n-1 → (n-1) 비교
> 외부 i = 1: inner j = 2, 3, ..., n-1 → (n-2) 비교
> ...
> 외부 i = n-2: inner j = n-1 → 1 비교
>
> 총 비교 = (n-1) + (n-2) + ... + 1 = n(n-1)/2
> ```
> n=5: 5·4/2 = **10**
>
> 입력에 무관하게 **항상 동일** (worst, best, average 모두 O(n²))

> **선행 지식:**
> - 등차수열 합: `1 + 2 + ... + (n-1) = n(n-1)/2`
> - **Selection sort는 입력 데이터에 무관**하게 같은 비교 횟수 (성능 최적화 불가)
> - 본 코드의 `comp++`이 inner for의 첫 줄에 위치 → 모든 비교에서 카운트

**추적 (`arr = {4, 2, 7, 1, 5}`, n=5):**

| 외부 i | inner j 범위 | 비교 횟수 |
|---|---|---|
| 0 | 1, 2, 3, 4 | 4 |
| 1 | 2, 3, 4 | 3 |
| 2 | 3, 4 | 2 |
| 3 | 4 | 1 |

**총: 4 + 3 + 2 + 1 = 10**

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `5` | n 자체를 답으로 (혹은 외부 루프 횟수만) | n=5는 배열 크기, 비교 수와 다름 |
| **(B) `10`** ✅ | 정답 | 4+3+2+1 = 10 = 5·4/2 |
| (C) `15` | n(n+1)/2 = 5·6/2 = 15 (1부터 n까지 합) | 1부터 n-1까지 합이 정답 |
| (D) `25` | n² = 25 | n²보다 약간 작음 (절반 수준) |

> ⚠️ **함정 1:** **공식 헷갈림**. `n(n-1)/2`와 `n(n+1)/2`. selection sort는 **`n(n-1)/2`** (1 ~ n-1까지 합).

> ⚠️ **함정 2:** **입력 무관**. selection sort는 worst case = best case = average case = O(n²). 정렬된 입력이라도 비교는 동일.

> ⚠️ **함정 3:** **`comp++` 위치**. inner for 본문 첫 줄에 위치 → 모든 비교에서 실행. 만약 `if` 안에 두면 갱신 시에만 카운트되어 잘못된 결과.

> 💡 **꿀팁 1:** **n=10이면 비교 = 45**, n=20이면 190, n=100이면 4950. n²과 비슷한 증가 추세.

> 💡 **꿀팁 2:** **CED 2.12 statement execution count** 패턴: 외부 + 내부 루프의 각 i에 대한 inner 실행 횟수를 합산.

> 💡 **꿀팁 3:** **Selection vs Insertion 비교 횟수**:
> - Selection: 항상 `n(n-1)/2` (입력 무관)
> - Insertion: best `n-1`, worst `n(n-1)/2`, 평균 절반

---

### Q3. 정답: **(C) `3`**

📌 **출제 의도:** Selection sort의 **실제 swap 발생 횟수**를 추적. self-swap(`minIdx == i`)을 제외한 의미 있는 swap만 카운트하는 패턴.

📎 **연계:** **CED 4.15.A.2** Selection sort 동작 + **CED 2.12** count 추적.

> **핵심 개념: 의미 있는 swap만 카운트**
> - 매 pass에서 minIdx 찾은 후, **`minIdx != i`이면만** swap (조건문 추가)
> - self-swap은 결과 변화 없음 → 카운트 제외
> - swap 횟수는 **0 ~ n-1** 범위 (가장 많아도 n-1번)

> **선행 지식:**
> - 이미 정렬된 입력 → 0 swap (best case)
> - 역순 정렬된 입력 → n/2 swap (worst case 근사)
> - 일반 무작위 입력 → 경우에 따라 다름

**추적 (`arr = {3, 1, 4, 1, 5, 9}`, n=6):**

| 외부 i | 미정렬 부분 | minIdx | swap? | swaps | 결과 arr |
|---|---|---|---|---|---|
| 0 | {3,1,4,1,5,9} | 1 (val 1) | ✓ (1≠0) | 1 | `{1,3,4,1,5,9}` |
| 1 | {3,4,1,5,9} (idx 1-5) | 3 (val 1) | ✓ (3≠1) | 2 | `{1,1,4,3,5,9}` |
| 2 | {4,3,5,9} (idx 2-5) | 3 (val 3) | ✓ (3≠2) | 3 | `{1,1,3,4,5,9}` |
| 3 | {4,5,9} (idx 3-5) | 3 (val 4) | ✗ (3==3) | 3 | `{1,1,3,4,5,9}` |
| 4 | {5,9} (idx 4-5) | 4 (val 5) | ✗ (4==4) | 3 | `{1,1,3,4,5,9}` |

**총 swaps = 3**

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `5` | 외부 루프 전체 횟수 (n-1=5)와 혼동 | 외부 5회지만 swap 발생은 처음 3회만 |
| (B) `2` | self-swap 회피 가드를 무시하고 마지막 두 pass swap 카운트 | i=3, 4는 minIdx == i → 제외 |
| **(C) `3`** ✅ | 정답 | i=0, 1, 2에서 swap 발생, i=3, 4는 self-swap |
| (D) `0` | 모든 pass에서 self-swap이라 오해 | 첫 3 pass는 의미 있는 swap |

> ⚠️ **함정 1:** **`minIdx != i` 가드의 의미**. 가드 없는 코드(Q1)와 있는 코드(Q3)는 결과는 같지만 **swap 호출 횟수**가 다름.

> ⚠️ **함정 2:** **swap 횟수 vs 비교 횟수**. 비교는 항상 `n(n-1)/2`이지만 swap은 데이터에 따라 변동.

> ⚠️ **함정 3:** **i=마지막에는 자동 self-swap**. 마지막 pass(i=n-2)에서는 미정렬이 1개만 남으므로 항상 self-swap. 따라서 swap 카운트는 최대 `n-2` (또는 그 이하).

> 💡 **꿀팁 1:** **`minIdx != i` 패턴**: 의미 없는 swap 회피 + 카운트 정확화. 성능 미세 최적화.

> 💡 **꿀팁 2:** **교환 횟수의 의미**: swap은 비교보다 비용 큼 (3개 대입). 교환 횟수 최소화는 작지만 의미 있는 최적화.

> 💡 **꿀팁 3:** **검산법**: 결과 배열이 정렬되는지 확인. {1, 1, 3, 4, 5, 9}는 정렬됨 ✓.

---

### Q4. 정답: **(A) `{2, 4, 5, 6, 1, 3}`**

📌 **출제 의도:** **삽입 정렬의 한 외부 반복 = "한 원소를 정렬 부분에 끼워넣기"** 의미를 추적할 수 있는지 테스트. inner while로 큰 원소들을 오른쪽으로 shift하면서 key를 올바른 위치에 삽입.

📎 **연계:** **CED 4.15.A.3**: *"Insertion sort inserts an element from the unsorted portion of a list into its correct (but not necessarily final) position in the sorted portion of the list by shifting elements of the sorted portion to make room for the new element."*

> **핵심 개념: Insertion Sort의 한 외부 반복(pass i)**
> 1. `key = arr[i]` — 삽입할 원소 백업
> 2. `j = i - 1` — 정렬 부분의 마지막 인덱스
> 3. **inner while**: `arr[j] > key`인 동안 `arr[j+1] = arr[j]; j--;` (오른쪽 shift)
> 4. `arr[j+1] = key` — key를 올바른 위치에 삽입
>
> 결과: `arr[0..i]`가 정렬됨 (단, 전체 최종은 아닐 수 있음 — "but not necessarily final")

> **선행 지식:**
> - inner while은 short-circuit으로 `j >= 0` 먼저 체크 (`arr[-1]` 접근 방지)
> - 이미 key가 가장 크면 inner while 즉시 종료 → shift 없음 (best case)
> - **Selection은 swap, Insertion은 shift + 단일 대입**

**추적 (`arr = {5, 2, 4, 6, 1, 3}`, 외부 3회 = i=1, 2, 3):**

**Pass i=1 (key=2):**

| j | arr[j] | arr[j] > key? | 동작 |
|---|---|---|---|
| 0 | 5 | 5>2 ✓ | shift: arr[1]=5 → `{5,5,4,6,1,3}`, j=-1 |
| -1 | — | j<0 종료 | arr[0]=key=2 → `{2,5,4,6,1,3}` |

**Pass i=2 (key=4):**

| j | arr[j] | arr[j] > key? | 동작 |
|---|---|---|---|
| 1 | 5 | 5>4 ✓ | shift: arr[2]=5 → `{2,5,5,6,1,3}`, j=0 |
| 0 | 2 | 2>4 ✗ | 종료 → arr[1]=4 → `{2,4,5,6,1,3}` |

**Pass i=3 (key=6):**

| j | arr[j] | arr[j] > key? | 동작 |
|---|---|---|---|
| 2 | 5 | 5>6 ✗ | 즉시 종료 → arr[3]=6 (변화 없음) → `{2,4,5,6,1,3}` |

**최종 (외부 3회 후): `{2, 4, 5, 6, 1, 3}`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `{2, 4, 5, 6, 1, 3}`** ✅ | 정답 | 3 pass 후 앞 4개 정렬, 뒤 2개 미정렬 |
| (B) `{1, 2, 3, 4, 5, 6}` | 완전 정렬 | 외부 5회 모두 진행 시. 본 문제는 3회만 |
| (C) `{2, 5, 4, 6, 1, 3}` | 1 pass만 진행 | 1회 후 상태. 본 문제는 3회 |
| (D) `{2, 4, 5, 1, 6, 3}` | shift 잘못 적용 (1을 잘못된 위치에) | 본 문제 i=3까지는 1 처리 안 됨. 1은 i=4에서 처리 |

> ⚠️ **함정 1:** **"correct but not necessarily final"** (CED 4.15.A.3). 매 pass 후 앞부분만 정렬. 전체 정렬은 모든 pass 진행 후.

> ⚠️ **함정 2:** **inner while 두 조건 순서**. `j >= 0 && arr[j] > key`. `j >= 0`을 먼저 체크해야 short-circuit으로 `arr[-1]` 접근 방지.

> ⚠️ **함정 3:** **key 백업**. `int key = arr[i];`로 미리 저장해두지 않으면 shift 과정에서 덮어씌워져 잃어버림.

> 💡 **꿀팁 1:** **Insertion vs Selection 차이**:
> - Selection: "미정렬 최솟값 → 정렬 끝에 swap"
> - Insertion: "미정렬 첫 원소 → 정렬 부분에 끼워넣기 (shift)"

> 💡 **꿀팁 2:** **k pass 후 상태**: `arr[0..k]`이 정렬됨 (k+1개), `arr[k+1..n-1]` 미정렬. Selection은 `arr[0..k-1]` (k개) 정렬과 비교.

> 💡 **꿀팁 3:** **Insertion이 빛나는 케이스**: 거의 정렬된 입력 → inner while 거의 안 돔 → O(n). Q6 참조.

---

### Q5. 정답: **(C) `3`**

📌 **출제 의도:** Insertion sort의 **shift 횟수**를 추적. inner while의 본문이 실행되는 총 횟수 = shift 횟수.

📎 **연계:** **CED 4.15.A.3** + **CED 2.12** (statement execution count). shift는 `arr[j+1] = arr[j]` 단일 대입 = 1 shift.

> **핵심 개념:** shift 횟수는 **inner while 본문 실행 횟수**.
> - Best case (이미 정렬): 0 shifts (inner while 즉시 종료)
> - Worst case (역순): `n(n-1)/2` shifts
> - 일반 무작위: O(n²) 평균

**추적 (`arr = {3, 1, 4, 1, 5}`):**

**Pass i=1 (key=1):**

| j | arr[j] | arr[j] > 1? | shift? |
|---|---|---|---|
| 0 | 3 | ✓ | shift (1) → arr={1,3,4,1,5}, j=-1 |

**누적 shifts = 1**

**Pass i=2 (key=4):**

| j | arr[j] | arr[j] > 4? | shift? |
|---|---|---|---|
| 1 | 3 | ✗ | 즉시 종료 (no shift) |

**누적 shifts = 1** (변화 없음)

**Pass i=3 (key=1):**

| j | arr[j] | arr[j] > 1? | shift? |
|---|---|---|---|
| 2 | 4 | ✓ | shift (2) → arr={1,3,4,4,5}, j=1 |
| 1 | 3 | ✓ | shift (3) → arr={1,3,3,4,5}, j=0 |
| 0 | 1 | ✗ | 종료, arr[1]=1 → arr={1,1,3,4,5} |

**누적 shifts = 3**

**Pass i=4 (key=5):**

| j | arr[j] | arr[j] > 5? | shift? |
|---|---|---|---|
| 3 | 4 | ✗ | 즉시 종료 |

**총 shifts = 3** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `1` | i=1만 카운트 | i=3에서 추가 shift 발생 |
| (B) `2` | 한 pass의 shift 빠뜨림 | 전체 합산 필요 |
| **(C) `3`** ✅ | 정답 | i=1: 1, i=3: 2, 합 3 |
| (D) `4` | 추가 shift 잘못 카운트 | 정확히 3회 |

> ⚠️ **함정 1:** **shift는 단일 대입**. `arr[j+1] = arr[j]`가 한 번 실행될 때마다 shift 1회. swap(3 대입)과 다름.

> ⚠️ **함정 2:** **마지막 `arr[j+1] = key` 대입은 shift 아님**. while 밖의 단일 삽입 — 카운트에서 제외.

> ⚠️ **함정 3:** **중복값 처리**. 본 데이터는 1이 두 번 등장. 두 번째 1은 첫 번째 1 직후에 삽입 (안정 정렬 — stable sort).

> 💡 **꿀팁 1:** **shift 횟수 ≈ 비교 횟수**. inner while마다 비교 + shift이므로 둘이 거의 같음. (정확한 비교 횟수 = shift 횟수 + outer 횟수, 종료 조건 비교 추가)

> 💡 **꿀팁 2:** **shift 0 = 이미 정렬**. shift가 한 번도 발생 안 하면 입력이 이미 정렬된 것.

> 💡 **꿀팁 3:** **inner while의 종료 조건**: (1) `j < 0` (배열 시작 도달) 또는 (2) `arr[j] <= key` (올바른 위치 발견).

---

### Q6. 정답: **(A) `0`**

📌 **출제 의도:** Insertion sort의 **best case** — 이미 정렬된 입력에서 inner while이 즉시 종료되어 **shift 0번**임을 이해. CED 2.12 best case run-time 분석.

📎 **연계:** **CED 4.15.A.3** Insertion sort 동작 + **CED 2.12** Run-Time Analysis. 인접한 알고리즘 중 best case가 가장 좋은 정렬 (O(n)).

> **핵심 개념: Insertion sort best case**
> - 입력이 **이미 오름차순 정렬**일 때:
>   - 매 pass에서 `key = arr[i]` (= 정렬된 부분의 최댓값보다 큰 값)
>   - inner while 첫 조건 `arr[j] > key`에서 `arr[i-1] > arr[i]`? **항상 false**
>   - while 즉시 종료 → shift 0
> - 외부 루프는 `n-1`번 돌지만 inner는 매번 0 iteration
> - 총 shifts = **0**, 비교 = `n-1`

> **선행 지식:**
> - Insertion sort는 **데이터 적응형(adaptive)** — 입력 정렬 정도에 따라 성능 변화
> - Selection sort는 비적응형 (입력 무관)
> - 거의 정렬된 데이터에서 insertion sort가 가장 빠른 정렬 알고리즘 중 하나

**추적 (`arr = {1, 2, 3, 4, 5}`):**

**Pass i=1 (key=2):**

| j | arr[j] | arr[j] > 2? | 동작 |
|---|---|---|---|
| 0 | 1 | ✗ | 즉시 종료, arr[1]=2 (변화 없음) |

shifts = 0

**Pass i=2, 3, 4: 모두 동일하게 첫 비교에서 false, 즉시 종료.**

**총 shifts = 0** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `0`** ✅ | 정답 | 이미 정렬 → 모든 pass에서 inner while 즉시 종료 |
| (B) `4` | 외부 루프 횟수(n-1=4)를 답으로 | 외부는 4회 돌지만 inner는 매번 0회 |
| (C) `5` | 배열 크기(n) | 크기와 shift는 무관 |
| (D) `10` | n(n-1)/2 = worst case | best case는 0, worst만 n(n-1)/2 |

> ⚠️ **함정 1:** **"외부 루프 = shift 발생"** 오해. 외부는 항상 n-1번 돌지만 inner의 동작이 핵심. inner가 0회면 shift도 0.

> ⚠️ **함정 2:** **Selection sort와 차이**. Selection도 정렬된 입력에 적용 가능하지만 **비교 횟수는 동일** (`n(n-1)/2`). Insertion은 **비교 횟수도 줄어** (`n-1`).

> ⚠️ **함정 3:** **거의 정렬 vs 완전 정렬**. 한 원소만 자리 바뀌어도 일부 shift 발생. 본 문제는 완전 정렬 → 0.

> 💡 **꿀팁 1:** **Insertion sort 시간 복잡도**:
> - Best case (정렬): O(n)
> - Average: O(n²)
> - Worst case (역순): O(n²)

> 💡 **꿀팁 2:** **언제 Insertion sort?**:
> - 작은 배열 (n < 20)
> - 거의 정렬된 데이터
> - Online 알고리즘 (데이터가 한 번에 하나씩 도착)

> 💡 **꿀팁 3:** **CED 2.12 분석 패턴**: best/worst/average case 구분. 각 case의 statement execution count 추적.

---

### Q7. 정답: **(C) `7`**

📌 **출제 의도:** **Merge sort의 재귀 호출 트리 크기**를 정확히 셀 수 있는지 테스트. base case 도달까지의 모든 호출 카운트.

📎 **연계:** **CED 4.17.C.2**: *"Merge sort repeatedly divides an array into smaller subarrays until each subarray is one element and then recursively merges the sorted subarrays back together in sorted order to form the final sorted array."*

> **핵심 개념: Merge sort 재귀 트리**
> - 매 호출은 두 자식 호출을 만들거나 base case에서 종료
> - n=4면 재귀 트리:
> ```
>          (0,3)
>         /     \
>      (0,1)   (2,3)
>      /   \    /   \
>   (0,0)(1,1)(2,2)(3,3)   ← 모두 base case
> ```
> - 호출 개수: 1 + 2 + 4 = **7**
> - 일반: n개 원소 → 약 `2n - 1` 호출 (n=4면 7, n=8이면 15)

> **선행 지식:**
> - base case `lo >= hi`: 단일 원소 또는 빈 범위 → 즉시 return
> - 재귀 호출도 호출 자체는 카운트됨 (base case에서 return해도 한 번 호출된 것)
> - 호출 트리는 **이진 트리** (각 호출은 0개 또는 2개 자식)

**추적 (`mergeSort(arr, 0, 3)`):**

```
mergeSort(0, 3):                    ← 호출 1
  lo=0 < hi=3, mid=1
  mergeSort(0, 1):                  ← 호출 2
    lo=0 < hi=1, mid=0
    mergeSort(0, 0):                ← 호출 3 (base, return)
    mergeSort(1, 1):                ← 호출 4 (base, return)
  mergeSort(2, 3):                  ← 호출 5
    lo=2 < hi=3, mid=2
    mergeSort(2, 2):                ← 호출 6 (base, return)
    mergeSort(3, 3):                ← 호출 7 (base, return)
```

**총 호출: 7** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `3` | 비-base 호출만 카운트 (`(0,3), (0,1), (2,3)`) | base case도 호출이므로 카운트 포함 |
| (B) `5` | 일부 호출 빠뜨림 | 정확히 7회 |
| **(C) `7`** ✅ | 정답 | 1 + 2 + 4 = 7 (각 레벨 호출 수의 합) |
| (D) `4` | 잎 노드(base case) 4개만 카운트 | 내부 노드 3개 추가 |

> ⚠️ **함정 1:** **base case도 호출**. `mergeSort(0,0)`은 진입 후 base 조건 만족하고 return하지만, 호출 자체는 발생.

> ⚠️ **함정 2:** **재귀 트리 구조**. 매 호출은 0 또는 2 자식. n원소면 정확히 `2n - 1` 호출 (완전 이진 트리의 노드 수).

> ⚠️ **함정 3:** **call vs depth**. call = 호출 횟수 (트리 노드 수), depth = 트리 높이 (Q9 참조).

> 💡 **꿀팁 1:** **n원소 merge sort 호출 수 공식**: `2n - 1`. n=4 → 7, n=8 → 15, n=16 → 31.

> 💡 **꿀팁 2:** **호출 추적법**: 트리 그리기. 위에서 아래로 들여쓰기로 호출 stack 표시. base case는 leaf node.

> 💡 **꿀팁 3:** **재귀 트레이싱 (CED 4.16 IN, writing OUT)**: AP는 재귀 코드 작성을 요구하지 않지만, **결과 추적은 필수 능력**.

---

### Q8. 정답: **(B) `{1, 2, 4, 5, 7, 8}`**

📌 **출제 의도:** **Merge 단계의 핵심 동작** — 두 정렬된 부분 배열을 비교하며 작은 쪽을 차례로 결과에 추가하는 과정을 이해할 수 있는지 테스트.

📎 **연계:** **CED 4.17.C.2**: *"recursively merges the sorted subarrays back together in sorted order"*. Merge step은 알고리즘의 핵심 로직 (학생이 트레이스).

> **핵심 개념: Merge 두 정렬 배열**
> ```
> 두 포인터(L_idx, R_idx)를 각 배열 시작에 위치
> 반복:
>   left[L_idx]와 right[R_idx] 비교
>   더 작은 쪽을 결과에 추가, 해당 포인터 +1
>   한쪽이 끝나면 나머지 전체 추가
> ```
> - 결과 배열 크기 = left + right 길이 합
> - **두 배열이 정렬되어 있어야** merge가 정렬된 결과를 보장
> - merge step 자체는 O(n) (각 원소 한 번씩만 비교)

> **선행 지식:**
> - Merge sort는 divide-and-conquer: divide(분할) + conquer(merge)
> - merge step은 새 배열을 만들어 결과 저장 (in-place 아님)
> - **두 정렬 배열의 결합 → 정렬된 결과** (안정 정렬)

**추적 (`left = {1, 4, 7}`, `right = {2, 5, 8}`):**

| 단계 | left[L] | right[R] | 비교 | 선택 | result | L | R |
|---|---|---|---|---|---|---|---|
| 시작 | — | — | — | — | `{}` | 0 | 0 |
| 1 | 1 | 2 | 1<2 | left | `{1}` | 1 | 0 |
| 2 | 4 | 2 | 4>2 | right | `{1,2}` | 1 | 1 |
| 3 | 4 | 5 | 4<5 | left | `{1,2,4}` | 2 | 1 |
| 4 | 7 | 5 | 7>5 | right | `{1,2,4,5}` | 2 | 2 |
| 5 | 7 | 8 | 7<8 | left | `{1,2,4,5,7}` | 3 | 2 |
| 6 | (left 끝) | 8 | left exhausted | right | `{1,2,4,5,7,8}` | 3 | 3 |

**결과: `{1, 2, 4, 5, 7, 8}`** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| (A) `{1, 4, 7, 2, 5, 8}` | 단순 concat (left + right) | merge는 비교 + 정렬, 단순 연결 아님 |
| **(B) `{1, 2, 4, 5, 7, 8}`** ✅ | 정답 | 두 정렬 배열의 정렬된 결합 |
| (C) `{2, 5, 8, 1, 4, 7}` | 역순 concat (right + left) | merge 결과는 정렬 (오름차순) |
| (D) `{1, 4, 2, 5, 7, 8}` | 일부만 비교/일부 잘못 | 모든 비교를 정확히 수행해야 |

> ⚠️ **함정 1:** **단순 concat 아님**. merge는 두 배열의 원소를 **interleave(교차)**하면서 정렬 순서 유지. 단순 합치면 정렬 깨짐.

> ⚠️ **함정 2:** **선행조건: 두 배열 모두 정렬**. merge의 정렬된 결과는 입력이 정렬되어 있을 때만 보장. merge sort는 재귀로 이를 보장.

> ⚠️ **함정 3:** **한쪽이 먼저 끝나면 나머지 그대로**. 본 문제처럼 left의 7이 마지막에 처리되면 right의 8 추가만 남음 (이미 정렬되어 있으므로 비교 없이 추가).

> 💡 **꿀팁 1:** **Merge step 시간 복잡도 O(n)**. 각 원소를 한 번씩만 처리. 공간은 추가 배열 필요 → O(n) 추가 메모리.

> 💡 **꿀팁 2:** **Merge sort 전체 복잡도**:
> - 시간: O(n log n) (best/avg/worst 모두)
> - 공간: O(n) 추가 메모리
> - **안정 정렬** (같은 값의 상대 순서 유지)

> 💡 **꿀팁 3:** **검산법**: 결과 배열이 정렬되어 있고 길이가 left + right 합이면 정상. {1,2,4,5,7,8} → 정렬됨, 길이 6 = 3+3 ✓.

---

### Q9. 정답: **(A) `4`**

📌 **출제 의도:** Merge sort의 **재귀 깊이**(stack frame 최대 개수)를 계산. n원소 → 깊이는 `⌈log₂n⌉ + 1`.

📎 **연계:** **CED 4.17.C** Merge sort의 divide-and-conquer 구조. **CED 4.16.A.2**: *"Each recursive call has its own set of local variables"* — 깊이 = 최대 동시 stack frame 수.

> **핵심 개념: 재귀 깊이 계산**
> - 매 호출이 절반으로 분할 → 깊이는 `log₂n` 정도
> - n=8: 8 → 4 → 2 → 1 (3번 분할 = 3 levels below initial)
> - 초기 호출 깊이를 1로 세면 최대 깊이 = `log₂n + 1` = **4**

> **선행 지식:**
> - 재귀 깊이 = 호출 trace에서 가장 깊은 stack frame 수
> - depth = 1: 초기 호출 (`mergeSort(0, 7)`)
> - depth = 2, 3, 4: 점점 더 깊은 재귀
> - n=2^k → 깊이 = k+1

**추적 (`mergeSort(arr, 0, 7)`, n=8):**

```
depth 1: mergeSort(0, 7)         ← 초기 호출
  depth 2: mergeSort(0, 3)       ← n=4 분할
    depth 3: mergeSort(0, 1)     ← n=2 분할
      depth 4: mergeSort(0, 0)   ← base case
      depth 4: mergeSort(1, 1)   ← base case
    depth 3: mergeSort(2, 3)
      depth 4: mergeSort(2, 2)
      depth 4: mergeSort(3, 3)
  depth 2: mergeSort(4, 7)       ← 우측 절반
    depth 3: mergeSort(4, 5)
      depth 4: mergeSort(4, 4)
      depth 4: mergeSort(5, 5)
    depth 3: mergeSort(6, 7)
      depth 4: mergeSort(6, 6)
      depth 4: mergeSort(7, 7)
```

**최대 깊이 = 4** ✓

**오답 분석:**

| 보기 | 값 | 왜 틀린가 |
|---|---|---|
| **(A) `4`** ✅ | 정답 | 초기 호출(1) + 3 levels of recursion |
| (B) `8` | n 자체를 깊이로 오해 | 깊이는 log₂n 수준 |
| (C) `3` | 초기 호출을 깊이 0으로 카운트 | 본 문제는 "초기 호출은 깊이 1"로 명시 |
| (D) `7` | 호출 횟수(2n-1=15)와 혼동, 또는 절반 | 호출 수 ≠ 깊이 |

> ⚠️ **함정 1:** **호출 수 vs 깊이**. n=8: 호출 수 = 15(2n-1), 깊이 = 4(log₂n + 1). 둘은 다른 개념.

> ⚠️ **함정 2:** **0-based vs 1-based 카운트**. 깊이를 어떻게 세느냐로 답이 달라짐. 본 문제는 명시적으로 "초기 = 1".

> ⚠️ **함정 3:** **n이 2의 거듭제곱이 아닐 때**. n=10이면 깊이는 ceil(log₂10) + 1 = 5. 분할이 비대칭일 수 있음.

> 💡 **꿀팁 1:** **깊이 공식**: n=2^k → 깊이 = k + 1 (초기 1 기준).
> - n=4: 깊이 3
> - n=8: 깊이 4
> - n=16: 깊이 5
> - n=1024: 깊이 11

> 💡 **꿀팁 2:** **공간 복잡도와 관계**: 재귀 깊이 = 동시 stack frame 수 → 메모리 사용량의 핵심. merge sort는 O(log n) recursion depth + O(n) merge buffer.

> 💡 **꿀팁 3:** **재귀 vs 반복형**: 재귀형은 stack 깊이 제한 (StackOverflowError 위험). 반복형으로 변환 가능하나 코드 복잡.

---

### Q10. 정답: **(D) Insertion sort — 이미 정렬된 입력에서는 inner while이 즉시 종료되어 O(n)**

📌 **출제 의도:** **세 정렬 알고리즘의 best case 비교** — 각 알고리즘의 입력 적응성 이해. CED 4.15 + 4.17.C 종합 개념 문제.

📎 **연계:** **CED 4.15** Selection/Insertion + **CED 4.17.C** Merge + **CED 2.12** Run-Time Analysis. 알고리즘 선택의 핵심 기준.

> **핵심 개념: Best Case 비교**
>
> | 알고리즘 | Best Case | Avg/Worst | 적응성 |
> |---|---|---|---|
> | Selection | O(n²) | O(n²) | 비적응 (입력 무관) |
> | Insertion | **O(n)** | O(n²) | 적응 (정렬되어 있으면 빠름) |
> | Merge | O(n log n) | O(n log n) | 비적응 (항상 같음) |
>
> **이미 정렬된 입력에서는 Insertion sort가 압도적으로 효율적** (O(n) vs O(n log n) vs O(n²)).

> **선행 지식:**
> - **Insertion sort의 적응성**: inner while이 첫 비교에서 false → 즉시 종료 → shift 0 (Q6 참조)
> - **Selection sort 비적응**: 항상 모든 미정렬 부분을 스캔 → 입력에 무관한 비교 횟수
> - **Merge sort 비적응**: 항상 분할 + merge → log n 깊이의 재귀 + 매 레벨 O(n) merge

**옵션별 검증:**

| 보기 | 분석 |
|---|---|
| (A) "Selection — 가장 단순" | Selection은 best case도 O(n²) — 정렬된 입력에서도 같은 비용. 가장 느림 |
| (B) "Merge — 항상 O(n log n)" | "일관됨"은 맞지만 best case **최적**은 아님 (O(n) > O(n log n)) |
| (C) "셋 다 동일" | 거짓 — 입력에 따라 알고리즘 성능 다름 (Insertion이 best case에서 가장 빠름) |
| **(D) Insertion — O(n)** ✅ | 정답 — inner while 즉시 종료 → 외부만 n-1회 → O(n) |

> ⚠️ **함정 1:** **Selection의 비적응성 간과**. "단순 = 빠름"이 아님. Selection은 비교 횟수가 항상 `n(n-1)/2`로 고정.

> ⚠️ **함정 2:** **Merge sort 우월성 가정**. "재귀 = 빠름"이 아님. 작은 배열이나 정렬된 배열에서는 Insertion이 더 빠름.

> ⚠️ **함정 3:** **Best vs Worst 혼동**. 본 문제는 **best case** (이미 정렬). Worst case라면 답이 다를 수 있음 (Merge가 O(n log n)으로 최적).

> 💡 **꿀팁 1:** **알고리즘 선택 가이드**:
> - 작은 배열 (n < 20) 또는 거의 정렬: **Insertion sort**
> - 큰 배열, 일관된 성능 필요: **Merge sort**
> - 메모리 제약, 단순 구현: **Selection sort**

> 💡 **꿀팁 2:** **시간 복잡도 표 외우기**:
> ```
>            Best     Avg      Worst
> Selection  O(n²)    O(n²)    O(n²)
> Insertion  O(n)     O(n²)    O(n²)
> Merge      O(n log n) O(n log n) O(n log n)
> ```

> 💡 **꿀팁 3:** **CED 출제 가능 개념 문제 패턴**: "어떤 알고리즘이 가장 효율적인가?" — 입력 데이터의 특성(크기, 정렬 정도)을 고려해 선택.

---

## 종합 정리

### 4.15 Selection Sort 골격
```java
for (int i = 0; i < arr.length - 1; i++) {
    int minIdx = i;
    for (int j = i + 1; j < arr.length; j++) {
        if (arr[j] < arr[minIdx]) minIdx = j;
    }
    int t = arr[i]; arr[i] = arr[minIdx]; arr[minIdx] = t;
}
```

### 4.15 Insertion Sort 골격
```java
for (int i = 1; i < arr.length; i++) {
    int key = arr[i];
    int j = i - 1;
    while (j >= 0 && arr[j] > key) {
        arr[j + 1] = arr[j];
        j--;
    }
    arr[j + 1] = key;
}
```

### 4.17.C Merge Sort 골격 (재귀)
```java
public static void mergeSort(int[] arr, int lo, int hi) {
    if (lo >= hi) return;
    int mid = (lo + hi) / 2;
    mergeSort(arr, lo, mid);
    mergeSort(arr, mid + 1, hi);
    merge(arr, lo, mid, hi);  // 두 정렬된 절반 결합
}
```

### 시간 복잡도 정리

| 알고리즘 | Best | Avg | Worst | 적응성 | 안정성 |
|---|---|---|---|---|---|
| Selection | O(n²) | O(n²) | O(n²) | 비적응 | 비안정 |
| Insertion | **O(n)** | O(n²) | O(n²) | 적응 | 안정 |
| Merge | O(n log n) | O(n log n) | O(n log n) | 비적응 | 안정 |

### EXCLUSION 재확인
- **CED 4.17.C.1**: *"Sorting algorithms other than selection, insertion, and merge sort are outside the scope"*
  - **Bubble sort, Quick sort, Heap sort 모두 OUT** ✓ — 본 세트 미사용
- **`Math.min/max` 사용 금지** ✓ — `if` 비교만 사용
- **`break`/`continue` 사용 금지** ✓ — while 종료 조건 + return만 사용
