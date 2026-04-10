# Java 환경설정 가이드 (AP CSA 과외용)

> 이 가이드는 프로그래밍을 처음 접하는 학생을 위해 작성되었습니다.
> 천천히 따라하면 누구나 할 수 있습니다!

---

## 1. 프로그래밍이란?

### 컴퓨터에게 일을 시키는 "명령서"

우리가 요리를 할 때 레시피(조리법)를 따르듯이, 컴퓨터도 **명령서**가 있어야 일을 합니다.

- 컴퓨터는 스스로 생각하지 못합니다. 우리가 **하나하나 알려줘야** 합니다.
- 이 명령서를 작성하는 것이 바로 **프로그래밍(코딩)** 입니다.

### Java는 뭔가요?

사람이 한국어, 영어, 일본어 등 여러 언어를 쓰듯이, 컴퓨터에게 명령을 내리는 언어도 여러 종류가 있습니다.

- Python, JavaScript, C++, **Java** 등이 있습니다.
- 이것들을 **프로그래밍 언어**라고 부릅니다.
- Java는 그중 하나입니다.

### 왜 Java를 배우나요?

- **AP Computer Science A 시험이 Java로 출제**됩니다.
- 시험에서 Java 코드를 읽고, 이해하고, 작성해야 합니다.
- Java를 잘 배워두면 다른 언어도 쉽게 배울 수 있습니다.

---

## 2. 필요한 프로그램 설치

코딩을 하려면 **코드를 작성하고 실행할 수 있는 프로그램**이 필요합니다.
이런 프로그램을 **IDE(통합 개발 환경)** 라고 부릅니다.

> 비유: Word가 글쓰기 도구인 것처럼, IDE는 코딩 도구입니다.

아래 세 가지 방법 중 **하나만 선택**하면 됩니다.

---

### 방법 A: IntelliJ IDEA (추천!)

전문 개발자들이 가장 많이 쓰는 Java 전용 도구입니다. AP CSA 수업에 가장 적합합니다.

#### 다운로드

1. 웹 브라우저에서 아래 주소로 이동합니다:
   - **https://www.jetbrains.com/idea/download/**
2. **Community Edition** (무료 버전)을 다운로드합니다.
   - 주의: 페이지 상단에 "Ultimate"(유료)가 먼저 보입니다. **아래로 스크롤**해서 **Community Edition**을 찾으세요!
   - Windows 사용자: `.exe` 파일 다운로드
   - Mac 사용자: `.dmg` 파일 다운로드
     - **내 Mac이 Apple Silicon인지 확인하는 법**: 왼쪽 상단 Apple 메뉴 > "이 Mac에 관하여" > "칩(Chip)"이 M1/M2/M3/M4이면 → `Apple Silicon` 버전, Intel이면 → `Intel` 버전 선택

#### 설치 과정 (Windows)

1. 다운로드한 `.exe` 파일을 더블클릭합니다.
2. "Next"를 클릭합니다.
3. 설치 위치는 그대로 두고 "Next"를 클릭합니다.
4. 옵션 화면이 나옵니다:
   - **"Add launchers dir to the PATH"** → 체크 ✓ (이걸 체크하면 어디서든 IntelliJ를 쉽게 실행할 수 있습니다)
   - **".java" 연결** → 체크 ✓ (.java 파일을 더블클릭하면 IntelliJ가 열립니다)
   - 나머지는 기본값 그대로
5. "Install"을 클릭하고 기다립니다.
6. 설치 완료 후 "Finish"를 클릭합니다.

#### 설치 과정 (Mac)

1. 다운로드한 `.dmg` 파일을 더블클릭합니다.
2. IntelliJ IDEA 아이콘을 **Applications 폴더로 드래그**합니다.
3. Applications 폴더에서 IntelliJ IDEA를 실행합니다.
4. 처음 실행하면 "개발자를 확인할 수 없습니다" 경고가 나올 수 있습니다 → "열기"를 클릭하세요.

#### JDK 설치 (첫 실행 시 자동)

JDK(Java Development Kit)란 Java 프로그램을 만들기 위한 도구 모음입니다.

> 비유: Java가 "언어"라면, JDK는 그 언어로 글을 쓸 수 있게 해주는 "연필과 종이"입니다.

