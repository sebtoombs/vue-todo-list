<template>
  <div :class="style.TodoItem">
    <div class="flex items-center justify-center">
      <input type="checkbox" />
    </div>
    <div class="text-lg font-medium py-2 flex items-center">
      <slot></slot>
    </div>
    <div class="flex items-center"></div>
    <div class="flex items-center">
      <button
        type="button"
        :class="style.DeleteButton"
        aria-label="Remove todo item"
        @click="() => $props.removeTodo($props.id)"
      >
        <svg
          stroke="currentColor"
          fill="currentColor"
          stroke-width="0"
          viewBox="0 0 24 24"
          aria-hidden="true"
          focusable="false"
          height="1em"
          width="1em"
          xmlns="http://www.w3.org/2000/svg"
        >
          <g>
            <path fill="none" d="M0 0h24v24H0z"></path>
            <path
              d="M17 6h5v2h-2v13a1 1 0 0 1-1 1H5a1 1 0 0 1-1-1V8H2V6h5V3a1 1 0 0 1 1-1h8a1 1 0 0 1 1 1v3zm1 2H6v12h12V8zM9 4v2h6V4H9z"
            ></path>
          </g>
        </svg>
      </button>
    </div>
  </div>
</template>

<script setup>
import style from "./TodoItem.module.css";
</script>

<script>
export default {
  name: "TodoItem",
  props: {
    id: {
      type: [String, Number],
    },
    type: {
      type: String,
      default: "button",
    },
    removeTodo: {
      type: Function,
    },
  },
  // methods: {
  //   onClick(event) {
  //     this.$emit("click", event);
  //   },
  // },
};
</script>
