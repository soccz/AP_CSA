# AP Computer Science A — 모의시험 1세트 Section II: Free Response
## 4 Questions | 90 Minutes | 45% of Score

**지시사항:** Java Quick Reference가 제공됩니다. 코드는 Java로 작성하세요. 코드 외의 설명은 필요하지 않습니다.

---

## Question 1: Methods and Control Structures (7점)

한 온라인 쇼핑몰에서 주문 처리 시스템을 관리합니다. `OrderProcessor` 클래스는 `Catalog` 객체를 사용하여 주문 정보를 조회합니다. 클래스의 일부가 아래에 나와 있습니다.

```java
public class Catalog {
    /** Returns the total price of all items currently in the catalog order.
     */
    public double getSubtotal()
    { /* implementation not shown */ }

    /** Returns the number of items in the catalog order.
     */
    public int getItemCount()
    { /* implementation not shown */ }

    /** Returns the coupon code applied to this order.
     *  Returns "" if no coupon is applied.
     */
    public String getCouponCode()
    { /* implementation not shown */ }
}
```

```java
public class OrderProcessor {
    private Catalog catalog;       // 주문 카탈로그 객체
    private boolean isMember;      // 멤버십 회원 여부

    /** Returns true if the customer is a member.
     */
    public boolean getIsMember()
    { /* implementation not shown */ }

    /** Computes and returns the shipping cost for this order.
     *
     *  Shipping rules:
     *  - If the customer is a member AND catalog.getSubtotal() >= 30.0,
     *    shipping is free (0.0).
     *  - Otherwise, if catalog.getItemCount() <= 3, shipping is 5.99.
     *  - Otherwise, if catalog.getItemCount() <= 8, shipping is 9.99.
     *  - Otherwise (itemCount > 8), shipping is 9.99 + 1.50 for each item beyond 8.
     *
     *  Precondition: catalog.getSubtotal() >= 0.0, catalog.getItemCount() >= 1
     */
    public double getShippingCost()
    { /* to be implemented in Part A */ }

    /** Returns a summary string for the order receipt.
     *
     *  The summary has the format:
     *    "Items: N | Subtotal: $X.XX | Shipping: $Y.YY | Coupon: CODE"
     *
     *  Where N is catalog.getItemCount(), X.XX is catalog.getSubtotal(),
     *  and Y.YY is this.getShippingCost().
     *
     *  If catalog.getCouponCode() is "", the coupon portion should read "Coupon: NONE".
     *
     *  If couponCode starts with "PCT" followed by digits (e.g. "PCT15"),
     *  the digits represent a percent discount. In that case, append
     *  " (-Z%)" after the coupon code, where Z is the extracted number.
     *    Example: couponCode "PCT15" → "Coupon: PCT15 (-15%)"
     *
     *  If couponCode starts with "FLAT" followed by digits (e.g. "FLAT10"),
     *  append " (-$W)" where W is the extracted number.
     *    Example: couponCode "FLAT10" → "Coupon: FLAT10 (-$10)"
     *
     *  For any other non-empty couponCode, just include the code as-is.
     *    Example: couponCode "WELCOME" → "Coupon: WELCOME"
     *
     *  You may use Integer.parseInt to convert a digit string to an int.
     *
     *  Precondition: catalog.getCouponCode() is not null.
     *                If couponCode starts with "PCT" or "FLAT", the remaining
     *                characters are valid digits.
     */
    public String getReceiptSummary()
    { /* to be implemented in Part B */ }
}
```

**예시:**

| catalog.getSubtotal() | catalog.getItemCount() | isMember | catalog.getCouponCode() | getShippingCost() | getReceiptSummary() |
|----------|-----------|----------|-----------|-------------------|---------------------|
| 50.0 | 2 | true | "PCT15" | 0.0 | "Items: 2 \| Subtotal: $50.0 \| Shipping: $0.0 \| Coupon: PCT15 (-15%)" |
| 20.0 | 5 | false | "" | 9.99 | "Items: 5 \| Subtotal: $20.0 \| Shipping: $9.99 \| Coupon: NONE" |
| 80.0 | 10 | false | "FLAT10" | 12.99 | "Items: 10 \| Subtotal: $80.0 \| Shipping: $12.99 \| Coupon: FLAT10 (-$10)" |

