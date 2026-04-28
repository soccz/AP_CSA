# Unit 4: Data Collections — 완전정복 딥다이브
## "왜?"로 시작해서 만점으로 끝내는 단 하나의 책

> **이 문서는 누구를 위한 것인가**
> - Java를 처음 보는 사람도 이 한 편을 읽으면 Unit 4의 모든 시험 개념을 **이해**한다.
> - 단순히 "외워라"가 아니라 "왜 이렇게 생겼는가"를 풀어 설명한다.
> - 초등학생에게 설명할 수 있는 비유부터 시작해서, 컴파일러가 메모리에서 어떻게 동작하는 메커니즘까지 한 줄로 잇는다.
> - 연습 문제 없음. **이해의 깊이**만 끌어올린다.
> - College Board 공식 CED(Course and Exam Description) 2025-26의 17개 토픽(4.1~4.17), 모든 Essential Knowledge(EK) 항목을 빠짐없이 다룬다.

---

## 0. 시험 지도 — Unit 4는 시험에서 무엇을 의미하는가

### 시험 비중 — Unit 4는 시험에서 가장 무거운 단원

| 항목 | 비중 |
|-----|------|
| MCQ (42문제 중) | **30-40%** = 약 13-17문제 |
| FRQ Q3 (Data Analysis with ArrayList) | **5점, 1번 문제 통째로** |
| FRQ Q4 (2D Array) | **6점, 1번 문제 통째로** |
| 전체 시험 점수 기여 | **약 36-42%** (MCQ 16-22% + FRQ Q3·Q4 합 19.8%) |

**Unit 4는 시험의 1/3 이상**을 차지하는 가장 무거운 단원이다.

### CED 공식 토픽 (17개) — 빠짐없이 다룸

| # | 토픽 | 본 문서 섹션 |
|---|-----|-----------|
| 4.1 | Ethical and Social Issues Around Data Collection | §2 |
| 4.2 | Introduction to Using Data Sets | §3 |
| 4.3 | Array Creation and Access | §4 |
| 4.4 | Array Traversals | §5 |
| 4.5 | Implementing Array Algorithms | §6 |
| 4.6 | Using Text Files | §7 |
| 4.7 | Wrapper Classes | §8 |
| 4.8 | ArrayList Methods | §9 |
| 4.9 | ArrayList Traversals | §10 |
| 4.10 | Implementing ArrayList Algorithms | §11 |
| 4.11 | 2D Array Creation and Access | §12 |
| 4.12 | 2D Array Traversals | §13 |
| 4.13 | Implementing 2D Array Algorithms | §14 |
| 4.14 | Searching Algorithms | §15 |
| 4.15 | Sorting Algorithms | §16 |
| 4.16 | Recursion | §17 |
| 4.17 | Recursive Searching and Sorting | §18 |

### Unit 4가 왜 이렇게 무거운가

**프로그래밍의 본질은 "데이터를 다루는 것"**이다. Unit 1-3까지는 "한 개의 값"이나 "한 개의 객체"를 다뤘다. Unit 4부터는 **수십, 수백, 수천 개의 데이터를 한꺼번에** 다루는 방법을 배운다. 이것이 진짜 프로그래밍.

현실에서 컴퓨터가 하는 일의 99%가:
- 사용자 명단 관리
- 게시글 모음 처리
- 점수 계산과 정렬
- 이미지(픽셀의 2D 배열) 처리
- 검색 엔진의 인덱싱

이 모두가 Unit 4의 도구들로 만들어진다. AP CSA가 이 단원에 **MCQ 30-40% + FRQ 2개**라는 가장 큰 비중을 할당한 이유.

### 이 단원의 종착점

이 문서를 다 읽으면 다음 6가지를 할 수 있다:

1. 배열·ArrayList·2D 배열을 빈 종이에 자유롭게 선언하고 다룰 수 있다.
2. **표준 알고리즘 9가지**(sum/avg/max/min/count/exists/forall/pairs/duplicates)를 손으로 코딩할 수 있다.
3. **삭제 중 순회의 함정**을 즉시 식별하고 두 가지 해결법을 제시할 수 있다.
4. **Linear search vs Binary search**의 적용 조건을 즉답할 수 있고, 두 알고리즘의 트레이싱 결과를 종이에 쓸 수 있다.
5. **Selection sort, Insertion sort, Merge sort**의 매 단계 배열 상태를 추적할 수 있다.
6. **재귀 메서드**를 보고 호출 트리를 그릴 수 있고 결과를 1초 안에 답할 수 있다.

### CED Skill Category 매핑 — 토픽이 어떤 능력을 묻는지

CED는 모든 시험 문제를 **5개 Skill Category(컴퓨팅 사고 실천)** 중 하나에 매핑한다. 같은 EK 내용도 어떤 Skill로 묻느냐에 따라 문제 형태가 달라지므로, 토픽별 Skill을 알면 **출제 형식을 미리 예측**할 수 있다.

#### 5개 Skill의 의미 (CED 원문 기반)

| Skill | 한 줄 의미 | 문제 형태 |
|---|---|---|
| **1.B** Extract Knowledge | 데이터에서 어떤 지식을 끌어낼 수 있는지 결정 | "이 데이터셋으로 무엇을 알 수 있나?" |
| **2.B** Write Code (data) | 데이터 추상화 코드 작성 (배열/ArrayList/2D 배열 조작) | FRQ Q3·Q4 본체 |
| **2.C** Write Code (procedural) | 절차 추상화 코드 작성 (메서드 호출, 파일 처리) | FRQ Q3·Q4의 메서드 부분 |
| **3.B** Determine Output (data) | 데이터 추상화 코드의 출력/결과 결정 | MCQ 트레이싱 (가장 빈출) |
| **3.C** Determine Output (procedural) | 절차 추상화 코드의 출력/결과 결정 | MCQ 트레이싱 (재귀 등) |
| **3.D** Explain Errors | 컴파일 에러나 오작동 이유 설명·수정 | MCQ "다음 중 에러는?" |
| **4.A** Describe Behavior | 코드가 무엇을 하는지 설명 | MCQ "이 알고리즘의 목적은?" |
| **4.B** Describe Preconditions | 의도대로 작동하려면 어떤 초기 조건이 필요한지 | MCQ "Binary search 사용 전제는?" |
| **5.A** Computing Impact | 컴퓨팅의 사회·경제·문화 영향 설명 | MCQ 시나리오 (윤리) |

#### Unit 4 토픽별 Skill 매핑 (CED p.95-98 공식)

| Topic | 제목 | 시험 강조 Skill |
|---|---|---|
| 4.1 | Ethical & Social Issues | **1.B** + **5.A** (지식 추출 + 사회 영향) |
| 4.2 | Introduction to Data Sets | **1.B** (데이터 활용) |
| 4.3 | Array Creation and Access | **2.B** + **3.B** (작성 + 결과) |
| 4.4 | Array Traversals | **2.B** + **3.B** + **3.D** (작성 + 결과 + 에러) |
| 4.5 | Implementing Array Algorithms | **2.B** + **3.B** + **3.D** + **4.A** (가장 많은 Skill — 알고리즘 핵심) |
| 4.6 | Using Text Files | **2.C** + **3.C** + **4.B** (작성 + 결과 + 전제) |
| 4.7 | Wrapper Classes | **2.B** (코드 작성) |
| 4.8 | ArrayList Methods | **2.B** + **3.B** + **3.D** |
| 4.9 | ArrayList Traversals | **2.B** + **3.D** + **4.A** |
| 4.10 | Implementing ArrayList Algorithms | **2.B** + **3.B** + **3.D** + **4.A** (FRQ Q3 핵심) |
| 4.11 | 2D Array Creation and Access | **2.B** + **3.B** |
| 4.12 | 2D Array Traversals | **2.B** + **3.B** + **3.D** |
| 4.13 | Implementing 2D Array Algorithms | **2.B** + **3.B** + **3.D** + **4.A** (FRQ Q4 핵심) |
| 4.14 | Searching Algorithms | **2.B** + **3.B** + **4.A** |
| 4.15 | Sorting Algorithms | **3.B** + **4.A** + **4.B** (트레이싱 + 설명 + 전제) |
| 4.16 | Recursion | **3.C** + **4.A** + **4.B** (트레이싱 + 설명 + 전제) |
| 4.17 | Recursive Searching/Sorting | **4.A** + **4.B** (설명 + 전제만 — 작성은 EXCLUSION) |

#### 시험 대비 활용법

- **Skill 2.B/2.C 강한 토픽**(4.3~4.13의 대부분) → **FRQ Q3·Q4 직결**. 배열/ArrayList/2D 코드를 손으로 쓰는 연습 필수.
- **Skill 3.B/3.C 강한 토픽**(4.5, 4.10, 4.13, 4.15, 4.16) → **MCQ 트레이싱**. 알고리즘 단계별 배열 상태 추적 연습.
- **Skill 3.D 강한 토픽**(4.4, 4.5, 4.8, 4.9, 4.10, 4.12, 4.13) → **MCQ 에러 진단**. AIOOBE/IOOBE/CME/NPE 발생 시점 정확히 알기.
- **Skill 4.A/4.B 강한 토픽**(4.5, 4.10, 4.13~4.17) → **MCQ "이 알고리즘은 무엇을 하나?", "전제 조건은?"**. 알고리즘 의도 파악 연습.
- **Skill 5.A**(4.1) → MCQ 시나리오 1-2문제 대비.

#### 4.16, 4.17의 특수성 — Skill 2.B/2.C 없음

재귀 토픽(4.16, 4.17)에는 **Skill 2(Write Code)가 빠져있다**. CED 4.16.A.3 EXCLUSION이 "재귀 코드 작성은 시험 범위 외"라고 명시했기 때문. 출제는 오직:
- **3.C**: 주어진 재귀 코드의 결과 결정 (트레이싱)
- **4.A**: 재귀 메서드의 동작 설명
- **4.B**: 재귀가 의도대로 작동하기 위한 base case 조건

작성 능력이 필요 없으므로, 학습은 **트레이싱 연습**에 집중하면 된다.

---

## 1. 본격 시작 전 — "데이터 컬렉션"이 도대체 뭔지부터

### 왜 컬렉션이 필요한가 — "변수 폭발 문제"

학생 30명의 점수를 저장한다고 하자.

```java
// 컬렉션 없이
int score1 = 90;
int score2 = 85;
int score3 = 78;
// ... 30번 반복
int score30 = 95;
```

문제:
- **변수가 30개**. 평균을 구하려면 `(score1 + score2 + ... + score30) / 30` 30개 일일이 적어야 함.
- 학생이 31명으로 늘면 새 변수와 모든 코드 수정.
- "i번째 학생 점수"라는 표현이 불가능 (변수 이름에 변수를 못 쓴다).

### 컬렉션의 해결책 — "한 변수에 여러 값"

```java
int[] scores = new int[30];   // 30개를 한 변수에 담음
scores[0] = 90;
scores[1] = 85;
// ...

// 평균을 한 줄로
int sum = 0;
for (int i = 0; i < scores.length; i++) {
    sum += scores[i];
}
double avg = (double) sum / scores.length;
```

**한 변수 + 인덱스 = 무한한 데이터를 같은 코드로 처리**. 이게 컬렉션의 본질.

### Unit 4의 세 가지 컬렉션

| 종류 | 한 줄 정의 | 비유 |
|-----|--------|-----|
| **Array (배열)** | 같은 타입, 고정 크기 | 30칸 아파트 (입주 후 칸 수 변경 불가) |
| **ArrayList** | 같은 타입, 가변 크기 | 호텔 (손님 늘면 방 추가 가능) |
| **2D Array** | 행과 열로 이루어진 격자 | 학교 시간표 (월~금 × 1~6교시) |

이 세 가지의 사용법, 차이, 알고리즘이 Unit 4의 전부.

---

## 2. CED 4.1 — 윤리와 사회적 이슈

### 왜 코딩 단원에 윤리가 끼어 있는가

대규모 데이터를 다루기 시작하면 **개인 정보, 알고리즘 편향, 데이터 품질**이 사회 문제가 된다. CED는 이 단원에서 학생이 **데이터 수집의 책임**을 인식하기를 요구한다. MCQ에서 시나리오 문제로 1-2문제 출제 가능.

### 4.1.A — 개인정보 위험 (CED 4.1.A.1)

> **"컴퓨터 사용 시 개인 프라이버시는 위험에 처해 있다. 새 프로그램 개발 시, 프로그래머는 사용자의 개인 프라이버시를 보호하려 노력해야 한다."**

#### 비유 — 일기장과 대형 데이터베이스

여러분의 일기장은 자물쇠로 잠겨 있다. 자물쇠를 열 수 있는 사람은 본인뿐. 그런데 일기장을 인터넷에 올린다고 하자. 누가 볼 수 있는지, 얼마나 오래 남는지 알 수 없다.

소셜 미디어, 쇼핑 앱, 위치 서비스가 모은 데이터도 마찬가지다. 한번 모아지면 **유출, 해킹, 제3자 판매** 위험이 있다. 프로그래머는 "정말 이 데이터가 필요한가?", "어떻게 안전하게 보관할까?", "사용자에게 어떤 동의를 받았는가?"를 매번 자문해야 한다.

### 4.1.B — 알고리즘 편향 (CED 4.1.B.1, 4.1.B.2, 4.1.B.3)

#### 알고리즘 편향(Algorithmic Bias)이란

> **"특정 사용자 그룹에 불공정한 결과를 만드는, 프로그램의 시스템적·반복적 오류."**

#### 어떻게 발생하는가 — 학습 데이터의 편향

대학 입시 알고리즘이 과거 합격자 데이터로 학습되었다고 하자. 과거에 특정 지역/성별/인종이 차별받았다면, 알고리즘은 **그 차별을 그대로 학습**한다. 그래서 미래의 지원자 평가도 그 편향대로 한다.

#### 시험 출제 시나리오 예

> "음성 인식 앱이 여성과 비백인 사용자에게 정확도가 떨어진다. 가장 가능성 높은 원인은?"
> 
> **답**: 학습 데이터가 백인 남성 위주로 수집되어 algorithmic bias 발생.

### 4.1.B.3 — 데이터 품질의 함정

> **"불완전(incomplete)하거나 부정확(inaccurate)한 데이터셋은 프로그램이 잘못 작동하거나 비효율적이게 만들 수 있다."**

#### 예

- 환자 의료 기록 일부가 누락 → 진단 알고리즘 오작동
- 옛 지도 데이터 사용 → 새로 생긴 도로 미반영
- 한쪽 그룹의 데이터만 풍부 → 다른 그룹 예측 불가

**프로그래머의 책임**: 데이터셋이 충분한지, 최신인지, 균형 잡혔는지 점검.

### 4.1.C — 적절한 데이터셋 선정 (CED 4.1.C.1)

> **"데이터셋의 내용은 특정 질문/주제와 관련될 수 있고, 다른 질문/주제에는 부적절할 수 있다."**

#### 예

- "지난 달 강수량 데이터"로 "내년 강수량"을 예측? **위험**. 한 달은 너무 짧음.
- "20대의 음악 취향 데이터"로 "60대 마케팅"? **부적절**. 다른 인구 통계.

데이터셋의 **수집 목적과 사용 목적이 일치하는지** 확인 필수.

### 한 줄 요약

> **데이터 수집은 책임. 프라이버시 보호 + 편향 인식 + 품질 점검 + 적절한 사용. MCQ 시나리오 1-2문제 대비.**

---

## 3. CED 4.2 — 데이터셋 도입

### 데이터셋이란 (CED 4.2.A.1)

> **"데이터셋(data set)은 특정한 정보 조각들의 모음."**

예: 학교의 모든 학생 점수, 한 도시의 매일 기온, 음악 플레이리스트의 곡 목록.

### 데이터셋 처리의 본질 (CED 4.2.A.2)

> **"데이터셋은 문제 해결이나 질문에 답하기 위해 조작·분석된다. 데이터셋 안의 값들은 한 번에 하나씩 접근하여 처리된다."**

핵심 표현: **"한 번에 하나씩(one at a time)"**. 이게 모든 컬렉션 알고리즘의 본질이다. 30개의 데이터를 동시에 보지 않는다. 첫 번째 → 두 번째 → ... → 마지막. 이 순회(traversal)가 모든 알고리즘의 기반.

