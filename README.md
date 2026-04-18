# AP CSA 과외 자료 통합 안내서

> **기준**: AP Computer Science A 2025-26 CED (Effective Fall 2025)
> **마지막 업데이트**: 2026-04-08

---

## 이 자료는 누구를 위한 것인가?

| 대상 | 설명 |
|------|------|
| **교사** | AP CSA를 처음 가르치는 과외 교사 |
| **학생** | Java를 처음 배우는 고등학생 |
| **목표** | AP CSA 시험 5점 |

총 80여 개 파일(공식 문서 + 커리큘럼 + 기출 + 연습 + 레퍼런스 + 모의시험 + 레벨테스트 10회 + 토픽별 보강 9세트)로 구성되어 있습니다.
아래 순서대로 따라가면 됩니다.

> ✅ **2025-26 CED 준수**: 본 자료의 모든 코드·문제·해설은 AP CSA 2025-26 Java Quick Reference 등재 메서드만 사용하며, CED EXCLUSION(상속/break/continue/switch/charAt/toUpperCase/toLowerCase/contains/trim/Math.min/Math.max/hasNextInt/hasNextLine/Scanner(System.in)/toString-equals 오버라이드 작성/bubble sort 등)을 위반하지 않습니다. 권위 검증 문서는 `공식_시험범위_검증.md` 참조.

---

## 자료 전체 지도

### 1단계: 시작 전 (교사)

| 순서 | 파일 | 설명 |
|------|------|------|
| 1 | `03_practice/교사용_수업진행_가이드.md` | **이것만 읽으면 수업 가능** - 분 단위 수업 스크립트 |
| 2 | `03_practice/수업계획서_10회.md` | 10회 수업 전체 계획, 시간 배분, 숙제 |
| 3 | `00_official_docs/AP_CSA_CED_2025-26.pdf` | 공식 교육과정 (참고용) |
| 4 | `00_official_docs/AP_CSA_Course_at_a_Glance.pdf` | 과정 한눈에 보기 |

### 2단계: 시작 전 (학생)

| 파일 | 설명 |
|------|------|
| `03_practice/00_Java_환경설정_가이드.md` | Java + IDE 설치 (IntelliJ/VSCode) |
| `03_practice/00_사전진단_테스트.md` | 학생 수준 측정 (난이도/구간별 진단) |

### 3단계: 수업 (10회)

수업은 `03_practice/교사용_수업진행_가이드.md`의 분 단위 스크립트를 따라 진행합니다.

| 자료 종류 | 파일 | 용도 |
|-----------|------|------|
| 수업 스크립트 | `03_practice/교사용_수업진행_가이드.md` | 수업 중 실시간 참고 |
| 수업 계획 | `03_practice/수업계획서_10회.md` | 회차별 목표, 시간, 숙제 |
| 강의노트 | `03_practice/Unit1_강의노트.md` | Unit 1: 변수, 타입, 연산, String, Math |
| 강의노트 | `03_practice/Unit2_강의노트.md` | Unit 2: Boolean, if/else, 반복문 |
| 강의노트 | `03_practice/Unit3_강의노트.md` | Unit 3: 클래스, 객체, OOP |
| 강의노트 | `03_practice/Unit4_강의노트.md` | Unit 4: Array, ArrayList, 2D Array, 정렬, 재귀 |
| 코딩 실습 | `03_practice/코딩실습_과제.md` | 수업 중 실습 + 숙제용 코딩 과제 |
| Quick Ref | `03_practice/QuickReference_한국어해설.md` | Java Quick Reference 한국어 해설 |

### 4단계: 연습

| 자료 종류 | 파일 | 분량 |
|-----------|------|------|
| MCQ 연습 | `03_practice/MCQ_문제집.md` | 120문제 (Unit별) |
| 코드 분석 | `03_practice/코드트레이싱_워크시트.md` | 43문제 (출력 예측) |
| FRQ 풀이 | `03_practice/FRQ_풀이해설.md` | 2025 FRQ 풀이해설 |
| FRQ 기출 | `02_frq_archive/` | 2021~2025 기출문제 + 채점기준 + 모범답안 |

### 5단계: 시험 대비

| 자료 종류 | 파일 | 설명 |
|-----------|------|------|
| 레벨테스트 | `06_level_tests/LevelTest1~10.md` | 10회 누적 레벨테스트 (문제 + `answers/` + `questions/`) |
| 토픽별 보강 | `07_topical_practice/TP1~TP9.md` | 9세트, 각 ~10문제. 약점 토픽 집중 보강 |
| 모의시험 MCQ | `05_mock_exams/Set1~5_MCQ.md` | 5세트, 각 42문제 (실제 시험 동일) |
| 모의시험 FRQ | `05_mock_exams/Set1~5_FRQ.md` | 5세트, 각 4문제 (실제 시험 동일) |
| 점수 변환 | `05_mock_exams/점수변환표.md` | 채점 후 AP 점수 예측 |
| 5점 드릴 | `03_practice/5점_고급드릴.md` | 상위 난이도 문제 |
| 시험 전략 | `03_practice/시험전략_가이드.md` | 시간 관리, 찍기 전략, FRQ 부분점수 |

