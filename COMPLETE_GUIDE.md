# 스마트에너지 ICT 프로젝트 완전 가이드

> 빌드, 배포, 스타일 수정, 페이지 추가를 위한 통합 가이드

**작성일**: 2026-01-27
**버전**: 3.0 (통합 완전판)

---

## 📋 목차

1. [프로젝트 개요](#1-프로젝트-개요)
2. [빌드 및 배포](#2-빌드-및-배포)
3. [페이지 구조](#3-페이지-구조)
4. [스타일 수정 가이드](#4-스타일-수정-가이드)
5. [컴포넌트별 상세 수정법](#5-컴포넌트별-상세-수정법)
6. [최근 수정 사항 (2026-01-27)](#6-최근-수정-사항-2026-01-27)
7. [트러블슈팅](#7-트러블슈팅)
8. [체크리스트](#8-체크리스트)

---

## 1. 프로젝트 개요

### 차시 구성
- **1차시**: 사전테스트 포함, 12페이지
- **2-19차시**: 사전테스트 없음, 9-10페이지
  - **2컨텐츠 차시** (02, 03, 05, 08-19): 9페이지
  - **3컨텐츠 차시** (04, 06, 07): 10페이지

### 페이지 유형
1. **인트로** (Intro) - 차시 시작
2. **학습목표** (Goal) - 학습 목표 제시
3. **주요키워드** (Keyword) - 핵심 키워드
4. **본문1-3** (Content) - 학습 내용
5. **생각해보기** (Think) - 사고력 확장
6. **퀴즈** (Quiz) - 학습 평가
7. **정리하기** (Summary) - 내용 요약
8. **아웃트로** (Outro) - 차시 종료

### 기술 스택
- **프레임워크**: Vue 3 (Composition API) + TypeScript
- **UI 라이브러리**: Vuetify 3
- **빌드 툴**: Vite
- **CSS**: SCSS
- **애니메이션**: animate.css

---

## 2. 빌드 및 배포

### 2.1. 사전 준비

```bash
# 의존성 패키지 설치 (최초 1회)
npm install
```

### 2.2. 빌드 실행

```bash
npm run build
```

빌드 과정:
1. TypeScript 타입 체킹 (`vue-tsc --noEmit`)
2. Vite 빌드 실행 (`vite build`)
3. HTML 후처리 스크립트 자동 실행 (`node scripts/flatten-html.mjs`)

### 2.3. 빌드 결과물

`dist/` 폴더 구조:
```
dist/
├── 01/
│   ├── 01.html (인트로)
│   ├── 02.html (사전테스트) ⭐ 1차시만
│   ├── 03.html (학습목표)
│   ├── ...
│   └── 12.html (아웃트로)
├── 02/
│   ├── 01.html (인트로)
│   ├── 02.html (학습목표)
│   ├── ...
│   └── 09.html (아웃트로)
├── assets/
│   ├── img/
│   ├── font/
│   └── ...
├── data/
├── down/
└── mp4/
```

### 2.4. NAS 배포

#### 배포 경로
```
/volume1/WEBSERVICE/@PREVIEW@/bitcampus/teset/dist
```

#### 배포 방법 (권장)
1. NAS의 기존 `dist` 폴더 전체 삭제
2. 로컬의 `dist` 폴더 전체를 NAS로 복사

#### 주의사항
- 동영상/이미지 파일 수정 시: 기존 파일 삭제 후 새 파일 업로드
- 파일명 변경 시: 기존 파일이 남아있지 않도록 주의
- 배포 후: 브라우저 강력 새로고침 필요

### 2.5. 웹 접속

```
http://preview.heyhey.com/bitcampus/teset/dist/
```

예시:
- 1차시, 1페이지: `http://preview.heyhey.com/bitcampus/teset/dist/01/01.html`
- 19차시, 7페이지(퀴즈): `http://preview.heyhey.com/bitcampus/teset/dist/19/07.html`

### 2.6. 브라우저 캐시 문제 해결

#### 강력 새로고침
- **Windows**: `Ctrl + Shift + R` 또는 `Shift + F5`
- **Mac**: `Cmd + Shift + R`

#### 시크릿 모드 테스트
- `Ctrl + Shift + N`으로 시크릿 창 열기
- 캐시 없이 최신 버전 확인 가능

### 2.7. 개발 환경

```bash
# 로컬 개발 서버 실행
npm run dev
```

접속: `http://localhost:3031`

---

## 3. 페이지 구조

### 3.1. 1차시 (사전테스트 포함)

```
Page1  → 인트로
Page2  → 사전테스트 (Pre-test) ⭐ 1차시만!
Page3  → 학습목표
Page4  → 주요 키워드
Page5  → 본문1
Page6  → 본문2
Page7  → 본문3
Page8  → 본문4
Page9  → 생각해보기 (Think)
Page10 → 퀴즈 (Quiz)
Page11 → 정리하기 (Summary)
Page12 → 아웃트로
```

**총 12페이지** | `totalPages = 12`

### 3.2. 2컨텐츠 차시 (02, 03, 05, 08-19)

```
Page1 → 인트로
Page2 → 학습목표
Page3 → 주요 키워드
Page4 → 본문1
Page5 → 본문2
Page6 → 생각해보기 (Think)
Page7 → 퀴즈 (Quiz)
Page8 → 정리하기 (Summary)
Page9 → 아웃트로
```

**총 9페이지** | `totalPages = 9`

### 3.3. 3컨텐츠 차시 (04, 06, 07)

```
Page1  → 인트로
Page2  → 학습목표
Page3  → 주요 키워드
Page4  → 본문1
Page5  → 본문2
Page6  → 본문3 ⭐ 추가 컨텐츠!
Page7  → 생각해보기 (Think)
Page8  → 퀴즈 (Quiz)
Page9  → 정리하기 (Summary)
Page10 → 아웃트로
```

**총 10페이지** | `totalPages = 10`

### 3.4. Think 페이지 추가 방법

#### Step 1: JSON 파일 수정 (`public/data/XX.json`)

##### video_X 추가
```json
{
  "video_1": "../mp4/intro_XX.mp4",
  "video_3": "../mp4/goal_XX.mp4",
  "video_4": "../mp4/keyword_XX.mp4",
  "video_5": "../mp4/XX_01.mp4",
  "video_6": "../mp4/XX_02.mp4",
  "video_7": "../mp4/XX_03.mp4",    // 3컨텐츠만
  "video_8": "../mp4/think.mp4",    // ✨ Think 비디오
  "video_9": "../mp4/quiz.mp4",
  "video_10": "../mp4/summary.mp4",
  "video_11": "../mp4/outro_XX.mp4"
}
```

##### pageInfo 배열 업데이트
```json
"pageInfo": [
  { "category": "1", "showChapter": false, "seq": "1", "title": "인트로" },
  { "category": "1", "showChapter": true,  "seq": "2", "title": "학습목표" },
  { "category": "1", "showChapter": true,  "seq": "3", "title": "주요 키워드" },
  { "category": "2", "showChapter": false, "seq": "4", "title": "본문1" },
  { "category": "2", "showChapter": false, "seq": "5", "title": "본문2" },
  { "category": "3", "showChapter": true,  "seq": "6", "title": "생각해보기" }, // ✨ 추가
  { "category": "3", "showChapter": true,  "seq": "7", "title": "퀴즈" },
  { "category": "3", "showChapter": true,  "seq": "8", "title": "정리하기" },
  { "category": "3", "showChapter": false, "seq": "9", "title": "아웃트로" }
]
```

**🔥 중요**: `seq` 번호를 순차적으로 재정렬!

##### think 섹션 추가
```json
"think": {
  "question": "학습 주제와 관련된 사고력 확장 질문",
  "answer": "전문가 의견 및 해설"
}
```

##### scripts 배열 확인
```json
// 2컨텐츠 차시 (9페이지)
"scripts": [
  "인트로 자막",          // 0
  "학습목표 자막",        // 1
  "주요키워드 자막",      // 2
  "본문1 자막",           // 3
  "본문2 자막",           // 4
  "Think 자막",           // 5 ✨
  "Quiz 자막",            // 6
  "Summary 자막",         // 7
  "Outro 자막"            // 8
]
// 총 9개 (index 0-8)
```

#### Step 2: Vue 파일 생성 (`src/pages/XX/flow/Page6.vue`)

2컨텐츠 차시 예시:
```vue
<script setup lang="ts">
import { onMounted, ref } from 'vue'
import axios from 'axios'
import VideoComponent from '@/components/VideoComponent.vue'
import ThinkComponent from '@/components/ThinkComponent.vue'

const props = defineProps({
  currentPage: { type: Number, required: true },
  totalPages: { type: Number, required: true },
})

const emit = defineEmits(['prevPage', 'nextPage', 'changePage'])

let json
const courseInfo = ref()
const pageInfo = ref()
const video = ref()
const thinkContent = ref()
const scriptText = ref()
const isReady = ref(false)

axios.get('/data/02.json').then((result) => {
  json = result.data
  courseInfo.value = json.courseInfo
  pageInfo.value = json.pageInfo
  video.value = json.video_8 as string  // ✨ Think 비디오

  if (json.think && json.think.question) {
    thinkContent.value = {
      question: json.think.question,
      answer: json.think.answer,
    }
  }

  scriptText.value = json.scripts[5] as string  // ✨ scripts[5]

  setTimeout(() => {
    isReady.value = true
  }, 1)
}).catch(() => {
  console.log('error')
})

const handlePrev = () => { emit('prevPage') }
const handleNext = () => { emit('nextPage') }
const handleChangeIndex = (target: number) => { emit('changePage', target) }

onMounted(() => {
  setTimeout(() => {
    const elMain = document.querySelector('#refInteractive') as HTMLDivElement
    const elVideo = document.querySelector('#videoPlayer') as HTMLVideoElement
    elVideo.appendChild(elMain)
  }, 100)
  parent.setCurrentPageNumber(6)  // ✨ currentPage와 일치
})
</script>

<template>
  <VideoComponent
    v-if="isReady"
    :video="video"
    :course-info="courseInfo"
    :page-info="pageInfo"
    :script-text="scriptText"
    :current-page="props.currentPage"
    :total-pages="props.totalPages"
    :auto-start="true"
    @handle-prev="handlePrev"
    @handle-next="handleNext"
    @handle-change-page="handleChangeIndex"
  />
  <div id="refInteractive" class="animate__animated animate__fadeIn animate__delay-3s">
    <ThinkComponent
      v-if="isReady && thinkContent"
      :think-content="thinkContent"
      @handle-next="handleNext"
    />
  </div>
</template>

<style scoped>
.video-js .vjs-tech {
  display: none;
}
#refInteractive {
  position: absolute;
  width: 1120px;
  height: 630px;
  overflow: hidden;
}
</style>
```

#### Step 3: App.vue 수정

```vue
<script lang="ts">
import Page1 from './flow/Page1.vue'
import Page2 from './flow/Page2.vue'
import Page3 from './flow/Page3.vue'
import Page4 from './flow/Page4.vue'
import Page5 from './flow/Page5.vue'
import Page6 from './flow/Page6.vue'  // ✨ Think
import Page7 from './flow/Page7.vue'
import Page8 from './flow/Page8.vue'
import Page9 from './flow/Page9.vue'

const totalPages = 9  // ✨ 페이지 수

export default defineComponent({
  components: {
    Page1, Page2, Page3, Page4, Page5,
    Page6, Page7, Page8, Page9,
  },
  // ...
})
</script>

<template>
  <v-app id="content-app">
    <v-main>
      <Page1 v-if="currentPage === 1" ... />
      <Page2 v-if="currentPage === 2" ... />
      <Page3 v-if="currentPage === 3" ... />
      <Page4 v-if="currentPage === 4" ... />
      <Page5 v-if="currentPage === 5" ... />
      <Page6 v-if="currentPage === 6" ... />  <!-- ✨ Think -->
      <Page7 v-if="currentPage === 7" ... />
      <Page8 v-if="currentPage === 8" ... />
      <Page9 v-if="currentPage === 9" ... />
    </v-main>
  </v-app>
</template>
```

---

## 4. 스타일 수정 가이드

### 4.1. 색상 참고표

| 색상 코드 | 색상명 | 사용 위치 |
|-----------|--------|-----------|
| `#0e7300` | 진한 녹색 | 퀴즈 문제, 정답, 카운트다운 |
| `#6ab554` | 밝은 녹색 | 타이머, 진행바 |
| `#ffffff` | 흰색 | 생각해보기 질문 |
| `#000000` | 검정색 | 챕터명, 정리하기 |
| `#333333` | 어두운 회색 | 보기 텍스트 |
| `#ff6699` | 핑크 | 강조 텍스트 |
| `#135db7` | 파랑 | 인덱스 메뉴 |
| `#808080` | 회색 | 스크롤바 |

### 4.2. 폰트 참고표

#### Paperlogy 시리즈
| 폰트명 | Weight | 사용 위치 |
|--------|--------|-----------|
| `Paperlogy-4Regular` | 400 | 보기 텍스트, 해설 |
| `Paperlogy-5Medium` | 500 | 챕터명, 스크립트 |
| `Paperlogy-7Bold` | 700 | 문제 텍스트 |
| `Paperlogy-7ExtraBold` | 700 | 카운트다운 숫자 |
| `Paperlogy-8ExtraBold` | 800 | 생각해보기 질문 |

### 4.3. 크기 단위
- **절대 크기**: `px` (예: `font-size: 18px`)
- **상대 크기**: `em` 또는 `%` (예: `line-height: 1.3em`)
- **뷰포트 단위**: `vh`, `vw`

---

## 5. 컴포넌트별 상세 수정법

### 5.1. 사전테스트 (PreComponent.vue)

**파일 위치**: `src/components/PreComponent.vue`

#### 정답 설정 (중요!)
```javascript
// 파일 위치: 25-26번 줄
const answers = [1, 2, 1, 1, 2, 1, 2, 1, 1, 2]  // 1=O, 2=X
```

| 문제 | 정답 | 배열 값 |
|------|------|---------|
| 1번  | O    | 1       |
| 2번  | X    | 2       |
| 3번  | O    | 1       |
| ...  | ...  | ...     |

#### PDF 다운로드 (새 창 열기)
```typescript
// 파일 위치: 95-107번 줄
const handleDownload = (level) => {
  let fileName = ''
  if (level === 1)
    fileName = '사전진단테스트 피드백 학습자료_초급.pdf'
  else if (level === 2)
    fileName = '사전진단테스트 피드백 학습자료_중급.pdf'
  else
    fileName = '사전진단테스트 피드백 학습자료_고급.pdf'

  // 새 창으로 PDF 열기
  window.open(`../down/${fileName}`, '_blank')
}
```

#### 레벨 텍스트 스타일
```scss
// 파일 위치: 298-307번 줄
p.level {
  font-family: 'Paperlogy-8ExtraBold', serif;
  font-size: 42px;
  color: #0e7300;
  position: absolute;
  top: 163px;
  left: 643px;
}
```

### 5.2. 생각해보기 (ThinkComponent.vue)

**파일 위치**: `src/components/ThinkComponent.vue`

#### 질문 텍스트
```scss
// 파일 위치: 124-195번 줄
.questionHead {
  font-family: 'Paperlogy-8ExtraBold', serif;
  font-size: 31px;  // 글씨 크기
  color: #0e7300;   // 글씨 색상
  position: absolute;
  top: 113px;       // 위치 (적어질수록 위로)
  left: 155px;      // 위치 (적어질수록 왼쪽)
  max-width: 800px;

  p {
    max-height: 115px;  // 스크롤 영역 높이
    overflow-y: auto;

    // 스크롤바 스타일
    &::-webkit-scrollbar {
      width: 8px;  // ✨ 통일된 너비
      background-color: transparent;
    }
    &::-webkit-scrollbar-thumb {
      background-color: #808080;
      border-radius: 100px;
    }
    &::-webkit-scrollbar-track {
      background-color: #6AB554;
      border-radius: 5px;
    }
  }
}
```

#### 답변 텍스트
```scss
// 파일 위치: 204-236번 줄
.answerContent {
  position: absolute;
  top: 160px;  // 위치 (적어질수록 위로)
  left: 130px;
  max-width: 889px;
  height: 190px;
  font-family: 'Paperlogy-4Regular', sans-serif;
  font-size: 23px;  // 글씨 크기
  color: #333;      // 글씨 색상

  // 스크롤바 스타일 (질문과 동일)
  &::-webkit-scrollbar {
    width: 8px;
  }
  &::-webkit-scrollbar-thumb {
    background-color: #808080;
    border-radius: 100px;
  }
  &::-webkit-scrollbar-track {
    background-color: #ffffff;
    border-radius: 5px;
  }
}
```

### 5.3. 퀴즈 (QuizComponent.vue)

**파일 위치**: `src/components/QuizComponent.vue`

#### 보기 번호 (1,2,3,4) 중앙 정렬
```scss
// 파일 위치: 801-818번 줄
&.exam-number {
  background-color: #fff;
  width: 28px;
  height: 28px;
  line-height: 1;  // ✨ 중앙 정렬의 핵심
  font-size: 22px;
  color: #000;
  border: 2px solid #000;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 0;
  margin: 0;
  flex-shrink: 0 !important;
}

// 각 숫자별 미세 조정 (파일 위치: 856-870번 줄)
.exam-lists:nth-child(1) div.exam-number {
  padding-top: 2px !important;  // 1번
}
.exam-lists:nth-child(2) div.exam-number {
  padding-top: 1px !important;  // 2번
}
.exam-lists:nth-child(3) div.exam-number {
  padding-top: 2px !important;  // 3번
}
.exam-lists:nth-child(4) div.exam-number {
  padding-top: 1px !important;  // 4번
}
```

#### 긴 보기 (longExam) 레이아웃
```vue
<!-- 파일 위치: 440-441번 줄 (template) -->
<div :class="[questionLists[quizSeq]?.longExam ? '' : 'd-inline-block', 'exam-number']"
     v-html="(Number(index) + 1)" />
<div :class="[questionLists[quizSeq]?.longExam ? '' : 'd-inline-block', 'exam-text',
              { 'exam-text-long': questionLists[quizSeq]?.longExam === true }]"
     v-html="exam" />
```

```scss
// 파일 위치: 839-853번 줄
li.exam-lists.exam-lists-long {
  height: auto !important;
  min-height: 40px !important;
  width: 850px !important;
  display: flex !important;
  flex-direction: row !important;
  align-items: flex-start !important;
  gap: 12px !important;
  margin: 0 !important;
  padding: 0 !important;
  line-height: normal !important;
}

// 파일 위치: 825-835번 줄
&.exam-text-long {
  flex: 1 !important;
  max-width: none !important;
  width: auto !important;
  line-height: 1.3em !important;
  word-break: keep-all !important;
  white-space: normal !important;
  text-indent: 0 !important;
  margin-top: 0 !important;
  font-size: 22px !important;
}
```

#### Shape.png (챕터명) 위치 조정

**일반 퀴즈 화면**
```scss
// 파일 위치: 1089-1114번 줄
.always-visible-overlay .shape-container {
  position: absolute;
  top: calc(50% - 314px);
  left: calc(50% - 429px);
  background: transparent url(@/assets/img/top/shape.png) no-repeat center center;
  background-size: contain;
  width: 317px;
  height: 78px;
  display: flex;
  align-items: center;
  justify-content: center;
  pointer-events: none;
  z-index: 1000001;

  p {
    font-family: 'Paperlogy-5Medium', sans-serif;
    font-size: 16px;
    font-weight: 200;
    letter-spacing: -1px;
    margin-left: 7px;   // 텍스트 좌우 위치
    margin-top: -4px;   // 텍스트 상하 위치
    color: #000000;
    text-align: center;
  }
}
```

**카운트다운 화면**
```scss
// 파일 위치: 1113-1138번 줄
.countdown-overlay .shape-container-countdown {
  position: absolute;
  top: calc(50% - 314px);
  left: calc(50% - 429px);
  background: transparent url(@/assets/img/top/shape.png) no-repeat center center;
  background-size: contain;
  width: 318px;
  height: 78px;
  display: flex;
  align-items: center;
  justify-content: center;
  pointer-events: none;
  z-index: 1000000;

  p {
    font-family: 'Paperlogy-5Medium', sans-serif;
    font-size: 16px;
    font-weight: 200;
    letter-spacing: -1px;
    margin-left: 7px;   // ✨ 오른쪽으로 이동: 숫자 증가
    margin-top: -3px;   // ✨ 아래로 이동: 숫자 증가 (예: -2px, -1px)
    color: #000000;
    text-align: center;
  }
}
```

**텍스트 위치 조정 방법**:
- `margin-left: 7px` → 오른쪽 이동: 8px, 9px 등으로 증가
- `margin-top: -3px` → 아래 이동: -2px, -1px, 0px 등으로 증가

### 5.4. 정리하기 (SummaryComponent.vue)

**파일 위치**: `src/components/SummaryComponent.vue`

#### 스크롤바 스타일 (기준 디자인)
```scss
// 파일 위치: 98-110번 줄
&::-webkit-scrollbar {
  width: 8px;  // ✨ 기준 너비
  background-color: transparent;
}
&::-webkit-scrollbar-thumb {
  background-color: #808080;
  border-radius: 100px;
}
&::-webkit-scrollbar-track {
  background-color: #ffffff;
  border-radius: 5px;
  margin: 40px 0 20px 0;
}
&::-webkit-scrollbar-button {
  display: none;
}
```

---

## 6. 최근 수정 사항 (2026-01-27)

### 6.1. 퀴즈 보기 번호 (1,2,3,4) 중앙 정렬

#### 문제 상황
- 보기 번호가 원의 중앙이 아닌 "5시 방향" (오른쪽 아래)에 표시됨
- 숫자별로 미묘하게 다른 위치에 표시됨

#### 해결 방법
1. **`line-height: 1` 사용**
   ```scss
   line-height: 1;  // 기존 28px에서 변경
   ```

2. **각 숫자별 개별 padding 조정**
   ```scss
   .exam-lists:nth-child(1) div.exam-number { padding-top: 2px !important; }
   .exam-lists:nth-child(2) div.exam-number { padding-top: 1px !important; }
   .exam-lists:nth-child(3) div.exam-number { padding-top: 2px !important; }
   .exam-lists:nth-child(4) div.exam-number { padding-top: 1px !important; }
   ```

3. **`!important` 사용 이유**: Vuetify의 기본 스타일 우선순위를 override하기 위함

### 6.2. 스크롤바 디자인 통일

#### 변경 내용
- ThinkComponent의 질문/답변 영역 스크롤바
- SummaryComponent를 기준으로 통일
- 너비: `10px` → `8px`
- 화살표 버튼 제거: `display: none`

#### 적용 위치
1. **ThinkComponent - 질문 영역** (152-167번 줄)
2. **ThinkComponent - 답변 영역** (234-249번 줄)
3. **SummaryComponent** (98-110번 줄) - 기준 디자인

### 6.3. PDF 다운로드 방식 변경

#### 기존 방식
```javascript
// 다운로드 속성을 가진 <a> 태그 생성
const link = document.createElement('a')
link.href = `../down/${fileName}`
link.download = fileName
link.click()
```

#### 변경 후
```javascript
// 새 창/탭에서 PDF 열기
window.open(`../down/${fileName}`, '_blank')
```

**변경 이유**: 사용자가 PDF를 브라우저에서 직접 보고 필요 시 다운로드할 수 있도록

### 6.4. 19차시 longExam 필드 추가

#### 문제 상황
- 19차시 2번 문제가 긴 보기 텍스트인데 레이아웃이 적용되지 않음
- JSON에는 `longExam: true`가 있었으나 Page7.vue에서 매핑하지 않음

#### 해결 방법
**파일 위치**: `src/pages/19/flow/Page7.vue` (42-73번 줄)

```typescript
questionLists.value = [
  {
    qNum:      imgQ1,
    question:  json.quiz[0].question,
    sentence:  json.quiz[0].sentence,
    tall:      json.quiz[0].tall,
    longExam:  json.quiz[0].longExam,  // ✨ 추가
    examLists: json.quiz[0].examLists,
    correct:   json.quiz[0].correct,
    explain:   json.quiz[0].explain,
  },
  {
    qNum:      imgQ2,
    question:  json.quiz[1].question,
    sentence:  json.quiz[1].sentence,
    tall:      json.quiz[1].tall,
    longExam:  json.quiz[1].longExam,  // ✨ 추가
    examLists: json.quiz[1].examLists,
    correct:   json.quiz[1].correct,
    explain:   json.quiz[1].explain,
  },
  {
    qNum:      imgQ3,
    question:  json.quiz[2].question,
    sentence:  json.quiz[2].sentence,
    tall:      json.quiz[2].tall,
    longExam:  json.quiz[2].longExam,  // ✨ 추가
    examLists: json.quiz[2].examLists,
    correct:   json.quiz[2].correct,
    explain:   json.quiz[2].explain,
  },
]
```

### 6.5. Shape.png 위치 조정

#### 조정 내용
- 카운트다운 화면에서 Shape.png가 미묘하게 다르게 보이는 문제
- 텍스트 위치를 독립적으로 조정할 수 있도록 설명 추가

#### 조정 가능한 속성
```scss
.countdown-overlay .shape-container-countdown {
  // 컨테이너 위치
  top: calc(50% - 314px);
  left: calc(50% - 429px);
  width: 318px;
  height: 78px;

  p {
    // 텍스트 위치 (독립적으로 조정 가능)
    margin-left: 7px;   // 오른쪽: 증가
    margin-top: -3px;   // 아래: 증가 (음수 값 증가)
  }
}
```

### 6.6. 챕터별 Shape.png 분기 처리 (Shapev2.png)

#### 배경
- 11, 12, 13, 19차시는 챕터 제목이 길어서 기본 Shape.png로는 텍스트가 잘림
- 해당 차시에만 더 넓은 Shapev2.png 적용 필요

#### 구현 방법
**파일 위치**: `src/components/VideoComponent.vue`

##### 1. HTML에 data-chapter 속성 추가 (788번째 줄)
```vue
<v-row v-if="pageInfo[currentPage - 1].showChapter"
       id="fixedChapter"
       class="ma-0 area-chapter animate__animated animate__flipInX"
       :class="!isPlayed ? 'hidden' : ''"
       :data-chapter="courseInfo.chapterNumber">
  <v-col>
    <p>{{ chapterTitle }}</p>
  </v-col>
</v-row>
```

##### 2. CSS 조건부 스타일 추가 (881-889번째 줄)
```scss
// 기본 Shape.png (전체 차시)
.area-chapter {
  position: absolute;
  top: calc(50% - 313px);
  left: calc(50% - 429px);
  z-index: 9997;
  background: transparent url(@/assets/img/top/shape.png) no-repeat center center;
  background-size: contain;
  width: 317px;
  height: 78px;
  display: flex;
  align-items: center;
  justify-content: center;
  p {
    font-family: 'Paperlogy-5Medium', sans-serif;
    font-size: 19px;
    font-weight: 200;
    letter-spacing: -1px;
    margin-left: 7px;
    margin-top: -2px;
    word-break: keep-all;
    color: #000000;
    text-align: center;
  }
}

// Shapev2.png (11, 12, 13, 19차시만)
.area-chapter[data-chapter="11"],
.area-chapter[data-chapter="12"],
.area-chapter[data-chapter="13"],
.area-chapter[data-chapter="19"] {
  background: transparent url(@/assets/img/top/Shapev2.png) no-repeat center center;
  background-size: contain;
  width: 400px;
  left: calc(50% - 450px);
}
```

#### 크기 및 위치 조정 방법
```scss
.area-chapter[data-chapter="11"],
.area-chapter[data-chapter="12"],
.area-chapter[data-chapter="13"],
.area-chapter[data-chapter="19"] {
  width: 400px;  // Shapev2.png 가로 크기 조정
  left: calc(50% - 450px);  // 중앙 정렬 위치 조정
  // width 변경 시: left = calc(50% - 429px - (width - 317) / 2)
}
```

**중앙 정렬 계산법**:
- 기본 width: 317px, left: calc(50% - 429px)
- 새 width가 400px이면: (400 - 317) / 2 = 41.5px 추가
- 새 left: calc(50% - 429px - 41px) = calc(50% - 470px)

#### 적용 대상 차시별 글자 수
- 11차시: "에너지저장장치(ESS)의 원리와 종류" (20자)
- 12차시: "배터리기술: 리튬이온, 전고체, 차세대 배터리" (25자) ⭐ 최장
- 13차시: "스마트그리드와 전력계통 운영시스템(EMS)" (23자)
- 19차시: "AI 프롬프트 엔지니어링과 실무 활용" (20자)

---

## 7. 트러블슈팅

### 7.1. 아웃트로가 재생되지 않음

#### 원인
- `pageInfo` 배열 개수 ≠ 실제 페이지 수
- Think 페이지 항목 누락

#### 해결
```json
"pageInfo": [
  // ... 기존 항목들
  { "category": "3", "showChapter": true, "seq": "6", "title": "생각해보기" }, // ✨ 추가
  { "category": "3", "showChapter": true, "seq": "7", "title": "퀴즈" },
  // ...
]
```

### 7.2. 스타일이 적용 안될 때

#### 해결 순서
1. 빌드 다시 실행: `npm run build`
2. NAS 파일 확인 및 재배포
3. 브라우저 캐시 삭제: `Ctrl + Shift + R`
4. 시크릿 모드로 테스트

### 7.3. 빌드 에러 발생 시

```bash
# 의존성 재설치
npm install

# TypeScript 체킹 생략하고 빌드만 실행
npx vite build
```

### 7.4. longExam 레이아웃이 적용 안될 때

#### 체크리스트
1. **JSON 파일에 `longExam: true` 확인**
   ```json
   {
     "question": "...",
     "longExam": true,  // ✨ 확인
     "examLists": [...]
   }
   ```

2. **Vue 파일에서 longExam 필드 매핑 확인**
   ```typescript
   questionLists.value = [
     {
       longExam: json.quiz[0].longExam,  // ✨ 확인
     }
   ]
   ```

3. **템플릿에서 조건부 클래스 적용 확인**
   ```vue
   :class="[questionLists[quizSeq]?.longExam ? '' : 'd-inline-block', ...]"
   ```

4. **개발자 도구에서 HTML 요소 확인**
   - `exam-lists-long` 클래스가 적용되었는지 확인
   - `d-inline-block` 클래스가 제거되었는지 확인

### 7.5. Shape.png가 카운트다운에서 다르게 보일 때

#### 확인 사항
1. **컨테이너 위치가 동일한지**
   ```scss
   // always-visible-overlay
   top: calc(50% - 314px);
   left: calc(50% - 429px);

   // countdown-overlay
   top: calc(50% - 314px);  // ✨ 동일해야 함
   left: calc(50% - 429px);  // ✨ 동일해야 함
   ```

2. **텍스트 위치 독립 조정**
   ```scss
   .countdown-overlay .shape-container-countdown p {
     margin-left: 7px;   // 조정 가능
     margin-top: -3px;   // 조정 가능
   }
   ```

3. **overlay scrim 영향**
   - 배경색이 다르면 같은 위치라도 다르게 보일 수 있음
   - 투명도 또는 blur 효과 확인

---

## 8. 체크리스트

### 8.1. 빌드 및 배포 체크리스트

#### 빌드 전
- [ ] 수정한 파일 저장 확인
- [ ] TypeScript 에러 없는지 확인
- [ ] `totalPages` 값 확인 (App.vue)

#### 빌드
- [ ] `npm run build` 실행
- [ ] 빌드 에러 없이 완료 확인
- [ ] `dist/` 폴더 생성 확인

#### 빌드 후 검증
- [ ] `dist/XX/` 폴더에 모든 HTML 파일 생성 확인
- [ ] 수정한 에셋 파일들이 포함되었는지 확인
- [ ] 아웃트로 HTML 파일 생성 확인

#### 배포
- [ ] NAS 기존 dist 폴더 백업 (선택)
- [ ] NAS 기존 dist 폴더 삭제
- [ ] 새 dist 폴더 NAS에 업로드
- [ ] 파일 복사 완료 확인

#### 테스트
- [ ] 브라우저 캐시 삭제 (`Ctrl + Shift + R`)
- [ ] 웹에서 모든 페이지 접근 가능한지 확인
- [ ] 페이지 이동이 정상적으로 작동하는지 확인
- [ ] 아웃트로 페이지가 정상 재생되는지 확인

### 8.2. Think 페이지 추가 체크리스트

#### JSON 파일 (`public/data/XX.json`)
- [ ] `video_8` 추가 (`"../mp4/think.mp4"`)
- [ ] `pageInfo` 배열에 "생각해보기" 항목 추가
- [ ] `seq` 번호 순차적으로 재정렬
- [ ] `think` 섹션 추가 (question, answer)
- [ ] `scripts` 배열 개수 확인 (2컨텐츠: 9개, 3컨텐츠: 10개)

#### Vue 파일 생성
- [ ] 2컨텐츠: `Page6.vue` (Think) 생성
- [ ] 3컨텐츠: `Page7.vue` (Think) 생성
- [ ] `video_8` 참조 확인
- [ ] `scripts[5]` (2컨텐츠) 또는 `scripts[6]` (3컨텐츠) 확인
- [ ] `setCurrentPageNumber` 값 확인 (6 또는 7)
- [ ] `ThinkComponent` import 확인

#### App.vue 업데이트
- [ ] Think 페이지 import 추가
- [ ] `totalPages` 값 확인 (9 또는 10)
- [ ] components 등록 확인
- [ ] 라우팅 조건 순차적으로 정렬
- [ ] 모든 `currentPage` 조건 확인

#### 다른 페이지 업데이트
- [ ] Quiz 페이지: `scripts` 인덱스 +1
- [ ] Quiz 페이지: `setCurrentPageNumber` +1
- [ ] Summary 페이지: `scripts` 인덱스 +1
- [ ] Summary 페이지: `setCurrentPageNumber` +1
- [ ] Outro 페이지: `scripts` 인덱스 확인
- [ ] Outro 페이지: `setCurrentPageNumber` 확인

### 8.3. 스타일 수정 체크리스트

#### 수정 전
- [ ] 수정할 파일 위치 확인 (컴포넌트/페이지)
- [ ] 현재 값 기록 (롤백을 위해)
- [ ] 브라우저 개발자 도구로 실제 적용된 스타일 확인

#### 수정
- [ ] SCSS 문법 확인 (중괄호, 세미콜론)
- [ ] CSS 우선순위 확인 (`!important` 필요 여부)
- [ ] 색상 코드 형식 확인 (`#RRGGBB` 또는 `rgba()`)
- [ ] 단위 확인 (`px`, `em`, `%` 등)

#### 수정 후
- [ ] 빌드 실행 (`npm run build`)
- [ ] NAS 배포
- [ ] 브라우저 강력 새로고침
- [ ] 여러 해상도에서 테스트
- [ ] 다른 페이지에 영향 없는지 확인

---

## 9. 핵심 포인트 요약

### 9.1. 파일 구조
```
프로젝트 루트/
├── src/
│   ├── pages/XX/
│   │   ├── flow/
│   │   │   ├── Page1.vue (인트로)
│   │   │   ├── Page2.vue (학습목표)
│   │   │   ├── ...
│   │   │   └── Page9.vue (아웃트로)
│   │   └── App.vue
│   └── components/
│       ├── VideoComponent.vue
│       ├── ThinkComponent.vue
│       ├── QuizComponent.vue
│       └── SummaryComponent.vue
├── public/
│   ├── data/XX.json
│   └── mp4/
└── scripts/
    └── flatten-html.mjs
```

### 9.2. 중요 원칙

1. **pageInfo 배열 = 실제 페이지 수**
   - 반드시 일치해야 네비게이션이 정상 작동

2. **파일명은 순차적으로**
   - `Page1.vue → Page2.vue → Page3.vue → ...`
   - 중간에 번호를 건너뛰면 안 됨

3. **scripts 인덱스 = 0부터 시작**
   - 9페이지 = `scripts[0]` ~ `scripts[8]` (총 9개)

4. **setCurrentPageNumber = currentPage**
   - `<Page6 v-if="currentPage === 6">` → `setCurrentPageNumber(6)`

5. **Think 페이지 위치 = Quiz 바로 앞**
   - `[본문] → [Think] → [Quiz] → [Summary] → [Outro]`

### 9.3. 스타일 수정 팁

1. **색상 변경 시**
   - 기본 상태, 호버 상태, 활성 상태 모두 확인
   - 16진수 코드 사용 (`#0e7300`)
   - 투명도 필요 시 `rgba()` 사용

2. **위치 조정 시**
   - `top`/`bottom`: 위아래 이동
   - `left`/`right`: 좌우 이동
   - 음수 값 가능 (예: `margin-top: -4px`)

3. **크기 조정 시**
   - 절대 크기: `px` 사용
   - 상대 크기: `em` 사용
   - 부모 요소 크기 고려

4. **스타일 우선순위**
   - 인라인 스타일 > `!important` > ID > 클래스 > 태그
   - Vuetify 기본 스타일 override 시 `!important` 필요할 수 있음

---

## 10. 참고 자료

### 관련 파일 위치
- **JSON 데이터**: `public/data/XX.json`
- **Vue 페이지**: `src/pages/XX/flow/PageX.vue`
- **App 라우터**: `src/pages/XX/App.vue`
- **컴포넌트**: `src/components/`

### 주요 비디오 파일
- `intro_XX.mp4` - 인트로
- `goal_XX.mp4` - 학습목표
- `keyword_XX.mp4` - 주요키워드
- `XX_01.mp4` ~ `XX_03.mp4` - 본문
- `think.mp4` - Think (공통) ✨
- `quiz.mp4` - Quiz (공통)
- `summary.mp4` - Summary (공통)
- `outro_XX.mp4` - Outro

### 개발 도구
- **개발자 도구**: `F12`
- **요소 검사**: `Ctrl + Shift + C`
- **콘솔**: `Ctrl + Shift + J`
- **네트워크**: `Ctrl + Shift + E`

---

## 📝 변경 이력

### v3.0 (2026-01-27)
- ✅ 퀴즈 보기 번호 중앙 정렬 해결 방법 추가
- ✅ 스크롤바 디자인 통일 (8px)
- ✅ PDF 다운로드 방식 변경 (새 창 열기)
- ✅ 19차시 longExam 필드 추가
- ✅ Shape.png 텍스트 위치 조정 방법 추가
- ✅ 챕터별 Shape.png 분기 처리 (Shapev2.png for 11, 12, 13, 19차시)
- ✅ data-chapter 속성 기반 조건부 스타일링 구현
- ✅ 3개 가이드 문서 통합 (STYLE_GUIDE, 페이지구조가이드, BUILD_GUIDE)
- ✅ 중복 내용 제거 및 구조 재정리

### v2.0 (2026-01-22)
- ✅ 모든 차시(02-19) JSON 파일에 "생각해보기" 항목 추가
- ✅ 아웃트로 재생 문제 해결
- ✅ 페이지 파일명 순차화

### v1.0 (2026-01-16)
- 기본 스타일 가이드 작성
- 빌드 가이드 작성

---

## 🎉 마무리

이 문서는 스마트에너지 ICT 프로젝트의 모든 수정 작업을 위한 완전한 가이드입니다.

- **빌드/배포**: 섹션 2 참고
- **페이지 추가**: 섹션 3 참고
- **스타일 수정**: 섹션 4, 5 참고
- **최근 수정 사항**: 섹션 6 참고
- **문제 해결**: 섹션 7 참고

질문이나 추가 사항이 있으면 이 문서를 업데이트하세요!
