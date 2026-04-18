# AP Computer Science A 2026 모의시험 — Set 2: Free Response Questions

> 4문제 | 90분 | 총 25점

---

## Q1: Methods and Control Structures (7점)

### 시나리오: 영화관 티켓 가격 계산기

한 영화관에서 티켓 가격을 계산하고 영수증을 생성하는 시스템을 관리합니다. `TicketBooth` 클래스의 일부가 아래에 나와 있습니다.

```java
public class TicketBooth {
    private int numTickets;       // 구매 티켓 수
    private int customerAge;      // 고객 나이
    private boolean isMatinee;    // 조조 상영 여부
    private String promoCode;     // 프로모션 코드 (없으면 "")

    /** Returns the number of tickets being purchased.
     */
    public int getNumTickets()
    { /* implementation not shown */ }

    /** Returns the customer's age.
     */
    public int getCustomerAge()
    { /* implementation not shown */ }

    /** Returns true if this is a matinee showing.
     */
    public boolean getIsMatinee()
    { /* implementation not shown */ }

    /** Returns the promotion code applied to this purchase.
     *  Returns "" if no promotion is applied.
     */
    public String getPromoCode()
    { /* implementation not shown */ }

    /** Computes and returns the total ticket price for this purchase.
     *
     *  Base price per ticket:
     *  - Matinee showing: $8.50 per ticket
     *  - Non-matinee: $13.00 per ticket
     *
     *  Discounts applied to the total (after multiplying by numTickets):
     *  - If customerAge < 13 OR customerAge >= 65: 25% off the total
     *  - If numTickets >= 5 (group discount): additional $1.50 off per ticket
     *    (applied AFTER the age discount if applicable)
     *
     *  The total price cannot go below 0.0.
     *
     *  Precondition: numTickets >= 1, customerAge >= 0
     */
    public double getTotalPrice()
    { /* to be implemented in Part A */ }

    /** Returns a receipt string for this purchase.
     *
     *  The receipt has the format:
     *    "Tickets: N x $P.PP = $T.TT | Promo: DESCRIPTION"
     *
     *  Where N is numTickets, P.PP is the per-ticket base price
     *  (8.50 or 13.00), and T.TT is the result of getTotalPrice().
     *
     *  The promo description is determined as follows:
     *  - If promoCode is "", the promo portion should read "Promo: NONE".
     *  - If promoCode starts with "OFF" followed by digits (e.g. "OFF5"),
     *    the digits represent a dollar discount. Append " (-$D)" where D
     *    is the extracted number.
     *      Example: promoCode "OFF5" → "Promo: OFF5 (-$5)"
     *  - If promoCode starts with "BUY" followed by digits (e.g. "BUY2"),
     *    append " (buy D get 1 free)" where D is the extracted number.
     *      Example: promoCode "BUY2" → "Promo: BUY2 (buy 2 get 1 free)"
     *  - For any other non-empty promoCode, just include the code as-is.
     *
     *  You may use Integer.parseInt to convert a digit string to an int.
     *
     *  Precondition: promoCode is not null.
     *                If promoCode starts with "OFF" or "BUY", the remaining
     *                characters are valid digits.
     */
    public String getReceipt()
    { /* to be implemented in Part B */ }
}
```

**예시:**

| numTickets | customerAge | isMatinee | promoCode | getTotalPrice() | getReceipt() |
|------------|-------------|-----------|-----------|-----------------|--------------|
| 2 | 10 | true | "OFF5" | 12.75 | "Tickets: 2 x $8.5 = $12.75 \| Promo: OFF5 (-$5)" |
| 6 | 30 | false | "" | 69.0 | "Tickets: 6 x $13.0 = $69.0 \| Promo: NONE" |
| 3 | 70 | false | "BUY2" | 29.25 | "Tickets: 3 x $13.0 = $29.25 \| Promo: BUY2 (buy 2 get 1 free)" |

*참고: 2장, 10세, 조조 → 8.50 * 2 = 17.0, 25% off → 12.75. / 6장, 30세, 비조조 → 13.0 * 6 = 78.0, 그룹 할인 78.0 - 1.50*6 = 69.0. / 3장, 70세, 비조조 → 13.0 * 3 = 39.0, 25% off → 29.25.*

