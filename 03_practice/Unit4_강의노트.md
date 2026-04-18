# Unit 4: Data Collections — AP CSA 강의노트

> **시험 비중: 30-40% (가장 큰 비중!)** | 약 50-52 수업시간  
> FRQ Q3 (ArrayList), Q4 (2D Array) 직접 출제 영역

> ⚠️ **2025-26 CED 토픽 번호 안내**:
> - 본 노트의 4.1(윤리), 4.2(데이터셋 도입)는 CED 2025-26 정식 Unit 4 토픽이 아니라 **수업 도입용 보조 자료**다. 윤리/사회적 이슈는 CED 전반(특히 Big Idea CRD)에 분산 배치되어 있다.
> - 4.3~4.17은 CED 2025-26 Unit 4의 정식 토픽(Array, ArrayList, 2D Array, Searching, Sorting, Recursion)과 매핑된다.
> - 4.6 "Using Text Files (Scanner+File)"은 Java Quick Reference에 포함된 토픽으로, FRQ에서 코드 추적/수정 형태로 출제될 수 있다. **`new Scanner(System.in)` 형태의 키보드 입력은 시험 범위 밖**이다.

---

## 4.1 Ethical and Social Issues (1기간)

> 📍 **CED 매핑**: CED 2025-26에서는 Unit 4의 정식 토픽이 아니다. 윤리적 컴퓨팅은 Big Idea CRD(Computing in Context)에 흩어져 다뤄지며, MCQ에서 시나리오 문제로 출제될 수 있다. 본 노트에서는 데이터 수집 단원의 도입부로 배치한다.

### 핵심 개념

데이터 수집과 활용에는 윤리적/사회적 책임이 따른다.

- **개인정보(PII)**: 이름, 주소, 위치 등 개인을 식별할 수 있는 정보
- **Algorithmic Bias**: 편향된 데이터로 학습된 알고리즘이 불공정한 결과를 만들어냄
- **불완전한 데이터**: 누락, 오류, 오래된 데이터는 잘못된 결론으로 이어짐
- **데이터 보안**: 수집한 데이터가 유출되면 개인에게 피해

### 시험 포인트

- MCQ에서 시나리오 기반 문제 출제 (코딩 아님)
- "이 상황에서 발생할 수 있는 문제는?" 유형
- 데이터 수집 시 동의(consent)의 중요성

### 연습문제

> Q: 대학 입시 알고리즘이 특정 지역 출신 지원자에게 불리한 결과를 보인다. 이 문제의 원인으로 가장 적절한 것은?
> 
> A: 학습 데이터가 특정 지역에 편향되어 있거나, 지역과 상관관계가 있는 변수가 포함된 algorithmic bias

---

## 4.2 Introduction to Using Data Sets (1기간)

> 📍 **CED 매핑**: CED 2025-26 Unit 4의 정식 LO 번호에는 없는 **수업 도입용 보조 토픽**이다. 본격적인 배열/ArrayList 학습(4.3 이후)을 시작하기 전에 "왜 데이터 컬렉션이 필요한가"를 동기 부여하는 단원으로 다룬다.

### 핵심 개념

- **데이터셋(Data Set)**: 관련 정보의 모음(collection of related data)
- 표(table), 차트(chart), 스프레드시트 등으로 표현
- 데이터셋을 프로그램으로 처리하면 패턴 발견, 의사결정 지원 가능
- 큰 데이터셋은 수작업 분석이 불가능 → 프로그래밍 필요

### 시험 포인트

- 개념적 이해 문제 위주
- "데이터를 배열/ArrayList로 저장하여 처리"하는 맥락 이해

---

## 4.3 Array Creation and Access (2기간)

> **쉽게 말해**: 학생 30명의 점수를 저장하려면 변수 30개(`score1`, `score2`, ... `score30`)를 만들어야 할까? 배열을 쓰면 `int[] scores = new int[30];` 한 줄이면 끝이다. 배열은 **같은 종류의 데이터를 한 묶음으로 관리하는 상자**다. 각 칸에 번호(인덱스)가 붙어있어서 `scores[0]`, `scores[1]`처럼 접근한다.

### 핵심 개념

배열(Array)은 **같은 타입**의 데이터를 **고정된 크기**로 저장하는 자료구조이다.

```java
// 선언과 생성 (기본값으로 초기화: int→0, double→0.0, boolean→false, 객체→null)
int[] scores = new int[5];

// 선언과 초기화를 동시에
int[] scores = {90, 85, 78, 92, 88};

// 접근
scores[0] = 95;          // 첫 번째 원소에 95 대입
int first = scores[0];   // 첫 번째 원소 읽기
int last = scores[scores.length - 1];  // 마지막 원소

// 배열 길이
int size = scores.length; // 괄호 없음! 필드(field)임
```

### 기본값 정리

| 타입 | 기본값 |
|------|--------|
| `int` | `0` |
| `double` | `0.0` |
| `boolean` | `false` |
| 참조 타입(String, 객체 등) | `null` |

### 시험 포인트

- **`arr.length`에 괄호 없음!** (String의 `.length()`와 혼동 주의)
- 인덱스 범위: `0` ~ `length - 1`
- 범위 벗어나면 **`ArrayIndexOutOfBoundsException`** (런타임 에러)
- 배열 크기는 생성 후 변경 불가
- `int[] arr;`만 선언하면 배열 객체가 아직 없음 (`null`)

```java
// 자주 나오는 함정
int[] arr = new int[5];
System.out.println(arr[5]); // ArrayIndexOutOfBoundsException! (0~4만 유효)
```

### 연습문제

```java
int[] nums = {10, 20, 30, 40, 50};
nums[2] = nums[0] + nums[4];
System.out.println(nums[2]); // 출력: ?
```

> 정답: `60` (10 + 50)

```java
String[] names = new String[3];
System.out.println(names[0]); // 출력: ?
```

> 정답: `null` (참조 타입 기본값)

---

## 4.4 Array Traversals (3기간)

### 핵심 개념

#### Indexed for loop (인덱스 기반)

```java
int[] arr = {10, 20, 30, 40, 50};

// 모든 원소 출력
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}

// 원소 수정 가능!
for (int i = 0; i < arr.length; i++) {
    arr[i] = arr[i] * 2; // 모든 원소를 2배로
}
```

#### Enhanced for loop (향상된 for문)

```java
int[] arr = {10, 20, 30, 40, 50};

// 모든 원소 출력
for (int val : arr) {
    System.out.println(val);
}
```

#### Enhanced for의 핵심 제약: 값의 복사본!

```java
// ❌ 원소 수정 불가 — val은 복사본
int[] arr = {1, 2, 3};
for (int val : arr) {
    val = val * 2; // arr은 변경되지 않음!
}
// arr은 여전히 {1, 2, 3}

// ✅ 객체 배열에서는 메서드 호출로 수정 가능 (참조의 복사본이므로)
Student[] students = new Student[3];
// ... 초기화 생략
for (Student s : students) {
    s.setGrade(100); // 실제 객체가 수정됨!
}
```

### 시험 포인트

- **indexed for**: 인덱스 필요할 때, 원소 수정할 때, 일부만 탐색할 때
- **enhanced for**: 전체 읽기 전용 탐색에 적합
- enhanced for에서 `val = ...`로 대입해도 원래 배열은 변하지 않음
- 객체 배열의 enhanced for: 참조의 복사본이므로 **메서드 호출은 실제 객체에 반영됨**
- off-by-one 에러 주의: `<=` vs `<`

### 연습문제