### Part A (4점)

`getShippingCost` 메서드를 작성하세요.

### Part B (3점)

`getReceiptSummary` 메서드를 작성하세요. `Integer.parseInt(String s)` 메서드를 사용할 수 있습니다.

---

## Question 2: Class Design (7점)

한 도서관에서 책 대출 시스템을 관리합니다. 각 `LibraryBook` 객체는 책 한 권을 나타내며 다음의 정보와 기능을 가집니다.

| 항목 | 설명 |
|------|------|
| `title` | 책 제목 (`String`). 생성 시 설정되며 변경 불가. |
| `isCheckedOut` | 대출 여부 (`boolean`). 생성 시 `false`. |
| `dueDate` | 반납 기한 (일 수, `int`). 대출 중이 아니면 `-1`. 생성 시 `-1`. |
| `LibraryBook(String title)` | 생성자. 제목을 설정하고 초기 상태를 지정. |
| `getTitle()` | 제목을 반환. |
| `isAvailable()` | 대출 가능 여부를 반환. 대출 중이 아니면 `true`. |
| `checkOut(int days)` | 책을 대출. `isCheckedOut`를 `true`로, `dueDate`를 `days`로 설정. 이미 대출 중이면 아무 동작 없이 `false` 반환. 성공하면 `true` 반환. Precondition: `days > 0` |
| `returnBook()` | 책을 반납. `isCheckedOut`를 `false`로, `dueDate`를 `-1`로 설정. 대출 중이 아니면 아무 동작 없이 `false` 반환. 성공하면 `true` 반환. |
| `getInfo()` | `"Title: [title], Status: [Available/Checked Out], Due: [dueDate 또는 N/A]"` 형식의 문자열 반환. |

**실행 예시 (Execution Table):**

| Statement / Expression | Return Value | Comment |
|----------------------|-------------|---------|
| `LibraryBook b = new LibraryBook("Java");` | | 책 생성, 대출 가능 상태 |
| `b.getTitle()` | `"Java"` | 제목 반환 |
| `b.isAvailable()` | `true` | 대출되지 않은 상태 |
| `b.checkOut(14)` | `true` | 14일간 대출 성공 |
| `b.isAvailable()` | `false` | 현재 대출 중 |
| `b.checkOut(7)` | `false` | 이미 대출 중 — 무시됨 |
| `b.getInfo()` | `"Title: Java, Status: Checked Out, Due: 14"` | 대출 중 상태 출력 |
| `b.returnBook()` | `true` | 반납 성공 |
| `b.isAvailable()` | `true` | 다시 대출 가능 |
| `b.returnBook()` | `false` | 대출 중이 아님 — 무시됨 |
| `b.getInfo()` | `"Title: Java, Status: Available, Due: N/A"` | 가용 상태 출력 |

`LibraryBook` 클래스를 완성하세요. 위의 모든 인스턴스 변수, 생성자, 메서드를 포함해야 합니다.

---

## Question 3: Data Analysis with ArrayList (5점)

한 학교에서 학생들의 시험 점수를 관리합니다. `GradeAnalyzer` 클래스의 일부가 아래에 나와 있습니다.

```java
public class GradeAnalyzer {
    private ArrayList<StudentRecord> records;

    /**
     * StudentRecord 클래스:
     * - String getName()     // 학생 이름 반환
     * - int getScore()       // 시험 점수 반환 (0~100)
     * - String getSubject()  // 과목명 반환
     */

    /**
     * 주어진 과목(subject)에서 점수가 threshold 이상인 학생들의 이름을 담은
     * ArrayList를 반환합니다.
     *
     * 결과 리스트는 records에 나타나는 순서대로 정렬됩니다.
     * 해당하는 학생이 없으면 빈 ArrayList를 반환합니다.
     *
     * 같은 학생이 같은 과목에서 여러 record를 가질 수 있습니다.
     * 이 경우, 조건을 만족하는 모든 record에 대해 이름이 추가됩니다.
     * (중복 허용)
     *
     * Precondition: subject is not null.
     *               No elements of records are null.
     *
     * @param subject 과목명
     * @param threshold 최소 점수 (이 점수 이상이면 포함)
     * @return 조건을 만족하는 학생 이름의 리스트
     */
    public ArrayList<String> getHighScorers(String subject, int threshold) {
        /* 여기에 구현 */
    }
}
```

