# AP Computer Science A — Mock Exam Set 5 (최종 점검용)
# Free Response Questions (4문제 · 90분)

---

## Question 1: Methods and Control Structures (7점)
### 시나리오: 택배 배송 추적기 (Package Delivery Tracker)

한 택배 회사에서 배송 상태를 추적하고 추적 코드를 파싱하는 시스템을 관리합니다. `DeliveryTracker` 클래스의 일부가 아래에 나와 있습니다.

```java
public class DeliveryTracker {
    private double weightKg;       // 패키지 무게 (kg)
    private int distanceKm;        // 배송 거리 (km)
    private boolean isExpress;     // 급행 배송 여부
    private String trackingCode;   // 추적 코드 (예: "STD-SEL-20250410-1234")

    /** Returns the package weight in kg.
     *  Precondition: weightKg > 0
     */
    public double getWeightKg()
    { /* implementation not shown */ }

    /** Returns the delivery distance in km.
     *  Precondition: distanceKm > 0
     */
    public int getDistanceKm()
    { /* implementation not shown */ }

    /** Returns true if this is an express delivery.
     */
    public boolean getIsExpress()
    { /* implementation not shown */ }

    /** Returns the tracking code string.
     */
    public String getTrackingCode()
    { /* implementation not shown */ }

    /** Computes and returns the delivery fee.
     *
     *  Base fee rules:
     *  - If distanceKm <= 10: base fee is 3000 (won)
     *  - If distanceKm <= 50: base fee is 5000
     *  - If distanceKm <= 200: base fee is 8000
     *  - Otherwise: base fee is 8000 + 50 * (distanceKm - 200)
     *
     *  Weight surcharge (added to base fee):
     *  - If weightKg > 20.0: surcharge is 2000 * (int)(weightKg - 20.0)
     *    (truncate to integer, e.g. weightKg 23.7 → (int)(3.7) = 3 → 6000)
     *  - Otherwise: no surcharge
     *
     *  Express multiplier (applied to sum of base fee + surcharge):
     *  - If isExpress: multiply total by 1.5
     *
     *  Precondition: weightKg > 0, distanceKm > 0
     */
    public double getDeliveryFee()
    { /* to be implemented in Part A */ }

    /** Parses the tracking code and returns a summary string.
     *
     *  The tracking code has the format: "TYPE-REGION-DATE-SEQ"
     *  where TYPE, REGION, DATE, and SEQ are separated by "-".
     *
     *  The method returns a string in the format:
     *    "SEQ (REGION) - TYPE delivery on DATE"
     *
     *  TYPE is the substring before the first "-".
     *  SEQ is the substring after the last "-".
     *  REGION is the substring between the first and second "-".
     *  DATE is the substring between the second and last "-".
     *
     *  If TYPE equals "EXP", replace it with "Express" in the output.
     *  If TYPE equals "STD", replace it with "Standard" in the output.
     *  Otherwise, use TYPE as-is.
     *
     *  Examples:
     *    trackingCode "EXP-SEL-20250410-1234"
     *      → "1234 (SEL) - Express delivery on 20250410"
     *    trackingCode "STD-BUS-20250315-5678"
     *      → "5678 (BUS) - Standard delivery on 20250315"
     *
     *  Precondition: trackingCode contains exactly three "-" characters.
     */
    public String getTrackingSummary()
    { /* to be implemented in Part B */ }
}
```

**예시:**

| weightKg | distanceKm | isExpress | trackingCode | getDeliveryFee() | getTrackingSummary() |
|----------|------------|-----------|-------------|-----------------|---------------------|
| 5.0 | 30 | false | "STD-SEL-20250410-1234" | 5000.0 | "1234 (SEL) - Standard delivery on 20250410" |
| 25.5 | 300 | true | "STD-BUS-20250315-5678" | 34500.0 | "5678 (BUS) - Standard delivery on 20250315" |
| 10.0 | 10 | false | "SPL-JEJ-20250101-0001" | 3000.0 | "0001 (JEJ) - SPL delivery on 20250101" |

