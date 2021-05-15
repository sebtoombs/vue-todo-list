<!--
This is just me having a play around with
some React style component type stuff.
We're just passing the props to the classname which
gives us all the tailwind goodness.
There's really not much point in it, it was more
of an exercise
-->

<template>
  <div :class="classArray"><slot></slot></div>
</template>

<script>
const boxPropKeys = [
  "p",
  "px",
  "py",
  "m",
  "mx",
  "my",
  "d",
  "bg",
  "color",
  "items",
  "justify",
  "maxW",
];
</script>

<script setup>
import { defineProps } from "vue";

const props = defineProps(
  boxPropKeys.reduce((obj, key) => ({ ...obj, [key]: [Number, String] }), {})
);

const classArray = Object.keys(props)
  .filter((propKey) => !!boxPropKeys.find((k) => propKey === k))
  .map((propKey) => `${propKey}-${props[propKey]}`);
</script>
