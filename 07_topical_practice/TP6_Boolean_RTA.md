# TP6: Boolean 심화 + Run-Time Analysis (보강 세트)

> **CED 2025-26 토픽**: 2.5 Compound Boolean, 2.6 Comparing Boolean Expressions, 2.12 Informal Run-Time Analysis
> **문항 수**: 8 MCQ (Hard 위주)
> **시간 권장**: 20분
> **목표 정답률**: 80% 이상

---

## CED 범위 준수 사항

- **2.5.A.1**: `!`, `&&`, `||` — 우선순위는 `!` > `&&` > `||`
- **2.5.A.2**: **Short-circuit evaluation** — 좌측만으로 결과 결정 시 우측 미평가
- **2.6.A.1**: 두 boolean 식이 모든 입력에서 같은 값이면 **equivalent**. 진리표로 검증
- **2.6.A.2**: **De Morgan's Law** — `!(a && b) ≡ !a || !b`, `!(a || b) ≡ !a && !b`
- **2.6.B.1**: 객체 참조는 `==`/`!=`로 비교 (참조 비교)
- **2.6.B.2**: 객체와 `null` 비교는 `==`/`!=`
- **2.6.B.3**: 클래스가 자체 `equals` 정의 가능 (단, **EXCLUSION**: equals 작성은 OUT)
- **2.12.A.1**: Statement execution count — 명령문 실행 횟수, 트레이싱으로 계산

- **EXCLUSION**: `equals` 오버라이드 작성 OUT, `Math.min/max`, `break`/`continue`, `switch`/`do-while` 모두 사용 금지

---

## 출제 토픽 분포

| # | 토픽 | 핵심 |
|---|------|------|
| 1 | 2.5.A.1 + 2.5.A.2 — short-circuit + 우선순위 | && > \|\|, side effect 추적 |
| 2 | 2.6.A.2 — De Morgan's law | `!(A \|\| B) ≡ !A && !B` |
| 3 | 2.5.A.2 — short-circuit으로 NPE 회피 | null 체크 패턴 |
| 4 | 2.12 — 중첩 루프 실행 횟수 | 1+2+...+n 누적 |
| 5 | 2.12 — while 절반 감소 | log₂n 직관 |
| 6 | 2.6.B.1 + 2.6.B.3 — `==` vs `.equals()` | 참조 vs 내용 비교 |
| 7 | 2.12 — 조건부 카운트 | 대각선 셀 수 |
| 8 | 2.6.A.2 — De Morgan 적용 + 동치 검증 | 두 식이 같은 결과 |

**답안 분포**: A:2 / B:2 / C:2 / D:2

---

## 시험 안내

**Directions**: 다음 각 문항에 대해 가장 적절한 답을 고르시오.

---

### 1. [CED 2.5 · Hard]

다음 코드의 **출력**은? (`check` 메서드는 호출될 때마다 인자를 출력하고 양수면 true 반환)

```java
public static boolean check(int n)
{
    System.out.print(n + " ");
    return n > 0;
}

public static void main(String[] args)
{
    boolean result = check(3) && check(-5) || check(7);
    System.out.println(result);
}
```

(A) `"3 -5 7 true"`
(B) `"3 true"`
(C) `"3 -5 false"`
(D) `"3 -5 7 false"`

---

### 2. [CED 2.6.A.2 · Hard]

다음 boolean 식과 **논리적으로 동치**(equivalent)인 식은? (CED 2.6.A.2: De Morgan's Law)

```java
!(x >= 5 || y < 8)
```

(A) `x >= 5 && y < 8`
(B) `!(x >= 5) || !(y < 8)`
(C) `x < 5 && y >= 8`
(D) `x > 5 && y <= 8`

---

### 3. [CED 2.5.A.2 · Hard]

다음 코드는 **short-circuit evaluation**(CED 2.5.A.2)으로 NullPointerException을 회피한다.

```java
String s = null;
if (s != null && s.length() > 0)
{
    System.out.println("Has content");
}
else
{
    System.out.println("Empty or null");
}
```

출력은?

(A) `"Has content"`
(B) Compile error
(C) `NullPointerException` 발생
(D) `"Empty or null"`

---

### 4. [CED 2.12 · Hard]

다음 코드의 출력은? (CED 2.12.A.1: statement execution count)

```java
int count = 0;
for (int i = 1; i <= 10; i++)
{
    for (int j = 1; j <= i; j++)
    {
        count++;
    }
}
System.out.println(count);
```

(A) `100`
(B) `55`
(C) `45`
(D) `10`

---

### 5. [CED 2.12 · Hard]

다음 코드는 `n`을 **절반씩 감소**시킨다. 출력은?

```java
int n = 100;
int count = 0;
while (n > 1)
{
    n = n / 2;
    count++;
}
System.out.println(count);
```

(A) `7`
(B) `100`
(C) `6`
(D) `50`

---

### 6. [CED 2.6.B · Hard]

다음 코드의 출력은? (CED 2.6.B.1: 객체 참조는 `==`로 비교)

```java
String a = "hello";
String b = new String("hello");
String c = a;

System.out.println((a == b) + " " + (a.equals(b)) + " " + (a == c));
```

(A) `"false true true"`
(B) `"true true true"`
(C) `"false false false"`
(D) `"true false true"`

---

### 7. [CED 2.12 · Hard]

다음 코드의 출력은?

```java
int n = 10;
int count = 0;
for (int i = 0; i < n; i++)
{
    for (int j = 0; j < n; j++)
    {
        if (i == j) count++;
    }
}
System.out.println(count);
```

(A) `100`
(B) `20`
(C) `1`
(D) `10`

---

### 8. [CED 2.5 + 2.6.A.2 · Hard]

다음 코드의 출력은?

```java
int x = 5, y = 10;
boolean a = !(x >= 5 || y < 8);
boolean b = (x < 5 && y >= 8);
System.out.println(a + " " + b + " " + (a == b));
```

(A) `"true true false"`
(B) `"false false true"`
(C) `"true false false"`
(D) `"false true true"`

---

**END OF TP6**
