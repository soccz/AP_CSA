# AP Computer Science A 2025 FRQ 풀이 해설서

> AP CSA 과외용 | 2025년 시험 기준 | 총 4문제 (90분)
>
> **배점 주의:** 이 해설은 **2025년 실제 시험** 기출을 다룹니다. 2025년은 구 CED 기준으로 각 문항 9점(총 36점)이 적용되었습니다. **2026년부터는 새 배점(Q1:7점, Q2:7점, Q3:5점, Q4:6점, 총 25점)이 적용**됩니다. 모의시험 세트(Set1~5)는 새 배점을 따르고 있으므로, 이 해설의 배점과 모의시험의 배점이 다른 것은 정상입니다.

---

## FRQ란 무엇인가? (처음 보는 학생을 위한 안내)

### FRQ 답안 작성 형식
- 2025-26부터 FRQ는 **Bluebook 앱**에서 직접 코드를 타이핑합니다 (종이 아님)
- 메서드 시그니처(헤더)가 이미 주어지므로, **본문(body)만 작성**하면 됩니다 (Q2 제외)
- Q2는 전체 클래스를 처음부터 작성합니다

### 문제 읽는 법
1. **시그니처 먼저 확인** — 반환 타입(void/int/String 등), 매개변수 타입과 이름
2. **Precondition 확인** — "~라고 가정하라"는 조건. 이 조건을 직접 검증할 필요 없음
3. **Postcondition 확인** — 메서드 실행 후 보장되는 상태
4. **예시 테이블 분석** — 입력 → 기대 출력을 직접 손으로 트레이싱
5. **"must use" 지시 확인** — 특정 메서드를 반드시 호출해야 하는 경우

### 일반적 FRQ 접근 5단계
1. 시그니처와 Javadoc을 30초간 읽고 "무엇을 해야 하는지" 한 문장으로 정리
2. 예시 테이블로 알고리즘을 머릿속에 그리기
3. 필요한 변수 선언 (accumulator, counter, index 등)
4. 루프/조건 구조 작성
5. 반환값 확인 (non-void이면 반드시 return)

### 점수 최대화 원칙
- **빈 칸 금지** — 뭐라도 쓰면 부분점수 가능
- **helper 메서드 반드시 사용** — "must use"라고 했으면 안 쓰면 algorithm point 불인정
- **채점은 기준별 독립** — 하나 틀려도 다른 기준에서 점수를 받을 수 있음
- **컴파일 에러보다 로직 에러가 낫다** — 세미콜론, 중괄호 실수는 무시해주는 경우가 많음 (CED p.173 "Errors to Ignore" 참조)

---

## FRQ 공통 전략

### 시간 배분

| 문제 | 유형 | 권장 시간 | 비고 |
|------|------|----------|------|
| Q1 | Methods and Control Structures | 15분 | 가장 쉬움, 빠르게 끝내기 |
| Q2 | Class Design (전체 클래스 작성) | 25분 | 가장 시간 많이 걸림 |
| Q3 | ArrayList | 20분 | 인덱스 실수 주의 |
| Q4 | 2D Array | 20분 | 중첩 루프 필수 |
| 여유 | 검토 | 10분 | 실수 확인 |

### Task Verb 의미

| 동사 | 의미 | 주의사항 |
|------|------|---------|
| **Assume** | "~라고 가정하라" | 해당 조건을 직접 검증할 필요 없음 |
| **Complete** | 메서드/생성자 본문만 작성 | 시그니처는 이미 주어짐, 다시 쓰지 말 것 |
| **Write / Implement** | 전체를 작성 | Q2에서 클래스 전체를 처음부터 작성 |

### 컴파일 에러 방지 체크리스트

- [ ] 세미콜론(`;`) 빠뜨리지 않았는가?
- [ ] 중괄호 `{}` 짝이 맞는가?
- [ ] `return` 문이 모든 경로에 있는가? (non-void 메서드)
- [ ] 메서드 호출 시 객체를 통해 호출했는가? (`company.numAvailableDogs(hour)`)
- [ ] `ArrayList`는 `new ArrayList<타입>()`으로 생성했는가?
- [ ] 배열 인덱스가 범위를 벗어나지 않는가?
- [ ] `String` 비교는 `==`가 아니라 `.equals()`인가?
- [ ] 인스턴스 변수 접근 시 `this.`는 생략 가능하지만, 파라미터와 이름이 같으면 `this.` 필수

### 부분점수 극대화 팁

