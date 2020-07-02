<template>
  <div>
    <h1>Stocks</h1>
    <Stock v-for="stock in stocks" :key="stock.id" />
  </div>
</template>

<script>
import Stock from "./Stock";
export default {
  data: () => ({
    stocks: [
      { id: 1, name: "Facebook", price: "250" },
      { id: 2, name: "Google", price: "200" },
      { id: 3, name: "Microsoft", price: "140" },
      { id: 4, name: "Twitter", price: "160" }
    ]
  }),
  components: {
    Stock
  }
};
</script>
