<template>
  <h1>watchEffect</h1>
  <input type="text" v-model="text.levels.txt" /><br />
  <input type="text" v-model="text.label" /><br />
</template>

<script setup>
import { reactive, ref } from "@vue/reactivity";
import { watch, watchEffect } from "@vue/runtime-core";

// 用 reactive，不要用 ref（不知為何不能用），watch 就可以不用加 value
const text = reactive({
  levels: {
    txt: "",
  },
  label: "123",
});

// watch cbFk 會回傳：1.新值 2.舊值 3.{deep:true/false}會監聽整個物件造成效能浪費，盡量不要開
// watch(
//   [() => text.value.levels.txt, () => text.value.label],
//   (newData) => {
//     console.log(newData);
//   },
//   { deep: true }
// );

// watch 好像會造成 watchEffect 失效
// watch([() => text.levels.txt, () => text.label], (newData) => {
//   console.log(newData);
// });

// 在 123 的 input 輸入 stop 後就會停止監聽
const stop = watchEffect(() => {
  console.log(text.levels.txt, text.label);
  if (text.label === "stop") stop();
});
</script>

<style></style>
