<script setup>
import { ref } from "vue";
const count = ref(0);

// 메서드 핸들러 함수 정의
const showAlert = () => {
  alert("함수가 성공적으로 호출되었습니다!");
};

// 3) event 객체 받기 — e.target 활용
const showTarget = (e) => {
  // 클릭된 태그 이름과 버튼에 쓰인 글자를 확인
  alert(`태그: ${e.target.tagName}, 글자: ${e.target.textContent}`);
};

// 4) 마우스 좌표 — e.clientX / e.clientY 활용
const mouseX = ref(0);
const mouseY = ref(0);
const trackMouse = (e) => {
  mouseX.value = e.clientX;
  mouseY.value = e.clientY;
};

// 5) 키보드 입력 — e.key 활용
const lastKey = ref("");
const showKey = (e) => {
  lastKey.value = e.key; // 누른 키의 실제 문자값
};
</script>

<template>
  <div class="practice-section">
    <h2>v-on 이벤트 핸들링 기초</h2>

    <h3>1) 인라인 연산 처리</h3>
    <p>현재 카운트: {{ count }}</p>
    <button @click="count++">1씩 증가</button>

    <h3>2) 스크립트 함수 호출</h3>
    <button @click="showAlert">알림창 띄우기</button>

    <h3>3) event 객체 받기 (e.target)</h3>
    <button @click="showTarget">내 정보 보기</button>

    <h3>4) 마우스 좌표 추적 (e.clientX / e.clientY)</h3>
    <div class="mouse-area" @mousemove="trackMouse">
      이 박스 안에서 마우스를 움직여보세요
      <p>X: {{ mouseX }}, Y: {{ mouseY }}</p>
    </div>

    <h3>5) 키보드 입력 감지 (e.key)</h3>
    <input @keyup="showKey" placeholder="아무 키나 눌러보세요" />
    <p>마지막으로 누른 키: {{ lastKey }}</p>
  </div>
</template>

<style scoped>
.mouse-area {
  padding: 20px;
  margin: 8px 0;
  border: 1px dashed #888;
  border-radius: 8px;
}
</style>
