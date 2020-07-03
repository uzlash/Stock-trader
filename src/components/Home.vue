<template>
  <div>
    <h1>Buy stocks or view your Portfolio</h1>
    <h6>You may Save &amp; Load your data</h6>
    <h6>Click on End day to begin a new day</h6>
    <hr />
    <h5>Your Funds: {{ funds | currency }}</h5>
  </div>
</template>

<script>
export default {
  computed: {
    funds() {
      return this.$store.getters.funds;
    }
  }
};
</script>
