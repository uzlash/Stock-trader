<template>
  <div class="col-sm-6 col-md-4">
    <div class="card border-success">
      <h5 class="card-header bg-light">{{ stock.name }}</h5>
      <div class="card-body">
        <h6 class="card-title text-success">(Price: ${{ stock.price }})</h6>

        <div class="float-left card-text">
          <input
            type="number"
            name="number"
            class="form-control"
            placeholder="Quantity"
            v-model="quantity"
            :class="{ 'border-danger': insufficientFunds }"
          />
        </div>
        <div class="float-right card-text">
          <button
            class="btn btn-success"
            :disabled="insufficientFunds || quantity <= 0"
            @click="buyStock"
          >
            {{ insufficientFunds ? "Insufficient Funds" : "Buy" }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["stock"],
  data: () => ({
    quantity: 0
  }),
  methods: {
    buyStock() {
      const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: parseInt(this.quantity)
      };
      // console.log(order);
      this.$store.dispatch("buyStock", order);
      this.quantity = 0;
    }
  },
  computed: {
    funds() {
      return this.$store.getters.funds;
    },
    insufficientFunds() {
      return this.quantity * this.stock.price > this.funds;
    }
  }
};
</script>
