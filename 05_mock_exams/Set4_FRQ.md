# AP CSA 2026 모의시험 Set 4 — FRQ (4문제)

> 총 25점 (Q1: 7점, Q2: 7점, Q3: 5점, Q4: 6점)

---

## Q1. Methods and Control Structures (7점)

### 시나리오: 학생 성적 계산기

한 학교에서 학생의 가중 평균 성적을 계산하고 성적표 문자열을 생성하는 시스템을 관리합니다. `GradeCalculator` 클래스의 일부가 아래에 나와 있습니다.

```java
public class GradeCalculator {
    private int[] scores;          // 각 과목별 점수 (0~100)
    private double[] weights;      // 각 과목별 가중치 (합이 1.0)
    private String studentInfo;    // "이름-학번-학년" 형식 (예: "Kim-20251234-11")
    private boolean isHonors;      // 우등반 여부

    /** Returns the number of subjects.
     *  Precondition: scores.length == weights.length, scores.length >= 1
     */
    public int getNumSubjects()
    { /* implementation not shown */ }

    /** Returns the score for the given subject index.
     *  Precondition: 0 <= idx < getNumSubjects()
     */
    public int getScore(int idx)
    { /* implementation not shown */ }

    /** Returns the weight for the given subject index.
     *  Precondition: 0 <= idx < getNumSubjects()
     */
    public double getWeight(int idx)
    { /* implementation not shown */ }

    /** Returns the student info string.
     */
    public String getStudentInfo()
    { /* implementation not shown */ }

    /** Returns true if the student is in the honors program.
     */
    public boolean getIsHonors()
    { /* implementation not shown */ }

    /** Computes and returns the weighted average grade.
     *
     *  The weighted average is computed as:
     *    sum of (score[i] * weight[i]) for all subjects
     *
     *  If the student is in honors AND the weighted average before bonus
     *  is >= 80.0, add a 5-point bonus.
     *
     *  The final grade is capped at 100.0 (cannot exceed 100.0).
     *
     *  Precondition: weights sum to 1.0
     */
    public double getWeightedAverage()
    { /* to be implemented in Part A */ }

    /** Returns a grade report string in the following format:
     *
     *    "NAME (ID, Grade GRADE): AVG - LETTER"
     *
     *  studentInfo has the form "NAME-ID-GRADE" with exactly two "-" characters.
     *  Use split("-") to obtain the three parts in order:
     *    parts[0] = NAME, parts[1] = ID, parts[2] = GRADE
     *
     *  AVG is the result of getWeightedAverage() (as a double).
     *  LETTER is determined by:
     *      AVG >= 90: "A"
     *      AVG >= 80: "B"
     *      AVG >= 70: "C"
     *      AVG >= 60: "D"
     *      otherwise: "F"
     *
     *  Examples:
     *    studentInfo "Kim-20251234-11", weightedAverage 92.5
     *      → "Kim (20251234, Grade 11): 92.5 - A"
     *    studentInfo "Lee-20250001-9", weightedAverage 73.0
     *      → "Lee (20250001, Grade 9): 73.0 - C"
     *
     *  Precondition: studentInfo contains exactly two "-" characters and
     *                NAME, ID, GRADE are all non-empty.
     */
    public String getGradeReport()
    { /* to be implemented in Part B */ }
}
```

**예시:**

| scores | weights | studentInfo | isHonors | getWeightedAverage() | getGradeReport() |
|--------|---------|-------------|----------|---------------------|-------------------|
| {90, 85, 95} | {0.4, 0.3, 0.3} | "Kim-20251234-11" | true | 95.0 | "Kim (20251234, Grade 11): 95.0 - A" |
| {70, 60, 80} | {0.5, 0.3, 0.2} | "Lee-20250001-9" | false | 69.0 | "Lee (20250001, Grade 9): 69.0 - D" |
| {95, 98, 100} | {0.3, 0.3, 0.4} | "Park-20253333-12" | true | 100.0 | "Park (20253333, Grade 12): 100.0 - A" |

