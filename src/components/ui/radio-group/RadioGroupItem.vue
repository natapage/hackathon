<script setup lang="ts">
import {
  RadioGroupIndicator,
  RadioGroupItem,
  type RadioGroupItemProps,
} from "radix-vue";
import { Circle } from "lucide-vue-next";
import { cn } from "@/lib/utils";

const props = defineProps<RadioGroupItemProps & { class?: string }>();
</script>

<template>
  <RadioGroupItem
    v-bind="props"
    :class="
      cn(
        'aspect-square h-4 w-4 rounded-full bg-accent-foreground cursor-pointer flex justify-center items-center disabled:cursor-not-allowed disabled:opacity-50',
        props.class
      )
    "
  >
    <RadioGroupIndicator
      :class="
        cn(
          'flex items-center justify-center w-2 h-2 bg-white border-none rounded-full',
          props.class
        )
      "
    >
    </RadioGroupIndicator>
  </RadioGroupItem>
</template>