IntelliJ를 처음 열고 프로젝트를 만들 때:

1. "New Project"를 클릭합니다.
2. **JDK** 항목에서 드롭다운을 클릭합니다.
3. **"Download JDK..."** 를 선택합니다.
4. Version: **17** 이상을 선택합니다 (가장 위에 있는 것으로).
5. Vendor: 아무거나 OK (기본값 그대로).
6. "Download"를 클릭하면 자동으로 설치됩니다!

---

### 방법 B: VS Code + Java Extension Pack

VS Code는 가볍고 빠른 코드 편집기입니다. Java 외에 다른 언어도 함께 쓰고 싶다면 좋은 선택입니다.

#### 1단계: VS Code 설치

1. **https://code.visualstudio.com/** 에서 다운로드합니다.
2. 운영체제에 맞는 버전을 클릭합니다 (Windows / Mac).
3. 다운로드한 파일을 실행하고, 계속 "Next"를 눌러 설치합니다.

#### 2단계: JDK 설치

VS Code는 IntelliJ와 달리 JDK를 따로 설치해야 합니다.

1. **https://adoptium.net/** 에서 다운로드합니다.
2. "Latest LTS Release"를 클릭합니다 (큰 버튼).
3. 다운로드한 파일을 실행합니다.
4. 설치 중 **"Set JAVA_HOME variable"** 옵션이 보이면 반드시 체크 ✓ 합니다.
5. 설치를 완료합니다.

#### 3단계: Java Extension Pack 설치

1. VS Code를 실행합니다.
2. 왼쪽 사이드바에서 **네모 블록 모양 아이콘** (Extensions)을 클릭합니다.
   - 또는 단축키: `Ctrl + Shift + X` (Windows) / `Cmd + Shift + X` (Mac)
3. 검색창에 **"Extension Pack for Java"** 를 입력합니다.
4. Microsoft에서 만든 것을 찾아 **"Install"** 을 클릭합니다.
5. 설치가 끝나면 VS Code를 **한 번 껐다가 다시 엽니다**.

---

### 방법 C: 온라인 (설치 없이 바로 시작!)

컴퓨터에 아무것도 설치하고 싶지 않다면, 웹 브라우저에서 바로 코딩할 수 있습니다.

#### Replit 사용법

1. **https://replit.com** 에 접속합니다.
2. "Sign Up"을 클릭해서 **회원가입**합니다 (Google 계정으로 가능).
3. 로그인 후 **"+ Create Repl"** 버튼을 클릭합니다.
4. Template에서 **"Java"** 를 선택합니다.
5. 프로젝트 이름을 입력하고 **"Create Repl"** 을 클릭합니다.
6. 화면 왼쪽에 코드를 입력하고, 상단의 **"Run"** 버튼을 누르면 실행됩니다!

> 장점: 설치 없이 바로 시작 가능, 어떤 컴퓨터에서든 접속 가능
>
> 단점: 인터넷이 필요, 무료 버전은 기능 제한이 있음

---

## 3. 첫 번째 프로그램: Hello World

모든 프로그래밍 학습은 **"Hello, World!"를 화면에 출력하는 것**에서 시작합니다.
이건 전통입니다! 전 세계 모든 개발자가 처음에 이걸 합니다.

### IntelliJ에서 프로젝트 만들기

1. IntelliJ IDEA를 실행합니다.
2. **"New Project"** 를 클릭합니다.
3. 왼쪽에서 **"Java"** 가 선택되어 있는지 확인합니다.
4. Project name에 **`HelloWorld`** 를 입력합니다.
5. JDK가 선택되어 있는지 확인합니다 (없으면 위의 JDK 설치 참고).
6. **"Create"** 를 클릭합니다.
7. `src` 폴더를 오른쪽 클릭 → **New → Java Class** 를 선택합니다.
8. 이름에 **`HelloWorld`** 를 입력하고 Enter를 누릅니다.

### 코드 입력

열린 파일에 아래 코드를 **그대로** 입력합니다:

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### 코드 한 줄씩 이해하기