`getHighScorers` 메서드를 구현하세요.

**예시:**

`records`가 다음과 같을 때:

| 이름 | 점수 | 과목 |
|------|------|------|
| "Kim" | 92 | "Math" |
| "Lee" | 85 | "Math" |
| "Park" | 78 | "Science" |
| "Kim" | 88 | "Science" |
| "Choi" | 95 | "Math" |

`getHighScorers("Math", 90)` 호출 시 `["Kim", "Choi"]`를 반환합니다.

---

## Question 4: 2D Array (6점)

한 날씨 관측소에서 여러 관측 지점의 여러 날에 걸친 기온 데이터를 2D 배열로 관리합니다. `WeatherStation` 클래스의 일부가 아래에 나와 있습니다.

```java
public class WeatherStation {

    /** 관측 지점 하나의 정보를 나타냅니다. */
    public class Location {
        /** 관측 지점의 이름을 반환합니다. */
        public String getName()
        { /* implementation not shown */ }

        /** 관측 지점의 위도를 반환합니다. */
        public double getLatitude()
        { /* implementation not shown */ }
    }

    /** temps[r][c]는 관측 지점 r의 c번째 날 기온(정수, 섭씨)을 나타냅니다.
     *  Precondition: temps는 최소 1행 1열의 직사각형 배열이다.
     */
    private int[][] temps;

    /** locations[r]은 관측 지점 r의 Location 객체입니다.
     *  Precondition: locations.length == temps.length
     */
    private Location[] locations;

    /** temps에서 기온 범위(해당 열의 최댓값 − 최솟값)가 가장 큰 열의
     *  인덱스를 반환합니다.
     *  기온 범위가 같은 열이 여러 개 있으면, 인덱스가 가장 작은 열을 반환합니다.
     *
     *  Precondition: temps는 최소 1행 1열의 직사각형 배열이다.
     */
    public int columnWithLargestRange() {
        /* 여기에 구현 */
    }
}
```

`columnWithLargestRange` 메서드를 구현하세요.

**예시:**

`temps`가 다음과 같을 때:

```
           Day 0   Day 1   Day 2   Day 3
지점 0  |   5   |  12   |   8   |  10   |
지점 1  |  -2   |  10   |   7   |   9   |
지점 2  |   3   |  14   |   9   |  11   |
```

- Day 0: max = 5, min = −2 → 범위 = 7
- Day 1: max = 14, min = 10 → 범위 = 4
- Day 2: max = 9, min = 7 → 범위 = 2
- Day 3: max = 11, min = 9 → 범위 = 2

Day 0의 범위(7)가 가장 크므로 반환값은 **0** 입니다.

---

---

## Q1 풀이 및 채점기준

### 정답 코드

**Part A:**
```java
public double getShippingCost() {
    if (getIsMember() && catalog.getSubtotal() >= 30.0) {
        return 0.0;
    }
    if (catalog.getItemCount() <= 3) {
        return 5.99;
    }
    if (catalog.getItemCount() <= 8) {
        return 9.99;
    }
    return 9.99 + 1.50 * (catalog.getItemCount() - 8);
}
```

**Part B:**
```java
public String getReceiptSummary() {
    String result = "Items: " + catalog.getItemCount()
                  + " | Subtotal: $" + catalog.getSubtotal()
                  + " | Shipping: $" + getShippingCost()
                  + " | Coupon: ";

    String code = catalog.getCouponCode();

    if (code.equals("")) {
        result += "NONE";
    } else if (code.indexOf("PCT") == 0) {
        int pct = Integer.parseInt(code.substring(3));
        result += code + " (-" + pct + "%)";
    } else if (code.indexOf("FLAT") == 0) {
        int amt = Integer.parseInt(code.substring(4));
        result += code + " (-$" + amt + ")";
    } else {
        result += code;
    }

    return result;
}
```