### 다이어그램으로 표현 (CED 4.2.A.3)

> **"데이터는 차트나 표로 시각화할 수 있다. 이 시각화는 알고리즘 계획에 도움이 된다."**

예시:
```
점수표
┌─────┬──────┐
│이름 │ 점수 │
├─────┼──────┤
│철수 │  90  │
│영희 │  85  │
│민수 │  78  │
│지영 │  95  │
└─────┴──────┘
```

이런 표를 보면 "이름 배열 + 점수 배열" 또는 "Student 객체의 ArrayList"로 자연스럽게 변환된다.

### 한 줄 요약

> **데이터셋 = 관련 정보의 모음. "한 번에 하나씩" 처리가 본질. 코드 전에 차트/표로 시각화하면 알고리즘이 보인다.**

---

## 4. CED 4.3 — 배열 (Array) 생성과 접근

### 왜 배열인가 — 메모리 관점

배열은 **연속된 메모리 칸**에 같은 타입 값을 저장한다.

```
int[] scores = {90, 85, 78, 95, 88};

메모리:
주소  4000  4004  4008  4012  4016
값  │  90 │  85 │  78 │  95 │  88 │
인덱스  0    1    2    3    4
```

각 int는 4바이트, 5개 = 20바이트가 **연속된 자리**에 저장됨. 이게 배열의 본질이고, 다음 모든 특성이 이 메모리 구조에서 파생된다.

### 왜 인덱스가 0부터 시작하는가

이게 항상 헷갈리는 부분. 메모리 관점에서 풀어보자.

배열 `scores`는 첫 번째 원소의 **시작 주소**(예: 4000)를 갖는다. `scores[i]`에 접근하려면:

```
주소 = 시작 주소 + i × 원소 크기
scores[0] → 4000 + 0 × 4 = 4000  ✅ 첫 원소
scores[1] → 4000 + 1 × 4 = 4004  ✅ 두 번째
scores[i] → 4000 + i × 4
```

만약 인덱스가 1부터 시작했다면 `주소 = 시작 주소 + (i-1) × 4`가 되어 매번 -1 연산이 필요. 비효율. **0부터 시작이 메모리 계산에 자연스럽다.**

이 한 가지 사실에서 다음 결과가 나온다:
- 첫 번째 원소: `arr[0]`
- 마지막 원소: `arr[arr.length - 1]` (length가 5면 마지막은 4)
- 유효 인덱스 범위: `0 ~ length - 1`

### 4.3.A.1 — 배열의 정의

> **"배열은 같은 타입의 여러 값을 저장한다. 값은 primitive 또는 객체 참조일 수 있다."**

#### 핵심 제약: "같은 타입"

```java
int[] scores = {90, 85.5, 78};   // ❌ 컴파일 에러 (85.5는 double)
```

배열은 같은 타입만 허용. 메모리 관점에서 보면, 각 원소가 **고정 크기**를 차지해야 인덱스로 위치 계산이 가능하기 때문.

### 4.3.A.2 — 길이는 생성 시 고정 (CED)

> **"배열의 길이는 생성 시점에 정해지고, 변경할 수 없다. 길이는 length 속성으로 접근."**

#### 왜 변경 불가인가

배열은 **연속된 메모리 블록**. 만들고 나서 늘리려면 그 옆 칸이 비어 있어야 함. 다른 변수가 그 자리를 이미 차지했으면 늘릴 방법이 없다. 그래서 "처음 정한 크기 그대로 사용". 더 큰 배열이 필요하면 새로 만들어야 함.

#### length는 필드, 메서드 아님!

```java
arr.length        // ✅ OK (필드 = 변수)
arr.length()      // ❌ 컴파일 에러
```

이게 시험 빈출 함정. **String은 `s.length()`(메서드), 배열은 `arr.length`(필드)**. 헷갈리지 말 것.

### 4.3.A.3 — 기본값으로 초기화 (CED)

> **"`new`로 배열 생성 시 모든 원소가 데이터 타입의 default value로 초기화된다. int=0, double=0.0, boolean=false, 참조 타입=null."**

```java
int[] a = new int[3];           // {0, 0, 0}
double[] b = new double[3];     // {0.0, 0.0, 0.0}
boolean[] c = new boolean[3];   // {false, false, false}
String[] d = new String[3];     // {null, null, null}
```

#### 왜 자동 초기화인가

C/C++에서는 배열 만들면 쓰레기 값이 들어 있어 버그 원천. Java는 **모든 원소에 강제로 default 부여** — 안전하지만 약간 느림.

#### 함정: 참조 타입 배열의 null

```java
String[] names = new String[3];   // {null, null, null}
System.out.println(names[0].length());   // NullPointerException!
```

`names[0]`은 null이라 아무 메서드도 못 부른다. 사용 전 각 원소에 실제 객체 할당 필요:

```java
names[0] = "Alice";
names[1] = "Bob";
names[2] = "Carol";
```

### 4.3.A.4 — 초기화 리스트 (CED)

> **"초기화 리스트(initializer list)로 배열을 생성·초기화할 수 있다."**

```java
int[] arr1 = {10, 20, 30};                    // 초기화 리스트
int[] arr2 = new int[]{10, 20, 30};           // 동일
int[] arr3 = new int[3];                      // {0, 0, 0}로 시작
```

#### 시험 함정: 분리된 대입

```java
int[] arr;
arr = {10, 20, 30};                // ❌ 컴파일 에러!
arr = new int[]{10, 20, 30};       // ✅ OK
```

`{...}` 리터럴은 **선언과 동시에만** 사용 가능. 나중에 대입할 때는 `new int[]{...}` 필수.

### 4.3.A.5 — 대괄호로 접근 (CED)

> **"대괄호 [] 로 1D 배열의 원소를 접근하고 수정한다."**

```java
arr[2] = 100;                    // 인덱스 2 수정
int x = arr[0];                  // 인덱스 0 읽기
arr[arr.length - 1] = 99;        // 마지막 원소 수정
```

### 4.3.A.6 — 인덱스 범위와 ArrayIndexOutOfBoundsException (CED)

> **"유효 인덱스는 0부터 length-1까지(포함). 범위 밖 사용 시 `ArrayIndexOutOfBoundsException` 발생."**

```java
int[] arr = new int[5];   // 유효 인덱스 0~4
arr[5] = 100;             // 런타임 에러: ArrayIndexOutOfBoundsException
arr[-1] = 100;            // 런타임 에러
```

#### 왜 컴파일 에러가 아니고 런타임 에러인가

```java
int i = 5;
arr[i] = 100;   // i가 변수라서 컴파일 시점에 5인지 알 수 없음
```

인덱스 값은 보통 변수나 계산 결과라서, 컴파일러가 미리 검사 불가. **실행 중에야 비로소 범위 위반이 드러남** → 런타임 예외.

### 한 줄 요약

> **배열 = 같은 타입, 고정 크기, 연속 메모리, 0부터 시작 인덱스. `new`로 만들면 default value, length는 필드, 범위 밖 = AIOOBE.**

---

## 5. CED 4.4 — 배열 순회 (Traversal)

### 왜 순회가 핵심인가

배열에 100개의 데이터가 있고 평균을 구해야 한다. 한 번에 모두 더할 방법은 없다. **하나씩 차례로 방문**해야 한다. 이 "하나씩 방문"이 순회(traversal). Unit 4의 모든 알고리즘은 결국 순회의 변형.

### 두 가지 순회 방법

#### 1. Indexed for loop (인덱스 기반)

```java
for (int i = 0; i < arr.length; i++) {
    arr[i] = arr[i] * 2;     // i를 알고, 원소 수정 가능
}
```

- **언제 쓰는가**: 인덱스가 필요할 때 (위치 출력, 일부만 순회, 원소 수정)

#### 2. Enhanced for loop (향상된 for문)

```java
for (int v : arr) {
    System.out.println(v);    // v는 현재 원소의 복사본
}
```

- **언제 쓰는가**: 원소만 차례로 읽을 때 (간결)

### 4.4.A.1 — 순회의 정의 (CED)

> **"배열의 순회(traversal)는 모든 또는 순서가 정해진 원소들에 접근하기 위해 반복문을 사용하는 것."**

#### 4.4.A.2 — Indexed 순회

> **"indexed for 또는 while 루프로 순회 시, 원소들은 인덱스로 접근된다."**

#### 4.4.A.3 — Enhanced for 변수

> **"enhanced for 루프 헤더는 변수 하나를 포함. 매 iteration마다 그 변수에는 인덱스 없이 원소의 **복사본**이 할당된다."**

이 "복사본(copy)"이 핵심. 다음 EK가 그 결과.

### 4.4.A.4 — Enhanced for의 값 복사 함정 (CED)

> **"enhanced for 변수에 새 값을 대입해도 배열에 저장된 값은 바뀌지 않는다."**

#### 시험 단골 트레이싱

```java
int[] arr = {1, 2, 3};
for (int v : arr) {
    v = v * 2;   // 복사본만 변경
}
System.out.println(arr[0]);   // ?
```

**답: 1.** `v`는 `arr[0]`의 값 1을 복사한 별도 변수. `v = 2`는 복사본만 변경. 원본 배열은 그대로.

#### 메커니즘 시각화

```
iteration 1:
  arr[0] = 1
  v ← arr[0]의 값 1 복사  →  v = 1
  v = v * 2                →  v = 2 (복사본만 바뀜)
  arr[0]은 여전히 1

iteration 2:
  arr[1] = 2
  v ← arr[1]의 값 2 복사  →  v = 2
  ...
```

**v와 arr[i]는 별개의 변수**. v 변경은 arr에 반영되지 않음.

### 4.4.A.5 — 객체 배열에서는 다른 동작 (CED)

> **"배열이 객체 참조를 저장하면, enhanced for 변수의 메서드 호출로 속성을 수정할 수 있다. 단, 배열에 저장된 객체 참조 자체는 바뀌지 않는다."**

#### 코드

```java
class Point {
    int x;
    void setX(int val) { this.x = val; }
}

Point[] arr = { new Point(), new Point(), new Point() };
arr[0].x = 1; arr[1].x = 2; arr[2].x = 3;

for (Point p : arr) {
    p.setX(0);   // 객체의 메서드 호출 → 객체 내부 변경
}

System.out.println(arr[0].x);   // 0 (변경됨!)
```

#### 왜 이건 반영되는가 (Unit 3 복습)

`p`는 `arr[0]`이 가리키는 **Point 객체의 주소를 복사**한다 (참조 복사). p와 arr[0]은 같은 Point 객체를 가리킨다. `p.setX(0)`은 **그 객체의 내부**를 변경 → arr[0]에서도 같은 객체를 보므로 변경 반영.

#### 그러나 객체 교체는 반영 안 됨

```java
for (Point p : arr) {
    p = new Point();   // 새 Point를 p에 대입 (배열은 무관)
}
System.out.println(arr[0].x);   // 여전히 0 (또는 원래 값)
```

`p`가 다른 객체를 가리키게 바뀐 것 뿐. 배열 안의 참조는 그대로.

#### 정리

| 작업 | 원본 배열 영향 |
|-----|------------|
| primitive 배열, `v = ...` | ❌ 안 됨 |
| 객체 배열, `p = new...` | ❌ 안 됨 |
| 객체 배열, `p.setX(...)`, `p.field = ...` | ✅ 됨 |

### 4.4.A.6 — Enhanced for ↔ Indexed for 변환 (CED)

> **"enhanced for로 작성된 코드는 indexed for나 while 루프로 다시 쓸 수 있다."**

```java
// Enhanced
for (int v : arr) {
    sum += v;
}

// Indexed (동일 결과)
for (int i = 0; i < arr.length; i++) {
    int v = arr[i];
    sum += v;
}
```

**기능적으로 동일**. 단, **enhanced로는 못 하는 것**이 있다:
- 인덱스 사용 (현재 위치 출력 등)
- 원소 수정 (값 복사라서)
- 일부만 순회 (예: 짝수 인덱스만)

### 한 줄 요약

> **순회 = 한 번에 하나씩 방문. indexed for는 인덱스 사용·수정 가능, enhanced for는 값 복사라서 단순 읽기만. 객체 배열에서 enhanced for + 메서드 호출은 원본 객체 변경 반영.**

---

## 6. CED 4.5 — 표준 배열 알고리즘 9가지

### 왜 "표준 알고리즘"인가

CED는 9가지 패턴을 명시적으로 학습 목표로 지정한다. 이 9가지가 **시험 문제와 FRQ의 99%를 구성**한다. 빠짐없이 손에 익혀야 한다.

CED 4.5.A.1의 정확한 9가지:
1. 최솟값 또는 최댓값 결정
2. 합계 또는 평균 계산
3. 적어도 하나의 원소가 특정 속성을 가지는지 (Exists)
4. 모든 원소가 특정 속성을 가지는지 (For-all)
5. 특정 속성을 가진 원소의 개수 (Count)
6. 모든 연속 쌍 접근
7. 중복 원소의 존재/부재
8. 좌/우 shift 또는 rotate
9. 원소 순서 reverse

각각을 깊이 본다.

### 알고리즘 1 — 합계와 평균

```java
int[] arr = {85, 92, 78, 95, 88};

int sum = 0;
for (int v : arr) {
    sum += v;
}
double avg = (double) sum / arr.length;
```

#### 왜 `(double)` 캐스팅이 필요한가

```java
double avg = sum / arr.length;   // ❌ sum=438, arr.length=5 → 정수 나눗셈 87
```

`sum`과 `arr.length`가 **둘 다 int**라 `/`도 정수 나눗셈. 결과 87. 소수점 절삭. `(double) sum`으로 한쪽을 double로 만들면 자동으로 실수 나눗셈.

#### 시험 빈출

이 캐스팅 누락이 가장 흔한 감점 항목. 평균 계산이 나오면 즉시 `(double)` 떠올려야 한다.

### 알고리즘 2 — 최댓값/최솟값

```java
int[] arr = {34, 12, 67, 23, 89, 45};

int max = arr[0];   // 첫 원소로 시작
for (int i = 1; i < arr.length; i++) {
    if (arr[i] > max) max = arr[i];
}
// max = 89
```

#### 왜 `arr[0]`으로 초기화하는가

`max = 0;`으로 시작하면 위험:
```java
int[] arr = {-10, -20, -5};   // 모두 음수
int max = 0;
for (int v : arr) if (v > max) max = v;
// max = 0 (틀림! 진짜 max는 -5)
```

배열에 모두 음수면 0이 max로 잘못 보고됨. **첫 원소로 시작**하면 항상 배열 안의 값이 max가 됨 → 안전.

#### Edge case: 빈 배열

`arr.length == 0`이면 `arr[0]` 접근 시 AIOOBE. AP FRQ는 보통 "배열이 비어있지 않다"는 precondition으로 보장. 알아두면 좋음.

### 알고리즘 3 — Exists (적어도 하나)

```java
boolean hasNegative = false;
for (int v : arr) {
    if (v < 0) {
        hasNegative = true;
    }
}
```

#### 패턴

- 초기값: `false`
- 조건 만족 시: `true`로 설정
- 한 번 true가 되면 계속 true (덮어쓸 일 없음)

### 알고리즘 4 — For-all (모든 원소)

```java
boolean allPositive = true;
for (int v : arr) {
    if (v <= 0) {
        allPositive = false;
    }
}
```

#### 패턴 (Exists의 반대)

- 초기값: `true`
- **반례** 발견 시: `false`로 설정
- 한 번 false가 되면 계속 false

#### 시험 함정 — 초기값과 조건 방향

```java
// 모든 양수 확인 (틀린 코드)
boolean all = false;
for (int v : arr) {
    if (v > 0) all = true;
}
// 하나라도 양수면 true → 의미가 다름!
```

**For-all은 항상 "반례 찾기"로 접근**: 초기값 `true`, **하나라도 위반하면** false.

### 알고리즘 5 — Count (개수)

```java
int count = 0;
for (int v : arr) {
    if (v >= 80) count++;
}
```

조건 만족 시 카운터 증가. 가장 단순한 패턴.

### 알고리즘 6 — 연속 쌍 (Consecutive Pairs)

