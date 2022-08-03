<script setup>
import { ref } from "vue";

defineProps({
  msg: String,
});
const text = ref("");
const type = ref("");
const check = ref(false);
const country = ref("");
function test() {
  console.log(country.value);
}
function handleInput() {
  return check.value ? "thank-you" : "";
}
function handleSubmit() {
  window.open(
    `https://staging--medallia-regional-staging.netlify.app/${country.value
      .toLowerCase()
      .trim()}/${type.value.trim()}/${text.value.trim()}/${handleInput()}`
  );
}
</script>

<template>
  <h1 class="py-6 text-6xl text-white">{{ msg }}</h1>
  <form @submit.prevent="handleSubmit" class="flex flex-col gap-4 text-center">
    <label for="country">Country:</label>

    <select name="country" id="country" v-model="country" @change="test">
      <option value="BR">BRAZIL</option>
      <option value="LATAM">LATAM</option>
      <option value="ES">SPAIN</option>
      <option value="KR">KOREAN</option>
      <option value="JP">JAPAN</option>
      <option value="FR">FRANCE</option>
      <option value="IT">ITALY</option>
      <option value="DE">GERMANY</option>
    </select>
    <label for="type">Type:</label>
    <input
      id="type"
      name="type"
      type="text"
      class="p-4 px-64 text-center text-green-400"
      v-model="type"
    />
    <label for="input">UID:</label>
    <input
      id="input"
      name="input"
      type="text"
      class="p-4 px-64 text-center text-green-400"
      v-model="text"
    />
    <label for="checkbox">Skip Form?</label>
    <input
      id="checkbox"
      name="checkbox"
      type="checkbox"
      class="p-4 px-64 text-center text-green-400"
      v-model="check"
      @input="handleInput"
    />
    <button
      type="submit"
      class="w-1/3 py-4 mx-auto bg-green-400 hover:bg-green-400/75 active:bg-green-400/25"
    >
      Submit
    </button>
  </form>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