*참고: 첫 행 → base=5000 (30km<=50), surcharge=0 (5.0<=20), express=no → 5000.0. TYPE="STD" → "Standard". 둘째 행 → base=8000+50*(300-200)=13000, surcharge=2000*(int)(25.5-20.0)=2000*5=10000, (13000+10000)*1.5=34500.0. 셋째 행 → base=3000 (10km<=10), surcharge=0, express=no → 3000.0.*

### Part A (4점)

`getDeliveryFee` 메서드를 작성하세요.

### Part B (3점)

`getTrackingSummary` 메서드를 작성하세요.

---

### 정답 코드

#### Part A (4점)
```java
public double getDeliveryFee() {
    int base;
    if (getDistanceKm() <= 10) {
        base = 3000;
    } else if (getDistanceKm() <= 50) {
        base = 5000;
    } else if (getDistanceKm() <= 200) {
        base = 8000;
    } else {
        base = 8000 + 50 * (getDistanceKm() - 200);
    }

    int surcharge = 0;
    if (getWeightKg() > 20.0) {
        surcharge = 2000 * (int)(getWeightKg() - 20.0);
    }

    double total = base + surcharge;

    if (getIsExpress()) {
        total = total * 1.5;
    }

    return total;
}
```

#### Part B (3점)
```java
public String getTrackingSummary() {
    String code = getTrackingCode();

    // 첫 번째 "-" 위치를 찾고 TYPE 추출
    int firstDash = code.indexOf("-");
    String type = code.substring(0, firstDash);
    String rest1 = code.substring(firstDash + 1);  // "REGION-DATE-SEQ"

    // 두 번째 "-": rest1에서 첫 번째 "-"가 곧 두 번째 "-"
    int secondDashInRest1 = rest1.indexOf("-");
    String region = rest1.substring(0, secondDashInRest1);
    String rest2 = rest1.substring(secondDashInRest1 + 1);  // "DATE-SEQ"

    // 세 번째 "-": rest2에서 첫 번째 "-"
    int thirdDashInRest2 = rest2.indexOf("-");
    String date = rest2.substring(0, thirdDashInRest2);
    String seq = rest2.substring(thirdDashInRest2 + 1);

    String typeLabel;
    if (type.equals("EXP")) {
        typeLabel = "Express";
    } else if (type.equals("STD")) {
        typeLabel = "Standard";
    } else {
        typeLabel = type;
    }

    return seq + " (" + region + ") - " + typeLabel + " delivery on " + date;
}
```

### Q1 채점 기준 (7점)

#### Part A (4점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 1 | `getDistanceKm()`에 따라 4단계 기본 요금 분기 (<=10: 3000, <=50: 5000, <=200: 8000, >200: 8000+50*(d-200)) *(algorithm)* | 경계값 처리(`<=` vs `<`) 틀리면 earn 불가. 200 초과 시 추가분 계산에서 `-200` 누락 시 earn 불가 | 1점 |
| 2 | `getWeightKg() > 20.0`일 때 `2000 * (int)(weightKg - 20.0)` 할증 계산 *(algorithm)* | `(int)` 캐스팅(절삭)이 핵심. 반올림이나 올림 사용 시 earn 불가. 20.0 이하일 때 할증 없는 조건 필요 | 1점 |
| 3 | `getIsExpress()`일 때 (base + surcharge)에 1.5를 곱함 *(algorithm)* | base에만 1.5를 곱하고 surcharge에는 안 곱하면 earn 불가 (전체에 곱해야 함) | 1점 |
| 4 | 올바른 순서: base → surcharge → 합산 → express 곱셈 → 반환 *(algorithm)* | express 곱셈을 surcharge 전에 적용하면 결과 다름 → earn 불가. 반환 누락 시 earn 불가 | 1점 |