```java
int[] arr = {5, 10, 15, 20};
for (int x : arr) {
    x = x + 1;
}
System.out.println(arr[0]); // 출력: ?
```

> 정답: `5` (enhanced for의 x는 복사본이므로 원본 변경 안 됨)

```java
int[] arr = {1, 2, 3, 4, 5};
for (int i = 0; i <= arr.length; i++) {  // 주의: <=
    System.out.print(arr[i] + " ");
}
```

> 정답: `1 2 3 4 5` 출력 후 **ArrayIndexOutOfBoundsException** (i=5일 때)

---

## 4.5 Implementing Array Algorithms (4기간)

### 표준 알고리즘 — 모두 코드로 구현할 수 있어야 함!

#### 1. 합계(Sum)와 평균(Average)

```java
int[] arr = {85, 92, 78, 95, 88};

int sum = 0;
for (int val : arr) {
    sum += val;
}
double avg = (double) sum / arr.length; // 캐스팅 필수!
System.out.println("합계: " + sum);     // 438
System.out.println("평균: " + avg);     // 87.6
```

#### 2. 최대값(Max)과 최소값(Min)

```java
int[] arr = {34, 12, 67, 23, 89, 45};

int max = arr[0]; // 첫 원소로 초기화 (Integer.MIN_VALUE도 가능)
int min = arr[0];
for (int i = 1; i < arr.length; i++) {
    if (arr[i] > max) max = arr[i];
    if (arr[i] < min) min = arr[i];
}
System.out.println("최대: " + max); // 89
System.out.println("최소: " + min); // 12
```

> **Edge Case 주의**: 위 알고리즘에서 `arr[0]`으로 초기화하므로, 배열이 비어있으면(`arr.length == 0`) `ArrayIndexOutOfBoundsException` 발생. AP FRQ에서는 precondition으로 "배열이 비어있지 않다"를 보장하지만, 알아두면 좋다.

#### 3. 특정 조건 존재 확인 (exists)

```java
// 배열에 음수가 있는가?
int[] arr = {3, -1, 7, 5};
boolean hasNegative = false;
for (int val : arr) {
    if (val < 0) {
        hasNegative = true;
        // break; — CED EXCLUSION: break는 AP 시험 범위 밖. 실무에서는 유용하지만 시험에는 사용하지 않는다.
    }
}
System.out.println(hasNegative); // true
```

#### 4. 모든 원소 조건 확인 (for all)

```java
// 모든 원소가 양수인가?
int[] arr = {3, 7, 5, 2};
boolean allPositive = true;
for (int val : arr) {
    if (val <= 0) {
        allPositive = false;
        // break; — CED EXCLUSION: break는 AP 시험 범위 밖
    }
}
System.out.println(allPositive); // true
```

#### 5. 조건 만족 개수 (count)

```java
// 80점 이상인 점수 개수
int[] scores = {85, 72, 91, 68, 95, 80};
int count = 0;
for (int s : scores) {
    if (s >= 80) count++;
}
System.out.println(count); // 4
```

#### 6. 연속 쌍 접근 (consecutive pairs)

```java
// 인접한 두 원소의 합 출력
int[] arr = {1, 3, 5, 7, 9};
for (int i = 0; i < arr.length - 1; i++) { // length-1 주의!
    System.out.println(arr[i] + " + " + arr[i+1] + " = " + (arr[i] + arr[i+1]));
}
// 1 + 3 = 4
// 3 + 5 = 8
// 5 + 7 = 12
// 7 + 9 = 16
```

#### 7. 중복 확인 (duplicates)

```java
int[] arr = {3, 7, 2, 7, 5, 3};
boolean hasDup = false;
for (int i = 0; i < arr.length; i++) {
    for (int j = i + 1; j < arr.length; j++) {
        if (arr[i] == arr[j]) {
            hasDup = true;
            // break; — CED EXCLUSION
        }
    }
    // if (hasDup) break; — CED EXCLUSION: break 대신 boolean 변수로 제어
}
System.out.println(hasDup); // true
```

#### 8. Shift / Rotate

```java
// 왼쪽으로 한 칸 shift (첫 원소 제거, 마지막에 0)
int[] arr = {1, 2, 3, 4, 5};
for (int i = 0; i < arr.length - 1; i++) {
    arr[i] = arr[i + 1];
}
arr[arr.length - 1] = 0;
// 결과: {2, 3, 4, 5, 0}

// 왼쪽으로 rotate (첫 원소가 마지막으로)
int[] arr2 = {1, 2, 3, 4, 5};
int first = arr2[0];
for (int i = 0; i < arr2.length - 1; i++) {
    arr2[i] = arr2[i + 1];
}
arr2[arr2.length - 1] = first;
// 결과: {2, 3, 4, 5, 1}
```

#### 9. Reverse (역순)

```java
int[] arr = {1, 2, 3, 4, 5};
for (int i = 0; i < arr.length / 2; i++) {
    int temp = arr[i];
    arr[i] = arr[arr.length - 1 - i];
    arr[arr.length - 1 - i] = temp;
}
// 결과: {5, 4, 3, 2, 1}
```

### 시험 포인트

- 평균 계산 시 `(double)` 캐스팅 빠뜨리면 정수 나눗셈!
- max/min 초기화를 `arr[0]`으로 하는 것이 안전 (0으로 초기화하면 오류 가능)
- 연속 쌍: 루프 범위 `< arr.length - 1` 기억
- reverse: `arr.length / 2`까지만 반복 (짝수/홀수 모두 동작)

### 연습문제

```java
int[] arr = {4, 7, 2, 8, 1};
int result = arr[0];
for (int i = 1; i < arr.length; i++) {
    if (arr[i] < result) {
        result = arr[i];
    }
}
System.out.println(result); // 출력: ?
```

> 정답: `1` (최소값 찾기)

---

## 4.6 Using Text Files (3기간) ★신규 토픽★

### 핵심 개념

2025-26 CED에서 새로 추가된 토픽. 파일에서 데이터를 읽어 처리하는 방법을 다룬다.

#### File과 Scanner 기본

```java
import java.io.*;         // File, IOException
import java.util.Scanner; // Scanner

public class FileExample {
    // throws IOException 필수!
    public static void main(String[] args) throws IOException {
        File myFile = new File("data.txt");
        Scanner scan = new Scanner(myFile);

        while (scan.hasNext()) {
            String line = scan.nextLine();
            System.out.println(line);
        }

        scan.close(); // 사용 후 닫기
    }
}
```

#### Scanner 주요 메서드

| 메서드 | 설명 | 반환 타입 |
|--------|------|----------|
| `nextInt()` | 다음 정수 읽기 | `int` |
| `nextDouble()` | 다음 실수 읽기 | `double` |
| `nextBoolean()` | 다음 boolean 읽기 | `boolean` |
| `next()` | 다음 토큰(공백 기준) 읽기 | `String` |
| `nextLine()` | 다음 줄 전체 읽기 | `String` |
| `hasNext()` | 읽을 토큰이 남았는가? | `boolean` |
| `close()` | Scanner 닫기 | `void` |

> ⚠️ **2025-26 CED 주의**: Java Quick Reference에는 **`hasNext()`만** 등재되어 있다. `hasNextInt()`, `hasNextLine()`, `hasNextDouble()` 등은 시험에 출제되지 않으므로, 파일 끝까지 읽을 때는 항상 `while (scan.hasNext())` 패턴을 사용한다.

#### 파일 전체 읽기 패턴

