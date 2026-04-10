# AP CSA Java 용어 사전

> AP Computer Science A를 처음 배우는 학생을 위한 용어 정리  
> 배우는 순서대로 정리 | 한국어 뜻 + 비유 + 코드 예시 + 시험 포인트

---

## Unit 1: 기본 용어

---

### Algorithm (알고리즘)
**한국어 뜻**: 문제를 풀기 위한 단계별 절차
**비유**: 라면 끓이는 레시피. "물 넣고 → 끓이고 → 면 넣고 → 스프 넣고" 같은 순서가 알고리즘이다.
**예시 코드**:
```java
// 두 수 중 큰 수를 찾는 알고리즘
int a = 5, b = 3;
if (a > b) {
    System.out.println(a);
} else {
    System.out.println(b);
}
```
**시험에서**: "다음 알고리즘의 출력은?" 형태로 코드 추적(trace) 문제가 나온다.

---

### Programming (프로그래밍)
**한국어 뜻**: 컴퓨터에게 일을 시키기 위해 코드를 작성하는 것
**비유**: 로봇에게 편지를 써서 명령하는 것. 로봇은 편지에 적힌 대로만 한다.
**예시 코드**:
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```
**시험에서**: 직접 출제되진 않지만, 모든 문제의 기본 배경이다.

---

### Compiler (컴파일러)
**한국어 뜻**: 사람이 쓴 코드(소스코드)를 컴퓨터가 이해하는 기계어로 번역해주는 프로그램
**비유**: 통역사. 한국어(자바 코드)를 영어(기계어)로 한 번에 통째로 번역한다.
**예시 코드**:
```java
// 컴파일 명령 (터미널에서)
// javac MyProgram.java  → 컴파일 (번역)
// java MyProgram        → 실행
```
**시험에서**: "컴파일 에러가 발생하는 코드는?" 문제에서 컴파일러가 잡아내는 에러(문법 오류)를 구분해야 한다.

---

### IDE (아이디이)
**한국어 뜻**: Integrated Development Environment. 코드 작성 + 컴파일 + 실행 + 디버깅을 한 곳에서 할 수 있는 통합 개발 도구
**비유**: 요리할 때 칼, 도마, 불, 접시가 다 갖춰진 주방 세트. Eclipse, IntelliJ, VS Code 같은 것들이다.
**예시 코드**:
```java
// IDE에서 코드를 작성하면
// 자동완성, 오류 표시, 실행 버튼 등이 제공됨
```
**시험에서**: 직접 나오진 않지만, 실습 환경으로 알아두면 좋다.

---

### Syntax (신택스)
**한국어 뜻**: 프로그래밍 언어의 문법 규칙
**비유**: 한국어에서 "나는 학생이다"는 맞지만 "나는 학생이다는"은 틀리듯, 자바에도 정해진 문법이 있다.
**예시 코드**:
```java
// 올바른 syntax
System.out.println("Hello");

// 잘못된 syntax (세미콜론 빠짐)
System.out.println("Hello")  // ← 컴파일 에러!
```
**시험에서**: "다음 중 컴파일 에러가 발생하는 코드는?" → 문법 오류를 찾는 문제.

---

### Syntax Error (신택스 에러)
**한국어 뜻**: 문법 규칙을 어겨서 생기는 에러. 컴파일할 때 발견됨.
**비유**: 맞춤법 오류. 제출 전에 선생님(컴파일러)이 빨간펜으로 "여기 틀렸어" 하고 잡아주는 것.
**예시 코드**:
```java
// 세미콜론 누락
int x = 5   // ← Syntax Error