```java
for (int i = 0; i < arr.length - 1; i++) {
    int sum = arr[i] + arr[i + 1];
    System.out.println(arr[i] + " + " + arr[i+1] + " = " + sum);
}
```

#### 왜 `< arr.length - 1`?

`arr[i + 1]`에 접근하려면 `i + 1 < arr.length` → `i < arr.length - 1`. 마지막 i는 `length - 2`. 이때 `arr[i+1]`은 `arr[length-1]` = 마지막 원소.

`< arr.length`로 잘못 쓰면 마지막 i = length-1, `arr[length]` 접근 → AIOOBE.

#### 일반화

k개 연속 원소를 보려면 `i <= length - k`.

### 알고리즘 7 — 중복 (Duplicates)

```java
int[] arr = {3, 7, 2, 7, 5, 3};
boolean hasDup = false;
for (int i = 0; i < arr.length; i++) {
    for (int j = i + 1; j < arr.length; j++) {
        if (arr[i] == arr[j]) {
            hasDup = true;
        }
    }
}
```

#### 왜 이중 루프인가

각 원소를 그 **이후의 모든 원소와 비교**해야 한다. `j = i + 1`부터 시작하면 같은 쌍을 두 번 비교하지 않음 (예: (i=2, j=4)와 (i=4, j=2)는 같은 쌍).

#### 복잡도

이중 루프 → O(n²). 큰 배열에서는 느리다. 더 빠른 방법(HashSet 등)은 AP 범위 밖.

### 알고리즘 8 — Shift / Rotate

#### 왼쪽 shift (앞으로 밀기, 마지막은 0)

```java
int[] arr = {1, 2, 3, 4, 5};
for (int i = 0; i < arr.length - 1; i++) {
    arr[i] = arr[i + 1];
}
arr[arr.length - 1] = 0;
// 결과: {2, 3, 4, 5, 0}
```

#### 오른쪽 shift (뒤로 밀기, 첫 자리는 0)

```java
int[] arr = {1, 2, 3, 4, 5};
for (int i = arr.length - 1; i >= 1; i--) {   // 뒤에서 앞으로!
    arr[i] = arr[i - 1];
}
arr[0] = 0;
// 결과: {0, 1, 2, 3, 4}
```

#### 왜 오른쪽 shift는 뒤에서 앞으로?

앞에서 뒤로 가면:
```
{1, 2, 3, 4, 5}
i=1: arr[1] = arr[0] = 1 → {1, 1, 3, 4, 5}
i=2: arr[2] = arr[1] = 1 → {1, 1, 1, 4, 5}
...
```
1로 다 덮여버린다. **읽으려는 값이 이미 덮어써진** 상태.

뒤에서 앞으로 가면:
```
i=4: arr[4] = arr[3] = 4 → {1, 2, 3, 4, 4}  (뒤에서 시작, 안 읽은 부분 덮음)
i=3: arr[3] = arr[2] = 3 → {1, 2, 3, 3, 4}
...
```
**아직 안 읽은 앞쪽**을 보존. 정상 작동.

#### Rotate (마지막을 첫 자리로)

```java
int[] arr = {1, 2, 3, 4, 5};
int last = arr[arr.length - 1];
for (int i = arr.length - 1; i >= 1; i--) {
    arr[i] = arr[i - 1];
}
arr[0] = last;
// 결과: {5, 1, 2, 3, 4}
```

shift + 빈자리에 마지막 값.

### 알고리즘 9 — Reverse

```java
int[] arr = {1, 2, 3, 4, 5};
for (int i = 0; i < arr.length / 2; i++) {
    int temp = arr[i];
    arr[i] = arr[arr.length - 1 - i];
    arr[arr.length - 1 - i] = temp;
}
// 결과: {5, 4, 3, 2, 1}
```

#### 왜 `length / 2`까지만?

전체를 다 돌면 같은 쌍을 두 번 swap → 원래대로 돌아감. 절반만 돌면 충분.
- length=5: i=0,1 (가운데 2는 가만히 둠)
- length=4: i=0,1 (모두 swap)

### 한 줄 요약

> **9가지 표준 알고리즘은 시험 문제와 FRQ의 99%. 평균은 (double) 캐스팅, max/min은 arr[0]으로 시작, exists/for-all 초기값 반대, 연속 쌍은 length-1, shift는 방향 주의, reverse는 length/2.**

---

## 7. CED 4.6 — 텍스트 파일 (Scanner + File)

### 왜 파일이 필요한가

지금까지 코드 안에 `int[] arr = {1,2,3}`처럼 직접 데이터를 적었다. 그러나 현실에서 데이터는 **외부 파일**에 있다 — 학생 명부, 매출 기록, 센서 로그. 프로그램 실행 후에도 **데이터가 남아 있어야** 하기 때문.

### 4.6.A.1 — 파일의 정의 (CED)

> **"파일은 프로그램이 실행 중이 아니어도 보존되는 데이터의 저장소. 프로그램 실행 중 데이터를 가져올 수 있다."**

#### RAM(메모리) vs Disk(파일) — "왜 파일이 영속인가"

| 저장 위치 | 용량 | 속도 | 전원 OFF 시 | 프로세스 종료 시 |
|----------|----|-----|-----------|-------------|
| **RAM** (변수, 배열, ArrayList) | 작음 (GB) | 빠름 (ns) | **사라짐** | **사라짐** |
| **Disk/SSD** (파일) | 큼 (TB) | 느림 (ms) | **남음** | **남음** |

`int[] arr = {1,2,3}`은 RAM에 있다. 프로그램이 끝나면 사라진다. 학생 명부를 저장하려면 **다음 실행에서도 읽을 수 있어야** 하므로 디스크의 파일에 기록한다.

#### 왜 ArrayList는 파일이 될 수 없나

ArrayList는 RAM 객체. 프로그램 종료 = 객체 사라짐. 영구 저장이 목적이라면 ArrayList의 내용을 **파일로 직렬화**(write)하거나 **파일에서 읽어 ArrayList로 복원**해야 한다. AP는 후자(읽기)만 다룬다.

### 4.6.A.2 — File과 Scanner (CED)

> **"파일은 File과 Scanner 클래스로 프로그램에 연결할 수 있다."**

#### 두 클래스의 역할 분리

```
[디스크의 data.txt]   ← 실제 파일
        ↑
        │  (1) File 객체가 "이 파일을 가리킴" — 메타정보만
        │
   File f = new File("data.txt");
        │
        │  (2) Scanner 객체가 File을 받아 실제 토큰 읽기
        ▼
   Scanner sc = new Scanner(f);
        │
   sc.nextInt(), sc.nextLine() ...   ← 실제 데이터 읽기
```

| 클래스 | 역할 | 비유 |
|------|----|----|
| **File** | 파일 경로·메타정보 (어디 있는지 / 존재 여부) | 책 표지의 청구기호 |
| **Scanner** | 실제 토큰을 한 개씩 꺼내는 reader | 책을 펴서 한 줄씩 읽어주는 사람 |

File 혼자서는 데이터를 못 꺼낸다 — Scanner와 짝지어야 비로소 읽기가 시작된다.

### 4.6.A.3 — File 생성자 (CED)

> **"`File(String str)`로 파일을 연다. str은 파일 경로 이름."**

```java
File myFile = new File("data.txt");
```

### 4.6.A.4 — IOException 처리 (CED)

> **"File을 사용할 때, 파일을 못 열었을 때 어떻게 할지 명시해야 한다. 한 가지 방법은 메서드 헤더에 `throws IOException`을 추가하는 것. 잘못된 파일 이름이면 프로그램은 종료된다."**

#### 왜 throws가 필요한가

파일 작업은 "**Checked Exception**"을 던질 수 있다 — Java가 컴파일 시점에 강제로 예외 처리를 요구한다. 두 가지 처리법:
- **try-catch**: 예외를 잡아서 처리 (AP 범위 밖)
- **throws**: "이 메서드는 IOException을 던질 수 있음"이라고 선언, 호출자에게 책임 떠넘김

AP CSA는 **throws 방식만** 사용한다.

#### 관용 코드

```java
import java.io.*;
import java.util.Scanner;

public static void main(String[] args) throws IOException {
    File myFile = new File("data.txt");
    Scanner scan = new Scanner(myFile);
    // ... 파일 읽기
    scan.close();
}
```

### 4.6.A.5 — import 필요 (CED)

> **"File과 IOException은 java.io 패키지의 일부. import 문이 필요하다."**

```java
import java.io.File;
import java.io.IOException;
import java.util.Scanner;
```

### 4.6.A.6 — Scanner 생성자 1개 + 메서드 7개 (CED Quick Reference)

CED 4.6.A.6은 정확히 **생성자 1개 + 메서드 7개 = 총 8개 항목**만 출제 범위로 명시 (CED 원문: "The following Scanner methods and constructor"):

| 메서드 | 반환 | 설명 | 발생 가능 예외 |
|-------|-----|-----|--------------|
| `Scanner(File f)` | (생성자) | File을 받는 생성자 | `FileNotFoundException`(IOException 하위) |
| `int nextInt()` | int | 다음 int 읽기 | **`InputMismatchException`** (다음 토큰이 int가 아니거나 범위 밖) |
| `double nextDouble()` | double | 다음 double 읽기 | **`InputMismatchException`** |
| `boolean nextBoolean()` | boolean | 다음 boolean 읽기 | **`InputMismatchException`** |
| `String nextLine()` | String | 다음 줄 전체 (개행 전까지) | — |
| `String next()` | String | 다음 토큰 (공백/개행 구분) | — |
| `boolean hasNext()` | boolean | 읽을 게 남았으면 true | — |
| `void close()` | void | Scanner 닫기 | — |

> **시험 출제**: CED 4.6.A.6은 `nextInt()`/`nextDouble()`/`nextBoolean()`이 잘못된 타입 입력 시 **`InputMismatchException`**을 발생시킨다고 명시. MCQ에서 "다음 코드 실행 시 발생하는 예외는?" 형태로 출제 가능. 즉시 떠올려야 한다.

#### EXCLUSION (CED 명시)

- **`Scanner(System.in)`**: 키보드 입력은 시험 범위 외
- **`hasNextInt()`, `hasNextLine()`, `hasNextDouble()`**: QR에 없음 → 항상 `hasNext()` 사용
- 정규표현식 (`split` 매개변수의 특수 문자): 시험 범위 외

### 4.6.A.7 — nextLine과 다른 메서드 혼용 (CED EXCLUSION)

> **"nextLine과 다른 Scanner 메서드를 같은 입력 소스에서 함께 쓰면 공백 처리 차이로 코드 조정이 필요할 수 있다. AP 시험은 이런 코드 작성/분석을 요구하지 않는다."**

즉 `nextInt() + nextLine()` 같은 혼용 문제는 **출제 안 됨**. 안심.

### 4.6.A.8 — String.split (CED)

> **"`String[] split(String del)`은 String을 del로 분할한 String 배열을 반환."**

```java
String line = "Alice,90,A";
String[] parts = line.split(",");
// parts = {"Alice", "90", "A"}
```

#### 활용 — CSV 파일 읽기

```java
Scanner scan = new Scanner(new File("students.csv"));
while (scan.hasNext()) {
    String line = scan.nextLine();
    String[] parts = line.split(",");
    String name = parts[0];
    int score = Integer.parseInt(parts[1]);
    String grade = parts[2];
    // 처리
}
scan.close();
```

#### EXCLUSION

`del` 매개변수에 정규표현식의 특수 문자(`*`, `.` 등)를 사용하는 것은 시험 범위 외. 단순 구분자(쉼표, 공백, `|` 등)만.

### 4.6.A.9 — hasNext로 종료 검사 (CED)

> **"while 루프와 hasNext 메서드로 파일에 읽을 원소가 남았는지 검사."**

```java
while (scan.hasNext()) {
    int v = scan.nextInt();
    sum += v;
}
```

이게 **파일 읽기의 표준 패턴**. 거의 모든 파일 처리 코드가 이 형태.

### 4.6.A.10 — close 호출 (CED)

> **"파일 사용 후 close 메서드로 닫아야 한다."**

```java
scan.close();
```

#### 왜 닫아야 하는가

파일을 열면 OS가 그 파일에 대한 자원을 잡고 있다. 안 닫으면 자원이 계속 점유되어 다른 프로그램이 그 파일에 접근 못할 수 있다. **항상 close**.

### 시험 빈출 함정

#### throws 누락

```java
public static void main(String[] args) {           // ← throws 없음
    Scanner scan = new Scanner(new File("f"));    // ❌ 컴파일 에러
}
```

#### import 누락

```java
public static void main(String[] args) throws IOException {
    File f = new File("data.txt");   // ❌ File 못 찾음 (import 안 했으면)
}
```

### 한 줄 요약

> **파일 읽기 = `import` + `throws IOException` + `new Scanner(new File(name))` + `while (hasNext())` + `close()`. 7개 Scanner 메서드만 시험 범위.**

---

## 8. CED 4.7 — Wrapper Classes (Integer, Double)

### 왜 Wrapper가 필요한가

Java의 **primitive 타입**(int, double, boolean)은 **객체가 아니다**. 그러나 ArrayList나 다른 컬렉션은 **객체만** 저장 가능. 이 충돌을 해결하기 위해 Java는 primitive를 객체처럼 감싸는 **Wrapper 클래스**를 제공.

| Primitive | Wrapper |
|-----------|--------|
| `int` | `Integer` |
| `double` | `Double` |
| `boolean` | `Boolean` |

### 4.7.A.1 — Integer/Double은 immutable (CED)

> **"Integer와 Double 클래스는 java.lang 패키지의 일부. **Integer/Double 객체는 immutable** — 한번 생성되면 속성을 바꿀 수 없다."**

#### 왜 immutable인가

`Integer x = 5;`라는 객체를 만들었다고 하자. 누군가 `x.value = 10;`처럼 바꿀 수 있다면 어떻게 될까? `5`라고 알고 있던 다른 코드들이 모두 잘못된 결과를 낸다.

immutable은 이런 위험을 원천 차단한다. **한번 만들어진 Integer/Double은 영원히 같은 값**. 안전.

#### Defensive Copy 불필요 (Unit 3 연결)

```java
public class Box {
    private Integer count;
    public Box(Integer count) {
        this.count = count;   // ✅ OK! Integer는 immutable이라 외부 변경 불가
    }
}
```

mutable 객체(ArrayList 등)와 달리 Integer는 방어적 복사 불필요.

### 4.7.A.2 — Autoboxing (CED)

> **"Autoboxing은 Java 컴파일러가 primitive 타입과 wrapper 클래스 사이의 자동 변환. int를 Integer로, double을 Double로."**

#### 적용 시점

- primitive 값을 wrapper 매개변수에 전달할 때
- primitive 값을 wrapper 변수에 대입할 때

```java
Integer a = 5;                    // 자동: Integer.valueOf(5)
ArrayList<Integer> list = new ArrayList<>();
list.add(10);                     // 자동: 10 → Integer
```

### 4.7.A.3 — Unboxing (CED)

> **"Unboxing은 wrapper에서 primitive로의 자동 변환."**

#### 적용 시점

- wrapper 객체를 primitive 매개변수에 전달할 때
- wrapper 객체를 primitive 변수에 대입할 때

```java
Integer a = 5;
int b = a;                        // 자동 unboxing (Java 컴파일러가 내부적으로 처리)
int x = list.get(0);              // 자동: Integer → int
```

> ⚠️ **시험 표기 주의**: `Integer.intValue()` / `Double.doubleValue()` 메서드는 **Java Quick Reference에 없음**. autoboxing/unboxing은 **자동**이므로 학생이 직접 호출할 필요도 없고, 답안에 쓰면 안 된다. 위 주석의 "내부적으로"는 컴파일러 동작 설명일 뿐 — 학생이 작성하는 코드에는 등장하지 않는다.

#### 함정: null Unboxing

```java
Integer a = null;
int b = a;   // ❌ NullPointerException!
```

null 객체를 primitive로 자동 변환하려는 순간 NPE가 발생한다 (내부적으로 unboxing이 호출되지만 객체가 없음).

### 4.7.A.4, 4.7.A.5 — parseInt, parseDouble (CED)

```java
int n = Integer.parseInt("42");          // String → int
double d = Double.parseDouble("3.14");   // String → double
```

