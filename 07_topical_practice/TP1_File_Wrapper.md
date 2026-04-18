# TP1: File I/O + Wrapper Classes (보강 세트)

> **CED 2025-26 토픽**: 4.6 Using Text Files, 4.7 Wrapper Classes
> **문항 수**: 10 MCQ (Hard 위주)
> **시간 권장**: 25분
> **목표 정답률**: 80% 이상 (5점 수준)

---

## 출제 토픽 분포

| # | 토픽 | 핵심 개념 |
|---|------|---------|
| 1 | 4.6 — `Scanner(File)` + `nextInt`/`nextLine` | 라인/토큰 읽기 구분 |
| 2 | 4.6 — `hasNext` 루프 + `nextInt` | 파일 종료 검사 |
| 3 | 4.6 — `nextLine` vs `next` 차이 | 공백/개행 처리 |
| 4 | 4.6 — `nextInt` 후 `nextLine` 함정 | 버퍼 잔여 개행 |
| 5 | 4.7 — `Integer.parseInt` 기본 | String → int |
| 6 | 4.7 — `Double.parseDouble` 정밀도 | String → double |
| 7 | 4.7 — Autoboxing/Unboxing | int ↔ Integer 자동 변환 |
| 8 | 4.7 — `Integer.MAX_VALUE` 오버플로 | 한계값 처리 |
| 9 | 4.6 + 4.7 — File에서 읽어 parseInt | 통합 패턴 |
| 10 | 4.6 — `close()` 호출 의미 | 자원 정리 |

**답안 분포**: A:3 / B:2 / C:3 / D:2 (균형)

---

## 시험 안내

**Directions**: 다음 각 문항에 대해 가장 적절한 답을 고르시오. 별도 명시가 없는 한 Java Quick Reference의 클래스가 import되어 있다고 가정한다. 모든 파일이 정상적으로 존재하고 읽기 가능하다고 가정한다.

---

### 1. [CED 4.6 · Hard]

`scores.txt` 파일의 내용은 다음과 같다 (각 줄 끝에는 개행 문자가 있다).

```
85
92
78
```

다음 코드를 실행하면 무엇이 출력되는가?

```java
File file = new File("scores.txt");
Scanner sc = new Scanner(file);
int sum = 0;
while (sc.hasNext())
{
    sum += sc.nextInt();
}
sc.close();
System.out.println(sum);
```

(A) `255`
(B) `0`
(C) `85`
(D) `857892`

---

### 2. [CED 4.6 · Hard]

`data.txt` 파일에 다음과 같이 저장되어 있다.

```
3 7 2
9 1
5
```

다음 코드는 무엇을 출력하는가?

```java
Scanner sc = new Scanner(new File("data.txt"));
int count = 0;
int max = Integer.MIN_VALUE;
while (sc.hasNext())
{
    int n = sc.nextInt();
    count++;
    if (n > max) max = n;
}
sc.close();
System.out.println(count + " " + max);
```

(A) `"3 9"`
(B) `"3 7"`
(C) `"6 9"`
(D) `"6 7"`

---

### 3. [CED 4.6 · Hard]

`words.txt` 파일의 내용:

```
hello world
java
```

다음 두 코드의 **차이**는?

**Code A:**
```java
Scanner sc = new Scanner(new File("words.txt"));
String s = sc.next();
sc.close();
System.out.println(s);
```

**Code B:**
```java
Scanner sc = new Scanner(new File("words.txt"));
String s = sc.nextLine();
sc.close();
System.out.println(s);
```

(A) Code A와 B 모두 `"hello world"`
(B) Code A와 B 모두 `"hello"`
(C) Code A: `"hello"`, Code B: `"hello world"`
(D) Code A: `"hello world"`, Code B: `"hello"`

---

### 4. [CED 4.6 · Hard]

`mixed.txt` 파일:

```
42
Hello World
```

다음 코드의 출력은?

```java
Scanner sc = new Scanner(new File("mixed.txt"));
int n = sc.nextInt();
String line = sc.nextLine();
sc.close();
System.out.println(n + "|" + line + "|");
```

(A) `"42||"`
(B) `"42|Hello World|"`
(C) `"42| Hello World|"`
(D) `"42|Hello|"`

---

### 5. [CED 4.7 · Medium]

```java
String s1 = "123";
String s2 = "45";
int n = Integer.parseInt(s1) + Integer.parseInt(s2);
System.out.println(n);
```

무엇이 출력되는가?

(A) `"12345"`
(B) `168`
(C) `"123" + "45"`
(D) Compile-time error

---

### 6. [CED 4.7 · Hard]

```java
String[] inputs = {"3.5", "2.25", "10"};
double sum = 0.0;
for (String s : inputs)
{
    sum += Double.parseDouble(s);
}
System.out.println(sum);
```

무엇이 출력되는가?

(A) `15`
(B) `"3.52.2510"`
(C) Runtime error
(D) `15.75`

---

### 7. [CED 4.7 · Hard]

```java
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(5);          // autoboxing: int 5 → Integer
list.add(10);
int x = list.get(0);  // unboxing: Integer → int
int y = list.get(1) + 3;
list.set(0, x + y);   // autoboxing: int → Integer
System.out.println(list);
```

무엇이 출력되는가?

(A) `[18, 10]`
(B) `[5, 10]`
(C) `[15, 10]`
(D) Compile-time error (int를 ArrayList<Integer>에 직접 add 불가)

---

### 8. [CED 4.7 + 1.5 · Hard]

```java
String s = "2147483647";    // Integer.MAX_VALUE
int n = Integer.parseInt(s);
int m = n + 1;
System.out.println(n == Integer.MAX_VALUE);
System.out.println(m > 0);
```

무엇이 출력되는가?

(A)
```
true
true
```
(B)
```
true
false
```
(C)
```
false
true
```
(D)
```
false
false
```

---

### 9. [CED 4.6 + 4.7 · Hard]

`numbers.txt` 파일은 각 줄에 정수 문자열이 저장되어 있다.

```
100
50
30
```

다음 코드의 출력은?

```java
Scanner sc = new Scanner(new File("numbers.txt"));
int total = 0;
while (sc.hasNext())
{
    String line = sc.nextLine();
    total += Integer.parseInt(line);
}
sc.close();
System.out.println(total);
```

(A) `"1005030"`
(B) Runtime error (`InputMismatchException`)
(C) `180`
(D) `0`

---

### 10. [CED 4.6 · Hard]

다음 두 코드 중 **올바르게 자원을 정리하는** 것은?

**Code A:**
```java
Scanner sc = new Scanner(new File("data.txt"));
int sum = 0;
while (sc.hasNext()) sum += sc.nextInt();
System.out.println(sum);
```

**Code B:**
```java
Scanner sc = new Scanner(new File("data.txt"));
int sum = 0;
while (sc.hasNext()) sum += sc.nextInt();
sc.close();
System.out.println(sum);
```

가장 정확한 설명은?

(A) Code A는 컴파일 에러가 난다 — `close()` 호출이 필수
(B) Code B는 `close()` 후 `System.out.println`이 실행되지 않음
(C) Code A는 `Scanner`가 닫히지 않아 `IOException`이 발생
(D) Code A와 B 모두 정상 동작하지만 Code B가 권장 — `close()`로 파일 핸들/자원을 해제

---

**END OF TP1**
