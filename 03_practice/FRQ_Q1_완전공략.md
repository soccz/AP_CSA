# FRQ Q1 완전공략 — Methods and Control Structures (9점)

> **배점 9점, 4문항 중 최고 배점, 매년 출제.** Q1은 Unit 1의 메서드 호출·매개변수·반환값 + Unit 2의 조건문·반복문을 결합한 **가장 전형적인 알고리즘 문제**다. 여기서 떨어뜨리는 점수는 전체 등급을 바꾼다.

---

## 1. Q1의 출제 구조 (매년 동일)

### 1.1 전형적 형식

```
[지문]
- 문제 도메인 설명 (게임, 학생 명부, 메시지 처리 등)
- 기존 클래스의 **일부 메서드·필드가 제공됨** (사용은 OK, 수정은 금지)
- 제공된 메서드의 **precondition**이 주어짐
- 학생이 구현해야 할 **1개 또는 2개의 메서드** 명세

[학생 작업]
Part (a): 메서드 1 작성 (보통 4~5점)
Part (b): 메서드 2 작성 (보통 4~5점, Part (a)를 호출해도 됨)
```

### 1.2 공통 특징

1. **클래스 설계는 요구 안 함** — Q2가 담당
2. **ArrayList 거의 안 나옴** — Q3이 담당
3. **2D Array 거의 안 나옴** — Q4가 담당
4. **Q1은 순수 알고리즘 + 메서드 조합**. 보통 1D 배열 또는 String 조작
5. **재귀 요구 안 함** (CED 4.16 EXCLUSION)

### 1.3 배점 분배 (대표 사례)

| 항목 | 점수 | 감점 포인트 |
|-----|-----|---------|
| 메서드 header (signature) 맞음 | 1점 | 반환 타입·매개변수 타입/순서/개수 |
| 정상 경로 알고리즘 정답 | 4~5점 | 루프 경계, 조건문, 수치 계산 |
| 엣지 케이스 처리 | 1~2점 | 빈 배열, 발견 없음, 첫/마지막 원소 |
| 반환값 정확 | 1점 | 타입 + 정답값 |

---

## 2. 필수 암기 템플릿 5종

Q1은 아래 5개 패턴의 **조합**으로 거의 전부 풀린다.

### 2.1 패턴 A — 조건 카운트 (count)

**지문 예**: "배열 `arr`에서 양수의 개수를 반환하시오."

```java
public static int countPositive(int[] arr) {
    int count = 0;
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] > 0) {
            count++;
        }
    }
    return count;
}
```

**사고 체크**:
- 반환 타입 int (카운트는 항상 int)
- count 초기값 0
- 매개변수 타입 정확히 일치
- 빈 배열이면 0 반환 (자동 OK)

### 2.2 패턴 B — 조건에 맞는 원소 찾기 (find)

**지문 예**: "배열 `arr`에서 target보다 큰 첫 원소의 인덱스. 없으면 -1."

```java
public static int findFirstLarger(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] > target) {
            return i;          // 즉시 반환
        }
    }
    return -1;                  // 못 찾음
}
```

**사고 체크**:
- 발견 즉시 `return` → 나머지 순회 안 함
- 못 찾음 처리 (-1) 필수
- 반환 타입 int (인덱스)

### 2.3 패턴 C — 변환/새 배열 생성 (transform)

**지문 예**: "배열 `arr`의 각 원소를 2배로 한 **새 배열**을 반환."

```java
public static int[] doubleAll(int[] arr) {
    int[] result = new int[arr.length];
    for (int i = 0; i < arr.length; i++) {
        result[i] = arr[i] * 2;
    }
    return result;
}
```

**사고 체크**:
- `new int[arr.length]`로 같은 크기 새 배열
- 원본 수정 아닌 **새 배열 반환**
- 반환 타입 `int[]`

### 2.4 패턴 D — 누적 계산 (accumulate)

**지문 예**: "배열 `arr`의 합계와 평균을 계산하는 메서드를 작성."

```java
public static double average(int[] arr) {
    if (arr.length == 0) return 0.0;   // 빈 배열 엣지 처리
    int sum = 0;
    for (int i = 0; i < arr.length; i++) {
        sum += arr[i];
    }
    return (double) sum / arr.length;   // int/int 함정 주의!
}
```

**사고 체크**:
- 합계 초기값 0
- 평균 반환 시 **`(double) sum / arr.length`** 형태 필수 (DD1.7)
- 빈 배열 방어 (0 나눗셈 회피)

### 2.5 패턴 E — String 조작 (substring 순회)

**지문 예**: "문자열 `s`에서 대문자 개수를 반환." (대문자 판별은 heuristic 주어짐)

