# AP CSA 2025-26 Topical Practice (보강용 토픽별 고난도 세트)

> **기준 문서**: `/mnt/20t/study/AP_CSA/공식_시험범위_검증.md`
> **작성일**: 2026-04-18
> **용도**: LT1~LT10에서 0~1회만 출제된 토픽을 집중 보강
> **형식**: **MCQ 전용** (Section II FRQ 없음), 4지선다, Hard 위주

---

## 배경

LT1~LT10 토픽 커버리지 분석(에이전트 10개 병렬) 결과, 다음 CED 토픽들이 **0~1회만 출제**되어 보강 필요:

| 영역 | 토픽 | 갭 |
|---|---|---|
| 신규 | 4.6 Using Text Files (`File`, `Scanner`) | 0회 |
| 단골 | 4.7 Wrapper Classes (`parseInt`, `parseDouble`) | 0~1회 |
| 표준 | 4.14 Linear Search | 1회 |
| 표준 | 4.15 Selection / Insertion Sort | 1회 |
| 표준 | 4.17 Binary Search / Merge Sort | 1회 |
| 단골 | 3.7 Class Variables (`static`, `final`) | 1회 |
| 단골 | 3.8 Scope and Access | 0회 |
| 보장 | 3.2 Impact of Program Design (윤리) | 0회 |
| 명시 | 2.12 Informal Run-Time Analysis | 0회 |

---

## 구성 — 9개 세트, 약 70문항

| Set | 제목 | CED 토픽 | 문항 | 난이도 |
|-----|------|---------|------|--------|
| **TP1** | File I/O + Wrapper Classes | 4.6, 4.7 | 10 | Hard |
| **TP2** | Searching: Linear + Binary | 4.14, 4.17.B | 8 | Hard |
| **TP3** | Sorting: Selection + Insertion + Merge | 4.15, 4.17.C | 10 | Hard |
| **TP4** | Recursion 트레이싱 심화 | 4.16, 4.17 | 8 | Hard |
| **TP5** | Static, Final, Scope, this | 3.7, 3.8, 3.9 | 8 | Hard |
| **TP6** | Boolean 심화 + Run-Time Analysis | 2.5, 2.6, 2.12 | 8 | Hard |
| **TP7** | Math + Casting + Overflow | 1.5, 1.11 | 6 | Medium-Hard |
| **TP8** | Object References + Null + Aliasing | 1.12~1.14, 3.6 | 6 | Hard |
| **TP9** | Ethics & Impact of Computing | 3.2 | 6 | Easy-Medium |

**총 70문항.**

---

## 작업 우선순위

| 순서 | 세트 | 이유 |
|------|------|------|
| 1 | TP1 (File I/O + Wrapper) | 0회, 신규 토픽 |
| 2 | TP2 (Searching) | 매년 출제, 1회만 |
| 3 | TP3 (Sorting) | 매년 출제, 1회만 |
| 4 | TP5 (Static/Scope/this) | 단골 함정, 0~1회 |
| 5 | TP9 (Ethics) | 1-2문항 보장, 0회 |
| 6 | TP6 (Boolean+RTA) | RTA 0회 |
| 7 | TP4 (Recursion 심화) | 다양화 |
| 8 | TP7 (Math+Casting) | 보강 |
| 9 | TP8 (References) | 보강 |

---

## 출제 표준 (모든 세트 공통)

### IN-스코프 검증
1. **Java Quick Reference 메서드만 사용** (CED p.185-186)
   - String: length, substring(int,int), substring(int), indexOf, equals, compareTo, split
   - Integer: MIN_VALUE, MAX_VALUE, parseInt
   - Double: parseDouble
   - Math: abs(int/double), pow, sqrt, random
   - ArrayList: size, add(E), add(int,E), get, set, remove(int)
   - File: File(String)
   - Scanner: Scanner(File), nextInt, nextDouble, nextBoolean, nextLine, next, hasNext, close
   - Object: equals, toString

2. **EXCLUSION 절대 위반 금지**
   - 4.16: 재귀 코드 **작성** OUT (트레이싱만)
   - 1.4: `Scanner(System.in)` 키보드 입력 OUT
   - 1.6: prefix `++x`, `arr[x++]` OUT
   - 1.12: 상속(`extends`, `super`) OUT
   - 1.15: `toString` 오버라이드 작성 OUT
   - 2.6: `equals` 오버라이드 작성 OUT
   - 4.11: 비직사각형 2D 배열 OUT
   - 4.14: linear/binary 외 검색 OUT
   - 4.17: selection/insertion/merge 외 정렬 OUT (bubble OUT)
   - **Math.min/max/floor/ceil/round** Quick Reference에 없음 → OUT
   - **ArrayList.contains/clear/indexOf/isEmpty** Quick Reference에 없음 → OUT
   - **break/continue/switch/do-while/try-catch** CED 본문 등장 없음 → 출제 회피

### 형식
- 헤더: `[CED 토픽 X.X · Hard]` 명시
- 4 선택지 (A, B, C, D)
- 답안 분포: 세트 내 균형 (가능한 한 A:B:C:D 균등)
- 해설 형식 (LT8 스타일):
  - 📌 출제 의도 (1-2 문장)
  - 📎 CED 연계 (구체 토픽 번호 + 인용)
  - 핵심 개념 + 선행 지식
  - 코드 + 단계별 추적 표
  - 오답 분석 (4 행)
  - ⚠️ 함정 × 3
  - 💡 꿀팁 × 3

---

## 디렉토리 구조

```
07_topical_practice/
├── README.md                       (이 파일)
├── TP1_File_Wrapper.md
├── TP2_Searching.md
├── TP3_Sorting.md
├── TP4_Recursion_Advanced.md
├── TP5_Static_Scope_This.md
├── TP6_Boolean_RTA.md
├── TP7_Math_Casting.md
├── TP8_References_Null.md
├── TP9_Ethics_Impact.md
└── answers/
    ├── TP1_File_Wrapper_answers.md
    ├── TP2_Searching_answers.md
    ├── ... (각 세트 대응)
    └── TP9_Ethics_Impact_answers.md
```

---

## 변경 이력

| 날짜 | 변경 |
|------|------|
| 2026-04-18 | 폴더 신규 생성. 9개 세트 계획 수립. |