*참고: 첫 행 → 90*0.4+85*0.3+95*0.3 = 90.0, honors+>=80 → 95.0. 셋째 행 → 97.9, honors+>=80 → 102.9, cap → 100.0.*

### Part A (4점)

`getWeightedAverage` 메서드를 작성하세요.

### Part B (3점)

`getGradeReport` 메서드를 작성하세요.

---

### 정답 코드

#### Part A (4점)
```java
public double getWeightedAverage() {
    double sum = 0;
    for (int i = 0; i < getNumSubjects(); i++) {
        sum += getScore(i) * getWeight(i);
    }

    if (getIsHonors() && sum >= 80.0) {
        sum += 5.0;
    }

    if (sum > 100.0) {
        sum = 100.0;
    }

    return sum;
}
```

#### Part B (3점)
```java
public String getGradeReport() {
    String info = getStudentInfo();
    String[] parts = info.split("-");
    String name = parts[0];
    String id = parts[1];
    String grade = parts[2];

    double avg = getWeightedAverage();
    String letter;
    if (avg >= 90) {
        letter = "A";
    } else if (avg >= 80) {
        letter = "B";
    } else if (avg >= 70) {
        letter = "C";
    } else if (avg >= 60) {
        letter = "D";
    } else {
        letter = "F";
    }

    return name + " (" + id + ", Grade " + grade + "): " + avg + " - " + letter;
}
```

*대안 풀이 (substring + indexOf 사용):*
```java
public String getGradeReport() {
    String info = getStudentInfo();
    int firstDash = info.indexOf("-");
    String name = info.substring(0, firstDash);

    String rest = info.substring(firstDash + 1);
    int secondDash = rest.indexOf("-");
    String id = rest.substring(0, secondDash);
    String grade = rest.substring(secondDash + 1);

    double avg = getWeightedAverage();
    String letter;
    if (avg >= 90)      letter = "A";
    else if (avg >= 80) letter = "B";
    else if (avg >= 70) letter = "C";
    else if (avg >= 60) letter = "D";
    else                letter = "F";

    return name + " (" + id + ", Grade " + grade + "): " + avg + " - " + letter;
}
```

### Q1 채점 기준 (7점)

#### Part A (4점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 1 | `getNumSubjects()`, `getScore(i)`, `getWeight(i)`를 사용하여 루프로 `score[i] * weight[i]`의 합계 산출 *(algorithm)* | 인스턴스 변수 직접 접근도 earn 가능. 루프 없이 하드코딩하면 earn 불가 | 1점 |
| 2 | `getIsHonors()` AND `sum >= 80.0` 일 때 5점 보너스 추가 *(algorithm)* | `&&` 대신 `\|\|` 사용 시 earn 불가. 보너스를 무조건 적용하면 earn 불가. 경계값 80.0에서 `>` 대신 `>=` 필요 | 1점 |
| 3 | 최종 점수가 100.0을 초과하면 100.0으로 보정 *(algorithm)* | `if (sum > 100.0) sum = 100.0;` 같은 if 비교로 cap 처리. 보정 누락 시 earn 불가 | 1점 |
| 4 | 올바른 순서: 가중 합계 → honors 보너스 → 100점 cap → 반환 *(algorithm)* | cap을 보너스 전에 적용하면 결과가 달라질 수 있음 → earn 불가. 반환 누락 시 earn 불가 | 1점 |

**Can still earn:** 헬퍼 메서드 대신 인스턴스 변수 직접 접근해도 알고리즘 포인트는 earn 가능.
**Will not earn:** 가중 합계를 아예 계산하지 않으면 포인트 1을 earn 불가.

