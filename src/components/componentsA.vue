<template>
  <h1>資料單向綁定</h1>
  {{ data }}
  <h1>資料雙向綁定</h1>
  <input type="text" v-model="text" />
  <p>{{ text }}</p>
</template>

<script setup>
// 資料雙向綁定需要引入ref
// import {ref} from "@vue/reactivity"
import { ref } from "vue";
// 資料驅動頁面
const data = "Hello Vue";
const text = ref("123");
</script>

<style></style>