| 코드 | 의미 |
|------|------|
| `public class HelloWorld` | "HelloWorld"라는 이름의 프로그램을 만든다. |
| `{` ... `}` (바깥쪽) | 이 프로그램의 내용물을 감싸는 상자. "여기서부터 여기까지가 HelloWorld 프로그램이다." |
| `public static void main(String[] args)` | 프로그램이 시작되는 곳. **컴퓨터는 항상 여기서부터 읽기 시작한다.** 지금은 이해하지 않아도 됩니다. 항상 이렇게 쓴다고 외우세요! |
| `{` ... `}` (안쪽) | main 안의 내용물을 감싸는 상자. |
| `System.out.println("Hello, World!");` | 화면에 `Hello, World!`를 출력(표시)한다. `println` = "print line"의 줄임말. |
| `;` (세미콜론) | 문장의 끝. 한국어의 마침표(.)와 같은 역할. **모든 명령문 끝에 반드시 써야 합니다!** |

> 정리하면: "HelloWorld라는 프로그램을 만들고, 프로그램이 시작되면, 화면에 Hello, World!를 보여줘라."

---

## 4. 실행하기

### IntelliJ에서 실행

1. 코드 왼쪽에 있는 **초록색 삼각형(재생 버튼)** 을 클릭합니다.
   - 또는 키보드에서 **`Shift + F10`** 을 누릅니다.
2. 화면 아래쪽에 **"Run"** 창이 열립니다.
3. 여기에 아래와 같이 나오면 성공입니다!

```
Hello, World!
```

축하합니다! 첫 번째 프로그램을 만들고 실행했습니다!

### VS Code에서 실행

1. 코드 파일을 열고, 오른쪽 위에 있는 **재생 버튼(삼각형)** 을 클릭합니다.
2. 또는 터미널에서 직접 실행:
   - `Ctrl + `` (백틱)을 눌러 터미널을 엽니다.
   - `javac HelloWorld.java` 입력 후 Enter (컴파일 = 번역)
   - `java HelloWorld` 입력 후 Enter (실행)

### 에러가 나면? (흔한 에러 5가지)

프로그래밍에서 에러는 **아주 자연스러운 일**입니다. 전문 개발자도 매일 에러를 만납니다. 당황하지 마세요!

#### 에러 1: `';' expected`

```
HelloWorld.java:3: error: ';' expected
```

- **원인**: 문장 끝에 세미콜론(`;`)을 빼먹었습니다.
- **해결**: 에러가 난 줄 끝에 `;`을 추가하세요.

#### 에러 2: `cannot find symbol`

```
error: cannot find symbol
    System.out.printIn("Hello, World!");
