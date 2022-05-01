<template>
  <button v-bind:style="{ background, color }" v-bind:disabled="disabled">
    Click Me
  </button>
</template>

<script>
export default {
  props: {
    background: {
      type: String,
      default: "#000",
    },
    color: {
      type: String,
      default: "#fff",
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style scoped></style>
