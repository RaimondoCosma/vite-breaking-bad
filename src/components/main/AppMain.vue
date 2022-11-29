<script>
import axios from "axios";
import { store } from "../../store.js";

import CharactersCard from "./CharactersCard.vue";

export default {
  name: "AppMain",
  components: {
    CharactersCard,
  },
  data() {
    return {
      store,
    };
  },
  methods: {
    getCards() {
      axios
        .get("https://www.breakingbadapi.com/api/characters", {
          params: {
            category: this.store.searchValue,
          },
        })
        .then((resp) => {
          this.store.serieCharacters = resp.data;
        });
    },
  },
  created() {
    this.getCards();
  },
};
</script>

<template>
  <main>
    <CharactersCard @search="getCards" />
  </main>
</template>

<style lang="scss" scoped></style>
