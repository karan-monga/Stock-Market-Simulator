<template>
  <div>
    <div class="row">
      <div class="col-lg-6 col-md-6 col-sm-3 col-xs-3 jumboalign">
        <b-jumbotron class="test">
          <h1 class="markh1" align="right">{{funds | currency }}.00</h1>
          <p class="smallp" align="right">Available Balance</p>
        </b-jumbotron>
      </div>
      <div class="col-lg-6 col-md-6 col-sm-6 col-xs-6" style="padding:20px">
        <h3>How to trade?</h3>
        <li>Click on 'Stocks' and enter the number of stocks you would like to buy</li>
        <li>Click on 'End Day' begin a new day and see stock prices change!</li>
        <li>Click on 'Portfolio' to see your stocks and select how many you want to sell</li>
        <li>You may save & load your data</li>
        <li>Stock Price Changes everyday, try to maximize profit</li>
      </div>
    </div>
    <div class="row">
      <div class="centerbutton">
        <router-link to="/stocks" class="btn btn-primary btn-lg" tag="button">
          <i class="fa fa-bolt" aria-hidden="true"></i> Start Trading
        </router-link>
      </div>
    </div>
    <hr />
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

<style scoped>
.smallp {
  font-size: 15px;
}
.mark {
  background-color: rgb(255, 255, 255);
  width: 45px;
}

.alignjumbotron {
  text-align: center;
}
.centerbutton {
  display: flex;
  align-items: center;
  justify-content: center;
}
.jumboalign {
  display: flex;
  align-items: right;
  justify-content: right;
}
</style>

  