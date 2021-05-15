<template>
  <input
    :id="id"
    :type="type"
    :value="modelValue"
    @input="updateInput"
    class="
      w-full
      px-4
      py-1
      rounded-md
      border border-solid border-gray-200
      min-h-input
      outline-none
      focus:ring
    "
  />
</template>

<script>
// Couldn't figure out how to do this with the new experimental
// syntax. The docs are... limited.
export default {
  name: "Input",
  props: {
    id: {
      type: String,
      default: "",
    },
    modelValue: {
      type: [String, Number],
      default: "",
    },
    type: {
      type: String,
      default: "text",
    },
  },
  methods: {
    updateInput(event) {
      this.$emit("update:modelValue", event.target.value);
    },
  },
};
</script>
