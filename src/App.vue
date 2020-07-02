<template>
  <div id="app" class="container">
    <Header />
    <div class="row row-custom">
      <div class="col-md-12">
        <router-view />
      </div>
    </div>
  </div>
</template>

<style></style>

<script>
import Header from "./components/Header";
export default {
  components: {
    Header
  }
};
</script>

<style>
body {
  padding: 30px;
}

.row-custom {
  padding: 30px;
}
</style>