// 괄호 짝 안 맞음
if (x > 3 {  // ← Syntax Error
```
**시험에서**: 3가지 에러(Syntax, Logic, Runtime) 구분 문제. Syntax Error는 프로그램이 아예 실행되지 않는다.

---

### Logic Error (로직 에러)
**한국어 뜻**: 문법은 맞지만 프로그램이 의도한 대로 동작하지 않는 에러
**비유**: 레시피대로 만들었는데 설탕 대신 소금을 넣은 것. 요리는 완성되지만 맛이 이상하다.
**예시 코드**:
```java
// 두 수의 평균을 구하려는데...
int a = 10, b = 20;
double avg = a + b / 2;  // 의도: 15, 실제: 20 (연산 순서 실수)
// 올바른 코드: (a + b) / 2.0
```
**시험에서**: "이 코드의 문제점은?" 또는 "의도와 다른 결과가 나오는 이유는?" 형태로 자주 출제.

---

### Runtime Error (런타임 에러)
**한국어 뜻**: 프로그램 실행 중에 발생하는 에러. 컴파일은 되지만 실행하다가 멈춤.
**비유**: 운전 중 갑자기 도로가 끊겨있는 것. 출발은 했지만 중간에 멈춘다.
**예시 코드**:
```java
int[] arr = {1, 2, 3};
System.out.println(arr[5]);  // ArrayIndexOutOfBoundsException!
// 배열 크기는 3인데 6번째 칸을 읽으려 함

int x = 10 / 0;  // ArithmeticException! 0으로 나눌 수 없음
```
**시험에서**: "다음 코드 실행 시 발생하는 에러는?" → 런타임 에러 종류를 알아야 한다.

---

### Exception (익셉션)
**한국어 뜻**: 프로그램 실행 중 발생하는 예외 상황. Runtime Error의 구체적인 이름.
**비유**: 학교에서 "이상 상황 발생!" 하고 비상벨이 울리는 것. 프로그램이 "나 이거 못해!" 라고 외치는 것.
**예시 코드**:
```java
String s = null;
s.length();  // NullPointerException!

int n = Integer.parseInt("abc");  // NumberFormatException!
```
**시험에서**: NullPointerException, ArrayIndexOutOfBoundsException 등 구체적인 이름을 알아야 한다.

---

### Debug / Debugging (디버그 / 디버깅)
**한국어 뜻**: 프로그램의 오류(버그)를 찾아서 고치는 과정
**비유**: 탐정이 범인(버그)을 추적해서 잡는 것. 코드를 한 줄씩 따라가며 "어디서 잘못됐지?" 찾는다.
**예시 코드**:
```java
// 디버깅 방법: print문으로 중간값 확인
int sum = 0;
for (int i = 0; i <= 10; i++) {
    sum += i;
    System.out.println("i=" + i + ", sum=" + sum);  // 디버깅용 출력
}
```
**시험에서**: 코드 추적(tracing) 문제 자체가 디버깅 능력을 테스트하는 것이다.

---

## Unit 1: 타입과 변수

---

### Data Type (데이터 타입)
**한국어 뜻**: 데이터의 종류. 정수, 실수, 문자열, 참/거짓 등.
**비유**: 서류 양식의 칸 종류. "이름" 칸에는 글자, "나이" 칸에는 숫자만 써야 하듯, 타입이 정해져 있다.
**예시 코드**:
```java
int age = 17;          // 정수 타입
double height = 175.5; // 실수 타입
boolean pass = true;   // 참/거짓 타입
String name = "Kim";   // 문자열 타입
```
**시험에서**: 타입에 따라 저장할 수 있는 값이 다르다. int에 소수점을 넣으면 잘림!

---

### Primitive Type (프리미티브 타입)
**한국어 뜻**: 기본 데이터 타입. 값 자체를 저장. Java에는 8개가 있지만 AP CSA에서는 int, double, boolean 3개가 핵심.
**비유**: 메모지에 숫자를 직접 적어놓는 것. 메모지 = 변수, 적힌 숫자 = 값.
**예시 코드**:
```java
int count = 10;      // 정수
double pi = 3.14;    // 실수
boolean done = false; // 참/거짓
```
**시험에서**: Primitive vs Reference 비교 문제. Primitive는 값을 직접 저장하고, == 비교가 값 비교다.

---

### Reference Type (레퍼런스 타입)
**한국어 뜻**: 객체의 주소(참조)를 저장하는 타입. String, 배열, 클래스 등.
**비유**: 메모지에 "창고 3번에 가봐"라고 주소를 적어놓는 것. 실제 물건(데이터)은 창고(메모리 힙)에 있다.
**예시 코드**:
```java
String name = "Kim";       // name은 "Kim" 객체의 주소를 저장
int[] arr = {1, 2, 3};     // arr은 배열 객체의 주소를 저장
String a = new String("Hi");
String b = a;               // b도 같은 객체를 가리킴
```
**시험에서**: Reference Type끼리 ==는 주소 비교! 내용 비교는 .equals() 사용. 매우 자주 나오는 함정.

---

### int (인트)
**한국어 뜻**: 정수(소수점 없는 숫자)를 저장하는 타입. -2,147,483,648 ~ 2,147,483,647
**비유**: 동전 지갑. 동전(정수)만 넣을 수 있고, 지폐(소수)는 안 된다.
**예시 코드**:
```java
int score = 95;
int total = 10 / 3;  // 결과: 3 (소수점 버림!)
```
**시험에서**: int끼리 나누면 소수점이 버려진다! 10/3 = 3 (3.33이 아님). 가장 흔한 함정.

---

### double (더블)
**한국어 뜻**: 실수(소수점 있는 숫자)를 저장하는 타입
**비유**: 정밀 저울. 소수점 아래까지 정확하게 잴 수 있다.
**예시 코드**:
```java
double price = 9.99;
double result = 10.0 / 3;  // 결과: 3.3333...
double x = 0.1 + 0.2;      // 결과: 0.30000000000000004 (부동소수점 오차!)
```
**시험에서**: int와 double 연산 시 결과가 double로 자동 변환됨. 부동소수점 오차도 알아두자.

---

### boolean (불리언)
**한국어 뜻**: true(참) 또는 false(거짓) 두 가지 값만 저장하는 타입
**비유**: 전등 스위치. 켜짐(true) 아니면 꺼짐(false) 둘 중 하나.
**예시 코드**:
```java
boolean isStudent = true;
boolean canVote = (age >= 18);  // 조건에 따라 true/false
```
**시험에서**: if문, while문의 조건에 항상 boolean이 들어간다. 조건식 결과 판단 문제 빈출.

---

### Variable (변수)
**한국어 뜻**: 데이터를 저장하는 이름 붙은 공간
**비유**: 이름표가 붙은 상자. "score"라는 상자에 95라는 숫자를 넣어둔다.
**예시 코드**:
```java
int score;       // 선언 (상자 준비)
score = 95;      // 대입 (상자에 값 넣기)
int age = 17;    // 선언 + 초기화 (한 번에)
age = 18;        // 값 변경 (상자에 새 값 넣기)
```
**시험에서**: 변수의 값 추적 문제. 변수에 새 값을 넣으면 이전 값은 사라진다!

---

### Literal (리터럴)
**한국어 뜻**: 코드에 직접 적은 고정된 값
**비유**: 메모지에 펜으로 직접 쓴 숫자. "42"라고 적으면 42는 리터럴이다.
**예시 코드**:
```java
int x = 42;           // 42는 int 리터럴
double y = 3.14;      // 3.14는 double 리터럴
boolean z = true;     // true는 boolean 리터럴
String s = "hello";   // "hello"는 String 리터럴
```
**시험에서**: 리터럴의 타입을 묻는 문제. 3.0은 double 리터럴, 3은 int 리터럴.

---

### String Literal (스트링 리터럴)
**한국어 뜻**: 큰따옴표로 감싼 문자열 값
**비유**: 포장지에 담긴 글자 묶음. 큰따옴표가 포장지 역할.
**예시 코드**:
```java
String greeting = "Hello, World!";  // "Hello, World!"가 String 리터럴
String empty = "";                  // 빈 문자열도 리터럴
```
**시험에서**: "" (빈 문자열)과 null은 다르다! 빈 문자열은 길이 0인 String 객체, null은 아무것도 없음.

---

### Initialization (이니셜라이제이션)
**한국어 뜻**: 변수에 처음으로 값을 넣는 것
**비유**: 새 수첩의 첫 페이지에 처음 글을 쓰는 것.
**예시 코드**:
```java
int count = 0;        // 선언과 동시에 초기화
String name;
name = "Kim";         // 나중에 초기화
```
**시험에서**: 초기화 안 한 지역 변수를 사용하면 컴파일 에러! 인스턴스 변수는 자동 초기화(int→0, boolean→false, 참조→null).

---

### Declaration (데클러레이션)
**한국어 뜻**: 변수의 타입과 이름을 정하는 것. "이런 종류의 상자를 만들겠다"는 선언.
**비유**: 서류에 "이름: ___" 칸을 만드는 것. 아직 이름을 안 적었지만 칸은 만들었다.
**예시 코드**:
```java
int score;          // 선언만 (값 없음)
double gpa;         // 선언만
int x = 10;         // 선언 + 초기화
```
**시험에서**: 선언만 하고 초기화 안 한 지역 변수를 쓰면 컴파일 에러.

---

### Assignment (어사인먼트)
**한국어 뜻**: 변수에 값을 넣는 것. = 기호를 사용.
**비유**: 상자에 물건을 넣는 동작. 이미 물건이 있으면 꺼내고 새로 넣는다.
**예시 코드**:
```java
int x;
x = 5;      // 첫 대입 (초기화)
x = 10;     // 재대입 (이전 값 5는 사라짐)
x = x + 1;  // x의 현재 값(10)에 1 더해서 다시 x에 넣음 → 11
```
**시험에서**: x = x + 1은 "x와 x+1이 같다"가 아니라 "x+1을 계산해서 x에 넣는다"는 뜻. 수학의 =과 다르다!

---

### null (널)
**한국어 뜻**: "아무것도 가리키지 않음"을 의미하는 특수한 값. Reference Type에만 쓸 수 있음.
**비유**: 주소록에 "주소: 없음"이라고 적힌 것. 집이 없는 게 아니라, 주소를 모르는 것.
**예시 코드**:
```java
String name = null;         // name은 아무 객체도 가리키지 않음
System.out.println(name);   // 출력: null
name.length();              // NullPointerException! null에 메서드 호출 불가
```
**시험에서**: null에서 메서드를 호출하면 NullPointerException. 자주 출제되는 런타임 에러.

---

### Casting (캐스팅)
**한국어 뜻**: 데이터 타입을 강제로 변환하는 것
**비유**: 리터 단위를 밀리리터로 바꾸는 것. 단위 변환처럼 타입을 바꾼다.
**예시 코드**:
```java
double d = 9.7;
int n = (int) d;          // 강제 캐스팅: 9 (소수점 버림, 반올림 아님!)

int a = 5, b = 2;
double result = (double) a / b;  // 2.5 (a를 double로 바꾼 후 나눗셈)
```
**시험에서**: (int) 캐스팅은 반올림이 아니라 소수점 절삭(truncation)! 9.9 → 9. 매우 빈출.

---

### Overflow (오버플로우)
**한국어 뜻**: 변수가 저장할 수 있는 범위를 넘어서 값이 이상해지는 현상
**비유**: 만보기가 99999에서 한 걸음 더 걸으면 00000으로 돌아가는 것.
**예시 코드**:
```java
int max = Integer.MAX_VALUE;  // 2147483647
System.out.println(max + 1);  // -2147483648 (오버플로우!)
```
**시험에서**: int의 최대값을 넘으면 음수가 된다. 에러가 발생하지 않고 조용히 이상한 값이 됨에 주의.

---

## Unit 1: 연산

---

### Operator (오퍼레이터)
**한국어 뜻**: 연산을 수행하는 기호. +, -, *, /, %, = 등.
**비유**: 계산기의 버튼. + 버튼을 누르면 더하기, - 버튼을 누르면 빼기.
**예시 코드**:
```java
int sum = 5 + 3;       // + 연산자
boolean check = (5 > 3); // > 연산자
```
**시험에서**: 연산자 우선순위와 각 연산자의 동작을 정확히 알아야 한다.

---

### Arithmetic Operator (아리스메틱 오퍼레이터)
**한국어 뜻**: 산술 연산자. +, -, *, /, % 다섯 가지.
**비유**: 초등학교 때 배운 사칙연산 + 나머지 구하기.
**예시 코드**:
```java
int a = 10, b = 3;
System.out.println(a + b);  // 13 (더하기)
System.out.println(a - b);  // 7  (빼기)
System.out.println(a * b);  // 30 (곱하기)
System.out.println(a / b);  // 3  (나누기 - 정수끼리 나누면 소수점 버림!)
System.out.println(a % b);  // 1  (나머지)
```
**시험에서**: int / int = int (소수점 버림)이 가장 큰 함정. 10 / 3 = 3, 10.0 / 3 = 3.333...

---

### Modulo (%) (모듈로)
**한국어 뜻**: 나머지 연산자. 나눗셈의 나머지를 구한다.
**비유**: 12시간제 시계. 15시 → 15 % 12 = 3시.
**예시 코드**:
```java
System.out.println(10 % 3);  // 1  (10 나누기 3의 나머지)
System.out.println(7 % 2);   // 1  (홀수 판별: 나머지가 1이면 홀수)
System.out.println(8 % 2);   // 0  (짝수 판별: 나머지가 0이면 짝수)
```
**시험에서**: 짝수/홀수 판별(n % 2), 자릿수 추출(n % 10), 순환 패턴에 자주 사용.

---

### Compound Assignment (+=, -=, *=, /=) (컴파운드 어사인먼트)
**한국어 뜻**: 연산과 대입을 한 번에 하는 축약 연산자
**비유**: "10원 추가"를 줄여서 "+10원"이라고 쓰는 것.
**예시 코드**:
```java
int x = 10;
x += 5;   // x = x + 5; → 15
x -= 3;   // x = x - 3; → 12
x *= 2;   // x = x * 2; → 24
x /= 4;   // x = x / 4; → 6
x %= 4;   // x = x % 4; → 2
```
**시험에서**: x += 5는 x = x + 5와 완전히 같다. 코드 추적 문제에서 자주 등장.

---

### Increment (++) / Decrement (--) (인크리먼트 / 데크리먼트)
**한국어 뜻**: 값을 1 증가(++) 또는 1 감소(--)시키는 연산자
**비유**: 엘리베이터 위 버튼(++)과 아래 버튼(--).
**예시 코드**:
```java
int count = 5;
count++;  // count = count + 1; → 6
count--;  // count = count - 1; → 5
```
**시험에서**: for 루프에서 i++ 형태로 거의 항상 등장. AP CSA에서는 전위/후위 구분은 안 나옴.

---

### Operator Precedence (오퍼레이터 프레시던스)
**한국어 뜻**: 연산자 우선순위. 어떤 연산을 먼저 할지 정하는 규칙.
**비유**: 수학에서 곱셈/나눗셈을 더하기/빼기보다 먼저 하는 것과 같다.
**예시 코드**:
```java
int result = 2 + 3 * 4;    // 14 (곱셈 먼저)
int result2 = (2 + 3) * 4; // 20 (괄호 먼저)
```
**시험에서**: 우선순위: () → * / % → + - → 비교 → 논리. 괄호가 없는 복합 연산의 결과를 묻는 문제.

---

### Concatenation (컨캐터네이션)
**한국어 뜻**: 문자열을 + 연산자로 이어 붙이는 것
**비유**: 기차 칸을 연결하듯 문자열들을 줄줄이 이어 붙인다.
**예시 코드**:
```java
String first = "Hello";
String second = "World";
System.out.println(first + " " + second);  // "Hello World"

int age = 17;
System.out.println("나이: " + age);  // "나이: 17" (int가 String으로 자동 변환)

System.out.println(1 + 2 + "abc");  // "3abc" (왼쪽부터: 1+2=3, 3+"abc"="3abc")
System.out.println("abc" + 1 + 2);  // "abc12" (왼쪽부터: "abc"+1="abc1", "abc1"+2="abc12")
```
**시험에서**: 1 + 2 + "abc" = "3abc" vs "abc" + 1 + 2 = "abc12" 차이. 왼쪽부터 순서대로! 초빈출.

---

## Unit 1: 출력

---

### System.out.print (시스템 아웃 프린트)
**한국어 뜻**: 괄호 안의 내용을 출력. 줄바꿈 없음.
**비유**: 같은 줄에 계속 글을 쓰는 것. 엔터를 안 친다.
**예시 코드**:
```java
System.out.print("Hello");
System.out.print(" World");
// 출력: Hello World (한 줄에 이어서)
```
**시험에서**: println과의 차이를 묻는 문제. print는 줄바꿈 없음, println은 줄바꿈 있음.

---

### System.out.println (시스템 아웃 프린트엘엔)
**한국어 뜻**: 괄호 안의 내용을 출력한 후 줄바꿈. ln = line의 약자.
**비유**: 글을 쓰고 엔터를 치는 것.
**예시 코드**:
```java
System.out.println("Hello");
System.out.println("World");
// 출력:
// Hello
// World
```
**시험에서**: 출력 결과를 정확히 맞추는 문제에서 print vs println 구분이 핵심.

---

### Escape Sequence (이스케이프 시퀀스)
**한국어 뜻**: 문자열 안에서 특수 문자를 표현하기 위한 백슬래시(\) 조합
**비유**: 특수 기호를 쓰기 위한 암호. \n은 "여기서 줄바꿈해!" 라는 암호.
**예시 코드**:
```java
System.out.println("Hello\nWorld");   // 줄바꿈
// Hello
// World

System.out.println("She said \"Hi\""); // 큰따옴표 출력
// She said "Hi"

System.out.println("C:\\Users\\Kim"); // 백슬래시 출력
// C:\Users\Kim
```
**시험에서**: \n(줄바꿈), \\"(큰따옴표), \\\\(백슬래시) 세 가지가 핵심. 출력 결과 맞추기 문제.

---

## Unit 2: 메서드와 클래스

---

### Class (클래스)
**한국어 뜻**: 객체를 만들기 위한 설계도(틀). 데이터(변수)와 동작(메서드)을 묶어놓은 것.
**비유**: 붕어빵 틀. 틀 하나로 붕어빵(객체)을 여러 개 찍어낼 수 있다.
**예시 코드**:
```java
public class Dog {
    String name;
    int age;
    
    public void bark() {
        System.out.println(name + " says Woof!");
    }
}
```
**시험에서**: 클래스 정의를 보고 객체 생성 후 동작을 추적하는 문제가 자주 나온다.

---

### Object (오브젝트)
**한국어 뜻**: 클래스에서 만들어진 실체. 메모리에 실제로 존재하는 데이터 덩어리.
**비유**: 붕어빵 틀(클래스)로 만든 실제 붕어빵. 각 붕어빵은 속이 다를 수 있다(팥, 크림 등).
**예시 코드**:
```java
Dog myDog = new Dog();     // Dog 클래스로 객체 생성
myDog.name = "Buddy";
myDog.bark();              // "Buddy says Woof!"
```
**시험에서**: 하나의 클래스에서 여러 객체를 만들 수 있고, 각 객체는 독립적인 데이터를 가진다.

---

### Instance (인스턴스)
**한국어 뜻**: 클래스에서 만들어진 개별 객체. Object와 거의 같은 뜻.
**비유**: "Dog 클래스의 인스턴스" = "Dog 설계도로 만든 실제 강아지 하나"
**예시 코드**:
```java
Dog dog1 = new Dog();  // Dog의 인스턴스 1
Dog dog2 = new Dog();  // Dog의 인스턴스 2 (dog1과 다른 독립 객체)
```
**시험에서**: "인스턴스 변수"는 각 객체마다 따로 있는 변수, "인스턴스 메서드"는 객체를 통해 호출하는 메서드.

---

### Method (메서드)
**한국어 뜻**: 객체가 할 수 있는 동작. 특정 작업을 수행하는 코드 묶음.
**비유**: 리모컨의 버튼. "전원" 버튼을 누르면 정해진 동작(TV 켜기)이 실행된다.
**예시 코드**:
```java
public int add(int a, int b) {   // 메서드 정의
    return a + b;
}

int result = add(3, 5);          // 메서드 호출 → 8
```
**시험에서**: 메서드 호출 시 매개변수 전달과 리턴값 추적이 핵심.

---

### Parameter (파라미터)
**한국어 뜻**: 메서드를 정의할 때 받아들이는 변수. "형식 매개변수(formal parameter)".
**비유**: 주문서의 빈칸. "음료: ___" 에서 빈칸이 파라미터.
**예시 코드**:
```java
public void greet(String name) {  // name이 파라미터
    System.out.println("Hi, " + name);
}
```
**시험에서**: Parameter(정의할 때) vs Argument(호출할 때) 구분 문제. 실질적으로 같은 의미지만 구분해야 한다.

---

### Argument (아규먼트)
**한국어 뜻**: 메서드를 호출할 때 실제로 전달하는 값. "실인자(actual parameter)".
**비유**: 주문서 빈칸에 실제로 적은 내용. "음료: 아메리카노" 에서 "아메리카노"가 아규먼트.
**예시 코드**:
```java
greet("Kim");   // "Kim"이 argument
greet("Lee");   // "Lee"가 argument
```
**시험에서**: Argument의 타입과 순서가 Parameter와 맞아야 한다. 안 맞으면 컴파일 에러.

---

### Return Type (리턴 타입)
**한국어 뜻**: 메서드가 돌려주는 값의 타입. 메서드 이름 앞에 적는다.
**비유**: 자판기에서 나오는 것의 종류. 음료 자판기(int 리턴)는 음료를 주고, 영수증 자판기(String 리턴)는 영수증을 준다.
**예시 코드**:
```java
public int square(int n) {      // 리턴 타입: int
    return n * n;
}
public String hello() {         // 리턴 타입: String
    return "Hello!";
}
```
**시험에서**: 리턴 타입과 실제 return 값의 타입이 맞아야 한다. 안 맞으면 컴파일 에러.

---

### Return Value (리턴 밸류)
**한국어 뜻**: 메서드가 실행 후 돌려주는 결과 값
**비유**: 자판기에서 나온 실제 음료. 동전(인수)을 넣으면 음료(리턴값)가 나온다.
**예시 코드**:
```java
public int add(int a, int b) {
    return a + b;      // a + b의 결과가 리턴 값
}
int sum = add(3, 5);   // sum에 8이 저장됨
```
**시험에서**: return문 이후의 코드는 실행되지 않는다. 메서드 추적 시 리턴값을 정확히 따라가야 한다.

---

### void (보이드)
**한국어 뜻**: "돌려줄 값 없음"을 의미하는 리턴 타입. 동작만 하고 끝.
**비유**: 청소 로봇. 청소만 하고 뭘 갖다주지는 않는다.
**예시 코드**:
```java
public void sayHello() {           // 리턴값 없음
    System.out.println("Hello!");
    // return문 없어도 됨
}
sayHello();                         // 호출만 가능
// int x = sayHello();              // 컴파일 에러! void는 값을 안 돌려줌
```
**시험에서**: void 메서드의 리턴값을 변수에 저장하려 하면 컴파일 에러. void 메서드도 return;으로 일찍 끝낼 수 있다.

---

### Static Method (스태틱 메서드)
**한국어 뜻**: 객체 없이 클래스 이름으로 직접 호출하는 메서드
**비유**: 공용 도구. 특정 사람 것이 아니라 누구나 쓸 수 있는 공용 가위.
**예시 코드**:
```java
// Math 클래스의 static 메서드들
double root = Math.sqrt(16);    // 4.0
int bigger = Math.max(5, 10);   // 10
double rand = Math.random();    // 0.0 ~ 0.999...
```
**시험에서**: Math.random(), Math.abs(), Math.pow() 등이 자주 출제. 호출 시 클래스이름.메서드이름() 형태.

---

### Instance Method (인스턴스 메서드)
**한국어 뜻**: 특정 객체를 통해 호출하는 메서드. 그 객체의 데이터에 접근 가능.
**비유**: 내 휴대폰으로 전화하기. 내 폰(객체)을 통해서만 내 연락처에 접근 가능.
**예시 코드**:
```java
String s = "Hello";
int len = s.length();        // s 객체의 instance method
String upper = s.toUpperCase(); // "HELLO"
```
**시험에서**: static method는 클래스이름.메서드(), instance method는 객체이름.메서드()로 호출.

---

### Constructor (컨스트럭터)
**한국어 뜻**: 객체를 생성할 때 자동으로 호출되는 특수 메서드. 초기값을 설정한다.
**비유**: 공장에서 제품을 만들 때 기본 세팅을 하는 과정. "색: 빨강, 크기: M"으로 초기 설정.
**예시 코드**:
```java
public class Dog {
    String name;
    int age;
    
    public Dog(String n, int a) {  // 생성자 (리턴 타입 없음, 클래스 이름과 같음)
        name = n;
        age = a;
    }
}
Dog myDog = new Dog("Buddy", 3);  // 생성자 호출
```
**시험에서**: 생성자는 리턴 타입이 없고 클래스 이름과 같다. 기본 생성자(매개변수 없음)를 직접 안 만들면 자바가 자동 제공하지만, 매개변수 있는 생성자를 만들면 기본 생성자는 자동 제공 안 됨!

---

### new (뉴)
**한국어 뜻**: 새 객체를 생성하는 키워드. 메모리에 공간을 할당하고 생성자를 호출.
**비유**: "새로 하나 만들어!" 명령. 공장에 "붕어빵 하나 찍어!" 하는 것.
**예시 코드**:
```java
Dog d = new Dog("Buddy", 3);    // Dog 객체 생성
String s = new String("Hello"); // String 객체 생성
int[] arr = new int[5];         // 배열 객체 생성
```
**시험에서**: new 뒤에는 항상 생성자가 온다. 배열도 new로 만든다.

---

### Method Signature (메서드 시그니처)
**한국어 뜻**: 메서드의 이름과 매개변수 목록(타입, 순서, 개수)의 조합. 리턴 타입은 포함 안 됨.
**비유**: 사람의 이름 + 생년월일 조합으로 신원을 식별하는 것.
**예시 코드**:
```java
public int add(int a, int b)     // 시그니처: add(int, int)
public double add(double a, double b)  // 시그니처: add(double, double)
// 이름은 같지만 시그니처가 다르므로 구분됨 (오버로딩)
```
**시험에서**: 오버로딩 문제에서 시그니처가 같은지 다른지 판별. 리턴 타입은 시그니처에 포함 안 됨!

---

### Overloading (오버로딩)
**한국어 뜻**: 같은 이름의 메서드를 매개변수를 다르게 해서 여러 개 정의하는 것
**비유**: "주문하다"라는 같은 동작이지만, "커피 주문"(1개)과 "커피+케이크 주문"(2개)은 다른 주문.
**예시 코드**:
```java
public int add(int a, int b) { return a + b; }
public double add(double a, double b) { return a + b; }
public int add(int a, int b, int c) { return a + b + c; }
// 모두 add지만 매개변수가 다르므로 OK
```
**시험에서**: 오버로딩 가능 여부 판별. 매개변수 타입/개수/순서가 달라야 함. 리턴 타입만 다른 건 오버로딩 안 됨!

---

### API (에이피아이)
**한국어 뜻**: Application Programming Interface. 다른 사람이 만든 프로그램을 사용하기 위한 설명서.
**비유**: 레스토랑 메뉴판. 주방(내부 코드)을 몰라도 메뉴판(API)을 보고 주문(호출)할 수 있다.
**예시 코드**:
```java
// Java API에 있는 Math 클래스를 사용
double result = Math.pow(2, 10);  // 2의 10승 = 1024.0
// Math 내부 코드를 몰라도 API 문서를 보고 사용 가능
```
**시험에서**: AP 시험에서는 주어진 클래스 설명(API 문서)을 읽고 사용하는 문제가 나온다.

---

### Library (라이브러리)
**한국어 뜻**: 미리 만들어진 클래스와 메서드의 모음. 가져다 쓸 수 있는 코드 도서관.
**비유**: 도서관에서 책을 빌려오듯, 다른 사람이 만든 코드를 가져다 쓴다.
**예시 코드**:
```java
import java.util.ArrayList;  // ArrayList 라이브러리 가져오기
import java.util.Scanner;    // Scanner 라이브러리 가져오기
```
**시험에서**: AP 시험에서는 java.lang(자동 포함), java.util 등의 라이브러리를 사용한다.

---

### import (임포트)
**한국어 뜻**: 다른 패키지의 클래스를 현재 파일에서 쓸 수 있게 가져오는 키워드
**비유**: 도서관에서 필요한 책을 꺼내오는 것. import 안 하면 그 클래스를 못 쓴다.
**예시 코드**:
```java
import java.util.Scanner;     // Scanner 클래스 가져오기
import java.util.ArrayList;   // ArrayList 클래스 가져오기
import java.util.*;            // java.util의 모든 클래스 가져오기
// java.lang 패키지(String, Math 등)는 자동 import됨
```
**시험에서**: AP 시험에서는 필요한 import가 이미 되어있다고 가정. 하지만 실제 코딩에서는 빠뜨리면 컴파일 에러.

---

## Unit 2: String 관련

---

### String (스트링)
**한국어 뜻**: 문자열. 글자들의 나열을 저장하는 클래스. Reference Type이다.
**비유**: 글자가 적힌 팔찌. 각 구슬(문자)이 순서대로 연결되어 있다.
**예시 코드**:
```java
String s1 = "Hello";               // 리터럴 방식
String s2 = new String("Hello");   // 객체 생성 방식
System.out.println(s1.length());   // 5
```
**시험에서**: String은 Reference Type이므로 ==가 아니라 .equals()로 비교해야 한다! AP CSA의 최빈출 주제 중 하나.

---

### Immutable (이뮤터블)
**한국어 뜻**: 한번 만들면 변경 불가. String은 immutable이다.
**비유**: 볼펜으로 쓴 글씨. 수정할 수 없고, 새 종이에 다시 써야 한다.
**예시 코드**:
```java
String s = "Hello";
s.toUpperCase();            // s는 그대로 "Hello" (원본 안 바뀜!)
String t = s.toUpperCase(); // t = "HELLO" (새 String 생성)

s = s + " World";           // 새 "Hello World" 객체가 만들어지고 s가 그걸 가리킴
```
**시험에서**: String 메서드는 원본을 바꾸지 않고 새 String을 리턴한다. s.substring(1)만 쓰면 s는 그대로!

---

### length() (렝스)
**한국어 뜻**: 문자열의 길이(글자 수)를 반환하는 메서드
**비유**: 팔찌의 구슬 개수를 세는 것.
**예시 코드**:
```java
String s = "Hello";
System.out.println(s.length());  // 5
System.out.println("".length()); // 0 (빈 문자열)
System.out.println("Hi there".length()); // 8 (공백도 포함)
```
**시험에서**: length()는 메서드(괄호 있음). 배열의 length는 필드(괄호 없음). 헷갈리면 감점!

---

### substring() (서브스트링)
**한국어 뜻**: 문자열의 일부분을 잘라서 새 문자열로 반환
**비유**: 긴 리본에서 원하는 부분만 가위로 잘라내는 것.
**예시 코드**:
```java
String s = "Hello World";
//          01234567890
System.out.println(s.substring(6));      // "World" (인덱스 6부터 끝까지)
System.out.println(s.substring(0, 5));   // "Hello" (인덱스 0~4, 5는 미포함!)
System.out.println(s.substring(2, 5));   // "llo"
```
**시험에서**: substring(a, b)는 인덱스 a부터 b-1까지! b는 포함 안 됨. 초빈출 함정.

---

### indexOf() (인덱스오브)
**한국어 뜻**: 문자열에서 특정 문자/문자열의 위치(인덱스)를 반환. 없으면 -1.
**비유**: 책에서 특정 단어가 몇 페이지에 있는지 찾는 것.
**예시 코드**:
```java
String s = "Hello World";
System.out.println(s.indexOf("World")); // 6
System.out.println(s.indexOf("o"));     // 4 (처음 나오는 위치)
System.out.println(s.indexOf("xyz"));   // -1 (없으면 -1)
```
**시험에서**: 못 찾으면 -1을 반환한다는 것을 기억. 처음 발견된 위치만 반환.

---

### equals() (이퀄즈)
**한국어 뜻**: 두 문자열의 내용이 같은지 비교. true/false 반환.
**비유**: 두 편지의 내용이 같은지 글자 하나하나 대조하는 것.
**예시 코드**:
```java
String a = "Hello";
String b = new String("Hello");
System.out.println(a == b);       // false (주소 비교 - 다른 객체)
System.out.println(a.equals(b));  // true  (내용 비교 - 같은 내용)
```
**시험에서**: String 비교는 반드시 .equals()! ==는 주소 비교라서 같은 내용이어도 false가 나올 수 있다. 매년 출제.

---

### compareTo() (컴페어투)
**한국어 뜻**: 두 문자열을 사전순으로 비교. 음수/0/양수 반환.
**비유**: 사전에서 어떤 단어가 앞에 오는지 비교. "apple" < "banana" (a가 b보다 앞).
**예시 코드**:
```java
String a = "apple";
String b = "banana";
System.out.println(a.compareTo(b));  // 음수 (a가 b보다 사전순 앞)
System.out.println(b.compareTo(a));  // 양수 (b가 a보다 사전순 뒤)
System.out.println(a.compareTo("apple")); // 0 (같음)
```
**시험에서**: 리턴값의 부호만 중요. 음수=앞, 0=같음, 양수=뒤. 대문자가 소문자보다 앞(A < a).

---

## Unit 3: 조건문

---

### Boolean (불리언 - 타입으로서)
**한국어 뜻**: true 또는 false 값을 가지는 데이터 타입 (위에서 설명한 것과 같음)
**비유**: 동전의 앞면(true)과 뒷면(false).
**예시 코드**:
```java
boolean isRaining = true;
boolean isSunny = !isRaining;  // false
```
**시험에서**: 조건문과 반복문의 핵심. 모든 조건식의 결과는 boolean이다.

---

### Boolean Expression (불리언 익스프레션)
**한국어 뜻**: 결과가 true 또는 false인 식
**비유**: "오늘 비 오나요?" 같은 예/아니오 질문.
**예시 코드**:
```java
int x = 5;
boolean result1 = (x > 3);          // true
boolean result2 = (x == 10);        // false
boolean result3 = (x > 0 && x < 10); // true
```
**시험에서**: 복잡한 boolean 표현식의 결과를 판단하는 문제가 자주 나온다.

---

### Relational Operator (리레이셔널 오퍼레이터)
**한국어 뜻**: 두 값을 비교하는 연산자. ==, !=, <, >, <=, >=
**비유**: 저울. 두 물건의 무게를 비교해서 "같다/다르다/크다/작다"를 알려준다.
**예시 코드**:
```java
int a = 5, b = 10;
System.out.println(a == b);  // false (같은가?)
System.out.println(a != b);  // true  (다른가?)
System.out.println(a < b);   // true  (작은가?)
System.out.println(a > b);   // false (큰가?)
System.out.println(a <= 5);  // true  (작거나 같은가?)
System.out.println(a >= 6);  // false (크거나 같은가?)
```
**시험에서**: = (대입)과 == (비교) 헷갈리지 말 것! == 는 primitive 비교 OK, Reference는 .equals() 사용.

---

### if (이프)
**한국어 뜻**: 조건이 true일 때만 코드를 실행하는 조건문
**비유**: "비가 오면 우산을 가져간다." 비가 오는 조건이 맞을 때만 우산을 챙긴다.
**예시 코드**:
```java
int score = 85;
if (score >= 90) {
    System.out.println("A");
}
// score가 85이므로 아무것도 출력 안 됨
```
**시험에서**: if문의 조건에 따라 어떤 코드가 실행되는지 추적하는 문제. 중괄호 범위 주의.

---

### else (엘스)
**한국어 뜻**: if 조건이 false일 때 실행되는 코드 블록
**비유**: "비가 오면 우산, 아니면 모자를 쓴다."
**예시 코드**:
```java
int score = 85;
if (score >= 90) {
    System.out.println("A");
} else {
    System.out.println("Not A");
}
// 출력: Not A
```
**시험에서**: if-else는 둘 중 하나만 실행된다. 절대 둘 다 실행되지 않음.

---

### else if (엘스 이프)
**한국어 뜻**: 이전 조건이 false일 때 새로운 조건을 검사
**비유**: 성적표: "90 이상이면 A, 80 이상이면 B, 70 이상이면 C, 나머지 F"
**예시 코드**:
```java
int score = 85;
if (score >= 90) {
    System.out.println("A");
} else if (score >= 80) {
    System.out.println("B");     // 이게 실행됨
} else if (score >= 70) {
    System.out.println("C");
} else {
    System.out.println("F");
}
// 출력: B
```
**시험에서**: 위에서부터 순서대로 검사하고, 처음 true인 곳에서 실행 후 나머지는 건너뜀. 순서가 중요!

---

### Logical Operator (&&, ||, !) (로지컬 오퍼레이터)
**한국어 뜻**: boolean 값을 조합하는 연산자. &&(AND), ||(OR), !(NOT)
**비유**: &&는 "둘 다 맞아야", ||는 "하나만 맞아도", !는 "반대로".
**예시 코드**:
```java
int age = 17;
boolean hasID = true;

// AND: 둘 다 true여야 true
boolean canEnter = (age >= 18) && hasID;   // false (나이가 안 됨)

// OR: 하나만 true여도 true
boolean canDiscount = (age < 18) || (age >= 65);  // true

// NOT: 반대로
boolean isMinor = !(age >= 18);  // true
```
**시험에서**: 복잡한 논리 연산 결과를 정확히 계산하는 문제. 드모르간 법칙과 함께 출제.

---

### Short-circuit Evaluation (숏서킷 이밸류에이션)
**한국어 뜻**: 논리 연산에서 결과가 이미 확정되면 나머지를 계산하지 않는 것
**비유**: "시험에 합격했니 AND 면접도 합격했니?" → 시험 불합격이면 면접 결과는 볼 필요 없다.
**예시 코드**:
```java
String s = null;
// &&: 왼쪽이 false면 오른쪽은 확인 안 함
if (s != null && s.length() > 0) {  // s가 null이므로 s.length()를 실행 안 함 → 에러 방지!
    System.out.println(s);
}
// ||: 왼쪽이 true면 오른쪽은 확인 안 함
```
**시험에서**: null 체크에서 && 순서가 중요. s.length() > 0 && s != null은 NullPointerException 발생!

---

### De Morgan's Law (드 모르간의 법칙)
**한국어 뜻**: 논리식을 변환하는 법칙. !(A && B) = !A || !B, !(A || B) = !A && !B
**비유**: "둘 다 맞는 게 아니다" = "하나는 틀리다". "하나라도 맞는 게 아니다" = "둘 다 틀리다".
**예시 코드**:
```java
int x = 5;
// 아래 두 줄은 같은 의미
boolean a = !(x > 3 && x < 10);
boolean b = (x <= 3 || x >= 10);   // De Morgan 적용

// 아래 두 줄도 같은 의미
boolean c = !(x == 1 || x == 2);
boolean d = (x != 1 && x != 2);    // De Morgan 적용
```
**시험에서**: "다음과 동치(equivalent)인 표현식은?" 문제로 매년 출제. !를 분배하면 &&↔||가 바뀐다.

---

## Unit 4: 반복문

---

### Iteration (이터레이션)
**한국어 뜻**: 반복. 같은 코드를 여러 번 실행하는 것.
**비유**: 운동장 10바퀴 뛰기. 같은 동작(한 바퀴 뛰기)을 10번 반복.
**예시 코드**:
```java
for (int i = 0; i < 10; i++) {
    System.out.println("바퀴 " + (i + 1));
}
```
**시험에서**: "이 루프는 몇 번 반복하는가?" 또는 "i번째 반복에서 변수의 값은?" 형태로 출제.

---

### Loop (루프)
**한국어 뜻**: 반복문. 조건이 true인 동안 코드를 반복 실행하는 구조.
**비유**: 회전목마. 조건이 맞는 동안 계속 돈다.
**예시 코드**:
```java
// while 루프
int i = 0;
while (i < 5) {
    System.out.println(i);
    i++;
}
```
**시험에서**: while, for, enhanced for 세 종류의 루프를 모두 알아야 한다.

---

### while Loop (와일 루프)
**한국어 뜻**: 조건이 true인 동안 반복하는 루프. 반복 횟수를 모를 때 주로 사용.
**비유**: "배부를 때까지 먹는다." 몇 번 먹을지 모르지만 조건(배부름)이 될 때까지 반복.
**예시 코드**:
```java
int count = 1;
while (count <= 5) {
    System.out.println(count);  // 1, 2, 3, 4, 5
    count++;
}
```
**시험에서**: while 루프는 조건을 먼저 검사. 처음부터 false면 한 번도 실행 안 됨.

---

### for Loop (포 루프)
**한국어 뜻**: 초기화, 조건, 증감을 한 줄에 쓰는 반복문. 반복 횟수가 정해져 있을 때 사용.
**비유**: "1번부터 10번까지 번호 순서대로 호명." 시작, 끝, 증가 규칙이 명확.
**예시 코드**:
```java
// for (초기화; 조건; 증감)
for (int i = 0; i < 5; i++) {
    System.out.println(i);  // 0, 1, 2, 3, 4
}
// i는 0부터 시작, 5 미만인 동안, 1씩 증가
```
**시험에서**: for 루프의 실행 순서: 초기화 → 조건 확인 → 실행 → 증감 → 조건 확인 → ... 반복 횟수 계산 빈출.

---

### Enhanced for Loop / for-each (인핸스드 포 루프)
**한국어 뜻**: 배열이나 컬렉션의 모든 원소를 하나씩 꺼내는 간편한 반복문
**비유**: 사탕 봉지에서 사탕을 하나씩 꺼내서 먹는 것. 몇 번째인지 신경 안 쓰고 순서대로.
**예시 코드**:
```java
int[] nums = {10, 20, 30, 40, 50};
for (int n : nums) {        // "nums에서 하나씩 꺼내서 n에 넣는다"
    System.out.println(n);  // 10, 20, 30, 40, 50
}
```
**시험에서**: 인덱스가 필요 없을 때 사용. 단, 원소를 수정하거나 인덱스가 필요하면 일반 for 루프를 써야 한다.

---

### Infinite Loop (인피닛 루프)
**한국어 뜻**: 끝나지 않는 반복문. 조건이 절대 false가 되지 않아서 영원히 반복.
**비유**: 출구 없는 미로. 빠져나올 조건이 없다.
**예시 코드**:
```java
// 무한 루프 예시 (실행하면 안 됨!)
while (true) {
    System.out.println("끝나지 않는다...");
}

// 흔한 실수
int i = 0;
while (i < 10) {
    System.out.println(i);
    // i++를 빼먹으면 무한 루프!
}
```
**시험에서**: "다음 중 무한 루프에 빠지는 코드는?" 문제. 종료 조건에 도달할 수 있는지 확인.

---

### Off-by-one Error (오프 바이 원 에러)
**한국어 뜻**: 반복 횟수가 1번 많거나 1번 적게 실행되는 논리 에러
**비유**: 100미터 울타리에 기둥을 세울 때, 10미터 간격이면 기둥이 10개가 아니라 11개 필요한 것.
**예시 코드**:
```java
// 1~10을 출력하려는데...
for (int i = 0; i < 10; i++) {    // 0~9 출력 (의도와 다름)
    System.out.println(i);
}
for (int i = 1; i <= 10; i++) {   // 1~10 출력 (올바름)
    System.out.println(i);
}
```
**시험에서**: < vs <= , 시작값 0 vs 1에 따라 결과가 달라진다. "몇 번 반복하는가?" 문제의 단골 함정.

---

### Nested Loop (네스티드 루프)
**한국어 뜻**: 반복문 안에 반복문이 있는 구조
**비유**: 달력. 바깥 루프=월(1~12), 안쪽 루프=일(1~30). 매달 날짜를 반복.
**예시 코드**:
```java
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 4; j++) {
        System.out.print("*");
    }
    System.out.println();
}
// 출력:
// ****
// ****
// ****
```
**시험에서**: 총 반복 횟수 = 바깥 × 안쪽. 2D 배열 탐색에 필수. 코드 추적이 복잡해지므로 표를 그려서 풀자.

---

## Unit 5: OOP (객체 지향 프로그래밍)

---

### Object-Oriented Programming / OOP (오오피)
**한국어 뜻**: 프로그램을 객체(데이터+동작) 단위로 설계하는 프로그래밍 방식
**비유**: 레고 블록 조립. 각 블록(객체)이 독립적이고, 블록들을 조합해서 큰 구조물을 만든다.
**예시 코드**:
```java
// 절차적: 함수들의 나열
// OOP: 관련 데이터와 동작을 클래스로 묶음
public class BankAccount {
    private double balance;
    public void deposit(double amount) { balance += amount; }
    public double getBalance() { return balance; }
}
```
**시험에서**: AP CSA는 OOP 기반 시험. 클래스 설계, 캡슐화, 상호작용이 핵심.

---

### Encapsulation (인캡슐레이션)
**한국어 뜻**: 데이터를 숨기고 메서드를 통해서만 접근하게 하는 것
**비유**: ATM 기계. 내부 금고(데이터)를 직접 열 수 없고, 버튼(메서드)으로만 입출금한다.
**예시 코드**:
```java
public class Student {
    private String name;   // private: 외부에서 직접 접근 불가
    private int grade;
    
