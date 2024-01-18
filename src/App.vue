<script setup lang="ts">
import { ref, computed } from "vue";
import Card from "./components/Card.vue";
import { questions } from "./data/questions";
import { Question } from "./types";

const score = ref(0);
const questionIndex = ref(0);
const question = computed(() => {
  return questions[questionIndex.value] as Question;
});
const isFinished = computed(() => {
  if (questionIndex.value === questions.length - 1) return true;
});
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
      <div class="flex-col">
        <div class="text-3xl font-extrabold text-accent">
          Question: {{ questionIndex + 1 }}/10
        </div>
        <div class="text-3xl font-extrabold text-green-700">
          Score: {{ score }}
        </div>
      </div>
    </header>
    <div class="flex items-center justify-center flex-1 bg-gray-200">
      <Card
        @increaseScore="() => score++"
        @showNext="() => questionIndex++"
        :question="question"
        :isFinished="isFinished"
      ></Card>
    </div>
  </div>
</template>

<style scoped></style>
