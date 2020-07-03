<template>
  <div>
    <h1>Stocks</h1>
    <div class="row">
      <Stock
        class="col-md-4 mb-4"
        v-for="stock in stocks"
        :key="stock.id"
        :stock="stock"
      />
    </div>
  </div>
</template>

<script>
import Stock from "./Stock";
export default {
  // data: () => ({
  //   stocks: []
  // }),
  components: {
    Stock
  },
  computed: {
    stocks() {
      return this.$store.getters.stocks;
    }
  }
};
</script>