    public String getName() { return name; }          // getter
    public void setName(String n) { name = n; }       // setter
}
// student.name = "Kim";  → 컴파일 에러!
// student.setName("Kim"); → OK!
```
**시험에서**: "왜 변수를 private으로 선언하는가?" → 캡슐화. getter/setter로 접근 제어. FRQ에서 클래스 설계 시 필수.

---

### Abstraction (앱스트랙션)
**한국어 뜻**: 복잡한 내부 구현을 숨기고 필요한 기능만 보여주는 것
**비유**: 자동차 운전. 엔진 원리를 몰라도 핸들과 페달만 알면 운전할 수 있다.
**예시 코드**:
```java
// Math.sqrt()의 내부 구현을 몰라도 사용 가능
double result = Math.sqrt(16);  // 4.0
// "어떻게"가 아니라 "무엇을" 하는지만 알면 됨
```
**시험에서**: 메서드를 호출할 때 내부 구현을 몰라도 사용할 수 있다는 개념.

---

### Access Modifier (액세스 모디파이어)
**한국어 뜻**: 클래스, 변수, 메서드에 대한 접근 범위를 제어하는 키워드
**비유**: 건물 출입 권한. public=누구나, private=직원만.
**예시 코드**:
```java
public class Example {
    public int a;    // 어디서든 접근 가능
    private int b;   // 이 클래스 안에서만 접근 가능
}
```
**시험에서**: AP CSA에서는 public과 private만 알면 된다. 변수는 private, 메서드는 보통 public.

---

### public (퍼블릭)
**한국어 뜻**: 어디서든 접근 가능한 접근 제어자
**비유**: 공개된 게시판. 누구나 볼 수 있다.
**예시 코드**:
```java
public class Dog {
    public void bark() {         // 어디서든 호출 가능
        System.out.println("Woof!");
    }
}
```
**시험에서**: 메서드와 클래스는 보통 public. 변수를 public으로 하면 캡슐화 위반.

---

### private (프라이빗)
**한국어 뜻**: 해당 클래스 안에서만 접근 가능한 접근 제어자
**비유**: 개인 일기장. 본인만 볼 수 있고 다른 사람은 못 본다.
**예시 코드**:
```java
public class Dog {
    private String name;  // 이 클래스 안에서만 접근 가능
    
