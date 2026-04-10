# AP Computer Science A — 모의시험 3세트 Section II: Free Response
## 4 Questions | 90 Minutes

---

## Question 1: Methods and Control Structures (7점)

### 시나리오: 기상 경보 시스템 (WeatherAlert)

한 기상청에서 기온 측정값을 분석하고 경보 메시지를 생성하는 시스템을 관리합니다. `WeatherAlert` 클래스의 일부가 아래에 나와 있습니다.

```java
public class WeatherAlert {
    private double[] readings;    // 시간별 기온 측정값 (섭씨)
    private String stationId;     // 관측소 ID (예: "KR-SEL-042")
    private boolean isCoastal;    // 해안 관측소 여부

    /** Returns the array of temperature readings.
     *  Precondition: readings has at least one element.
     */
    public double[] getReadings()
    { /* implementation not shown */ }

    /** Returns the station ID string.
     */
    public String getStationId()
    { /* implementation not shown */ }

    /** Returns true if this is a coastal station.
     */
    public boolean getIsCoastal()
    { /* implementation not shown */ }

    /** Returns the number of readings in the array.
     */
    public int getNumReadings()
    { /* implementation not shown */ }

    /** Returns the temperature reading at the given index.
     *  Precondition: 0 <= idx < getNumReadings()
     */
    public double getReading(int idx)
    { /* implementation not shown */ }

    /** Determines the alert level based on the temperature readings.
     *
     *  The method computes the average of all readings and finds the
     *  maximum reading.
     *
     *  Alert level rules (checked in this order):
     *  - If the maximum reading >= 40.0 AND the average >= 35.0:
     *    return "RED"
     *  - If the maximum reading >= 35.0 OR (isCoastal AND average >= 30.0):
     *    return "ORANGE"
     *  - If the average >= 28.0:
     *    return "YELLOW"
     *  - Otherwise: return "GREEN"
     *
     *  Precondition: readings has at least one element.
     */
    public String getAlertLevel()
    { /* to be implemented in Part A */ }

    /** Builds and returns an alert message string.
     *
     *  The message has the format:
     *    "Station REGION-CODE: LEVEL alert (N readings)"
     *
     *  Where REGION is extracted from stationId as the characters before the
     *  first "-", CODE is extracted as the characters after the last "-",
     *  LEVEL is the result of getAlertLevel(), and N is getNumReadings().
     *
     *  Examples:
     *    stationId "KR-SEL-042", alert "RED", 24 readings
     *      → "Station KR-042: RED alert (24 readings)"
     *    stationId "US-NYC-007", alert "GREEN", 12 readings
     *      → "Station US-007: GREEN alert (12 readings)"
     *
     *  Precondition: stationId contains at least two "-" characters.
     */
    public String buildAlertMessage()
    { /* to be implemented in Part B */ }
}
```

**예시:**

| readings | stationId | isCoastal | getAlertLevel() | buildAlertMessage() |
|----------|-----------|-----------|-----------------|---------------------|
| {38.0, 41.0, 36.5} | "KR-SEL-042" | false | "RED" | "Station KR-042: RED alert (3 readings)" |
| {30.0, 31.0, 29.0} | "US-MIA-003" | true | "ORANGE" | "Station US-003: ORANGE alert (3 readings)" |
| {25.0, 27.0, 26.0} | "JP-TKY-101" | false | "GREEN" | "Station JP-101: GREEN alert (3 readings)" |

*참고: 첫 행 → 평균 38.5, 최대 41.0 → RED. 둘째 행 → 평균 30.0, 최대 31.0, 해안+평균>=30 → ORANGE. 셋째 행 → 평균 26.0, 최대 27.0 → GREEN.*

### Part A (4점)

`getAlertLevel` 메서드를 작성하세요.

### Part B (3점)

`buildAlertMessage` 메서드를 작성하세요.

---

### Q1 정답 코드

#### Part A (4점)

```java
public String getAlertLevel() {
    double sum = 0;
    double max = getReading(0);

    for (int i = 0; i < getNumReadings(); i++) {
        double temp = getReading(i);
        sum += temp;
        if (temp > max) {
            max = temp;
        }
    }

    double avg = sum / getNumReadings();

    if (max >= 40.0 && avg >= 35.0) {
        return "RED";
    }
    if (max >= 35.0 || (getIsCoastal() && avg >= 30.0)) {
        return "ORANGE";
    }
    if (avg >= 28.0) {
        return "YELLOW";
    }
    return "GREEN";
}
```

