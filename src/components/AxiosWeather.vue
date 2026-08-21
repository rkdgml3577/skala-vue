<script setup>
import { ref } from "vue";
import axios from "axios";

const weatherData = ref(null);
const isLoading = ref(false);

// 💡 드롭다운에 뿌릴 도시 목록
// value는 OpenWeatherMap이 알아듣는 영문 도시명 + 국가코드 형식입니다.
const cityList = [
  { name: "광주", query: "Gwangju,KR" },
  { name: "서울", query: "Seoul,KR" },
  { name: "인천", query: "Incheon,KR" },
  { name: "대전", query: "Daejeon,KR" },
  { name: "대구", query: "Daegu,KR" },
  { name: "부산", query: "Busan,KR" },
  { name: "울산", query: "Ulsan,KR" },
  { name: "세종", query: "Sejong,KR" },
  { name: "수원", query: "Suwon,KR" },
  { name: "청주", query: "Cheongju,KR" },
  { name: "전주", query: "Jeonju,KR" },
  { name: "창원", query: "Changwon,KR" },
  { name: "춘천", query: "Chuncheon,KR" },
  { name: "강릉", query: "Gangneung,KR" },
  { name: "제주", query: "Jeju,KR" },
];

// v-model로 select와 묶이는 반응형 상태. 기본값은 광주.
const selectedCity = ref("Gwangju,KR");

const handleFetchWeather = async () => {
  isLoading.value = true;

  const API_KEY = "8964edc63b366d27b5b728b7976570b7";
  // 💡 lat/lon 대신 q(도시명)로 조회합니다.
  //    좌표로 부르면 가장 가까운 관측 지점의 마을 이름(예: Yach'on)이 튀어나오지만,
  //    q로 부르면 우리가 아는 도시 이름 그대로 응답에 담깁니다.
  const URL = `https://api.openweathermap.org/data/2.5/weather?q=${selectedCity.value}&appid=${API_KEY}&units=metric&lang=kr`;

  try {
    // 비동기 통신 가동: 서버에서 데이터를 다 가져올 때까지 await로 기다립니다.
    const response = await axios.get(URL);
    // fetch와 달리 .json() 변환 과정 없이 response.data에 알맹이가 즉시 담깁니다.
    console.log("Axios 통신 응답 전체 객체:", response);
    console.log("백엔드가 준 핵심 날씨 데이터(JSON):", response.data);
    weatherData.value = response.data;
  } catch (error) {
    // 4xx, 5xx 에러나 네트워크 오프라인 시 자동으로 이 catch 영역으로 튕겨 들어옵니다.
    console.error("통신 중 에러가 발생했습니다:", error);
    // 404면 도시명을 못 찾은 경우, 401이면 API 키 문제입니다.
    if (error.response?.status === 404) {
      alert("해당 도시를 찾지 못했습니다. 도시명을 확인하세요.");
    } else {
      alert(
        "데이터를 가져오지 못했습니다. API 키 활성화 여부나 주소를 확인하세요.",
      );
    }
  } finally {
    isLoading.value = false;
  }
};
</script>

<template>
  <div class="practice-section">
    <h2>⚡ Axios 통신 검증</h2>

    <div class="control-zone">
      <select v-model="selectedCity" class="city-select">
        <option v-for="city in cityList" :key="city.query" :value="city.query">
          {{ city.name }}
        </option>
      </select>
      <button @click="handleFetchWeather" :disabled="isLoading">
        {{ isLoading ? "데이터 로딩 중..." : "실시간 날씨 데이터 당겨오기" }}
      </button>
    </div>

    <div v-if="weatherData" class="result-card">
      <p>
        📍 위치: <strong>{{ weatherData.name }}</strong>
      </p>
      <p>
        🌡️ 현재 기온: <strong>{{ weatherData.main.temp }}°C</strong> (정상 섭씨
        변환 완료)
      </p>
      <p>
        ☁️ 날씨 상태: <strong>{{ weatherData.weather[0].description }}</strong>
      </p>
      <p>
        💧 습도: <strong>{{ weatherData.main.humidity }}%</strong>
      </p>
    </div>
    <div v-else>
      <p>아직 가져온 데이터가 없습니다. 버튼을 눌러 통신을 가동하세요.</p>
    </div>
  </div>
</template>

<style scoped>
.control-zone {
  display: flex;
  gap: 8px;
  margin-bottom: 15px;
}
.city-select {
  padding: 8px 12px;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  font-size: 14px;
  cursor: pointer;
}
.result-card {
  background: #000;
  padding: 15px;
  border-radius: 8px;
  border: 1px solid #e2e8f0;
  line-height: 1.8;
}
.result-card strong {
  color: #0284c7;
}
</style>
