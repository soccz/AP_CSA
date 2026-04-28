# Unit 3: Class Creation — 완전정복 딥다이브
## "왜?"로 시작해서 만점으로 끝내는 단 하나의 책

> **이 문서는 누구를 위한 것인가**
> - Java를 처음 보는 사람도 이 한 편을 읽으면 Unit 3의 모든 시험 개념을 **이해**한다.
> - 단순히 "외워라"가 아니라 "왜 이렇게 생겼는가"를 풀어 설명한다.
> - 초등학생에게 설명할 수 있는 비유부터 시작해서, 컴파일러가 실제로 어떻게 동작하는 메커니즘까지 한 줄로 잇는다.
> - 연습 문제 없음. **이해의 깊이**만 끌어올린다.

---

## 0. 시험 지도 — Unit 3는 시험에서 무엇을 의미하는가

### 시험 비중

| 항목 | 비중 |
|-----|------|
| MCQ (42문제 중) | **10-18%** = 약 4-8문제 |
| FRQ Q2 (Class Design) | **7점 만점, 1번 문제 통째로** |
| 전체 시험 점수 기여 | 약 **20-25%** |

### Unit 3가 시험에서 차지하는 진짜 무게

MCQ 비중만 보면 작아 보인다. 그러나:

1. **FRQ Q2가 매년 100% Class Design 문제로 출제**된다. 7점 짜리 문제 하나를 통째로 Unit 3 지식으로 푼다.
2. Unit 4(데이터 컬렉션)의 모든 코드는 Unit 3의 클래스 위에 만들어진다. **Unit 3를 모르면 Unit 4도 무너진다.** (참고: 2025-26 CED는 Unit 1~4 총 4개로 구성. 이전 버전에 있던 상속·다형성 단원은 시험 범위에서 제외되었다.)
3. AP CSA가 측정하려는 핵심 능력 = "객체 지향 설계". Unit 3가 그 핵심.

> **결론**: Unit 3는 "시험 비중 작아서 후순위"가 아니다. **반드시 모든 개념을 코드로 직접 쓸 수 있을 때까지 파고들어야** 한다.

### 이 단원의 종착점 (학습 목표)

이 문서를 다 읽으면 다음 4가지를 할 수 있다:

1. **빈 종이에 클래스 하나를 처음부터 끝까지 작성**할 수 있다 (FRQ Q2 형식 그대로).
2. 다른 사람이 쓴 코드를 보고 **"왜 이 변수는 private인지, 왜 이 메서드는 static인지"** 즉답할 수 있다.
3. **객체가 메모리에서 어떻게 존재하는지** 그림으로 그릴 수 있다.
4. **참조 vs 값**의 차이를 이해해서 "이 코드 실행 후 원본이 바뀌는가?"라는 질문에 1초 안에 답할 수 있다.

### CED Skill Category 매핑 — 토픽이 어떤 능력을 묻는지

CED는 모든 시험 문제를 **5개 Skill Category(컴퓨팅 사고 실천)** 중 하나에 매핑한다. 같은 EK 내용도 어떤 Skill로 묻느냐에 따라 문제 형태가 달라지므로, 토픽별 Skill을 알면 **출제 형식을 미리 예측**할 수 있다.

#### 5개 Skill의 의미 (CED 원문 기반)

| Skill | 한 줄 의미 | 문제 형태 |
|---|---|---|
| **1.A** Design Code | 문제 해결을 위한 적절한 프로그램 설계·알고리즘 결정 | "어떤 클래스/메서드 구조가 적절?" — 설계 판단 |
| **2.B** Write Code (data) | 데이터 추상화 관련 코드 작성 (필드·생성자·접근자 등) | FRQ Q2 본체 |
| **2.C** Write Code (procedural) | 절차 추상화 관련 코드 작성 (메서드 본문) | FRQ Q2의 메서드 부분 |
| **3.B** Determine Output (data) | 데이터 추상화가 들어간 코드의 출력/결과 결정 | MCQ 트레이싱 |
| **3.C** Determine Output (procedural) | 절차 추상화가 들어간 코드의 출력/결과 결정 | MCQ 트레이싱 |
| **3.D** Explain Errors | 컴파일 안 되거나 의도대로 동작 안 하는 이유 설명·수정 | MCQ "다음 중 에러는?" |
| **4.A** Describe Behavior | 코드가 무엇을 하는지 설명 | MCQ "이 코드의 목적은?" |
| **4.B** Describe Preconditions | 코드가 의도대로 작동하려면 어떤 초기 조건이 필요한지 | MCQ "전제 조건은?" |
| **5.A** Computing Impact | 컴퓨팅의 사회·경제·문화 영향 설명 | MCQ 시나리오 (윤리) |

#### Unit 3 토픽별 Skill 매핑 (CED p.77-78 공식)

| Topic | 제목 | 시험 강조 Skill |
|---|---|---|
| 3.1 | Abstraction and Program Design | **1.A** (설계 판단) |
| 3.2 | Impact of Program Design | **5.A** (사회 영향) |
| 3.3 | Anatomy of a Class | **1.A** + **2.B** (설계 + 코드 작성) |
| 3.4 | Constructors | **2.B** + **3.B** (작성 + 결과 결정) |
| 3.5 | Methods: How to Write | **2.C** + **3.C** + **3.D** + **4.B** (가장 많은 Skill — FRQ 핵심) |
| 3.6 | Methods: Passing/Returning References | **2.C** + **4.A** (작성 + 동작 설명) |
| 3.7 | Class Variables and Methods | **2.C** + **3.B** (작성 + 결과) |
| 3.8 | Scope and Access | **3.B** + **3.D** + **4.A** (트레이싱 + 에러 + 설명) |
| 3.9 | this Keyword | **2.B** (코드 작성) |

#### 시험 대비 활용법

- **Skill 2.B/2.C가 많은 토픽**(3.3, 3.4, 3.5, 3.7, 3.9) → **FRQ Q2 직결**. 손으로 코드 쓰는 연습 필수.
- **Skill 3.B/3.C/3.D가 많은 토픽**(3.5, 3.7, 3.8) → **MCQ 트레이싱·에러 진단**. 코드 읽기 연습.
- **Skill 4.A/4.B**(3.5, 3.6, 3.8) → **MCQ 서술형**. "이 코드의 목적/전제는?" 형태.
- **Skill 5.A**(3.2 단독) → **MCQ 시나리오**. 사회 영향 1-2문제 대비.

---

## 1. 본격 시작 전 — "객체"가 도대체 뭔지부터

### 왜 이 이야기부터 하는가

Unit 3의 모든 코드는 "객체"를 다룬다. 그런데 객체가 정확히 무엇인지 모르고 시작하면, 모든 코드가 외계어로 보인다. 5분만 투자해서 객체가 무엇인지부터 머리에 박아두자.

### 비유 — 붕어빵 가게

여러분이 붕어빵 가게 사장이라고 하자. 손님이 한 명 오면 붕어빵 하나, 백 명 오면 백 개를 만들어야 한다. 매번 새 모양의 빵을 만들지는 않는다. **틀(mold)이 하나 있고, 그 틀로 똑같은 모양의 붕어빵을 여러 개 찍어낸다.**

```
붕어빵 틀(mold) ───→ 붕어빵 1, 붕어빵 2, 붕어빵 3, ... (똑같은 모양, 다른 빵)
```

이 비유에서:
- **틀** = **클래스(class)** — 설계도, 같은 종류의 사물을 찍어내는 청사진
- **붕어빵 하나하나** = **객체(object)** = **인스턴스(instance)** — 틀로 찍어낸 실제 사물

### 왜 이 비유가 정확한가

붕어빵 하나하나는:
- **모양은 같다** (모두 붕어 모양). → 모든 객체는 같은 메서드/속성을 가진다.
- **속재료는 다를 수 있다** (팥/슈크림/치즈). → 각 객체는 자신만의 데이터(필드 값)를 가진다.
- **하나가 부서져도 다른 붕어빵은 멀쩡** (독립적). → 한 객체의 상태 변경은 다른 객체에 영향 없다.
- **틀 자체는 먹는 게 아니다.** 틀로 빵을 찍어야 비로소 사용 가능. → 클래스 자체로는 쓸모 없다. `new`로 객체를 만들어야 사용한다.

### Java 코드로 옮기면

```java
// 틀(클래스) 정의
public class 붕어빵 {
    private String 속재료;
    
    public 붕어빵(String 재료) {
        this.속재료 = 재료;
    }
    
    public String 먹기() {
        return "맛있는 " + 속재료 + " 붕어빵!";
    }
}

// 사용 (틀로 빵 찍기)
붕어빵 빵1 = new 붕어빵("팥");      // 객체 1
붕어빵 빵2 = new 붕어빵("슈크림");  // 객체 2
붕어빵 빵3 = new 붕어빵("치즈");    // 객체 3
```

`빵1, 빵2, 빵3`은 같은 클래스(`붕어빵`)로 만들어졌지만 각자 다른 속재료를 가진다. 이게 **객체**다.

### 왜 객체가 필요한가 — "절차적 사고"의 한계

객체 없이 프로그램을 짜면 어떻게 될까? 학생 30명의 정보를 관리한다고 하자:

```java
// 객체 없는 코드 — 변수 폭발
String 학생1_이름;  int 학생1_학년;  double 학생1_평점;
String 학생2_이름;  int 학생2_학년;  double 학생2_평점;
String 학생3_이름;  int 학생3_학년;  double 학생3_평점;
// ... 30번 반복
```

90개의 변수를 관리해야 한다. 학생 한 명의 정보를 출력하려면 그 학생 번호에 맞는 3개 변수를 일일이 가져와야 한다. **이름과 학년이 짝이 맞는지** 보장할 방법도 없다.

```java
// 객체로 해결
public class Student {
    private String 이름;
    private int 학년;
    private double 평점;
    // ...
}

Student 학생1 = new Student("김철수", 11, 3.8);
Student 학생2 = new Student("이영희", 12, 3.9);
// ... 한 명당 한 줄
```

이름·학년·평점이 **하나의 학생**으로 묶여서 관리된다. **연관된 데이터를 묶는다** — 이게 객체의 첫 번째 존재 이유.

### 객체의 두 번째 존재 이유 — "행동도 함께"

붕어빵 하나는 데이터(속재료)뿐 아니라 **할 수 있는 행동**(먹기)도 있다. Student 객체도 마찬가지로 "이름 알려주기", "학년 올리기", "졸업하기" 같은 행동을 가질 수 있다. **데이터와 그 데이터를 다루는 행동을 한 곳에 묶는다** — 이게 객체의 두 번째 존재 이유.

### 정리 — 객체란?

> **객체 = 관련된 데이터(필드) + 그 데이터를 다루는 행동(메서드)을 하나로 묶은 것**

이 한 문장이 Unit 3의 모든 내용을 관통한다. 앞으로 "이 개념은 왜 이렇게 생겼는가?"라는 질문이 나올 때마다 이 한 문장으로 돌아가면 답이 보인다.

---

## 2. CED Topic 3.1 — 추상화 (Abstraction) — 왜 첫 번째 개념인가

### 왜 이 개념을 가장 먼저 배우는가

추상화는 "복잡한 걸 간단해 보이게 만드는 기술"이다. 이것이 클래스를 설계할 때 가장 먼저 결정해야 할 사고방식이기 때문에 단원의 첫 토픽이다.

### 일상의 추상화 — 전자레인지

전자레인지를 쓸 때 우리는 그냥 버튼을 누른다. **마이크로파가 어떻게 발생하는지, 회전 접시가 어떻게 돌아가는지, 타이머가 어떻게 카운트다운하는지** 알 필요가 없다. 우리에게 보이는 건 "버튼"과 "결과(따뜻해진 음식)"뿐이다.

전자레인지를 만든 엔지니어는 우리에게 **버튼이라는 인터페이스**만 노출하고, **내부 동작은 숨겼다**. 이것이 추상화다.

### 두 종류의 추상화

AP CSA에서는 추상화를 두 가지로 나눈다.

#### (1) 데이터 추상화 (Data Abstraction)

> **"데이터가 내부에서 어떻게 저장되는지 모르고, 이름만으로 사용한다."**

예를 들어 `student.getName()`을 호출하면 학생 이름이 반환된다. 그런데:
- 이름이 String으로 저장되어 있는지?
- 데이터베이스에서 가져오는지?
- 매번 계산되는 건지?

**우리는 모른다, 알 필요도 없다.** 그냥 `getName()`을 부르면 이름이 나온다는 사실만 알면 된다. 이것이 데이터 추상화.

```java
// 사용자 입장
String 이름 = student.getName();   // 어떻게 저장되는지 몰라도 됨

// 만든 사람 입장 (둘 중 어느 쪽이든 사용자에게 동일하게 보임)
public class Student {
    private String 이름;
    public String getName() { return 이름; }
}

public class Student {
    private String 성;
    private String 이름;
    public String getName() { return 성 + " " + 이름; }
}
```