1. **빈칸으로 두지 마라** -- 뭐라도 쓰면 부분점수 가능
2. **의도를 주석으로 표현** -- 코드가 틀려도 로직이 맞으면 점수를 줄 수 있음
3. **helper 메서드는 반드시 사용** -- 문제에서 "must use"라고 하면 안 쓰면 감점
4. **루프 구조만 맞아도 점수** -- 올바른 for 루프 범위 = 1점
5. **리턴 타입을 맞춰라** -- `int`를 리턴해야 하면 마지막에 `return 0;`이라도 써라
6. **new 키워드를 잊지 마라** -- `ArrayList`, 배열, 객체 생성 시 반드시 `new`

---

## Q1. DogWalker (Methods and Control Structures)

### 1. 문제 요약

개 산책 회사(`DogWalkCompany`)와 개 산책자(`DogWalker`) 클래스가 주어진다.

- **(a) `walkDogs(int hour)`**: 주어진 시간에 이 산책자가 산책시킬 개의 수를 결정하고, 회사에 업데이트한 뒤, 그 수를 반환한다.
- **(b) `dogWalkShift(int startHour, int endHour)`**: startHour부터 endHour까지 매 시간 산책을 수행하고, 총 수입(달러)을 반환한다.

**핵심 규칙:**
- 산책자는 회사에 남은 개 수와 자신의 `maxDogs` 중 작은 값만큼 산책
- 시급: 개당 $5 기본급
- 보너스 $3: `maxDogs`만큼 꽉 채우고 AND 시간이 9~17시(피크타임)일 때

### 2. 접근 전략

**Part (a):**
1. `company.numAvailableDogs(hour)`로 가용 개 수 확인
2. `maxDogs`와 비교하여 작은 값 선택 (= 실제 산책할 개 수)
3. `company.updateDogs(hour, 실제산책수)`로 회사에 알림
4. 실제 산책 수 반환

**Part (b):**
1. startHour부터 endHour까지 루프
2. 매 시간 `walkDogs(hour)` 호출하여 산책한 개 수 얻기
3. 수입 계산: `개수 * 5` + 보너스 조건 충족 시 `3`
4. 총합 반환

### 3. 정답 코드

#### Part (a): walkDogs

```java
public int walkDogs(int hour)
{
    int available = company.numAvailableDogs(hour);
    int dogsToWalk;

    if (available <= maxDogs)
    {
        dogsToWalk = available;
    }
    else
    {
        dogsToWalk = maxDogs;
    }

    company.updateDogs(hour, dogsToWalk);
    return dogsToWalk;
}
```

**더 간결한 버전:**

```java
public int walkDogs(int hour)
{
    int available = company.numAvailableDogs(hour);
    int dogsToWalk = Math.min(available, maxDogs);
    company.updateDogs(hour, dogsToWalk);
    return dogsToWalk;
}
```

#### Part (b): dogWalkShift

```java
public int dogWalkShift(int startHour, int endHour)
{
    int totalEarned = 0;

    for (int hour = startHour; hour <= endHour; hour++)
    {
        int dogs = walkDogs(hour);
        int earned = dogs * 5;

        if (dogs == maxDogs && hour >= 9 && hour <= 17)
        {
            earned += 3;
        }

        totalEarned += earned;
    }

    return totalEarned;
}
```

### 4. 코드 설명

#### Part (a)
| 코드 | 왜 필요한가 |
|------|------------|
| `company.numAvailableDogs(hour)` | 회사에 해당 시간에 남은 개 수를 질의 (반드시 사용해야 함) |
| `Math.min(available, maxDogs)` | 산책자가 감당 가능한 수와 남은 수 중 작은 값 선택 |
| `company.updateDogs(hour, dogsToWalk)` | 다른 산책자와 중복 배정 방지를 위해 회사에 알림 (반드시 사용해야 함) |
| `return dogsToWalk` | 실제 산책한 개 수 반환 |

#### Part (b)
| 코드 | 왜 필요한가 |
|------|------------|
| `for (int hour = startHour; hour <= endHour; hour++)` | startHour부터 endHour까지 **inclusive** 반복 |
| `int dogs = walkDogs(hour)` | (a)에서 작성한 메서드 재사용 (반드시 호출해야 함) |
| `dogs * 5` | 기본급 계산 |
| `dogs == maxDogs && hour >= 9 && hour <= 17` | 보너스 조건: 풀가동 AND 피크타임 |
| `earned += 3` | 보너스는 시간당 $3 (개당이 아님!) |

### 5. 채점 기준 요약 (CED 공식 배점 기반)