둘 다 **static 메서드** (Integer.parseInt, Double.parseDouble — 객체 없이 클래스 이름으로 호출).

#### 함정

```java
Integer.parseInt("abc");      // NumberFormatException
Integer.parseInt("3.14");     // NumberFormatException ("3.14"는 int 아님)
Integer.parseInt("3");        // 3 (OK)
Double.parseDouble("3.14");   // 3.14 (OK)
```

### Wrapper의 함정 — Integer cache와 ==

```java
Integer a = 100, b = 100;
Integer c = 200, d = 200;
System.out.println(a == b);   // true
System.out.println(c == d);   // false (!)
```

#### 왜?

Java는 **[-128, 127] 범위의 Integer를 미리 캐시**한다. 그 범위의 Integer는 **같은 객체를 공유** → `==`로 비교하면 주소가 같아서 true. 범위 밖(200)은 매번 새 객체 → 다른 주소 → false.

#### 안전 규칙

> **wrapper 객체끼리 비교는 `.equals()`. 또는 primitive 변수에 자동 unboxing 시킨 뒤 `==`. `==`로 wrapper 직접 비교는 위험.**

```java
a.equals(b)       // ✅ 항상 값 비교 (시험 권장)

// 또는 자동 unboxing 활용
int aVal = a;
int bVal = b;
aVal == bVal      // ✅ primitive 비교
```

> ⚠️ **시험에서는 `.equals()`만 사용.** `a.intValue() == b.intValue()`처럼 `intValue()`를 직접 호출하는 코드는 **Quick Reference에 없는 메서드 사용**이므로 답안에 쓰지 않는다. 자동 unboxing을 쓰거나 `.equals()`를 쓴다.

### Java QR 등재 상수 — Integer.MIN_VALUE / Integer.MAX_VALUE

> **CED Java Quick Reference (p.185) 원문**:
> - `Integer.MIN_VALUE` = "The minimum value represented by an `int` or `Integer`" (= -2,147,483,648)
> - `Integer.MAX_VALUE` = "The maximum value represented by an `int` or `Integer`" (= 2,147,483,647)

#### 시험 활용 1 — 안전한 max/min 초기화

```java
// 비어있을 가능성 있는 배열에서 최댓값
int max = Integer.MIN_VALUE;
for (int v : arr) {
    if (v > max) max = v;
}
// arr가 비어있으면 max = Integer.MIN_VALUE 그대로
```

`max = arr[0]`로 시작하면 빈 배열에서 AIOOBE. `Integer.MIN_VALUE`로 시작하면 안전. (단, 빈 배열의 max는 의미 없음을 알아야 함.)

#### 시험 활용 2 — 정수 오버플로우 인식

```java
int big = Integer.MAX_VALUE;
big = big + 1;
System.out.println(big);   // -2147483648 (오버플로우로 음수 됨)
```

`Integer.MAX_VALUE + 1` = `Integer.MIN_VALUE`. wrap-around 현상. AP CSA 시험에서 가끔 트레이싱 문제로 출제.

#### Double은?

`Double.MIN_VALUE` / `Double.MAX_VALUE`도 존재하지만 Java QR 등재는 **Integer만**. Double 상수는 시험 범위 외.

### 한 줄 요약

> **Wrapper = primitive를 객체로 감싸기. Integer/Double은 immutable. autoboxing/unboxing은 자동, 그러나 null unboxing은 NPE. wrapper 비교는 .equals() 사용. `Integer.MIN_VALUE`/`MAX_VALUE`는 Java QR 등재 — max/min 초기화·오버플로우 트레이싱에 활용.**

---

## 9. CED 4.8 — ArrayList 메서드

### 왜 ArrayList인가

배열은 크기가 고정. 학생 30명을 위해 만든 배열에 31명을 넣을 수 없다. **크기가 변할 수 있는** 컬렉션이 필요. ArrayList가 그 답.

### 비유 — 호텔 vs 아파트

| 컬렉션 | 비유 | 특징 |
|------|-----|-----|
| **Array** | 30실 아파트 | 입주 후 방 수 변경 불가, 원소 접근 빠름 |
| **ArrayList** | 호텔 | 손님 늘면 방 추가 가능, 원소 삽입/삭제 가능 |

### 4.8.A.1 — ArrayList의 정의 (CED)

> **"ArrayList 객체는 **크기가 가변(mutable in size)**이고 객체 참조를 담는다."**

#### 핵심 제약: "객체 참조만"

```java
ArrayList<int> bad;        // ❌ 컴파일 에러 (primitive 불가)
ArrayList<Integer> good;   // ✅ Wrapper 사용
ArrayList<String> ok;      // ✅
```

ArrayList 내부는 `Object[]`로 구현되어 있어 모든 원소가 Object여야 한다. primitive는 Object가 아니므로 wrapper 필요.

### 4.8.A.2 — 생성자 (CED)

> **"`ArrayList()`는 빈 리스트를 생성한다."**

```java
ArrayList<String> names = new ArrayList<>();
```

처음에는 size=0인 빈 리스트. add()로 원소 추가.

### 4.8.A.3 — Generic Type `<E>` (CED)

> **"Java는 generic 타입 `ArrayList<E>`를 허용. 타입 매개변수 E는 원소의 타입을 지정. ArrayList<E>가 ArrayList보다 선호된다 — 컴파일러가 런타임 에러를 컴파일 시점에 잡을 수 있게 해준다."**

```java
// ✅ Generic 사용 (권장)
ArrayList<String> names = new ArrayList<String>();
ArrayList<Integer> nums = new ArrayList<>();   // diamond operator도 OK

// ❌ Generic 없이 — 시험에서 보면 안 됨
ArrayList list = new ArrayList();
```

#### 왜 generic이 안전한가

```java
ArrayList<String> names = new ArrayList<>();
names.add("Alice");
names.add(42);       // ❌ 컴파일 에러! generic이 String만 허용

// generic 없이
ArrayList list = new ArrayList();
list.add("Alice");
list.add(42);        // 컴파일은 됨, 그러나 String으로 꺼내면 런타임 에러
```

generic은 **컴파일 시점**에 타입을 강제 → 런타임 에러를 미리 차단.

### 4.8.A.4 — import 필요 (CED)

> **"ArrayList는 java.util 패키지의 일부. import 필요."**

```java
import java.util.ArrayList;
```

### 4.8.A.5 — 6개 메서드 (CED Quick Reference)

CED는 정확히 6개 메서드만 출제:

| 메서드 | 반환 | 경계 | 설명 |
|-------|-----|-----|-----|
| `int size()` | int | — | 원소 개수 |
| `boolean add(E obj)` | true (항상) | — | 끝에 추가 |
| `void add(int index, E obj)` | void | `0 <= index <= size` | index 위치에 삽입 |
| `E get(int index)` | E | `0 <= index < size` | index 원소 반환 |
| `E set(int index, E obj)` | **이전 원소** | `0 <= index < size` | 교체하고 이전 값 반환 |
| `E remove(int index)` | **제거된 원소** | `0 <= index < size` | 제거하고 뒤 원소 당김 |

#### EXCLUSION — 쓰면 안 되는 메서드

QR에 없는 메서드는 시험에서 **사용 금지**:
- `isEmpty()` → `size() == 0`으로 직접 검사
- `contains(x)` → 직접 루프로 검사
- `indexOf(x)` → 직접 루프로 검사
- `clear()` → 모두 remove하거나 새 리스트 생성

### add(int, E)의 경계 함정

```java
ArrayList<String> list = new ArrayList<>();
list.add("A");          // size = 1
list.add(1, "B");       // ✅ index 1 = size, 끝에 추가하는 효과
list.add(3, "C");       // ❌ size=2, index 3은 범위 밖 (size까지만 허용)
```

`add(int, E)`만 특별히 `index == size`를 허용 — "맨 끝에 삽입"의 의미.

### remove와 set의 반환값 함정

```java
list.add("A"); list.add("B"); list.add("C");
String r = list.remove(1);      // r = "B" (제거된 원소)
                                 // list = [A, C]

String prev = list.set(0, "X"); // prev = "A" (이전 원소)
                                 // list = [X, C]
```

- `remove`: 제거된 원소 반환 (true/false 아님)
- `set`: **이전** 원소 반환 (새 원소 아님)

### Index 기반 remove 주의

```java
ArrayList<Integer> nums = new ArrayList<>();
nums.add(10); nums.add(20); nums.add(30);

nums.remove(0);   // ✅ 인덱스 0의 원소(10) 제거 → [20, 30]
                  // ❌ 값 0이 제거되는 것이 아님
```

QR에 등재된 `remove`는 **`remove(int index)`만**. 값 기반 제거는 시험 범위 밖.

### 4.8.A.6 — 인덱스 범위 (CED)

> **"ArrayList의 인덱스는 0에서 시작, 원소 수 - 1에서 끝."**

배열과 동일하지만 **size가 동적으로 변하기 때문에 유효 범위도 바뀐다**:

```java
ArrayList<Integer> list = new ArrayList<>();
// list.size() == 0,  유효 인덱스 없음
list.add(10);       // size 1, 유효 [0..0]
list.add(20);       // size 2, 유효 [0..1]
list.add(30);       // size 3, 유효 [0..2]
list.remove(0);     // size 2, 유효 [0..1]  ← 범위 다시 줄어듦

list.get(2);        // ❌ size=2이므로 인덱스 2는 IndexOutOfBoundsException
```

**핵심**: `add`/`remove` 후 `size()`를 다시 확인. 루프 직전에 size를 변수에 저장해두고 루프 도중 변경하면 위험.

> **add(int, E) 예외 한 번 더**: `add(i, v)`는 `0 ≤ i ≤ size`까지 허용 — `i = size`이면 끝에 추가. 다른 메서드는 모두 `0 ≤ i ≤ size-1`.

### 한 줄 요약

> **ArrayList = 가변 크기, 객체만, generic 필수, 6개 메서드만 출제. add(int, E)만 size까지 허용. set/remove는 이전/제거된 원소 반환.**

---

## 10. CED 4.9 — ArrayList 순회

### 4.9.A.1 — 순회의 정의 (CED)

> **"ArrayList의 순회는 모든 원소 또는 순서가 정해진 원소들에 접근하기 위해 반복 또는 재귀를 사용하는 것."**

배열 순회와 동일하지만 메서드 호출 형태:

#### Indexed for
```java
for (int i = 0; i < list.size(); i++) {
    System.out.println(list.get(i));
}
```

#### Enhanced for
```java
for (String name : list) {
    System.out.println(name);
}
```

### 4.9.A.2 — 삭제 중 순회의 함정 (CED)

> **"ArrayList 순회 중 원소 삭제는 원소를 건너뛰지 않기 위해 특별한 기법이 필요하다."**

이게 시험 단골이고 가장 많이 틀리는 부분이다. 풀어 설명한다.

#### 함정 시연

```java
ArrayList<Integer> list = new ArrayList<>();
list.add(1); list.add(2); list.add(2); list.add(3);

for (int i = 0; i < list.size(); i++) {
    if (list.get(i) == 2) {
        list.remove(i);
    }
}
// 결과: [1, 2, 3]  ← 두 번째 2가 살아남음!
```

#### 왜?

```
초기:    [1, 2, 2, 3]
i=0: list.get(0) = 1, 삭제 안 함
i=1: list.get(1) = 2, remove(1) → [1, 2, 3]
     원래 인덱스 2였던 두 번째 2가 인덱스 1로 당겨짐
     하지만 i는 다음 반복에서 2로 증가
i=2: list.get(2) = 3, 삭제 안 함 (두 번째 2를 건너뜀!)
종료
```

remove로 뒤 원소들이 **앞으로 당겨지는데** i는 그대로 증가 → 한 칸씩 건너뛰는 효과.

#### 해결 1 — 삭제 후 i--

```java
for (int i = 0; i < list.size(); i++) {
    if (list.get(i) == 2) {
        list.remove(i);
        i--;   // 같은 인덱스 다시 검사
    }
}
```

#### 해결 2 — 뒤에서 앞으로 순회 (가장 안전)

```java
for (int i = list.size() - 1; i >= 0; i--) {
    if (list.get(i) == 2) {
        list.remove(i);
    }
}
```

뒤에서부터 보면, remove로 뒤 원소들이 당겨져도 **이미 처리한 부분**이라 무관. 가장 깔끔.

#### 해결 3 — 새 리스트 생성

```java
ArrayList<Integer> result = new ArrayList<>();
for (int v : list) {
    if (v != 2) result.add(v);
}
list = result;
```

원본은 건드리지 않고 유지할 원소만 새 리스트에. 명확하지만 메모리 추가.

### 4.9.A.3 — IndexOutOfBoundsException (CED)

> **"범위 밖 인덱스 접근은 IndexOutOfBoundsException."**

#### 코드 시연

```java
ArrayList<Integer> list = new ArrayList<>();
list.add(10);
list.add(20);
list.add(30);
// size == 3, 유효 인덱스 [0..2]

list.get(3);        // ❌ IndexOutOfBoundsException
list.get(-1);       // ❌ IndexOutOfBoundsException
list.set(5, 99);    // ❌ IndexOutOfBoundsException
list.remove(10);    // ❌ IndexOutOfBoundsException

// 단, add(int, E)는 size까지 허용:
list.add(3, 40);    // ✅ size=3에서 인덱스 3에 추가 → 끝에 붙음, size=4
list.add(5, 50);    // ❌ 5 > 4 → IndexOutOfBoundsException
```

#### 배열 AIOOBE와 클래스 계층 관계

```
RuntimeException
    └─ IndexOutOfBoundsException     ← ArrayList가 던지는 부모 클래스
            └─ ArrayIndexOutOfBoundsException  ← 배열이 던지는 자식
            └─ StringIndexOutOfBoundsException ← String이 던지는 자식
```

ArrayList는 **부모(IOOBE)**, 배열은 **자식(AIOOBE)**. 시험에서 "정확한 예외 이름"을 묻는 MCQ가 나오면 **자료구조와 일치하는 이름**을 골라야 한다.

### 4.9.A.4 — Enhanced for + remove = ConcurrentModificationException (CED)

> **"enhanced for 루프로 ArrayList를 순회하는 동안 크기를 변경(add/remove)하면 ConcurrentModificationException이 발생할 수 있다. 그러므로 enhanced for 루프 사용 시 add/remove 금지."**

#### 시연

```java
ArrayList<String> list = new ArrayList<>();
list.add("a"); list.add("b"); list.add("c");

for (String s : list) {
    if (s.equals("b")) {
        list.remove(s);   // ❌ ConcurrentModificationException!
    }
}
```

#### 왜?

Enhanced for는 내부적으로 **Iterator**를 쓴다. Iterator는 "리스트가 순회 도중 바뀌면" 감지하고 예외를 던진다 (자료 무결성 보장). add/remove는 리스트 크기를 바꾸므로 Iterator가 감지 → CME.

#### 규칙

> **순회 중 list 크기 변경이 필요하면 indexed for를 써라. enhanced for + add/remove = 절대 금지.**

### 한 줄 요약

> **ArrayList 순회는 indexed/enhanced for 둘 다 가능. 그러나 삭제 중 순회는 (1) i-- 또는 (2) 뒤에서 앞으로 순회. enhanced for + add/remove = ConcurrentModificationException.**

---

## 11. CED 4.10 — ArrayList 알고리즘

### 4.10.A.1 — CED 표준 알고리즘 11가지 (배열의 9가지 + ArrayList 특유 2가지)

**CED 4.10.A.1**는 ArrayList의 표준 알고리즘으로 **11가지**를 명시한다 — 배열 4.5.A.1의 9가지 + ArrayList의 가변 크기를 살린 **insert/delete 2가지**가 추가된 형태:

1. 최솟값/최댓값
2. 합계/평균
3. Exists
4. For-all
5. Count
6. 연속 쌍
7. 중복
8. Shift/Rotate
9. Reverse
10. **원소 삽입(insert elements)** — `add(int, E)` 활용 ← **CED 공식**
11. **원소 삭제(delete elements)** — `remove(int)` 활용 ← **CED 공식**

