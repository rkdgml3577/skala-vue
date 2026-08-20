<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
import { ref } from "vue";
import SampleOne from "./components/ReactivityExample.vue";
import SampleTwo from "./components/TextInterpolationExample.vue";
import SampleThree from "./components/VueHtml.vue";
import SampleFour from "./components/VueHtmlXSS.vue";
import SampleFive from "./components/VueText.vue";
import SampleSix from "./components/VueBind.vue";
import SampleSeven from "./components/VueBindClassBindingExample.vue";
import SampleEight from "./components/VueBindStyleBindingExample.vue";
import SampleNine from "./components/VueBindSameNameShorthandExample.vue";
import SampleTen from "./components/VueIfVueElseifVueElse.vue";
import SampleEleven from "./components/VueShow.vue";
import SampleTwelve from "./components/VueFor.vue";
import SampleThirteen from "./components/VuePre.vue";
import SampleFourteen from "./components/VueCloak.vue";
import SampleFifteen from "./components/VueOnce.vue";
import SampleSixteen from "./components/VueMemo.vue";
import SampleSeventeen from "./components/VueOnEventHandlerExample.vue";
import SampleEighteen from "./components/EventObjectExample.vue";
import SampleNineteen from "./components/EventModifierExample.vue";
import SampleTwenty from "./components/TwowayDataBindingWithVueModel.vue";
import SampleTwentyOne from "./components/FormElementsHandlingExample.vue";
import SampleTwentyTwo from "./components/VueModelModifiersExample.vue";
import SampleTwentyThree from "./components/VueStyleExample.vue";
import SampleTwentyFour from "./components/RefExample.vue";
import SampleTwentyFive from "./components/ReactiveExample.vue";
import SampleTwentySix from "./components/ComputedExample.vue";
import SampleTwentySeven from "./components/WatchExample.vue";
import SampleTwentyEight from "./components/MultiSourceWatchExample.vue";
import SampleTwentyNine from "./components/DeepWatchExample.vue";
import SampleThirty from "./components/ReactiveDataWatchExample.vue";
import SampleThirtyOne from "./components/WatchEffectExample.vue";
import SampleThirtyTwo from "./components/LifecycleHookExample.vue";
import SampleThirtyThree from "./components/PropsEmitsParents.vue";
const isVisible = ref(true);
const samples = [
  SampleOne,
  SampleTwo,
  SampleThree,
  SampleFour,
  SampleFive,
  SampleSix,
  SampleSeven,
  SampleEight,
  SampleNine,
  SampleTen,
  SampleEleven,
  SampleTwelve,
  SampleThirteen,
  SampleFourteen,
  SampleFifteen,
  SampleSixteen,
  SampleSeventeen,
  SampleEighteen,
  SampleNineteen,
  SampleTwenty,
  SampleTwentyOne,
  SampleTwentyTwo,
  SampleTwentyThree,
  SampleTwentyFour,
  SampleTwentyFive,
  SampleTwentySix,
  SampleTwentySeven,
  SampleTwentyEight,
  SampleTwentyNine,
  SampleThirty,
  SampleThirtyOne,
  SampleThirtyTwo,
  SampleThirtyThree,
];
</script>

<template>
  <template v-if="isVisible">
    <div v-for="(sample, index) in samples" :key="index" class="box">
      <component :is="sample" />
    </div>
  </template>
  <div v-else class="tombstone">
    🪦 모든 컴포넌트가 파괴되었습니다. (F12 콘솔 창을 확인해 보세요!)
  </div>

  <div class="control-panel">
    <button class="toggle-btn" @click="isVisible = !isVisible">
      <span v-if="isVisible">🔴 모든 컴포넌트 파괴하기 (v-if="false")</span>
      <span v-else>🟢 모든 컴포넌트 다시 살리기 (v-if="true")</span>
    </button>
  </div>
</template>

<style scoped>
.control-panel {
  text-align: center;
  margin: 20px 0;
}
.toggle-btn {
  padding: 12px 24px;
  font-size: 16px;
  font-weight: bold;
  border-radius: 8px;
  border: none;
  background-color: #ff7675;
  color: white;
  cursor: pointer;
}
.tombstone {
  text-align: center;
  padding: 50px;
  font-size: 18px;
  color: #fff;
  background-color: #2d3436;
  border-radius: 8px;
  margin-top: 20px;
}
.box {
  padding: 20px;
  margin: 12px 0;
  border: 1px solid #ddd;
  border-radius: 8px;
  background: #000;
}
.box :deep(h2) {
  color: #fff; /* 검은 배경이라 글씨는 흰색 */
  padding-bottom: 8px; /* 글자와 밑줄 사이 간격 */
  border-bottom: 2px solid #ddd; /* 이게 밑줄 */
  margin-bottom: 16px; /* 밑줄과 아래 내용 사이 간격 */
}
</style>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