#### Part B (3점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 5 | `studentInfo`를 NAME / ID / GRADE 세 부분으로 올바르게 분리 *(algorithm)* | `split("-")` 사용 시 `parts[0]`, `parts[1]`, `parts[2]` 세 부분 모두 정확히 추출하면 earn. `indexOf`와 substring을 두 번 적용한 풀이도 동일하게 earn. 하드코딩 인덱스는 earn 불가 | 1점 |
| 6 | `getWeightedAverage()` 결과에 따라 letter grade 분기 (A/B/C/D/F) *(algorithm)* | 경계값(90, 80, 70, 60) 처리 올바르고 우선순위 맞아야 함. `>` 대신 `>=` 필요 | 1점 |
| 7 | 올바른 형식의 성적표 문자열 조합 — `"NAME (ID, Grade GRADE): AVG - LETTER"` | 괄호, 콜론, 쉼표 등 형식이 크게 어긋나면 earn 불가. 사소한 공백 오류는 의도 명확하면 earn 가능 | 1점 |

**Can still earn:** Part A의 `getWeightedAverage()`가 틀려도 Part B에서 호출 로직이 올바르면 Part B 점수는 독립적으로 earn 가능.
**Will not earn:** String 메서드(`split`, `substring`, `indexOf`)를 전혀 사용하지 않고 분리하지 못하면 포인트 5를 earn 불가.

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)
- `else if` 대신 독립 `if`문을 사용했지만 로직이 동일하면

### 흔한 실수
- 가중 합계에서 `getScore(i) * getWeight(i)` 대신 단순 평균 계산
- honors 보너스를 무조건 적용 (조건 체크 누락)
- 100점 cap을 보너스 추가 전에 적용
- `split("-")` 결과 인덱스를 잘못 사용 (parts[1]이 ID인데 parts[2]를 ID로 처리)
- `substring`을 사용할 때 끝 인덱스에 `+1` 누락하여 대시가 포함됨
- letter grade 경계값에서 `>` 대신 `>=` 사용해야 함

---

## Q2. Class Design (7점)

### 시나리오: 온도 변환기 클래스

섭씨와 화씨 온도를 저장하고 변환하는 `Temperature` 클래스를 설계합니다.

변환 공식:
- 섭씨 → 화씨: `F = C × 9/5 + 32`
- 화씨 → 섭씨: `C = (F - 32) × 5/9`

### 작성할 클래스

```java
public class Temperature {
    // instance variable(s)

    /** Constructs a Temperature object with the given value in Celsius.
     */
    public Temperature(double celsius)

    /** Returns the temperature in Celsius.
     */
    public double getCelsius()

    /** Returns the temperature in Fahrenheit.
     */
    public double getFahrenheit()

    /** Increases the temperature by the given amount in Celsius.
     *  Precondition: delta can be positive or negative.
     */
    public void adjust(double delta)

    /** Returns true if this temperature is below freezing (0°C).
     */
    public boolean isBelowFreezing()

    /** Returns a string in the format "C_TENTHS / F_TENTHS"
     *  where C_TENTHS is Celsius rounded to 1 decimal place and
     *  F_TENTHS is Fahrenheit rounded to 1 decimal place.
     *
     *  Round each value to 1 decimal using the arithmetic idiom:
     *      (int)(value * 10 + 0.5) / 10.0   (for value >= 0)
     *      (int)(value * 10 - 0.5) / 10.0   (for value <  0)
     *
     *  Examples:
     *    Temperature with celsius == 100.0  → "100.0 / 212.0"
     *    Temperature with celsius == -10.0  → "-10.0 / 14.0"
     *    Temperature with celsius == 36.789 → "36.8 / 98.2"
     *
     *  Precondition: -1000.0 <= celsius <= 1000.0.
     */
    public String getDisplayString()
}
```

**실행 예시 (Execution Table):**