#### (2) 절차 추상화 (Procedural Abstraction)

> **"메서드가 내부에서 어떻게 작동하는지 모르고, 이름과 입력만으로 사용한다."**

`Math.sqrt(25)`를 호출하면 5.0이 나온다. **어떤 알고리즘으로 제곱근을 계산하는지** 우리는 모른다. 뉴턴 방법인지, 이진 탐색인지, 비트 조작인지. 그냥 "제곱근 함수가 있고, 25를 넣으면 5가 나온다"만 알면 된다. 이것이 절차 추상화.

#### CED 공식 용어 — Method Decomposition (메서드 분해)

> **CED 3.1.A.4 원문**: "Through **method decomposition**, a programmer breaks down larger behaviors of the class into smaller behaviors by creating methods to represent each individual smaller behavior."

**메서드 분해(method decomposition)** = 클래스의 큰 행동을 작은 행동들로 나눠 각각을 별도 메서드로 만드는 것. 절차 추상화의 실천 기법.

예: "학생 성적표 출력"이라는 큰 행동 → `printName()` + `printGrades()` + `printAverage()` 세 개의 작은 메서드로 분해. 각 메서드는 한 가지 일만 하므로 재사용·테스트·수정이 쉬워진다.

이를 통해 **공통 기능을 추출**(extract shared features)해서 코드 재사용이 가능해지고, 복잡성도 낮아진다. AP CSA가 강조하는 핵심 설계 원칙.

#### CED 공식 용어 — Attribute (속성)

> **CED 3.1.A.3 원문**: "An **attribute** is a type of data abstraction that is defined in a class outside any method or constructor. An **instance variable** is an attribute whose value is unique to each instance of the class. A **class variable** is an attribute shared by all instances of the class."

**attribute(속성)** = 메서드/생성자 외부에 클래스 안에 정의되는 데이터 추상화의 총칭. instance variable과 class variable이 모두 attribute의 한 종류다.

| CED 용어 | 한국어 | 의미 |
|---------|------|-----|
| **attribute** | 속성 | 클래스 안, 메서드/생성자 밖에 정의된 데이터 추상화 |
| **instance variable** | 인스턴스 변수 | 객체마다 고유한 값을 가지는 attribute |
| **class variable** | 클래스 변수 (static) | 모든 객체가 공유하는 attribute |

> **시험 빈출**: "Which of the following is an example of an **attribute** of a class?" → 답은 인스턴스 변수 또는 static 변수 선언. 메서드 안의 지역 변수는 attribute가 아님.

### 왜 추상화가 중요한가 — 두 가지 이유

#### 이유 1: 복잡성 관리 (Complexity Management)

큰 프로그램에는 수만 줄의 코드가 있다. 모든 코드를 한꺼번에 머릿속에 넣고 일할 수는 없다. 추상화를 하면:
- 다른 사람의 코드를 쓸 때 **내부를 안 봐도 된다**.
- 자신의 코드도 모듈로 나눠서 한 번에 한 모듈씩 다룰 수 있다.

#### 이유 2: 변경의 자유 (Freedom to Change)

위의 Student 예에서, 만든 사람이 "이름을 성+이름으로 분리해서 저장"하는 방식으로 바꿔도 **사용자 코드는 변경할 필요 없다**. `getName()`이라는 인터페이스가 같으면 내부 구현은 자유롭게 바꿀 수 있다.

### 시험에 어떻게 나오는가

MCQ에서 "다음 중 데이터 추상화의 예는?" 식으로 출제. 두 종류를 구분할 수 있어야 한다.

| 보기 | 종류 |
|-----|-----|
| `student.getName()` 호출, 이름이 어떻게 저장되는지 모름 | 데이터 추상화 |
| `Math.sqrt(25)` 호출, 알고리즘 모름 | 절차 추상화 |
| `ArrayList`에 `add(x)` 호출, 내부 배열 어떻게 늘어나는지 모름 | 데이터 추상화 |
| `Collections.sort(list)` 호출, 어떤 정렬 알고리즘인지 모름 | 절차 추상화 |

### 매개변수가 추상화의 일반화 도구인 이유 (CED 3.1.A.5)

```java
// 매개변수 없는 버전 — 한 가지만 함
public int 더하기5() { return x + 5; }
public int 더하기7() { return x + 7; }   // 새 함수 또 만들어야 함

// 매개변수가 있는 버전 — 모든 더하기 가능
public int 더하기(int n) { return x + n; }
```

**매개변수**는 "한 가지 동작을 다양한 입력에 재사용 가능하게 만드는" 도구. 매개변수가 늘어날수록 메서드가 더 일반화(generalize)되어 재사용 폭이 넓어진다. 추상화의 핵심 메커니즘 중 하나.

### 추상화 덕분에 가능한 것 — 내부 변경의 자유 (CED 3.1.A.6)

이미 캡슐화 부분에서 본 원리와 같은 맥락이다. 한 번 더 강조:

> **"메서드 시그니처(이름·매개변수)와 메서드가 하는 일이 같다면, 내부 구현은 자유롭게 바꿔도 메서드 사용자에게 통보할 필요 없다."**

예: `Math.sqrt(x)`의 내부 알고리즘이 Java 8과 Java 22 사이에 바뀌었더라도, 우리 코드는 변경 불요. 시그니처가 같고 결과가 같으면 OK.

이 원리 덕분에:
- 라이브러리 개발자는 성능을 개선할 자유를 가진다
- 사용자는 안정적인 인터페이스를 신뢰할 수 있다
- 큰 시스템도 부분 부분 점진적으로 개선 가능

### 클래스 설계는 코드 작성 전에 — 다이어그램의 역할 (CED 3.1.A.7)

> **"클래스를 구현하기 전에, 그 클래스의 속성(attributes)과 행동(behaviors)을 자연어나 다이어그램으로 먼저 설계하는 것이 좋다."**

#### 왜 먼저 설계해야 하는가

코드부터 쓰면:
- 중요한 속성을 빠뜨리고 나중에 추가 → 큰 수정
- 메서드 시그니처가 일관성 없게 됨
- 클래스 간 관계가 꼬임

설계를 먼저 하면 큰 그림이 보이고, 코드 작성은 빠르고 정확해진다.

#### 자연어 설계의 예 (FRQ 지문도 이 방식)

> **Book 클래스**
> - 속성: 제목(String), 저자(String), 페이지 수(int)
> - 행동:
>   - 생성자: 제목, 저자, 페이지 수를 받아 초기화
>   - getTitle(): 제목 반환
>   - addPages(int n): n이 0 이상이면 pages에 더함
>   - isLong(): pages > 300이면 true 반환

이 자연어 설명을 그대로 Java 코드로 변환하면 된다. **FRQ Q2의 지문은 정확히 이 형식으로 주어진다** — 지문을 읽고 한 문장씩 코드로 옮기는 것이 정답 작성 흐름.

#### UML 다이어그램의 예 (간단 표기)

```
┌──────────────────────┐
│       Book           │     ← 클래스 이름
├──────────────────────┤
│ - title: String      │     ← '-' = private
│ - author: String     │     ← 인스턴스 변수
│ - pages: int         │
├──────────────────────┤
│ + Book(...)          │     ← '+' = public
│ + getTitle(): String │     ← 생성자/메서드
│ + addPages(int): void│
│ + isLong(): boolean  │
└──────────────────────┘
```

UML(Unified Modeling Language)은 클래스의 구조를 시각적으로 표현하는 표준. AP CSA에서 직접 작성을 요구하지는 않지만, **읽고 이해하는** 능력은 필요할 수 있다.

### 한 줄 요약

> **추상화 = "어떻게(how)"가 아니라 "무엇을(what)"만 보이게 만드는 것.** 매개변수로 일반화하고, 내부 구현을 숨겨 변경 자유를 얻고, 코드 전에 자연어/다이어그램으로 설계한다.

---

## 2½. CED Topic 3.2 — 프로그램 설계의 영향 (Impact of Program Design)

### 왜 이 토픽이 단원에 있는가

클래스를 설계하기 시작하면 단순히 "코드가 작동하는가"를 넘어 **"이 프로그램이 사회에 어떤 영향을 미치는가"**를 고민해야 한다. CED는 이 토픽을 약 **1 instructional period**(약 45분)로 책정. MCQ 시나리오 1-2문제 출제 가능.

### 3.2.A.1 — 시스템 신뢰성 (System Reliability)

> **CED 원문 (3.2.A.1)**: "**System reliability** refers to the program being able to perform its tasks as expected under stated conditions without failure. Programmers should make an effort to maximize system reliability by testing the program with a variety of conditions."
>
> **번역**: 시스템 신뢰성 = 프로그램이 명시된 조건에서 실패 없이 기대대로 작동하는 능력. 프로그래머는 다양한 조건의 테스트로 신뢰성을 최대화해야 한다.

#### 비유 — 자동차 안전 검사

새 자동차는 출고 전에 수많은 테스트를 거친다 — 충돌 테스트, 비 오는 날 주행, 영하 30도, 영상 50도, 산악 도로... 이런 다양한 조건에서 모두 작동해야 "신뢰성 있는 자동차". 한두 조건에서만 잘 굴러가도 신뢰성이 떨어진다.

소프트웨어도 동일. 정상 입력에만 작동하면 신뢰성 없음. **edge case**(빈 입력, 음수, 매우 큰 수, null, 동시 접속 등)에서도 작동해야 신뢰성 있음.

#### 신뢰성을 높이는 방법

1. **다양한 입력으로 테스트** — 정상값, 경계값, 극단값, 비정상값
2. **edge case 처리 코드 추가** — 빈 배열, null 참조 검사
3. **Precondition / Postcondition 명시** — 메서드가 가정하는 조건 문서화
4. **단위 테스트(unit test) 작성** — AP 범위 밖이지만 실무 중요

#### 시험 출제 형태

> "프로그램의 system reliability를 높이는 방법으로 가장 적절한 것은?"
> - (A) 모든 변수를 public으로 → ❌ (오히려 캡슐화 위반, 신뢰성 저하)
> - (B) 다양한 조건에서 테스트 → ✅
> - (C) 코드를 짧게 작성 → ❌ (간결성과 신뢰성은 다른 문제)
> - (D) 한 가지 입력만 검증 → ❌

### 3.2.A.2 — 사회·경제·문화에 미치는 영향

> **CED 원문 (3.2.A.2)**: "The creation of programs has impacts on society, the economy, and culture. These impacts can be both **beneficial and harmful**. Programs meant to fill a need or solve a problem can have **unintended harmful effects** beyond their intended use."
>
> **번역**: 프로그램 제작은 사회·경제·문화에 영향을 미친다. 그 영향은 **이로울 수도 해로울 수도** 있다. 필요를 채우거나 문제 해결을 위해 만든 프로그램이 의도된 용도를 넘어 **의도치 않은 해로운 결과**를 낼 수 있다.

#### 영향의 두 얼굴

| 영역 | 긍정적 영향 | 부정적 영향 (의도치 않은 해) |
|-----|-----------|--------------------------|
| **사회** | 의료 앱으로 건강 관리 향상 | SNS 알고리즘이 우울증·중독 유발 |
| **경제** | 자동화로 생산성 향상 | 일자리 감소, 양극화 심화 |
| **문화** | 온라인 학습으로 교육 격차 해소 | 가짜 뉴스 확산, 양극화 |

#### 핵심 단어: "Unintended Harmful Effects"

처음 만들 때는 좋은 의도였지만 결과적으로 해를 끼치는 경우가 많다. 예:
- 추천 알고리즘 → 사용자가 좋아할 콘텐츠 노출 → 결과: filter bubble, 극단주의 강화
- 얼굴 인식 → 보안 향상 → 결과: 인종 차별, 개인 추적

프로그래머는 **"이 코드가 어떤 의도치 않은 결과를 낳을 수 있는가?"**를 항상 자문해야 한다.

#### 시험 출제 시나리오

> "한 SNS의 추천 알고리즘이 청소년 우울증 증가와 상관관계를 보인다. 이 상황을 가장 잘 설명하는 개념은?"
>
> **답**: Unintended harmful effect. 사용자 참여(engagement) 증가가 의도였지만, 부작용으로 정신건강 문제 발생.

### 3.2.A.3 — 법적 이슈와 지적재산권

> **CED 원문 (3.2.A.3)**: "Legal issues and intellectual property concerns arise when creating programs. Programmers often **reuse code written by others** and published as **open source** and free to use. Incorporation of code that is not published as open source requires the programmer to **obtain permission** and often **purchase** the code before integrating it into their program."
>
> **번역**: 프로그램 제작 시 법적 이슈와 지적재산권 문제가 발생한다. 프로그래머는 다른 사람이 작성하여 **open source**로 공개된 코드를 자주 재사용한다. open source가 아닌 코드를 사용하려면 **허가를 받고**, 종종 **구매**해야 한다.