배열은 크기 고정이라 진짜 삽입/삭제가 불가능(덮어쓰기만). ArrayList는 가변 크기여서 가능 — 그래서 CED가 4.5(배열)와 달리 4.10(ArrayList)에서 insert/delete를 별도 표준으로 명시했다.

> **CED 원문 인용 (p.113, EK 4.10.A.1)**: "There are standard ArrayList algorithms that utilize traversals to: … reverse the order of the elements, **insert elements**, **delete elements**."

### 배열 9가지 → ArrayList 변환 코드 (4.10.A.1.a~i)

배열의 `arr[i]` → `list.get(i)`, `arr.length` → `list.size()`, 대입 `arr[i] = v` → `list.set(i, v)`로 바꾸면 끝. 시험은 이 ArrayList 호출 형태를 직접 채점한다.

#### ① min/max — 최솟값·최댓값

```java
int min = list.get(0);
for (int i = 1; i < list.size(); i++) {
    if (list.get(i) < min) min = list.get(i);
}
```

`list.get(0)`로 초기화. 빈 리스트 호출은 `IndexOutOfBoundsException` — 사전 검증 필요한 경우 `if (list.size() == 0) ...`.

#### ② sum/average — 합계·평균

```java
int sum = 0;
for (int i = 0; i < list.size(); i++) {
    sum += list.get(i);
}
double avg = (double) sum / list.size();   // (double) 캐스팅 필수
```

`(double)` 캐스팅 누락 시 정수 나눗셈으로 결과 손실 — 4.5와 동일 함정.

#### ③ exists — 존재 여부

```java
boolean found = false;
for (String s : list) {
    if (s.equals(target)) {
        found = true;
        break;   // 발견하면 즉시 종료
    }
}
```

객체는 **`.equals()`** 사용 (`==`은 참조 비교 — 함정).

#### ④ for-all — 모두 만족

```java
boolean allPositive = true;
for (int x : list) {
    if (x <= 0) {
        allPositive = false;
        break;
    }
}
```

exists와 반대 패턴. 하나라도 어기면 즉시 false.

#### ⑤ consecutive pairs — 인접 쌍

```java
// 오름차순인지 검사
boolean sorted = true;
for (int i = 0; i < list.size() - 1; i++) {
    if (list.get(i) > list.get(i + 1)) {
        sorted = false;
        break;
    }
}
```

`size() - 1`까지 — `i+1` 접근 때문. off-by-one 함정 핵심.

#### ⑥ duplicates — 중복 검출

```java
// 중복이 하나라도 있는지
boolean hasDup = false;
for (int i = 0; i < list.size(); i++) {
    for (int j = i + 1; j < list.size(); j++) {
        if (list.get(i).equals(list.get(j))) {
            hasDup = true;
        }
    }
}
```

`j = i + 1` 시작 — 같은 쌍 두 번 검사 방지. O(n²).

#### ⑦ shift/rotate — 한 칸 우측 이동

```java
// list를 오른쪽으로 한 칸 회전 (마지막 → 처음)
String last = list.get(list.size() - 1);
for (int i = list.size() - 1; i > 0; i--) {
    list.set(i, list.get(i - 1));
}
list.set(0, last);
```

뒤에서 앞으로. 4.5와 같은 원리. **인덱스 shift라 size는 그대로** — `add`/`remove` 아닌 `set`만 사용.

#### ⑧ reverse — 순서 뒤집기

```java
int n = list.size();
for (int i = 0; i < n / 2; i++) {
    String tmp = list.get(i);
    list.set(i, list.get(n - 1 - i));
    list.set(n - 1 - i, tmp);
}
```

`n / 2`까지만. ArrayList도 `set` swap으로 동일 (size 유지).

> **시험 빈출**: FRQ Q3는 위 8가지 + insert/delete 2가지를 조합하는 형태로 출제. 각 패턴을 `list.get(i)` / `list.size()` / `list.set(i, v)` 호출 형태로 즉시 작성 가능해야 한다.

### ArrayList 특유의 삽입/삭제 (CED 표준 10·11 상세)

#### 조건 만족 원소 모두 삭제

```java
// 60점 미만 모두 제거
for (int i = scores.size() - 1; i >= 0; i--) {
    if (scores.get(i) < 60) {
        scores.remove(i);
    }
}
```

뒤에서 앞으로 순회 (4.9.A.2 함정 회피).

#### 조건 만족 원소만 새 리스트로

```java
ArrayList<String> filtered = new ArrayList<>();
for (String s : original) {
    if (s.substring(0, 1).equals("a")) {   // 첫 글자가 "a"인지 검사
        filtered.add(s);
    }
}
```

> ⚠️ **함정**: `s.startsWith("a")`는 직관적이지만 **Quick Reference에 없음**. 시험 답안에서는 위처럼 `substring(0, 1).equals("a")` 또는 `indexOf("a") == 0`으로 풀어 쓴다. QR에 있는 String 메서드는 `length`, `substring`, `indexOf`, `equals`, `compareTo`, `split` 6개뿐.

#### 정렬된 위치에 삽입

```java
// list가 오름차순일 때 v를 정렬 위치에 삽입
int i = 0;
while (i < list.size() && list.get(i) < v) i++;
list.add(i, v);
```

### 4.10.A.2 — 여러 컬렉션 동시 순회 (CED)

> **"일부 알고리즘은 여러 String, 배열, ArrayList를 **동시에** 순회해야 한다."**

#### 비유 — 두 명단의 짝짓기

이름 명단과 점수 명단이 같은 인덱스로 매칭되어 있다고 하자:

```java
ArrayList<String> names = ...;     // ["Alice", "Bob", "Carol"]
ArrayList<Integer> scores = ...;   // [90, 75, 88]

// 최고점 학생 찾기
int maxIdx = 0;
for (int i = 1; i < scores.size(); i++) {
    if (scores.get(i) > scores.get(maxIdx)) maxIdx = i;
}
String topStudent = names.get(maxIdx);   // "Alice"
int topScore = scores.get(maxIdx);       // 90
```

**같은 인덱스로 두 컬렉션을 동시에 접근**. FRQ 빈출 패턴.

### 한 줄 요약

> **ArrayList 알고리즘 = CED 4.10.A.1 표준 11가지 (배열 9가지 + ArrayList 특유 insert/delete 2가지). 삭제는 뒤에서 앞으로. 여러 컬렉션 동시 순회는 같은 인덱스로 동기화.**

---

## 12. CED 4.11 — 2D 배열 생성과 접근

### 왜 2D 배열인가

1D 배열은 한 줄. 그러나 현실에는 **표(table)** 형태 데이터가 많다:
- 학교 시간표 (요일 × 시간)
- 체스판 (8×8)
- 이미지 (행 × 열의 픽셀)
- 엑셀 시트

이런 **격자(grid)** 데이터를 표현하는 게 2D 배열.

### 4.11.A.1 — 2D 배열의 정의 (CED)

> **"2D 배열은 **배열의 배열**로 저장. 1D 배열과 비슷하게 생성·접근. 크기는 생성 시 고정. primitive 또는 객체 참조 저장 가능."**

#### CED EXCLUSION

> **"비직사각형(nonrectangular) 2D 배열은 시험 범위 외."**

각 행의 길이가 다른 jagged array는 **시험에 안 나옴**. 모든 2D 배열이 직사각형이라고 가정.

### "배열의 배열" 메모리 구조

```java
int[][] grid = new int[3][4];

메모리:
grid (외부 배열) → [row0 참조] → [0, 0, 0, 0]   ← 1D int 배열
                   [row1 참조] → [0, 0, 0, 0]
                   [row2 참조] → [0, 0, 0, 0]
```

외부 배열의 각 원소는 **1D 배열의 참조**. 이 구조 이해가 다음 모든 규칙의 근원.

### 4.11.A.2 — 기본값 (CED)

> **"`new`로 2D 배열 생성 시 모든 원소가 default value로 초기화. int=0, double=0.0, boolean=false, 참조=null."**

#### 시각화 — `new int[2][3]` 직후 메모리 상태

```
int[][] grid = new int[2][3];

       col 0   col 1   col 2
       ┌─────┬─────┬─────┐
row 0  │  0  │  0  │  0  │
       ├─────┼─────┼─────┤
row 1  │  0  │  0  │  0  │
       └─────┴─────┴─────┘

grid[0][0] == 0 ✓
grid[1][2] == 0 ✓  (모든 6개 칸이 0)
```

각 타입별:

```java
new int[2][3]      // 모두 0
new double[2][3]   // 모두 0.0
new boolean[2][3]  // 모두 false
new String[2][3]   // 모두 null  ← 객체 메서드 호출 시 NullPointerException 함정
```

> **함정**: `String[][] words = new String[2][3]; words[0][0].length();` → NullPointerException. 참조 타입 2D 배열은 사용 전 각 칸에 객체를 대입해야 한다.

### 4.11.A.3 — 초기화 리스트 (CED)

> **"2D 배열 초기화 리스트는 1D 초기화 리스트들로 구성. 예: `int[][] arr2D = { {1, 2, 3}, {4, 5, 6} };`"**

```java
int[][] grid = {
    {1, 2, 3, 4},      // row 0
    {5, 6, 7, 8},      // row 1
    {9, 10, 11, 12}    // row 2
};
```

### 4.11.A.4 — 대괄호 두 개로 접근 (CED)

> **"`[row][col]`로 2D 배열 원소 접근·수정. 첫 번째 인덱스가 행, 두 번째가 열."**

```java
grid[0][0]    // 첫 행, 첫 열
grid[2][3]    // 셋째 행, 넷째 열
grid[r][c]    // r행 c열
```

### 4.11.A.5 — 한 행을 1D 배열로 접근 (CED)

> **"2D 배열의 한 행은 2D 배열 이름과 행 인덱스를 담은 대괄호 한 쌍으로 접근."**

```java
int[][] grid = {{1,2,3}, {4,5,6}};
int[] row1 = grid[1];     // {4, 5, 6} — 1D 배열
int x = row1[0];          // 4
int y = grid[1][0];       // 4 (직접 접근, 같은 결과)
```

### 4.11.A.6 — length 두 종류 (CED)

> **"2D 배열의 행 수는 length 속성으로 접근. 유효 행 인덱스는 0 ~ 행 수-1. 열 수는 한 행의 length로 접근. 예: `values.length`(행 수), `values[0].length`(열 수). 범위 밖 인덱스 사용 시 ArrayIndexOutOfBoundsException."**

```java
int[][] grid = new int[3][4];

grid.length;        // 3 (외부 배열 길이 = 행 수)
grid[0].length;     // 4 (한 행의 길이 = 열 수)
```

#### 시험 빈출 함정

```java
// ❌ 헷갈리기 쉬움
int rows = grid[0].length;    // 이건 열 수!
int cols = grid.length;       // 이건 행 수!

// ✅ 올바름
int rows = grid.length;       // 행 수
int cols = grid[0].length;    // 열 수
```

#### 외우기 한 줄

> **"점 첫 번째(외부)는 행, 점 두 번째(내부)는 열."**

### 한 줄 요약

> **2D 배열 = 배열의 배열, [행][열] 순서, 시험은 직사각형만. grid.length=행 수, grid[0].length=열 수. 범위 밖 = AIOOBE.**

---

## 13. CED 4.12 — 2D 배열 순회

### 4.12.A.1 — 중첩 순회 (CED)

> **"중첩 반복문으로 2D 배열의 모든 원소를 순회. 2D 배열은 배열의 배열로 저장되므로, for 루프와 enhanced for 루프 사용법은 1D와 비슷. row-major, column-major, 또는 사용자 정의 순서로 순회 가능. **Row-major**는 각 행을 가로지르며 순회. **Column-major**는 각 열을 따라 순회."**

### Row-major (가장 일반적)

외부 루프 = 행, 내부 루프 = 열.

```java
int[][] grid = {{1,2,3}, {4,5,6}};

for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[0].length; c++) {
        System.out.print(grid[r][c] + " ");
    }
    System.out.println();
}
// 출력:
// 1 2 3
// 4 5 6
// 방문 순서: (0,0), (0,1), (0,2), (1,0), (1,1), (1,2)
```

**한 행을 다 본 다음 다음 행**. 책 읽는 순서와 같음.

### Column-major

외부 루프 = 열, 내부 루프 = 행.

```java
for (int c = 0; c < grid[0].length; c++) {
    for (int r = 0; r < grid.length; r++) {
        System.out.print(grid[r][c] + " ");
    }
    System.out.println();
}
// 출력 순서: 1, 4, 2, 5, 3, 6
```

**한 열을 다 본 다음 다음 열**.

### 시험 단골 트레이싱

```java
int[][] g = {{1,2,3}, {4,5,6}};
for (int c = 0; c < g[0].length; c++) {
    for (int r = 0; r < g.length; r++) {
        System.out.print(g[r][c]);
    }
}
```

**답**: `142536` (column-major).

판별: **외부 루프 변수가 c**(column) → column-major.

### 4.12.A.2 — Enhanced for의 2D (CED)

> **"중첩 enhanced for로 2D 배열 순회 시, 외부 루프 변수는 각 행의 타입(1D 배열). 내부 루프는 한 행을 순회 — 변수는 1D 배열의 원소 타입. 변수에 새 값 대입은 배열에 저장된 값을 바꾸지 않는다."**

#### 코드

```java
int[][] grid = {{1,2,3}, {4,5,6}};

for (int[] row : grid) {       // 외부: 1D int 배열
    for (int v : row) {         // 내부: int
        System.out.print(v + " ");
    }
    System.out.println();
}
```

#### 핵심: 외부 변수 타입은 `int[]`

2D는 "배열의 배열". 외부 iteration이 가져오는 건 **한 행** = 1D 배열. 그래서 `int[] row`.

#### 1D 함정 동일 — 값 변경은 반영 안 됨

```java
for (int[] row : grid) {
    for (int v : row) {
        v = 0;   // 복사본만 변경, 원본 grid 무관
    }
}
```

값 수정이 필요하면 indexed for 사용.

### 한 줄 요약

> **2D 순회 = row-major(외부=행) 또는 column-major(외부=열). enhanced for 외부 변수는 int[] (1D 배열), 내부는 int. 값 수정은 indexed for.**

---

## 14. CED 4.13 — 2D 배열 알고리즘

### 4.13.A.1 — 표준 알고리즘 9가지 (CED)

배열의 9가지와 비슷하지만 "전체, 또는 지정된 행/열/일부분"에 대해 적용:

1. 최솟값/최댓값 (전체 또는 행/열)
2. 합계/평균 (전체 또는 행/열)
3. Exists
4. For-all
5. Count
6. 연속 쌍
7. 중복
8. 행 left/right shift, 열 up/down shift
9. 행/열 reverse

### 알고리즘 1 — 전체 합계

```java
int[][] grid = {{1,2,3}, {4,5,6}, {7,8,9}};
int sum = 0;
for (int[] row : grid) {
    for (int v : row) {
        sum += v;
    }
}
// sum = 45
```

### 알고리즘 2 — 특정 행/열의 합

```java
// 행 1의 합
int rowSum = 0;
for (int c = 0; c < grid[0].length; c++) {
    rowSum += grid[1][c];
}
// rowSum = 4+5+6 = 15

// 열 2의 합
int colSum = 0;
for (int r = 0; r < grid.length; r++) {
    colSum += grid[r][2];
}
// colSum = 3+6+9 = 18
```

### 알고리즘 3 — 대각선

#### 주대각선 (좌상→우하)

```java
int diagSum = 0;
for (int i = 0; i < grid.length; i++) {
    diagSum += grid[i][i];   // [0][0], [1][1], [2][2]...
}
// diagSum = 1+5+9 = 15
```

#### 반대각선 (우상→좌하)

```java
int antiSum = 0;
int n = grid.length;
for (int i = 0; i < n; i++) {
    antiSum += grid[i][n - 1 - i];   // [0][n-1], [1][n-2], ..., [n-1][0]
}
// antiSum = 3+5+7 = 15
```

### 알고리즘 4 — 최댓값 위치

```java
int maxR = 0, maxC = 0;
for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[0].length; c++) {
        if (grid[r][c] > grid[maxR][maxC]) {
            maxR = r;
            maxC = c;
        }
    }
}
```

### 알고리즘 5 — 인접 원소 (상하좌우)

