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
          />
        </div>
        <div class="float-right card-text">
          <button
            class="btn btn-success"
            :disabled="quantity <= 0"
            @click="buyStock"
          >
            Buy
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
      const stockOrder = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: parseInt(this.quantity)
      };
      console.log(stockOrder);
      this.quantity = 0;
    }
  }
};
</script>