    public String getName() {   // 외부에서는 getter로 접근
        return name;
    }
}
// Dog d = new Dog();
// d.name;  → 컴파일 에러! (private)
// d.getName();  → OK!
```
**시험에서**: 인스턴스 변수는 private으로 선언하는 것이 정석. FRQ 클래스 작성에서 필수.

---

### Accessor / Getter (액세서 / 게터)
**한국어 뜻**: private 변수의 값을 읽어서 반환하는 메서드
**비유**: 은행 잔고 조회. 돈(데이터)을 직접 보는 게 아니라 조회 기능(getter)으로 확인.
**예시 코드**:
```java
public class Student {
    private String name;
    
    public String getName() {   // accessor (getter)
        return name;
    }
}
```
**시험에서**: getter는 리턴 타입이 있고, 매개변수가 없는 것이 일반적. get + 변수이름 형태.

---

### Mutator / Setter (뮤테이터 / 세터)
**한국어 뜻**: private 변수의 값을 변경하는 메서드
**비유**: 은행 입금. 돈(데이터)을 직접 넣는 게 아니라 입금 기능(setter)으로 넣는다.
**예시 코드**:
```java
public class Student {
    private String name;
    
    public void setName(String newName) {   // mutator (setter)
        name = newName;
    }
}
```
**시험에서**: setter는 void 리턴, 매개변수 있음. set + 변수이름 형태. FRQ에서 setter 작성 문제 나옴.

---

### this (디스)
**한국어 뜻**: 현재 객체 자신을 가리키는 키워드
**비유**: "나 자신". 자기소개할 때 "제 이름은 ○○입니다"에서 "제"가 this.
**예시 코드**:
```java
public class Dog {
    private String name;
    