### Part A (4점)

`getTotalPrice` 메서드를 작성하세요.

### Part B (3점)

`getReceipt` 메서드를 작성하세요. `Integer.parseInt(String s)` 메서드를 사용할 수 있습니다.

---

### Q1 정답 코드

**Part A:**
```java
public double getTotalPrice() {
    double basePrice;
    if (getIsMatinee()) {
        basePrice = 8.50;
    } else {
        basePrice = 13.00;
    }

    double total = basePrice * getNumTickets();

    if (getCustomerAge() < 13 || getCustomerAge() >= 65) {
        total = total * 0.75;
    }

    if (getNumTickets() >= 5) {
        total = total - 1.50 * getNumTickets();
    }

    if (total < 0.0) {
        total = 0.0;
    }

    return total;
}
```

**Part B:**
```java
public String getReceipt() {
    double basePrice;
    if (getIsMatinee()) {
        basePrice = 8.50;
    } else {
        basePrice = 13.00;
    }

    String result = "Tickets: " + getNumTickets() + " x $" + basePrice
                  + " = $" + getTotalPrice() + " | Promo: ";

    String code = getPromoCode();

    if (code.equals("")) {
        result += "NONE";
    } else if (code.indexOf("OFF") == 0) {
        int dollars = Integer.parseInt(code.substring(3));
        result += code + " (-$" + dollars + ")";
    } else if (code.indexOf("BUY") == 0) {
        int num = Integer.parseInt(code.substring(3));
        result += code + " (buy " + num + " get 1 free)";
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
| 1 | `getIsMatinee()`에 따라 기본 가격 결정 (8.50 / 13.00) + `getNumTickets()` 곱하여 총액 산출 *(algorithm)* | 헬퍼 메서드를 올바르게 호출해야 함. 인스턴스 변수 직접 접근도 earn 가능. 기본 가격이 뒤바뀌면 earn 불가 | 1점 |
| 2 | `getCustomerAge() < 13` OR `getCustomerAge() >= 65`일 때 25% 할인 적용 *(algorithm)* | `&&` 대신 `\|\|` 사용 필요. `0.75` 곱하기 또는 `0.25` 빼기 모두 가능. 경계값(13, 65) 처리가 틀리면 earn 불가 | 1점 |
| 3 | `getNumTickets() >= 5`일 때 `1.50 * numTickets` 추가 할인 (나이 할인 후 적용) *(algorithm)* | 나이 할인 전에 그룹 할인이 적용되면 결과가 다를 수 있음. `>=` 대신 `>` 사용 시 earn 불가 | 1점 |
| 4 | 최종 가격이 0.0 미만이면 0.0으로 보정 + 반환 *(algorithm)* | `if (total < 0.0) total = 0.0;` 형태의 if 비교 사용. 보정 누락 시 earn 불가 | 1점 |

**Can still earn:** 헬퍼 메서드 대신 인스턴스 변수 직접 접근해도 알고리즘 포인트는 earn 가능.
**Will not earn:** 할인 적용 순서가 뒤바뀌어 결과가 달라지면 포인트 3을 earn 불가.

#### Part B (3점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 5 | `getPromoCode()`가 빈 문자열인지 `equals("")`로 판별 + "NONE" 처리 *(algorithm)* | `==`로 빈 문자열 비교 시 earn 불가. `length() == 0`도 earn 가능 | 1점 |
| 6 | `"OFF"`/`"BUY"` 접두사를 `indexOf()` 또는 `substring()`으로 판별 + `substring(3)`으로 숫자 추출 + `Integer.parseInt`로 변환 *(algorithm)* | `"OFF"`, `"BUY"` 모두 3글자이므로 `substring(3)` 필요. 인덱스 오류 시 earn 불가 | 1점 |
| 7 | 올바른 형식의 영수증 문자열 조합 — `" | "` 구분자, 가격 포함, OFF일 때 `"(-$D)"`, BUY일 때 `"(buy D get 1 free)"` | 구분자나 형식이 크게 어긋나면 earn 불가. 사소한 공백 오류는 의도 명확하면 earn 가능 | 1점 |

**Can still earn:** Part A의 `getTotalPrice()`가 틀려도 Part B에서 호출 로직이 올바르면 Part B 점수는 독립적으로 earn 가능.
**Will not earn:** String 메서드(`substring`, `indexOf`, `equals`)를 전혀 사용하지 않으면 포인트 5, 6을 earn 불가.

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)
- `else if` 대신 독립 `if`로 판별 (기능적으로 동일하면)

### Q1 흔한 실수
- 나이 할인과 그룹 할인의 적용 순서를 뒤바꿈 (나이 할인 먼저, 그룹 할인 나중)
- `getCustomerAge() < 13 || getCustomerAge() >= 65`에서 `||` 대신 `&&` 사용
- 그룹 할인 조건 `>= 5`를 `> 5`로 잘못 작성
- 총 가격이 0 미만일 때 0으로 보정하는 처리 누락
- `getPromoCode().equals("")` 대신 `== ""` 사용 (문자열 비교는 `equals`)
- `"OFF"`, `"BUY"` 모두 3글자인데 `substring(4)`로 잘못 추출

---

## Q2: Class Design (7점)

### 시나리오: 자판기 (VendingMachine)

자판기를 관리하는 `VendingMachine` 클래스를 설계합니다. 각 자판기에는 하나의 상품이 들어 있으며, 가격과 재고를 관리합니다.

다음 요구사항에 따라 `VendingMachine` 클래스를 **완전히** 작성하세요.

| 항목 | 설명 |
|------|------|
| `itemName` | 상품 이름 (`String`). 생성 시 설정되며 변경 불가. |
| `price` | 상품 가격 (`double`). 생성 시 설정되며 변경 불가. |
| `stock` | 현재 재고 수량 (`int`). 생성 시 설정. |
| `totalRevenue` | 누적 매출 (`double`). 생성 시 `0.0`. |
| `VendingMachine(String itemName, double price, int stock)` | 생성자. 상품명, 가격, 초기 재고를 설정. Precondition: `price > 0`, `stock >= 0` |
| `getItemName()` | 상품 이름을 반환. |
| `getStock()` | 현재 재고를 반환. |
| `isInStock()` | 재고가 1개 이상이면 `true` 반환. |
| `dispense(int quantity)` | 상품을 `quantity`개 판매. 재고가 충분하면 재고를 줄이고 `totalRevenue`에 `price * quantity`를 더한 뒤 `true` 반환. 재고 부족이면 아무 동작 없이 `false` 반환. Precondition: `quantity > 0` |
| `restock(int amount)` | 재고를 `amount`만큼 추가. Precondition: `amount > 0` |
| `getInfo()` | `"[itemName]: $[price] (stock: [stock], revenue: $[totalRevenue])"` 형식 반환. |

**실행 예시 (Execution Table):**

| Statement / Expression | Return Value | Comment |
|----------------------|-------------|---------|
| `VendingMachine vm = new VendingMachine("Cola", 1.50, 10);` | | 자판기 생성 |
| `vm.getItemName()` | `"Cola"` | 상품명 반환 |
| `vm.getStock()` | `10` | 초기 재고 |
| `vm.isInStock()` | `true` | 재고 있음 |
| `vm.dispense(3)` | `true` | 3개 판매 성공 (매출 $4.5) |
| `vm.getStock()` | `7` | 재고 감소 |
| `vm.dispense(8)` | `false` | 재고 부족 — 무시됨 |
| `vm.getStock()` | `7` | 재고 변화 없음 |
| `vm.restock(5)` | | 재고 5개 추가 |
| `vm.getStock()` | `12` | 재고 증가 |
| `vm.getInfo()` | `"Cola: $1.5 (stock: 12, revenue: $4.5)"` | 현재 상태 출력 |

---

### Q2 정답 코드

```java
public class VendingMachine {
    private String itemName;
    private double price;
    private int stock;
    private double totalRevenue;

