<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
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
];
</script>

<template>
  <div v-for="(sample, index) in samples" :key="index" class="box">
    <component :is="sample" />
  </div>
</template>

<style scoped>
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