    public Dog(String name) {
        this.name = name;  // this.name = 인스턴스 변수, name = 매개변수
    }
}
```
**시험에서**: 매개변수와 인스턴스 변수 이름이 같을 때 this로 구분. this.name vs name.

---

### static (스태틱)
**한국어 뜻**: 객체가 아닌 클래스에 속하는 것. 모든 객체가 공유.
**비유**: 교실의 시계. 학생(객체) 개인 것이 아니라 교실(클래스) 전체가 공유하는 것.
**예시 코드**:
```java
public class Counter {
    static int count = 0;     // 클래스 변수 (모든 객체가 공유)
    
    public Counter() {
        count++;              // 객체가 만들어질 때마다 공유 변수 증가
    }
    
    public static int getCount() {  // static 메서드
        return count;
    }
}
// Counter.getCount();  → 객체 없이 호출 가능
```
**시험에서**: static 변수는 객체마다 따로 있지 않고 클래스에 하나만 존재. static 메서드에서 인스턴스 변수 접근 불가.

---

### final (파이널)
**한국어 뜻**: 한번 값이 정해지면 변경 불가. 상수를 만들 때 사용.
**비유**: 볼펜으로 돌에 새긴 글자. 한번 새기면 바꿀 수 없다.
**예시 코드**:
```java
final double PI = 3.14159;
// PI = 3.0;  → 컴파일 에러! final 변수는 변경 불가
final int MAX_SIZE = 100;
```
**시험에서**: 상수 이름은 관례상 대문자+언더스코어(MAX_SIZE). final 변수 재대입 시 컴파일 에러.

---

### Scope (스코프)
**한국어 뜻**: 변수가 사용 가능한 범위. 선언된 중괄호 {} 안에서만 사용 가능.
**비유**: 학교 교실. 그 교실(중괄호) 안에서만 책상(변수)을 쓸 수 있다.
**예시 코드**:
```java
public void test() {
    int x = 10;              // 메서드 전체에서 사용 가능
    if (x > 5) {
        int y = 20;          // if 블록 안에서만 사용 가능
        System.out.println(x + y);  // OK
    }
    // System.out.println(y);  → 컴파일 에러! y는 if 블록 밖에서 사용 불가
}
```
**시험에서**: for 루프의 int i는 루프 안에서만 유효. 루프 밖에서 i를 쓰면 컴파일 에러.

---

### Local Variable (로컬 변수)
**한국어 뜻**: 메서드 안에서 선언된 변수. 그 메서드 안에서만 사용 가능.
**비유**: 교실 안의 임시 메모. 수업이 끝나면(메서드 종료) 메모도 사라진다.
**예시 코드**:
```java
public void calculate() {
    int temp = 0;    // 지역 변수 (이 메서드 안에서만 존재)
    temp = 42;
}  // 여기서 temp 소멸
```
**시험에서**: 지역 변수는 자동 초기화 안 됨. 초기화 안 하고 쓰면 컴파일 에러. 인스턴스 변수와 구분!

---

### Instance Variable (인스턴스 변수)
**한국어 뜻**: 클래스 안에서 선언되고, 각 객체마다 따로 가지는 변수
**비유**: 학생의 성적표. 각 학생(객체)마다 자기만의 성적(인스턴스 변수)이 있다.
**예시 코드**:
```java
public class Student {
    private String name;   // 인스턴스 변수 (각 Student 객체마다 다름)
    private int score;     // 인스턴스 변수
}
Student s1 = new Student();
Student s2 = new Student();
// s1.name과 s2.name은 서로 다른 변수
```
**시험에서**: 인스턴스 변수는 자동 초기화됨 (int→0, double→0.0, boolean→false, 참조→null). 지역 변수와 차이!

---

### Class Variable (클래스 변수)
**한국어 뜻**: static으로 선언된 변수. 모든 객체가 공유하는 하나의 변수.
**비유**: 학교 게시판. 모든 학생이 같은 게시판을 본다.
**예시 코드**:
```java
public class Student {
    private static int totalStudents = 0;  // 클래스 변수 (공유)
    private String name;                    // 인스턴스 변수 (개별)
    