#### Part B (3점)

```java
public String buildAlertMessage() {
    String id = getStationId();
    int firstDash = id.indexOf("-");
    int lastDash = id.lastIndexOf("-");

    String region = id.substring(0, firstDash);
    String code = id.substring(lastDash + 1);

    return "Station " + region + "-" + code + ": "
         + getAlertLevel() + " alert (" + getNumReadings() + " readings)";
}
```

### Q1 채점 기준 (7점)

#### Part A (4점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 1 | `getNumReadings()`와 `getReading(i)`를 사용하여 루프로 readings를 순회하며 합계(sum)를 구함 + 평균 계산 *(algorithm)* | `getReadings()`로 배열 직접 접근해도 earn 가능. 합계를 구하지 않으면 earn 불가 | 1점 |
| 2 | 루프 내에서 최댓값(max)을 올바르게 추적 *(algorithm)* | max 초기값을 첫 번째 원소로 설정하거나 적절한 최솟값으로 해도 가능. 초기값 0은 모든 기온이 음수일 때 틀림 → earn 불가 | 1점 |
| 3 | RED 조건 (`max >= 40.0 && avg >= 35.0`)과 ORANGE 조건 (`max >= 35.0 \|\| (isCoastal && avg >= 30.0)`)을 올바르게 구현 *(algorithm)* | `&&`와 `\|\|` 혼동 시 earn 불가. ORANGE 조건의 복합 논리가 올바르지 않으면 earn 불가 | 1점 |
| 4 | 올바른 우선순위 (RED → ORANGE → YELLOW → GREEN) + GREEN 기본 반환 *(algorithm)* | 우선순위가 뒤바뀌면 earn 불가. GREEN 반환 누락 시 earn 불가 | 1점 |

**Can still earn:** 헬퍼 메서드 대신 `getReadings()` 배열에 직접 접근해도 알고리즘 포인트는 earn 가능.
**Will not earn:** 평균이나 최댓값을 아예 계산하지 않으면 포인트 1, 2를 earn 불가.

#### Part B (3점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 5 | `indexOf("-")`로 첫 번째 대시 위치를 찾고 `substring(0, firstDash)`로 REGION 추출 *(algorithm)* | `indexOf` 또는 `substring`을 사용해야 함. 하드코딩(예: `substring(0, 2)`)은 일반적이지 않으므로 earn 불가 | 1점 |
| 6 | `lastIndexOf("-")`로 마지막 대시 위치를 찾고 `substring(lastDash + 1)`로 CODE 추출 *(algorithm)* | `lastIndexOf` 사용이 핵심. `indexOf`만으로 마지막 대시를 찾으려면 별도 로직 필요 — 올바르면 earn 가능 | 1점 |
| 7 | 올바른 형식의 메시지 문자열 조합 — `"Station REGION-CODE: LEVEL alert (N readings)"` | `getAlertLevel()` 및 `getNumReadings()` 호출 포함. 형식이 크게 어긋나면 earn 불가 | 1점 |

**Can still earn:** Part A의 `getAlertLevel()`가 틀려도 Part B에서 호출 로직이 올바르면 Part B 점수는 독립적으로 earn 가능.
**Will not earn:** String 메서드(`substring`, `indexOf`, `lastIndexOf`)를 전혀 사용하지 않으면 포인트 5, 6을 earn 불가.

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)
- `else if` 대신 독립 `if`문을 사용했지만 로직이 동일하면

### Q1 흔한 실수
- max 초기값을 0으로 설정 → 모든 기온이 음수일 때 잘못된 최댓값
- 평균 계산에서 정수 나눗셈 발생 (`sum`과 `getNumReadings()` 모두 int인 경우)
- RED와 ORANGE 조건에서 `&&`와 `||` 혼동
- ORANGE 조건에서 `isCoastal && avg >= 30.0` 부분을 괄호로 묶지 않아 연산자 우선순위 오류
- `lastIndexOf("-")` 대신 `indexOf("-")`만 사용하여 중간 대시를 마지막으로 잘못 인식
- `substring(lastDash)` 대신 `substring(lastDash + 1)` 필요 (대시 자체는 제외)