### Q1 채점 기준 (7점)

#### Part A (4점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 1 | `getIsMember()` AND `catalog.getSubtotal() >= 30.0` 조건에서 0.0 반환 *(algorithm)* | `catalog` 객체의 메서드를 올바르게 호출해야 함. `>` 대신 `>=` 필요 (경계 포함) | 1점 |
| 2 | 멤버 무료배송이 아닌 경우 `catalog.getItemCount() <= 3` → 5.99 반환 *(algorithm)* | `<` 대신 `<=` 필요 (3개 이하). 멤버 체크보다 먼저 오면 earn 불가 | 1점 |
| 3 | `catalog.getItemCount() <= 8` → 9.99 반환 *(algorithm)* | 이전 조건(`<= 3`)과 올바르게 구분되어야 함. `else if` 또는 순차 `if`+`return` 모두 가능 | 1점 |
| 4 | `itemCount > 8`일 때 `9.99 + 1.50 * (catalog.getItemCount() - 8)` 계산 *(algorithm)* | 초과분 계산에서 `-8` 누락 시 earn 불가. `1.50` 대신 `1.5`도 earn 가능 | 1점 |

**Can still earn:** `catalog.getSubtotal()` 대신 `catalog.subtotal` 등 직접 접근 시도는 컴파일 에러이지만, 의도가 명확하면 알고리즘 포인트는 earn 가능.
**Will not earn:** `catalog` 객체를 전혀 사용하지 않고 존재하지 않는 `getSubtotal()` / `getItemCount()`를 `this`에서 호출하면 해당 조건의 포인트를 earn 불가.

#### Part B (3점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 5 | `catalog.getCouponCode()`가 빈 문자열인지 `equals("")`로 판별 + "NONE" 처리 *(algorithm)* | `==`로 빈 문자열 비교 시 earn 불가. `length() == 0`도 earn 가능 | 1점 |
| 6 | `"PCT"`/`"FLAT"` 접두사를 `indexOf()` 또는 `substring()`으로 판별 + `substring(3)` 또는 `substring(4)`로 숫자 추출 + `Integer.parseInt`로 변환 *(algorithm)* | `"PCT"`는 3글자이므로 `substring(3)`, `"FLAT"`는 4글자이므로 `substring(4)` 필요. 인덱스 오류 시 earn 불가 | 1점 |
| 7 | 올바른 형식의 결과 문자열 조합 — `" | "` 구분자, `"$"` 기호, PCT일 때 `"(-Z%)"`, FLAT일 때 `"(-$W)"` 포함 | 구분자나 기호가 크게 어긋나면 earn 불가. 사소한 공백 오류는 의도 명확하면 earn 가능 | 1점 |

**Can still earn:** Part A의 `getShippingCost()`가 틀려도 Part B에서 호출한 로직이 올바르면 Part B 점수는 독립적으로 earn 가능.
**Will not earn:** String 메서드(`substring`, `indexOf`, `equals`)를 전혀 사용하지 않으면 포인트 5, 6을 earn 불가.

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect (인스턴스 변수를 의도치 않게 변경)
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)
- `else if` 대신 독립 `if`문을 사용했지만 로직이 동일하면

### 흔한 실수
- `catalog.getSubtotal() >= 30.0` 경계값에서 `>` 사용 (30.0 포함이므로 `>=` 필요)
- `catalog` 객체를 통하지 않고 `getSubtotal()` / `getItemCount()`를 `this`에서 호출 (존재하지 않는 메서드)
- 8개 초과 시 추가 배송비 계산에서 `catalog.getItemCount() - 8` 대신 `catalog.getItemCount()` 사용
- `catalog.getCouponCode().equals("")` 대신 `catalog.getCouponCode() == ""` 사용 (문자열 비교는 `equals`)
- `"PCT"`는 3글자인데 `substring(4)`로 잘못 추출
- `"FLAT"`는 4글자인데 `substring(3)`으로 잘못 추출

