<template>
  <h1>Computed 計算屬性1</h1>
  <!-- 一般方法 -->
  <!-- <h3>{{ numFormat() }}</h3> -->
  <!-- 使用 computed -->
  <h3>{{ numFormat }}</h3>

  <!-- 使用 function numFormat，即使在 input text輸入，也會不斷重新 render -->
  <input type="text" v-model="text" /><br /><br />
  <input type="number" v-model="num" />
</template>

<script setup>
// 使用 cpmputed
import { computed, ref } from "vue";
const num = ref(0);

// 一般方法
// const num = 0.6;
// const numFormat = () => {
//   if (Number.isNaN(num)) {
//     return num;
//   } else {
//     return `${num * 100}%`;
//   }
// };

// 使用 cpmputed，computed 裏面純計算就好，不要再寫別的東西
// 不要再重新對 computed function 賦值
const numFormat = computed(() => {
  console.log("change");
  if (Number.isNaN(num.value)) return num;
  return `${num.value * 100}%`;
});
</script>

<style></style>