```java
// 줄 단위 읽기
public static void main(String[] args) throws IOException {
    Scanner scan = new Scanner(new File("students.txt"));

    while (scan.hasNext()) {
        String line = scan.nextLine();
        System.out.println(line);
    }
    scan.close();
}

// 토큰 단위 읽기 (공백/줄바꿈 기준)
public static void main(String[] args) throws IOException {
    Scanner scan = new Scanner(new File("numbers.txt"));
    int sum = 0;

    while (scan.hasNext()) {
        sum += scan.nextInt();
    }
    scan.close();
    System.out.println("합계: " + sum);
}
```

#### String의 split 메서드

```java
// CSV(쉼표로 구분된 값) 파일 처리
// data.txt 내용:
// Alice,90,A
// Bob,75,B

Scanner scan = new Scanner(new File("data.txt"));
while (scan.hasNext()) {
    String line = scan.nextLine();
    String[] parts = line.split(","); // 쉼표로 분할
    String name = parts[0];          // "Alice"
    int score = Integer.parseInt(parts[1]); // 90
    String grade = parts[2];         // "A"
    System.out.println(name + ": " + score);
}
scan.close();
```

#### 파일 데이터를 배열/ArrayList에 저장

```java
// 파일의 숫자들을 ArrayList에 저장
public static void main(String[] args) throws IOException {
    Scanner scan = new Scanner(new File("scores.txt"));
    ArrayList<Integer> scores = new ArrayList<>();

    while (scan.hasNext()) {
        scores.add(scan.nextInt());
    }
    scan.close();

    // 이제 ArrayList 알고리즘으로 처리
    int max = scores.get(0);
    for (int s : scores) {
        if (s > max) max = s;
    }
    System.out.println("최고 점수: " + max);
}
```

### 시험 포인트

- **`throws IOException`** 빠뜨리면 컴파일 에러
- `new Scanner(new File("filename"))` 패턴 암기
- `while(scan.hasNext())` 패턴 (Quick Reference에 `hasNextInt`/`hasNextLine` 없음)
- `split()`은 String 메서드, 구분자를 받아 String 배열 반환
- `Integer.parseInt()`, `Double.parseDouble()`로 문자열→숫자 변환
- **시험 범위 밖**: 키보드 입력용 Scanner, nextLine과 다른 메서드 혼용 문제, 정규표현식

### 연습문제

```java
// data.txt 내용:
// 10 20 30
// 40 50

// 이 코드의 출력은?
Scanner scan = new Scanner(new File("data.txt"));
int total = 0;
while (scan.hasNext()) {
    total += scan.nextInt();
}
System.out.println(total); // 출력: ?
```

> 정답: `150` (10+20+30+40+50, nextInt는 줄바꿈과 상관없이 정수를 읽음)

---

## 4.7 Wrapper Classes (1기간)

### 핵심 개념

- **Wrapper Class**: primitive 타입을 객체로 감싸는 클래스
- `int` → `Integer`, `double` → `Double`
- ArrayList는 primitive를 저장할 수 없으므로 Wrapper 필요

```java
// Autoboxing: primitive → Wrapper (자동 변환)
Integer num = 42;        // int 42가 자동으로 Integer 객체로
ArrayList<Integer> list = new ArrayList<>();
list.add(10);            // int 10이 자동으로 Integer로 autoboxing

// Unboxing: Wrapper → primitive (자동 변환)
int x = num;             // Integer가 자동으로 int로
int y = list.get(0);     // Integer가 자동으로 int로 unboxing
```

#### 문자열 ↔ 숫자 변환

```java
// String → int/double
int n = Integer.parseInt("42");       // 42
double d = Double.parseDouble("3.14"); // 3.14

// int/double → String
String s1 = Integer.toString(42);     // "42"
String s2 = "" + 42;                  // "42" (간단한 방법)
```

### 시험 포인트

- **Integer와 Double은 immutable** (불변 객체)
- `Integer.MAX_VALUE`, `Integer.MIN_VALUE` 상수
- Autoboxing/Unboxing은 자동이지만 **`null` Unboxing은 NullPointerException**
- `ArrayList<int>` ❌ → `ArrayList<Integer>` ✅

### 연습문제

```java
ArrayList<Integer> nums = new ArrayList<>();
nums.add(5);           // autoboxing
nums.add(10);
int sum = nums.get(0) + nums.get(1); // unboxing
System.out.println(sum); // 출력: ?
```

> 정답: `15`

---

## 4.8 ArrayList Methods (3기간)

> **배열 vs ArrayList**: 배열은 **고정 크기 아파트**(입주 후 방 수 변경 불가), ArrayList는 **확장 가능한 호텔**(손님이 늘면 방을 추가할 수 있다). 크기가 변해야 할 때 ArrayList를 쓴다.

### 핵심 개념

ArrayList는 **가변 크기** 리스트로, 객체만 저장한다.

```java
import java.util.ArrayList;

// 생성
ArrayList<String> names = new ArrayList<>();  // 빈 리스트
ArrayList<Integer> nums = new ArrayList<>();

// 주요 메서드
names.add("Alice");          // 끝에 추가       → ["Alice"]
names.add("Bob");            // 끝에 추가       → ["Alice", "Bob"]
names.add(1, "Charlie");     // 인덱스 1에 삽입 → ["Alice", "Charlie", "Bob"]

names.size();                // 3 (length가 아님!)
names.get(0);                // "Alice"
names.set(0, "Amy");         // 인덱스 0을 교체 → ["Amy", "Charlie", "Bob"]
names.remove(1);             // 인덱스 1 제거   → ["Amy", "Bob"]
```

### 메서드 정리

| 메서드 | 설명 | 반환 |
|--------|------|------|
| `size()` | 원소 개수 | `int` |
| `add(E obj)` | 끝에 추가 | `boolean` (항상 true) |
| `add(int idx, E obj)` | idx 위치에 삽입 (뒤로 밀림) | `void` |
| `get(int idx)` | idx 원소 반환 | `E` |
| `set(int idx, E obj)` | idx 원소 교체, 이전 값 반환 | `E` |
| `remove(int idx)` | idx 원소 제거 (앞으로 당겨짐), 제거된 값 반환 | `E` |

### Array vs ArrayList 비교

| 특성 | Array | ArrayList |
|------|-------|-----------|
| 크기 | 고정 | 가변 |
| 타입 | primitive + 객체 | 객체만 (Wrapper 필요) |
| 길이 | `.length` (필드) | `.size()` (메서드) |
| 접근 | `arr[i]` | `list.get(i)` |
| 수정 | `arr[i] = val` | `list.set(i, val)` |
| 선언 | `int[] arr` | `ArrayList<Integer> list` |

### 시험 포인트

- `size()` 괄호 있음! (Array의 `length`는 괄호 없음)
- `add(index, obj)`: 삽입 후 뒤 원소들이 한 칸씩 밀림
- `remove(index)`: 제거 후 뒤 원소들이 한 칸씩 당겨짐
- 인덱스 범위: `0` ~ `size() - 1`
- `remove()`는 **제거된 객체를 반환**함
- `set()`은 **이전 객체를 반환**함

### 연습문제

```java
ArrayList<String> list = new ArrayList<>();
list.add("A");  // ["A"]
list.add("B");  // ["A", "B"]
list.add("C");  // ["A", "B", "C"]
list.add(1, "D"); // ["A", "D", "B", "C"]
list.set(2, "E"); // ["A", "D", "E", "C"]
list.remove(0);   // ["D", "E", "C"]
System.out.println(list.get(1)); // 출력: ?
```

> 정답: `"E"`

---

## 4.9 ArrayList Traversals (3기간)

### 핵심 개념

#### Indexed for loop

