<script setup lang="ts">
import { ref, computed } from "vue";
import Card from "./components/Card.vue";
import { questions } from "./data/questions";
import { Question } from "./types";
import { Button } from "@/components/ui/button";

const score = ref(0);
const questionIndex = ref(0);
const question = computed(() => {
  return questions[questionIndex.value] as Question;
});
const isFinished = computed(() => {
  if (questionIndex.value === questions.length - 1) return true;
  if (isSubmitted) return false;
});
const isSubmitted = ref(false);

function startAgain() {
  isSubmitted.value = false;
  questionIndex.value = 0;
  score.value = 0;
}
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
      <div
        v-if="isSubmitted"
        class="w-[817px]h-auto bg-white rounded-xl py-20 px-32"
      >
        <h1
          class="flex justify-center mb-4 text-3xl font-bold text-center text-accent-foreground"
        >
          Congratulations!
        </h1>

        <span
          class="flex justify-center text-xl font-bold text-center text-accent"
          >You gave {{ score }} correct answers out of
          {{ questions.length }}</span
        >
        <Button variant="start" @click="startAgain">Start again</Button>
      </div>
      <Card
        v-if="!isSubmitted"
        @submit="() => (isSubmitted = true)"
        @increaseScore="() => score++"
        @showNext="() => questionIndex++"
        :question="question"
        :isFinished="isFinished"
      ></Card>
    </div>
  </div>
</template>

<style scoped></style>
