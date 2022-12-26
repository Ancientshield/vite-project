<template>
  <button v-on:click="changeView(1)">顯示單向綁定</button>
  <!-- <button v-on:click="changeView(2)">顯示雙向綁定</button> -->
  <button @click="changeView(2)">顯示雙向綁定</button>
  <button @click="changeView(10000)">沒畫面</button>

  <div class="container-1" v-if="view === 1">
    <h1>資料單向綁定</h1>
    {{ data }}
  </div>

  <div class="container-2" v-if="view === 2">
    <h1>資料雙向綁定</h1>
    <input type="text" v-model="text" />
    <p>{{ text }}</p>
  </div>

  <!-- <div v-if="view !== 1 && view !== 2">沒畫面</div> -->
  <!-- v-show 是用 css 的 display:none 隱藏，v-if 是真的 render 讓 DOM 消失 -->
  <!-- 數量很多時，使用 v-if 效能較好，因為不用渲染一大堆真實 DOM-->
  <div v-show="view !== 1 && view !== 2">沒畫面</div>
</template>

<script setup>
// 資料雙向綁定需要引入ref
// import {ref} from "@vue/reactivity"
import { ref } from "vue";
// 資料驅動頁面
const data = "Hello Vue";
const text = ref("123");
const view = ref(1);
const changeView = (index) => {
  view.value = index;
};
</script>

<style>
.container-1 {
  border: 2px red solid;
}
.container-2 {
  border: 2px skyblue solid;
}
</style>