```java
ArrayList<String> names = new ArrayList<>();
names.add("Alice"); names.add("Bob"); names.add("Charlie");

for (int i = 0; i < names.size(); i++) {
    System.out.println(names.get(i));
}
```

#### Enhanced for loop

```java
for (String name : names) {
    System.out.println(name);
}
```

### 핵심 함정: 탐색 중 삭제

```java
// ❌ 잘못된 삭제 — 원소를 건너뜀!
ArrayList<Integer> nums = new ArrayList<>();
nums.add(1); nums.add(2); nums.add(2); nums.add(3);

for (int i = 0; i < nums.size(); i++) {
    if (nums.get(i) == 2) {
        nums.remove(i);
        // i=1에서 첫 번째 2 삭제 → 두 번째 2가 인덱스 1로 당겨짐
        // i=2로 넘어가서 두 번째 2를 건너뜀!
    }
}
// 결과: [1, 2, 3] — 두 번째 2가 남아있음!
```

#### 해결법 1: 삭제 시 i-- (가장 직관적)

```java
for (int i = 0; i < nums.size(); i++) {
    if (nums.get(i) == 2) {
        nums.remove(i);
        i--; // 삭제 후 인덱스 보정
    }
}
```

#### 해결법 2: 뒤에서 앞으로 탐색 (가장 안전)

```java
for (int i = nums.size() - 1; i >= 0; i--) {
    if (nums.get(i) == 2) {
        nums.remove(i); // 뒤에서 삭제하면 앞 인덱스에 영향 없음
    }
}
```

#### Enhanced for에서 add/remove → ConcurrentModificationException!

```java
// ❌ 런타임 에러!
for (String name : names) {
    if (name.equals("Bob")) {
        names.remove(name); // ConcurrentModificationException!
    }
}
```

### 시험 포인트

- 삭제 중 탐색은 **FRQ 단골 출제** (Q3)
- 뒤에서 앞으로 탐색이 가장 깔끔한 해결법
- enhanced for에서 리스트 구조 변경(add/remove) 절대 금지
- `IndexOutOfBoundsException`: size() 이상의 인덱스 접근 시
- 삽입(add) 중 탐색도 유사한 인덱스 문제 발생

### 연습문제

```java
ArrayList<Integer> list = new ArrayList<>();
list.add(1); list.add(2); list.add(2); list.add(3); list.add(5);

for (int i = 0; i < list.size(); i++) {
    if (list.get(i) == 2) {
        list.remove(i);
    }
}
System.out.println(list); // 출력: ?
```

> 정답: `[1, 2, 3, 5]` — 연속된 2 중 하나가 건너뛰어져서 남아있음!
> 추적: i=0: get(0)=1, skip. i=1: get(1)=2, remove(1)→[1,2,3,5], size=4. i=2: get(2)=3, skip. i=3: get(3)=5, skip. → **두 번째 2가 살아남음!**
> 해결: i-- 추가하거나 뒤에서 앞으로 순회

---

## 4.10 Implementing ArrayList Algorithms (4기간)

### 핵심 개념

Array 알고리즘(4.5)과 동일하지만 ArrayList 메서드를 사용하며, **삽입/삭제가 추가**됨.

#### 조건에 맞는 원소 제거 (필터링)

```java
// 60점 미만 제거
ArrayList<Integer> scores = new ArrayList<>();
scores.add(85); scores.add(42); scores.add(91); scores.add(55); scores.add(78);

for (int i = scores.size() - 1; i >= 0; i--) {
    if (scores.get(i) < 60) {
        scores.remove(i);
    }
}
// 결과: [85, 91, 78]
```

#### 조건에 맞는 원소만 새 리스트로

```java
ArrayList<String> original = new ArrayList<>();
original.add("apple"); original.add("banana"); original.add("avocado"); original.add("cherry");

ArrayList<String> filtered = new ArrayList<>();
for (String s : original) {
    if (s.substring(0, 1).equals("a")) {  // startsWith는 Quick Reference에 없음 → substring + equals
        filtered.add(s);
    }
}
// filtered: ["apple", "avocado"]
```

#### 여러 리스트 동시 탐색

```java
// 이름과 점수를 병렬 리스트로 관리
ArrayList<String> names = new ArrayList<>();
ArrayList<Integer> scores = new ArrayList<>();
names.add("Alice"); scores.add(90);
names.add("Bob");   scores.add(75);
names.add("Charlie"); scores.add(88);

// 최고 점수 학생 찾기
int maxIdx = 0;
for (int i = 1; i < scores.size(); i++) {
    if (scores.get(i) > scores.get(maxIdx)) {
        maxIdx = i;
    }
}
System.out.println(names.get(maxIdx) + ": " + scores.get(maxIdx));
// Alice: 90
```

#### ArrayList와 Array 간 변환

```java
// Array → ArrayList
String[] arr = {"A", "B", "C"};
ArrayList<String> list = new ArrayList<>();
for (String s : arr) {
    list.add(s);
}

// ArrayList → Array (수동)
String[] arr2 = new String[list.size()];
for (int i = 0; i < list.size(); i++) {
    arr2[i] = list.get(i);
}
```

### 시험 포인트

- FRQ Q3에서 가장 빈출: 조건부 삭제, 필터링, 변환
- 삭제 루프는 반드시 뒤에서 앞으로 또는 i-- 패턴 사용
- 여러 리스트의 병렬 인덱스 활용 문제 자주 출제
- String 비교는 항상 `.equals()` 사용 (== 아님!)

### 연습문제

```java
// "e"를 포함하는 단어를 제거하시오
ArrayList<String> words = new ArrayList<>();
words.add("hello"); words.add("world"); words.add("test"); words.add("java");

// 코드를 작성하세요
```

> 정답:
> ```java
> for (int i = words.size() - 1; i >= 0; i--) {
>     if (words.get(i).indexOf("e") >= 0) {
>         words.remove(i);
>     }
> }
> // 결과: ["world", "java"]
> ```

---

## 4.11 2D Array Creation and Access (2기간)

### 핵심 개념

2D 배열은 "배열의 배열" — 행(row)과 열(column)로 구성된 격자(grid)이다.

```java
// 선언과 생성 (3행 4열, 기본값 0)
int[][] grid = new int[3][4];

// 선언과 초기화
int[][] grid = {
    {1, 2, 3, 4},    // row 0
    {5, 6, 7, 8},    // row 1
    {9, 10, 11, 12}  // row 2
};

// 접근
grid[0][0] = 100;   // 0행 0열에 100 대입
int val = grid[1][2]; // 1행 2열 값 = 7

// 크기
int rows = grid.length;      // 행 수 = 3
int cols = grid[0].length;   // 열 수 = 4
```

### 메모리 구조 이해

```
grid → [ row0 참조 ] → [1, 2, 3, 4]
       [ row1 참조 ] → [5, 6, 7, 8]
       [ row2 참조 ] → [9, 10, 11, 12]

grid.length = 3 (행 수 = 외부 배열의 길이)
grid[0].length = 4 (열 수 = 내부 배열의 길이)
```

### 시험 포인트

- `arr.length` = **행 수**, `arr[0].length` = **열 수** — 절대 혼동 금지!
- `arr[row][col]` 순서: 행 먼저, 열 나중
- 비정방(jagged) 2D 배열은 **시험 범위 아님** (EXCLUSION)
- `new int[3][4]`에서 3이 행, 4가 열

### 연습문제

```java
int[][] m = {
    {1, 2, 3},
    {4, 5, 6}
};
System.out.println(m.length);      // 출력: ?
System.out.println(m[0].length);   // 출력: ?
System.out.println(m[1][2]);       // 출력: ?
```