```java
int r = 1, c = 1;
int[][] dirs = {{-1,0}, {1,0}, {0,-1}, {0,1}};   // 상, 하, 좌, 우

for (int[] d : dirs) {
    int nr = r + d[0];
    int nc = c + d[1];
    if (nr >= 0 && nr < grid.length && nc >= 0 && nc < grid[0].length) {
        // grid[nr][nc] 처리
    }
}
```

**경계 검사**(boundary check) 필수. 안 하면 AIOOBE.

### 알고리즘 6 — 행 reverse

```java
int row = 1;
for (int i = 0; i < grid[row].length / 2; i++) {
    int temp = grid[row][i];
    grid[row][i] = grid[row][grid[row].length - 1 - i];
    grid[row][grid[row].length - 1 - i] = temp;
}
```

### 알고리즘 7 — Exists (음수 존재 여부 / 4.13.A.1.c)

```java
boolean hasNeg = false;
for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[r].length; c++) {
        if (grid[r][c] < 0) {
            hasNeg = true;
            // break는 이중 루프라 외부 탈출엔 라벨 필요 — 시험에선 보통 그대로 진행
        }
    }
}
```

For-all (예: 모두 양수) 도 같은 패턴 — 초기값 `true`, 위배 발견 시 `false`.

### 알고리즘 8 — Count (특정 값 등장 횟수 / 4.13.A.1.e)

```java
// 전체 grid에서 target 등장 횟수
int count = 0;
for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[r].length; c++) {
        if (grid[r][c] == target) count++;
    }
}

// 특정 행 r0의 카운트만
int rowCount = 0;
for (int c = 0; c < grid[r0].length; c++) {
    if (grid[r0][c] == target) rowCount++;
}

// 특정 열 c0의 카운트만
int colCount = 0;
for (int r = 0; r < grid.length; r++) {
    if (grid[r][c0] == target) colCount++;
}
```

CED는 "전체 / 특정 행 / 특정 열 / 일부분"으로 명시 — 4가지 모두 익숙해야.

### 알고리즘 9 — Duplicates (같은 행 내 중복 / 4.13.A.1.g)

```java
// 행 r 안에서 중복이 있는지
boolean rowHasDup = false;
for (int i = 0; i < grid[r].length; i++) {
    for (int j = i + 1; j < grid[r].length; j++) {
        if (grid[r][i] == grid[r][j]) rowHasDup = true;
    }
}

// 전체 grid에서 중복 여부 — 모든 위치 쌍 비교
boolean anyDup = false;
int rows = grid.length, cols = grid[0].length;
int total = rows * cols;
for (int p = 0; p < total; p++) {
    for (int q = p + 1; q < total; q++) {
        int r1 = p / cols, c1 = p % cols;
        int r2 = q / cols, c2 = q % cols;
        if (grid[r1][c1] == grid[r2][c2]) anyDup = true;
    }
}
```

`p / cols`, `p % cols`로 1D 인덱스를 (행, 열)로 변환 — 시험엔 단순 형태 위주이지만 패턴은 알아두자.

### 알고리즘 10 — 행/열 Shift (4.13.A.1.h)

```java
// 행 r을 오른쪽으로 한 칸 shift (마지막 → 처음)
int rowLast = grid[r][grid[r].length - 1];
for (int c = grid[r].length - 1; c > 0; c--) {
    grid[r][c] = grid[r][c - 1];
}
grid[r][0] = rowLast;

// 열 c를 아래로 한 칸 shift (마지막 행 → 첫 행)
int colLast = grid[grid.length - 1][c];
for (int r = grid.length - 1; r > 0; r--) {
    grid[r][c] = grid[r - 1][c];
}
grid[0][c] = colLast;
```

행 shift = 한 1D 배열의 shift와 동일. 열 shift = 외부 인덱스가 행이고 같은 열만 따라 이동.

### 알고리즘 11 — 열 reverse (4.13.A.1.i)

```java
// 열 c를 뒤집기 (위 ↔ 아래)
int col = 1;
int rows = grid.length;
for (int i = 0; i < rows / 2; i++) {
    int temp = grid[i][col];
    grid[i][col] = grid[rows - 1 - i][col];
    grid[rows - 1 - i][col] = temp;
}
```

행 reverse(알고리즘 6)와 대칭 — `grid[row].length` 대신 `grid.length`(행 개수) 사용.

### 한 줄 요약

> **2D 알고리즘 = 1D의 9가지를 전체/행/열/일부분에 적용. 행/열 혼동 주의(grid.length vs grid[0].length). 인접 탐색은 경계 검사 필수. shift·reverse는 행/열 모두 가능 — 인덱스 방향만 바뀜.**

---

## 15. CED 4.14 — 검색 알고리즘 (Linear, Binary)

### 왜 두 가지 검색이 있는가

배열에서 특정 값을 찾는 두 가지 전략:
1. **Linear search**: 처음부터 끝까지 하나씩 검사. 단순하지만 느림.
2. **Binary search**: 정렬된 배열에서 절반씩 줄여가며 검사. 복잡하지만 빠름.

### 비유 — 사전에서 단어 찾기

종이 사전에서 "Java"를 찾는다고 하자:
- **Linear**: 사전 첫 페이지부터 한 단어씩 확인. 30분 소요.
- **Binary**: 사전 가운데를 펴고 "J"가 어느 쪽인지 보고 절반 버림. 다시 가운데 펴고 또 절반 버림. 5번 만에 도착.

사전이 **정렬되어 있기 때문에** binary가 가능. 정렬 안 된 메모장에서는 linear밖에 못 함.

### 4.14.A.1 — Linear search (CED)

> **"Linear search는 desired value를 찾거나 모든 원소를 다 확인할 때까지 각 원소를 순서대로 검사. 양 끝 어디에서도 시작 가능."**

#### 기본 구현

```java
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) {
            return i;       // 찾으면 인덱스 반환
        }
    }
    return -1;              // 못 찾으면 -1
}
```

#### 객체 검색은 .equals()

```java
public static int find(String[] arr, String target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i].equals(target)) return i;   // == 절대 아님!
    }
    return -1;
}
```

#### 복잡도

- **최악**: O(n) — 끝까지 못 찾음
- **평균**: 비교 횟수 ≈ n/2, **Big-O는 O(n)** (상수 계수는 흡수)
- **최선**: O(1) — 첫 원소가 target

### 4.14.A.2 — 2D 배열에 Linear search (CED)

> **"2D 배열에 linear search 적용 시, 각 행에 접근한 후 그 행에 linear search."**

```java
public static int[] find2D(int[][] grid, int target) {
    for (int r = 0; r < grid.length; r++) {
        for (int c = 0; c < grid[0].length; c++) {
            if (grid[r][c] == target) {
                return new int[]{r, c};
            }
        }
    }
    return new int[]{-1, -1};
}
```

2D에 binary search는 AP 범위 외.

### Binary search (CED 4.17.B에서 재등장, 여기서 미리 봄)

> **"이진 탐색은 정렬된 배열/ArrayList에서만 사용. 정렬된 배열의 가운데에서 시작해 매번 배열의 절반을 제거."**

#### 기본 구현 (iterative)

```java
public static int binarySearch(int[] arr, int target) {
    int low = 0;
    int high = arr.length - 1;
    
    while (low <= high) {
        int mid = (low + high) / 2;
        
        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            low = mid + 1;       // 오른쪽 절반
        } else {
            high = mid - 1;      // 왼쪽 절반
        }
    }
    return -1;
}
```

#### 트레이싱 단계 (시험 단골)

```
arr = {2, 5, 8, 12, 16, 23, 38}, target = 23

iter 1: low=0, high=6, mid=3, arr[3]=12 < 23 → low=4
iter 2: low=4, high=6, mid=5, arr[5]=23 == 23 → return 5
```

#### 복잡도

- **최악**: O(log n)
- **n=1000일 때**: 최대 10번 비교 (log₂ 1000 ≈ 10)
- **n=1,000,000**: 최대 20번 비교

### Binary search의 핵심 전제

> **반드시 정렬된 배열에만 적용 가능.**

정렬 안 된 배열에 적용하면 결과가 보장되지 않음 (-1을 반환하거나 잘못된 인덱스 반환).

### 두 검색 비교표

| 항목 | Linear | Binary |
|-----|-------|-------|
| 정렬 필요? | ❌ 불요 | ✅ **필수** |
| 시간 복잡도 | O(n) | O(log n) |
| 평균 비교 횟수 (n=1000) | 500 | 10 |
| 구현 난이도 | 쉬움 | 중간 (경계 주의) |
| 적용 가능 자료구조 | 배열, ArrayList, 2D | 정렬된 배열, 정렬된 ArrayList |

### 시험 판별 플로우

```
Q1. 배열이 "정렬되어 있다"고 명시?
    YES → binary 가능
    NO → 반드시 linear

Q2. n이 큼 또는 O(log n) 언급?
    YES → binary 권장
    NO → linear도 OK
```

### 한 줄 요약

> **Linear = 처음부터 끝까지, 정렬 불필요, O(n). Binary = 절반씩 줄임, 정렬 필수, O(log n). 못 찾으면 둘 다 -1 반환.**

---

## 16. CED 4.15 — 정렬 알고리즘 (Selection, Insertion, Merge)

### 왜 세 가지 정렬을 배우는가

CED는 정확히 3가지만 출제 (다른 정렬은 EXCLUSION):
- **Selection sort**: 가장 작은 원소를 찾아 앞으로
- **Insertion sort**: 정렬된 부분에 새 원소를 삽입
- **Merge sort**: 분할-병합 (재귀)

각각 다른 사고방식. 시험은 트레이싱(중간 단계 추적)이 핵심.

### 4.15.A.1 — Selection/Insertion은 iterative (CED)

> **"Selection sort와 insertion sort는 배열/ArrayList 원소를 정렬하는 iterative 알고리즘."**

### 4.15.A.2 — Selection sort 정의 (CED)

> **"Selection sort는 미정렬 부분에서 가장 작은(또는 큰) 원소를 반복해서 선택해 정렬된 부분의 올바른(최종) 위치로 swap."**

#### 알고리즘

```java
public static void selectionSort(int[] arr) {
    for (int i = 0; i < arr.length - 1; i++) {
        int minIdx = i;
        for (int j = i + 1; j < arr.length; j++) {
            if (arr[j] < arr[minIdx]) minIdx = j;
        }
        // swap arr[i] and arr[minIdx]
        int temp = arr[i];
        arr[i] = arr[minIdx];
        arr[minIdx] = temp;
    }
}
```

#### 트레이싱 (단골)

```
{64, 25, 12, 22, 11}

i=0: 미정렬 [64,25,12,22,11], 최소=11(idx 4), swap(0,4)
     → {11, 25, 12, 22, 64}
i=1: 미정렬 [25,12,22,64], 최소=12(idx 2), swap(1,2)
     → {11, 12, 25, 22, 64}
i=2: 미정렬 [25,22,64], 최소=22(idx 3), swap(2,3)
     → {11, 12, 22, 25, 64}
i=3: 미정렬 [25,64], 최소=25(idx 3), swap(3,3) (제자리)
     → {11, 12, 22, 25, 64}
```

#### 불변량 (Invariant)

> **"i번 반복 후: 첫 i개 원소는 정렬되었고 전체에서 가장 작은 i개."**

각 i 반복이 끝나면 앞쪽 i개는 **최종 위치**에 있다.

#### 복잡도

- 비교 횟수: 항상 n(n-1)/2 → O(n²)
- swap 횟수: 최대 n-1회

### 4.15.A.3 — Insertion sort 정의 (CED)

> **"Insertion sort는 미정렬 부분의 원소를 정렬된 부분의 올바른(최종이 아닐 수도 있는) 위치에 삽입. 정렬된 부분의 원소들을 옆으로 밀어 새 원소 자리를 만든다."**

#### 알고리즘

```java
public static void insertionSort(int[] arr) {
    for (int i = 1; i < arr.length; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];   // 한 칸 오른쪽으로 밀기
            j--;
        }
        arr[j + 1] = key;          // 빈 자리에 삽입
    }
}
```

#### 트레이싱

```
{64, 25, 12, 22, 11}

i=1: key=25, 64>25 → 64 뒤로, 25를 [0]
     → {25, 64, 12, 22, 11}
i=2: key=12, 64>12 → 64 뒤로, 25>12 → 25 뒤로, 12를 [0]
     → {12, 25, 64, 22, 11}
i=3: key=22, 64>22 → 64 뒤로, 25>22 → 25 뒤로, 12<22 → 정지, 22를 [1]
     → {12, 22, 25, 64, 11}
i=4: key=11, 64>11, 25>11, 22>11, 12>11 → 모두 뒤로, 11을 [0]
     → {11, 12, 22, 25, 64}
```

#### 불변량

> **"i번 반복 후: 앞 i+1개 원소는 자기들끼리 정렬됨 (최종 위치는 아닐 수 있음)."**

Selection과의 차이: Selection은 i번 후 앞 i개가 **최종 위치**. Insertion은 i번 후 앞 i+1개가 **자기들끼리만 정렬**되었지만, 나중에 더 작은 원소가 들어오면 밀려날 수 있다.

#### 복잡도

- 최악: O(n²) (역순 정렬된 배열)
- **최선: O(n)** (이미 정렬된 배열, 비교만 하고 끝)
- 평균: O(n²)

거의 정렬된 데이터에서는 Selection보다 빠름.

### Merge sort (4.17.C에서 재등장)

> **"Merge sort는 배열/ArrayList를 정렬할 수 있는 재귀 정렬 알고리즘."** (CED 4.17.C.1)

> **"Merge sort는 배열을 더 작은 부분 배열로 반복 분할 (각 부분이 1개가 될 때까지), 그 다음 정렬된 부분 배열들을 재귀적으로 병합."** (CED 4.17.C.2)

#### 핵심 아이디어

```
1. 배열을 반으로 나눈다.
2. 각 반을 재귀로 정렬한다.
3. 두 정렬된 반을 병합(merge)한다.
```

#### 분할-병합 트리 (n=8 예)

```
[8,4,2,7,1,3,6,5]
       │  분할
[8,4,2,7]    [1,3,6,5]
       │
[8,4] [2,7]  [1,3] [6,5]
       │
[8][4][2][7] [1][3][6][5]   ← base case
       │  병합 (아래에서 위로)
[4,8][2,7]   [1,3][5,6]
       │
[2,4,7,8]    [1,3,5,6]
       │
[1,2,3,4,5,6,7,8]
```

#### 왜 O(n log n)?

- **레벨 수**: n→n/2→n/4→...→1까지 `log₂ n` 단계
- **레벨당 작업**: 각 레벨에서 모든 n개 원소를 한 번씩 병합·복사
- **총 작업**: n × log n

#### 비교 — n=1000일 때

| 정렬 | 비교 횟수 |
|-----|--------|
| Selection (O(n²)) | 약 1,000,000 |
| Insertion 평균 (O(n²)) | 약 500,000 |
| Merge (O(n log n)) | 약 10,000 |

Merge가 **100배 빠름**. 큰 데이터에서 큰 차이.

### 정렬 알고리즘 비교표

| 항목 | Selection | Insertion | Merge |
|-----|----------|----------|-------|
| 시간 복잡도 (최악) | O(n²) | O(n²) | O(n log n) |
| 시간 복잡도 (최선) | O(n²) | **O(n)** | O(n log n) |
| 공간 복잡도 | O(1) | O(1) | O(n) (임시 배열) |
| 안정성 (stable) | 아니오 | 예 | 예 |
| 재귀? | 아니오 | 아니오 | 예 |
| 시험 작성? | OK | OK | 트레이싱만 (재귀 EXCLUSION) |

### EXCLUSION (CED 명시)

> **"Selection, insertion, merge 외의 정렬은 시험 범위 외."** (Bubble sort, Quick sort 등)

`Arrays.sort()`나 `Collections.sort()` 같은 Java 내장 정렬도 시험에서 사용 금지.

### 객체 정렬 시 비교 — `compareTo` (Java QR 등재)

정렬 알고리즘이 객체(특히 `String`)를 비교할 때는 `<`, `>` 연산자 사용 불가 (객체는 비교 연산자가 의미 없음). 대신 **`compareTo`**를 사용한다.