**Can still earn:** 헬퍼 메서드 대신 인스턴스 변수 직접 접근해도 알고리즘 포인트는 earn 가능.
**Will not earn:** base fee 분기를 아예 하지 않으면 포인트 1을 earn 불가.

#### Part B (3점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 5 | 1-인자 `indexOf("-")` + `substring`을 반복적으로 사용하여 4개 부분(TYPE, REGION, DATE, SEQ)을 순차 추출 *(algorithm)* | `substring`과 1-인자 `indexOf`만으로 (Quick Reference 한도) 4개 토큰을 분리해야 함. 하드코딩 인덱스는 earn 불가 | 1점 |
| 6 | TYPE이 "EXP"이면 "Express", "STD"이면 "Standard", 그 외는 원래 값으로 변환 — `equals()`로 비교 *(algorithm)* | `==`로 문자열 비교 시 earn 불가. 변환 로직이 없으면 earn 불가 | 1점 |
| 7 | 올바른 형식의 요약 문자열 조합 — `"SEQ (REGION) - TYPE delivery on DATE"` | 괄호, 대시, 공백 등 형식이 크게 어긋나면 earn 불가. 사소한 공백 오류는 의도 명확하면 earn 가능 | 1점 |

**Can still earn:** Part A의 `getDeliveryFee()`가 틀려도 Part B 점수는 독립적으로 earn 가능.
**Will not earn:** String 메서드(`substring`, `indexOf`, `equals`)를 전혀 사용하지 않으면 포인트 5, 6을 earn 불가.

> 참고: `lastIndexOf` 및 2-인자 `indexOf(String, int)` 오버로드는 AP CSA Java Quick Reference에 포함되지 않습니다. 정답 코드는 1-인자 `indexOf` + `substring` 조합만 사용합니다 (`split("-")` 사용도 허용 — Quick Reference에 있음).

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
- base fee 경계값에서 `<=` 대신 `<` 사용
- 200km 초과 시 추가분에서 `getDistanceKm() - 200` 대신 `getDistanceKm()` 사용
- `(int)` 캐스팅 누락하여 소수 무게가 그대로 할증에 반영됨
- express 곱셈을 surcharge 추가 전에 적용
- 두 번째/세 번째 대시 위치를 찾을 때 원본 문자열 `code`에서 `indexOf("-")`만 반복 호출하여 매번 첫 번째 대시(인덱스 동일)만 찾음 → 남은 부분문자열(`rest1`, `rest2`)에서 다시 `indexOf("-")` 호출 필요
- `type.equals("EXP")` 대신 `type == "EXP"` 사용 (문자열 비교는 `equals`)
- `substring(dashIndex)` 대신 `substring(dashIndex + 1)` 필요 (대시 자체 제외)

---

## Question 2: Class Design (7점)
### 시나리오: 피트니스 트래커 (FitnessTracker)

사용자의 일일 운동 기록을 관리하는 `FitnessTracker` 클래스를 설계하세요.

```java
/**
 * 피트니스 트래커는 사용자의 운동 기록을 관리합니다.
 *
 * 생성자:
 *   FitnessTracker(String userName, int dailyGoal)
 *     - userName: 사용자 이름
 *     - dailyGoal: 일일 목표 칼로리 (양수)
 *
 * 메서드:
 *   void addWorkout(String type, int calories)
 *     - 운동 유형과 소모 칼로리를 기록합니다.
 *     - calories가 0 이하이면 기록하지 않습니다.
 *     - 운동 횟수(workoutCount)를 1 증가시킵니다.
 *     - 총 소모 칼로리(totalCalories)를 누적합니다.
 *
 *   boolean isGoalMet()
 *     - 총 소모 칼로리가 일일 목표 이상이면 true 반환
 *
 *   String getSummary()
 *     - 형식: "userName: totalCalories/dailyGoal cal (workoutCount workouts)"
 *     - 예: "Alice: 350/500 cal (3 workouts)"
 *
 *   int getCaloriesRemaining()
 *     - 목표까지 남은 칼로리 반환
 *     - 이미 목표 달성 시 0 반환
 */
```