---

## Question 2: Class Design (7점)

### 시나리오: 주차 미터기 (ParkingMeter)

주차장의 주차 미터기를 관리하는 `ParkingMeter` 클래스를 설계합니다. 각 미터기는 시간당 요금과 남은 시간을 추적합니다.

다음 요구사항에 따라 `ParkingMeter` 클래스를 **완전히** 작성하세요.

| 항목 | 설명 |
|------|------|
| `meterID` | 미터기 고유 번호 (`String`). 생성 시 설정되며 변경 불가. |
| `ratePerHour` | 시간당 요금 (`double`). 생성 시 설정되며 변경 불가. |
| `minutesRemaining` | 남은 주차 시간 (분, `int`). 생성 시 `0`. |
| `totalCollected` | 누적 수금액 (`double`). 생성 시 `0.0`. |
| `ParkingMeter(String meterID, double ratePerHour)` | 생성자. 미터기 번호와 시간당 요금을 설정. Precondition: `ratePerHour > 0` |
| `getMeterID()` | 미터기 번호를 반환. |
| `getMinutesRemaining()` | 남은 시간(분)을 반환. |
| `isExpired()` | 남은 시간이 0 이하이면 `true` 반환. |
| `addTime(int minutes)` | 동전 투입. 분 단위 시간을 추가하고, `totalCollected`에 `ratePerHour * minutes / 60.0`을 더함. Precondition: `minutes > 0` |
| `tick(int minutes)` | 시간 경과. 남은 시간에서 `minutes`를 뺌. 남은 시간이 음수가 되면 0으로 설정. Precondition: `minutes > 0` |
| `toString()` | `"Meter [meterID]: [minutesRemaining] min remaining ($[totalCollected] collected)"` 형식 반환. |

**실행 예시 (Execution Table):**

| Statement / Expression | Return Value | Comment |
|----------------------|-------------|---------|
| `ParkingMeter pm = new ParkingMeter("A-101", 2.00);` | | 미터기 생성 (시간당 $2.00) |
| `pm.getMeterID()` | `"A-101"` | 미터기 번호 |
| `pm.isExpired()` | `true` | 남은 시간 0분 |
| `pm.addTime(60)` | | 60분 추가 ($2.00 수금) |
| `pm.getMinutesRemaining()` | `60` | 60분 남음 |
| `pm.isExpired()` | `false` | 아직 시간 남음 |
| `pm.addTime(30)` | | 30분 추가 ($1.00 수금) |
| `pm.getMinutesRemaining()` | `90` | 90분 남음 |
| `pm.tick(100)` | | 100분 경과 → 남은 시간 0 (음수 방지) |
| `pm.isExpired()` | `true` | 시간 만료 |
| `pm.getMinutesRemaining()` | `0` | 음수가 아닌 0 |
| `pm.toString()` | `"Meter A-101: 0 min remaining ($3.0 collected)"` | 현재 상태 출력 |

```java
public class ParkingMeter {
    /* 전체 클래스를 구현하시오 */
}
```

---

### Q2 정답 코드

```java
public class ParkingMeter {
    private String meterID;
    private double ratePerHour;
    private int minutesRemaining;
    private double totalCollected;

    public ParkingMeter(String meterID, double ratePerHour) {
        this.meterID = meterID;
        this.ratePerHour = ratePerHour;
        this.minutesRemaining = 0;
        this.totalCollected = 0.0;
    }

    public String getMeterID() {
        return meterID;
    }

    public int getMinutesRemaining() {
        return minutesRemaining;
    }

    public boolean isExpired() {
        return minutesRemaining <= 0;
    }

    public void addTime(int minutes) {
        minutesRemaining += minutes;
        totalCollected += ratePerHour * minutes / 60.0;
    }

    public void tick(int minutes) {
        minutesRemaining -= minutes;
        if (minutesRemaining < 0) {
            minutesRemaining = 0;
        }
    }

    public String toString() {
        return "Meter " + meterID + ": " + minutesRemaining
               + " min remaining ($" + totalCollected + " collected)";
    }
}
```

### Q2 채점 기준 (7점)