> 정답: `2`, `3`, `6`

---

## 4.12 2D Array Traversals (3기간)

### 핵심 개념

#### Row-major 순회 (행 우선 — 가장 일반적)

```java
int[][] grid = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// 외부 루프 = 행, 내부 루프 = 열
for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[0].length; c++) {
        System.out.print(grid[r][c] + " ");
    }
    System.out.println();
}
// 출력: 1 2 3
//       4 5 6
//       7 8 9
```

#### Column-major 순회 (열 우선)

```java
// 외부 루프 = 열, 내부 루프 = 행
for (int c = 0; c < grid[0].length; c++) {
    for (int r = 0; r < grid.length; r++) {
        System.out.print(grid[r][c] + " ");
    }
    System.out.println();
}
// 출력: 1 4 7
//       2 5 8
//       3 6 9
```

#### Enhanced for로 2D 배열 순회

```java
// row는 1D 배열(int[])의 참조
for (int[] row : grid) {
    for (int val : row) {
        System.out.print(val + " ");
    }
    System.out.println();
}
```

### 시험 포인트

- **Row-major**: 외부 행, 내부 열 → 가로로 읽기 (1,2,3,4,5,6,7,8,9)
- **Column-major**: 외부 열, 내부 행 → 세로로 읽기 (1,4,7,2,5,8,3,6,9)
- MCQ에서 "다음 코드가 출력하는 순서는?" 형태 빈출
- enhanced for에서 외부 변수는 `int[]` 타입임을 기억

### 연습문제

```java
int[][] arr = {{1, 2}, {3, 4}, {5, 6}};
int sum = 0;
for (int c = 0; c < arr[0].length; c++) {
    for (int r = 0; r < arr.length; r++) {
        sum += arr[r][c];
    }
}
System.out.println(sum); // 출력: ?
```

> 정답: `21` (1+3+5+2+4+6, column-major이지만 합은 같음)

```java
// 이 코드가 방문하는 순서는?
int[][] m = {{1, 2, 3}, {4, 5, 6}};
for (int c = 0; c < m[0].length; c++) {
    for (int r = 0; r < m.length; r++) {
        System.out.print(m[r][c] + " ");
    }
}
```

> 정답: `1 4 2 5 3 6` (column-major: 열 0→행0,1 / 열 1→행0,1 / 열 2→행0,1)

---

## 4.13 Implementing 2D Array Algorithms (4기간)

### 표준 알고리즘

#### 1. 전체 합계/평균

```java
int[][] grid = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
int sum = 0;
int count = 0;
for (int[] row : grid) {
    for (int val : row) {
        sum += val;
        count++;
    }
}
double avg = (double) sum / count;
// sum = 45, count = 9, avg = 5.0
```

#### 2. 특정 행/열의 합

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

#### 3. 대각선 합 (정방 행렬)

```java
// 주대각선 (좌상→우하)
int diagSum = 0;
for (int i = 0; i < grid.length; i++) {
    diagSum += grid[i][i];
}
// diagSum = 1+5+9 = 15

// 반대각선 (우상→좌하)
int antiDiagSum = 0;
int n = grid.length;
for (int i = 0; i < n; i++) {
    antiDiagSum += grid[i][n - 1 - i];
}
// antiDiagSum = 3+5+7 = 15
```

#### 4. 최대값의 위치 찾기

```java
int[][] grid = {{3, 7, 1}, {9, 2, 8}, {4, 6, 5}};
int maxVal = grid[0][0];
int maxRow = 0, maxCol = 0;

for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[0].length; c++) {
        if (grid[r][c] > maxVal) {
            maxVal = grid[r][c];
            maxRow = r;
            maxCol = c;
        }
    }
}
System.out.println("최대값 " + maxVal + " 위치: [" + maxRow + "][" + maxCol + "]");
// 최대값 9 위치: [1][0]
```

#### 5. 조건 만족 원소 개수

```java
// 짝수 개수 세기
int count = 0;
for (int[] row : grid) {
    for (int val : row) {
        if (val % 2 == 0) count++;
    }
}
```

#### 6. 행/열 뒤집기 (Reverse a row)

```java
// 특정 행 뒤집기
int row = 1; // 행 1을 뒤집기
for (int i = 0; i < grid[row].length / 2; i++) {
    int temp = grid[row][i];
    grid[row][i] = grid[row][grid[row].length - 1 - i];
    grid[row][grid[row].length - 1 - i] = temp;
}
```

#### 7. 인접 원소 확인 (상하좌우)

```java
// (r, c) 주변의 유효한 이웃 탐색
int r = 1, c = 1;
int[][] dirs = {{-1,0}, {1,0}, {0,-1}, {0,1}}; // 상, 하, 좌, 우
for (int[] d : dirs) {
    int nr = r + d[0];
    int nc = c + d[1];
    if (nr >= 0 && nr < grid.length && nc >= 0 && nc < grid[0].length) {
        System.out.println("이웃: " + grid[nr][nc]);
    }
}
```

### 시험 포인트

- FRQ Q4에서 2D 배열 알고리즘 직접 출제
- 행/열 혼동이 가장 흔한 실수 (`grid.length` vs `grid[0].length`)
- 경계 검사(boundary check) 빠뜨리면 ArrayIndexOutOfBoundsException
- "특정 부분만 탐색" 문제 주의 (예: 대각선, 테두리 등)

### 연습문제

```java
int[][] m = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
int result = 0;
for (int r = 0; r < m.length; r++) {
    result += m[r][r];
}
System.out.println(result); // 출력: ?
```

> 정답: `15` (대각선 합: 1+5+9)

---

## 4.14 Searching Algorithms (3기간)

### Linear Search (순차 탐색)

배열을 처음부터 끝까지 하나씩 확인한다.

```java
// 배열에서 target의 인덱스를 반환 (없으면 -1)
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) {
            return i;
        }
    }
    return -1; // 못 찾음
}
```

- **시간 복잡도**: O(n) — 최악의 경우 모든 원소를 확인
- **정렬 필요 없음**
- ArrayList 버전:

```java
public static int linearSearch(ArrayList<Integer> list, int target) {
    for (int i = 0; i < list.size(); i++) {
        if (list.get(i) == target) {
            return i;
        }
    }
    return -1;
}
```

### Binary Search (이진 탐색)

**정렬된 배열에서만** 사용 가능. 중간값과 비교하여 탐색 범위를 절반씩 줄인다.

```java
// 반복(iterative) 버전
public static int binarySearch(int[] arr, int target) {
    int low = 0;
    int high = arr.length - 1;

    while (low <= high) {
        int mid = (low + high) / 2;

        if (arr[mid] == target) {
            return mid;          // 찾음!
        } else if (arr[mid] < target) {
            low = mid + 1;       // 오른쪽 절반 탐색
        } else {
            high = mid - 1;      // 왼쪽 절반 탐색
        }
    }
    return -1; // 못 찾음
}
```

#### Binary Search 과정 추적 (MCQ 빈출!)

```
arr = {2, 5, 8, 12, 16, 23, 38, 56, 72, 91}
target = 23

Step 1: low=0, high=9, mid=4 → arr[4]=16 < 23 → low=5
Step 2: low=5, high=9, mid=7 → arr[7]=56 > 23 → high=6
Step 3: low=5, high=6, mid=5 → arr[5]=23 == 23 → 찾음! return 5
```

### 비교