| Statement / Expression | Return Value | Comment |
|----------------------|-------------|---------|
| `Temperature t = new Temperature(100);` | | 100°C로 생성 |
| `t.getCelsius()` | `100.0` | 섭씨 반환 |
| `t.getFahrenheit()` | `212.0` | 화씨 변환 반환 |
| `t.isBelowFreezing()` | `false` | 100°C > 0°C |
| `t.adjust(-110)` | | -110 조정 → -10°C |
| `t.getCelsius()` | `-10.0` | 조정 후 섭씨 |
| `t.getFahrenheit()` | `14.0` | -10°C의 화씨 |
| `t.isBelowFreezing()` | `true` | -10°C < 0°C |
| `t.getDisplayString()` | `"-10.0 / 14.0"` | 반올림 적용 형식 |
| `Temperature t2 = new Temperature(0);` | | 0°C로 생성 |
| `t2.isBelowFreezing()` | `false` | 0°C는 "below"가 아님 |
| `Temperature t3 = new Temperature(36.789);` | | 36.789°C로 생성 |
| `t3.getDisplayString()` | `"36.8 / 98.2"` | 36.789→36.8, 98.2202→98.2 |

---

### 정답 코드

```java
public class Temperature {
    private double celsius;

    public Temperature(double celsius) {
        this.celsius = celsius;
    }

    public double getCelsius() {
        return celsius;
    }

    public double getFahrenheit() {
        return celsius * 9.0 / 5 + 32;
    }

    public void adjust(double delta) {
        celsius += delta;
    }

    public boolean isBelowFreezing() {
        return celsius < 0;
    }

    public String getDisplayString() {
        double roundedC;
        if (celsius >= 0) {
            roundedC = (int)(celsius * 10 + 0.5) / 10.0;
        } else {
            roundedC = (int)(celsius * 10 - 0.5) / 10.0;
        }

        double f = getFahrenheit();
        double roundedF;
        if (f >= 0) {
            roundedF = (int)(f * 10 + 0.5) / 10.0;
        } else {
            roundedF = (int)(f * 10 - 0.5) / 10.0;
        }

        return roundedC + " / " + roundedF;
    }
}
```

### Q2 채점 기준 (7점)

| # | 알고리즘 포인트 | 채점 기준 | Decision Rules | 배점 |
|---|--------------|---------|---------------|------|
| 1 | **Instance Variable** | `private double celsius` 인스턴스 변수 선언 | `public` 선언 시 earn 불가. 여러 변수(celsius + fahrenheit 둘 다)를 두는 것은 비효율적이지만 로직 올바르면 earn 가능 | 1점 |
| 2 | **Constructor** | 생성자에서 `celsius` 올바르게 초기화 | 매개변수 할당 누락 시 earn 불가 | 1점 |
| 3 | **Accessor — getCelsius** | `getCelsius()`: `celsius` 반환 | 다른 값 반환 시 earn 불가 | 1점 |
| 4 | **Accessor — getFahrenheit** | `getFahrenheit()`: `celsius * 9.0 / 5 + 32` 변환 공식 올바름 | `9/5` (정수 나눗셈 → 1) 사용 시 earn 불가. `9.0/5` 또는 `(double)9/5` 필요 | 1점 |
| 5 | **Mutator — adjust** | `adjust(double delta)`: `celsius += delta`로 값 변경 | 새 지역변수에 할당하고 인스턴스 변수 미변경 시 earn 불가 | 1점 |
| 6 | **Boolean Method** | `isBelowFreezing()`: `celsius < 0` 반환 | `<= 0` 사용 시 earn 불가 (0도는 freezing point이지 below가 아님) | 1점 |
| 7 | **getDisplayString** | `getDisplayString()`: `(int)(value * 10 + 0.5) / 10.0` 산술 관용구로 양수/음수 모두 1자리 반올림 + `"C / F"` 형식 문자열 반환 | 반올림 관용구 누락 시 형식이 맞으면 earn 가능하지만 1점 감점. `toString` 메서드 시그니처로 작성하면 EXCLUSION 위반이지만 명세된 시그니처 준수 여부는 채점 외 | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)
- `this.` 사용 여부는 채점에 영향 없음
- 반올림에서 양수만 처리하고 음수 케이스를 누락 — 명세된 예시가 모두 양/음 동작을 다루므로 1점 감점

