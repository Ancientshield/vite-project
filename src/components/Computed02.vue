<template>
  <h1>Computed 計算屬性2</h1>
  <input type="text" v-model="fullName" />
  <p>{{ firstName }}</p>
  <p>{{ lastName }}</p>
</template>

<script setup>
import { computed, ref } from "vue";

const firstName = ref("Jone");
const lastName = ref("Doe");

const fullName = computed({
  get() {
    return `${firstName.value} ${lastName.value}`;
  },
  set(newName) {
    const [newFirstName, newLastName] = newName.split(" ");
    firstName.value = newFirstName;
    lastName.value = newLastName;
  },
});
</script>

<style></style>