#### Open Source의 의미

> **Open Source**: 소스 코드가 공개되어 누구나 보고, 사용하고, 수정하고, 재배포할 수 있는 소프트웨어. 단, **라이선스 조건**(예: MIT, Apache, GPL)을 따라야 한다.

예시: Linux, Python, React, TensorFlow.

#### Proprietary (독점) Code의 의미

> **Proprietary code**: 회사 또는 개인이 소유권을 가진 코드. 사용/수정/재배포에 명시적 허가가 필요하고, 대개 비용 발생.

예시: Microsoft Windows, Adobe Photoshop, Oracle Database.

#### 비유 — 책의 저작권

도서관에서 빌린 책은 자유롭게 읽을 수 있다. 그러나 그 책의 내용을 **복사해서 자기 책으로 출판**하려면 저작권 침해. 출판하려면 저작자의 허락 또는 구매(권리 양도) 필요.

소프트웨어도 동일. 코드를 보고 배우는 건 자유롭지만, 자기 프로젝트에 **그대로 가져다 쓰려면** 라이선스 확인 필수.

#### 시험 출제 시나리오

> "한 학생이 다른 사람이 작성한 코드를 자신의 프로젝트에 복사해서 사용하려고 한다. 가장 먼저 확인해야 할 것은?"
>
> **답**: 그 코드의 라이선스. open source인지 (어떤 조건의 open source인지), proprietary인지 확인하고, 필요시 허가/구매.

### 한 줄 요약

> **Topic 3.2 = (1) 신뢰성을 위해 다양한 조건 테스트 (2) 의도치 않은 해로운 영향 인식 (3) 코드 재사용 시 라이선스 확인. MCQ 시나리오 1-2문제 대비.**

---

## 3. CED Topic 3.3 (EK 3.3.A.1) — 캡슐화 (Encapsulation) — 왜 데이터를 숨겨야 하는가

> ⚠️ **CED 토픽 구조 안내**: 본 문서 §3과 §4는 모두 **CED Topic 3.3 "Anatomy of a Class"**(EK 3.3.A.1 ~ 3.3.A.6)를 다룬다. §3은 EK 3.3.A.1(캡슐화/public·private), §4는 EK 3.3.A.2~A.6(클래스의 5대 구성 요소)를 분리해 설명한다. CED 공식 토픽명은 "Anatomy of a Class" 하나이며, 캡슐화는 그 안의 한 EK다.

### 추상화와 무엇이 다른가

추상화와 캡슐화는 헷갈리기 쉬운데, 명확한 차이가 있다.

| 개념 | 핵심 질문 |
|-----|---------|
| **추상화** | "사용자에게 **무엇을** 보여줄까?" |
| **캡슐화** | "사용자가 **함부로 못 만지게** 어떻게 막을까?" |

추상화는 인터페이스 설계. 캡슐화는 그 인터페이스를 **강제로 따르게 만드는 메커니즘**이다.

### 비유 — 은행 통장

여러분의 통장 잔액을 다른 사람이 마음대로 바꿀 수 있다고 하자. 모르는 사람이 "잔액을 -1억으로 설정"한다. 끔찍하다.

실제 은행은 어떻게 막는가?
- 잔액은 은행 데이터베이스 깊숙이 보관 (직접 접근 불가)
- 입금/출금은 **반드시 정해진 절차**(창구, ATM, 앱)를 통과해야 함
- 절차에는 **검증 로직**이 들어있음 (음수 출금 불가, 잔액 초과 출금 불가 등)

이것이 캡슐화다. **데이터를 숨기고, 정해진 메서드를 통해서만 접근하게 한다.**

### Java로 옮기면

```java
// ❌ 캡슐화 없음 — 위험!
public class BankAccount {
    public double balance;   // 누구나 직접 만질 수 있음
}

// 사용자가 마음대로
BankAccount 통장 = new BankAccount();
통장.balance = -1_000_000_000;   // 잔액 -10억! 막을 방법 없음
```

```java
// ✅ 캡슐화 적용
public class BankAccount {
    private double balance;   // 외부에서 직접 못 만짐
    
    public void 입금(double 금액) {
        if (금액 > 0) {              // 검증 로직
            balance += 금액;
        }
    }
    
    public void 출금(double 금액) {
        if (금액 > 0 && balance >= 금액) {   // 검증 로직
            balance -= 금액;
        }
    }
    
    public double 잔액조회() {
        return balance;   // 읽기만 허용
    }
}

// 사용자가 마음대로 할 수 없음
BankAccount 통장 = new BankAccount();
통장.balance = -1_000_000_000;   // ❌ 컴파일 에러! private이라 접근 불가
통장.출금(-100);                  // 메서드는 부를 수 있지만, 검증 로직이 막음 (금액 > 0 위반)
```

### `private`의 정확한 의미

> **`private`이 붙은 변수/메서드는 같은 클래스 내부 코드에서만 접근 가능하다.**

다른 클래스, 심지어 같은 패키지의 클래스에서도 접근 불가. 이것이 캡슐화의 **문법적 강제 메커니즘**이다.

### `public`의 정확한 의미

> **`public`이 붙은 변수/메서드는 어디서든 접근 가능하다.**

### 왜 모든 인스턴스 변수는 `private`이어야 하는가 — 시험의 절대 규칙

AP CSA FRQ Q2 채점 기준에 **"필드는 private인가?"**가 1점 항목으로 별도 존재한다. 즉:

| 코드 | 채점 |
|-----|-----|
| `private int x;` | ✅ 1점 |
| `public int x;` | ❌ 0점 |
| `int x;` (접근 제한자 누락) | ❌ 0점 |

**규칙: 모든 instance variable은 무조건 `private`. 예외 없음.**

### 왜 메서드는 보통 `public`인가

메서드는 외부에서 객체를 사용하기 위한 **인터페이스**다. 외부가 호출할 수 없으면 의미가 없으므로 보통 `public`. 예외는 **내부 보조 메서드** — 클래스 내부에서만 쓰는 helper는 `private`로 둔다.

### 캡슐화의 진짜 가치 — "변경 가능성"

추상화 부분에서 본 것처럼, 캡슐화가 있으면 **내부 구현을 자유롭게 바꿀 수 있다**:

```java
// 처음 버전
public class BankAccount {
    private double balance;
    public double 잔액조회() { return balance; }
}

// 나중에 멀티 통화 지원으로 변경
public class BankAccount {
    private double 원화잔액;
    private double 달러잔액;
    public double 잔액조회() { return 원화잔액 + 달러잔액 * 1300; }
}
```

`잔액조회()`라는 인터페이스가 같으면 **이 메서드를 쓰는 모든 코드는 변경 불필요**. `private`로 가려놨기 때문에 가능한 일.

### 한 줄 요약

> **캡슐화 = `private` 필드 + `public` 메서드. 데이터를 숨기고, 정해진 통로만 열어둔다.**

---

## 4. CED Topic 3.3 (계속) — 클래스의 해부학 (Anatomy of a Class)

### 왜 이 토픽을 별도로 다루는가

클래스 정의는 정해진 부품들로 구성된다. **각 부품이 무엇이고, 왜 그 자리에 있는지** 알아야 빈 종이에 클래스를 쓸 수 있다 (FRQ Q2의 핵심 능력).

### 클래스의 5대 구성 요소

```java
public class Dog {                    // ① 클래스 헤더
    
    private String name;              // ② 인스턴스 변수 (필드)
    private int age;
    
    public Dog(String name, int age) { // ③ 생성자
        this.name = name;
        this.age = age;
    }
    
    public String getName() {          // ④ 접근자 (accessor / getter)
        return name;
    }
    
    public void setAge(int age) {      // ⑤ 변경자 (mutator / setter)
        this.age = age;
    }
}
```

### ① 클래스 헤더 — 왜 `public class`인가

```java
public class Dog {
```

- **`public`**: 다른 패키지/파일에서도 이 클래스를 쓸 수 있게 함. AP CSA에서는 항상 public.
- **`class`**: "이건 클래스 정의"라고 컴파일러에게 선언.
- **`Dog`**: 클래스 이름. 관례상 **PascalCase** (단어 첫 글자 대문자).

> **시험 함정**: 클래스 이름은 **파일 이름과 일치**해야 한다 (Dog.java 파일 안에 `public class Dog`). FRQ에서는 파일명 신경 쓸 필요 없지만, 컴파일 환경에서는 중요.

### ② 인스턴스 변수 — 왜 클래스의 "본체"인가

```java
private String name;
private int age;
```

이것이 **클래스의 데이터**다. 각 객체(인스턴스)가 자신만의 값을 보유한다.

#### 비유

붕어빵 클래스의 인스턴스 변수가 `속재료`라면, 붕어빵 객체 1은 `속재료="팥"`, 객체 2는 `속재료="슈크림"`. **같은 변수 이름, 다른 값**.

#### 메모리 시각화

```
힙(Heap) 메모리:
┌──────────────────┐  ┌──────────────────┐
│ Dog 객체 1        │  │ Dog 객체 2        │
│ name = "Buddy"   │  │ name = "Max"     │
│ age = 3          │  │ age = 5          │
└──────────────────┘  └──────────────────┘
```

각 객체는 자기 메모리 영역에 자기 인스턴스 변수 값을 저장.

#### 규칙: 무조건 `private`

(앞에서 다룬 캡슐화 규칙) 모든 인스턴스 변수는 `private`.

### ③ 생성자 — 왜 특별한 메서드인가

(다음 섹션에서 깊이 다룸)

### ④ 접근자 (Accessor / Getter) — 왜 필요한가

```java
public String getName() {
    return name;
}
```

`name`이 `private`라서 외부에서 직접 못 읽는다. 그러나 외부도 가끔 이름을 알아야 한다. **읽기 전용 통로**가 필요. 그것이 getter.

#### 규칙

- **`public`**: 외부에서 호출 가능해야 함
- **반환 타입 = 필드 타입**: `String name` → `String getName()`
- **매개변수 없음**: 그냥 값을 돌려주는 것
- **이름 관례**: `get` + 필드명 (첫 글자 대문자). boolean이면 `is` + 필드명도 가능.

### ⑤ 변경자 (Mutator / Setter) — 왜 필요한가

```java
public void setAge(int age) {
    this.age = age;
}
```

외부가 가끔 값을 바꿔야 한다 (예: 강아지 생일이 지나서 나이 +1). **검증된 변경 통로**가 필요. 그것이 setter.

#### 규칙

- **`public`**: 외부에서 호출 가능
- **반환 타입 = `void`**: 값을 바꾸는 게 목적이지 돌려주는 게 아니므로
- **매개변수 1개**: 새 값을 받는 통로
- **이름 관례**: `set` + 필드명

#### Setter는 검증을 위한 자리

```java
public void setAge(int age) {
    if (age >= 0 && age <= 30) {     // 강아지 나이는 0~30이어야 함
        this.age = age;
    }
    // else: 무시 또는 예외 (AP 범위 밖)
}
```

이 검증 로직 덕분에 객체의 데이터가 항상 **유효한 상태**를 유지한다. `public` 필드면 이 보호가 불가능.

### 작성 순서 (관례)

권장 순서: ① 헤더 → ② 필드 → ③ 생성자 → ④ getter → ⑤ setter → ⑥ 추가 메서드

이 순서를 따르면 **읽는 사람이 위에서 아래로 자연스럽게** 클래스를 이해할 수 있다.

### 한 줄 요약

> **클래스 = `public class` + `private 필드` + `public 생성자` + `public getter/setter` + 비즈니스 메서드.** 이 5가지 부품의 조합.

---

## 5. CED Topic 3.4 — 생성자 (Constructor) — 객체에 첫 숨을 불어넣는 일

### 왜 별도의 "생성자"라는 게 필요한가

새 객체가 만들어질 때, **인스턴스 변수에 초기 값을 넣어야 한다**. 강아지 객체를 만들면서 이름을 안 정하면 그 강아지는 어떤 강아지인지 모른다. 객체가 태어나는 순간 호출되어 **초기 상태를 설정하는 특별한 메서드** — 그게 생성자.

### 비유 — 신생아의 출생 신고

아기가 태어날 때:
- 이름을 짓는다
- 생년월일을 기록한다
- 부모 정보를 등록한다

이 모든 절차가 **출생과 동시에** 일어나야 한다. 나중에 따로 "이름 짓기 함수"를 부르는 방식은 위험 — 누가 잊어버릴 수 있다. 생성자는 이 출생 신고를 **자동으로 강제**한다.

### CED 3.4.A.1 — "has-a relationship" (객체와 인스턴스 변수의 관계)

