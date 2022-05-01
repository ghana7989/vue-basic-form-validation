<template>
  <my-button background="red" color="black" disabled="false" />
  <my-input
    name="Username"
    :rules="{
      required: true,
      minLength: 3,
    }"
    :value="username.value"
    :error="username.error"
    @update="update"
  />
  <my-input
    name="Password"
    :rules="{
      required: true,
      minLength: 5,
    }"
    :value="password.value"
    :error="password.error"
    @update="update"
  />
</template>

<script>
import MyButton from "./components/MyButton.vue";
import MyInput from "./components/MyInput.vue";
export default {
  components: {
    MyButton,
    MyInput,
  },
  data() {
    return {
      username: {
        error: "",
        value: "pavan",
      },
      password: {
        error: "",
        value: "pass",
      },
    };
  },
  methods: {
    update({ name, value, error }) {
      this[name]["value"] = value;
      this[name]["error"] = error;
    },
  },
};
</script>

<style scoped></style>