#### Part (a) walkDogs -- 4점
| 포인트 | 채점 항목 | 세부사항 |
|--------|----------|---------|
| +1 | `company`에서 `DogWalkCompany` 메서드 호출 | `numAvailableDogs`와 `updateDogs`를 `company` 객체에서 호출. 잘못된 파라미터 타입이면 불인정 |
| +1 | available dogs와 `maxDogs`를 비교하여 산책할 개 수 결정 | `numAvailableDogs`를 잘못 호출해도 비교 로직이 맞으면 인정 |
| +1 | `numAvailableDogs`에 `hour` 전달 **AND** `updateDogs`에 `hour`과 올바른 산책 수 전달 (*algorithm*) | 산책 수 계산이 틀리면 불인정 |
| +1 | 계산된 값을 반환 | `int` 외 타입 반환 시 불인정, 일부 경로에서 반환 누락 시 불인정 |

#### Part (b) dogWalkShift -- 5점
| 포인트 | 채점 항목 | 세부사항 |
|--------|----------|---------|
| +1 | `startHour`부터 `endHour`까지 inclusive 루프 | 루프 내 early return이 있어도 범위가 맞으면 인정 |
| +1 | 루프 안에서 `walkDogs`를 `int` 파라미터로 호출 | 반환값 저장/사용 안 해도 인정. 클래스에서 호출하거나 `company`에서 호출하면 불인정 |
| +1 | 한 시간의 기본급 계산 (`dogs * 5`) | 루프 밖에서 계산하거나 `walkDogs` 잘못 호출해도 기본급 로직이 맞으면 인정 |
| +1 | 한 시간의 보너스 계산 (dogs == maxDogs && 9~17시 조건) | 보너스를 이중 계산하거나, 두 조건 중 하나만 확인하거나, 보너스를 잘못 계산하면 불인정 |
| +1 | 총 수입 누적 (*algorithm*) | 기본급/보너스가 틀려도 누적 로직이 맞으면 인정. 변수 초기화 누락, 루프 내 다중 `walkDogs` 호출, 루프 내 미누적, early return은 불인정 |

### 6. 흔한 실수

1. **`updateDogs` 호출 누락** -- 문제에서 "must use"라고 명시했으므로 반드시 호출
2. **보너스 조건 오해** -- 보너스는 개당 $3이 아니라 시간당 $3 (한 번만 추가)
3. **피크타임 범위 실수** -- 9 이상 17 이하 (inclusive). `>` 또는 `<`로 쓰면 감점
4. **`walkDogs` 대신 직접 계산** -- Part (b)에서 반드시 `walkDogs` 호출해야 함
5. **`<=` 대신 `<` 사용** -- `endHour`도 포함이므로 `<=` 필수
6. **보너스 조건에서 AND 대신 OR** -- 두 조건 모두 충족해야 보너스

### 7. 부분점수 전략

- 루프 구조(`for hour = startHour to endHour`)만 맞아도 1점
- `walkDogs(hour)` 호출만 해도 1점
- 보너스 로직이 틀려도 `dogs * 5` 기본급 계산이 맞으면 1점
- Part (a)가 틀려도 Part (b)는 독립 채점 -- "Assume walkDogs works as specified"

---

## Q2. SignedText (Class Design -- 전체 클래스 작성)

### 1. 문제 요약

서명 기능이 있는 텍스트 클래스 `SignedText`를 **전체 작성**한다.

- **생성자**: firstName과 lastName을 받아 저장
- **`getSignature()`**: 서명 문자열 생성
  - firstName이 빈 문자열이면: lastName만 반환 (예: `"Wong"`)
  - firstName이 있으면: 첫글자 + `-` + lastName (예: `"h-dubois"`, `"G-LOPEZ"`)
- **`addSignature(String text)`**: 텍스트에 서명을 추가/이동
  - 서명이 text에 없으면: text 끝에 서명 붙여서 반환
  - 서명이 text 끝에 있으면: text 그대로 반환
  - 서명이 text 앞에 있으면: 앞의 서명을 제거하고 끝에 붙여서 반환

### 2. 접근 전략

1. 인스턴스 변수: `firstName`, `lastName` (또는 `signature` 미리 계산)
2. `getSignature()`: if-else로 firstName 빈 문자열 여부 확인
3. `addSignature()`:
   - `getSignature()`로 서명 얻기
   - `text.indexOf(signature)` 또는 `startsWith`/`endsWith`로 위치 판단
   - 3가지 경우 분기

### 3. 정답 코드

