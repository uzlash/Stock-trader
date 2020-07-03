<template>
  <div class="col-sm-6 col-md-4">
    <div class="card border-info">
      <h5 class="card-header bg-light">{{ stock.name }}</h5>
      <div class="card-body">
        <h6 class="card-title text-info">
          (Price: ${{ stock.price }} | Quantity: {{ stock.quantity }})
        </h6>

        <div class="float-left card-text">
          <input
            type="number"
            name="number"
            class="form-control"
            placeholder="Quantity"
            v-model="quantity"
            :class="{ 'border-danger': insufficientQuantity }"
          />
        </div>
        <div class="float-right card-text">
          <button
            class="btn btn-danger"
            :disabled="insufficientQuantity || quantity <= 0"
            @click="sellStock"
          >
            {{ insufficientQuantity ? "Not Enough Stocks" : "Sell" }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  props: ["stock"],
  data: () => ({
    quantity: 0
  }),
  methods: {
    ...mapActions({
      placeSellOrder: "sellStock"
    }),
    sellStock() {
      const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity
      };
      console.log(order);
      this.placeSellOrder(order);
      this.quantity = 0;
    }
  },
  computed: {
    insufficientQuantity() {
      return this.quantity > this.stock.quantity;
    }
  }
};
</script>
