<template>
  <h1>watch</h1>
  <input type="text" v-model="text" :style="dynamicStyle" />
</template>

<script setup>
import { reactive, ref } from "@vue/reactivity";
import { watch, watchEffect } from "@vue/runtime-core";

const text = ref("");

const dynamicStyle = reactive({
  color: "red",
  fontSize: "20px",
  transition: "ease-in-out 0.2s",
});

watch(text, (newData) => {
  if (newData.length % 2 === 0) {
    dynamicStyle.color = "skyblue";
    dynamicStyle.fontSize = "30px";
  } else {
    dynamicStyle.color = "red";
    dynamicStyle.fontSize = "20px";
  }
});
</script>

<style></style>