**실행 예시 (Execution Table):**

| Statement / Expression | Return Value | Comment |
|----------------------|-------------|---------|
| `FitnessTracker ft = new FitnessTracker("Alice", 500);` | | 목표 500cal 트래커 생성 |
| `ft.addWorkout("Running", 200)` | | 200cal 기록 |
| `ft.addWorkout("Swimming", 150)` | | 150cal 기록 (누적 350) |
| `ft.getSummary()` | `"Alice: 350/500 cal (2 workouts)"` | 현재 상태 요약 |
| `ft.isGoalMet()` | `false` | 350 < 500 |
| `ft.getCaloriesRemaining()` | `150` | 500 - 350 = 150 |
| `ft.addWorkout("Cycling", -10)` | | 무시됨 (calories <= 0) |
| `ft.addWorkout("Yoga", 200)` | | 200cal 기록 (누적 550) |
| `ft.isGoalMet()` | `true` | 550 >= 500 |
| `ft.getCaloriesRemaining()` | `0` | 이미 목표 달성, 음수 대신 0 |
| `ft.getSummary()` | `"Alice: 550/500 cal (3 workouts)"` | Cycling은 미기록 |

아래 코드가 올바르게 동작하도록 `FitnessTracker` 클래스를 작성하세요.

### 정답 코드

```java
public class FitnessTracker {
    private String userName;
    private int dailyGoal;
    private int totalCalories;
    private int workoutCount;

    public FitnessTracker(String userName, int dailyGoal) {
        this.userName = userName;
        this.dailyGoal = dailyGoal;
        this.totalCalories = 0;
        this.workoutCount = 0;
    }

    public void addWorkout(String type, int calories) {
        if (calories > 0) {
            totalCalories += calories;
            workoutCount++;
        }
    }

    public boolean isGoalMet() {
        return totalCalories >= dailyGoal;
    }

    public String getSummary() {
        return userName + ": " + totalCalories + "/" + dailyGoal
               + " cal (" + workoutCount + " workouts)";
    }

    public int getCaloriesRemaining() {
        int remaining = dailyGoal - totalCalories;
        if (remaining < 0) {
            return 0;
        }
        return remaining;
    }
}
```

### Q2 채점 기준 (7점)

| # | 알고리즘 포인트 | 채점 기준 | Decision Rules | 배점 |
|---|--------------|---------|---------------|------|
| 1 | **Instance Variables** | `private` 인스턴스 변수 4개 (userName, dailyGoal, totalCalories, workoutCount) | `public` 선언 시 earn 불가. 타입 오류 시 earn 불가 | 1점 |
| 2 | **Constructor** | 생성자: `userName`, `dailyGoal` 매개변수 할당 + `totalCalories`/`workoutCount`를 0으로 초기화 | Java int 자동 초기화에 의존해도 earn 가능 | 1점 |
| 3 | **Mutator — guard** | `addWorkout`: `calories > 0` 검증 (0 이하면 무시) | 검증 없이 항상 누적하면 earn 불가 | 1점 |
| 4 | **Mutator — update** | `addWorkout`: `totalCalories += calories` + `workoutCount++` | 둘 중 하나 누락 시 earn 불가. `type` 매개변수 미사용은 정상 | 1점 |
| 5 | **Boolean Method** | `isGoalMet`: `totalCalories >= dailyGoal` 비교 + boolean 반환 | `>` 사용 시 earn 불가 (정확히 같을 때도 목표 달성) | 1점 |
| 6 | **toString-style** | `getSummary`: `"userName: totalCalories/dailyGoal cal (workoutCount workouts)"` 형식 | 공백/슬래시/괄호 등 형식 오류 시에도 의도 명확하면 earn 가능 | 1점 |
| 7 | **Computed Value** | `getCaloriesRemaining`: `dailyGoal - totalCalories` 계산 + 음수일 때 0 반환 | `if (remaining < 0) return 0;` 또는 동등한 조건문으로 처리. 음수 방지 누락 시 earn 불가 | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)
- `this.` 사용 여부는 채점에 영향 없음

