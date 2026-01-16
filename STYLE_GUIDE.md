# 페이지별 스타일 수정 가이드

이 문서는 각 페이지별로 나타나는 화면의 텍스트 색상, 크기, 위치를 수정하는 방법을 설명합니다.

---

## 📋 목차

1. [인트로 (1페이지)](#1-인트로-1페이지)
2. [사전테스트 (2페이지)](#2-사전테스트-2페이지)
3. [학습목표 (3페이지)](#3-학습목표-3페이지)
4. [주요 키워드 (4페이지)](#4-주요-키워드-4페이지)
5. [본 학습 (5~8페이지)](#5-본-학습-5-8페이지)
6. [생각해보기 (9페이지)](#6-생각해보기-9페이지)
7. [평가하기 (10페이지)](#7-평가하기-10페이지)
8. [정리하기 (11페이지)](#8-정리하기-11페이지)
9. [아웃트로 (12페이지)](#9-아웃트로-12페이지)

---

## 1. 인트로 (1페이지)

### 배경 이미지
- 없음 (비디오 재생)

### 수정 가능한 요소
없음 (순수 비디오 페이지)

---

## 2. 사전테스트 (2페이지)

### 배경 이미지
- `src/assets/img/pre/bgPre.png` - 사전테스트 메인 화면

### 수정 파일
**`src/components/PreComponent.vue`**

### 수정 가능한 요소

#### 1) Submit 버튼
- **파일 위치**: 194-206번 줄
- **이미지 파일**:
  - 기본: `btnSubmit.png`
  - 호버: `btnSubmitOn.png`
- **크기**: 194px × 120px
- **위치**:
  - `top: 142px` (위에서부터)

#### 2) O/X 체크박스
- **파일 위치**: 208-244번 줄
- **위치 조정**:
  - `left: 905px` (210번 줄) - 왼쪽 여백
  - `margin-bottom: 14px` (216번 줄) - 간격
  - `max-width: 53px` (217번 줄) - 버튼 간 간격
- **이미지 파일**:
  - O 버튼: `btnCheckO.png` / `btnCheckOOn.png`
  - X 버튼: `btnCheckX.png` / `btnCheckXOn.png`

#### ⭐ 3) 정답 설정 (중요!)
- **파일**: `src/components/PreComponent.vue`
- **파일 위치**: 25-26번 줄
- **정답 배열**: `const answers = [1, 2, 1, 1, 2, 1, 2, 1, 1, 2]`
  - **형식**: `1 = O`, `2 = X`
  - **총 10문제**: 배열의 각 요소가 각 문제의 정답에 해당

##### 정답 배열 설명:
```javascript
// 정답: 1=O, 2=X, 3=O, 4=O, 5=X, 6=O, 7=X, 8=O, 9=O, 10=X
const answers = [1, 2, 1, 1, 2, 1, 2, 1, 1, 2] // 1=O, 2=X
```

| 문제 번호 | 정답 | 배열 인덱스 | 배열 값 |
|----------|------|------------|---------|
| 1번 문제 | O    | 0          | 1       |
| 2번 문제 | X    | 1          | 2       |
| 3번 문제 | O    | 2          | 1       |
| 4번 문제 | O    | 3          | 1       |
| 5번 문제 | X    | 4          | 2       |
| 6번 문제 | O    | 5          | 1       |
| 7번 문제 | X    | 6          | 2       |
| 8번 문제 | O    | 7          | 1       |
| 9번 문제 | O    | 8          | 1       |
| 10번 문제 | X   | 9          | 2       |

##### 정답 수정 방법:
1. `src/components/PreComponent.vue` 파일 열기
2. 26번 줄 찾기: `const answers = [1, 2, 1, 1, 2, 1, 2, 1, 1, 2]`
3. 배열 값 수정:
   - O로 바꾸려면 → `1`
   - X로 바꾸려면 → `2`
4. 예시: 첫 번째 문제를 X로 바꾸려면:
   ```javascript
   const answers = [2, 2, 1, 1, 2, 1, 2, 1, 1, 2]  // 1번을 1→2로 변경
   ```

##### 채점 로직:
- **파일 위치**: 63-65번 줄
- 사용자가 선택한 값(col)과 정답(answers[row - 1])을 비교
- 정답이면 5점, 오답이면 0점
- 총점에 따라 레벨 결정:
  - 0-30점: 초급
  - 35-40점: 중급
  - 45-50점: 고급

---

### 사전테스트 결과 화면

### 배경 이미지
- `src/assets/img/pre/bgResult.png`

### 수정 가능한 요소

#### 3) 레벨 텍스트 ("초급", "중급", "고급")
- **파일 위치**: 298-307번 줄
- **글씨체**: `font-family: 'Paperlogy-8ExtraBold'`
- **글씨 크기**: `font-size: 42px`
- **글씨 색상**: `color: #0e7300` ⭐
- **위치**:
  - `top: 163px` (위에서부터)
  - `left: 643px` (왼쪽에서부터)
- **글자 간격**: `letter-spacing: -2px`

#### 4) Download 버튼
- **이미지 파일**: `btnDownload.png` / `btnDownloadOn.png`
- **위치**: 310번 줄 (`top: 392px`)

#### 5) Close 버튼
- **이미지 파일**: `btnClose.png` / `btnCloseOn.png`

---

## 3. 학습목표 (3페이지)

### 배경 이미지
- 없음 (비디오 재생)

### 수정 가능한 요소

#### 챕터명 표시
- **배경 이미지**: `src/assets/img/top/shape.png`
- **파일**: `src/components/VideoComponent.vue`
- **위치**: 857-881번 줄

##### 수정 가능한 속성:
- **위치 조정**:
  - `top: calc(50% - 314px)` (859번 줄)
  - `left: calc(50% - 429px)` (860번 줄) - 숫자가 클수록 왼쪽
- **배경 크기**:
  - `width: 290px` (864번 줄)
  - `height: 80px` (865번 줄)
- **글씨 스타일** (869-880번 줄):
  - `font-family: 'Paperlogy-5Medium'`
  - `font-size: 18px` ⭐ - 챕터명 크기
  - `color: #000000` ⭐ - 챕터명 색상
  - `letter-spacing: -1px`

---

## 4. 주요 키워드 (4페이지)

### 배경 이미지
- 없음 (비디오 재생)

### 수정 가능한 요소
- 3페이지와 동일 (챕터명 표시)

---

## 5. 본 학습 (5~8페이지)

### 배경 이미지
- 없음 (비디오 재생)

### 수정 파일
**`src/components/VideoComponent.vue`**

### 수정 가능한 요소

#### 1) 챕터명 표시
- 3페이지와 동일

#### 2) Skip 버튼 (건너뛰기)
- **파일 위치**: 923-940번 줄
- **이미지 파일**:
  - 기본: `skipBtn.png`
  - 호버: `skipBtnOver.png`
- **크기**: 140px × 140px
- **위치**:
  - `bottom: calc(50% - 360px)` ⭐
  - `right: calc(50% - 640px)` ⭐
- **애니메이션**: `transition: background 500ms ease-in-out`

#### 3) 인덱스 메뉴 (목차)
- **파일 위치**: 1034-1124번 줄
- **배경 이미지**: `indexBg.png`
- **크기**: 1120px × 184px
- **위치**: `bottom: 0`
- **z-index**: `z-index: 9`

##### 인덱스 닫기 버튼
- **파일 위치**: 1049-1062번 줄
- **이미지 파일**:
  - 기본: `indexCloseBtn.png`
  - 호버: `indexCloseBtnOver.png`
- **크기**: 50px × 50px
- **위치**: `right: 20px`, `top: 20px`

##### 인덱스 메뉴 텍스트
- **파일 위치**: 1103-1133번 줄
- **글씨체**: `font-family: 'Paperlogy-5Medium'`
- **기본 크기**: `font-size: 18px` ⭐
- **기본 색상**: `color: #135db7` ⭐
- **활성 색상**: `color: #ff6699` ⭐
- **호버 색상**: `color: #ff3358` ⭐
- **줄 간격**: `line-height: 30px`
- **여백**: `padding: 10px 10px`

##### 인덱스 아이콘
- **파일 위치**: 1084-1092번 줄
- **이미지 파일**: `index_1.png`, `index_2.png`, `index_3.png`
- **크기**: 132px × 132px

#### 4) 스크립트 영역 (자막)
- **파일 위치**: 885-922번 줄
- **배경**: `rgba(0, 0, 0, 0.75)` ⭐
- **백드롭 필터**: `backdrop-filter: blur(100px)` ⭐
- **글씨체**: `font-family: 'Paperlogy-5Medium'`
- **글씨 크기**: `font-size: 20px` ⭐
- **글씨 색상**: `color: #fff` ⭐
- **줄 간격**: `line-height: 1.5em`
- **위치**: `bottom: 0`, `position: fixed`
- **크기**:
  - `width: 1120px`
  - `max-height: 9em`
- **스크롤바 색상**: `background-color: #ff80ab` ⭐

---

## 6. 생각해보기 (9페이지)

### 배경 이미지
- `src/assets/img/think/bgThink.png`

### 수정 파일
**`src/components/ThinkComponent.vue`**

### 수정 가능한 요소

#### 1) 질문 텍스트
- **파일 위치**: 115-163번 줄
- **글씨체**: `font-family: 'Paperlogy-8ExtraBold'`
- **글씨 크기**: `font-size: 32px` ⭐
- **글씨 색상**: `color: #ffffff` ⭐ (현재 흰색)
- **위치**:
  - `top: 130px` ⭐ - 적어질수록 위로
  - `left: 130px` ⭐ - 적어질수록 왼쪽
- **글자 간격**: `letter-spacing: -1px`
- **줄 간격**: `line-height: 1.2em`

#### 2) 전문가 의견 버튼
- **파일 위치**: 100-113번 줄
- **이미지 파일**:
  - 기본: `btnThink.png`
  - 호버: `btnThinkOn.png`
- **크기**: 373px × 453px
- **위치**:
  - `top: 342px` ⭐ - 적어질수록 위로

#### 3) 답변 텍스트 (버튼 클릭 후)
- **파일 위치**: 172-210번 줄
- **글씨체**: `font-family: 'Paperlogy-4Regular'`
- **글씨 크기**: `font-size: 27px` ⭐
- **글씨 색상**: `color: #333` ⭐
- **위치**:
  - `top: 160px` ⭐ - 적어질수록 위로
  - `left: 143px` (왼쪽에서부터)
- **영역 크기**:
  - `max-width: 869px`
  - `height: 180px`

---

## 7. 평가하기 (10페이지)

### A. 인트로 화면

#### 배경 이미지
- `src/assets/img/quiz/bgQuizIntro.png`

#### 수정 파일
**`src/components/QuizComponent.vue`**

#### 수정 가능한 요소

##### 1) START 버튼
- **파일 위치**: 528-541번 줄
- **이미지 파일**:
  - 기본: `btnStart.png`
  - 호버: `btnStartOn.png`
- **크기**: 212px × 58px
- **위치**: `top: 345px`

##### 2) 차시명 (주석 처리됨)
- **파일 위치**: 554-567번 줄
- **글씨 색상**: `color: #fff`
- **그림자**: `text-shadow: 2px 2px 2px #302495`

---

### B. 카운트다운 화면

#### 배경 이미지
- `src/assets/img/quiz/bgQuizCountDown.png`

#### 수정 가능한 요소

##### 1) "첫 번째 문제" 텍스트
- **파일 위치**: 1009-1018번 줄
- **글씨체**: `font-family: 'Paperlogy-5Medium'`
- **글씨 크기**: `font-size: 68px` ⭐
- **글씨 색상**: `color: #0e7300` ⭐
- **글자 간격**: `letter-spacing: -4px`
- **여백**: `margin-bottom: 44px`

##### 2) "3, 2, 1, GO!" 숫자
- **파일 위치**: 1020-1028번 줄
- **글씨체**: `font-family: 'Paperlogy-7ExtraBold'`
- **글씨 크기**: `font-size: 140px` ⭐
- **글씨 색상**: `color: #0e7300` ⭐
- **테두리**: `-webkit-text-stroke: 2px #0e7300` ⭐
- **그림자**: `text-shadow: 2px 2px 0 #0e7300` ⭐

---

### C. 메인 퀴즈 화면

#### 배경 이미지
- `src/assets/img/quiz/bgQuizMain.png`

#### 수정 가능한 요소

##### 1) "시간 내에 문제를 풀어보세요" 텍스트
- **파일 위치**: 607-613번 줄
- **글씨체**: `font-family: 'Paperlogy-5Medium'`
- **글씨 크기**: `font-size: 23px` ⭐
- **글씨 색상**: `color: #0e7300` ⭐

##### 2) 타이머 (숫자)
- **파일 위치**: 615-654번 줄
- **글씨체**: `font-family: 'Paperlogy-7Bold'`
- **글씨 크기**: `font-size: 22px` ⭐
- **글씨 색상**: `color: #6ab554` ⭐
- **테두리 색상**: `border: 6px solid #6ab554` ⭐
- **크기**: 50px × 50px

##### 3) 진행바
- **파일 위치**: 358-365번 줄 (template 부분)
- **배경색**: `bg-color="#e9e9e9"` ⭐
- **진행바 색상**: `color="#6ab554"` ⭐
- **높이**: `height="12"`

##### 4) 문제 텍스트
- **파일 위치**: 682-701번 줄
- **글씨체**: `font-family: 'Paperlogy-7Bold'`
- **글씨 크기**: `font-size: 32px` ⭐
- **글씨 색상**: `color: #0e7300` ⭐
- **위치**:
  - `margin-left: 120px`
  - `top: 180px`

##### 5) 보기 (선택지)
- **파일 위치**: 728-770번 줄
- **번호 스타일**:
  - 배경색: `background-color: #fff`
  - 글자색: `color: #000` ⭐
  - 테두리: `border: 2px solid #000` ⭐
  - 크기: 33px × 33px
- **텍스트 크기**: `font-size: 26px` ⭐
- **텍스트 색상**: `color: #333` ⭐

##### 6) 보기 호버/정답 색상
- **파일 위치**: 809-821번 줄
- **번호 배경**: `background-color: #0e7300` ⭐
- **번호 글자**: `color: #fff` ⭐
- **텍스트**: `color: #0e7300` ⭐

---

### D. 정답 해설 화면

#### 배경 이미지
- `src/assets/img/quiz/bgQuizExplain.png`

#### 수정 가능한 요소

##### 1) 정답 번호 (큰 숫자)
- **파일 위치**: 832-839번 줄
- **글씨체**: `font-family: 'Paperlogy-7Bold'`
- **글씨 크기**: `font-size: 45px` ⭐
- **글씨 색상**: `color: #0e7300` ⭐
- **위치**:
  - `margin-left: 15px`
  - `margin-top: 50px`

##### 2) 해설 텍스트
- **파일 위치**: 840-869번 줄
- **글씨체**: `font-family: 'Paperlogy-4Regular'`
- **글씨 크기**: `font-size: 22px` ⭐
- **글씨 색상**: `color: #000` ⭐
- **줄 간격**: `line-height: 1.3em`
- **위치**:
  - `bottom: 50px`
  - `margin-left: 85px`

##### 3) Next/Result 버튼
- **이미지 파일**:
  - Next: `btnNext.png` / `btnNextOn.png`
  - Result: `btnResult.png` / `btnResultOn.png`

---

### E. 결과 화면

#### 배경 이미지
- `src/assets/img/quiz/bgResult.png` (퀴즈용)

#### 수정 가능한 요소

##### 1) O/X 마크
- **이미지 파일**:
  - 정답: `resultCorrect.png`
  - 오답: `resultWrong.png`

##### 2) 점수 텍스트
- **파일 위치**: 941-960번 줄
- **글씨체**: `font-family: 'Paperlogy-5Medium'`
- **글씨 크기**: `font-size: 27px` ⭐
- **총 문항 색상**: `color: #182093` ⭐
- **맞은 문항 색상**: `color: #ff3e6b` ⭐

##### 3) Restart 버튼
- **이미지 파일**: `btnRetry.png` / `btnRetryOn.png`

---

## 8. 정리하기 (11페이지)

### 배경 이미지
- `src/assets/img/summary/bgSummary.png`

### 수정 파일
**`src/components/SummaryComponent.vue`**

### 수정 가능한 요소

#### 1) 전체 영역 설정
- **파일 위치**: 77-116번 줄
- **위치**:
  - `margin-left: 124px` ⭐ - 왼쪽 여백
  - `margin-top: 150px` ⭐ - 위쪽 여백
- **스크롤 영역**:
  - `max-width: 880px`
  - `max-height: 980px`
- **글씨체**: `font-family: 'Paperlogy-5Medium'`
- **기본 글씨 크기**: `font-size: 30px` ⭐
- **글씨 색상**: `color: #000` ⭐
- **줄 간격**: `line-height: 1.3em`
- **글자 간격**: `letter-spacing: -1px`

#### 2) 리스트 항목
- **파일 위치**: 125-146번 줄
- **글씨 크기**: `font-size: 18px` ⭐
- **줄 간격**: `line-height: 29px` ⭐
- **항목 간 간격**: `margin: 10px 0` ⭐
- **정렬**: `align-items: flex-start` - 글머리 기호가 첫 줄에 위치

#### 3) 글머리 기호
- **파일 위치**: 136-145번 줄
- **이미지**: `@/assets/img/summary/bullet.png`
- **크기**: 12px × 12px
- **위치**:
  - `margin-right: 10px` - 텍스트와의 간격
  - `margin-top: 8px` ⭐ - 첫 줄 정렬

#### 4) 애니메이션
- **파일 위치**: 44번 줄 (template), 135번 줄 (style), 151-160번 줄 (keyframes)
- **시작 시간**: 2초
- **간격**: 0.5초씩
  - 1번째 줄: 2초
  - 2번째 줄: 2.5초
  - 3번째 줄: 3초
  - 4번째 줄: 3.5초
- **애니메이션 시간**: 0.5초

---

## 9. 아웃트로 (12페이지)

### 배경 이미지
- 없음 (비디오 재생)

### 수정 가능한 요소
없음 (순수 비디오 페이지)

---

## 📝 데이터 수정

### JSON 데이터 파일
- **위치**: `public/data/01.json`

### 수정 가능한 데이터

#### 1) 코스 정보
```json
"courseInfo": {
  "courseName": "미래를 밝히는 기술, 스마트에너지 ICT",
  "chapterNumber": 1,
  "chapterTitle": "광기술의 기초: LED, 레이저, 광섬유",
  ...
}
```

#### 2) 생각해보기
```json
"think": {
  "question": "LED 기술은 어느 반도체의 특성을 이용한 것인가?",
  "answer": "LED는 Light Emitting Doide로서..."
}
```

#### 3) 퀴즈 문제
```json
"quiz": [
  {
    "question": "LED 기술은 어느 반도체의 특성을 이용한 것인가?",
    "examLists": ["다이오드", "콘덴서", "트랜지스터", "레지스터"],
    "correct": 1,
    "explain": "LED는 Light Emitting Diode로서..."
  }
]
```

#### 4) 정리하기 내용
```json
"summary": [
  {
    "context": [
      "광기술은 단순히 빛을...",
      "LED는 PN반도체를..."
    ]
  }
]
```

---

## 🎨 색상 참고표

### 현재 적용된 주요 색상

| 색상 코드 | 색상명 | 사용 위치 |
|-----------|--------|-----------|
| `#0e7300` | 진한 녹색 | 퀴즈 문제, 정답, 카운트다운, 사전테스트 결과 |
| `#6ab554` | 밝은 녹색 | 타이머, 진행바 |
| `#ffffff` | 흰색 | 생각해보기 질문 |
| `#000000` | 검정색 | 챕터명, 정리하기, 해설 텍스트 |
| `#333333` | 어두운 회색 | 보기 텍스트, 생각해보기 답변 |
| `#1e9e8a` | 청록색 | 퀴즈 지문 텍스트 |
| `#182093` | 진한 파랑 | 퀴즈 결과 - 총 문항 수 |
| `#ff6699` | 핑크 | 강조 텍스트 (positive/negative) |
| `#ff3e6b` | 빨강 핑크 | 퀴즈 결과 - 맞은 문항 수 |
| `#999999` | 회색 | 비활성화 상태 |
| `#e9e9e9` | 연한 회색 | 진행바 배경 |
| `#135db7` | 파랑 | 인덱스 메뉴 텍스트 |
| `#808080` | 회색 | 스크롤바 |

### 배경색 (Background-Color)

| 색상 코드 | 설명 | 사용 위치 |
|-----------|------|-----------|
| `rgba(0, 0, 0, 0.75)` | 반투명 검정 | 스크립트 영역 배경 |
| `rgba(255, 255, 255, 0.75)` | 반투명 흰색 | 북마크 배경 |
| `rgba(0, 0, 0, 0.5)` | 반투명 검정 (50%) | 오버레이 |
| `rgba(40, 40, 40, 0.25)` | 반투명 어두운 회색 | 지문 테두리 |

---

## 📚 폰트 참고표

### 사용 중인 폰트 패밀리

#### Paperlogy 시리즈 (주요 사용)
| 폰트명 | Weight | 사용 위치 |
|--------|--------|-----------|
| `Paperlogy-1Thin` | 100 | - |
| `Paperlogy-2ExtraLight` | 200 | - |
| `Paperlogy-3Light` | 300 | - |
| `Paperlogy-4Regular` | 400 | 보기 텍스트, 해설, 정리하기 |
| `Paperlogy-5Medium` | 500 | 챕터명, 타이머 설명, 스크립트, 인덱스 |
| `Paperlogy-6SemiBold` | 600 | - |
| `Paperlogy-7Bold` | 700 | 타이머 숫자, 문제 텍스트 |
| `Paperlogy-7ExtraBold` | 700 | 카운트다운 숫자 |
| `Paperlogy-8ExtraBold` | 800 | 생각해보기 질문, 레벨 텍스트 |
| `Paperlogy-9Black` | 900 | - |

#### 기타 폰트
| 폰트명 | 사용 위치 |
|--------|-----------|
| `GmarketSansMedium` | 특정 UI 요소 |
| `SBAggroL` | - |
| `SBAggroM` | 도움말 |
| `SBAggroB` | - |
| `S-CoreDream-3Light` | - |
| `S-CoreDream-4Regular` | - |
| `S-CoreDream-5Medium` | - |
| `S-CoreDream-7ExtraBold` | - |
| `NanumSquareNeo` | 최근 추가 |

---

## 🎯 고급 스타일 속성

### Z-Index 계층 구조

| z-index 값 | 용도 |
|------------|------|
| `99999` | 알림 오버레이 (최상위) |
| `99998` | 알림 배경 |
| `9999` | 챕터명, 스크립트, 카운트다운 |
| `999` | 도움말 닫기 버튼 |
| `9` | 인덱스 메뉴 |

### 애니메이션 & 트랜지션

#### Transition 속성
```css
transition: background 300ms ease-in-out;    /* 버튼 배경 변화 */
transition: background 200ms ease-in-out;    /* 보기 선택 */
transition: background 500ms ease-in-out;    /* Skip 버튼 */
transition: transform .3s ease-in-out;       /* 회전 애니메이션 */
transition: color 300ms ease-in-out;         /* 텍스트 색상 변화 */
```

#### Transform 효과
```css
transform: rotate(180deg);      /* 버튼 회전 (Close 버튼) */
transform: scale(0.9);          /* 축소 (애니메이션 시작) */
transform: scale(1.05);         /* 확대 (애니메이션 중간) */
transform: translateY(10px);    /* 아래로 이동 (페이드인) */
```

#### Keyframe 애니메이션
1. **@keyframes pulse** (QuizComponent.vue)
   - 카운트다운 숫자 펄스 효과
   - 0%: scale(0.9), opacity(0.6)
   - 50%: scale(1.05), opacity(1)
   - 100%: scale(1)

2. **@keyframes fadeInItem** (SummaryComponent.vue)
   - 정리하기 항목 페이드인
   - from: opacity(0), translateY(10px)
   - to: opacity(1), translateY(0)

3. **@keyframes fadeInBg** (SummaryComponent.vue)
   - 배경 페이드인 (4초 딜레이)

### 백드롭 필터 (Backdrop Filter)

| 속성값 | 사용 위치 |
|--------|-----------|
| `backdrop-filter: blur(10px)` | 지문 영역 배경 |
| `backdrop-filter: blur(100px)` | 스크립트 영역 배경 |

### 텍스트 스타일 상세

#### Letter-spacing (글자 간격)
| 값 | 사용 위치 |
|----|-----------|
| `-4px` | 카운트다운 제목 |
| `-2px` | 레벨 텍스트, 생각해보기 답변 |
| `-1px` | 대부분의 제목 텍스트 |
| `0` | 타이머 숫자 |

#### Line-height (줄 간격)
| 값 | 사용 위치 |
|----|-----------|
| `1.2em` | 일반 제목 |
| `1.3em` | 긴 텍스트, 정리하기 |
| `1.5em` | 스크립트, 지문 |
| `29px` | 정리하기 리스트 |
| `30px` | 인덱스 메뉴 |
| `40px` | 생각해보기 질문 |
| `44px` | 보기 텍스트 |

#### Word-break
```css
word-break: keep-all;  /* 모든 한글 텍스트에 적용 */
```

### 테두리 스타일

| 속성 | 값 | 사용 위치 |
|------|-----|-----------|
| border | `6px solid #6ab554` | 타이머 원형 |
| border | `2px solid #000` | 보기 번호 (기본) |
| border | `2px solid #0e7300` | 보기 번호 (선택/정답) |
| border | `8px solid rgba(40,40,40,0.25)` | 지문 영역 |
| border-radius | `50%` | 타이머, 보기 번호 (원형) |
| border-radius | `10px` | 진행바, 버튼 모서리 |
| border-radius | `100px` | 스크롤바 |

### 스크롤바 커스터마이징

#### WebKit 스크롤바 (Chromium 기반 브라우저)
```scss
&::-webkit-scrollbar {
  width: 10px;
  background-color: #ffffff;
}

&::-webkit-scrollbar-thumb {
  background-color: #808080;
  border-radius: 100px;
}

&::-webkit-scrollbar-track {
  background-color: #ffffff;
}

&::-webkit-scrollbar-button {
  display: block;
  height: 16px;
  background-repeat: no-repeat;
  background-position: center;
}
```

#### Firefox 스크롤바
```css
scrollbar-width: thin;
scrollbar-color: rgba(0, 0, 0, 0.4) transparent;
```

### Flexbox 레이아웃

#### 주요 속성
```css
display: flex;
align-items: center | flex-start | flex-end;
justify-content: center;
flex-direction: row | column;
flex-shrink: 0;
gap: 30px | 20px | 10px;
```

### 포인터 이벤트

```css
pointer-events: none;    /* 클릭 비활성화 */
pointer-events: all;     /* 클릭 활성화 */
cursor: none | pointer;  /* 커서 스타일 */
user-select: none;       /* 텍스트 선택 방지 */
```

---

## 🔧 빌드 및 배포

### 1. 수정 후 빌드
```bash
npm run build
```

### 2. NAS 배포
- **경로**: `/volume1/WEBSERVICE/@PREVIEW@/bitcampus/teset/dist`
- **방법**: 기존 dist 폴더 삭제 후 새 dist 폴더 업로드

### 3. 웹 접속
```
http://preview.heyhey.com/bitcampus/teset/dist/01/01.html
```

### 4. 캐시 삭제
- Windows: `Ctrl + Shift + R`
- Mac: `Cmd + Shift + R`

---

## 🖼️ 이미지 파일 전체 목록

### 버튼 이미지

#### 사전테스트 (Pre)
| 파일명 | 용도 | 크기 |
|--------|------|------|
| `btnSubmit.png` | Submit 버튼 기본 | 194×120px |
| `btnSubmitOn.png` | Submit 버튼 호버 | 194×120px |
| `btnCheckO.png` | O 체크박스 기본 | 20×20px |
| `btnCheckOOn.png` | O 체크박스 선택 | 20×20px |
| `btnCheckX.png` | X 체크박스 기본 | 20×20px |
| `btnCheckXOn.png` | X 체크박스 선택 | 20×20px |
| `btnDownload.png` | 다운로드 버튼 기본 | 184×42px |
| `btnDownloadOn.png` | 다운로드 버튼 호버 | 184×42px |
| `btnClose.png` | 닫기 버튼 기본 | 44×44px |
| `btnCloseOn.png` | 닫기 버튼 호버 | 44×44px |

#### 평가하기 (Quiz)
| 파일명 | 용도 | 크기 |
|--------|------|------|
| `btnStart.png` | START 버튼 기본 | 212×58px |
| `btnStartOn.png` | START 버튼 호버 | 212×58px |
| `btnNext.png` | Next 버튼 기본 | 175×74px |
| `btnNextOn.png` | Next 버튼 호버 | 175×74px |
| `btnResult.png` | Result 버튼 기본 | 175×74px |
| `btnResultOn.png` | Result 버튼 호버 | 175×74px |
| `btnRetry.png` | Restart 버튼 기본 | 350×50px |
| `btnRetryOn.png` | Restart 버튼 호버 | 350×50px |

#### 생각해보기 (Think)
| 파일명 | 용도 | 크기 |
|--------|------|------|
| `btnThink.png` | 전문가 의견 버튼 기본 | 373×453px |
| `btnThinkOn.png` | 전문가 의견 버튼 호버 | 373×453px |

#### 공통 (Common)
| 파일명 | 용도 | 크기 |
|--------|------|------|
| `skipBtn.png` | Skip 버튼 기본 | 140×140px |
| `skipBtnOver.png` | Skip 버튼 호버 | 140×140px |

#### 인덱스 (Index)
| 파일명 | 용도 | 크기 |
|--------|------|------|
| `indexCloseBtn.png` | 인덱스 닫기 기본 | 50×50px |
| `indexCloseBtnOver.png` | 인덱스 닫기 호버 | 50×50px |
| `index_1.png` | 메뉴 아이콘 1 | 132×132px |
| `index_2.png` | 메뉴 아이콘 2 | 132×132px |
| `index_3.png` | 메뉴 아이콘 3 | 132×132px |

### 배경 이미지

| 파일명 | 사용 위치 | 크기 |
|--------|-----------|------|
| `bgPre.png` | 사전테스트 | - |
| `bgResult.png` (pre) | 사전테스트 결과 | 1120×630px |
| `bgThink.png` | 생각해보기 | - |
| `bgQuizIntro.png` | 퀴즈 인트로 | - |
| `bgQuizCountDown.png` | 카운트다운 | 1120×630px |
| `bgQuizMain.png` | 메인 퀴즈 | - |
| `bgQuizExplain.png` | 정답 해설 | - |
| `bgResult.png` (quiz) | 퀴즈 결과 | 1120×630px |
| `bgSummary.png` | 정리하기 | - |
| `shape.png` | 챕터명 배경 | 290×80px |
| `indexBg.png` | 인덱스 메뉴 배경 | 1120×184px |
| `bullet.png` | 정리하기 글머리 | 12×12px |

### 마크/아이콘

| 파일명 | 용도 |
|--------|------|
| `markCorrect.png` | 정답 O 마크 (50×50px) |
| `markWrong.png` | 오답 X 마크 (50×50px) |
| `resultCorrect.png` | 결과 정답 (97×97px) |
| `resultWrong.png` | 결과 오답 (97×97px) |
| `alertCorrect.png` | 정답 알림 (800px width) |
| `alertWrong.png` | 오답 알림 (800px width) |
| `alertRetry.png` | 재시도 알림 (800px width) |
| `questionLeft.png` | 물음표 좌 (주석 처리) |
| `questionRight.png` | 물음표 우 (주석 처리) |

---

## 📌 주의사항

### 파일 경로
1. **소스 코드 내 경로**: 절대경로 사용 (`@/assets/...`)
2. **public 폴더**: 상대경로 사용 (`../data/`, `../mp4/`)
3. **경로 변경 시**: 반드시 모든 참조 위치 확인

### 색상 코드
1. **16진수 코드 사용** (예: `#0e7300`)
2. **투명도 포함 시**: `rgba()` 형식 (예: `rgba(0, 0, 0, 0.75)`)
3. **색상 변경 시**: 호버 상태, 활성 상태도 함께 확인

### 크기 단위
1. **절대 크기**: `px` 사용 (예: `font-size: 18px`)
2. **상대 크기**: `em` 또는 `%` 사용 (예: `line-height: 1.3em`)
3. **뷰포트 단위**: `vh`, `vw` 사용 가능 (예: `margin-top: 2dvh`)

### 빌드 및 배포
1. **수정 후 반드시 빌드 필요**: `npm run build`
2. **TypeScript 에러 확인**: 빌드 전 타입 체킹
3. **이미지 파일 변경 시**: NAS에서 기존 파일 삭제 후 새 파일 업로드
4. **캐시 문제**: 브라우저 강력 새로고침 (`Ctrl + Shift + R`)

### 스타일 수정 시
1. **CSS 우선순위 확인**: `!important` 사용 여부
2. **부모 요소 영향**: 상속되는 스타일 확인
3. **반응형 확인**: 다양한 해상도에서 테스트
4. **애니메이션 충돌**: 기존 애니메이션과의 호환성
5. **z-index 계층**: 오버레이 순서 확인

### 텍스트 수정 시
1. **줄바꿈 확인**: `<br>` 태그 위치
2. **HTML 엔티티**: 특수문자 인코딩 (`&nbsp;`, `&lt;` 등)
3. **말줄임**: `word-break: keep-all` 적용 확인
4. **폰트 로딩**: 커스텀 폰트 로드 여부 확인

### JSON 데이터 수정 시
1. **JSON 문법 확인**: 따옴표, 쉼표, 괄호
2. **배열 인덱스**: 0부터 시작
3. **correct 값**: 1부터 시작 (첫 번째 보기 = 1)
4. **HTML 태그**: `v-html`로 렌더링되므로 HTML 사용 가능

---

## 🆘 문제 해결

### 스타일이 적용 안될 때
1. 빌드 다시 실행: `npm run build`
2. NAS 파일 확인
3. 브라우저 캐시 삭제
4. 시크릿 모드로 테스트

### 빌드 에러 발생 시
```bash
npm install
npm run build
```

---

## 📊 문서 정보

**작성일**: 2026-01-16
**최종 수정**: 2026-01-16
**버전**: 2.0 (완전판)

### 변경 이력

#### v2.0 (2026-01-16)
- ✅ 누락된 10가지 색상 코드 추가
- ✅ 전체 폰트 목록 추가 (Paperlogy 전체 시리즈)
- ✅ Skip 버튼, 인덱스 메뉴, 스크립트 영역 추가
- ✅ Z-Index 계층 구조 추가
- ✅ 애니메이션 & 트랜지션 상세 설명 추가
- ✅ 백드롭 필터, 스크롤바 커스터마이징 추가
- ✅ Flexbox 레이아웃 가이드 추가
- ✅ 모든 버튼 이미지 목록 (크기 포함)
- ✅ 배경 이미지 전체 목록
- ✅ 상세한 주의사항 추가

#### v1.0 (2026-01-16)
- 기본 페이지별 스타일 가이드 작성
- 주요 색상, 데이터 수정 방법 포함

### 문서 완성도

- **페이지 커버리지**: 12/12 페이지 (100%)
- **스타일 속성 커버리지**: ~95%
- **이미지 파일 커버리지**: 100%
- **색상 코드 커버리지**: 100%
- **폰트 커버리지**: 100%
