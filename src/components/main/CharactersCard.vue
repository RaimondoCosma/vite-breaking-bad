<script>
import { store } from "../../store.js";
import AppCard from "../commons/AppCard.vue";
import LoadingSpinner from "../commons/LoadingSpinner.vue";

export default {
  name: "CharactersCard",
  emits: {
    search: null,
  },
  components: {
    AppCard,
    LoadingSpinner,
  },
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <!-- Parte input option -->
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
  <!-- /Parte input option -->
  <!-- Sezione card -->
  <section class="row container-lg m-auto bg-white">
    <div class="w-100 text-white p-3 mt-5 mb-3 my-info">
      Found {{ store.serieCharacters.length }} Characters
    </div>
    <AppCard
      v-if="store.serieCharacters.length !== 0"
      v-for="character in store.serieCharacters"
      class="my-card"
      :character="character"
    />
    <div v-else>
      <LoadingSpinner />
    </div>
  </section>
  <!-- /Sezione card -->
</template>

<style lang="scss" scoped>
.my-info {
  background-color: #212529;
}
.my-card {
  width: 100%;
  margin: 0 0.625rem;
  @include media-breakpoint-up(sm) {
    width: calc(100% / 2 - 1.25rem);
  }
  @include media-breakpoint-up(md) {
    width: calc(100% / 3 - 1.25rem);
  }
  @include media-breakpoint-up(lg) {
    width: calc(100% / 4 - 1.25rem);
  }
  @include media-breakpoint-up(xl) {
    width: calc(100% / 5 - 1.25rem);
  }
}
</style>