```java
public class SignedText
{
    private String firstName;
    private String lastName;

    public SignedText(String firstName, String lastName)
    {
        this.firstName = firstName;
        this.lastName = lastName;
    }

    public String getSignature()
    {
        if (firstName.equals(""))
        {
            return lastName;
        }
        else
        {
            return firstName.substring(0, 1) + "-" + lastName;
        }
    }

    public String addSignature(String text)
    {
        String sig = getSignature();

        if (text.endsWith(sig))
        {
            return text;
        }
        else if (text.startsWith(sig))
        {
            return text.substring(sig.length()) + sig;
        }
        else
        {
            return text + sig;
        }
    }
}
```

### 4. 코드 설명

#### 생성자
| 코드 | 왜 필요한가 |
|------|------------|
| `this.firstName = firstName;` | 파라미터와 인스턴스 변수 이름이 같으므로 `this.` 필수 |
| `this.lastName = lastName;` | 동일 |

#### getSignature()
| 코드 | 왜 필요한가 |
|------|------------|
| `firstName.equals("")` | 빈 문자열 확인. `==`가 아니라 `.equals()` 사용! |
| `firstName.substring(0, 1)` | 첫 글자 추출. `charAt(0)`을 쓰면 char이므로 문자열 연결 시에도 작동하지만 `substring`이 더 안전 |
| `+ "-" +` | 대시로 연결 |

#### addSignature(String text)
| 코드 | 왜 필요한가 |
|------|------------|
| `text.endsWith(sig)` | 서명이 끝에 있는지 확인 -- 이 경우를 **먼저** 체크해야 함 |
| `text.startsWith(sig)` | 서명이 앞에 있는지 확인 |
| `text.substring(sig.length())` | 앞의 서명을 제거 (서명 길이만큼 잘라냄) |
| `return text + sig` | 서명이 없으면 끝에 추가 |

**주의: `endsWith`를 `startsWith`보다 먼저 체크해야 하는 이유**
- 만약 text가 정확히 서명 자체와 같다면 (예: `"FOX"`), 이것은 `startsWith`와 `endsWith` 모두 true
- 문제 명세에 따르면 끝에 있으면 그대로 반환해야 하므로 `endsWith`를 먼저 검사

### 5. 채점 기준 요약 (CED 공식 배점 기반)

#### SignedText 전체 -- 9점 (CED 공식 배점: Q2 = 9점)
| 포인트 | 채점 항목 | 세부사항 |
|--------|----------|---------|
| +1 | 클래스 헤더 선언: `class SignedText` | `private` 클래스, 클래스 외부 코드, 헤더에 `()` 포함 시 불인정 |
| +1 | 적절한 `private` 인스턴스 변수 선언 + 생성자에서 파라미터로 초기화 | `static` 변수, `private` 누락, 생성자 내부에서 선언, 파라미터 미사용 등은 불인정. signature를 하나의 String으로 미리 계산해 저장해도 인정 |
| +1 | 생성자 헤더 선언: `SignedText(String ___, String ___)` | `private`/`static` 생성자는 불인정 |
| +1 | 메서드 헤더 선언: `public String getSignature()` + `public String addSignature(String ___)` | `public` 누락, 잘못된 메서드 이름, 잘못된 반환/파라미터 타입은 불인정 |
| +1 | firstName을 빈 문자열과 비교 | `length()` 비교 등 암묵적 비교도 인정 |
| +1 | 두 경우 모두에서 적절한 서명 문자열 결정 (*algorithm*) | 일부 경우 반환 누락이어도 인정 (반환 자체는 여기서 미평가) |
| +1 | 클래스 전체에서 올바른 구문으로 `String` 메서드 호출 | `substring`을 한 번만 호출해도 인정. `indexOf`, `contains`, `charAt` 등도 인정. `length`/`equals`만 사용하고 문자열 접근 메서드 미사용 시 불인정 |
| +1 | `addSignature`의 세 가지 필수 경우를 적절한 조건으로 식별 | 잘못된 문자열을 반환하는 경우가 있어도 인정 |
| +1 | `addSignature`가 세 경우 모두에서 적절한 `String` 반환 (*algorithm*) | `getSignature` 잘못 호출/구현해도 세 경우 분기가 맞으면 인정. 세 경우 미식별, 올바른 문자열을 잘못된 경우에 배정, 반환 대신 출력은 불인정 |

### 6. 흔한 실수

