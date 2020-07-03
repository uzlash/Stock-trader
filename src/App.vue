<template>
  <div id="app" class="container">
    <Header />
    <div class="row-custom">
      <router-view />
    </div>
  </div>
</template>

<style></style>

<script>
import Header from "./components/Header";
export default {
  components: {
    Header
  },
  created() {
    this.$store.dispatch("initStocks");
  }
};
</script>

<style>
body {
  padding: 20px;
}

.row-custom {
  padding: 20px;
}
</style>