| # | 알고리즘 포인트 | 채점 기준 | Decision Rules | 배점 |
|---|--------------|---------|---------------|------|
| 1 | **Instance Variables** | 4개의 `private` 인스턴스 변수 선언 (`String`, `double`, `int`, `double`) | `public` 선언 시 earn 불가. 타입 하나라도 틀리면 earn 불가 | 1점 |
| 2 | **Constructor** | 생성자: 2개 매개변수 할당 + `minutesRemaining = 0`, `totalCollected = 0.0` 초기화 | 기본값 초기화 누락 시 earn 불가 | 1점 |
| 3 | **Accessor Methods** | `getMeterID()` + `getMinutesRemaining()` + `isExpired()` 올바르게 구현 | `isExpired`가 `minutesRemaining <= 0` 반환해야 함. 셋 중 하나라도 틀리면 earn 불가 | 1점 |
| 4 | **Mutator — addTime (time)** | `addTime`: `minutesRemaining += minutes` 올바르게 구현 | 덮어쓰기(`=`) 사용 시 earn 불가 | 1점 |
| 5 | **Mutator — addTime (revenue)** | `addTime`: `totalCollected += ratePerHour * minutes / 60.0` 계산 올바름 | `/ 60` (정수 나눗셈) 사용 시 earn 불가. `ratePerHour` 곱하기 누락 시 earn 불가 | 1점 |
| 6 | **Mutator — tick** | `tick`: `minutesRemaining -= minutes` + 음수 방지 (`< 0`이면 0으로 설정) | 음수 방지 누락 시 earn 불가. `Math.max(0, ...)` 또는 if문 모두 가능 | 1점 |
| 7 | **toString** | `toString`: 올바른 형식 문자열 반환 | 형식 오류 시에도 의도가 명확하면 earn 가능 | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)
- `this.` 사용 여부는 채점에 영향 없음

### Q2 흔한 실수
- 인스턴스 변수를 `public`으로 선언 (캡슐화 위반)
- `addTime`에서 수금액 계산 시 `/ 60` (정수 나눗셈) 사용 → `/ 60.0` 필요
- `tick`에서 음수 방지 누락 → 남은 시간이 음수가 됨
- `isExpired`에서 `< 0` 사용 → 정확히 0분일 때 만료로 판단 안 됨 (`<= 0` 필요)
- `addTime`에서 `minutesRemaining = minutes` (누적이 아닌 덮어쓰기)

---

## Question 3: ArrayList (5점)

### 시나리오: 메시지 필터 (MessageFilter)

메시지 목록에서 스팸 메시지를 탐지하고 제거하는 시스템입니다.

```java
public class Message {
    /** 발신자 이름을 반환합니다. */
    public String getSender()
    { /* implementation not shown */ }

    /** 메시지 본문을 반환합니다. */
    public String getBody()
    { /* implementation not shown */ }

    /** 메시지 본문의 단어 수를 반환합니다. */
    public int getWordCount()
    { /* implementation not shown */ }
}
```

```java
import java.util.ArrayList;

public class MessageFilter {
    private ArrayList<Message> messages;

    public MessageFilter(ArrayList<Message> messages) {
        this.messages = messages;
    }

    /**
     * 스팸으로 의심되는 메시지를 messages에서 제거하고,
     * 제거된 메시지의 발신자 이름을 담은 ArrayList<String>을 반환합니다.
     *
     * 스팸 판정 기준:
     * - 메시지 본문(getBody())에 keyword가 포함되어 있고 (indexOf 사용)
     * - 단어 수(getWordCount())가 maxWords보다 큰 경우
     *
     * 두 조건을 모두 만족하는 메시지만 스팸으로 판정합니다.
     * 반환 리스트의 순서는 messages에서의 원래 순서와 같아야 합니다.
     * 같은 발신자의 메시지가 여러 개 제거되면 이름이 중복될 수 있습니다.
     *
     * Precondition: keyword는 null이 아니고 빈 문자열이 아님
     *               maxWords > 0
     * Postcondition: messages는 수정됨 (스팸 메시지가 제거된 상태)
     *
     * @param keyword 스팸 키워드
     * @param maxWords 이 단어 수를 초과하면 스팸 의심
     * @return 제거된 메시지의 발신자 이름 리스트
     */
    public ArrayList<String> removeSpam(String keyword, int maxWords) {
        /* 여기에 구현 */
    }
}
```

