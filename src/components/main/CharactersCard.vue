<script>
import { store } from "../../store.js";
import AppCard from "../commons/AppCard.vue";
import OptionValue from "../commons/OptionValue.vue";
import LoadingSpinner from "../commons/LoadingSpinner.vue";

export default {
  name: "CharactersCard",
  emits: {
    search: null,
  },
  components: {
    AppCard,
    LoadingSpinner,
    OptionValue,
  },
  data() {
    return {
      store,
    };
  },
  computed: {
    getArrayLength() {
      return this.store.serieCharacters.length;
    },
  },
};
</script>

<template>
  <OptionValue @search="$emit('search')" />
  <section class="row container-lg m-auto bg-white">
    <!-- Tiene conto del numero delle card -->
    <div class="w-100 text-white p-3 mt-5 mb-3 my-info">
      Found {{ getArrayLength }} Characters
    </div>
    <!-- /Tiene conto del numero delle card -->
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