1. **`class` 선언 누락** -- Q2는 전체 클래스를 써야 한다. `public class SignedText { }` 필수
2. **인스턴스 변수를 `public`으로 선언** -- 반드시 `private`
3. **`firstName == ""`로 비교** -- String 비교는 반드시 `.equals()`
4. **`charAt(0)` 사용 시 주의** -- 반환 타입이 `char`이므로 `+ "-"`와 연결하면 숫자가 될 수 있음. `substring(0,1)`이 안전
5. **`endsWith`/`startsWith` 순서 뒤바뀜** -- 서명이 text 전체일 때 두 조건 모두 true가 되므로 순서가 중요
6. **`addSignature`에서 `getSignature()` 미사용** -- 서명을 직접 재계산하면 중복 코드 + 실수 가능성

### 7. 부분점수 전략

- 클래스 선언 + 인스턴스 변수 + 생성자만 써도 3점 확보
- `getSignature()`의 빈 문자열 케이스만 맞아도 1점
- `addSignature()`에서 서명이 없을 때 추가하는 것만 맞아도 1점
- 나머지가 틀려도 구조가 올바르면 부분점수 가능

---

## Q3. Round (ArrayList)

### 1. 문제 요약

토너먼트 라운드를 관리하는 클래스. 선수(`Competitor`)를 짝지어 경기(`Match`)를 만든다.

- **(a) Round 생성자**: `String[] names`를 받아 `competitorList` (ArrayList\<Competitor\>)를 초기화. 이름 순서대로 rank 1, 2, 3... 부여
- **(b) `buildMatches()`**: competitorList에서 선수들을 짝지어 Match 객체의 ArrayList를 반환
  - 짝수 명: 1위 vs 꼴찌, 2위 vs 꼴찌에서2번째, ...
  - 홀수 명: 1위는 부전승(bye), 나머지를 짝수 규칙으로 매칭

### 2. 접근 전략

**Part (a):**
1. `competitorList = new ArrayList<Competitor>()`
2. names 배열을 순회하며 `new Competitor(names[i], i + 1)` 생성 후 add

**Part (b):**
1. 시작 인덱스 결정: 짝수면 0, 홀수면 1
2. 앞쪽 포인터와 뒤쪽 포인터로 양끝에서 만나면서 Match 생성
3. `new Match(앞선수, 뒤선수)`를 ArrayList에 add

### 3. 정답 코드

#### Part (a): Round 생성자

```java
public Round(String[] names)
{
    competitorList = new ArrayList<Competitor>();

    for (int i = 0; i < names.length; i++)
    {
        competitorList.add(new Competitor(names[i], i + 1));
    }
}
```

#### Part (b): buildMatches

```java
public ArrayList<Match> buildMatches()
{
    ArrayList<Match> matches = new ArrayList<Match>();

    int start = 0;
    if (competitorList.size() % 2 == 1)
    {
        start = 1;
    }

    int end = competitorList.size() - 1;

    for (int i = start; i < end; i++)
    {
        matches.add(new Match(competitorList.get(i),
                              competitorList.get(end)));
        end--;
    }

    return matches;
}
```

**또는 더 명확한 two-pointer 스타일:**

```java
public ArrayList<Match> buildMatches()
{
    ArrayList<Match> matches = new ArrayList<Match>();

    int left;
    if (competitorList.size() % 2 == 1)
    {
        left = 1;
    }
    else
    {
        left = 0;
    }

    int right = competitorList.size() - 1;

    while (left < right)
    {
        matches.add(new Match(competitorList.get(left),
                              competitorList.get(right)));
        left++;
        right--;
    }

    return matches;
}
```

### 4. 코드 설명

#### Part (a)
| 코드 | 왜 필요한가 |
|------|------------|
| `competitorList = new ArrayList<Competitor>()` | 인스턴스 변수 초기화. `new`를 빠뜨리면 NullPointerException |
| `i + 1` | rank는 1부터 시작 (인덱스는 0부터) |
| `new Competitor(names[i], i + 1)` | 이름과 랭크로 Competitor 객체 생성 |

#### Part (b)
| 코드 | 왜 필요한가 |
|------|------------|
| `competitorList.size() % 2 == 1` | 홀수인지 확인 -- 홀수면 1위(인덱스 0)는 건너뜀 |
| `left = 1` (홀수일 때) | 1위 부전승 처리 |
| `left < right` | 두 포인터가 만나면 종료 |
| `competitorList.get(left)` | ArrayList에서 인덱스로 접근할 때는 `get()` 사용 (배열처럼 `[]` 불가) |
| `new Match(...)` | 짝지은 두 선수로 Match 객체 생성 |

