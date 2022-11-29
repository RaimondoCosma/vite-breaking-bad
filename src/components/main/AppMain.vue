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
    cardsFilter() {
      axios
        .get("https://www.breakingbadapi.com/api/characters", {
          params: {
            category: this.store.searchValue,
          },
        })
        .then((resp) => {
          this.store.serieCharacters = resp.data;
          console.log(resp.data);
        });
    },
  },
  created() {
    axios.get("https://www.breakingbadapi.com/api/characters").then((resp) => {
      this.store.serieCharacters = resp.data;
    });
  },
};
</script>

<template>
  <main>
    <CharactersCard @search="cardsFilter" />
  </main>
</template>

<style lang="scss" scoped></style>
