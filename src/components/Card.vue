<script setup lang="ts">
import { ref, defineProps } from "vue";
import { Label } from "../components/ui/label";
import { Button } from "@/components/ui/button";
import { RadioGroup, RadioGroupItem } from "@/components/ui/radio-group";

const userAnswer = ref("");

const props = defineProps({
  question: Object,
  isFinished: Boolean,
});

const emit = defineEmits(["show-next", "increase-score", "submit"]);

function onClickNext() {
  if (
    userAnswer.value === props.question?.variants[props.question.answerIndex]
  ) {
    emit("increase-score");
  }
  emit("show-next");
}
</script>

<template>
  <div class="w-[817px] h-auto bg-white rounded-xl py-20 px-32">
    <h1 class="flex justify-center text-3xl font-bold text-accent">
      {{ props.question?.question }}
    </h1>
    <RadioGroup v-model="userAnswer" class="mt-20">
      <div
        v-for="(variant, index) in props.question?.variants"
        :key="index"
        class="flex items-center space-x-2"
      >
        <RadioGroupItem :id="variant" :value="variant" />
        <Label :for="variant">{{ variant }}</Label>
      </div>
    </RadioGroup>
    <div class="flex justify-end gap-10 mt-20">
      <Button
        type="Submit"
        @click="() => $emit('submit')"
        :disabled="!isFinished"
        variant="submit"
        >Submit</Button
      >
      <Button :disabled="isFinished" @click="onClickNext">Next</Button>
    </div>
  </div>
</template>

<style scoped></style>
