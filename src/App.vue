<script>
import AppHeader from "./components/header/AppHeader.vue";
import AppMain from "./components/main/AppMAin.vue";

export default {
  components: {
    AppHeader,
    AppMain,
  },
};
</script>

<template>
  <div>
    <AppHeader />
    <AppMain />
  </div>
</template>

<style lang="scss">
@import "./style/global.scss";
</style>
