<script setup>
import { ref, onMounted, onUpdated, onUnmounted } from "vue";

const count = ref(0);
let timerId = null; // 실시간 타이머 메모리 주소를 담을 변수

// 1. 생성 (Creation) 단계
console.log("1. [setup] 컴포넌트가 메모리에 생성되었습니다. (DOM 접근 불가능)");

// 2. 부착 (Mounting) 단계
onMounted(() => {
  console.log("2. [onMounted] 화면에 완벽히 부착되었습니다!");
  // 3초마다 숫자가 자동으로 올라가는 타이머 가동
  timerId = setInterval(() => {
    count.value++;
  }, 3000);
});

// 3. 갱신 (Updating) 단계
onUpdated(() => {
  console.log(
    `3. [onUpdated] 데이터가 변경되어 화면을 새로 그렸습니다. (현재 count: ${count.value})`,
  );
});

// 4. 소멸 (Unmounting) 단계
onUnmounted(() => {
  // 잘려있던 코드 수정 완료: 메모리 누수 방지를 위해 타이머 해제
  clearInterval(timerId);
  console.log(
    "4. [onUnmounted] 컴포넌트가 파괴되어 타이머를 안전하게 종료했습니다.",
  );
});
</script>

<template>
  <div class="lifecycle-box">
    <h3>⏱️ 라이프사이클 훅 흐름 탐색기</h3>
    <div class="timer-content">
      <p>실시간 타이머 카운트: {{ count }}</p>
      <!-- 수동으로 숫자를 올려 onUpdated 훅을 강제 실행시킵니다 -->
      <button @click="count++">수동으로 숫자 올리기</button>
    </div>
  </div>
</template>

<style scoped>
.lifecycle-box {
  margin-top: 20px;
  border-radius: 8px;
  overflow: hidden;
  font-family: sans-serif;
}

.lifecycle-box h3 {
  margin: 0;
  padding: 12px;
  font-size: 16px;
  color: #2c3e50;
}

.timer-content {
  background-color: #e0f7fa; /* 이미지와 비슷한 민트색 배경 */
  padding: 30px;
  text-align: center;
  border-radius: 8px;
}

.timer-content p {
  margin: 0 0 10px 0;
  font-size: 15px;
  color: #34495e;
}

.timer-content button {
  padding: 8px 16px;
  border: 1px solid #bdc3c7;
  background-color: #fff;
  border-radius: 4px;
  cursor: pointer;
  font-size: 13px;
}

.timer-content button:hover {
  background-color: #f1f2f6;
}
</style>