    public Student(String name) {
        this.name = name;
        totalStudents++;  // 학생이 생성될 때마다 공유 카운터 증가
    }
}
```
**시험에서**: static 변수는 클래스이름.변수이름 또는 객체이름.변수이름으로 접근. 모든 객체가 같은 값을 공유.

---

## Unit 6: 자료구조 - Array

---

### Array (배열 / 어레이)
**한국어 뜻**: 같은 타입의 데이터를 여러 개 연속으로 저장하는 자료구조. 크기 고정.
**비유**: 아파트 호수. 101호, 102호, 103호... 같은 구조의 방이 번호 순서대로 있다.
**예시 코드**:
```java
int[] scores = new int[5];          // 크기 5의 int 배열 생성 (모두 0으로 초기화)
int[] nums = {90, 85, 92, 78, 88}; // 선언과 동시에 초기화
System.out.println(nums[0]);        // 90 (첫 번째 원소, 인덱스 0)
System.out.println(nums[4]);        // 88 (마지막 원소)
// nums[5]  → ArrayIndexOutOfBoundsException!
```
**시험에서**: 인덱스는 0부터 시작! 크기가 n이면 마지막 인덱스는 n-1. 배열 크기는 생성 후 변경 불가.

---

### Index (인덱스)
**한국어 뜻**: 배열이나 문자열에서 각 원소의 위치 번호. 0부터 시작.
**비유**: 아파트 호수. 0호부터 시작하는 아파트.
**예시 코드**:
```java
int[] arr = {10, 20, 30};
// 인덱스:    0   1   2
System.out.println(arr[0]);  // 10 (첫 번째)
System.out.println(arr[2]);  // 30 (세 번째)
```
**시험에서**: 0-based indexing. 첫 번째 원소는 인덱스 0, 마지막 원소는 인덱스 length-1.

---

### length (배열의 길이)
**한국어 뜻**: 배열의 크기(원소 개수). 필드(괄호 없음)로 접근.
**비유**: 아파트 총 세대수.
**예시 코드**:
```java
int[] arr = {10, 20, 30, 40, 50};
System.out.println(arr.length);     // 5 (괄호 없음!)
// String의 length()와 구분!
// String s = "Hello";
// s.length()   → 메서드 (괄호 있음)
// arr.length   → 필드 (괄호 없음)
```
**시험에서**: 배열은 .length (괄호X), String은 .length() (괄호O), ArrayList는 .size() (괄호O). 셋 다 다르다!

---

## Unit 7: 자료구조 - ArrayList

---

### ArrayList (어레이리스트)
**한국어 뜻**: 크기가 자동으로 늘어나는 배열. java.util.ArrayList에 있음.
**비유**: 고무줄 가방. 물건을 넣으면 알아서 늘어나고, 빼면 줄어든다.
**예시 코드**:
```java
import java.util.ArrayList;
ArrayList<String> names = new ArrayList<String>();
names.add("Kim");      // ["Kim"]
names.add("Lee");      // ["Kim", "Lee"]
names.add("Park");     // ["Kim", "Lee", "Park"]
System.out.println(names.size());  // 3
System.out.println(names.get(0));  // "Kim"
```
**시험에서**: ArrayList는 Reference Type만 저장 가능 (int 대신 Integer). 크기가 자동 조절된다는 점이 배열과의 차이.

---

### size() (사이즈)
**한국어 뜻**: ArrayList의 현재 원소 개수를 반환
**비유**: 가방에 지금 몇 개 들어있는지 세는 것.
**예시 코드**:
```java
ArrayList<String> list = new ArrayList<String>();
System.out.println(list.size());  // 0 (비어있음)
list.add("A");
list.add("B");
System.out.println(list.size());  // 2
```
**시험에서**: ArrayList는 size(), 배열은 length, String은 length(). 세 가지 구분!

---

### add() (애드)
**한국어 뜻**: ArrayList에 원소를 추가하는 메서드
**비유**: 가방에 물건을 넣는 것.
**예시 코드**:
```java
ArrayList<String> list = new ArrayList<String>();
list.add("A");        // 끝에 추가: ["A"]
list.add("B");        // 끝에 추가: ["A", "B"]
list.add(1, "C");     // 인덱스 1에 삽입: ["A", "C", "B"]
```
**시험에서**: add(값)은 끝에 추가, add(인덱스, 값)은 해당 위치에 삽입하고 나머지를 뒤로 밀어냄.

---

### remove() (리무브)
**한국어 뜻**: ArrayList에서 원소를 제거하는 메서드
**비유**: 가방에서 물건을 꺼내는 것. 뒤의 물건들이 앞으로 당겨진다.
**예시 코드**:
```java
ArrayList<String> list = new ArrayList<String>();
list.add("A"); list.add("B"); list.add("C");  // ["A", "B", "C"]
list.remove(1);         // 인덱스 1 제거: ["A", "C"]
list.remove("A");       // "A" 제거: ["C"]
```
**시험에서**: remove 후 뒤의 원소들이 앞으로 당겨짐. 루프에서 remove하면 인덱스가 밀려서 버그 발생! 뒤에서부터 삭제하면 안전.

---

### get() (겟)
**한국어 뜻**: ArrayList에서 특정 인덱스의 원소를 가져오는 메서드
**비유**: 가방에서 몇 번째 물건을 꺼내보는 것 (빼는 게 아니라 확인만).
**예시 코드**:
```java
ArrayList<String> list = new ArrayList<String>();
list.add("A"); list.add("B"); list.add("C");
System.out.println(list.get(0));  // "A"
System.out.println(list.get(2));  // "C"
// list.get(5);  → IndexOutOfBoundsException!
```
**시험에서**: 배열은 arr[i], ArrayList는 list.get(i). 대괄호 vs get() 구분.

---

### set() (셋)
**한국어 뜻**: ArrayList에서 특정 인덱스의 원소를 새 값으로 교체하는 메서드
**비유**: 가방의 3번째 칸에 있는 물건을 다른 물건으로 바꿔치기.
**예시 코드**:
```java
ArrayList<String> list = new ArrayList<String>();
list.add("A"); list.add("B"); list.add("C");  // ["A", "B", "C"]
list.set(1, "X");                               // ["A", "X", "C"]
String old = list.set(0, "Y");                  // old = "A", list = ["Y", "X", "C"]
```
**시험에서**: set()은 원래 있던 값을 리턴한다. 크기는 변하지 않음 (add/remove와 차이).

---

### Wrapper Class (래퍼 클래스)
**한국어 뜻**: Primitive Type을 객체로 감싸는 클래스. int→Integer, double→Double 등.
**비유**: 선물 포장. 알맹이(primitive)를 예쁜 상자(객체)에 담아서 주는 것.
**예시 코드**:
```java
// ArrayList는 primitive 타입을 직접 못 담음
// ArrayList<int> list = ...;  → 컴파일 에러!
ArrayList<Integer> list = new ArrayList<Integer>();  // Integer로 감싸야 함
list.add(42);  // autoboxing: int 42 → Integer 42
int n = list.get(0);  // unboxing: Integer 42 → int 42
```
**시험에서**: ArrayList에 int를 넣으려면 Integer, double을 넣으려면 Double을 써야 한다.

---

### Integer (인티저)
**한국어 뜻**: int의 Wrapper 클래스. int를 객체로 감싼 것.
**비유**: int라는 알맹이를 Integer라는 상자에 담은 것.
**예시 코드**:
```java
Integer num = 42;                          // autoboxing
int val = num;                              // unboxing
int max = Integer.MAX_VALUE;               // 2147483647
int parsed = Integer.parseInt("123");      // 문자열 → int 변환
```
**시험에서**: Integer.MAX_VALUE, Integer.MIN_VALUE, Integer.parseInt() 알아두자.

---

### Double (더블 - 래퍼)
**한국어 뜻**: double의 Wrapper 클래스.
**비유**: double이라는 알맹이를 Double이라는 상자에 담은 것.
**예시 코드**:
```java
Double d = 3.14;    // autoboxing
double val = d;     // unboxing
ArrayList<Double> prices = new ArrayList<Double>();
prices.add(9.99);   // autoboxing
```
**시험에서**: ArrayList에 실수를 넣으려면 Double 사용.

---

### Autoboxing (오토박싱)
**한국어 뜻**: primitive 값이 자동으로 Wrapper 객체로 변환되는 것
**비유**: 선물을 주면 자동으로 포장해주는 기계.
**예시 코드**:
```java
Integer num = 42;               // int 42 → Integer 42 (자동 변환)
ArrayList<Integer> list = new ArrayList<Integer>();
list.add(10);                   // int 10 → Integer 10 (자동)
```
**시험에서**: 자바가 자동으로 해주므로 의식하지 못할 수 있지만, 원리는 알아야 한다.

---

### Unboxing (언박싱)
**한국어 뜻**: Wrapper 객체가 자동으로 primitive 값으로 변환되는 것
**비유**: 선물 포장을 자동으로 풀어주는 기계.
**예시 코드**:
```java
Integer num = 42;
int val = num;     // Integer 42 → int 42 (자동 변환)