### 흔한 실수
- `getFahrenheit()`에서 `9/5`로 정수 나눗셈 사용 → 항상 1을 곱하게 됨 (`9/5 = 1`). 반드시 `9.0/5` 또는 `(double)9/5` 사용
- instance variable을 `public`으로 선언 (캡슐화 위반)
- `getDisplayString()`에서 반올림 로직 빠뜨림 (그냥 그대로 출력)
- `isBelowFreezing()`에서 `<=` 사용 (0도는 정확히 freezing point이지 below가 아님)
- `adjust()`에서 celsius 대신 새 변수에 할당 (원본 미변경)
- 메서드 이름을 `toString`으로 작성 — 본 명세는 별도 메서드 `getDisplayString`을 요구함 (AP CSA 범위에서 `toString` 오버라이드 작성은 OUT)

---

## Q3. ArrayList (5점)

### 시나리오: 일정 충돌 감지 (EventScheduler)

일정 목록에서 시간이 겹치는 이벤트를 찾아내는 시스템입니다.

```java
public class Event {
    /** 이벤트 이름을 반환합니다. */
    public String getName()
    { /* implementation not shown */ }

    /** 시작 시간을 반환합니다 (0~2359 형식, 예: 1430 = 오후 2시 30분). */
    public int getStartTime()
    { /* implementation not shown */ }

    /** 종료 시간을 반환합니다 (0~2359 형식). */
    public int getEndTime()
    { /* implementation not shown */ }
}
```

```java
import java.util.ArrayList;

public class EventScheduler {
    private ArrayList<Event> events;

    public EventScheduler(ArrayList<Event> events) {
        this.events = events;
    }

    /**
     * 주어진 이벤트(target)와 시간이 겹치는 모든 이벤트의 이름을
     * ArrayList<String>으로 반환합니다.
     *
     * 두 이벤트가 "겹친다"는 것은:
     * - target의 시작 시간이 다른 이벤트의 종료 시간보다 작고 (target.getStartTime() < other.getEndTime())
     * - target의 종료 시간이 다른 이벤트의 시작 시간보다 큰 경우 (target.getEndTime() > other.getStartTime())
     *
     * target 자신은 결과에 포함하지 않습니다.
     * (target과 같은 이름의 다른 이벤트는 포함할 수 있습니다.)
     * 반환 리스트의 순서는 events에서의 원래 순서와 같아야 합니다.
     * 겹치는 이벤트가 없으면 빈 ArrayList를 반환합니다.
     *
     * Precondition: target은 events에 포함된 이벤트이고, null이 아닙니다.
     *               모든 이벤트에서 getStartTime() < getEndTime()
     *
     * @param target 충돌을 확인할 기준 이벤트
     * @return 시간이 겹치는 이벤트의 이름 리스트
     */
    public ArrayList<String> findConflicts(Event target) {
        /* 여기에 구현 */
    }
}
```

`findConflicts` 메서드를 구현하세요.

**예시:**

`events`가 다음과 같을 때:

| 이름 | 시작 시간 | 종료 시간 |
|------|----------|----------|
| "Math" | 900 | 1030 |
| "English" | 1000 | 1130 |
| "Lunch" | 1200 | 1300 |
| "Science" | 1030 | 1200 |

target이 "Math" (900~1030)일 때:
- "English" (1000~1130): 900 < 1130 AND 1030 > 1000 → 겹침
- "Lunch" (1200~1300): 900 < 1300 AND 1030 > 1200? → 1030 > 1200 거짓 → 안 겹침
- "Science" (1030~1200): 900 < 1200 AND 1030 > 1030? → 1030 > 1030 거짓 → 안 겹침

반환값: `["English"]`

---

### 정답 코드

