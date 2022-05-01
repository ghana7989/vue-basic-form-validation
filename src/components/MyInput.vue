<template>
  <div class="label">
    <div class="error">{{ error }}</div>
    <label :for="name">{{ name }}</label>
  </div>
  <input type="text" :id="name" :value="value" @input="input" />
</template>

<script>
export default {
  emits: ["update"],
  props: {
    name: {
      type: String,
      required: true,
    },
    value: {
      type: String,
      required: true,
    },
    error: {
      type: String,
    },
    rules: {
      type: Object,
    },
  },
  methods: {
    input($event) {
      this.$emit("update", {
        value: $event.target.value,
        name: this.name.toLowerCase(),
        error: this.validate($event.target.value),
      });
    },
    validate(value) {
      if (this.rules.required && value.length === 0) {
        return "This field is required";
      } else if (this.rules.minLength && value.length < this.rules.minLength) {
        return `Minimum length should be  ${this.rules.minLength}`;
      }
      return "";
    },
  },
};
</script>

<style scoped>
.error {
  color: red;
}
</style>