### 흔한 실수
- 인스턴스 변수를 `public`으로 선언 → 캡슐화 위반 (감점)
- `totalCalories`와 `workoutCount` 초기화 누락 (Java는 int를 0으로 자동 초기화하지만, 명시적 초기화 권장)
- `addWorkout`에서 `type` 매개변수를 사용하지 않아도 괜찮음 (문제 요구사항에 저장하라는 말 없음)
- `getCaloriesRemaining`에서 음수 반환 → `if (remaining < 0) return 0;` 조건문으로 처리 (참고: AP CSA Quick Reference의 `Math` 메서드는 `abs`, `pow`, `sqrt`, `random`만 포함 — `Math.max`/`Math.min`은 범위 외)
- `getSummary` 형식 오류 (공백, 슬래시 위치 등)

### 부분점수 팁
- 클래스 선언 + private 변수만 있어도 1점
- 생성자가 올바르면 +1점
- 각 메서드가 독립적으로 채점됨 → 하나가 틀려도 나머지 정상이면 점수 확보

---

## Question 3: ArrayList (5점)
### 시나리오: 수강 관리 (StudentRoster)

학교의 수강 명단을 관리하는 시스템에서, 수강 인원 제한을 초과한 학생을 대기 목록으로 이동시키는 기능을 구현합니다.

```java
public class Enrollment {
    /** 학생 이름을 반환합니다. */
    public String getStudentName()
    { /* implementation not shown */ }

    /** 수강 과목명을 반환합니다. */
    public String getCourseName()
    { /* implementation not shown */ }

    /** 수강 신청 순번을 반환합니다 (낮을수록 먼저 신청). */
    public int getPriority()
    { /* implementation not shown */ }
}
```

```java
import java.util.ArrayList;

public class StudentRoster {
    private ArrayList<Enrollment> enrollments;

    public StudentRoster(ArrayList<Enrollment> enrollments) {
        this.enrollments = enrollments;
    }

    /**
     * 지정된 과목(courseName)의 수강 인원이 maxCapacity를 초과하는 경우,
     * 해당 과목에서 순번(getPriority())이 가장 높은(값이 큰) 학생들을
     * enrollments에서 제거하여 초과 인원을 해소합니다.
     *
     * 제거된 학생의 이름을 담은 ArrayList<String>을 반환합니다.
     *
     * 동작 방식:
     * 1. 해당 과목의 수강생 수를 센다.
     * 2. 수강생 수가 maxCapacity 이하이면 빈 리스트를 반환한다.
     * 3. 수강생 수가 maxCapacity보다 크면, 해당 과목 수강생 중
     *    getPriority()가 가장 큰 학생을 enrollments에서 제거하고
     *    이름을 결과 리스트에 추가한다.
     * 4. 수강생 수가 maxCapacity 이하가 될 때까지 3을 반복한다.
     *
     * 같은 priority를 가진 학생이 여러 명이면 enrollments에서
     * 먼저 나타나는 학생을 제거합니다.
     *
     * Precondition: maxCapacity > 0
     *               courseName은 null이 아님
     * Postcondition: enrollments는 수정됨
     *
     * @param courseName 과목명
     * @param maxCapacity 최대 수강 인원
     * @return 제거된 학생 이름 리스트
     */
    public ArrayList<String> trimExcess(String courseName, int maxCapacity) {
        /* 여기에 구현 */
    }
}
```

`trimExcess` 메서드를 구현하세요.

**예시:**

`enrollments`가 다음과 같을 때:

| 학생 이름 | 과목 | 순번 |
|----------|------|------|
| "Kim" | "Math" | 1 |
| "Lee" | "Math" | 3 |
| "Park" | "Science" | 2 |
| "Choi" | "Math" | 5 |
| "Jung" | "Math" | 2 |