### 5. 채점 기준 요약 (CED 공식 배점 기반)

#### Part (a) Round 생성자 -- 4점
| 포인트 | 채점 항목 | 세부사항 |
|--------|----------|---------|
| +1 | `names`의 모든 원소에 접근 (bounds error 없이) | `names` 잘못 접근 시 불인정 |
| +1 | 각 competitor에 대한 rank를 1부터 시작하여 초기화/유지 | 초기값 0이라도 접근 시 +1 오프셋이면 인정. `Competitor` 생성 실패해도 rank 계산이 맞으면 인정. rank를 잘못 계산하면 불인정 |
| +1 | 주어진 name과 계산된 rank로 `Competitor` 객체 생성 | name/rank 접근이 틀려도 `new Competitor(name, rank)` 형태면 인정. `new` 누락이나 파라미터 타입/개수 오류는 불인정 |
| +1 | 모든 competitor를 올바른 순서로 `competitorList`에 추가 (*algorithm*) | `competitorList` 초기화 누락이어도 add 로직이 맞으면 인정. `Competitor` 미생성 시 불인정. `competitorList`를 지역변수로 재선언하면 불인정 |

#### Part (b) buildMatches -- 5점
| 포인트 | 채점 항목 | 세부사항 |
|--------|----------|---------|
| +1 | 지역 `ArrayList<Match>` 선언 및 초기화 | 다른 지역변수가 있어도 `ArrayList` 미선언 시 불인정 |
| +1 | `competitorList` 양끝에서 이동하는 인덱스 초기화/유지 (*algorithm*) | 0 대신 1에서 시작하거나 그 반대여도 인정. 별도 인덱스 변수 2개 사용도 인정. 양끝에서 세지 않으면 불인정 |
| +1 | 짝수/홀수 비교에 기반하여 시작 인덱스 결정 | 인덱스를 잘못 계산해도 짝수/홀수 경우가 다른 인덱스에서 시작하면 인정. 짝수/홀수 판별 자체가 틀리면 불인정 |
| +1 | 유지된 인덱스로 `competitorList`에서 두 원소를 얻어 `Match` 객체를 생성하고 지역 리스트에 추가 | `new` 누락이어도 인정 (이 항목에서 `new`는 미평가). 잘못된 인덱스, `Match` 미생성, 파라미터 오류는 불인정 |
| +1 | 올바른 수의 쌍으로 리스트를 채움 -- 홀수일 때 첫 번째 competitor 생략, bounds error 없음 (*algorithm*) | `ArrayList` 반환 누락이어도 인정. 짝수/홀수 판별이 틀려도 의도가 명확하면 인정. 홀수에서 첫 번째 포함, 짝수에서 첫 번째 생략, 중간 지점 초과, 인덱스 대신 competitor 추가, `competitorList` 영구 변경은 불인정 |

### 6. 흔한 실수

1. **rank를 0부터 시작** -- rank는 1부터! `i + 1`을 잊으면 감점
2. **`competitorList`를 지역변수로 선언** -- `ArrayList<Competitor> competitorList = ...`라고 쓰면 인스턴스 변수가 아닌 지역변수가 됨. 타입 선언 없이 `competitorList = ...`로 써야 함
3. **`[]` 대신 `.get()` 사용** -- ArrayList는 배열이 아니므로 `competitorList[i]` 불가
4. **홀수일 때 처리 누락** -- 홀수 케이스를 처리하지 않으면 1위가 두 번 매칭됨
5. **매칭 방향 오해** -- 1위 vs 꼴찌 (양 끝에서 안쪽으로)
6. **competitorList 변경** -- Postcondition에 "unchanged"라고 명시됨. remove 사용 금지!

### 7. 부분점수 전략

- Part (a): ArrayList 생성 + for 루프만 맞아도 2점
- Part (b): ArrayList\<Match\> 생성 + return만 해도 1점
- 홀수 처리가 틀려도 짝수 매칭이 맞으면 상당 부분 점수 획득
- Match 생성 시 두 Competitor 순서는 어느 쪽이든 OK ("may appear in either order")

---

## Q4. SumOrSameGame (2D Array)

### 1. 문제 요약

숫자 퍼즐 게임. 2D 배열에서 두 원소의 합이 10이거나 값이 같으면 pair로 제거(0으로 설정).