> **CED Java QR (p.185)**: `int compareTo(String other)` — "Returns a value < 0 if this is less than other; returns zero if this is equal to other; returns a value > 0 if this is greater than other."

#### 사용 예 — String 배열을 selection sort로 정렬

```java
String[] arr = {"banana", "apple", "cherry"};
for (int i = 0; i < arr.length - 1; i++) {
    int minIdx = i;
    for (int j = i + 1; j < arr.length; j++) {
        if (arr[j].compareTo(arr[minIdx]) < 0) {   // ← compareTo로 비교
            minIdx = j;
        }
    }
    String temp = arr[i];
    arr[i] = arr[minIdx];
    arr[minIdx] = temp;
}
// arr = {"apple", "banana", "cherry"}
```

#### 반환값 해석

| `a.compareTo(b)` 반환값 | 의미 |
|---|---|
| 음수 (예: -1, -25) | a < b (사전순으로 a가 앞) |
| 0 | a equals b |
| 양수 (예: 1, 25) | a > b (사전순으로 a가 뒤) |

**시험 함정**: 반환값은 **단순 -1/0/1이 아닐 수 있다**. 첫 번째로 다른 문자의 **유니코드 값 차이**가 그대로 반환되기 때문이다.

| 호출 | 반환값 | 계산 |
|---|---|---|
| `"a".compareTo("z")` | **-25** | 'a'(97) - 'z'(122) = -25 |
| `"z".compareTo("a")` | **+25** | 'z'(122) - 'a'(97) = +25 |
| `"apple".compareTo("banana")` | **-1** | 첫 글자 'a'(97) - 'b'(98) = -1 |
| `"apple".compareTo("apple")` | **0** | 모두 동일 |
| `"apple".compareTo("apples")` | **-1** | 앞부분 동일, 길이 차 = 5-6 = -1 |

> **외울 것은 부호 규칙뿐**: 음수면 앞(왼쪽), 양수면 뒤(오른쪽), 0이면 같음. 정확한 숫자값을 묻는 시험 문제는 없다 — `if (a.compareTo(b) < 0)` 같은 부호 비교만 익히면 된다.

#### == 절대 금지

```java
"apple" == "apple"          // ❌ 주소 비교 (true일 때도 있지만 신뢰 불가)
"apple".equals("apple")     // ✅ 값 비교 (항상 true)
"apple".compareTo("banana") // ✅ 정렬용 비교 (음수)
```

### 한 줄 요약

> **3가지 정렬 — Selection(매번 최솟값을 앞으로), Insertion(정렬된 부분에 삽입), Merge(분할-병합 재귀, 가장 빠름). 트레이싱이 시험 핵심. 다른 정렬은 EXCLUSION.**

---

## 17. CED 4.16 — 재귀 (Recursion)

### 매우 중요한 CED EXCLUSION

> **CED 4.16.A.3: "재귀 코드 작성은 AP CSA 시험 범위 외."**

즉:
- **MCQ**: 주어진 재귀 코드를 추적(tracing)하는 문제 출제 가능
- **FRQ**: 재귀 메서드 작성 절대 안 나옴

학생이 알아야 할 것은 **"주어진 재귀 코드의 결과를 트레이스"**할 수 있는 능력.

### 왜 재귀를 배우는가

> **재귀는 "큰 문제를 작은 같은 문제로 줄이는" 사고방식.** 어떤 문제는 반복문(iteration)보다 재귀로 푸는 게 자연스럽다 (트리 탐색, 분할-병합 등).

또한 **컴퓨터 과학의 핵심 개념** — 함수형 프로그래밍, 알고리즘 분석의 기반.

### 비유 — 양파 까기

큰 양파를 까는 일을 생각하자.
- 가장 안쪽 양파는 더 까지 않는다 (**base case**).
- 그 외 양파는 "겉껍질 한 장 벗기기 + 안쪽 양파 까기" (**recursive case**).

이 두 개로 모든 양파를 깐다. 재귀의 본질.

### 4.16.A.1 — 재귀의 정의 (CED)

> **"재귀 메서드(recursive method)는 자기 자신을 호출하는 메서드. 적어도 하나의 base case와 적어도 하나의 recursive call을 포함. 재귀는 반복의 또 다른 형태."**

#### 두 필수 요소

1. **Base case**: 재귀를 멈추는 조건. 없으면 무한 호출 → StackOverflowError.
2. **Recursive case**: 자기 자신 호출. **단, 인자는 더 작은 문제로**.

### 예제 1 — 팩토리얼

```java
public static int factorial(int n) {
    if (n <= 1) return 1;          // Base case
    return n * factorial(n - 1);   // Recursive case
}
```

#### `factorial(4)` 트레이스

```
factorial(4)
  = 4 * factorial(3)
  = 4 * (3 * factorial(2))
  = 4 * 3 * (2 * factorial(1))
  = 4 * 3 * 2 * 1
  = 24
```

### 예제 2 — 피보나치

```java
public static int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);   // 두 번의 재귀 호출
}
```

#### `fib(4)` 호출 트리

```
fib(4)
├── fib(3)
│   ├── fib(2)
│   │   ├── fib(1) → 1
│   │   └── fib(0) → 0
│   │   결과: 1
│   └── fib(1) → 1
│   결과: 2
└── fib(2)
    ├── fib(1) → 1
    └── fib(0) → 0
    결과: 1
결과: 3
```

`fib(4) = 3`. 호출 횟수가 **지수적으로 증가**(피보나치 자체).

### 예제 3 — 문자열 뒤집기

```java
public static String reverse(String s) {
    if (s.length() <= 1) return s;
    return reverse(s.substring(1)) + s.substring(0, 1);
}

reverse("abc")
  = reverse("bc") + "a"
  = (reverse("c") + "b") + "a"
  = ("c" + "b") + "a"
  = "cba"
```

### 4.16.A.2 — 각 호출의 독립적 변수 (CED)

> **"각 재귀 호출은 자신만의 로컬 변수와 매개변수 집합을 가진다. 매개변수 값이 재귀 진행을 포착 — 마치 루프 제어 변수가 루프 진행을 포착하듯."**

#### 메모리 모델 — Call Stack

각 메서드 호출은 **stack frame**을 만든다. 자기만의 매개변수, 지역 변수.

```
factorial(4) 호출 시 Call Stack:

│ factorial(1) │ ← 가장 위 (가장 깊은 호출)
│ factorial(2) │
│ factorial(3) │
│ factorial(4) │ ← 가장 아래 (처음 호출)
└──────────────┘

각 frame은 독립.
factorial(1)이 1을 반환하면 factorial(2)가 그 값을 받아 계산하고 반환.
```

이 stack 구조 이해가 트레이싱의 열쇠.

### 4.16.A.3 — 재귀 ↔ 반복 변환 (CED)

> **"모든 재귀 솔루션은 반복으로, 모든 반복 솔루션은 재귀로 바꿀 수 있다."**

기능적으로 동등하지만 표현 방식이 다름. 재귀가 자연스러운 문제(트리, 분할-병합), 반복이 자연스러운 문제(단순 누적, 카운트)가 따로 있다.

### 시험 트레이싱 전략

#### 전략 1 — 작은 인자 직접 트레이싱

```java
public static int mystery(int n) {
    if (n == 0) return 1;
    if (n == 1) return 1;
    return mystery(n - 1) + mystery(n - 2);
}
```

`mystery(6)`을 묻는다면, 표를 만들어 한 번씩 채운다:

| n | mystery(n) |
|---|----------|
| 0 | 1 |
| 1 | 1 |
| 2 | 1+1 = 2 |
| 3 | 2+1 = 3 |
| 4 | 3+2 = 5 |
| 5 | 5+3 = 8 |
| 6 | 8+5 = 13 |

답: **13**.

> ℹ️ **참고**: 위 시퀀스는 base case가 `mystery(0)=1, mystery(1)=1`이라 표준 피보나치(F(0)=0, F(1)=1)와 다르다. 표준 피보나치라면 fib(6)=8. 시험에서 등장하는 재귀 시퀀스는 base case부터 정확히 트레이싱해야 한다 — 표 만들어 한 줄씩 채우는 위 방식이 가장 안전.

#### 전략 2 — 호출 횟수 세기

`mystery(n)`의 호출 횟수 T(n):
- T(0) = T(1) = 1 (base case는 호출 1번)
- T(n) = 1 + T(n-1) + T(n-2)

| n | T(n) |
|---|-----|
| 0 | 1 |
| 1 | 1 |
| 2 | 3 |
| 3 | 5 |
| 4 | 9 |
| 5 | 15 |

#### 전략 3 — 패턴 인식

- **단일 재귀** (`return f(n-1)`): 호출 횟수 ≈ n
- **이중 재귀** (`return f(n-1) + f(n-2)`): 호출 횟수 지수적
- **분할 재귀** (`return f(n/2)`): 호출 횟수 ≈ log n

### 한 줄 요약

> **재귀 = 자기 자신 호출 + base case + 더 작은 인자. 작성은 EXCLUSION, 트레이싱만 출제. 호출 트리/stack frame을 그려 결과 추적.**

---

## 18. CED 4.17 — 재귀 검색과 정렬

### 4.17.A.1 — 재귀로 String/배열/ArrayList 순회 (CED)

> **"재귀는 String, 배열, ArrayList 객체를 순회하는 데 사용 가능."**

#### 예 — 배열 합 (재귀)

```java
public static int sumArray(int[] arr, int index) {
    if (index == arr.length) return 0;          // Base case
    return arr[index] + sumArray(arr, index + 1);
}

sumArray({3, 7, 2}, 0)
  = 3 + sumArray({3,7,2}, 1)
  = 3 + 7 + sumArray({3,7,2}, 2)
  = 3 + 7 + 2 + sumArray({3,7,2}, 3)
  = 3 + 7 + 2 + 0
  = 12
```

작성은 안 하지만, 이런 코드 트레이싱은 가능해야 함.

### 4.17.B — Binary Search 재귀 (CED)

#### 4.17.B.1 — 정의

> **"Binary search는 정렬된 데이터에 사용. 정렬된 배열/ArrayList의 중간에서 시작, 매 재귀 호출마다 절반을 제거. 원하는 값을 찾거나 모든 원소가 제거될 때까지."**

#### 4.17.B.2 — 효율성

> **"Binary search는 보통 linear search보다 효율적."**

#### 4.17.B.3 — Iterative 또는 Recursive

> **"Binary search 알고리즘은 iterative 또는 recursive로 작성 가능."**

#### Recursive Binary Search 코드

```java
public static int binarySearch(int[] arr, int target, int low, int high) {
    if (low > high) return -1;             // Base case (못 찾음)
    
    int mid = (low + high) / 2;
    
    if (arr[mid] == target) {
        return mid;                          // Base case (찾음)
    } else if (arr[mid] < target) {
        return binarySearch(arr, target, mid + 1, high);   // 오른쪽
    } else {
        return binarySearch(arr, target, low, mid - 1);    // 왼쪽
    }
}

// 호출: binarySearch(arr, target, 0, arr.length - 1);
```

#### 트레이싱

```
arr = {2, 5, 8, 12, 16, 23, 38}, target = 8
호출 1: binarySearch(arr, 8, 0, 6)
        mid=3, arr[3]=12 > 8 → 왼쪽: binarySearch(arr, 8, 0, 2)
호출 2: binarySearch(arr, 8, 0, 2)
        mid=1, arr[1]=5 < 8 → 오른쪽: binarySearch(arr, 8, 2, 2)
호출 3: binarySearch(arr, 8, 2, 2)
        mid=2, arr[2]=8 == 8 → return 2
```

총 3번 호출 만에 찾음.

#### EXCLUSION (CED 명시)

> **"Linear와 binary search 외의 검색 알고리즘은 시험 범위 외."**

### 4.17.C — Merge Sort 재귀 (CED)

#### 4.17.C.1 — 정의

> **"Merge sort는 배열/ArrayList를 정렬할 수 있는 재귀 정렬 알고리즘."**

#### 4.17.C.2 — 메커니즘

> **"Merge sort는 배열을 더 작은 부분 배열로 반복 분할 (각 부분이 1개가 될 때까지), 그 다음 정렬된 부분 배열들을 재귀적으로 병합해 최종 정렬된 배열을 만든다."**

#### 코드 (트레이싱용 — 작성은 EXCLUSION)

```java
public static void mergeSort(int[] arr, int left, int right) {
    if (left >= right) return;             // Base case
    
    int mid = (left + right) / 2;
    mergeSort(arr, left, mid);             // 왼쪽 정렬
    mergeSort(arr, mid + 1, right);        // 오른쪽 정렬
    merge(arr, left, mid, right);          // 병합
}

public static void merge(int[] arr, int left, int mid, int right) {
    int[] temp = new int[right - left + 1];
    int i = left, j = mid + 1, k = 0;
    
    while (i <= mid && j <= right) {
        if (arr[i] <= arr[j]) {
            temp[k] = arr[i];
            k++; i++;
        } else {
            temp[k] = arr[j];
            k++; j++;
        }
    }
    while (i <= mid) {
        temp[k] = arr[i];
        k++; i++;
    }
    while (j <= right) {
        temp[k] = arr[j];
        k++; j++;
    }
    for (int t = 0; t < temp.length; t++) {
        arr[left + t] = temp[t];
    }
}
```

#### 호출 트리 (n=4 예)

```
{5, 3, 8, 1}

mergeSort(0, 3)
├── mergeSort(0, 1)
│   ├── mergeSort(0, 0) → base
│   ├── mergeSort(1, 1) → base
│   └── merge(0, 0, 1) → {3, 5, 8, 1}
├── mergeSort(2, 3)
│   ├── mergeSort(2, 2) → base
│   ├── mergeSort(3, 3) → base
│   └── merge(2, 2, 3) → {3, 5, 1, 8}
└── merge(0, 1, 3) → {1, 3, 5, 8}
```

매 단계의 배열 상태를 추적하는 능력이 시험 핵심.

#### EXCLUSION (CED 명시)

> **"Selection, insertion, merge 외의 정렬은 시험 범위 외."**

### 한 줄 요약

> **재귀 검색·정렬 = Binary Search(정렬 필수, log n) + Merge Sort(분할-병합, n log n). 작성은 EXCLUSION, 트레이싱만 출제. 호출 트리 그리기 능력이 핵심.**

---

## 19. FRQ Q3 (ArrayList) 완전 공략

### 출제 형식

> **데이터 분석 with ArrayList**: 객체 ArrayList가 주어지고, 한 메서드를 작성. 보통 **삽입/삭제/필터링/계산** 중 하나.

### 채점 기준 패턴 (5-7점)

1. ArrayList 모든 원소 순회 — 1점
2. 정확한 메서드 호출 (`get(i)`, `size()`) — 1점
3. 조건 비교 정확 — 1점
4. 조건 충족 시 정확한 동작 (add, remove, count) — 1점
5. 인덱스 처리 정확 (삭제 시 shift 고려) — 1점
6. 알고리즘 전체 정합성 — 1점

### 만점 답안 패턴

#### 패턴 1 — 카운트

```java
public int countMatching(int target) {
    int count = 0;
    for (int i = 0; i < items.size(); i++) {
        if (items.get(i).getValue() == target) {
            count++;
        }
    }
    return count;
}
```

#### 패턴 2 — 필터링 (제거)

```java
public void removeBelow(int min) {
    for (int i = items.size() - 1; i >= 0; i--) {   // 뒤에서 앞으로!
        if (items.get(i).getScore() < min) {
            items.remove(i);
        }
    }
}
```

#### 패턴 3 — 새 리스트 만들기

```java
public ArrayList<Item> getMatching(String type) {
    ArrayList<Item> result = new ArrayList<>();
    for (int i = 0; i < items.size(); i++) {
        if (items.get(i).getType().equals(type)) {
            result.add(items.get(i));
        }
    }
    return result;
}
```

### 자주 감점되는 실수 Top 5

| # | 실수 | 결과 |
|---|-----|-----|
| 1 | 앞에서 뒤로 순회하며 remove (인덱스 shift 무시) | -1 |
| 2 | enhanced for + remove (CME 위험) | -1 |
| 3 | String 비교에 `==` 사용 (`.equals()` 아님) | -1 |
| 4 | `list.length` 사용 (`size()`가 맞음) | -1 |
| 5 | EXCLUSION 메서드 사용 (`contains`, `isEmpty` 등) | -1 |

