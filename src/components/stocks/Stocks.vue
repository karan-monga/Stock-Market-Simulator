<template>
  <div>
    <h1 class="text-center">Stocks Listings</h1>
    <br />
    <div class="container" v-show="isBuy">
      <div class="col-md-offset-4 col-md-4 text-center">
        <div class="alert alert-success">
          <p>
            <i class="fa fa-check"></i> Stock Purchase Success!
          </p>
        </div>
      </div>
    </div>
    <br />
    <app-stock v-for="stock in stocks" :stock="stock" @isbuyd="changeIsBuy"></app-stock>
    <br />
    <p class="text-center" id="info">
      <i class="fa fa-info-circle"></i>
      <i>Enter number of stocks you'd like to buy</i>
    </p>
    <hr />
  </div>
</template>

<script>
import Stock from "./Stock.vue";

export default {
  data() {
    return {
      isBuy: false
    };
  },
  components: {
    "app-stock": Stock
  },
  computed: {
    stocks() {
      return this.$store.getters.stocks;
    }
  },
  methods: {
    changeIsBuy() {
      return (this.isBuy = true);
    }
  }
};
</script>