> **CED 원문 (3.4.A.1)**: "An object's **state** refers to its attributes and their values at a given time and is defined by instance variables belonging to the object. This defines a **has-a relationship** between the object and its instance variables."
>
> **번역**: 객체의 **상태(state)** = 특정 시점에서의 속성들과 그 값들. 인스턴스 변수가 정의한다. 이것이 객체와 인스턴스 변수 간의 **"has-a 관계"**를 정의한다.

#### "has-a" 관계란

> **"객체 A는 인스턴스 변수 B를 **가진다(has-a)**."**
> - Student **has-a** name
> - Student **has-a** grade
> - Student **has-a** gpa
> - Car **has-a** engine
> - Car **has-a** color

CED는 Unit 3에서 **has-a 관계만** 다룬다. (이전 버전 CED에 있던 "is-a 관계"(상속)는 2025-26 시험 범위에서 제거됨.)

| 관계 | 의미 | 예시 | 코드 표현 |
|-----|-----|-----|---------|
| **has-a** | 가지고 있다 (객체가 인스턴스 변수를 보유) | Car has-a Engine | `class Car { private Engine engine; }` |

#### 비유

- "**has-a**": 책가방은 책을 가진다. 책가방 ≠ 책. 책가방 안에 책이 있을 뿐. → Student "has-a" name, Account "has-a" balance, Car "has-a" Engine.

이 관계가 객체의 state(상태)를 정의한다.

### CED 3.4.A.2 — Constructor의 메모리 할당

> **CED 원문 (3.4.A.2)**: "A constructor is used to set the initial state of an object, which should include initial values for all instance variables. **When a constructor is called, memory is allocated for the object and the associated object reference is returned.** Constructor parameters, if specified, provide data to initialize instance variables."
>
> **번역**: 생성자는 객체의 초기 상태 설정에 사용. 모든 인스턴스 변수 초기값 포함해야 한다. **생성자 호출 시 객체용 메모리가 할당되고 그 객체 참조가 반환된다.** 생성자 매개변수가 있다면 인스턴스 변수 초기화 데이터를 제공.

#### `new Student("Tom")` 호출 시 일어나는 5단계

1. **메모리 할당**: 힙(heap)에 Student 객체용 공간 확보
2. **인스턴스 변수 default value 설정**: name=null, grade=0, gpa=0.0
3. **선언 시 초기화 식 실행**: `private int grade = 9;`라면 grade=9
4. **생성자 본체 실행**: `this.name = "Tom";` 등
5. **객체 참조(주소) 반환**: 변수가 그 주소를 받음

```java
Student s = new Student("Tom");
//          ^^^^^^^^^^^^^^^^^^^
//          5단계 모두 일어남
//          마지막에 반환된 참조가 변수 s에 저장됨
```

이 과정 이해가 "왜 default value가 자동 부여되는가", "왜 새 객체마다 독립된 메모리를 가지는가"를 설명한다.

### 생성자의 6가지 특징

```java
public class Dog {
    private String name;
    private int age;
    
    public Dog(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

1. **이름 = 클래스 이름과 동일** (`Dog`).
2. **반환 타입 없음** — `void`도 안 씀.
3. **항상 `public`으로 지정** (CED 3.3.A.3 원문: *"In this course, constructors are always designated public."*) — AP CSA 시험 범위 내 모든 클래스에서 생성자는 예외 없이 `public`. `private` 생성자나 default(접근 제한자 생략) 생성자는 시험 답안에 등장 X.
4. **`new` 키워드와 함께 호출**됨: `new Dog(...)`.
5. **객체가 만들어진 직후 자동 호출**.
6. **모든 인스턴스 변수를 초기화**하는 게 책임.

### 왜 반환 타입이 없는가 — 컴파일러 입장

생성자가 반환하는 건 **만들어진 객체 자신**이다. `new Dog("Buddy", 3)`은 자동으로 새 Dog 객체 참조를 반환한다. 그래서 반환 타입을 따로 명시할 필요가 없다 — Java 문법 자체가 그렇게 정의되어 있다.

#### 시험 단골 함정

```java
public class Dog {
    private String name;
    
    public void Dog(String name) {       // ⚠️ 'void' 반환 타입!
        this.name = name;
    }
}

Dog d = new Dog("Buddy");   // 컴파일 에러!
```

**왜 에러?** `public void Dog(...)`는 Java가 **일반 메서드**로 처리한다 (생성자가 아니라!). 이름이 클래스명과 같지만 반환 타입이 있으니 그냥 메서드. 따라서 진짜 생성자는 정의되지 않은 상태가 되고, `new Dog("Buddy")`에 매칭되는 생성자가 없어서 에러.

> **규칙: 생성자에 절대 반환 타입을 쓰지 않는다. `void`도 안 쓴다.**

### Default Constructor (기본 생성자) — Java가 몰래 만들어주는 것

```java
public class Cat {
    private String name;
    // 생성자를 하나도 안 만들었음
}

Cat c = new Cat();   // OK! 어떻게?
```

**Java가 몰래 default 생성자를 추가**해준다:

```java
public Cat() { }   // Java가 자동 생성
```

이 생성자는 매개변수가 없고, 본체도 비어있다. 인스턴스 변수들은 default value로 자동 초기화 (다음 섹션 참조).

### Default Value 규칙 — 외워야 할 4가지

생성자가 명시적으로 초기화하지 않은 인스턴스 변수는 다음 값으로 자동 초기화된다:

| 타입 | Default Value |
|-----|---------------|
| `int` (모든 정수형) | `0` |
| `double` (모든 실수형) | `0.0` |
| `boolean` | `false` |
| 참조 타입 (`String`, 배열, 객체) | `null` |

> **시험 빈출 외워라**: `int → 0`, `double → 0.0`, `boolean → false`, `참조 → null`.

### 왜 default value가 있는가

Java는 **"초기화되지 않은 변수"를 두려워한다**. 그런 변수가 있으면 프로그램이 예측 불가능한 동작을 한다. C/C++에서는 초기화 안 된 변수가 쓰레기 값을 가져서 버그의 원천. Java는 이를 막기 위해 **모든 인스턴스 변수에 강제로 default value를 부여**한다.

### Default Constructor의 함정 — "사라짐" 규칙

> **Java가 default 생성자를 자동 만들어주는 건, 사용자 정의 생성자가 하나도 없을 때만이다. 하나라도 정의하면 Java는 default 생성자를 만들어주지 않는다.**

```java
public class Cat {
    private String name;
    public Cat(String n) { name = n; }  // 사용자 정의 생성자 1개 추가
}

Cat c1 = new Cat("Tom");   // OK
Cat c2 = new Cat();        // ❌ 컴파일 에러!
```

**왜 사라지는가?** Java의 설계 철학: "당신이 생성자를 정의했다면, 당신은 객체 생성 방식을 직접 책임지겠다는 뜻. Java가 default를 강제로 끼워넣지 않겠다."

#### 해결책 — 둘 다 명시하기

```java
public Cat() { }            // 매개변수 없는 버전 (default 역할)
public Cat(String n) { ... } // 매개변수 있는 버전
```

이제 `new Cat()`과 `new Cat("Tom")` 둘 다 가능. 이를 **생성자 오버로딩**이라 한다.

### Constructor Overloading — 여러 개의 생성자

```java
public class Point {
    private int x, y;
    
    public Point() {
        this.x = 0;
        this.y = 0;
    }
    
    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
    
    public Point(int v) {
        this.x = v;
        this.y = v;   // (v, v) 좌표
    }
}
```

같은 이름이지만 **매개변수의 종류·개수가 다른** 여러 개의 생성자. 호출 시점에 매개변수에 맞는 생성자가 선택된다.

```java
new Point();         // 첫 번째 호출: (0, 0)
new Point(3, 5);     // 두 번째 호출: (3, 5)
new Point(7);        // 세 번째 호출: (7, 7)
```

### 왜 생성자가 모든 인스턴스 변수를 초기화해야 하는가

**FRQ Q2 채점 기준** 중 하나가 "생성자가 모든 인스턴스 변수를 의도된 값으로 초기화하는가"다. 누락 1개 = 1점 감점.

#### 잘못된 예

```java
public class Point {
    private int x, y;
    
    public Point(int x) {
        this.x = x;
        // y는 초기화 안 됨!
    }
}
```

기술적으로는 컴파일된다 (y는 default 0). 그러나 의도가 불명확하면 채점에서 감점.

#### 올바른 예

```java
public Point(int x) {
    this.x = x;
    this.y = 0;   // 명시적으로 0
}
```

명시적으로 초기화하면 의도가 분명해진다.

### Mutable 매개변수의 함정 — 방어적 복사 (Defensive Copy)

이 개념이 시험 단골이고 가장 헷갈리는 부분이다. 천천히 풀어 설명한다.

#### 비유 — 도둑이 보낸 박스

여러분이 친구 영희에게 "내 가방을 좀 보관해줘"라고 부탁한다고 하자. 영희는 그 가방을 자기 방에 둔다.

문제: **여러분이 그 가방을 계속 들고 있다**. 영희 모르게 가방을 열어서 물건을 꺼내거나 넣는다. 영희 입장에서는 "내가 보관 중인 가방"이 외부에서 마음대로 변경되고 있다. 보관의 의미가 없다.

해결: 영희가 받자마자 **가방의 내용물을 자기의 새 가방에 옮긴다**. 그러면 외부의 가방을 만져도 영희의 가방은 멀쩡.

이게 방어적 복사다.

#### Java 코드로

```java
public class Classroom {
    private ArrayList<String> students;
    
    // ❌ 위험한 생성자
    public Classroom(ArrayList<String> students) {
        this.students = students;   // 외부 리스트의 주소를 그대로 저장
    }
}

// 사용
ArrayList<String> 명단 = new ArrayList<>();
명단.add("철수");
Classroom 교실 = new Classroom(명단);

// 외부에서 명단 변경
명단.add("영희");

// 교실 내부 students도 변경됨! (같은 객체를 가리키므로)
System.out.println(교실.getStudents());   // [철수, 영희]
```

**문제**: `this.students = students;`는 ArrayList의 주소만 복사한다. 외부 `명단`과 내부 `students`가 **같은 ArrayList 객체**를 가리킨다. 한쪽이 변경하면 다른 쪽에도 보인다.

#### 해결 — 새 ArrayList 생성

```java
public Classroom(ArrayList<String> students) {
    this.students = new ArrayList<>(students);   // 새 ArrayList 생성, 요소만 복사
}
```

`new ArrayList<>(students)`는 **새 ArrayList를 만들고 기존 요소들을 복사**한다. 이제 외부 명단과 내부 students는 **다른 객체**. 외부 변경이 내부에 영향 없음.

#### 언제 방어적 복사가 필요한가 — 판별표

| 매개변수 타입 | 방어적 복사 | 이유 |
|------------|---------|-----|
| `int`, `double`, `boolean` (primitive) | ❌ 불필요 | 값 자체가 복사됨 |
| `String` | ❌ 불필요 | **불변(immutable)** — 외부가 바꿀 방법 없음 |
| `Integer`, `Double`, `Boolean` (wrapper) | ❌ 불필요 | 불변 |
| `int[]`, `String[]` 등 배열 | ✅ **필요** | 배열은 항상 변경 가능 |
| `ArrayList<E>` | ✅ **필요** | ArrayList는 변경 가능 |
| 사용자 정의 클래스 (setter 있음) | ✅ **필요** | setter로 변경 가능 |

#### 한 문장 기억법

> **"외부가 그 객체를 변경할 방법이 있으면 방어적 복사."**

primitive와 String은 변경할 방법이 없으므로 안전. 배열·ArrayList·일반 객체는 변경 가능하므로 위험.

#### Getter도 같은 함정

```java
public ArrayList<String> getStudents() {
    return students;   // ❌ 위험! 내부 객체의 주소 노출
}

// 사용자가
교실.getStudents().add("악성");   // 교실 내부 students에도 반영!
```

해결:

```java
public ArrayList<String> getStudents() {
    return new ArrayList<>(students);   // ✅ 복사본 반환
}
```

### 한 줄 요약

> **생성자 = 객체의 출생 신고. 모든 인스턴스 변수를 초기화하는 책임. 반환 타입 없음, 이름 = 클래스명. mutable 매개변수는 방어적 복사.**

---

## 6. CED Topic 3.5 — 메서드: 작성하는 법 (Methods: How to Write Them)

### 왜 메서드가 필요한가

객체가 단순히 데이터만 가지고 있으면 그냥 "구조체(struct)"일 뿐이다. 객체의 진짜 힘은 **데이터를 다루는 행동을 함께 가진다**는 것. 그 행동이 메서드다.

### 메서드의 4가지 종류

| 종류 | 반환 타입 | 매개변수 | 용도 |
|-----|---------|--------|-----|
| **Accessor (getter)** | non-void | 없음 | 필드 값 읽기 |
| **Mutator (setter)** | `void` | 1개 | 필드 값 변경 |
| **일반 비즈니스 메서드** | 다양 | 다양 | 객체의 행동 |
| **Helper 메서드** | 다양 | 다양 | 클래스 내부 보조 (`private`) |

### CED 3.5.A.3 — "Return by Value" — 비-void 메서드의 반환 메커니즘

> **CED 원문 (3.5.A.3)**: "In non-void methods, a return expression compatible with the return type is evaluated, and the value is returned. This is referred to as **return by value**."
>
> **번역**: 비-void 메서드에서 반환 타입과 호환되는 return 식이 평가되고 그 값이 반환된다. 이를 **"return by value"**라 한다.

#### "Return by Value"의 정확한 의미

> **return by value = 메서드가 값을 돌려줄 때 그 값의 복사본을 반환자에게 전달하는 방식.**

primitive를 반환하면 → 그 값의 복사본 반환. 호출자가 받은 값을 변경해도 메서드 내부 변수에 영향 없음.

```java
public int getAge() {
    return age;          // age의 값 복사본 반환
}

