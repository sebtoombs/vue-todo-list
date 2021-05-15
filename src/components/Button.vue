<template>
  <button
    :type="type"
    @click="onClick"
    class="
      px-4
      py-1
      rounded-md
      bg-gray-300
      text-black
      font-medium
      hover:bg-gray-400
      transition
      duration-200
      min-h-input
      outline-none
      focus:ring
      focus:outline-none
    "
    :class="{
      'bg-green-500 text-white hover:bg-green-600': colorScheme === 'green',
    }"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    type: {
      type: String,
      default: "button",
    },
    colorScheme: {
      type: String,
    },
  },
  methods: {
    onClick(event) {
      this.$emit("click", event);
    },
  },
};
</script>