`removeSpam` 메서드를 구현하세요.

**예시:**

`messages`가 다음과 같을 때:

| 발신자 | 본문 | 단어 수 |
|--------|------|---------|
| "Kim" | "Buy now! Special offer" | 4 |
| "Lee" | "Meeting at 3pm" | 3 |
| "Park" | "Buy this amazing product now" | 5 |
| "Kim" | "Buy something today" | 3 |

`removeSpam("Buy", 3)` 호출 후:
- 반환값: `["Kim", "Park"]` (첫 번째 "Kim": "Buy" 포함 + 단어 4 > 3, "Park": "Buy" 포함 + 단어 5 > 3)
- `messages`에 남은 항목: "Lee"의 메시지, "Kim"의 두 번째 메시지 (단어 3, 3 초과 아님)

---

### Q3 정답 코드

```java
public ArrayList<String> removeSpam(String keyword, int maxWords) {
    ArrayList<String> removed = new ArrayList<String>();
    int i = 0;
    while (i < messages.size()) {
        Message m = messages.get(i);
        if (m.getBody().indexOf(keyword) >= 0 && m.getWordCount() > maxWords) {
            removed.add(m.getSender());
            messages.remove(i);
        } else {
            i++;
        }
    }
    return removed;
}
```

### Q3 채점 기준 (5점)

| # | 알고리즘 포인트 | 채점 기준 | Decision Rules | 배점 |
|---|--------------|---------|---------------|------|
| 1 | **Initialize** | `ArrayList<String>` 결과 리스트 생성 | `new ArrayList<>()` 또는 `new ArrayList<String>()` 모두 가능 | 1점 |
| 2 | **Traverse** | `messages` 리스트를 올바르게 순회 | while 또는 역순 for 루프 필요. for-each + remove → `ConcurrentModificationException` → earn 불가 | 1점 |
| 3 | **Compare (keyword)** | `getBody().indexOf(keyword) >= 0`으로 키워드 포함 여부 판별 | `==`로 비교 시 earn 불가. `indexOf > 0` (0 제외) 시 earn 불가 | 1점 |
| 4 | **Compare (wordCount)** | `getWordCount() > maxWords` 조건 올바름 | `>=` 사용 시 earn 불가 ("초과"이므로 `>`) 두 조건을 AND로 결합해야 함 | 1점 |
| 5 | **Remove + Build Result** | 조건 충족 시 발신자명(`getSender()`)을 결과 리스트에 추가 + `messages`에서 제거 + 인덱스 관리 올바름 + 반환 | for 루프에서 remove 후 무조건 i++ → 건너뜀 → earn 불가. 반환 누락 시 earn 불가 | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)

### Q3 흔한 실수
- for 루프에서 `remove(i)` 후 무조건 `i++` → 인덱스 밀림으로 일부 메시지 건너뜀
- `indexOf(keyword) > 0` 사용 → 본문 맨 앞에 키워드가 있을 때 놓침 (`>= 0` 필요)
- `getWordCount() >= maxWords` 사용 → "초과"가 아닌 "이상"이 되어 경계값 오류
- 키워드 조건과 단어 수 조건을 OR로 결합 (문제는 AND 요구)
- `getSender()` 대신 `Message` 객체 자체를 결과 리스트에 추가 (타입 불일치)

---

## Question 4: 2D Array (6점)

### 시나리오: 강의실 시간표 (ClassSchedule)

대학교의 강의실 사용 현황을 2D 배열로 관리합니다. `ScheduleAnalyzer` 클래스의 일부가 아래에 나와 있습니다.

