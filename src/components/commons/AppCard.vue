<script>
export default {
  name: "AppCard",
  props: {
    character: Object,
  },
};
</script>

<template>
  <div class="text-center m-2 p-3 my-card">
    <img class="img-fluid" :src="character.img" :alt="character.name" />
    <h3 class="text-white mt-2">{{ character.name }}</h3>
    <div class="serie text-secondary">{{ character.category }}</div>
    <div class="status text-secondary">{{ character.status }}</div>
  </div>
</template>

<style lang="scss" scoped>
.my-card {
  background-color: #2e3a46;
}
</style>