`trimExcess("Math", 2)` 호출 후:
- Math 수강생 4명 → maxCapacity 2 → 2명 제거 필요
- priority 가장 높은 순: Choi(5) 제거 → Lee(3) 제거
- 반환값: `["Choi", "Lee"]`
- `enrollments`에 남은 항목: Kim(Math,1), Park(Science,2), Jung(Math,2)

---

### 정답 코드

```java
public ArrayList<String> trimExcess(String courseName, int maxCapacity) {
    ArrayList<String> removed = new ArrayList<String>();

    // 해당 과목 수강생 수 세기
    int count = 0;
    for (Enrollment e : enrollments) {
        if (e.getCourseName().equals(courseName)) {
            count++;
        }
    }

    // 초과 인원만큼 반복 제거
    while (count > maxCapacity) {
        // 해당 과목에서 priority가 가장 큰 학생의 인덱스 찾기
        int maxPriority = -1;
        int maxIndex = -1;
        for (int i = 0; i < enrollments.size(); i++) {
            Enrollment e = enrollments.get(i);
            if (e.getCourseName().equals(courseName)) {
                if (e.getPriority() > maxPriority) {
                    maxPriority = e.getPriority();
                    maxIndex = i;
                }
            }
        }

        removed.add(enrollments.get(maxIndex).getStudentName());
        enrollments.remove(maxIndex);
        count--;
    }

    return removed;
}
```

### Q3 채점 기준 (5점)

| # | 알고리즘 포인트 | 채점 기준 | Decision Rules | 배점 |
|---|--------------|---------|---------------|------|
| 1 | **Initialize** | `ArrayList<String>` 결과 리스트 생성 + 해당 과목 수강생 수 카운트 | `getCourseName().equals(courseName)`로 비교 필수. `==` 사용 시 earn 불가 | 1점 |
| 2 | **Outer Loop** | `count > maxCapacity`인 동안 반복하는 구조 | 초과 인원 없을 때 즉시 빈 리스트 반환도 가능. 고정 횟수 반복도 올바르면 earn 가능 | 1점 |
| 3 | **Find Max** | 해당 과목 수강생 중 `getPriority()` 최대인 학생의 인덱스 찾기 | `>=` 사용 시 동점에서 뒤쪽 학생 제거 → earn 불가 (앞쪽 제거 요구). 과목 필터 없이 전체에서 찾으면 earn 불가 | 1점 |
| 4 | **Remove** | 최대 priority 학생을 `enrollments`에서 제거 + 학생 이름을 결과 리스트에 추가 | `Enrollment` 객체를 추가하면 타입 불일치로 earn 불가. 제거 후 count 감소 필요 | 1점 |
| 5 | **Return** | 결과 리스트 반환 | 반환 누락 시 earn 불가 | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)

### 흔한 실수
- `getCourseName()` 비교 시 `==` 사용 → `equals()` 필요
- 최대 priority 찾기에서 과목 필터링을 빠뜨려 다른 과목 학생을 제거
- `getPriority()` 비교 시 `>=` 사용 → 동점에서 뒤쪽 학생을 먼저 제거 (앞쪽 우선 요구)
- 제거 후 count를 감소시키지 않아 무한 루프
- 결과 리스트에 `getStudentName()` 대신 `Enrollment` 객체 추가 (타입 불일치)

---

## Question 4: 2D Array (6점)
### 시나리오: 고도 지도 — 하강 경로 탐색 (Elevation Map — River Path Detection)

지형의 고도 데이터를 2D 배열로 관리합니다. `TerrainAnalyzer` 클래스의 일부가 아래에 나와 있습니다.