---

## Q2 풀이 및 채점기준

### 정답 코드

```java
public class LibraryBook {
    private String title;
    private boolean isCheckedOut;
    private int dueDate;

    public LibraryBook(String title) {
        this.title = title;
        this.isCheckedOut = false;
        this.dueDate = -1;
    }

    public String getTitle() {
        return title;
    }

    public boolean isAvailable() {
        return !isCheckedOut;
    }

    public boolean checkOut(int days) {
        if (isCheckedOut) {
            return false;
        }
        isCheckedOut = true;
        dueDate = days;
        return true;
    }

    public boolean returnBook() {
        if (!isCheckedOut) {
            return false;
        }
        isCheckedOut = false;
        dueDate = -1;
        return true;
    }

    public String getInfo() {
        String status = isCheckedOut ? "Checked Out" : "Available";
        String due = isCheckedOut ? "" + dueDate : "N/A";
        return "Title: " + title + ", Status: " + status + ", Due: " + due;
    }
}
```

### Q2 채점 기준 (7점)

| # | 알고리즘 포인트 | 채점 기준 | Decision Rules | 배점 |
|---|--------------|---------|---------------|------|
| 1 | **Class Header** | 클래스 헤더 올바름 (`public class LibraryBook`) | `class` 키워드 누락 시 earn 불가 | 1점 |
| 2 | **Instance Variables** | 3개의 `private` 인스턴스 변수 선언 (`String`, `boolean`, `int`) | `public` 선언 시 earn 불가. 타입이 하나라도 틀리면 earn 불가 | 1점 |
| 3 | **Constructor** | 생성자: 매개변수 `title` 설정 + `isCheckedOut = false` + `dueDate = -1` | 기본값 누락 시 earn 불가 | 1점 |
| 4 | **Accessor Methods** | `getTitle()` + `isAvailable()` 올바르게 구현 | `isAvailable`이 `!isCheckedOut` 반환해야 함. 둘 중 하나만 맞으면 earn 불가 | 1점 |
| 5 | **Mutator — checkOut** | `checkOut`: 이미 대출 중일 때 `false` 반환 + 성공 시 상태 변경 및 `true` 반환 | 가드 조건 없이 항상 변경하면 earn 불가 | 1점 |
| 6 | **Mutator — returnBook** | `returnBook`: 대출 중이 아닐 때 `false` 반환 + 성공 시 `isCheckedOut=false`, `dueDate=-1`, `true` 반환 | `dueDate`를 -1로 리셋 안 하면 earn 가능하지만 1점 감점 (penalty y) | 1점 |
| 7 | **getInfo** | `getInfo`: 올바른 형식 문자열 반환 — 대출 상태에 따라 "Available"/"Checked Out" 분기, dueDate 또는 "N/A" | 분기 없이 하나의 형식만 반환하면 earn 불가. **`toString` 오버라이드 작성은 CED 1.15.A.5 EXCLUSION이므로 금지** | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴 (예: returnBook에서 dueDate 리셋 누락)
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)
- `this.` 사용 여부는 채점에 영향 없음

### 흔한 실수
- 인스턴스 변수를 `public`으로 선언
- 생성자에서 `isCheckedOut`과 `dueDate` 초기화 누락
- `checkOut`에서 이미 대출 중인 경우의 가드 조건 누락
- `getInfo`에서 `dueDate`를 대출 중이 아닐 때도 숫자로 표시

---

## Q3 풀이 및 채점기준

### 정답 코드

```java
public ArrayList<String> getHighScorers(String subject, int threshold) {
    ArrayList<String> result = new ArrayList<String>();

    for (StudentRecord record : records) {
        if (record.getSubject().equals(subject) && record.getScore() >= threshold) {
            result.add(record.getName());
        }
    }

    return result;
}
```

### Q3 채점 기준 (5점)

