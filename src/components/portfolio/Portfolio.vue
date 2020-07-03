<template>
  <div>
    <h1>Portfolio</h1>
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
import { mapGetters } from "vuex";
import Stock from "./Stock";

export default {
  computed: {
    ...mapGetters({
      stocks: "stockPortfolio"
    })
  },
  components: {
    Stock
  }
};
</script>
