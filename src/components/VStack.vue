<template>
  <div :class="style.VStack" :style="{ '--vstack-spacing': props.spacing }">
    <slot></slot>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
import style from "./VStack.module.css";

const props = defineProps({
  spacing: [Number, String],
});
</script>