| 특성 | Linear Search | Binary Search |
|------|--------------|---------------|
| 시간 복잡도 | O(n) | O(log n) |
| 정렬 필요 | 아니오 | **예** |
| 원소 10개 최악 비교 횟수 | 10 | 4 (log₂10 ≈ 3.3) |
| 원소 1000개 최악 비교 횟수 | 1000 | 10 (log₂1000 ≈ 10) |
| 구현 난이도 | 쉬움 | 보통 |

### 시험 포인트

- Binary search는 **정렬된 배열에서만!** 정렬 안 되어 있으면 결과 보장 안 됨
- MCQ에서 "몇 번 비교하는가?" 유형 빈출
- `(low + high) / 2`에서 정수 나눗셈 기억
- 비교 횟수 계산: n개 원소 → 최대 ⌊log₂(n)⌋ + 1번
- Binary search에서 target이 없을 때의 `low`와 `high` 최종 값 추적 가능해야 함

### 연습문제

```java
int[] arr = {3, 7, 11, 15, 19, 23, 27};
// binary search로 15를 찾을 때, 비교되는 원소들의 순서는?
```

> 정답:
> 1. mid = 3 → arr[3] = 15 → 찾음!
> 비교 1번만에 찾음 (운 좋게 중간값이 target)

```java
int[] arr = {3, 7, 11, 15, 19, 23, 27};
// binary search로 20을 찾을 때의 과정은?
```

> 정답:
> 1. low=0, high=6, mid=3 → arr[3]=15 < 20 → low=4
> 2. low=4, high=6, mid=5 → arr[5]=23 > 20 → high=4
> 3. low=4, high=4, mid=4 → arr[4]=19 < 20 → low=5
> 4. low=5 > high=4 → 종료, return -1

---

## 4.15 Sorting Algorithms (3기간)

### Selection Sort (선택 정렬)

**아이디어**: 가장 작은 원소를 찾아 앞으로 보낸다.

```java
public static void selectionSort(int[] arr) {
    for (int i = 0; i < arr.length - 1; i++) {
        int minIdx = i;
        for (int j = i + 1; j < arr.length; j++) {
            if (arr[j] < arr[minIdx]) {
                minIdx = j;
            }
        }
        // swap arr[i]와 arr[minIdx]
        int temp = arr[i];
        arr[i] = arr[minIdx];
        arr[minIdx] = temp;
    }
}
```

#### 과정 추적

```
원본: [64, 25, 12, 22, 11]
Pass 1: 최소=11(idx 4) → swap(0,4) → [11, 25, 12, 22, 64]
Pass 2: 최소=12(idx 2) → swap(1,2) → [11, 12, 25, 22, 64]
Pass 3: 최소=22(idx 3) → swap(2,3) → [11, 12, 22, 25, 64]
Pass 4: 최소=25(idx 3) → swap(3,3) → [11, 12, 22, 25, 64]
```

### Insertion Sort (삽입 정렬)

**아이디어**: 정렬된 부분에 새 원소를 올바른 위치에 삽입한다.

```java
public static void insertionSort(int[] arr) {
    for (int i = 1; i < arr.length; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j]; // 한 칸씩 오른쪽으로 밀기
            j--;
        }
        arr[j + 1] = key; // 빈 자리에 삽입
    }
}
```

#### 과정 추적

```
원본: [64, 25, 12, 22, 11]
Pass 1: key=25, 64>25 → shift → [25, 64, 12, 22, 11] (삽입위치 0)
                                  [25, 64, 12, 22, 11]
Pass 2: key=12, 64>12, 25>12 → [12, 25, 64, 22, 11]
Pass 3: key=22, 64>22, 25>22 → [12, 22, 25, 64, 11]
Pass 4: key=11, 64>11, 25>11, 22>11, 12>11 → [11, 12, 22, 25, 64]
```

### Merge Sort (병합 정렬)

**아이디어**: 배열을 반씩 나누고(분할), 각각 정렬한 뒤, 합친다(병합). 재귀적.

```java
public static void mergeSort(int[] arr, int left, int right) {
    if (left < right) {
        int mid = (left + right) / 2;
        mergeSort(arr, left, mid);       // 왼쪽 반 정렬
        mergeSort(arr, mid + 1, right);  // 오른쪽 반 정렬
        merge(arr, left, mid, right);    // 병합
    }
}

public static void merge(int[] arr, int left, int mid, int right) {
    // 임시 배열에 복사
    int[] temp = new int[right - left + 1];
    int i = left;       // 왼쪽 포인터
    int j = mid + 1;    // 오른쪽 포인터
    int k = 0;          // temp 포인터

    while (i <= mid && j <= right) {
        if (arr[i] <= arr[j]) {
            temp[k++] = arr[i++];
        } else {
            temp[k++] = arr[j++];
        }
    }
    while (i <= mid) temp[k++] = arr[i++];
    while (j <= right) temp[k++] = arr[j++];

    // temp를 원본에 복사
    for (int t = 0; t < temp.length; t++) {
        arr[left + t] = temp[t];
    }
}

// 호출: mergeSort(arr, 0, arr.length - 1);
```

#### 과정 추적

```
[38, 27, 43, 3, 9, 82, 10]
     /                    \
[38, 27, 43]         [3, 9, 82, 10]
   /      \              /        \
[38]   [27, 43]      [3, 9]    [82, 10]
        /    \         /  \      /    \
      [27]  [43]     [3] [9]  [82]  [10]
        \    /         \  /      \    /
      [27, 43]        [3, 9]   [10, 82]
   \      /              \        /
[27, 38, 43]         [3, 9, 10, 82]
     \                    /
[3, 9, 10, 27, 38, 43, 82]
```

### 정렬 알고리즘 비교

| 특성 | Selection Sort | Insertion Sort | Merge Sort |
|------|---------------|---------------|------------|
| 시간 복잡도 (최악) | O(n²) | O(n²) | O(n log n) |
| 시간 복잡도 (최선) | O(n²) | **O(n)** (이미 정렬) | O(n log n) |
| 공간 복잡도 | O(1) | O(1) | O(n) (임시 배열) |
| 안정성(Stable) | 아니오 | 예 | 예 |
| 특징 | 항상 같은 횟수 비교 | 거의 정렬된 데이터에 빠름 | 항상 빠르지만 메모리 추가 |

### 시험 포인트

- 각 정렬의 **pass별 배열 상태**를 추적할 수 있어야 함 (MCQ 빈출!)
- Selection Sort: "i번째 pass 후 앞 i+1개가 정렬됨"
- Insertion Sort: "i번째 pass 후 앞 i+1개가 (서로 간에) 정렬됨"
- Merge Sort: 재귀 호출 순서와 merge 과정 이해
- O(n²) vs O(n log n) 비교 문제

### 연습문제

```java
// Selection Sort로 {5, 3, 8, 1, 4}를 정렬할 때,
// 2번째 pass(i=1) 완료 후 배열 상태는?
```

> 정답:
> Pass 0: 최소=1(idx 3) → swap(0,3) → [1, 3, 8, 5, 4]
> Pass 1: 최소=3(idx 1) → swap(1,1) → [1, 3, 8, 5, 4]
> 2번째 pass 완료 후: `[1, 3, 8, 5, 4]`

```java
// Insertion Sort로 {5, 3, 8, 1, 4}를 정렬할 때,
// 3번째 pass(i=3) 완료 후 배열 상태는?
```

> 정답:
> Pass 1(i=1): key=3, 5>3 → [3, 5, 8, 1, 4]
> Pass 2(i=2): key=8, 5<8 → [3, 5, 8, 1, 4] (이동 없음)
> Pass 3(i=3): key=1, 8>1, 5>1, 3>1 → [1, 3, 5, 8, 4]