    public VendingMachine(String itemName, double price, int stock) {
        this.itemName = itemName;
        this.price = price;
        this.stock = stock;
        this.totalRevenue = 0.0;
    }

    public String getItemName() {
        return itemName;
    }

    public int getStock() {
        return stock;
    }

    public boolean isInStock() {
        return stock > 0;
    }

    public boolean dispense(int quantity) {
        if (quantity > stock) {
            return false;
        }
        stock -= quantity;
        totalRevenue += price * quantity;
        return true;
    }

    public void restock(int amount) {
        stock += amount;
    }

    public String getInfo() {
        return itemName + ": $" + price + " (stock: " + stock
               + ", revenue: $" + totalRevenue + ")";
    }
}
```

### Q2 채점 기준 (7점)

| # | 알고리즘 포인트 | 채점 기준 | Decision Rules | 배점 |
|---|--------------|---------|---------------|------|
| 1 | **Instance Variables** | 4개의 `private` 인스턴스 변수 선언 (`String`, `double`, `int`, `double`) | `public` 선언 시 earn 불가. 타입 하나라도 틀리면 earn 불가 | 1점 |
| 2 | **Constructor** | 생성자: 3개 매개변수 할당 + `totalRevenue = 0.0` 초기화 | 기본값 초기화 누락 시 earn 불가 | 1점 |
| 3 | **Accessor Methods** | `getItemName()` + `getStock()` + `isInStock()` 올바르게 구현 | `isInStock`이 `stock > 0` 반환해야 함. 셋 중 하나라도 틀리면 earn 불가 | 1점 |
| 4 | **Mutator — dispense (guard)** | `dispense`: 재고 부족 시 `false` 반환 + 상태 변경 없음 | 가드 조건 없이 항상 판매하면 earn 불가 | 1점 |
| 5 | **Mutator — dispense (update)** | `dispense`: 성공 시 `stock -= quantity` + `totalRevenue += price * quantity` + `true` 반환 | 매출 계산에서 quantity 곱하기 누락 시 earn 불가 | 1점 |
| 6 | **Mutator — restock** | `restock`: `stock += amount` 올바르게 구현 | `stock = amount` (덮어쓰기) 시 earn 불가 | 1점 |
| 7 | **getInfo** | `getInfo`: 올바른 형식 문자열 반환 | 형식 오류 시에도 의도가 명확하면 earn 가능. **`toString` 오버라이드 작성은 CED 1.15.A.5 EXCLUSION이므로 금지** | 1점 |

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
- `dispense`에서 재고 부족 체크 없이 항상 판매 → 재고가 음수가 됨
- `totalRevenue += price` (quantity 곱하기 누락)
- `restock`에서 `stock = amount` (누적이 아닌 덮어쓰기)
- `getInfo`에서 `$` 기호 위치 오류

---

## Q3: ArrayList (5점)

### 시나리오: 주문 처리기 (OrderProcessor)

온라인 쇼핑몰에서 재고 부족 상품이 포함된 주문을 걸러내는 시스템입니다.

```java
public class OrderItem {
    /** 상품명을 반환합니다. */
    public String getProductName()
    { /* implementation not shown */ }