ArrayList<Integer> list = new ArrayList<Integer>();
list.add(10);
int x = list.get(0);  // Integer 10 → int 10 (자동)
```
**시험에서**: null인 Wrapper를 unboxing하면 NullPointerException! 주의.

---

### 2D Array (2차원 배열)
**한국어 뜻**: 배열의 배열. 행(row)과 열(column)으로 이루어진 표 형태의 데이터.
**비유**: 엑셀 스프레드시트. 행과 열이 있는 표.
**예시 코드**:
```java
int[][] grid = new int[3][4];    // 3행 4열
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
System.out.println(matrix[0][2]); // 3 (0행 2열)
System.out.println(matrix.length);    // 3 (행 수)
System.out.println(matrix[0].length); // 3 (열 수)
```
**시험에서**: matrix[row][col] 순서. matrix.length=행수, matrix[0].length=열수. FRQ에서 2D 배열 문제 매년 출제.

---

### Row-major (로우 메이저)
**한국어 뜻**: 2D 배열을 행(가로줄) 단위로 순서대로 탐색하는 방식
**비유**: 책을 읽을 때 한 줄씩 왼쪽→오른쪽으로 읽는 것.
**예시 코드**:
```java
int[][] grid = {{1,2,3},{4,5,6},{7,8,9}};
// Row-major 순서: 1,2,3,4,5,6,7,8,9
for (int row = 0; row < grid.length; row++) {           // 행 먼저
    for (int col = 0; col < grid[row].length; col++) {  // 열 순서대로
        System.out.print(grid[row][col] + " ");
    }
}
```
**시험에서**: 바깥 루프=행, 안쪽 루프=열이면 row-major. AP 시험에서 기본 탐색 방식.

---

### Column-major (컬럼 메이저)
**한국어 뜻**: 2D 배열을 열(세로줄) 단위로 순서대로 탐색하는 방식
**비유**: 신문의 세로 기사를 위에서 아래로 읽는 것.
**예시 코드**:
```java
int[][] grid = {{1,2,3},{4,5,6},{7,8,9}};
// Column-major 순서: 1,4,7,2,5,8,3,6,9
for (int col = 0; col < grid[0].length; col++) {       // 열 먼저
    for (int row = 0; row < grid.length; row++) {      // 행 순서대로
        System.out.print(grid[row][col] + " ");
    }
}
```
**시험에서**: 바깥 루프=열, 안쪽 루프=행이면 column-major. row-major와 결과 순서가 다름에 주의.

---

## Unit 7-10: 알고리즘

---

### Traversal (트래버설)
**한국어 뜻**: 배열이나 리스트의 모든 원소를 하나씩 방문하는 것
**비유**: 복도의 모든 방을 하나씩 노크하며 확인하는 것.
**예시 코드**:
```java
int[] arr = {10, 20, 30, 40, 50};

// 인덱스로 traversal
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}

// for-each로 traversal
for (int num : arr) {
    System.out.println(num);
}
```
**시험에서**: 모든 원소를 빠짐없이 방문하는 것이 traversal. 배열, ArrayList, String, 2D 배열 모두 해당.

---

### Linear Search (리니어 서치)
**한국어 뜻**: 처음부터 끝까지 하나씩 비교하며 찾는 탐색 알고리즘
**비유**: 출석부를 1번부터 끝까지 하나씩 이름을 확인하며 찾는 것.
**예시 코드**:
```java
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) {
            return i;    // 찾으면 인덱스 반환
        }
    }
    return -1;           // 못 찾으면 -1
}
```
**시험에서**: 시간복잡도 O(n). 정렬 안 된 데이터에서도 사용 가능. Binary Search와 비교 문제 출제.

---

### Binary Search (바이너리 서치)
**한국어 뜻**: 정렬된 배열에서 중간값과 비교하며 반씩 줄여가며 찾는 탐색 알고리즘
**비유**: 사전에서 단어 찾기. 가운데를 펴서 앞인지 뒤인지 확인하고, 해당 반쪽에서 다시 가운데를 편다.
**예시 코드**:
```java
public static int binarySearch(int[] arr, int target) {
    int low = 0, high = arr.length - 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}