```

- **원인**: 이름을 잘못 입력했습니다. (예: `println`을 `printIn`으로 씀 - 소문자 L과 대문자 I 헷갈림!)
- **해결**: 오타를 찾아서 고치세요. `println`에서 마지막은 소문자 L(`l`)입니다.

#### 에러 3: `class, interface, or enum expected`

- **원인**: 중괄호 `{` `}`의 짝이 안 맞습니다.
- **해결**: 여는 중괄호 `{`와 닫는 중괄호 `}`의 개수가 같은지 확인하세요.

#### 에러 4: `Main method not found`

```
Error: Main method not found in class HelloWorld
```

- **원인**: `public static void main(String[] args)` 부분을 정확히 쓰지 않았습니다.
- **해결**: main 메서드 선언을 위 코드와 **완전히 동일하게** 다시 입력하세요.

#### 에러 5: 파일명과 클래스명 불일치

```
error: class HelloWorld is public, should be declared in a file named HelloWorld.java
```

- **원인**: 파일 이름이 `Helloworld.java`인데 코드에는 `HelloWorld`로 되어 있습니다 (대소문자 다름!).
- **해결**: 파일 이름과 `class` 뒤에 오는 이름을 **완전히 똑같게** 맞추세요.

---

## 5. 두 번째 프로그램: 변수 사용하기

### 변수란?

**변수 = 이름이 붙은 상자**

- 상자에 물건을 넣듯이, 변수에 값(데이터)을 넣습니다.
- 상자에 "과자"라고 이름을 쓰듯이, 변수에도 이름을 붙입니다.
- 나중에 상자를 열어서 안에 든 것을 꺼내 쓸 수 있습니다.

### 코드 입력

새 Java Class를 만들고 이름을 **`MyInfo`** 로 합니다. 아래 코드를 입력하세요:

```java
public class MyInfo {
    public static void main(String[] args) {
        String name = "김철수";
        int age = 17;
        System.out.println("이름: " + name);
        System.out.println("나이: " + age);
    }
}
```

### 코드 한 줄씩 이해하기

| 코드 | 의미 |
|------|------|
| `String name = "김철수";` | `name`이라는 이름의 상자를 만들고, 그 안에 `"김철수"`라는 글자를 넣는다. `String`은 "이 상자에는 글자가 들어간다"는 뜻. |
| `int age = 17;` | `age`라는 이름의 상자를 만들고, 그 안에 `17`이라는 숫자를 넣는다. `int`는 "이 상자에는 정수(integer)가 들어간다"는 뜻. |
| `"이름: " + name` | 글자와 변수를 `+`로 이어붙인다. 결과: `이름: 김철수` |

### 실행 결과

```
이름: 김철수
나이: 17
```

### 변수의 종류 (자주 쓰는 것만!)

| 종류 | 의미 | 예시 |
|------|------|------|
| `int` | 정수 (소수점 없는 숫자) | `int score = 100;` |
| `double` | 실수 (소수점 있는 숫자) | `double height = 170.5;` |
| `String` | 글자(문자열) | `String name = "홍길동";` |
| `boolean` | 참/거짓 | `boolean isStudent = true;` |

> 지금은 `int`, `double`, `String` 이 세 가지만 기억하면 충분합니다!

---

## 6. 세 번째 프로그램: 계산하기

컴퓨터는 **계산을 매우 잘합니다**. Java에서 계산하는 방법을 알아봅시다.

### 산술 연산자

| 기호 | 의미 | 예시 | 결과 |
|------|------|------|------|
| `+` | 더하기 | `5 + 3` | `8` |
| `-` | 빼기 | `10 - 4` | `6` |
| `*` | 곱하기 | `3 * 7` | `21` |
| `/` | 나누기 | `10 / 3` | `3` (주의!) |
| `%` | 나머지 | `10 % 3` | `1` |

> `*`는 키보드에서 `Shift + 8`로 입력합니다. 수학에서 쓰는 `x`가 아닙니다!
>
> `%`는 나머지를 구합니다. 10을 3으로 나누면 몫이 3이고 **나머지가 1**이니까 `10 % 3 = 1`

### 코드 입력

새 Java Class 이름: **`Calculator`**

```java
public class Calculator {
    public static void main(String[] args) {
        int a = 10;
        int b = 3;

        System.out.println("a + b = " + (a + b));
        System.out.println("a - b = " + (a - b));
        System.out.println("a * b = " + (a * b));
        System.out.println("a / b = " + (a / b));
        System.out.println("a % b = " + (a % b));
    }
}
```

### 실행 결과

```
a + b = 13
a - b = 7
a * b = 30
a / b = 3
a % b = 1
```

### 정수 나눗셈 함정 (중요!)

`10 / 3`의 답이 `3.333...`이 아니라 **`3`** 인 것을 눈치챘나요?

Java에서 **정수(int)끼리 나누면 결과도 정수**입니다. 소수점 아래는 **버려집니다** (반올림이 아니라 버림!).

```java
System.out.println(10 / 3);     // 결과: 3 (소수점 버림!)
System.out.println(10.0 / 3);   // 결과: 3.3333... (하나라도 실수면 OK)
System.out.println(10 / 3.0);   // 결과: 3.3333... (하나라도 실수면 OK)
```

> 규칙: **int / int = int** (소수점 버림)
>
> 소수점까지 나오게 하려면, 숫자 하나에라도 `.0`을 붙이면 됩니다.
>
> 이건 AP 시험에 자주 나오는 함정이니 꼭 기억하세요!

---

## 7. 코딩할 때 지켜야 할 규칙 (초보자용)

Java에는 반드시 지켜야 하는 규칙이 있습니다. 안 지키면 에러가 납니다!

### 규칙 1: 파일 이름 = 클래스 이름 (대소문자까지!)

```java
// 파일 이름: HelloWorld.java
public class HelloWorld {  // 이름이 완전히 같아야 함!
```

- `HelloWorld.java` 파일 안에는 `public class HelloWorld`가 있어야 합니다.
- `helloworld.java`도 안 됩니다! **대소문자가 완전히 같아야** 합니다.

### 규칙 2: 세미콜론(;)을 빼먹으면 에러

```java
System.out.println("Hello")   // 에러! ; 없음
System.out.println("Hello");  // 올바름
```

- 모든 명령문 끝에는 반드시 `;`을 붙입니다.
- 실수하기 가장 쉬운 부분이니 항상 확인하세요!

### 규칙 3: 중괄호 { }는 항상 짝이 맞아야 함

```java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello");
    }  // main의 닫는 중괄호
}  // class의 닫는 중괄호
```

- `{`를 열었으면 반드시 `}`로 닫아야 합니다.
- 팁: IntelliJ에서 `{`를 입력하면 자동으로 `}`가 생깁니다.

### 규칙 4: 대소문자 구분

Java는 대문자와 소문자를 **완전히 다른 글자로** 취급합니다.

```java
System.out.println("Hello");  // 올바름
system.out.println("Hello");  // 에러! (S가 소문자)
SYSTEM.OUT.PRINTLN("Hello");  // 에러! (전부 대문자)
```

### 규칙 5: 들여쓰기 습관 (Tab 키)

들여쓰기는 에러가 나지는 않지만, **코드를 읽기 쉽게** 만듭니다.

```java
// 나쁜 예 (읽기 어려움)
public class Hello {
public static void main(String[] args) {
System.out.println("Hello");
}
}