```java
public class TerrainAnalyzer {

    /** 지형 셀 하나의 정보를 나타냅니다. */
    public class TerrainCell {
        /** 지형 유형을 반환합니다. 예: "grass", "rock", "water" */
        public String getType()
        { /* implementation not shown */ }

        /** 이 셀의 경사도를 반환합니다. */
        public double getSlope()
        { /* implementation not shown */ }
    }

    /** elevation[r][c]는 행 r, 열 c 위치의 고도(정수, 미터)를 나타냅니다.
     *  Precondition: elevation은 최소 1행 1열의 직사각형 배열이다.
     */
    private int[][] elevation;

    /** cells[r][c]는 해당 위치의 TerrainCell 객체입니다.
     *  Precondition: cells의 크기는 elevation과 동일하다.
     */
    private TerrainCell[][] cells;

    /** 주어진 시작 셀에서 오른쪽(RIGHT) 또는 아래쪽(DOWN)으로만 이동하면서,
     *  고도가 **엄격하게 감소(strictly lower)**하는 연속 이동의 최대 횟수를 반환합니다.
     *
     *  이동 규칙:
     *  - 현재 위치에서 오른쪽(같은 행, 열+1)과 아래쪽(행+1, 같은 열)을
     *    후보로 검토합니다.
     *  - 후보 셀의 고도가 현재 셀의 고도보다 엄격하게 작아야 이동 가능합니다.
     *  - 두 방향 모두 이동 가능하면, 고도가 더 낮은 쪽으로 이동합니다.
     *  - 두 방향의 고도가 같으면, 오른쪽을 우선합니다.
     *  - 이동 가능한 방향이 없으면 (배열 경계 밖이거나 고도가 감소하지 않으면)
     *    탐색을 종료합니다.
     *
     *  Precondition: 0 <= startRow < elevation.length,
     *                0 <= startCol < elevation[0].length
     */
    public int longestDescentPath(int startRow, int startCol) {
        /* 여기에 구현 */
    }
}
```

`longestDescentPath` 메서드를 구현하세요.

**예시:**

`elevation`이 다음과 같을 때:

```
        Col 0   Col 1   Col 2   Col 3
Row 0 |  90   |  80   |  70   |  65   |
Row 1 |  85   |  75   |  60   |  55   |
Row 2 |  80   |  70   |  50   |  40   |
Row 3 |  78   |  72   |  68   |  35   |
```

`longestDescentPath(0, 0)` 호출 시:
- (0,0)=90: 오른쪽(0,1)=80, 아래(1,0)=85. 둘 다 < 90. 80 < 85 → 오른쪽으로 이동. step=1
- (0,1)=80: 오른쪽(0,2)=70, 아래(1,1)=75. 둘 다 < 80. 70 < 75 → 오른쪽으로 이동. step=2
- (0,2)=70: 오른쪽(0,3)=65, 아래(1,2)=60. 둘 다 < 70. 60 < 65 → 아래로 이동. step=3
- (1,2)=60: 오른쪽(1,3)=55, 아래(2,2)=50. 둘 다 < 60. 50 < 55 → 아래로 이동. step=4
- (2,2)=50: 오른쪽(2,3)=40, 아래(3,2)=68. 68 < 50이 거짓 → 아래로 이동 불가 (현재 값 50보다 크므로 내리막이 아님). 오른쪽 40 < 50 → 오른쪽으로 이동. step=5
- (2,3)=40: 오른쪽 없음(경계 밖), 아래(3,3)=35. 35 < 40 → 아래로 이동. step=6
- (3,3)=35: 오른쪽 없음, 아래 없음 → 종료.

반환값: **6**

`longestDescentPath(3, 0)` 호출 시:
- (3,0)=78: 오른쪽(3,1)=72. 72 < 78 → 이동 가능. 아래 없음(경계 밖). 오른쪽으로 이동. step=1
- (3,1)=72: 오른쪽(3,2)=68. 68 < 72 → 이동. step=2
- (3,2)=68: 오른쪽(3,3)=35. 35 < 68 → 이동. step=3
- (3,3)=35: 종료. 반환값: **3**

---