int x = obj.getAge();    // x는 age의 복사본
x = 999;                 // x만 바뀜, obj의 age는 무관
```

#### 객체 참조를 반환할 때는?

객체 참조도 **참조 자체(주소)의 복사본**이 반환된다. 그러나 같은 객체를 가리킨다 → 호출자가 그 객체 내부를 변경하면 반영. (CED 3.6.A.2와 연결, 캡슐화 구멍의 원인)

#### 왜 이 용어를 정확히 알아야 하는가

CED 공식 용어. MCQ 보기에 "return by value", "pass by value" 같은 정확한 표현으로 등장 가능. 한글 "값 반환"으로만 알고 있으면 영문 보기를 헷갈릴 수 있다.

### void vs non-void

#### void 메서드

```java
public void setAge(int age) {
    this.age = age;
}

public void doubleSize() {
    width *= 2;
    height *= 2;
}
```

**값을 돌려주지 않는** 메서드. **상태 변경, 출력, 부수 효과(side effect)**가 목적.

#### non-void 메서드

```java
public int getAge() {
    return age;
}

public double getArea() {
    return width * height;
}
```

**값을 돌려주는** 메서드. 반환 타입을 반드시 명시해야 하고, **모든 실행 경로에서 `return` 문이 필요**.

### `return` 문의 규칙

#### 규칙 1: non-void는 반드시 return

```java
public int getAge() {
    return age;   // 빠뜨리면 컴파일 에러
}
```

#### 규칙 2: 모든 경로에서 return

```java
// ❌ 컴파일 에러
public int compare(int a, int b) {
    if (a > b) return 1;
    if (a < b) return -1;
    // a == b일 때 return 없음!
}

// ✅ OK
public int compare(int a, int b) {
    if (a > b) return 1;
    if (a < b) return -1;
    return 0;
}
```

#### 규칙 3: return 이후의 코드 (Unreachable Code)

```java
public int getValue() {
    return 42;
    System.out.println("이 코드는 절대 실행 안 됨");   // ❌ 컴파일 에러!
}
```

`return` 다음에 코드를 쓰면 **컴파일 에러** (unreachable statement). Java는 도달할 수 없는 코드를 허용하지 않는다.

### 메서드 매개변수 — Pass by Value의 본질

여기가 가장 중요한 개념이다. 천천히 풀어 설명한다.

#### Java의 절대 원칙

> **Java는 모든 매개변수를 "값으로(by value)" 전달한다. 예외 없음.**

이 원칙이 시험에서 가장 많이 변형되어 출제된다. **"값"의 의미가 타입에 따라 다른 것**이 핵심.

#### Primitive의 경우 — 값 자체가 복사됨

```java
public static void changeIt(int x) {
    x = 999;
}

int num = 5;
changeIt(num);
System.out.println(num);   // 5 (변경 안 됨)
```

**메커니즘**:
1. `changeIt(num)`을 호출하면 `num`의 값(5)이 매개변수 `x`에 **복사**된다.
2. 메서드 안에서 `x = 999`는 복사본을 변경할 뿐.
3. 원본 `num`은 그대로 5.

```
호출 전:    [num | 5]
호출 시:    [num | 5]  →  [x | 5]  (5가 복사됨)
x = 999:   [num | 5]  →  [x | 999]
호출 후:    [num | 5]
```

#### 참조 타입의 경우 — 주소가 복사됨

```java
public static void changeIt(int[] arr) {
    arr[0] = 999;
}