    /** 주문 수량을 반환합니다. */
    public int getQuantity()
    { /* implementation not shown */ }

    /** 현재 재고 수량을 반환합니다. */
    public int getStockAvailable()
    { /* implementation not shown */ }
}
```

```java
import java.util.ArrayList;

public class OrderProcessor {
    private ArrayList<OrderItem> items;

    public OrderProcessor(ArrayList<OrderItem> items) {
        this.items = items;
    }

    /**
     * items에서 주문 수량(getQuantity())이 재고 수량(getStockAvailable())보다
     * 큰 항목을 모두 제거하고, 제거된 항목의 상품명을 담은
     * ArrayList<String>을 반환합니다.
     *
     * 반환 리스트의 순서는 items에서의 원래 순서와 같아야 합니다.
     * 해당하는 항목이 없으면 빈 ArrayList를 반환합니다.
     *
     * Precondition: No elements of items are null.
     * Postcondition: items는 수정됨 (재고 부족 항목이 제거된 상태)
     *
     * @param 없음
     * @return 제거된 항목의 상품명 리스트
     */
    public ArrayList<String> removeOutOfStock() {
        /* 여기에 구현 */
    }
}
```

`removeOutOfStock` 메서드를 구현하세요.

**예시:**

`items`가 다음과 같을 때:

| 상품명 | 주문 수량 | 재고 수량 |
|--------|----------|----------|
| "Laptop" | 2 | 5 |
| "Mouse" | 10 | 3 |
| "Keyboard" | 1 | 1 |
| "Monitor" | 3 | 2 |

`removeOutOfStock()` 호출 후:
- 반환값: `["Mouse", "Monitor"]`
- `items`에 남은 항목: "Laptop", "Keyboard"

---

### Q3 정답 코드

```java
public ArrayList<String> removeOutOfStock() {
    ArrayList<String> removed = new ArrayList<String>();
    int i = 0;
    while (i < items.size()) {
        if (items.get(i).getQuantity() > items.get(i).getStockAvailable()) {
            removed.add(items.get(i).getProductName());
            items.remove(i);
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
| 2 | **Traverse** | `items` 리스트를 올바르게 순회 | while 또는 역순 for 루프 필요. for-each + remove → `ConcurrentModificationException` → earn 불가 | 1점 |
| 3 | **Compare** | `getQuantity() > getStockAvailable()` 조건 올바름 | `>=` 사용 시 earn 불가 (수량 == 재고일 때는 충족 가능). 메서드명 틀리면 earn 불가 | 1점 |
| 4 | **Remove + Collect** | 조건 충족 시 상품명(`getProductName()`)을 결과 리스트에 추가 + `items`에서 제거 | 상품명이 아닌 객체 자체를 추가하면 타입 불일치로 earn 불가 | 1점 |
| 5 | **Index Management** | 제거 시 인덱스 밀림 없이 올바르게 처리 + 결과 리스트 반환 | for 루프에서 remove 후 무조건 i++ → 건너뜀 → earn 불가. 반환 누락 시 earn 불가 | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)

### Q3 흔한 실수
- for 루프에서 `remove(i)` 후 무조건 `i++` → 인덱스 밀림으로 일부 항목 건너뜀
- `getQuantity() >= getStockAvailable()` 사용 → 수량 == 재고인 경우를 잘못 제거
- `getProductName()` 대신 `OrderItem` 객체 자체를 결과 리스트에 추가 (타입 불일치)
- for-each 루프에서 `remove()` 호출 → `ConcurrentModificationException`
- 결과 리스트에 추가하기 전에 `items.remove(i)` 호출 → 상품명 접근 불가 (remove가 반환하므로 가능하지만 혼동 위험)

---

## Q4: 2D Array (6점)

### 시나리오: 이미지 밝기 분석 (Pixel Brightness)

디지털 이미지의 픽셀 밝기를 2D 배열로 관리합니다. `ImageAnalyzer` 클래스의 일부가 아래에 나와 있습니다.

```java
public class ImageAnalyzer {

    /** 픽셀 하나의 정보를 나타냅니다. */
    public class Pixel {
        /** 이 픽셀의 밝기 값(0~255)을 반환합니다. */
        public int getBrightness()
        { /* implementation not shown */ }

        /** 이 픽셀의 색상 채널 이름("R", "G", 또는 "B")을 반환합니다. */
        public String getChannel()
        { /* implementation not shown */ }
    }

    /** pixels[r][c]는 행 r, 열 c 위치의 밝기(0~255 정수)를 나타냅니다.
     *  Precondition: pixels는 최소 3행 3열의 직사각형 배열이다.
     */
    private int[][] pixels;

    /** pixels에서 "밝은 내부 셀"의 수를 반환합니다.
     *
     *  "밝은 내부 셀"의 정의:
     *  - 배열의 가장자리(첫/마지막 행, 첫/마지막 열)에 있지 않은 셀
     *  - 상하좌우 4개의 인접 셀 모두보다 밝기 값이 **엄격하게 큰(strictly greater)** 셀
     *
     *  Precondition: pixels는 최소 3행 3열의 직사각형 배열이다.
     */
    public int countBrightPeaks() {
        /* 여기에 구현 */
    }
}
```

`countBrightPeaks` 메서드를 구현하세요.

**예시:**

`pixels`가 다음과 같을 때:

```
        Col 0   Col 1   Col 2   Col 3   Col 4
Row 0 |  100  |  110  |  120  |  110  |  100  |
Row 1 |  110  |  200  |  130  |  180  |  110  |
Row 2 |  105  |  140  |  250  |  140  |  105  |
Row 3 |  110  |  190  |  130  |  170  |  110  |
Row 4 |  100  |  110  |  120  |  110  |  100  |
```

내부 셀 검사 (가장자리 행/열 제외):
- (1,1)=200: 위 110, 아래 140, 좌 110, 우 130 → 모두보다 큼 → **밝은 내부 셀**
- (1,2)=130: 위 120, 아래 250, 좌 200, 우 180 → 250보다 작음 → 아님
- (1,3)=180: 위 110, 아래 140, 좌 130, 우 110 → 모두보다 큼 → **밝은 내부 셀**
- (2,1)=140: 위 200, 아래 190, 좌 105, 우 250 → 200보다 작음 → 아님
- (2,2)=250: 위 130, 아래 130, 좌 140, 우 140 → 모두보다 큼 → **밝은 내부 셀**
- (2,3)=140: 위 180, 아래 170, 좌 250, 우 105 → 180보다 작음 → 아님
- (3,1)=190: 위 140, 아래 110, 좌 110, 우 130 → 모두보다 큼 → **밝은 내부 셀**
- (3,2)=130: 위 250, 아래 120, 좌 190, 우 170 → 250보다 작음 → 아님
- (3,3)=170: 위 140, 아래 110, 좌 130, 우 110 → 모두보다 큼 → **밝은 내부 셀**

반환값: **5**

---

### Q4 정답 코드

```java
public int countBrightPeaks() {
    int count = 0;

    for (int r = 1; r < pixels.length - 1; r++) {
        for (int c = 1; c < pixels[0].length - 1; c++) {
            int val = pixels[r][c];
            if (val > pixels[r - 1][c]
                    && val > pixels[r + 1][c]
                    && val > pixels[r][c - 1]
                    && val > pixels[r][c + 1]) {
                count++;
            }
        }
    }

    return count;
}
```

### Q4 채점 기준 (6점)

| # | 채점 기준 | Decision Rules | 배점 |
|---|---------|---------------|------|
| 1 | 외부 루프: 행을 **1**부터 `pixels.length - 2`(포함)까지 순회 (가장자리 행 제외) | 0부터 또는 `length-1`까지 순회하면 가장자리 포함 → earn 불가 | 1점 |
| 2 | 내부 루프: 열을 **1**부터 `pixels[0].length - 2`(포함)까지 순회 (가장자리 열 제외) | 열 범위도 가장자리를 제외해야 earn *(algorithm)* | 1점 |
| 3 | 현재 셀의 값과 **위쪽** 인접 셀(`pixels[r-1][c]`)을 올바르게 비교 | 행/열 인덱스 혼동 시 earn 불가 *(algorithm)* | 1점 |
| 4 | 현재 셀의 값과 **아래쪽** 인접 셀(`pixels[r+1][c]`)을 올바르게 비교 | *(algorithm)* | 1점 |
| 5 | 현재 셀의 값과 **좌/우** 인접 셀 모두 올바르게 비교 (4방향 전체 AND 조건) | 4개 중 하나라도 누락 시 earn 불가. `>=` 대신 `>` 필요 (strictly greater) *(algorithm)* | 1점 |
| 6 | 조건 충족 시 카운트 증가 + 최종 카운트 반환 | 반환 누락 시 earn 불가 | 1점 |

#### 1점 감점 사유 (문항당 최대 3점)
- v) `[]` vs `.get()` 혼동
- w) 불필요한 side-effect
- x) 지역변수 미선언
- y) persistent data 파괴
- z) void에서 return value

#### 감점 안 하는 실수
- 세미콜론, 괄호, 대소문자 등 사소한 문법 실수 (의도가 명확하면)
- 4개의 if문 대신 방향 배열(`dr/dc`)로 처리해도 동일 점수

### Q4 흔한 실수
- 가장자리 행/열을 제외하지 않아 인접 셀 접근 시 `ArrayIndexOutOfBoundsException`
- `>=` 사용 → "엄격하게 큰" 조건이 아닌 "이상" 조건이 되어 동일값도 포함됨
- 4방향 비교 중 일부 누락 (예: 좌우만 비교하고 상하 빠뜨림)
- 행/열 인덱스를 뒤바꿈: `pixels[r-1][c]`(위)를 `pixels[r][c-1]`(좌)로 잘못 작성
- AND 조건 대신 OR 조건 사용 → "하나라도 크면"이 되어 결과 과대 집계

---

*끝*