// 좋은 예 (들여쓰기 O)
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```

- `{` 안에 들어갈 때마다 **Tab 키를 한 번** 눌러 들여쓰기 합니다.
- IntelliJ에서 `Ctrl + Alt + L` (Windows) / `Cmd + Option + L` (Mac)을 누르면 **자동 정렬**됩니다!

---

## 8. 연습 문제

이제 직접 해봅시다! 아래 두 프로그램을 만들어 보세요.

### 연습 1: 자기소개 프로그램

아래 조건을 만족하는 프로그램을 작성하세요.

- 클래스(파일) 이름: `SelfIntro`
- 변수 사용: 이름, 나이, 좋아하는 것 각각 변수에 저장
- `System.out.println`으로 출력

**실행 결과 예시:**
```
=== 자기소개 ===
이름: 박지민
나이: 16살
좋아하는 음식: 치킨
좋아하는 과목: 수학
장래희망: 개발자
```

**힌트:**

```java
public class SelfIntro {
    public static void main(String[] args) {
        String name = "여기에 내 이름";
        int age = 0;  // 내 나이
        String food = "여기에 좋아하는 음식";
        // ... 나머지는 직접 해보세요!

        System.out.println("=== 자기소개 ===");
        System.out.println("이름: " + name);
        // ... 나머지도 출력해보세요!
    }
}
```

---

### 연습 2: 계산기 프로그램

두 숫자를 변수에 저장하고, 네 가지 연산 결과를 출력하세요.

- 클래스(파일) 이름: `MyCalculator`
- 두 정수를 변수에 저장
- 덧셈, 뺄셈, 곱셈, 나눗셈 결과를 각각 출력

**실행 결과 예시:**
```
=== 계산기 ===
첫 번째 수: 15
두 번째 수: 4
덧셈: 15 + 4 = 19
뺄셈: 15 - 4 = 11
곱셈: 15 * 4 = 60
나눗셈: 15 / 4 = 3
나머지: 15 % 4 = 3
```

**힌트:**

```java
public class MyCalculator {
    public static void main(String[] args) {
        int num1 = 15;
        int num2 = 4;

        System.out.println("=== 계산기 ===");
        System.out.println("첫 번째 수: " + num1);
        System.out.println("두 번째 수: " + num2);
        // 여기에 덧셈, 뺄셈, 곱셈, 나눗셈, 나머지를 출력하는 코드를 작성하세요!
        // 힌트: (num1 + num2) 이런 식으로 괄호를 사용하세요.
    }
}
```

---

> 다 했으면 다음 시간에 **조건문(if문)** 을 배울 준비 완료입니다!