```java
public class ScheduleAnalyzer {

    /** 강의실 하나의 정보를 나타냅니다. */
    public class Room {
        /** 강의실 이름을 반환합니다. 예: "Room 101" */
        public String getName()
        { /* implementation not shown */ }

        /** 수용 인원을 반환합니다. */
        public int getCapacity()
        { /* implementation not shown */ }
    }

    /** schedule[r][c]는 강의실 r이 시간대 c에 사용 중인지를 나타냅니다.
     *  true이면 사용 중, false이면 비어 있음.
     *  Precondition: schedule는 최소 1행 1열의 직사각형 배열이다.
     */
    private boolean[][] schedule;

    /** rooms[r]은 강의실 r의 Room 객체입니다.
     *  Precondition: rooms.length == schedule.length
     */
    private Room[] rooms;

    /** schedule에서 비어 있는 강의실(false)이 가장 많은 시간대(열)의
     *  인덱스를 반환합니다.
     *  비어 있는 강의실 수가 같은 시간대가 여러 개 있으면,
     *  인덱스가 가장 작은 시간대를 반환합니다.
     *
     *  Precondition: schedule는 최소 1행 1열의 직사각형 배열이다.
     */
    public int timeSlotWithMostAvailable() {
        /* 여기에 구현 */
    }
}
```

`timeSlotWithMostAvailable` 메서드를 구현하세요.

**예시:**

`schedule`이 다음과 같을 때 (`T` = true/사용중, `F` = false/비어있음):

```
              9:00    10:00    11:00    12:00
Room 101  |   T   |   F   |   T   |   F   |
Room 102  |   F   |   F   |   T   |   F   |
Room 103  |   T   |   T   |   F   |   F   |
Room 104  |   F   |   F   |   F   |   T   |
```

- 9:00 (열 0): false 2개 (Room 102, 104)
- 10:00 (열 1): false 3개 (Room 101, 102, 104)
- 11:00 (열 2): false 2개 (Room 103, 104)
- 12:00 (열 3): false 3개 (Room 101, 102, 103)

10:00(열 1)과 12:00(열 3) 모두 3개로 동점 → 인덱스가 작은 **1** 을 반환합니다.

---

### Q4 정답 코드

```java
public int timeSlotWithMostAvailable() {
    int bestCol = 0;
    int bestCount = 0;

    for (int c = 0; c < schedule[0].length; c++) {
        int available = 0;

        for (int r = 0; r < schedule.length; r++) {
            if (!schedule[r][c]) {
                available++;
            }
        }

        if (available > bestCount) {
            bestCount = available;
            bestCol = c;
        }
    }

    return bestCol;
}
```

### Q4 채점 기준 (6점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 1 | 외부 루프로 각 열(c)을 순회 (`c < schedule[0].length`) | 행을 외부 루프로 잡으면 열별 집계가 불가 → earn 불가 | 1점 |
| 2 | 내부 루프로 각 행(r)을 순회 (`r < schedule.length`) | 행과 열 범위를 혼동하면 earn 불가 | 1점 |
| 3 | `!schedule[r][c]` (또는 `schedule[r][c] == false`)로 비어 있는 강의실 판별 *(algorithm)* | `schedule[r][c]`만 체크하면 사용 중인 것을 세게 됨 → earn 불가 | 1점 |
| 4 | 비어 있는 강의실 수를 올바르게 카운트 *(algorithm)* | 각 열 처리 시 카운트 초기화 필요. 누락 시 누적되어 earn 불가 | 1점 |
| 5 | 가장 많은 열의 인덱스 추적 (최댓값 갱신 로직) *(algorithm)* | `>=` 사용 시 동점에서 마지막 열 반환 → earn 불가 (`>` 필요) | 1점 |
| 6 | 최종 결과(열 인덱스) 반환 | 반환 누락 시 earn 불가. 카운트 값 대신 인덱스를 반환해야 함 | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)

### Q4 흔한 실수
- **행/열 혼동**: 열을 외부 루프로 잡아야 "시간대별" 집계가 가능 — 행을 외부로 잡으면 "강의실별" 집계가 됨
- `schedule[0].length` 대신 `schedule.length`를 열 수로 사용 → 행 수와 열 수 혼동
- `!schedule[r][c]` 대신 `schedule[r][c]`를 조건으로 사용 → 사용 중인 강의실을 세게 됨
- 각 열 처리 시 `available` 카운트를 0으로 초기화하지 않음 → 이전 열의 값이 누적됨
- 동점 처리: `>` 대신 `>=` 사용 → 마지막 열이 반환됨 (문제는 가장 작은 인덱스 요구)
- 결과로 카운트 값을 반환 (열 인덱스가 아닌 비어있는 수를 반환하는 실수)
