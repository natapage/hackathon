<script setup lang="ts">
import { ref } from "vue";

const count = ref();
</script>

<template>
  <header class="h-[131px] w-full">
    <div>js Quiz</div>
    <div>Count: {{ count }}/10</div>
  </header>
  <div class="h-screen w-full bg-gray-200"></div>
</template>

<style scoped></style>
