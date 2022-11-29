<script>
import { store } from "../../store.js";

export default {
  name: "OptionValue",
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div class="container-lg mt-4 mb-3">
    <select
      class="form-select w-auto"
      aria-label="Default select example"
      v-model="store.searchValue"
      @change="$emit('search')"
    >
      <option value="" selected>Select Category</option>
      <option value="Breaking Bad">Breaking Bad</option>
      <option value="Better Call Saul">Better Call Saul</option>
    </select>
  </div>
</template>

<style lang="scss" scoped></style>
