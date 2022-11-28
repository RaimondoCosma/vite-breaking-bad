<script>
import axios from "axios";
import AppCard from "../commons/AppCard.vue";

export default {
  name: "CharactersCard",
  components: {
    AppCard,
  },
  data() {
    return {
      serieCharacters: [],
    };
  },
  created() {
    axios.get("https://www.breakingbadapi.com/api/characters").then((resp) => {
      this.serieCharacters = resp.data;
    });
  },
};
</script>

<template>
  <div class="container-lg mt-4 mb-3">
    <select class="form-select w-auto" aria-label="Default select example">
      <option selected>Select Category</option>
      <option value="1">One</option>
      <option value="2">Two</option>
      <option value="3">Three</option>
    </select>
  </div>
  <div class="row container-lg m-auto bg-white">
    <div class="w-100 text-white p-3 mt-5 mb-3 my-info">
      Found {{ serieCharacters.length }} Characters
    </div>
    <AppCard
      v-if="serieCharacters.length !== 0"
      v-for="character in serieCharacters"
      class="my-card"
      :character="character"
    />
    <!-- Parte loading spinner -->
    <div v-else class="lds-ring">
      <div></div>
      <div></div>
      <div></div>
      <div></div>
    </div>
    <!-- /Parte loading spinner -->
  </div>
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
/* ------------------
    LOADING SPINNER
------------------ */
.lds-ring {
  display: inline-block;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 80px;
  height: 80px;
}
.lds-ring div {
  box-sizing: border-box;
  display: block;
  position: absolute;
  width: 64px;
  height: 64px;
  margin: 8px;
  border: 8px solid #fdd;
  border-radius: 50%;
  animation: lds-ring 1.2s cubic-bezier(0.5, 0, 0.5, 1) infinite;
  border-color: #fcf transparent transparent transparent;
}
.lds-ring div:nth-child(1) {
  animation-delay: -0.45s;
}
.lds-ring div:nth-child(2) {
  animation-delay: -0.3s;
}
.lds-ring div:nth-child(3) {
  animation-delay: -0.15s;
}
@keyframes lds-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