```java
public static int countMatch(String s, String target) {
    int count = 0;
    for (int i = 0; i < s.length(); i++) {
        String ch = s.substring(i, i + 1);    // charAt 금지!
        if (ch.equals(target)) {
            count++;
        }
    }
    return count;
}
```

**사고 체크**:
- `s.length()` — String은 괄호 있음 (DD2.13)
- `charAt` 쓰지 말고 **`substring(i, i+1)`**
- String 비교는 **`.equals()`** (DD1.14)

---

## 3. 지문 읽기 5단계 전략

### Step 1 — 요구 메서드 시그니처 확인

지문에서 **이 부분을 먼저 체크**:
- 메서드 이름 (정확한 대소문자)
- 반환 타입 (`int`, `double`, `boolean`, `String`, `int[]` 등)
- 매개변수 (타입·개수·순서)
- `public static`인가 `public`(instance)인가

### Step 2 — 지문에서 제공되는 도구 파악

- 이미 주어진 메서드 목록 — **호출 가능**
- 필드 목록 — **읽기 가능** (instance 메서드라면)
- precondition — **체크 불필요 (assume)**

### Step 3 — 5패턴 중 어디에 해당하는가 판별

| 질문 형태 | 패턴 |
|---------|-----|
| "~의 개수를 반환" | A (count) |
| "첫 번째 ~의 인덱스", "~가 있는지" | B (find) |
| "~로 변환한 새 배열 반환" | C (transform) |
| "합/평균/곱 반환" | D (accumulate) |
| "문자열 ~ 처리" | E (String) |

대부분 이 5패턴 중 하나. 조합되면 두 패턴의 합. 예: "문자열에서 'a' 개수 반환" = A + E.

### Step 4 — 엣지 케이스 체크

```
□ 빈 배열/빈 문자열 → 메서드가 정상 동작?
□ 못 찾음 → 무엇을 반환? (-1, null, false, 0 중 지문 요구)
□ 첫 원소가 답인 경우 → 정상 처리?
□ 마지막 원소가 답인 경우 → 정상 처리?
□ 모든 원소가 조건 만족 / 아무도 만족 안 함 → 정상?
```

### Step 5 — 작성·제출 전 확인

```
□ 시그니처 지문과 일치?
□ 반환 타입 올바름?
□ 모든 경로에서 return?
□ 중괄호 페어링 맞음?
□ 세미콜론 빠짐 없음?
□ charAt, Math.PI, Scanner(System.in) 안 썼는가?
□ ++i, arr[i++] 안 썼는가?
```

---

## 4. 실전 풀이 — 2024 FRQ Q1 스타일 예시

### 지문 (가상)

> `WordChecker` 클래스에는 다음이 제공된다:
> - `private String[] words;` — 단어 배열 (항상 null 아님, length ≥ 0)
> - `private int length();` — 배열 길이 반환
>
> **Part (a)**: `public int countShort(int maxLen)`을 작성하라. words에서 길이가 `maxLen` 이하인 단어의 개수를 반환한다.
>
> **Part (b)**: `public String longest()`을 작성하라. words에서 가장 긴 단어를 반환한다. words가 비어있으면 `""`를 반환한다. 길이가 같으면 먼저 등장한 것을 반환한다.

### Part (a) 풀이

**패턴 A (count)** + String length()

```java
public int countShort(int maxLen) {
    int count = 0;
    for (int i = 0; i < words.length; i++) {
        if (words[i].length() <= maxLen) {
            count++;
        }
    }
    return count;
}
```

**채점 분해**:
- 시그니처 일치 (1점)
- for 루프 경계 올바름 (1점)
- if 조건 `<= maxLen` 올바름 (1점)
- count 증가 및 반환 (1점)
- 빈 배열 자동 처리 (0점 별도 없이 자동 OK)

### Part (b) 풀이

**패턴 B (find)** 변형 + 최대값 추적

```java
public String longest() {
    if (words.length == 0) return "";         // 엣지
    String best = words[0];
    for (int i = 1; i < words.length; i++) {
        if (words[i].length() > best.length()) {
            best = words[i];
        }
    }
    return best;
}
```

**채점 분해**:
- 시그니처 일치 (1점)
- 빈 배열 `""` 반환 (1점)
- 초기값 `words[0]` (1점)
- 비교 연산 `>`가 아닌 `>=`면 감점 (지문 "먼저 등장한 것") (1점)
- 반환 (1점)

### 함정 피하기

**① `>=` 대신 `>` 필수**: "길이 같으면 먼저 것"이라는 지문 조건. `>`를 쓰면 자동으로 "먼저 등장한 것" 유지. `>=`이면 같은 길이일 때 나중 것으로 교체.