> **EXCLUSION**: `Arrays.sort()`와 `Collections.sort()` 같은 Java 내장 정렬 메서드는 AP 시험에서 사용할 수 없다. FRQ에서는 직접 정렬 알고리즘을 구현하거나, 문제에서 제공하는 헬퍼 메서드를 사용해야 한다.

---

## 4.16 Recursion (3기간)

> **중요: 2025-26 CED에서 재귀는 MCQ 트레이싱(코드 추적)에서만 출제됩니다. 재귀 메서드를 직접 작성하는 것은 시험 범위 밖입니다. FRQ에서는 절대 재귀를 요구하지 않습니다. 아래 코드들은 "읽고 추적하는 연습"용이지 "작성 암기"용이 아닙니다.**

### 핵심 개념

재귀(Recursion)는 메서드가 **자기 자신을 호출**하는 기법이다.

#### 재귀의 두 요소

1. **Base case** (기저 조건): 재귀를 멈추는 조건. 없으면 무한 루프 → StackOverflowError
2. **Recursive case** (재귀 조건): 자기 자신을 호출하되, **문제를 더 작게** 만들어야 함

#### 기본 예제: 팩토리얼

```java
public static int factorial(int n) {
    if (n == 0 || n == 1) {  // Base case
        return 1;
    }
    return n * factorial(n - 1);  // Recursive case
}

// factorial(4) 추적:
// factorial(4) = 4 * factorial(3)
//              = 4 * 3 * factorial(2)
//              = 4 * 3 * 2 * factorial(1)
//              = 4 * 3 * 2 * 1
//              = 24
```

#### 거듭제곱

```java
public static int power(int base, int exp) {
    if (exp == 0) return 1;            // Base case
    return base * power(base, exp - 1); // Recursive case
}

// power(2, 3) = 2 * power(2, 2) = 2 * 2 * power(2, 1) = 2 * 2 * 2 * power(2, 0) = 8
```

#### 피보나치 수열

```java
public static int fibonacci(int n) {
    if (n <= 1) return n;  // Base case: fib(0)=0, fib(1)=1
    return fibonacci(n - 1) + fibonacci(n - 2);  // 두 번의 재귀 호출
}

// fibonacci(5) = fibonacci(4) + fibonacci(3)
//              = (fib(3) + fib(2)) + (fib(2) + fib(1))
//              = ... = 5
```

#### 문자열 재귀

```java
// 문자열 뒤집기
public static String reverse(String s) {
    if (s.length() <= 1) return s;  // Base case
    return reverse(s.substring(1)) + s.substring(0, 1);  // charAt 대신 substring(0,1) 사용 (Quick Reference 준수)
}

// reverse("hello")
// = reverse("ello") + "h"
// = (reverse("llo") + "e") + "h"
// = ((reverse("lo") + "l") + "e") + "h"
// = (((reverse("o") + "l") + "l") + "e") + "h"
// = ((("o" + "l") + "l") + "e") + "h"
// = "olleh"
```

#### 합계 재귀

```java
public static int sumArray(int[] arr, int index) {
    if (index == arr.length) return 0;  // Base case
    return arr[index] + sumArray(arr, index + 1);
}

// sumArray({3, 7, 2}, 0)
// = 3 + sumArray({3,7,2}, 1)
// = 3 + 7 + sumArray({3,7,2}, 2)
// = 3 + 7 + 2 + sumArray({3,7,2}, 3)
// = 3 + 7 + 2 + 0 = 12
```

### 시험 포인트

- **MCQ에서만 출제 (FRQ 아님!)**
- 코드 tracing으로 결과 예측하는 문제가 대부분
- Base case 누락 → StackOverflowError
- 재귀 호출마다 문제가 작아지는지 확인 (그렇지 않으면 무한 재귀)
- "이 코드의 출력은?" 또는 "f(5)의 반환값은?" 유형

### 연습문제

```java
public static int mystery(int n) {
    if (n == 0) return 1;
    if (n == 1) return 1;
    return mystery(n - 1) + mystery(n - 2);
}
System.out.println(mystery(6)); // 출력: ?
```

> 정답: `13` (피보나치: 1, 1, 2, 3, 5, 8, 13)

```java
public static String mystery2(String s) {
    if (s.length() == 0) return "";
    return mystery2(s.substring(1)) + s.substring(0, 1);
}
System.out.println(mystery2("ABCD")); // 출력: ?
```

> 정답: `"DCBA"` (문자열 뒤집기)

```java
public static int mystery3(int a, int b) {
    if (b == 0) return 0;
    return a + mystery3(a, b - 1);
}
System.out.println(mystery3(3, 4)); // 출력: ?
```

> 정답: `12` (3 * 4 = 12, 재귀로 곱셈 구현)

---

## 4.17 Recursive Searching and Sorting (2기간)

### Binary Search의 재귀 버전

```java
public static int binarySearchRecursive(int[] arr, int target, int low, int high) {
    if (low > high) return -1;  // Base case: 못 찾음

    int mid = (low + high) / 2;

    if (arr[mid] == target) {
        return mid;  // Base case: 찾음!
    } else if (arr[mid] < target) {
        return binarySearchRecursive(arr, target, mid + 1, high);  // 오른쪽
    } else {
        return binarySearchRecursive(arr, target, low, mid - 1);   // 왼쪽
    }
}

// 호출: binarySearchRecursive(arr, target, 0, arr.length - 1);
```

#### 반복 vs 재귀 Binary Search

```
반복 버전: while 루프로 low, high 갱신
재귀 버전: 매 호출마다 low 또는 high가 좁혀짐 → 범위가 작아지는 것이 "문제를 작게 만드는 것"

둘 다 O(log n) 시간 복잡도
```

### Merge Sort의 재귀 구조 (복습)

```java
// Merge Sort는 본질적으로 재귀 알고리즘
public static void mergeSort(int[] arr, int left, int right) {
    if (left >= right) return;  // Base case: 크기 0 또는 1

    int mid = (left + right) / 2;
    mergeSort(arr, left, mid);       // 왼쪽 절반 재귀 정렬
    mergeSort(arr, mid + 1, right);  // 오른쪽 절반 재귀 정렬
    merge(arr, left, mid, right);    // 병합
}
```

#### Merge Sort 재귀 호출 순서 추적

```
mergeSort([5, 3, 8, 1], 0, 3)
├── mergeSort([5, 3, 8, 1], 0, 1)    -- 왼쪽 절반
│   ├── mergeSort([5, 3, 8, 1], 0, 0)    -- base case (크기 1)
│   ├── mergeSort([5, 3, 8, 1], 1, 1)    -- base case (크기 1)
│   └── merge: [5, 3] → [3, 5]
├── mergeSort([3, 5, 8, 1], 2, 3)    -- 오른쪽 절반
│   ├── mergeSort([3, 5, 8, 1], 2, 2)    -- base case
│   ├── mergeSort([3, 5, 8, 1], 3, 3)    -- base case
│   └── merge: [8, 1] → [1, 8]
└── merge: [3, 5] + [1, 8] → [1, 3, 5, 8]
```

### 시험 포인트

- 재귀 Binary Search: 매개변수로 `low`, `high` 전달 (범위 축소)
- Merge Sort: "왼쪽 먼저 끝까지 분할 → 병합 → 오른쪽 분할 → 병합 → 전체 병합" 순서
- 재귀 호출 트리를 그릴 수 있어야 MCQ 풀 수 있음
- FRQ에서는 출제 안 됨 (MCQ only)

### 연습문제

```java
int[] arr = {2, 5, 8, 12, 16, 23, 38};
// binarySearchRecursive(arr, 8, 0, 6) 호출 시 재귀 과정은?
```