```java
public ArrayList<String> findConflicts(Event target) {
    ArrayList<String> result = new ArrayList<String>();

    for (Event e : events) {
        if (e != target) {
            if (target.getStartTime() < e.getEndTime()
                    && target.getEndTime() > e.getStartTime()) {
                result.add(e.getName());
            }
        }
    }

    return result;
}
```

### Q3 채점 기준 (5점)

| # | 알고리즘 포인트 | 채점 기준 | Decision Rules | 배점 |
|---|--------------|---------|---------------|------|
| 1 | **Initialize** | `ArrayList<String>` 결과 리스트 생성 | `new ArrayList<>()` 또는 `new ArrayList<String>()` 모두 가능 | 1점 |
| 2 | **Traverse** | `events` 리스트를 올바르게 순회 | for-each 또는 인덱스 루프 모두 가능. 범위 오류 시 earn 불가 | 1점 |
| 3 | **Exclude Self** | target 자신을 결과에서 제외 (`e != target`) | `==` 대신 `equals` 사용 시에도 이름만 같은 다른 이벤트를 잘못 제외할 위험. `!=` (참조 비교)가 올바름. 제외 안 하면 earn 불가 | 1점 |
| 4 | **Overlap Check** | 겹침 조건: `target.getStartTime() < e.getEndTime() && target.getEndTime() > e.getStartTime()` | `<=` / `>=` 사용 시 경계값 오류 → earn 불가. 두 조건 중 하나만 체크 시 earn 불가 | 1점 |
| 5 | **Build Result** | 겹치는 이벤트의 `getName()` 결과를 리스트에 추가 + 리스트 반환 | `Event` 객체를 추가하면 타입 불일치로 earn 불가. 반환 누락 시 earn 불가 | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect (원본 events 변경)
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)

### 흔한 실수
- target 자신을 결과에서 제외하지 않음 → 항상 자기 자신이 포함됨
- 겹침 조건에서 `<=` / `>=` 사용 → 끝나는 시간 == 시작하는 시간인 경우를 잘못 겹침으로 판정
- 겹침 조건의 두 부분 중 하나만 체크 → 겹치지 않는 이벤트도 포함됨
- `getName()` 대신 `Event` 객체 자체를 결과에 추가 (타입 불일치)
- `equals()`로 target을 제외하려 함 → 같은 이름의 다른 이벤트까지 제외될 위험

---

## Q4. 2D Array (6점)

### 시나리오: 매출 데이터 분석 (SalesAnalyzer)

한 회사에서 제품별 월간 매출 데이터를 2D 배열로 관리합니다. `SalesAnalyzer` 클래스의 일부가 아래에 나와 있습니다.

```java
public class SalesAnalyzer {

    /** 제품 하나의 정보를 나타냅니다. */
    public class Product {
        /** 제품 이름을 반환합니다. 예: "Widget A" */
        public String getName()
        { /* implementation not shown */ }

        /** 제품 카테고리를 반환합니다. 예: "Electronics" */
        public String getCategory()
        { /* implementation not shown */ }
    }

    /** sales[r][c]는 제품 r의 c번째 월 매출액(정수, 만원 단위)을 나타냅니다.
     *  Precondition: sales는 최소 1행 2열의 직사각형 배열이다.
     */
    private int[][] sales;

    /** products[r]은 제품 r의 Product 객체입니다.
     *  Precondition: products.length == sales.length
     */
    private Product[] products;

    /** sales에서 매출이 연속으로 증가(strictly increasing)한 기간이 가장 긴
     *  제품(행)의 인덱스를 반환합니다.
     *
     *  연속 증가 기간의 길이는 "연속으로 이전 월보다 매출이 큰 월의 수"입니다.
     *  예: 매출이 [10, 20, 30, 25, 35]이면
     *      연속 증가 구간: [10,20,30](길이 2), [25,35](길이 1) → 최대 = 2
     *
     *  최대 연속 증가 기간이 같은 제품이 여러 개 있으면,
     *  인덱스가 가장 작은 제품을 반환합니다.
     *
     *  Precondition: sales는 최소 1행 2열의 직사각형 배열이다.
     */
    public int productWithLongestGrowth() {
        /* 여기에 구현 */
    }
}
```

