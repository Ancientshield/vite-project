<template>
  <div>
    <!-- 使用 :key="" 綁定，會重新創建 element 觸發 render -->
    <h1 class="test-cls" :key="test">{{ test }}</h1>
  </div>
  <!-- for d in dataList, 用v-bind:key綁定 key -->
  <!-- <p v-for="(d, i) in dataList" v-bind:key="i">{{ d }}</p> -->

  <!-- 可簡寫 :key="" 綁定每一個 array 值 -->
  <p v-for="(d, i, index) in dataList" :key="d">
    <span v-if="i !== 'key3'"> index:{{ index }} {{ i }}: {{ d }} </span>
  </p>
</template>

<script setup>
import { ref } from "vue";
const test = ref("test");
const dataList = { key1: "a", key2: "b", key3: "c", key4: "d" };

setTimeout(() => {
  test.value = "apple";
}, 2000);
</script>

<style>
.test-cls {
  font-size: 40px;
  animation: openIn 1s ease-in-out;
}

@keyframes openIn {
  0% {
    opacity: 0;
    transform: translateY(20px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
