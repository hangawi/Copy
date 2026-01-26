<script setup lang="ts">
import { onMounted, ref } from 'vue'
import { useSound } from '@vueuse/sound'
import 'animate.css'

import sfxClick from '@/assets/sound/effect/click.mp3'

import imgQuestionLeft from '@/assets/img/think/questionLeft.png'
import imgQuestionRight from '@/assets/img/think/questionRight.png'

const props = defineProps({
  thinkContent: {
    type: Object,
    required: true,
  },
})

const soundClick = useSound(sfxClick)

const thinkSeq = ref(0)

const refThink = ref()

const thinkContent = props.thinkContent

const handleStart = () => {
  if (thinkSeq.value > 0)
    return false

  soundClick.play()
  thinkSeq.value++

  const elButton = document.querySelector('.think-intro-container .btnStart') as HTMLElement
  const elAnswer = document.querySelector('.think-intro-container .area-answer') as HTMLElement
  const elQuestion = document.querySelector('.think-intro-container .questionHead p') as HTMLElement

  elButton.classList.remove('animate__delay-2s')
  elButton.classList.add('animate__flipOutX')

  setTimeout(() => {
    elAnswer.classList.remove('hidden')
    elAnswer.classList.add('animate__fadeIn')

    // 스크롤 활성화 유지
    if (elQuestion) {
      elQuestion.style.pointerEvents = 'auto'
      elQuestion.style.userSelect = 'auto'
    }
  }, 500)
}

onMounted(() => {
  const elProgress = document.querySelector('.video-js .vjs-progress-control') as HTMLElement
  const elPlayControl = document.querySelector('.vjs-play-control') as HTMLElement
  elProgress.classList.add('event-none')
  elPlayControl.classList.add('event-none')
})
</script>

<template>
  <v-container
    id="elOverlay"
    ref="refThink"
    class="w-100 pa-0 think-intro-container animate__animated animate__fadeIn animate__slow"
  >
    <v-row>
      <v-col class="think-question questionHead">
        <p>
<!--          <img class="animate__animated animate__fadeInLeftBig animate__delay-1s" :src="imgQuestionLeft" alt="">-->
          <span class="animate__animated animate__fadeIn animate__delay-1_6s" v-html="thinkContent.question" />
<!--          <img class="animate__animated animate__fadeInRightBig animate__delay-1s" :src="imgQuestionRight" alt="">-->
        </p>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <button
          class="d-flex position-relative ma-auto animate__animated animate__delay-2s animate__flipInX btnStart"
          @click="handleStart"
        >
          START
        </button>
      </v-col>
    </v-row>
    <v-row class="ma-0 mt-6 area-answer hidden animate__animated">
      <v-col class="d-flex align-end mr-4">
        <div class="answerContent animate__animated animate__fadeIn animate__delay-1s">
          <p v-html="thinkContent.answer" />
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<style lang="scss" scoped>
// 인트로 화면
.think-intro-container {
  background: transparent url(@/assets/img/think/bgThink.png) no-repeat 0 0;
  background-size: contain;
  width: 100%;
  height: 100%;
  max-width: 1120px;
  position: absolute;
}

// 인트로 스타트 버튼
.btnStart {
  background: transparent url(@/assets/img/think/btnThink.png) no-repeat 0 0;
  background-size: contain;
  text-indent: -9999em;
  width: 373px;
  height: 453px;
  top: 342px; // 적어질수록 위로 올라감
  left: 0;
  transition: background 300ms ease-in-out;
  pointer-events: auto;  // 버튼만 클릭 가능
  z-index: 1;
  &:hover {
    background: transparent url(@/assets/img/think/btnThinkOn.png) no-repeat 0 0;
    background-size: contain;
  }
}

.questionHead {
  font-family: 'Paperlogy-8ExtraBold', serif;
  font-size: 31px; //생각해보기 제목 폰트 사이즈
  font-weight: 400;
  letter-spacing: -1px;
  margin-top: 3dvh;
  margin-left: 2px;
  margin-bottom: -40px;
  line-height: 1.0em;
  word-break: keep-all;
  color: #0e7300;
  position: absolute;
  top: 113px; //적어질수록 위로 올라감
  left: 155px; //적어질수록 왼쪽으로 이동
  max-width: 800px;
  z-index: 10;  // 질문 영역을 버튼보다 위로
  p {
    position: absolute;
    width: 828px;
    max-height: 115px;  // 스크롤 공간(높이) 증가
    overflow-y: auto;
    display: block;
    padding-right: 30px;
    cursor: default;  // 커서 모양
    pointer-events: auto;  // 기본적으로 활성화
    user-select: text;  // 텍스트 선택 가능

    // 스크롤바 스타일 (정리하기 기준 통일)
    &::-webkit-scrollbar {
      width: 8px;
      background-color: transparent;
    }
    &::-webkit-scrollbar-thumb {
      background-color: #808080;
      border-radius: 100px;
    }
    &::-webkit-scrollbar-track {
      background-color: #6AB554;
      border-radius: 5px;
      margin: 00px 0 10px 0;  // 길이 조정: margin 값 변경
    }
    &::-webkit-scrollbar-button {
      display: none;  // 화살표 버튼 제거
    }

    img, span {
      position: relative;
      display: inline-block;
      vertical-align: middle;
    }
    img {
      width: 30px;
      margin: 0 10px;
    }
    span {
      display: inline;
      max-width: 800px;
      line-height: 33px;
      text-align: left;
      letter-spacing: -2px;
    }
  }
  span.positive {
    color: #ff6699;
    border-bottom: 2px solid;
  }

  span.negative {
    color: #ff6699;
    border-bottom: 2px solid;
  }
}

.area-answer {
  //background: transparent url(@/assets/img/think/bgAnswer.png) no-repeat 0 0;
  //background-size: contain;
  width: 1000px;
  height: 500px;
  bottom: 0;
  position: absolute;
  .answerContent {
    position: absolute;
    top: 160px; //적어질수록 위로 올라감
    left: 130px;
    right: 3px;
    max-width: 889px;
    height: 190px;
    line-height: 1.4em;
    overflow-y: auto;
    word-break: keep-all;
    font-family: 'Paperlogy-4Regular', sans-serif;
    font-size: 23px; //답변 글씨 크기
    font-weight: 400;
    color: #333;
    padding-right: 20px; // 스크롤바와 글자 간격
    // 스크롤바 스타일 (정리하기 기준 통일)
    &::-webkit-scrollbar {
      width: 8px;
      background-color: transparent;
    }
    &::-webkit-scrollbar-thumb {
      background-color: #808080;
      border-radius: 100px;
    }
    &::-webkit-scrollbar-track {
      background-color: #ffffff;
      border-radius: 5px;
      margin: 40px 0 20px 0;  // 길이 조정: margin 값 변경
    }
    &::-webkit-scrollbar-button {
      display: none;  // 화살표 버튼 제거
    }
  }
}
</style>