**② 빈 배열 방어**: `words[0]`을 index 0이 없는 배열에 접근하면 AIOOBE. 지문에 "빈 배열이면 `""`"라는 요구가 있으므로 가장 처음에 체크.

**③ `.length()` vs `.length`**: `words[i]`는 String이므로 **`.length()`** (method). `words`는 배열이므로 **`.length`** (field). 섞이면 컴파일 에러.

---

## 5. 자주 틀리는 Q1 함정 Top 10

| # | 함정 | 증상 | 방지 |
|---|-----|-----|-----|
| 1 | 반환 타입 누락/오타 | 컴파일 에러 | 시그니처를 지문에서 **글자 그대로 복사** |
| 2 | 매개변수 개수/순서 틀림 | 컴파일 에러 or logic 오류 | 시그니처 복사 |
| 3 | int/int로 평균 계산 | 정수 나눗셈으로 틀림 | `(double) sum / arr.length` |
| 4 | 못 찾음 반환값 누락 | 컴파일 에러 "missing return" | 루프 후 별도 return |
| 5 | 빈 배열 시 AIOOBE | RuntimeException | 앞에서 length==0 체크 |
| 6 | String `==` 비교 | false 반환으로 logic 오류 | `.equals()` 쓰기 |
| 7 | charAt 사용 | QR 없음 감점 | `substring(i, i+1)` |
| 8 | for 경계 `<=` 사용 | AIOOBE | `<`로 통일 (`< arr.length`) |
| 9 | `i++`를 표현식에 | EXCLUSION | 단독 문장 또는 for update만 |
| 10 | Math.max/min 사용 | QR 없음 | `if`로 수동 비교 |

---

## 6. 부록 — Q1에서 자주 등장하는 보조 메서드 사용법

### 6.1 배열 복사 (수동 — QR에 System.arraycopy 없음)

```java
int[] copy = new int[arr.length];
for (int i = 0; i < arr.length; i++) {
    copy[i] = arr[i];
}
```

### 6.2 배열 일부 복사

```java
int[] partial = new int[end - start];
for (int i = 0; i < partial.length; i++) {
    partial[i] = arr[start + i];
}
```

### 6.3 두 메서드 조합 — (a)를 (b)에서 호출

```java
public int countShort(int maxLen) { /* Part (a) */ }

public boolean hasAnyShort(int maxLen) {
    return countShort(maxLen) > 0;   // Part (a) 호출
}
```

Part (b)에서 Part (a)를 호출해도 **감점 없음**. 오히려 권장.

### 6.4 static vs instance 구분

Q1 지문이 클래스 안의 메서드를 요구하면 대개 **instance** (즉 `this.field` 사용 가능).
독립된 utility 메서드면 **static** (`public static`). 지문의 `this.words` 같은 표현이 있으면 instance.

---

## 7. 제출 직전 90초 체크리스트

```
□ 1. 메서드 시그니처 — public, static 여부, 반환 타입, 매개변수 일치
□ 2. 중괄호 쌍 — 모든 { 에 대응하는 } 있는가
□ 3. 세미콜론 — 각 문장 끝
□ 4. 모든 분기 return — 컴파일러가 "missing return" 안 내는가
□ 5. 변수 이름 오타 — 지문의 필드/매개변수 이름 정확
□ 6. .length vs .length() — 배열/String 구분
□ 7. EXCLUSION 안 씀 — charAt, Math.PI, Scanner(System.in), ++ prefix, arr[i++]
□ 8. 엣지 케이스 — 빈 배열/String, 발견 없음, 첫·마지막 원소
□ 9. 반환값 타입 — return한 식이 선언된 반환 타입과 일치
□ 10. 한 번 읽기 — 지문의 요구와 최종 코드가 일치
```

이 10개를 **90초 안에 체크**할 수 있을 때까지 훈련하면 Q1 9점 중 7~8점은 안정적으로 확보.

---

## 8. Q1 ↔ 다른 DD 연결

Q1 풀이에 동원되는 DD들:
- **DD1.7** (캐스팅): 평균 계산 `(double) sum / n`
- **DD1.11** (`++` 경계): for update만 OK
- **DD1.14** (String `.equals()`): 문자열 비교
- **DD1.17** (substring exclusive `to`): 부분 문자열 추출
- **DD1.18** (indexOf `-1`): 못 찾음 처리
- **DD2.3-2.5** (short-circuit): 가드 조건
- **DD2.12** (off-by-one): 루프 경계
- **DD2.17** (min/max 초기값): arr[0]로 초기화
- **DD4.6** (표준 배열 알고리즘): count/exists/for-all

**Q1은 Unit 1, 2의 모든 개념이 실전 메서드 작성으로 합성되는 종합 시험**. 위 DD들을 각자 깊게 이해하면 Q1은 "여러 DD의 조합 적용"일 뿐이다.