> 정답:
> 1. low=0, high=6, mid=3 → arr[3]=12 > 8 → 왼쪽: (arr, 8, 0, 2)
> 2. low=0, high=2, mid=1 → arr[1]=5 < 8 → 오른쪽: (arr, 8, 2, 2)
> 3. low=2, high=2, mid=2 → arr[2]=8 == 8 → return 2

---

## FRQ 대비 전략

### Q3: ArrayList (매년 출제)

**빈출 패턴**:
- 조건에 맞는 원소 삭제/수정/이동
- 두 ArrayList 결합 또는 비교
- 클래스 내부의 ArrayList 필드 조작

**핵심 실수 방지**:

```java
// ★ 삭제 루프는 반드시 뒤에서 앞으로!
for (int i = list.size() - 1; i >= 0; i--) {
    if (조건) {
        list.remove(i);
    }
}

// ★ String 비교는 .equals()
if (list.get(i).equals("target")) { ... }

// ★ remove(index)와 remove(Object) 혼동 주의
ArrayList<Integer> nums = new ArrayList<>();
nums.add(1); nums.add(2); nums.add(3);
nums.remove(1);   // 인덱스 1의 원소(2) 제거 → [1, 3]
// 값 2를 제거하려면:
nums.remove(Integer.valueOf(2));
```

**실전 연습**:

```java
// 문제: temperatures 리스트에서 평균 이하 온도를 모두 제거하시오
public void removeBelowAverage(ArrayList<Double> temperatures) {
    double sum = 0;
    for (double t : temperatures) {
        sum += t;
    }
    double avg = sum / temperatures.size();

    for (int i = temperatures.size() - 1; i >= 0; i--) {
        if (temperatures.get(i) <= avg) {
            temperatures.remove(i);
        }
    }
}
```

### Q4: 2D Array (매년 출제)

**빈출 패턴**:
- 특정 행/열/영역 탐색
- 조건에 맞는 위치 찾기
- 2D 배열 변환 (회전, 전치 등)

**핵심 실수 방지**:

```java
// ★ 행과 열 순서 혼동 방지
for (int r = 0; r < grid.length; r++) {         // 행
    for (int c = 0; c < grid[0].length; c++) {   // 열
        // grid[r][c]
    }
}

// ★ 경계 체크 잊지 말기
if (r >= 0 && r < grid.length && c >= 0 && c < grid[0].length) {
    // 안전하게 접근
}
```

**실전 연습**:

```java
// 문제: 2D 배열에서 각 행의 최대값을 1D 배열로 반환하시오
public static int[] rowMaxes(int[][] grid) {
    int[] result = new int[grid.length];
    for (int r = 0; r < grid.length; r++) {
        int max = grid[r][0];
        for (int c = 1; c < grid[r].length; c++) {
            if (grid[r][c] > max) {
                max = grid[r][c];
            }
        }
        result[r] = max;
    }
    return result;
}
```

---

## FRQ 실전 연습

### FRQ Q3 스타일: ArrayList 필터링

다음 `StudentList` 클래스에서 `removeBelow` 메서드를 구현하시오. 이 메서드는 `students` 리스트에서 점수가 `minScore` 미만인 학생을 모두 제거한다.

```java
public class StudentList {
    private ArrayList<Student> students;
    
    // Student 클래스에는 다음 메서드가 있다:
    // public String getName() — 학생 이름 반환
    // public int getScore() — 학생 점수 반환
    
    public void removeBelow(int minScore) {
        // 여기에 구현
    }
}
```

Precondition: students는 null이 아니며, 원소도 null이 아님.

<details>
<summary>모범 답안</summary>

```java
public void removeBelow(int minScore) {
    for (int i = students.size() - 1; i >= 0; i--) {
        if (students.get(i).getScore() < minScore) {
            students.remove(i);
        }
    }
}
```

**채점 기준 (5점)**:
1. ArrayList의 모든 원소를 순회 — 1점
2. getScore() 올바르게 호출 — 1점
3. minScore 미만 조건 올바르게 비교 — 1점
4. 조건 충족 원소 삭제 — 1점
5. 삭제 시 인덱스 밀림 올바르게 처리 (역순 또는 i--) — 1점 (algorithm)
</details>

### FRQ Q4 스타일: 2D Array 탐색

다음 `Grid` 클래스에서 `countRowsWithAll` 메서드를 구현하시오. 이 메서드는 2D 배열 `grid`에서 모든 원소가 `target` 값인 행의 수를 반환한다.

```java
public class Grid {
    private int[][] grid;
    
    public int countRowsWithAll(int target) {
        // 여기에 구현
    }
}
```

예: grid = {{1,1,1}, {1,2,1}, {3,3,3}}이고 target=1이면, 첫 번째 행만 모두 1이므로 1을 반환.

<details>
<summary>모범 답안</summary>

```java
public int countRowsWithAll(int target) {
    int count = 0;
    for (int r = 0; r < grid.length; r++) {
        boolean allMatch = true;
        for (int c = 0; c < grid[r].length; c++) {
            if (grid[r][c] != target) {
                allMatch = false;
            }
        }
        if (allMatch) {
            count++;
        }
    }
    return count;
}
```

**채점 기준 (6점)**:
1. 외부 루프가 모든 행을 순회 — 1점
2. 내부 루프가 해당 행의 모든 열을 순회 — 1점
3. grid[r][c]와 target 비교 — 1점
4. 행별 boolean 플래그로 "모두 일치" 판단 — 1점
5. 일치하는 행 카운트 — 1점
6. 전체 알고리즘 정합성 (올바른 반환) — 1점 (algorithm)
</details>

---

## 총정리: 자주 틀리는 포인트 체크리스트

| # | 함정 | 올바른 방법 |
|---|------|------------|
| 1 | `arr.length()` | `arr.length` (배열은 괄호 없음) |
| 2 | `list.length` | `list.size()` (ArrayList는 메서드) |
| 3 | `str.length` | `str.length()` (String은 메서드) |
| 4 | enhanced for에서 배열 수정 | indexed for 사용 |
| 5 | enhanced for에서 list.remove() | ConcurrentModificationException |
| 6 | 삭제 루프를 앞에서 뒤로 | 뒤에서 앞으로 또는 i-- |
| 7 | `==`로 String 비교 | `.equals()` 사용 |
| 8 | 평균 계산에서 정수 나눗셈 | `(double)` 캐스팅 |
| 9 | `arr[arr.length]` 접근 | `arr[arr.length - 1]` |
| 10 | 2D에서 `grid[col][row]` | `grid[row][col]` |
| 11 | Binary search를 정렬 안 된 배열에 | 정렬 후 사용 |
| 12 | `ArrayList<int>` | `ArrayList<Integer>` |
| 13 | 파일 읽기에서 throws 누락 | `throws IOException` 필수 |
| 14 | Scanner 닫기 안 함 | `scan.close()` 호출 |

---

## 시험 비중별 학습 우선순위

1. **최우선** (시험 직접 출제): Array 알고리즘(4.5), ArrayList 알고리즘(4.10), 2D Array 알고리즘(4.13)
2. **높음** (기초 필수): Array 기본(4.3-4.4), ArrayList 기본(4.8-4.9), 2D Array 기본(4.11-4.12)
3. **중요** (MCQ 빈출): Searching(4.14), Sorting(4.15), Recursion(4.16)
4. **보통**: Wrapper(4.7), File I/O(4.6), Recursive Search/Sort(4.17)
5. **낮음** (개념만): Ethics(4.1), Data Sets(4.2)