int[] nums = {1, 2, 3};
changeIt(nums);
System.out.println(nums[0]);   // 999 (변경됨!)
```

**메커니즘**:
1. `nums`는 배열의 **주소**를 가지고 있다 (예: 주소 #1000, 그 주소에 {1,2,3} 저장).
2. `changeIt(nums)`를 호출하면 **주소가 복사**된다 → `arr`도 주소 #1000.
3. `arr[0] = 999`는 주소 #1000의 객체를 변경 → {999, 2, 3}.
4. `nums`도 같은 주소 #1000을 보고 있으므로 같은 객체 → 변경된 결과를 봄.

```
호출 전:    [nums | 주소#1000] → [힙: 1, 2, 3]
호출 시:    [nums | 주소#1000] → [힙: 1, 2, 3]
            [arr  | 주소#1000] ──↗
arr[0]=999: [힙: 999, 2, 3]
호출 후:    [nums | 주소#1000] → [힙: 999, 2, 3]   ← 변경 보임!
```

#### 그러나! 참조 자체를 바꾸면 반영 안 됨

```java
public static void replaceIt(int[] arr) {
    arr = new int[]{7, 8, 9};   // arr이 새 배열을 가리키게 함
}

int[] nums = {1, 2, 3};
replaceIt(nums);
System.out.println(nums[0]);   // 1 (변경 안 됨)
```

**메커니즘**:
1. `arr`이 처음에 주소 #1000을 가짐 (`nums`와 같은 곳).
2. `arr = new int[]{7,8,9}`는 새 배열(주소 #2000)을 만들어 `arr`에 대입.
3. **`arr`만** 주소 #2000을 가리킴. `nums`는 여전히 #1000을 가리킴.
4. 호출 후 `nums`를 통해 보면 여전히 #1000 = {1, 2, 3}.

```
호출 전:    [nums | 주소#1000] → [힙: 1, 2, 3]
호출 시:    [nums | 주소#1000] → [힙: 1, 2, 3]
            [arr  | 주소#1000] ──↗
arr = new:  [nums | 주소#1000] → [힙: 1, 2, 3]
            [arr  | 주소#2000] → [힙: 7, 8, 9]
호출 후:    [nums | 주소#1000] → [힙: 1, 2, 3]   ← 변경 안 보임
```

#### 정리표 — "이 메서드 호출 후 원본은 바뀌나?"

| 메서드가 한 일 | 호출자 입장에서 변화 보임? |
|------------|----------------------|
| primitive 매개변수 변경 (`x = 999`) | ❌ 안 보임 |
| 객체 매개변수 자체 재대입 (`arr = new...`) | ❌ 안 보임 |
| 객체 매개변수가 가리키는 객체의 내부 변경 (`arr[0] = ...`, `obj.setX(...)`) | ✅ 보임 |
| ArrayList의 add/remove (`list.add(...)`) | ✅ 보임 |

#### 시험 빈출 트레이싱

```java
public static void swap(int[] a, int[] b) {
    int[] temp = a;
    a = b;
    b = temp;
}

int[] x = {1, 2};
int[] y = {3, 4};
swap(x, y);
System.out.println(x[0] + ", " + y[0]);
```

**답**: `1, 3` (변경 없음). `swap` 안에서는 **매개변수 a, b의 값만 바뀜**. 호출자의 x, y는 그대로.

### Method Overloading — 같은 이름의 다른 메서드

```java
public class Calculator {
    public int add(int a, int b) { return a + b; }
    public double add(double a, double b) { return a + b; }
    public int add(int a, int b, int c) { return a + b + c; }
}
```

같은 이름이지만 매개변수 타입·개수가 달라서 구분됨. **시그니처(signature)** = 메서드 이름 + 매개변수 타입 목록.

#### 규칙

- 시그니처가 다르면 같은 이름 OK
- **반환 타입만 다른 건 오버로딩 아님** — 컴파일 에러

```java
// ❌ 컴파일 에러
public int print(int x) { ... }
public void print(int x) { ... }   // 시그니처 같음
```

### 한 줄 요약

> **메서드 = 객체의 행동. void는 부수효과, non-void는 값 반환. Java는 모든 매개변수를 값으로 전달 — primitive는 값 복사, 객체는 주소 복사 (= 같은 객체 공유).**

---

## 7. CED Topic 3.6 — 메서드: 객체 참조 전달과 반환 (Methods: Passing and Returning References)

### 왜 이 토픽을 별도로 다루는가

앞에서 매개변수가 어떻게 전달되는지 봤다. 여기서는 **반환** 측면과 **캡슐화 구멍**을 깊게 다룬다.

### 캡슐화 구멍 1 — 생성자에서 (앞 섹션 복습)

```java
public class Box {
    private int[] arr;
    
    public Box(int[] arr) {
        this.arr = arr;   // ❌ 외부 배열의 주소를 그대로 저장
    }
}
```

해결: `this.arr = new int[arr.length]` + 요소 복사 (또는 ArrayList면 `new ArrayList<>(arr)`).

### 캡슐화 구멍 2 — Getter에서

```java
public class Box {
    private int[] arr;
    
    public int[] getArr() {
        return arr;   // ❌ 내부 배열의 주소를 노출
    }
}

// 외부가 마음대로
Box box = new Box(...);
box.getArr()[0] = 999;   // 내부 arr이 변경됨!
```

해결:

```java
public int[] getArr() {
    int[] copy = new int[arr.length];
    for (int i = 0; i < arr.length; i++) {
        copy[i] = arr[i];
    }
    return copy;
}
```

### 캡슐화 구멍 3 — 메서드 매개변수로 받은 객체를 저장

```java
public class Garage {
    private Car car;
    
    public void store(Car c) {
        this.car = c;   // ❌ 외부 Car의 주소를 저장
    }
}

Car myCar = new Car(...);
Garage g = new Garage();
g.store(myCar);
myCar.setSpeed(200);   // 외부에서 변경 → garage 내부 car도 변경됨
```

해결: Car의 복사본을 만들거나 (Car에 복사 생성자 필요), 또는 Garage가 받자마자 새 Car를 만들거나.

### 같은 타입 매개변수의 private 접근 — CED 3.6.A.3 빈출 함정

> **"메서드는 매개변수가 가리키는 객체의 private 데이터에 접근할 수 없다 — 단, 매개변수가 메서드를 둘러싼 클래스와 같은 타입이면 가능."**

이게 처음 들으면 헷갈리는 규칙이다. 풀어 설명한다.

#### 비유 — "같은 회사 직원끼리는 서로 사물함을 본다"

회사에서 사물함(`private` 필드)은 본인만 접근 가능. 그런데 **같은 회사 직원끼리**는 일종의 "내부자 권한"이 있어서, 다른 직원의 사물함도 들여다볼 수 있다고 하자. 다른 회사 사람은 절대 안 됨.

Java도 동일. **같은 클래스의 인스턴스끼리는 서로의 private 필드에 접근 가능**.

#### 코드 예

```java
public class Point {
    private int x, y;
    
    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
    
    // 매개변수 other도 Point 타입 (같은 클래스!)
    public boolean sameLocation(Point other) {
        return this.x == other.x && this.y == other.y;
        //                          ^^^^^^^ ← OK! 같은 Point 클래스이므로
    }
    
    public double distanceTo(Point other) {
        int dx = this.x - other.x;       // ✅ OK
        int dy = this.y - other.y;       // ✅ OK
        return Math.sqrt(dx * dx + dy * dy);
    }
}
```

`other.x`와 `other.y`는 다른 Point 객체의 **private** 필드인데도 접근 가능하다 — `sameLocation`이 Point 클래스 안에 정의되어 있고, 매개변수 `other`도 Point 타입이기 때문.

#### 다른 클래스라면 불가능

```java
public class Rectangle {
    public boolean sameAs(Point p) {
        return p.x == 0;      // ❌ 컴파일 에러! Rectangle은 Point의 private에 못 접근
    }
}
```

`Rectangle` 클래스 안에서 `Point` 타입 매개변수의 `private` 필드 접근은 차단.

#### 왜 이 규칙이 존재하는가

같은 클래스의 두 인스턴스가 **서로 비교/연산**해야 하는 일이 자주 있다 (예: 두 점의 거리, 두 학생의 점수 비교). 매번 getter를 호출하면 코드가 길고 복잡해진다. 같은 클래스 내부 코드끼리는 서로 "신뢰"할 수 있다고 보고 직접 접근을 허용한다.

#### 시험 출제 형태

```java
public class Student {
    private double gpa;
    
    public boolean smarterThan(Student other) {
        return this.gpa > other.gpa;   // ← 이게 컴파일 되나?
    }
}
```

**답: 컴파일된다.** `other`가 `Student` 타입이고 코드가 `Student` 클래스 안에 있으므로 `other.gpa` 직접 접근 OK.

### Primitive 반환은 항상 안전

```java
public int getX() {
    return x;   // ✅ int는 값 복사. 외부가 받아도 원본 무관.
}
```

primitive는 **값 자체가 복사**되므로 외부가 어떻게 다뤄도 원본 영향 없음.

### String 반환도 항상 안전

```java
public String getName() {
    return name;   // ✅ String은 immutable. 외부가 변경할 방법 없음.
}
```

String은 한 번 만들어지면 내용을 바꿀 수 없는 **불변** 객체. 그래서 주소 노출해도 안전.

### 판별 한 줄

> **반환 타입이 primitive 또는 immutable(String)이면 안전. 가변 참조(배열, ArrayList, 일반 객체)면 방어적 복사 필요.**

### 시험 출제 패턴

MCQ에서 코드를 보여주고 "이 클래스의 캡슐화 결함은?" 묻는다. 위 3가지 구멍 중 하나가 답.

FRQ Q2에서 "ArrayList를 매개변수로 받는 생성자"가 나오면 **방어적 복사가 별도 1점**으로 채점.

---

## 8. CED Topic 3.7 — Class Variables and Methods (static — 클래스 자체에 속하는 것)

### CED 공식 용어 — "Class Variable" / "Class Method"

> **CED 원문 (3.7.B.1)**: "**Class variables** belong to the class, with all objects of a class sharing a single copy of the class variable. Class variables are designated with the **static** keyword before the variable type."
>
> **번역**: 클래스 변수(class variable)는 클래스에 속하고, 그 클래스의 모든 객체가 단 하나의 사본을 공유한다. 변수 타입 앞의 **static** 키워드로 지정.

#### 두 용어는 같은 뜻

| CED 공식 용어 | 비공식 통용 용어 | 의미 |
|------------|--------------|-----|
| **Class variable** | static variable | 클래스에 속한 변수 (모든 객체 공유) |
| **Class method** | static method | 클래스에 속한 메서드 (인스턴스 없이 호출) |
| **Instance variable** | (동일 표현) | 객체 각자 가진 변수 |
| **Instance method** | (동일 표현) | 객체 통해 호출하는 메서드 |

시험 문제에서 "class variable"이라는 표현을 보면 곧 **static 변수**임을 즉시 떠올려야 한다. 한글로만 "static 변수"로 알고 있으면 영문 보기가 낯설 수 있다.

### 왜 static이 존재하는가

지금까지 본 모든 변수·메서드는 **인스턴스에 속한다**. 즉, 객체 하나하나가 자기만의 사본을 가진다. 그러나 가끔 **모든 객체가 공유해야 할 데이터**나 **객체 없이도 호출하고 싶은 메서드**가 필요하다.

### 비유 — 학교의 "총 학생 수"

학교에 학생이 1000명 있다. 각 학생은 자기 이름, 학년, 점수 같은 **개인 정보**를 가진다 (인스턴스 변수).

그러나 "총 학생 수 = 1000"는 **개인 정보가 아니다**. 학교 전체에 하나만 있어야 할 정보. 학생 객체마다 "총 학생 수 = 1000"을 따로 저장하면 1000개의 사본이 생긴다 — 낭비. 게다가 한 학생이 그 값을 1001로 바꾸면 다른 학생들과 일치 안 함.

이 정보는 **학생 클래스 자체**에 한 번만 저장되어야 한다. 그게 static.

### static 변수 코드

```java
public class Student {
    private String name;             // 인스턴스 변수: 학생마다 다름
    private static int count = 0;    // static 변수: 모든 학생이 공유
    
    public Student(String name) {
        this.name = name;
        count++;   // 학생 만들어질 때마다 count 증가
    }
    
    public static int getCount() {   // static 메서드: 객체 없이 호출
        return count;
    }
}

// 사용
Student s1 = new Student("Alice");   // count = 1
Student s2 = new Student("Bob");     // count = 2
Student s3 = new Student("Carol");   // count = 3

System.out.println(Student.getCount());   // 3 (클래스 이름으로 호출)
```

### static의 메모리 시각화

```
힙(Heap):
┌────────────────────┐  ┌────────────────────┐  ┌────────────────────┐
│ Student 객체 1     │  │ Student 객체 2     │  │ Student 객체 3     │
│ name = "Alice"     │  │ name = "Bob"       │  │ name = "Carol"     │
└────────────────────┘  └────────────────────┘  └────────────────────┘

Method Area (클래스 영역):
┌──────────────────────┐
│ Student 클래스       │
│ count = 3            │  ← 단 하나만 존재
└──────────────────────┘
```

각 객체에는 `name`만 있고, `count`는 **클래스 자체**에 하나만 있다.

### static 메서드 — 인스턴스 없이 호출 가능

```java
public class Student {
    public static int getCount() { return count; }
}

Student.getCount();   // 객체 없이 클래스 이름으로 직접 호출
```

#### 비교

| 종류 | 호출 방법 |
|-----|--------|
| Instance method | `객체참조.메서드()` (예: `s1.getName()`) |
| Static method | `클래스이름.메서드()` (예: `Student.getCount()`) |

### 우리가 이미 써온 static — Math, Integer, System

여러분이 Unit 1부터 써온 코드에 static이 잔뜩 있다. 이제 그 의미를 안다.

| 코드 | 의미 |
|-----|-----|
| `Math.abs(x)` | Math 클래스의 static 메서드 abs |
| `Math.sqrt(25)` | Math 클래스의 static 메서드 sqrt |
| `Math.PI` | Math 클래스의 static 변수(상수) PI |
| `Integer.parseInt("42")` | Integer 클래스의 static 메서드 parseInt |
| `Integer.MAX_VALUE` | Integer 클래스의 static 상수 |
| `System.out.println(...)` | System 클래스의 static 변수 out |

이들이 왜 static인가? **객체의 상태와 무관한 기능**이기 때문이다. `Math.sqrt(16)`은 어떤 Math 객체에서 호출하든 항상 4.0. 객체마다 다를 이유가 없다 → static.

### Static의 핵심 제약 — 인스턴스 변수에 접근 불가

```java
public class Test {
    private int x;             // instance
    private static int y;      // static
    
    public static void foo() {
        y = 10;     // ✅ OK — static에서 static 접근
        x = 10;     // ❌ 컴파일 에러!
    }
}
```

#### 왜 안 되는가

`x`는 **인스턴스 변수** — 어떤 인스턴스의 x를 말하는가? `Test.foo()`처럼 **인스턴스 없이** 호출되면 어느 객체의 x도 알 수 없다. → 컴파일러가 차단.

### static에서 `this` 사용 불가

```java
public static void foo() {
    System.out.println(this);   // ❌ 컴파일 에러
}
```

`this`는 "현재 인스턴스". static에는 인스턴스가 없으므로 `this`도 없음.

### static final — 상수

```java
public static final double PI = 3.14159;
public static final int MAX_STUDENTS = 1000;
```

`final` = 값 변경 불가 = **상수**.
`static final` = 모든 인스턴스가 공유하는 상수.
관례: 대문자 + 언더스코어 (`MAX_STUDENTS`, `DEFAULT_NAME`).

### 언제 static을 쓰는가 — 판별 기준

> **"이 변수/메서드는 객체의 개별 상태와 무관한가?"**
> - YES → static
> - NO (객체마다 다른 데이터/행동을 다룸) → instance

**FRQ Q2의 클래스는 거의 모두 instance**. "Book", "Account", "Player" 같은 객체는 각자의 상태를 가지므로 인스턴스. static은 가끔 카운터(`총 객체 수`)나 상수(`MAX_VALUE`) 정도로만 등장.

### 한 줄 요약

> **static = 클래스 자체에 속함. 모든 인스턴스가 공유 또는 인스턴스 없이 호출 가능. 인스턴스 변수와 `this`는 사용 불가.**

---

## 9. CED Topic 3.8 — Scope and Access (변수가 살아있는 영역)

### 왜 scope가 있는가

변수 이름은 한정된 자원이다. 큰 프로그램에서 모든 변수가 전역(어디서든 접근 가능)이면 이름 충돌이 끔찍해진다. **변수가 사용 가능한 영역을 제한**하는 메커니즘이 scope.

### 비유 — 학교의 출입증

여러분의 학생증으로:
- **본인 교실**에는 들어갈 수 있음 (작은 scope)
- **본인 학년 건물**에도 들어갈 수 있음 (중간 scope)
- **다른 학년 건물**에는 못 들어감 (scope 밖)

변수도 마찬가지로 "어디까지 접근 가능한가" 영역이 있다.

### Java의 scope 4계층

```java
public class ScopeDemo {
    private int instanceVar = 10;       // ① 클래스 scope (인스턴스)
    private static int classVar = 20;   // ② 클래스 scope (static)
    
    public void method(int parameter) { // ③ 메서드 scope (매개변수)
        int local = 30;                  // ④ 블록 scope (지역 변수)
        
        for (int i = 0; i < 5; i++) {    // ⑤ for 블록 scope (i, loopVar)
            int loopVar = 40;
            // 여기서는 instanceVar, classVar, parameter, local, i, loopVar 모두 접근 가능
        }
        // 여기서는 i, loopVar 접근 불가 (for 블록 끝남)
        
        // 여기서는 instanceVar, classVar, parameter, local 접근 가능
    }
    // 여기서는 parameter, local 접근 불가 (메서드 끝남)
}
```

### Scope 표

| 변수 종류 | 유효 범위 | 접근 제한자 가능? |
|---------|--------|----------------|
| Instance variable | 클래스 전체 | `private`/`public` |
| Static variable | 클래스 전체 | `private`/`public` |
| 매개변수 (Parameter) | 그 메서드 전체 | ❌ |
| 지역 변수 (Local variable) | 선언된 블록 `{}` 안 | ❌ |

### 왜 local 변수에는 접근 제한자를 못 쓰는가

지역 변수는 **그 메서드/블록 안에서만 존재**한다. 외부에서 접근 자체가 불가능하므로 `private`/`public`이 의미 없다. Java 문법이 처음부터 막고 있다.

```java
public void method() {
    private int x = 5;   // ❌ 컴파일 에러
}
```

### Shadowing — 같은 이름이 두 개일 때

```java
public class Box {
    private int value = 100;        // ① 인스턴스 변수
    
    public void demo(int value) {   // ② 매개변수 (shadowing!)
        System.out.println(value);       // 매개변수 출력
        System.out.println(this.value);  // 인스턴스 변수 출력
    }
}

Box b = new Box();
b.demo(20);   // 출력: 20, 100
```

#### 메커니즘

같은 이름이 여러 scope에 있으면 **가장 안쪽(가장 좁은) scope의 것이 우선**. 위 예에서 `demo` 메서드 안에서 `value`는 매개변수를 가리킨다 (인스턴스 변수가 가려짐 = shadowing).

#### 왜 shadowing이 자주 일어나는가

생성자/setter에서 매개변수 이름을 필드 이름과 같게 짓는 게 관례:

```java
public Box(int value) {
    this.value = value;   // 왼쪽 = 필드, 오른쪽 = 매개변수
}
```

이름이 같으니 의도가 명확. 그래서 **shadowing을 의도적으로** 쓰고, `this.`로 필드를 명시한다.

### Shadowing의 함정 — `value = value`

```java
public void setValue(int value) {
    value = value;   // 매개변수에 매개변수 대입 — 아무 일도 안 함!
}
```

**왜 안 되는가**: 메서드 안에서 `value`는 매개변수. `value = value`는 매개변수에 매개변수를 다시 넣는 것. **인스턴스 필드 `value`는 안 바뀜**. setter 의미가 없는 코드.

#### 해결 — `this.`

```java
public void setValue(int value) {
    this.value = value;   // 왼쪽 = 인스턴스 필드, 오른쪽 = 매개변수
}
```

### FRQ 안전 규칙 — 필드 대입에는 항상 `this.`

```java
// ✅ 권장 패턴
public Box(int value) {
    this.value = value;
}

public void setValue(int value) {
    this.value = value;
}
```

이론상 매개변수 이름이 다르면 `this.` 생략 가능. 하지만 FRQ에서는 **항상 `this.`를 붙이는 게 안전**:
1. 채점자가 "이건 필드"임을 한눈에 안다
2. 나중에 매개변수 이름을 바꿔도 버그 없음
3. 일관된 스타일

### 한 줄 요약

> **Scope = 변수가 살아있는 영역. 안쪽 scope가 우선(shadowing). 필드 대입에는 항상 `this.` 붙이면 안전.**

---

## 10. CED Topic 3.9 — this Keyword (자기 자신을 가리키는 방법)

### 왜 this가 필요한가

객체 안에서 "**자기 자신**"을 가리킬 방법이 필요하다. 예를 들어:

1. shadowing 상황에서 인스턴스 필드를 명시하려고 → `this.value = value`
2. 자기 자신을 다른 메서드에 인자로 넘기려고 → `list.add(this)`
3. 자기 자신의 메서드를 호출할 때 (생략 가능) → `this.getName()`

이 모든 경우에 "지금 이 메서드를 호출한 객체"를 가리키는 키워드가 `this`.

### 비유 — 일인칭 시점

여러분이 일기를 쓸 때 "**나**는 오늘 학교에 갔다"라고 쓴다. 다른 사람이 같은 일기를 읽어도 "나"는 항상 일기 작성자를 가리킨다.

`this`도 마찬가지. 메서드가 호출될 때 그 메서드를 호출한 객체를 "나(this)"라고 부른다.

```java
public class Student {
    private String name;
    
    public void introduce() {
        System.out.println("내 이름은 " + this.name);
    }
}

Student a = new Student("철수");
Student b = new Student("영희");

a.introduce();   // "내 이름은 철수" — this == a
b.introduce();   // "내 이름은 영희" — this == b
```

같은 메서드지만 호출하는 객체에 따라 `this`가 다른 객체를 가리킨다.

### this의 3가지 용법

#### 용법 1: Shadowing 해결

```java
public Point(int x, int y) {
    this.x = x;   // this.x = 필드, x = 매개변수
    this.y = y;
}
```

가장 흔한 용법. 생성자/setter에서 필수.

#### 용법 2: 자기 자신을 다른 메서드에 전달

```java
public class Circle {
    public void addToList(ArrayList<Circle> list) {
        list.add(this);   // 현재 Circle 객체를 리스트에 추가
    }
}
```

#### 용법 3: 자기 자신의 메서드 호출 (생략 가능)

```java
public class Rectangle {
    private int width, height;
    
    public int getArea() {
        return this.width * this.height;   // this. 생략 가능
        // return width * height;          // 동일
    }
    
    public int getPerimeter() {
        return 2 * (width + height);       // 같은 인스턴스의 다른 메서드 호출 시 this. 생략 가능
    }
}
```

### this를 쓸 수 있는 곳 / 못 쓰는 곳

| 위치 | this 사용 |
|-----|---------|
| Instance method 안 | ✅ |
| Constructor 안 | ✅ |
| **Static method 안** | ❌ **컴파일 에러** |

### 왜 static에서는 못 쓰는가 — 다시

static 메서드는 **인스턴스 없이** 호출된다. 그러므로 "현재 인스턴스"가 없음. `this`가 가리킬 게 없음 → Java가 차단.

### 시험 단골 함정

```java
public class MyClass {
    private int val;
    
    public MyClass(int val) {
        this.val = val;        // (A) ✅ OK
    }
    
    public static void reset() {
        this.val = 0;          // (B) ❌ 컴파일 에러 (static에서 this 불가)
    }
    
    public void show() {
        System.out.println(this.val);   // (C) ✅ OK
    }
}
```

(B)가 문제. static에서는 `this` 절대 불가.

### 한 줄 요약

> **`this` = 현재 객체 자기 자신. shadowing 해결, 자기 전달, 자기 메서드 호출의 3가지 용법. static에서는 사용 불가.**

---

## 11. CED Topic 3.7 (계속) — final 키워드 — 상수와 변경 불가

### 왜 final이 필요한가

가끔 "한 번 설정하면 절대 바뀌지 않아야 할 값"이 있다. 원주율 π, 최대 학생 수, 전화번호 자릿수 등. 이런 값을 **변경 불가능**하게 만들어 실수를 방지하고 의도를 명확히 하는 키워드가 `final`.

### final 변수의 의미

```java
final int x = 5;
x = 10;   // ❌ 컴파일 에러
```

`final`이 붙은 변수는 **재대입 불가능**.

### static final — 상수

```java
public class Circle {
    public static final double PI = 3.14159;
    public static final int MAX_RADIUS = 100;
}
```

- `static`: 모든 인스턴스가 공유 (객체마다 사본 만들 필요 없음)
- `final`: 변경 불가 = 상수
- 관례: **대문자 + 언더스코어** (`PI`, `MAX_RADIUS`)

사용:

```java
double area = Circle.PI * r * r;
if (radius <= Circle.MAX_RADIUS) { ... }
```

### final on Reference — 헷갈리는 부분

```java
final int[] arr = {1, 2, 3};

arr[0] = 999;          // ✅ OK (배열 내부 변경)
arr = new int[]{4,5,6}; // ❌ 컴파일 에러 (재대입)
```

#### 왜 첫 번째는 OK?

`final`은 변수의 **바인딩(연결)**을 고정한다. `arr` 변수가 가리키는 **주소를 바꿀 수 없다**는 의미. 그러나 그 주소에 있는 객체의 **내용**은 자유롭게 변경 가능.

#### 시각화

```
final int[] arr = {1, 2, 3};
                 ┌────────────┐
[arr | 주소#1000] → [힙: 1, 2, 3]
                 └────────────┘
                 
arr[0] = 999:    [arr | 주소#1000] → [힙: 999, 2, 3]   ← OK
arr = new...:    [arr | ???]                            ← final이 차단
```

### 시험 출제 형태

```java
final int x = 5;
x = 10;                        // (A)

final int[] arr = {1, 2, 3};
arr[0] = 999;                   // (B)
arr = new int[]{9, 8, 7};       // (C)
```

컴파일되는 건? **(B)만**. (A)는 primitive 재대입 불가, (C)는 reference 재대입 불가.

### 한 줄 요약

> **`final` = 변수의 재대입 금지. primitive면 값 고정, reference면 주소 고정 (객체 내부는 변경 가능). static final = 상수, 대문자 관례.**

---

## 12. 종합 시각 — 빈 종이에서 클래스 만들기

### FRQ Q2를 푸는 머릿속 흐름

이 단원 전체의 **종착점**. 빈 종이에 클래스를 작성할 때 머릿속에서 이런 순서로 사고한다.

#### 1단계: 클래스 이름 정하기

지문이 "Book 클래스를 작성하시오"라면:

```java
public class Book {
    
}
```

#### 2단계: 인스턴스 변수 결정 (모두 private)

지문이 "Book은 제목, 저자, 페이지 수를 가진다"라면:

```java
public class Book {
    private String title;
    private String author;
    private int pages;
}
```

자문: "이게 정말 모든 책에 공통? 책마다 다름? → 인스턴스 변수." "모든 책에 같은 값? → static 변수."

#### 3단계: 생성자 작성

지문이 "생성자 `Book(String t, String a, int p)`"라면:

```java
public Book(String t, String a, int p) {
    this.title = t;
    this.author = a;
    this.pages = p;
}
```

체크:
- 클래스명과 동일?
- 반환 타입 없음?
- 모든 인스턴스 변수 초기화?
- mutable 매개변수면 방어적 복사?

#### 4단계: Getter 작성 (필요한 것만)

지문이 "`public String getTitle()`"이라 명시하면:

```java
public String getTitle() {
    return title;
}
```

지문에서 명시한 메서드만 작성. 안 시킨 getter는 굳이 안 만든다 (시간 낭비).

#### 5단계: Setter / 비즈니스 메서드 작성

지문이 "`public void addPages(int n)`: n ≥ 0이면 pages에 더함"이라면:

```java
public void addPages(int n) {
    if (n >= 0) {
        pages += n;
    }
}
```

체크:
- 시그니처 정확?
- 반환 타입 맞음?
- 검증 로직 (precondition) 처리?
- non-void면 모든 경로에서 return?

#### 완성

```java
public class Book {
    private String title;
    private String author;
    private int pages;
    
    public Book(String t, String a, int p) {
        this.title = t;
        this.author = a;
        this.pages = p;
    }
    
    public String getTitle() {
        return title;
    }
    
    public void addPages(int n) {
        if (n >= 0) {
            pages += n;
        }
    }
    
    public boolean isLong() {
        return pages > 300;
    }
}
```

### FRQ Q2 채점 체크리스트 (제출 직전)

- [ ] `public class ClassName`로 시작
- [ ] 모든 인스턴스 변수 `private`
- [ ] 생성자 이름 = 클래스 이름 (대소문자 일치)
- [ ] 생성자 반환 타입 없음 (`void`도 안 씀)
- [ ] 모든 인스턴스 변수가 생성자에서 초기화됨
- [ ] mutable 매개변수 (ArrayList, 배열)는 방어적 복사
- [ ] 메서드 시그니처가 지문과 정확히 일치
- [ ] non-void 메서드는 모든 경로에서 `return`
- [ ] `this.field = field` 패턴으로 shadowing 해결
- [ ] precondition 검증 로직 포함
- [ ] **`toString` 오버라이드 작성 금지** (CED 1.15.A.5 EXCLUSION — 2025-26 시험 범위 외. 지문이 객체 정보 반환을 요구하면 `getInfo()`, `getDescription()` 같은 일반 메서드명 사용)
- [ ] **`equals` 오버라이드 작성 금지** (CED 2.6.B.3 EXCLUSION — Object의 equals 재정의는 시험 범위 외)

### 자주 감점되는 함정 Top 10

| # | 함정 | 결과 |
|---|-----|------|
| 1 | 인스턴스 변수를 `public`으로 | -1 |
| 2 | 생성자에 `void` 또는 다른 반환 타입 | -1 (실제로는 메서드가 됨) |
| 3 | 일부 인스턴스 변수 초기화 누락 | -1 |
| 4 | 메서드 시그니처가 지문과 다름 (예: `int` 대신 `double`) | -1 |
| 5 | non-void 메서드에 `return` 없음 | -1 |
| 6 | `this.` 빠뜨려서 shadowing으로 필드 안 바뀜 | -1 |
| 7 | `static` 메서드에서 인스턴스 변수 직접 접근 | -1 |
| 8 | mutable 매개변수에 방어적 복사 안 함 | -1 |
| 9 | precondition 검증 누락 (음수 체크 등) | -1 |
| 10 | `toString()` 오버라이드 작성 (EXCLUSION 위반) | -1 |

---

## 13. 통합 원리 — Unit 3를 관통하는 한 가지 진실

### 모든 게 결국 "참조"의 이해

Unit 3에서 가장 중요한 단 하나의 원리:

> **Java에서 객체는 항상 "참조(reference)"로 다뤄진다. 변수는 객체 자체가 아니라 객체의 주소를 담는다. 대입·매개변수 전달·반환은 모두 주소의 복사다. 두 변수가 같은 주소를 가지면 같은 객체를 공유한다.**

이 한 문장에서 다음 모든 게 파생된다:

| 개념 | 이 원리의 적용 |
|-----|------------|
| 캡슐화 | 외부와 내부가 같은 객체 공유하면 보호 깨짐 → `private` + 방어적 복사 |
| 생성자에서 mutable 저장 | `this.field = param`은 주소 복사 → 외부와 같은 객체 → 방어적 복사 필요 |
| Getter에서 mutable 반환 | `return field`는 주소 노출 → 외부가 같은 객체 접근 → 방어적 복사 필요 |
| Pass-by-value (객체) | 매개변수에 주소 복사 → 메서드 안에서 객체 변경하면 호출자도 봄 |
| `this` | 현재 객체의 참조 — "지금 이 메서드를 호출한 객체의 주소" |
| static | 인스턴스에 속하지 않음 → 객체 참조 무관 → `this` 사용 불가 |
| `final` on reference | 주소 고정, 객체 내부는 자유 |

### 시험 사고 흐름 — "이 코드 실행 후 원본은 바뀌나?"

```
Q1. 변수가 primitive (int/double/boolean)인가?
    YES → 바뀌지 않음 (값 복사)
    NO → Q2로

Q2. 변수가 immutable 객체 (String, Integer, Double)인가?
    YES → 바뀌지 않음 (변경 불가)
    NO → Q3로

Q3. 코드가 참조 자체를 재대입했는가? (var = new ...)
    YES → 바뀌지 않음 (다른 객체 가리킴)
    NO → Q4로

Q4. 코드가 객체의 내부 상태를 변경했는가? (var.set..., arr[i] = ..., list.add)
    YES → 바뀜 (같은 객체 공유)
```

이 4단계 흐름만 외우면 Unit 3의 모든 트레이싱 문제를 풀 수 있다.

---

## 14. 시험 직전 1분 요약 — 절대 까먹으면 안 될 것

### 클래스 작성 5규칙

1. `public class ClassName` (헤더는 항상 public)
2. 모든 인스턴스 변수 `private`
3. 생성자: 클래스명과 동일, 반환 타입 없음, 모든 필드 초기화
4. mutable 매개변수 받는 생성자는 방어적 복사
5. `toString`/`equals` 오버라이드 작성 안 함 (EXCLUSION)

### Default value 4가지

`int → 0`, `double → 0.0`, `boolean → false`, `참조 → null`

### Pass-by-value 진실

Java는 **항상** 값 전달. primitive는 값, 참조는 주소. 객체 내부 변경은 보임, 참조 재대입은 안 보임.

### static의 두 제약

- static method는 instance variable 직접 접근 불가
- static method에서 `this` 사용 불가

### 방어적 복사 판별

primitive와 String → 불필요. 배열·ArrayList·setter 있는 객체 → 필요.

### `this`의 3가지 용법

- shadowing 해결
- 자기 자신 전달
- 자기 메서드 호출 (생략 가능)

### `final`의 두 종류 효과

- primitive: 값 고정
- reference: 주소 고정 (내부는 자유)

---

## 15. 마지막으로 — 이 단원을 진짜 마스터했는지 자가진단

다음 5가지 질문에 망설임 없이 답할 수 있다면 Unit 3는 완전히 끝났다.

1. **"왜 인스턴스 변수는 private이어야 하는가?"** 
   → 캡슐화. 외부에서 직접 변경 못하게 막아 데이터 무결성 보장. 내부 구현을 바꿔도 외부 코드 영향 없게 함.

2. **"`new Student("Tom")`을 호출할 때 무슨 일이 일어나는가?"**
   → ① 힙에 새 Student 객체를 위한 메모리 할당. ② 모든 인스턴스 변수에 default value 부여. ③ 선언 시 초기화 식 실행. ④ 생성자 본체 실행 ("Tom"으로 name 설정). ⑤ 객체의 참조(주소)를 반환.

3. **"왜 `Integer.parseInt("42")`는 `Integer` 객체 없이 호출 가능한가?"**
   → `parseInt`가 static 메서드이기 때문. static 메서드는 클래스 자체에 속해서 인스턴스 없이 호출 가능. 문자열 → int 변환은 객체의 개별 상태와 무관해서 static이 적합.

4. **"생성자에서 `this.x = x;` 대신 `x = x;`로 쓰면 무슨 일이 일어나는가?"**
   → 매개변수에 매개변수를 대입할 뿐. 인스턴스 필드 x는 default value 그대로. shadowing 때문에 메서드 안에서 `x`는 매개변수를 가리키므로, `this.`를 빼면 필드를 못 가리킨다.

5. **"`final int[] arr = {1,2,3};` 후에 `arr[0] = 99`는 가능한가?"**
   → 가능. `final`은 `arr` 변수가 가리키는 **주소를 고정**할 뿐. 그 주소에 있는 배열의 내용은 자유롭게 변경 가능. `arr = new int[]{4,5,6}`처럼 주소 자체를 바꾸려는 건 불가.

5개 모두 1분 안에 답할 수 있다면 **Unit 3 만점 준비 완료**.

---

## 부록 A: 학습 자원 매핑

이 문서를 다 읽고 보충이 필요하면 다음 순서로:

| 보충 자료 | 언제 보는가 |
|---------|----------|
| `Unit3_강의노트.md` | 코드 예시가 더 필요할 때 |
| `Unit3_시험개념_딥다이브.md` | DD 형식 단편 정리가 필요할 때 |
| `MCQ_문제집.md` | 개념 이해 후 문제 적용 연습 |
| `FRQ_풀이해설.md` | FRQ Q2 실전 연습 |
| `시험전략_가이드.md` | 시간 배분, 답안 작성 요령 |

---

## 부록 B: CED 모든 EK 항목 매핑 검증

본 문서가 다룬 CED 2025-26 Unit 3의 모든 Essential Knowledge 항목 (College Board 공식 출처 기반):

### Topic 3.1 — Abstraction and Program Design
- **3.1.A.1** Abstraction은 복잡성 감소 → §2 (추상화 도입부)
- **3.1.A.2** Data abstraction → §2 (데이터 추상화)
- **3.1.A.3** Attribute / Instance variable / Class variable → §2, §4, §8
- **3.1.A.4** Procedural abstraction & Method decomposition → §2 (절차 추상화)
- **3.1.A.5** 매개변수의 일반화 효과 → §2 ("매개변수가 추상화의 일반화 도구")
- **3.1.A.6** 내부 구현 변경의 자유 → §2 ("추상화 덕분에 가능한 것")
- **3.1.A.7** 자연어/다이어그램 사전 설계 → §2 ("클래스 설계는 코드 작성 전에")

### Topic 3.2 — Impact of Program Design
- **3.2.A.1** System reliability → §2½ (3.2.A.1)
- **3.2.A.2** 사회·경제·문화 영향, 의도치 않은 해 → §2½ (3.2.A.2)
- **3.2.A.3** Open source / Proprietary 라이선스 → §2½ (3.2.A.3)

### Topic 3.3 — Anatomy of a Class
- **3.3.A.1** Data encapsulation, public/private 키워드 → §3
- **3.3.A.2** 클래스는 항상 public, class 키워드 → §4 ("① 클래스 헤더")
- **3.3.A.3** 생성자는 항상 public → §5 (생성자 6가지 특징, 3번 항목)
- **3.3.A.4** 인스턴스 변수는 객체 소유 → §3, §4 ("② 인스턴스 변수")
- **3.3.A.5** 인스턴스 변수는 private 권장 → §3, §4
- **3.3.A.6** 메서드 public/private 접근 범위 → §4 ("⑤ 변경자")

### Topic 3.4 — Constructors
- **3.4.A.1** 객체 state, has-a 관계 → §5 (CED 3.4.A.1 섹션)
- **3.4.A.2** Constructor의 메모리 할당과 객체 참조 반환 → §5 (CED 3.4.A.2 섹션)
- **3.4.A.3** Mutable 매개변수는 방어적 복사 → §5 (방어적 복사 섹션)
- **3.4.A.4** Default constructor 자동 생성 조건 → §5 (Default Constructor 섹션)
- **3.4.A.5** Default value 4가지 (0, 0.0, false, null) → §5 (Default Value 규칙)

### Topic 3.5 — Methods: How to Write Them
- **3.5.A.1** void 메서드 → §6 (void 메서드)
- **3.5.A.2** 비-void 메서드 → §6 (non-void 메서드)
- **3.5.A.3** Return by value → §6 (CED 3.5.A.3 섹션)
- **3.5.A.4** return 키워드, return 이후 unreachable → §6 (return 규칙)
- **3.5.A.5** Accessor 메서드 정의 → §4, §6
- **3.5.A.6** Mutator 메서드 정의 → §4, §6
- **3.5.A.7** 매개변수 있는 메서드 → §6
- **3.5.A.8** Primitive 매개변수는 값 복사 → §6 (Pass-by-Value)

### Topic 3.6 — Methods: Passing and Returning References
- **3.6.A.1** 객체 참조 매개변수는 복사본, mutable 객체 변경 가능 → §6, §7
- **3.6.A.2** 객체 참조 반환 — 새 복사본 아닌 같은 참조 → §7 (캡슐화 구멍)
- **3.6.A.3** 같은 타입 매개변수의 private 접근 → §7 (CED 3.6.A.3 섹션)

### Topic 3.7 — Class Variables and Methods
- **3.7.A.1** Class methods는 instance variables/methods 직접 접근 불가 → §8
- **3.7.A.2** Class methods는 class variables 접근/다른 class methods 호출 가능 → §8
- **3.7.B.1** Class variables는 클래스 소속, static 키워드 → §8 (CED 공식 용어 섹션)
- **3.7.B.2** public class variables는 클래스 이름과 dot 연산자로 접근 → §8
- **3.7.B.3** final 변수는 변경 불가 → §11

### Topic 3.8 — Scope and Access
- **3.8.A.1** Local variables 정의, public/private 불가 → §9
- **3.8.A.2** 같은 이름 local/parameter는 instance variable 가림 (shadowing) → §9

### Topic 3.9 — this Keyword
- **3.9.A.1** this는 인스턴스 메서드/생성자 안의 특별 변수 → §10
- **3.9.A.2** this를 메서드 인자로 전달 가능 → §10 (3가지 용법)
- **3.9.A.3** Class methods는 this 참조 없음 → §10

**모든 EK 항목 빠짐없이 다룸.** ✅ (College Board CED 2025-26 v.1 공식 출처 매핑)

---

## 부록 C: Unit 3 EXCLUSION 정리 (절대 쓰면 안 되는 것)

CED 2025-26에서 명시적으로 시험 범위 밖이라고 선언한 항목:

| EXCLUSION | 출처 | 의미 |
|----------|-----|------|
| `toString` 오버라이드 작성 | CED 1.15.A.5 | 학생이 작성하는 것은 시험 X (트레이싱은 가능). FRQ Q2에서 객체 정보 반환 메서드는 `getInfo()` 등 일반 이름 사용 |
| `equals` 오버라이드 작성 | CED 2.6.B.3 (p.66) | 작성 X (Object의 equals를 클래스에서 재정의하지 않음) |
| 상속 (`extends`) | 2025-26 CED 전면 제외 | 이전 CED의 Unit 5(상속/다형성)는 2025-26 시험에서 통째로 제거. extends, super, @Override 모두 시험 X |
| 인터페이스 구현 (`implements`) | 2025-26 CED 전면 제외 | 동일 — 시험 X |
| try/catch 예외 처리 | CED 범위 | 시험 X (단 throws IOException은 Unit 4 4.6에서 허용) |
| 정적 초기화 블록 | CED 범위 | 시험 X |
| 추상 클래스 (`abstract`) | 2025-26 CED 전면 제외 | 시험 X |

**FRQ Q2 작성 시**: 위 항목은 절대 쓰지 않는다. 일반 메서드, 단순 클래스로만 답안 구성.

---

## 부록 D: Unit 4와의 연결

Unit 3의 클래스 위에 Unit 4가 쌓인다.

- **Unit 4**: 클래스로 만든 객체들을 **여러 개 모아 관리** (배열, ArrayList, 2D 배열의 원소가 객체)

Unit 3가 흔들리면 Unit 4도 흔들린다. **반드시 이 단원에서 객체와 참조 개념을 완전히 잡고** 다음으로 넘어간다.

> ⚠️ **2025-26 CED 변경 안내**: 이전 버전 CED에 있던 **Unit 5(상속/다형성)는 2025-26 시험에서 완전히 제거**되었다. 2025년 봄 시험부터는 Unit 1~4의 4개 단원만 출제. `extends`, `implements`, `super`, `abstract`, `@Override` 모두 시험 범위 외. FRQ Q2(Class Design)에서도 절대 사용 X.

---

## 부록 E: 출처 (Sources)

본 문서의 모든 내용은 다음 공식 출처를 기반으로 한다:

1. **AP Computer Science A Course and Exam Description (CED), Effective Fall 2025**, College Board, June 2025 (194 pages, v.1).
   - URL: https://apcentral.collegeboard.org/courses/ap-computer-science-a
   - Direct PDF: https://apcentral.collegeboard.org/media/pdf/ap-computer-science-a-course-and-exam-description.pdf
   - Unit 3 토픽 페이지: CED p.78-90 (UNIT 3: Class Creation, 토픽 3.1~3.9)
   - 모든 Learning Objective(LO)와 Essential Knowledge(EK) 항목을 본 문서 §2~§11 및 부록 B에 빠짐없이 매핑

2. **AP CSA Java Quick Reference (CED Appendix)** — 시험 출제 메서드 범위 정의

3. **EXCLUSION 출처** (CED 원문 EK 위치):
   - **1.15.A.5** (toString 오버라이드 작성) — CED p.50
   - **2.6.B.3** (equals 오버라이드 작성) — CED p.66
   - **4.6.A.6** (Scanner(System.in) 키보드 입력) — CED Unit 4 p.106
   - **4.6.A.7** (nextLine + 다른 Scanner 메서드 혼용) — CED Unit 4 p.106
   - **4.6.A.8** (split 정규표현식 특수문자) — CED Unit 4 p.107
   - **4.11.A.1** (비직사각형 2D 배열) — CED Unit 4 p.114
   - **4.16.A.3** (재귀 코드 작성) — CED Unit 4 p.120
   - **4.17.B.2** (linear/binary 외 검색) — CED Unit 4 p.121
   - **4.17.C.1** (selection/insertion/merge 외 정렬) — CED Unit 4 p.121

본 문서가 CED와 어긋나는 부분이 있다면 항상 **CED가 우선**한다 (College Board 공식 문서이므로).

---

> **이 문서를 다 읽었다면 — 축하한다.**
> 
> Unit 3의 모든 시험 개념을 "왜 이렇게 생겼는가"의 메커니즘 수준에서 이해했다.
> 이제 코드를 쓰는 손이 머리를 따라가도록 직접 코드를 작성해보면 된다.
> FRQ Q2 만점은 이해의 깊이 × 손에 익은 패턴 × 차분함의 곱이다.
> 첫 번째 항을 채웠으니, 나머지 두 항을 위해 손을 움직이자.