- **(a) 생성자**: `numRows x numCols` 크기의 2D 배열을 만들고, 1~9의 랜덤 정수로 채움 (각 값이 나올 확률 동일)
- **(b) `clearPair(int row, int col)`**: 주어진 위치의 원소와 pair가 되는 다른 원소를 찾아 둘 다 0으로 설정
  - pair 조건: (1) 상대 원소의 행 인덱스 >= row, (2) 두 값의 합이 10이거나 같은 값
  - 찾으면 true, 못 찾으면 false 반환

### 2. 접근 전략

**Part (a):**
1. `puzzle = new int[numRows][numCols]`
2. 이중 루프로 각 원소에 `(int)(Math.random() * 9) + 1` 할당

**Part (b):**
1. `puzzle[row][col]`의 값을 저장
2. row번째 행부터 마지막 행까지 탐색
3. 같은 행이면 자기 자신(col) 이후부터, 이후 행이면 처음부터 탐색
4. 값이 1~9이고 (합이 10 OR 같은 값)인 원소 발견 시 둘 다 0으로 설정, true 반환
5. 못 찾으면 false 반환

**주의:** "행 인덱스 >= row"이므로 같은 행의 **앞쪽 열**도 탐색 대상이다. 단, 자기 자신은 제외해야 한다.

### 3. 정답 코드

#### Part (a): 생성자

```java
public SumOrSameGame(int numRows, int numCols)
{
    puzzle = new int[numRows][numCols];

    for (int r = 0; r < numRows; r++)
    {
        for (int c = 0; c < numCols; c++)
        {
            puzzle[r][c] = (int)(Math.random() * 9) + 1;
        }
    }
}
```

#### Part (b): clearPair

```java
public boolean clearPair(int row, int col)
{
    int val = puzzle[row][col];

    for (int r = row; r < puzzle.length; r++)
    {
        for (int c = 0; c < puzzle[r].length; c++)
        {
            if (!(r == row && c == col))
            {
                int other = puzzle[r][c];

                if (other != 0 && (val + other == 10 || val == other))
                {
                    puzzle[row][col] = 0;
                    puzzle[r][c] = 0;
                    return true;
                }
            }
        }
    }

    return false;
}
```

### 4. 코드 설명

#### Part (a)
| 코드 | 왜 필요한가 |
|------|------------|
| `puzzle = new int[numRows][numCols]` | 인스턴스 변수 puzzle 초기화. 타입 선언 없이! |
| `(int)(Math.random() * 9) + 1` | 1~9 랜덤. `Math.random()`은 0.0 이상 1.0 미만이므로 `* 9`하면 0~8, `+ 1`하면 1~9 |
| 이중 for 루프 | 2D 배열의 모든 원소 순회 |

#### Part (b)
| 코드 | 왜 필요한가 |
|------|------------|
| `int val = puzzle[row][col]` | 기준 원소의 값 저장 |
| `for (int r = row; ...)` | **row 이상**의 행만 탐색 (조건: 행 인덱스 >= row) |
| `for (int c = 0; ...)` | 각 행의 모든 열 탐색 (같은 행의 앞쪽 열도 포함) |
| `!(r == row && c == col)` | 자기 자신은 제외 |
| `other != 0` | 이미 제거된 원소(0)는 건너뜀. 문제에서 값은 1~9 사이라고 했지만, 이전 clearPair 호출로 0이 될 수 있음 |
| `val + other == 10 \|\| val == other` | pair 조건: 합이 10 OR 같은 값 |
| `puzzle[row][col] = 0; puzzle[r][c] = 0;` | 둘 다 제거 |
| `return true;` | 즉시 반환 -- 첫 번째 매칭만 처리 |
| `return false;` | 루프 끝까지 못 찾으면 |

### 5. 채점 기준 요약 (CED 공식 배점 기반)

#### Part (a) SumOrSameGame 생성자 -- 4점
| 포인트 | 채점 항목 | 세부사항 |
|--------|----------|---------|
| +1 | 올바른 크기의 2D `int` 배열을 생성하여 인스턴스 변수 `puzzle`에 할당 | `puzzle`을 지역변수로 재선언하면 불인정. 값 출력/반환은 불인정 |
| +1 | 2D 배열을 순회 (bounds error 없이) | 배열 생성 실패해도 순회 범위가 맞으면 인정. 2D 배열 원소에 접근하지 않으면 불인정 |
| +1 | `[1, 9]` 범위의 균등 랜덤 정수 생성 | `Math.random()` 미호출, 잘못된 호출, `Math.` 없이 `random` 호출, `int` 캐스팅 누락은 불인정 |
| +1 | 2D 배열 원소에 값 할당 (*algorithm*) | 랜덤 값이 틀려도 할당 로직이 맞으면 인정. 랜덤 값 외의 값 할당, 올바르게 초기화 후 다른 곳에 할당, 동일 값을 모든 원소에 할당, 전체 미할당은 불인정 |