### Q4 정답 코드

```java
public int longestDescentPath(int startRow, int startCol) {
    int steps = 0;
    int r = startRow;
    int c = startCol;
    boolean moving = true;

    while (moving) {
        int current = elevation[r][c];

        boolean canRight = (c + 1 < elevation[0].length)
                           && (elevation[r][c + 1] < current);
        boolean canDown  = (r + 1 < elevation.length)
                           && (elevation[r + 1][c] < current);

        if (!canRight && !canDown) {
            moving = false;
        } else {
            if (canRight && canDown) {
                if (elevation[r + 1][c] < elevation[r][c + 1]) {
                    r++;
                } else {
                    c++;
                }
            } else if (canRight) {
                c++;
            } else {
                r++;
            }
            steps++;
        }
    }

    return steps;
}
```

### Q4 채점 기준 (6점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 1 | 현재 위치를 추적하는 변수 초기화 (`r = startRow`, `c = startCol`) + step 카운터 초기화 *(algorithm)* | 시작 위치를 (0,0)으로 하드코딩하면 earn 불가 | 1점 |
| 2 | 오른쪽 이동 가능 여부 판정: `c + 1 < elevation[0].length` (경계 검사) AND `elevation[r][c+1] < current` (엄격 감소) *(algorithm)* | 경계 검사 누락 시 `ArrayIndexOutOfBoundsException` → earn 불가. `<=` 대신 `<` 필요 | 1점 |
| 3 | 아래쪽 이동 가능 여부 판정: `r + 1 < elevation.length` (경계 검사) AND `elevation[r+1][c] < current` (엄격 감소) *(algorithm)* | 행/열 인덱스 혼동 시 earn 불가 | 1점 |
| 4 | 두 방향 모두 가능할 때 고도가 더 낮은 쪽 선택 + 동점 시 오른쪽 우선 *(algorithm)* | 항상 한 방향만 선택하면 earn 불가. 동점 처리 오류 시에도 earn 불가 | 1점 |
| 5 | 이동 불가 시(두 방향 모두 불가) 루프 종료 *(algorithm)* | 종료 조건 없으면 무한루프 → earn 불가. 한 방향만 가능할 때 올바르게 이동해야 함 | 1점 |
| 6 | 이동할 때마다 step 증가 + 최종 step 수 반환 | 반환 누락 시 earn 불가. 시작 셀을 1로 세면 off-by-one → earn 불가 | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)
- `while(true) + break` 대신 `while(canMove)` 패턴 사용도 동일 점수

### 흔한 실수
- 경계 검사를 하지 않아 배열 밖 접근 (`ArrayIndexOutOfBoundsException`)
- 엄격 감소 조건에서 `<=` 사용 → 같은 고도로도 이동 가능해짐 (문제는 strictly lower 요구)
- 두 방향 모두 가능할 때 비교 없이 항상 오른쪽(또는 항상 아래)만 선택
- 동점 시 오른쪽 우선 규칙을 무시하고 아래로 이동
- 시작 셀 자체를 1 step으로 카운트하여 off-by-one 오류
- 이동 후 `current` 값을 갱신하지 않음 (루프 시작에서 `elevation[r][c]`를 다시 읽어야 함)
- `r`과 `c`를 동시에 증가시킴 (대각선 이동은 허용되지 않음)

---

## 전체 FRQ 요약

| 문제 | 유형 | 배점 | 핵심 토픽 |
|------|------|------|-----------|
| Q1 | Methods + String | 7점 | String 메서드, 문자 판별, substring 경계 처리 |
| Q2 | Class Design | 7점 | 캡슐화, 생성자, 조건 검증, 문자열 형식화 |
| Q3 | ArrayList | 5점 | ArrayList 순회, 필터링, 안전한 제거 패턴 |
| Q4 | 2D Array | 6점 | 순차 경로 탐색, 경계 검사, 방향 선택 (greedy descent) |
| | **합계** | **25점** | |