`productWithLongestGrowth` 메서드를 구현하세요.

**예시:**

`sales`가 다음과 같을 때:

```
              1월     2월     3월     4월     5월     6월
제품 0  |   50  |   60  |   70  |   65  |   80  |   90  |
제품 1  |   30  |   30  |   30  |   30  |   30  |   30  |
제품 2  |   10  |   20  |   15  |   25  |   35  |   45  |
```

- 제품 0: 연속 증가 구간 [50,60,70](길이 2), [65,80,90](길이 2) → 최대 = 2
- 제품 1: 연속 증가 없음 (같은 값은 증가가 아님) → 최대 = 0
- 제품 2: 연속 증가 구간 [10,20](길이 1), [15,25,35,45](길이 3) → 최대 = 3

제품 2의 최대 연속 증가(3)가 가장 크므로 반환값은 **2** 입니다.

---

### 정답 코드

```java
public int productWithLongestGrowth() {
    int bestProduct = 0;
    int bestStreak = 0;

    for (int r = 0; r < sales.length; r++) {
        int maxStreak = 0;
        int currentStreak = 0;

        for (int c = 1; c < sales[r].length; c++) {
            if (sales[r][c] > sales[r][c - 1]) {
                currentStreak++;
                if (currentStreak > maxStreak) {
                    maxStreak = currentStreak;
                }
            } else {
                currentStreak = 0;
            }
        }

        if (maxStreak > bestStreak) {
            bestStreak = maxStreak;
            bestProduct = r;
        }
    }

    return bestProduct;
}
```

### Q4 채점 기준 (6점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 1 | 외부 루프로 각 행(제품)을 순회 (`r < sales.length`) | 범위가 올바르면 earn | 1점 |
| 2 | 내부 루프로 각 열(월)을 순회하되 인덱스 **1**부터 시작 (`c = 1`) | `c = 0`부터 시작하면 `c-1`에서 AIOOBE → earn 불가 | 1점 |
| 3 | `sales[r][c] > sales[r][c-1]` 조건으로 매출 **증가** 판별 *(algorithm)* | `>=` 사용 시 earn 불가 (같은 매출은 증가가 아님) | 1점 |
| 4 | 연속 증가 카운터 관리: 증가 시 증가, 아닐 때 **0으로 리셋** *(algorithm)* | 리셋 누락 시 earn 불가 | 1점 |
| 5 | 각 행의 **최대** 연속 증가 길이를 올바르게 추적 (행 내부에서 max 갱신) *(algorithm)* | 루프 밖에서만 갱신하면 마지막 구간만 기록될 위험 → earn 불가 | 1점 |
| 6 | 전체 행 중 가장 큰 연속 증가의 행 인덱스 추적 + 동점 시 최소 인덱스 + 반환 | `>=` 사용 시 동점에서 마지막 행 반환 → earn 불가. 반환 누락 시 earn 불가 | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴 (원본 sales 배열 변경)
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)
- 변수명이 다르지만 로직이 올바르면 감점 안 함

### 흔한 실수
- 내부 루프를 `c = 0`부터 시작하여 `c - 1`에서 `ArrayIndexOutOfBoundsException`
- `>=` 사용 (같은 매출은 "증가"가 아님 — strictly increasing)
- 연속 증가가 끊겼을 때 `currentStreak`을 0으로 리셋하지 않음
- 행 내부의 `maxStreak` 갱신을 루프 안에서 하지 않고 루프 밖에서만 해서 마지막 구간만 기록
- 전체 행 중 최댓값 비교 시 `>=` 사용 → 동점에서 마지막 행 반환 (최소 인덱스 요구)
- `maxStreak` 초기화를 외부 루프 안에서 하지 않아 이전 행의 값이 누적됨
