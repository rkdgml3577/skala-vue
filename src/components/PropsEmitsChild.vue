<script setup>
import { ref } from "vue"; // 추가: 입력창 데이터를 담을 ref 불러오기

// 1. 상위 컴포넌트로부터 주입받을 데이터 (Props)
defineProps({
  parentData: {
    type: String,
    required: true,
  },
});

// 2. 상위 컴포넌트로 송신할 커스텀 이벤트 식별자 등록
const emit = defineEmits(["update-request"]);

// 추가: 사용자가 직접 입력할 텍스트를 담는 반응형 변수[cite: 1]
const childInputText = ref("");

// 3. 버튼 클릭 시, 고정된 텍스트 대신 '사용자가 입력한 값'을 부모로 보냄
const sendNotification = () => {
  emit("update-request", childInputText.value);
  childInputText.value = ""; // (선택) 부모에게 전송한 후 입력창 비워주기
};
</script>

<template>
  <div class="child-container">
    <h2>하위 컴포넌트 (Child)</h2>
    <p>
      수신된 Props 데이터: <strong>{{ parentData }}</strong>
    </p>
    <br />

    <!-- 추가: 자식 쪽에서 글자를 입력할 수 있는 v-model 입력창[cite: 1] -->
    <input
      type="text"
      v-model="childInputText"
      placeholder="부모에게 보낼 메시지 입력"
      style="padding: 6px; margin-right: 8px"
    />
    <button @click="sendNotification">상위 컴포넌트로 갱신 요청 (Emit)</button>
  </div>
</template>

<style scoped>
.child-container {
  border: 2px dashed #fdfdfd;
  padding: 20px;
  background-color: #000;
  border-radius: 6px;
}
</style>