---

## 20. FRQ Q4 (2D Array) 완전 공략

### 출제 형식

> **2D Array**: 시나리오와 클래스가 주어지고, 한 메서드 작성. 보통 **2D 데이터 접근/조작/계산**.

### 채점 기준 패턴 (5-7점)

1. 외부 루프가 모든 행 순회 — 1점
2. 내부 루프가 모든 열 순회 — 1점
3. `grid[r][c]` 정확 접근 — 1점
4. 조건 비교/계산 정확 — 1점
5. 결과 누적/저장 정확 — 1점
6. 알고리즘 전체 정합성 — 1점

### 만점 답안 패턴

#### 패턴 1 — 전체 합

```java
public int totalSum(int[][] grid) {
    int sum = 0;
    for (int r = 0; r < grid.length; r++) {
        for (int c = 0; c < grid[0].length; c++) {
            sum += grid[r][c];
        }
    }
    return sum;
}
```

#### 패턴 2 — 행/열 합을 1D 배열로 반환

```java
public int[] rowSums(int[][] grid) {
    int[] result = new int[grid.length];
    for (int r = 0; r < grid.length; r++) {
        int sum = 0;
        for (int c = 0; c < grid[r].length; c++) {
            sum += grid[r][c];
        }
        result[r] = sum;
    }
    return result;
}
```

#### 패턴 3 — 조건 만족 위치 찾기

```java
public int[] findValue(int[][] grid, int target) {
    for (int r = 0; r < grid.length; r++) {
        for (int c = 0; c < grid[0].length; c++) {
            if (grid[r][c] == target) {
                return new int[]{r, c};
            }
        }
    }
    return new int[]{-1, -1};
}
```

#### 패턴 4 — 모든 행 검사 (for-all)

```java
public int countRowsWithAll(int[][] grid, int target) {
    int count = 0;
    for (int r = 0; r < grid.length; r++) {
        boolean allMatch = true;
        for (int c = 0; c < grid[r].length; c++) {
            if (grid[r][c] != target) {
                allMatch = false;
            }
        }
        if (allMatch) count++;
    }
    return count;
}
```

### 자주 감점되는 실수 Top 5

| # | 실수 | 결과 |
|---|-----|-----|
| 1 | `grid[c][r]` (행/열 순서 틀림) | -1 |
| 2 | `grid.length` vs `grid[0].length` 혼동 | -1 |
| 3 | 경계 검사 누락 (인접 탐색 등) | -1 |
| 4 | 빈 행 또는 1×n 처리 안 됨 | -1 |
| 5 | column-major 요구인데 row-major 작성 | -1 |

---

## 21. 통합 원리 — Unit 4를 관통하는 한 가지 진실

### "한 번에 하나씩" 원리

Unit 4의 모든 알고리즘은 결국:

> **"컬렉션에서 한 번에 한 원소씩 보고, 각 원소에 대해 무언가 한다."**

이 한 문장에서 모든 패턴이 파생된다:

| 알고리즘 | "각 원소에 대해 무언가" |
|--------|---------------------|
| 합계 | 누적 변수에 더한다 |
| 평균 | 합계 / 개수 |
| 최댓값 | 현재 max보다 크면 갱신 |
| 카운트 | 조건 만족하면 +1 |
| Exists | 조건 만족 발견하면 true |
| For-all | 조건 위반 발견하면 false |
| 검색 | 일치하면 인덱스 반환 |

이 통합 시각에서 보면 **"새 알고리즘"도 결국 "각 원소에 대해 무엇을"의 변형**일 뿐이다.

### 참조 복사 원리 (Unit 3 연결)

Unit 4에서 자주 등장하는 함정들도 결국 **참조 복사**의 결과:

| 맥락 | 원인 |
|-----|-----|
| Enhanced for의 값 복사 함정 | 변수에 값/참조의 복사본 할당 |
| 객체 배열에서 메서드 호출이 반영됨 | 참조 복사 = 같은 객체 공유 |
| ArrayList 매개변수 변경이 외부에 반영 | 같은 객체 공유 |
| 2D 배열의 행 공유 (`grid[1] = grid[0]`) | 같은 1D 배열 공유 |

**Unit 3의 "참조 = 주소" 이해**가 Unit 4의 모든 함정을 풀어준다.

### 시험 사고 흐름 — "이 코드의 결과는?"

```
Q1. 무엇을 순회하는가? (배열, ArrayList, 2D)
Q2. 어떻게 순회하는가? (indexed, enhanced, 뒤에서, row/col-major)
Q3. 각 원소에 무엇을 하는가? (누적, 비교, 카운트, 변경)
Q4. 변경 시 참조 복사 함정 있는가? (값 복사인가, 객체 변경인가)
Q5. 종료 조건은? (반환값, 최종 상태)
```

이 5단계로 모든 트레이싱 문제를 분해할 수 있다.

---

## 22. 시험 직전 1분 요약 — 절대 까먹으면 안 될 것

### 배열 핵심 5규칙

1. `arr.length` (필드, 괄호 없음)
2. 인덱스 `0 ~ length-1`, 벗어나면 AIOOBE
3. `new int[5]`은 `{0,0,0,0,0}`로 초기화
4. enhanced for의 변수는 **복사본** — 원본 안 바뀜
5. 객체 배열 + 메서드 호출은 원본 객체 변경 반영

### ArrayList 핵심 5규칙

1. **6개 메서드만** 사용 (`size, add, add(int,E), get, set, remove`)
2. `size()`(메서드, 괄호 있음)
3. **Generic 필수**: `ArrayList<Integer>`
4. 삭제 중 순회는 **뒤에서 앞으로** 또는 `i--`
5. enhanced for + add/remove = ConcurrentModificationException

### 2D 배열 핵심 3규칙

1. `grid.length` = 행 수, `grid[0].length` = 열 수
2. `grid[행][열]` 순서
3. enhanced for 외부 변수는 `int[]`(1D 배열), 내부는 `int`

### 검색 핵심

- Linear: 정렬 불필요, O(n)
- Binary: **정렬 필수**, O(log n), 못 찾으면 -1

### 정렬 핵심

- Selection: 매번 최솟값을 앞으로
- Insertion: 정렬된 부분에 삽입
- Merge: 분할-병합, O(n log n)
- 그 외 정렬은 **EXCLUSION**

### 재귀 핵심

- **트레이싱만** 출제 (작성 EXCLUSION)
- Base case + Recursive case
- Call stack frame으로 시각화
- Binary search/Merge sort는 재귀 트레이싱 가능

### 파일 핵심

- `import java.io.*; import java.util.Scanner;`
- `throws IOException`
- `new Scanner(new File(name))`
- `while (scan.hasNext())`
- `scan.close()`

### Wrapper 핵심

- `int → Integer`, `double → Double`, immutable
- ArrayList는 wrapper만 (`<int>` 불가)
- Autoboxing/Unboxing 자동, null unboxing은 NPE
- 비교는 `.equals()` (== 위험)

### EXCLUSION 정리 (절대 쓰면 안 되는 것)

- `toString()` 오버라이드 작성 (CED 1.15.A.5)
- `equals()` 오버라이드 작성
- `Scanner(System.in)` (키보드 입력)
- `nextLine() + nextInt()` 혼용
- `Arrays.sort()`, `Collections.sort()`
- `list.contains()`, `isEmpty()`, `clear()`, `indexOf()`
- Bubble sort, Quick sort 등
- HashMap, HashSet, LinkedList 등
- 비직사각형 2D 배열
- 재귀 메서드 작성 (FRQ에서)

---

## 23. 마지막 자가진단 — 진짜 마스터했는지 확인

다음 7가지 질문에 망설임 없이 답할 수 있다면 Unit 4는 완전히 끝났다.

1. **"`for (int v : arr) v = v * 2;` 후 arr는 바뀌는가?"**
   → 아니다. v는 값 복사본. arr는 그대로.

2. **"`arr.length`와 `s.length()`의 차이는?"**
   → arr는 배열(필드, 괄호 없음), s는 String(메서드, 괄호 있음). 시험 빈출.

3. **"ArrayList에서 조건 만족 원소를 모두 제거하는 가장 안전한 방법은?"**
   → 뒤에서 앞으로 순회 (`for (int i = list.size()-1; i >= 0; i--)`).

4. **"`grid.length`는 행 수인가 열 수인가?"**
   → 행 수. 열 수는 `grid[0].length`.

5. **"Binary search를 정렬 안 된 배열에 쓰면 어떻게 되는가?"**
   → 결과가 보장되지 않음. -1을 반환할 수도, 잘못된 인덱스를 반환할 수도. 정렬이 절대 전제.

6. **"Selection sort i=2 반복 후, `{5,3,8,1,4}`는 어떤 상태인가?"**
   → i=0: {1,3,8,5,4}, i=1: {1,3,8,5,4}, i=2: {1,3,4,5,8}. 답: `{1,3,4,5,8}`.

7. **"`fib(5)`의 호출 횟수는?"**
   → T(5) = 1 + T(4) + T(3) = 1 + 9 + 5 = 15.

7개 모두 1분 안에 답할 수 있다면 **Unit 4 만점 준비 완료**.

---

## 부록 A: 학습 자원 매핑

| 보충 자료 | 언제 보는가 |
|---------|----------|
| `Unit4_강의노트.md` | 코드 예시가 더 필요할 때 |
| `Unit4_시험개념_딥다이브.md` | DD 형식 단편 정리 |
| `MCQ_문제집.md` | 개념 후 문제 적용 |
| `FRQ_풀이해설.md` | FRQ Q3, Q4 실전 |
| `5점_고급드릴.md` | 만점 추가 훈련 |

## 부록 B: CED 모든 EK 항목 매핑 검증

본 문서가 다룬 CED 2025-26 Unit 4의 모든 Essential Knowledge 항목:

- **4.1.A.1, 4.1.B.1-3, 4.1.C.1** (윤리/편향/적절성) — §2
- **4.2.A.1-3** (데이터셋, 한 번에 하나씩, 다이어그램) — §3
- **4.3.A.1-6** (배열 전체) — §4
- **4.4.A.1-6** (배열 순회) — §5
- **4.5.A.1** (배열 알고리즘 9가지) — §6
- **4.6.A.1-10** (파일 전체, EXCLUSION 포함) — §7
- **4.7.A.1-5** (Wrapper 전체) — §8
- **4.8.A.1-6** (ArrayList 전체) — §9
- **4.9.A.1-4** (ArrayList 순회 전체) — §10
- **4.10.A.1-2** (ArrayList 알고리즘 CED 표준 11가지 — 배열 9가지 + insert/delete 2가지, 동시 순회) — §11
- **4.11.A.1-6** (2D 배열 생성/접근, 직사각형 EXCLUSION) — §12
- **4.12.A.1-2** (2D 순회, enhanced for) — §13
- **4.13.A.1** (2D 알고리즘 9가지) — §14
- **4.14.A.1-2** (Linear search, 2D linear) — §15
- **4.15.A.1-3** (Selection, Insertion 정렬) — §16
- **4.16.A.1-3** (재귀 정의, 변수 독립, 변환, EXCLUSION) — §17
- **4.17.A.1, 4.17.B.1-3, 4.17.C.1-2** (재귀 순회, Binary, Merge) — §18

**모든 EK 항목 빠짐없이 다룸.** ✅

---

## 부록 C: 2025-26 CED 단원 구성 변경 안내

> ⚠️ **중요**: 이전 버전 CED에 있던 **Unit 5(상속/다형성)는 2025-26 시험에서 완전히 제거**되었다.
>
> 2025-26 AP CSA 시험은 Unit 1~4의 **4개 단원만** 출제:
> - Unit 1 (Using Objects and Methods, 15-25%)
> - Unit 2 (Selection and Iteration, 25-35%)
> - Unit 3 (Class Creation, 10-18%)
> - **Unit 4 (Data Collections, 30-40%)** ← 본 문서
>
> **시험 범위 외 (절대 사용 X)**:
> - 상속 (`extends`, `super`)
> - 인터페이스 (`implements`)
> - 추상 클래스 (`abstract`)
> - 다형성 (polymorphism), 메서드 오버라이딩 (`@Override`)
> - `Object` 클래스의 `toString`, `equals` 오버라이드 작성
>
> 단, **Unit 4의 컬렉션은 모든 종류의 클래스 객체를 원소로 받을 수 있다**. FRQ Q3는 보통 단순한 클래스 한 개의 ArrayList를 다룬다 (상속 관계 객체 X).
>
> 예시 (FRQ Q3 형식):
> ```java
> // Student라는 단일 클래스의 ArrayList
> ArrayList<Student> students = ...;
> for (int i = 0; i < students.size(); i++) {
>     if (students.get(i).getScore() >= 80) count++;
> }
> ```
> 상속이나 다형성 없이 **평범한 클래스 객체**만 다룬다. 이 점을 명심하고 답안 작성.

---

## 부록 D: 출처 (Sources)

본 문서의 모든 내용은 다음 공식 출처를 기반으로 한다:

1. **AP Computer Science A Course and Exam Description (CED), Effective Fall 2025**, College Board, June 2025 (194 pages, v.1).
   - URL: https://apcentral.collegeboard.org/courses/ap-computer-science-a
   - Direct PDF: https://apcentral.collegeboard.org/media/pdf/ap-computer-science-a-course-and-exam-description.pdf
   - Unit 4 토픽 페이지: CED p.92-122 (UNIT 4: Data Collections, 토픽 4.1~4.17)
   - 모든 Learning Objective(LO)와 Essential Knowledge(EK) 항목을 본 문서 §2~§18 및 부록 B에 빠짐없이 매핑

2. **AP CSA Java Quick Reference (CED Appendix)** — 시험 출제 메서드 범위 정의
   - Scanner: `Scanner(File f)`, `nextInt`, `nextDouble`, `nextBoolean`, `next`, `nextLine`, `hasNext`, `close` (총 8 항목)
   - String: `split(String del)` (그 외는 Unit 1-2 참조)
   - Integer: `parseInt(String s)`, `MIN_VALUE`, `MAX_VALUE`
   - Double: `parseDouble(String s)`
   - ArrayList: `size`, `add(E)`, `add(int, E)`, `get(int)`, `set(int, E)`, `remove(int)` (총 6 항목)

3. **CED EXCLUSION 출처 (시험 범위 외 명시)**:
   - **4.6.A.6** Keyboard input (`Scanner(System.in)`) — Unit 4
   - **4.6.A.7** `nextLine` + 다른 Scanner 메서드 혼용 코드 — Unit 4
   - **4.6.A.8** Regular expression 특수 문자 (`split` 매개변수) — Unit 4
   - **4.11.A.1** Nonrectangular (jagged) 2D arrays — Unit 4
   - **4.16.A.3** Writing recursive code — Unit 4
   - **4.17.B.2** Search algorithms other than linear/binary — Unit 4
   - **4.17.C.1** Sorting algorithms other than selection/insertion/merge — Unit 4
   - **1.15.A.5** Overriding `toString` (Unit 1, FRQ Q2 영향)

4. **검증 방법**: 본 문서는 College Board 공식 CED PDF를 직접 텍스트 추출 후 모든 EK 항목(4.1.A.1 ~ 4.17.C.2)을 항목별로 본문에 매핑. 부록 B의 항목별 매핑표 참조.

본 문서가 CED와 어긋나는 부분이 있다면 항상 **CED가 우선**한다 (College Board 공식 문서이므로).

---

> **이 문서를 다 읽었다면 — 축하한다.**
>
> AP CSA 시험에서 가장 무거운 단원, **시험 점수의 약 1/3 (FRQ Q3·Q4까지 합치면 40%에 육박)**을 차지하는 Unit 4의 모든 시험 개념을 "왜 이렇게 생겼는가"의 메커니즘 수준에서 이해했다.
>
> 이제 코드를 쓰는 손이 머리를 따라가도록 직접 배열·ArrayList·2D를 다뤄보면 된다.
> FRQ Q3, Q4 만점은 이해의 깊이 × 손에 익은 패턴 × 차분함의 곱이다.
> 첫 번째 항을 채웠으니, 나머지 두 항을 위해 손을 움직이자.