### 6단계: 시험 직전

| 파일 | 설명 |
|------|------|
| `04_reference/치트시트_전체요약.md` | 시험 전 최종 복습 (전 범위 1장 요약) |
| `04_reference/학습추적_오답노트.md` | 오답 기록 + 약점 분석 템플릿 |

---

## 상시 참고 자료

| 상황 | 파일 |
|------|------|
| 용어가 모르겠다 | `04_reference/Java_용어사전.md` (134개 용어) |
| 자주 하는 질문 | `04_reference/초보자_FAQ.md` (50개 Q&A) |
| 외부 학습 자료 추천 | `04_reference/학습자료_가이드.md` |
| Java Quick Reference 원본 | `00_official_docs/Java_Quick_Reference.pdf` |
| 교육과정 상세 | `00_official_docs/AP_CSA_CED_2025-26.pdf` |
| CSAwesome 교재 목차 | `01_curriculum/CSAwesome2_목차.md` |

---

## 회차별 사용 자료 맵

| 회차 | 주제 | CED 대응 | 사용 자료 |
|------|------|----------|-----------|
| **1회** | 변수, 타입, 출력, 연산 | Unit 1 (1.1~1.6) | Unit1 강의노트, 환경설정 가이드, 코딩실습 |
| **2회** | 메서드, Math, String | Unit 1 (1.7~1.15) | Unit1 강의노트, QuickReference, MCQ 문제집 |
| **3회** | Boolean, if/else, De Morgan | Unit 2 (2.1~2.6) | Unit2 강의노트, MCQ 문제집 |
| **4회** | while, for, 중첩루프 | Unit 2 (2.7~2.12) | Unit2 강의노트, 코드트레이싱 워크시트 |
| **5회** | 클래스, OOP, FRQ Q2 | Unit 3 (3.1~3.9) | Unit3 강의노트, FRQ 2024 기출 |
| **6회** | Array, 9가지 알고리즘 | Unit 4 (4.1~4.5) | Unit4 강의노트, MCQ 문제집, 코딩실습 |
| **7회** | ArrayList, FRQ Q3 | Unit 4 (4.6~4.10) | Unit4 강의노트, FRQ 2024 기출 |
| **8회** | 2D Array, 정렬, 재귀, FRQ Q4 | Unit 4 (4.11~4.17) | Unit4 강의노트, FRQ 2024 기출 |
| **9회** | FRQ 풀세트 실전 | 전체 | FRQ 2025 기출, 채점기준, FRQ 풀이해설 |
| **10회** | 모의시험 MCQ + 최종 리뷰 | 전체 | 모의시험 Set1, 시험전략 가이드, 치트시트 |

> 10회 수업 후 남은 모의시험(Set2~5)은 학생이 자율 연습용으로 풀고, `점수변환표.md`로 채점합니다.

---

## 추천 학습 루트 (자습용)

수업 없이 혼자 공부하는 경우:

1. `00_Java_환경설정_가이드.md`로 Java 설치
2. Unit1~4 강의노트를 순서대로 읽으며 코딩실습 병행
3. 각 Unit 끝나면 MCQ 문제집 해당 Unit 풀기
4. 코드트레이싱 워크시트 43문제 풀기
5. FRQ 풀이해설로 FRQ 유형 파악
6. 모의시험 5세트 풀기 (시간 재고, 점수변환표로 채점)
7. 약점 Unit 치트시트로 복습
8. 시험 전날: 치트시트 + Quick Reference 최종 확인

---

## 자료 품질 정보

- **전수 검증 완료**: MCQ 360문제 정답 확인, FRQ 채점기준 대조
- **CED 커버리지**: 53개 토픽 전체 대응 확인
- **기준**: AP CSA 2025-26 CED (Effective Fall 2025)
- **FRQ 기출**: 2021~2025 공식 문제 + 채점기준 + 2024-2025 모범답안 포함

---

## 폴더 구조

```
AP_CSA/
├── 00_official_docs/    ← College Board 공식 문서 (CED, Quick Reference)
├── 01_curriculum/       ← 교재 목차 (CSAwesome2)
├── 02_frq_archive/      ← FRQ 기출 2021-2025 (문제+채점기준+모범답안)
├── 03_practice/         ← 수업 자료 전체 (강의노트, 실습, MCQ, FRQ, 가이드)
├── 04_reference/        ← 참고 자료 (치트시트, 용어사전, FAQ)
├── 05_mock_exams/       ← 모의시험 5세트 + 점수변환표
├── 06_level_tests/      ← 누적 레벨테스트 10회 (문제 + answers/ + questions/)
├── 07_topical_practice/ ← 토픽별 보강 9세트 (약점 집중)
├── 공식_시험범위_검증.md ← 권위 검증 문서 (CED/QR/EXCLUSION)
└── 출제기준서.md         ← 본 자료 출제 기준
```