```
**시험에서**: 반드시 정렬된 배열에서만 사용 가능! 시간복잡도 O(log n). "최대 몇 번 비교하는가?" 문제 빈출.

---

### Selection Sort (셀렉션 소트)
**한국어 뜻**: 가장 작은(큰) 값을 찾아서 맨 앞으로 보내는 정렬 알고리즘
**비유**: 키 순서대로 줄 세우기. 전체에서 가장 작은 사람을 맨 앞으로, 그 다음 작은 사람을 그 뒤로...
**예시 코드**:
```java
public static void selectionSort(int[] arr) {
    for (int i = 0; i < arr.length - 1; i++) {
        int minIdx = i;
        for (int j = i + 1; j < arr.length; j++) {
            if (arr[j] < arr[minIdx]) {
                minIdx = j;
            }
        }
        // swap
        int temp = arr[i];
        arr[i] = arr[minIdx];
        arr[minIdx] = temp;
    }
}
```
**시험에서**: 시간복잡도 O(n^2). "k번째 패스 후 배열 상태는?" 형태 문제. 코드 추적 연습 필수.

---

### Insertion Sort (인서션 소트)
**한국어 뜻**: 카드를 한 장씩 올바른 위치에 끼워넣는 정렬 알고리즘
**비유**: 카드 게임에서 새 카드를 받으면 이미 정렬된 손패에서 맞는 위치에 끼워넣는 것.
**예시 코드**:
```java
public static void insertionSort(int[] arr) {
    for (int i = 1; i < arr.length; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
```
**시험에서**: 시간복잡도 O(n^2). Selection Sort와 비교해서 동작 원리 차이를 묻는 문제.

---

### Merge Sort (머지 소트)
**한국어 뜻**: 배열을 반으로 나누고, 각각 정렬한 후, 합치는 정렬 알고리즘 (분할 정복)
**비유**: 카드 더미를 반으로 나누고 → 각각 정렬하고 → 두 더미를 하나로 합치면서 순서대로 놓는다.
**예시 코드**:
```java
public static void mergeSort(int[] arr, int left, int right) {
    if (left < right) {
        int mid = (left + right) / 2;
        mergeSort(arr, left, mid);      // 왼쪽 반 정렬
        mergeSort(arr, mid + 1, right); // 오른쪽 반 정렬
        merge(arr, left, mid, right);   // 합치기
    }
}
```
**시험에서**: 시간복잡도 O(n log n)으로 Selection/Insertion Sort보다 빠르다. 재귀 호출 과정 추적 문제.

---

### Recursion (리커전)
**한국어 뜻**: 메서드가 자기 자신을 호출하는 것
**비유**: 거울 앞에 거울을 놓으면 무한히 반사되는 것. 단, 멈추는 조건(base case)이 있어야 한다.
**예시 코드**:
```java
public static int factorial(int n) {
    if (n <= 1) return 1;           // Base Case (멈추는 조건)
    return n * factorial(n - 1);    // Recursive Case (자기 자신 호출)
}
// factorial(4) = 4 * factorial(3) = 4 * 3 * factorial(2) = 4 * 3 * 2 * 1 = 24
```
**시험에서**: 재귀 호출 추적이 매년 출제. Base Case 없으면 StackOverflowError!

---

### Base Case (베이스 케이스)
**한국어 뜻**: 재귀를 멈추는 조건. 더 이상 자기 자신을 호출하지 않는 경우.
**비유**: "이 칸에 도착하면 멈춰!" 하는 정지선.
**예시 코드**:
```java
public static int sum(int n) {
    if (n == 0) return 0;       // base case: n이 0이면 멈춤
    return n + sum(n - 1);      // recursive case
}
```
**시험에서**: Base Case가 없거나 도달할 수 없으면 StackOverflowError. "이 재귀의 base case는?" 문제.

---

### Recursive Case (리커시브 케이스)
**한국어 뜻**: 자기 자신을 호출하는 부분. 문제를 더 작은 문제로 쪼개는 단계.
**비유**: "큰 문제를 작은 문제로 나눠서 넘기기". 5! = 5 × 4! 처럼.
**예시 코드**:
```java
public static int fibonacci(int n) {
    if (n <= 1) return n;                           // base case
    return fibonacci(n - 1) + fibonacci(n - 2);    // recursive case
}
```
**시험에서**: Recursive Case에서 문제가 base case에 가까워지는지 확인. 안 가까워지면 무한 재귀.

---

## 파일 입출력

---

### File (파일)
**한국어 뜻**: 컴퓨터에 저장된 데이터 묶음. java.io.File 클래스로 다룬다.
**비유**: 서랍에 넣어둔 서류. 이름(파일명)으로 찾아서 꺼내 읽을 수 있다.
**예시 코드**:
```java
import java.io.File;
File f = new File("data.txt");
System.out.println(f.exists());  // 파일이 존재하면 true
```
**시험에서**: AP CSA에서 직접 나오진 않지만, 실습에서 사용법을 알아두면 좋다.

---

### Scanner (스캐너)
**한국어 뜻**: 키보드 입력이나 파일에서 데이터를 읽어오는 클래스
**비유**: 바코드 스캐너처럼 데이터를 하나씩 읽어들이는 장치.
**예시 코드**:
```java
import java.util.Scanner;

// 키보드 입력
Scanner sc = new Scanner(System.in);
System.out.print("이름: ");
String name = sc.nextLine();

// 파일 입력
Scanner fileSc = new Scanner(new File("data.txt"));
while (fileSc.hasNext()) {
    System.out.println(fileSc.nextLine());
}
fileSc.close();
```
**시험에서**: AP 시험에서 직접 나오진 않지만, 랩(lab) 과제에서 자주 사용.

---

### throws (쓰로우즈)
**한국어 뜻**: 이 메서드에서 예외가 발생할 수 있음을 선언하는 키워드
**비유**: "이 작업은 위험할 수 있습니다" 경고 표시.
**예시 코드**:
```java
import java.io.IOException;

public static void readFile() throws IOException {
    Scanner sc = new Scanner(new File("data.txt"));
    // 파일이 없으면 IOException 발생 가능
}
```
**시험에서**: AP 시험에서 직접 출제되진 않지만, 파일 관련 코드 작성 시 필요.

---

### IOException (아이오 익셉션)
**한국어 뜻**: 입출력(파일 읽기/쓰기) 도중 발생하는 예외
**비유**: 서류를 꺼내려는데 서랍이 잠겨있는 상황.
**예시 코드**:
```java
import java.io.*;

public static void main(String[] args) throws IOException {
    Scanner sc = new Scanner(new File("nofile.txt"));
    // 파일이 없으면 FileNotFoundException (IOException의 하위 클래스)
}
```
**시험에서**: AP 시험에서 직접 출제되진 않음. 실습용으로 알아두자.

---

### hasNext() (해즈 넥스트)
**한국어 뜻**: Scanner에 읽을 데이터가 더 있으면 true 반환
**비유**: 뷔페에서 "다음 접시가 있나요?" 확인하는 것.
**예시 코드**:
```java
Scanner sc = new Scanner(new File("data.txt"));
while (sc.hasNext()) {           // 읽을 게 더 있는 동안
    System.out.println(sc.next()); // 한 단어씩 읽기
}
```
**시험에서**: 파일의 끝까지 읽을 때 while(hasNext()) 패턴 사용.

---

### nextInt() (넥스트 인트)
**한국어 뜻**: Scanner에서 다음 정수를 읽어오는 메서드
**비유**: 번호표 기계에서 다음 번호를 뽑는 것.
**예시 코드**:
```java
Scanner sc = new Scanner(System.in);
System.out.print("나이: ");
int age = sc.nextInt();  // 사용자가 입력한 정수를 읽음
```
**시험에서**: nextInt() 후에 nextLine()을 쓰면 빈 줄이 읽히는 버그가 있다. nextInt() 후 nextLine()을 한 번 더 호출해서 버리자.

---

### nextLine() (넥스트 라인)
**한국어 뜻**: Scanner에서 한 줄 전체를 문자열로 읽어오는 메서드
**비유**: 메모장의 한 줄을 통째로 읽는 것.
**예시 코드**:
```java
Scanner sc = new Scanner(System.in);
System.out.print("이름: ");
String name = sc.nextLine();  // 한 줄 전체를 읽음
```
**시험에서**: nextInt()와 nextLine()을 섞어 쓸 때 주의. 줄바꿈 문자 처리 이슈.

---

### split() (스플릿)
**한국어 뜻**: 문자열을 특정 구분자로 나눠서 배열로 반환하는 메서드
**비유**: 긴 소시지를 일정 간격으로 자르는 것.
**예시 코드**:
```java
String csv = "Kim,Lee,Park,Choi";
String[] names = csv.split(",");    // 쉼표로 나누기
// names = ["Kim", "Lee", "Park", "Choi"]
System.out.println(names.length);   // 4

String sentence = "Hello World Java";
String[] words = sentence.split(" ");  // 공백으로 나누기
// words = ["Hello", "World", "Java"]
```
**시험에서**: AP 시험에서 직접 나오진 않지만, 데이터 파싱 실습에서 유용.

---

### close() (클로즈)
**한국어 뜻**: Scanner나 파일 등의 리소스를 닫는 메서드. 사용이 끝나면 닫아야 한다.
**비유**: 다 읽은 책을 도서관에 반납하는 것.
**예시 코드**:
```java
Scanner sc = new Scanner(new File("data.txt"));
// 파일 읽기 작업...
sc.close();  // 다 쓰면 닫기!
```
**시험에서**: 리소스 누수 방지. close() 안 하면 메모리 낭비. AP 시험에서는 직접 나오진 않음.

---

## 기타 중요 용어

---

### Precondition (프리컨디션)
**한국어 뜻**: 메서드가 올바르게 동작하기 위해 호출 전에 만족해야 하는 조건
**비유**: "이 놀이기구는 키 120cm 이상만 탑승 가능." 탑승 전 조건.
**예시 코드**:
```java
/**
 * Precondition: n > 0 (n은 양수여야 함)
 */
public static double squareRoot(double n) {
    return Math.sqrt(n);
}
// squareRoot(-1)을 호출하면? → precondition 위반 (결과가 보장 안 됨)
```
**시험에서**: FRQ에서 "Precondition: ..."이 주어지면, 그 조건이 이미 만족된다고 가정하고 풀면 된다. 따로 검사할 필요 없음.

---

### Postcondition (포스트컨디션)
**한국어 뜻**: 메서드가 실행된 후에 보장되는 조건/결과
**비유**: "이 세탁기를 돌리면 빨래가 깨끗해집니다." 실행 후 보장되는 것.
**예시 코드**:
```java
/**
 * Precondition: arr is not null
 * Postcondition: returns the sum of all elements in arr
 */
public static int sum(int[] arr) {
    int total = 0;
    for (int n : arr) total += n;
    return total;
}
```
**시험에서**: Postcondition은 "이 메서드가 무엇을 보장하는가?"에 대한 답. 메서드의 역할을 이해하는 데 도움.

---

### Algorithmic Bias (알고리즈믹 바이어스)
**한국어 뜻**: 알고리즘이 특정 그룹에 불공평한 결과를 만들어내는 편향
**비유**: 채용 AI가 남성 이력서만 선호하게 학습된 것. 데이터나 설계의 편향이 결과에 반영됨.
**예시 코드**:
```java
// 코드 예시라기보다 개념 이해
// 예: 대출 심사 알고리즘이 특정 지역 주민에게 불리한 결과를 내는 경우
// 데이터가 편향되면 → 알고리즘도 편향됨
```
**시험에서**: AP CSA 시험의 사회적/윤리적 문제로 가끔 출제. 기술적 코드보다는 개념 이해.

---

### NullPointerException (널 포인터 익셉션)
**한국어 뜻**: null인 참조 변수에서 메서드를 호출하거나 필드에 접근할 때 발생하는 에러
**비유**: 주소가 "없음"인 편지를 배달하려는 것. 갈 곳이 없으니 에러.
**예시 코드**:
```java
String s = null;
s.length();          // NullPointerException!

int[] arr = null;
System.out.println(arr.length);  // NullPointerException!

ArrayList<String> list = null;
list.add("Hi");      // NullPointerException!
```
**시험에서**: 가장 흔한 런타임 에러. "이 코드에서 발생할 수 있는 에러는?" → null 체크 여부 확인.

---

### ArrayIndexOutOfBoundsException (어레이 인덱스 아웃 오브 바운즈 익셉션)
**한국어 뜻**: 배열의 유효한 인덱스 범위를 벗어났을 때 발생하는 에러
**비유**: 5층 건물에서 6층 버튼을 누르는 것. 없는 층이다.
**예시 코드**:
```java
int[] arr = {10, 20, 30};  // 인덱스 0, 1, 2만 유효
System.out.println(arr[3]);   // ArrayIndexOutOfBoundsException!
System.out.println(arr[-1]);  // ArrayIndexOutOfBoundsException!

for (int i = 0; i <= arr.length; i++) {  // <= 때문에 마지막에 에러!
    System.out.println(arr[i]);
}
```
**시험에서**: i <= arr.length (잘못) vs i < arr.length (올바름). Off-by-one 에러와 연결.

---

### ConcurrentModificationException (컨커런트 모디피케이션 익셉션)
**한국어 뜻**: 컬렉션을 순회하는 도중에 그 컬렉션을 수정할 때 발생하는 에러
**비유**: 달리는 기차에서 선로를 바꾸려는 것. 이동 중에 구조를 바꾸면 위험.
**예시 코드**:
```java
ArrayList<String> list = new ArrayList<String>();
list.add("A"); list.add("B"); list.add("C");

// for-each 루프 중 삭제 → ConcurrentModificationException!
for (String s : list) {
    if (s.equals("B")) {
        list.remove(s);  // 에러!
    }
}

// 해결법: 일반 for 루프 사용 (뒤에서부터)
for (int i = list.size() - 1; i >= 0; i--) {
    if (list.get(i).equals("B")) {
        list.remove(i);  // OK
    }
}
```
**시험에서**: for-each 루프 안에서 add/remove 하면 이 에러 발생. 일반 for 루프로 해결.

---

### StackOverflowError (스택 오버플로우 에러)
**한국어 뜻**: 재귀 호출이 너무 깊어서 메모리(스택)가 넘칠 때 발생하는 에러
**비유**: 접시를 무한히 쌓다가 탑이 무너지는 것. 호출할 때마다 접시(스택 프레임)가 쌓인다.
**예시 코드**:
```java
// base case 없는 재귀 → StackOverflowError!
public static int bad(int n) {
    return bad(n - 1);  // 멈추는 조건이 없음!
}

// base case에 도달 못 하는 재귀
public static int alsoBad(int n) {
    if (n == 0) return 0;
    return alsoBad(n + 1);  // n이 점점 커져서 0에 도달 못 함!
}
```
**시험에서**: "이 재귀 메서드의 문제점은?" → base case 없거나 도달 불가 → StackOverflowError.

---

## 부록: 핵심 비교표

| 구분 | 배열 (Array) | ArrayList |
|------|-------------|-----------|
| 크기 | 고정 | 가변 |
| 타입 | primitive + reference | reference만 (Wrapper 사용) |
| 길이 | `.length` (괄호X) | `.size()` (괄호O) |
| 접근 | `arr[i]` | `list.get(i)` |
| 수정 | `arr[i] = x` | `list.set(i, x)` |
| import | 불필요 | `java.util.ArrayList` 필요 |

---

| 구분 | == | .equals() |
|------|-----|-----------|
| Primitive | 값 비교 (정상) | 사용 불가 |
| Reference | 주소 비교 (위험!) | 내용 비교 (정상) |
| String | 주소 비교 (쓰지 말 것) | 내용 비교 (이것을 써야 함) |

---

| 에러 종류 | 발견 시점 | 예시 |
|-----------|----------|------|
| Syntax Error | 컴파일 시 | 세미콜론 누락, 괄호 짝 안 맞음 |
| Runtime Error | 실행 중 | NullPointerException, 0으로 나누기 |
| Logic Error | 테스트 시 | 의도와 다른 결과 (프로그램은 실행됨) |

---

| 정렬 알고리즘 | 시간 복잡도 | 특징 |
|-------------|-----------|------|
| Selection Sort | O(n^2) | 최솟값 찾아서 앞으로 |
| Insertion Sort | O(n^2) | 맞는 위치에 끼워넣기 |
| Merge Sort | O(n log n) | 반으로 나누고 합치기 (재귀) |

---

> 이 용어 사전은 AP Computer Science A의 전 범위를 다룹니다.  
> 시험 전에 **비유**로 개념을 떠올리고, **시험에서** 파트로 출제 유형을 확인하세요.