| # | 알고리즘 포인트 | 채점 기준 | Decision Rules | 배점 |
|---|--------------|---------|---------------|------|
| 1 | **Initialize** | `ArrayList<String>` 결과 리스트 생성 | `new ArrayList<>()` 또는 `new ArrayList<String>()` 모두 가능 | 1점 |
| 2 | **Traverse** | `records` 리스트를 올바르게 순회 | for-each 또는 인덱스 루프 모두 가능. 범위 오류 시 earn 불가 | 1점 |
| 3 | **Compare (String)** | `getSubject().equals(subject)`로 과목 비교 | `==`로 비교 시 earn 불가 | 1점 |
| 4 | **Compare (int)** | `getScore() >= threshold` 조건 올바름 (경계값 포함) | `>` 사용 시 earn 불가 ("이상"이므로 `>=`) | 1점 |
| 5 | **Build Result** | 조건을 만족하는 학생의 `getName()` 결과를 리스트에 추가 + 리스트 반환 | `record` 자체를 추가하면 earn 불가 (타입 불일치). 반환 누락 시에도 earn 불가 | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect (원본 records 변경)
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)
- `ArrayList<String>` 대신 `ArrayList` (raw type) 사용 — 경고는 나지만 감점 안 함

### 흔한 실수
- `subject == record.getSubject()` 사용 (문자열은 `equals`로 비교)
- `> threshold` 사용 (문제에서 "이상"이므로 `>=`)
- 결과 리스트를 생성하지 않거나 반환하지 않음
- `record.getName()` 대신 `record` 자체를 추가

---

## Q4 풀이 및 채점기준

### 정답 코드

```java
public int columnWithLargestRange() {
    int bestCol = 0;
    int bestRange = 0;

    for (int c = 0; c < temps[0].length; c++) {
        int max = temps[0][c];
        int min = temps[0][c];

        for (int r = 1; r < temps.length; r++) {
            if (temps[r][c] > max) {
                max = temps[r][c];
            }
            if (temps[r][c] < min) {
                min = temps[r][c];
            }
        }

        int range = max - min;
        if (range > bestRange) {
            bestRange = range;
            bestCol = c;
        }
    }

    return bestCol;
}
```

### Q4 채점 기준 (6점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 1 | 외부 루프로 각 열(c)을 순회 (`c < temps[0].length`) | 행을 외부 루프로 잡으면 열별 범위를 구할 수 없음 → earn 불가 | 1점 |
| 2 | 내부 루프로 각 행(r)을 순회하며 해당 열의 값 접근 (`temps[r][c]`) | 행과 열 인덱스가 뒤바뀌면 earn 불가 | 1점 |
| 3 | 각 열에서 최댓값(max)을 올바르게 추적 | max 초기값을 0이나 `Integer.MIN_VALUE`로 해도 로직 올바르면 earn 가능 *(algorithm)* | 1점 |
| 4 | 각 열에서 최솟값(min)을 올바르게 추적 | min 초기값을 `Integer.MAX_VALUE`로 해도 가능. `temps[0][c]`로 초기화가 가장 안전 *(algorithm)* | 1점 |
| 5 | `range = max - min` 계산 올바름 | `min - max`로 하면 음수 → earn 불가 *(algorithm)* | 1점 |
| 6 | 가장 큰 범위의 열 인덱스 추적 + 동점 시 최소 인덱스 + 반환 | `>=` 사용 시 동점에서 마지막 열 반환 → earn 불가. 반환 누락 시 earn 불가 | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴 (원본 temps 배열 변경)
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)
- 변수명이 다르지만 로직이 올바르면 감점 안 함

### 흔한 실수
- **행/열 혼동**: 열을 순회해야 하는데 행을 외부 루프로 잡으면 열별 범위를 구할 수 없음
- `max`/`min` 초기값을 0으로 설정 → 기온이 모두 양수이거나 모두 음수일 때 오류
- `max - min` 대신 `min - max` → 범위가 음수가 되어 비교 실패
- 동점 처리: `>` 대신 `>=` 사용 → 마지막 열이 반환됨 (문제는 가장 작은 인덱스 요구)
- `temps[0].length` 대신 `temps.length`를 열 수로 사용 → 행 수와 열 수 혼동