#### Part (b) clearPair -- 5점
| 포인트 | 채점 항목 | 세부사항 |
|--------|----------|---------|
| +1 | `row` 이상의 행에서 `puzzle`의 필요한 모든 원소에 접근 (bounds error 없이) | 추가 행 접근이어도 self-pairing 방지가 되면 인정. 자기 자신과 페어링해도 인정 (이 항목). early return이어도 범위 내 접근이 맞으면 인정. `puzzle` 원소 접근 실패 시 불인정 |
| +1 | 자기 자신과의 페어링 방지 | 잘못된 self-pairing guard로 추가 원소를 누락해도 인정 가능. 루프가 없으면 불인정 |
| +1 | 두 원소가 같거나 합이 10인지 판별 | 자기 자신과 페어링해도 인정. 루프가 없어도 인정. 조건 하나만 테스트하면 불인정 |
| +1 | 루프 안에서 2D 배열 원소를 0으로 설정 | 식별된 원소 중 하나만 0으로 설정해도 인정. 원소를 잘못 식별해도 인정. 2개 초과 원소를 0으로 설정해도 인정 |
| +1 | 매치 발견 시 식별된 원소를 0으로 설정하고 양쪽 경우에 적절한 `boolean` 반환 (*algorithm*) | 원소를 잘못 식별해도 조건 분기가 맞으면 인정. 한쪽만 0으로 설정, 기준 원소 외 2개 이상 변경, early return으로 잘못된 값 반환, 클리어 후 미반환은 불인정 |

### 6. 흔한 실수

1. **랜덤 범위 오류** -- `(int)(Math.random() * 9)`는 0~8. `+ 1`을 잊으면 0이 포함됨
2. **`(int)` 캐스팅 위치** -- `(int)(Math.random() * 9)`가 맞음. `(int)Math.random() * 9`는 항상 0
3. **자기 자신과 매칭** -- `r == row && c == col`일 때 건너뛰어야 함. 같은 값 조건에서 자기 자신과 매칭하면 오류
4. **같은 행의 앞쪽 열 누락** -- 조건이 "행 인덱스 >= row"이므로, 같은 행에서 col보다 작은 열도 탐색 대상. `c = col + 1`부터 시작하면 안 됨!
5. **0인 원소와 매칭** -- 이미 cleared된 원소(0)도 매칭 대상이 되면 안 됨. `other >= 1 && other <= 9` 또는 `other != 0` 체크 필요
6. **한 쪽만 0으로 설정** -- 두 원소 모두 0으로 설정해야 함
7. **`puzzle.length` vs `puzzle[0].length`** -- 행 수는 `puzzle.length`, 열 수는 `puzzle[r].length`

### 7. 부분점수 전략

- Part (a): `puzzle = new int[numRows][numCols]`만 써도 1점
- Part (b): 이중 루프 구조만 맞아도 1점
- pair 조건이 하나만 맞아도 (합 10만 또는 같은 값만) 부분점수
- `return false;`를 루프 밖에 쓰기만 해도 반환 구조 점수
- 자기 자신 제외를 못해도 나머지 로직이 맞으면 1점만 감점

---

## 종합 요약표

| 문제 | 유형 | 핵심 개념 | 킬러 포인트 |
|------|------|----------|------------|
| Q1 | Method/Control | `Math.min`, 보너스 조건 | 보너스가 개당이 아니라 시간당 $3 |
| Q2 | Class Design | String 메서드, 전체 클래스 | `endsWith`를 `startsWith`보다 먼저 체크 |
| Q3 | ArrayList | 생성자, two-pointer 매칭 | 홀수일 때 1위 건너뛰기, `get()` 사용 |
| Q4 | 2D Array | 랜덤, 이중 루프 탐색 | 같은 행 앞쪽 열도 탐색, 자기 자신 제외 |

### 시험 당일 최종 체크리스트

1. 모든 메서드에 `return`문이 있는가? (void 제외)
2. ArrayList는 `new`로 생성했는가?
3. String 비교는 `.equals()`인가?
4. 루프 범위가 inclusive/exclusive 맞는가?
5. 인스턴스 변수에 타입을 다시 선언하지 않았는가? (지역변수와 혼동 주의)
6. helper 메서드를 문제에서 요구한 대로 사용했는가?
