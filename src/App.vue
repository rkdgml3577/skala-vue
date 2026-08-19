<!-- <script setup>
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
</style> -->

<script setup>
import { ref } from "vue";
import SearchBox from "./components/SearchBox.vue";
import WeatherCard from "./components/WeatherCard.vue";
import StatusBar from "./components/Statusbar.vue";

const weatherList = ref([
  { id: "city_01", name: "서울", temp: 28, status: "맑음" },
  { id: "city_02", name: "수원", temp: 24, status: "비" },
  { id: "city_03", name: "부산", temp: 26, status: "구름" },
  { id: "city_04", name: "대구", temp: 31, status: "맑음" },
  { id: "city_05", name: "제주", temp: 22, status: "바람" },
  { id: "city_06", name: "광주", temp: 29, status: "맑음" },
  { id: "city_07", name: "대전", temp: 27, status: "비" },
  { id: "city_08", name: "강릉", temp: 30, status: "맑음" },
  { id: "city_09", name: "울산", temp: 25, status: "구름" },
  { id: "city_10", name: "인천", temp: 23, status: "비" },
]);

const searchCity = ref("");
const searchResult = ref("");
const selectedCity = ref("");

const onSearch = () => {
  searchResult.value = searchCity.value;
};

const onSelect = (name) => {
  selectedCity.value = name;
};

const onDetail = (city) => {
  window.alert(`${city.name}의 현재 날씨는 [${city.status}] 상태입니다.`);
};
</script>

<template>
  <div class="weather-app">
    <h1 class="app-title">🌤️ 날씨 (Mockup)</h1>

    <SearchBox v-model="searchCity" :result="searchResult" @search="onSearch" />

    <section class="card-list">
      <h2 class="section-title">📍 지역별 날씨 현황</h2>

      <WeatherCard
        v-for="city in weatherList"
        :key="city.id"
        :city="city"
        @select="onSelect"
        @detail="onDetail"
      />
    </section>

    <StatusBar :selected-city="selectedCity" />
  </div>
</template>

<style scoped>
.weather-app {
  max-width: 480px;
  margin: 24px auto;
  padding: 20px;
  font-family:
    "Pretendard",
    -apple-system,
    sans-serif;
  color: #2d3436;
}
.app-title {
  font-size: 22px;
  margin-bottom: 20px;
}
.section-title {
  font-size: 16px;
  padding-bottom: 8px;
  border-bottom: 2px solid #dfe6e9;
  margin-bottom: 14px;
}
</style>
