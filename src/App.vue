<script setup lang="ts">
import { ref } from "vue";
import Card from "./components/Card.vue";

const count = ref();
</script>

<template>
  <div class="flex flex-col h-screen">
    <header
      class="h-[131px] w-full justify-between flex pl-20 pr-24 items-center"
    >
      <div class="flex text-3xl font-extrabold">
        <span class="text-accent-logo"> js </span>
        <span class="text-accent-foreground">Quiz</span>
      </div>
      <div class="text-3xl font-extrabold text-accent">
        Count: {{ count }}/10
      </div>
    </header>
    <div class="flex items-center justify-center flex-1 bg-gray-200">
      <Card></Card>
    </div>
  </div>
</template>

<style scoped></style>
