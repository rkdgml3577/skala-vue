<script setup>
import { ref } from "vue";
import PropsEmitsChild from "./PropsEmitsChild.vue";

// 1. 상위 컴포넌트의 로컬 반응형 상태 정의
const message = ref("Parent 초기 메시지");

// 2. 하위 컴포넌트의 커스텀 이벤트를 수신했을 때 실행될 핸들러 함수
const handleUpdateRequest = (newValue) => {
  message.value = newValue;
};
</script>

<template>
  <div class="practice-section">
    <h2>Props & Emits 무한 테스트</h2>
    <div class="parent-container">
      <h2>상위 컴포넌트 (Parent)</h2>

      <!-- 추가: 부모 쪽에서 데이터를 실시간으로 바꿔보는 v-model 입력창[cite: 1] -->
      <label>부모 데이터 강제 수정: </label>
      <input type="text" v-model="message" style="padding: 6px" />

      <p>
        현재 로컬 데이터(State): <strong>{{ message }}</strong>
      </p>
      <br />
      <PropsEmitsChild
        :parent-data="message"
        @update-request="handleUpdateRequest"
      />
    </div>
  </div>
</template>

<style scoped>
.parent-container {
  border: 2px solid #ffffff;
  padding: 20px;
  background-color: #f000;
  margin: 0 auto;
  border-radius: 8px;
}
</style>
