<template>
    <nav class="navbar navbar-reverse">
        <div class="container-fluid">
          <div class="navbar-header">
            <router-link to="/" class="navbar-brand">Stock Trader</router-link>
          </div>
          <div id="navbar" class="navbar-collapse collapse">
            <ul class="nav navbar-nav">
                <router-link to="/portfolio" active-class="active" tag="li"><a><i aria-hidden="true"></i>Portfolio</a></router-link>
                <router-link to="/stocks" active-class="active" tag="li"><a> Stocks</a></router-link>                
            </ul>
            <ul id="funds" class="navbar-text navbar-right"><i class="fa fa-money" aria-hidden="true"></i> Funds: {{funds | currency }}.00</ul>
            <ul class="nav navbar-nav navbar-right">
              <li><a href="#" @click="endDay"><i class="fa fa-power-off" aria-hidden="true"></i> End the Day</a></li>
              <li class="dropdown" :class="{ open : isDropdownOpen }"
			  @click="isDropdownOpen = !isDropdownOpen">
                <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false">
									<i class="fa fa-floppy-o" aria-hidden="true"></i> Save & Load <span class="caret"></span></a>
                <ul class="dropdown-menu" id="drop">
                  <li><a href="#" @click="saveData"><i class="fa fa-floppy-o" aria-hidden="true"></i> Save Data</a></li>
                  <li><a href="#" @click="loadData"><i class="fa fa-cloud-download" aria-hidden="true"></i> Load Data</a></li>
                </ul>
              </li> 
            </ul>
          </div><!--/.nav-collapse -->
        </div><!--/.container-fluid -->
      </nav>
</template>

<script>
import { mapActions } from 'vuex';

export default {
	data () {
		return {
			isDropdownOpen: false
		}
	},
	computed: {
		funds() {
			return this.$store.getters.funds;
		}
	},
	methods: {
		...mapActions({
			randomizeStocks: 'randomizeStocks',
			fetchData: 'loadData'
		}),
		endDay() {
			return this.randomizeStocks();
		},
		saveData() {
			const data = {
				funds: this.$store.getters.funds,
				stockPortfolio: this.$store.getters.stockPortfolio,
				stocks: this.$store.getters.stocks
			};
			this.$http.put('data.json', data);
			alert('Data Saved Successfully');
		},
		loadData() {
			this.fetchData();
			alert('Data Loaded Successfully');
		}
	}
}
</script>


<style scoped>
.navbar {
	background: #00879c;
	border-radius: 0px;
	min-height: 70px;
}

.navbar a{
    color: #fff;
}

.navbar li {
	padding-top: 10px;
}

#drop a{
    color: #000;
}

.navbar a:hover, .navbar a:active{
    color: #000;
}

.navbar-brand {
	padding-top: 25px;
}

.navbar-brand:hover {
	color: #fff;
	font-weight: bold;
}

#funds {
	color: #fff;
	padding-top: 10px;
	background: #777777;
	padding: 10px;
	border-radius: 5px;
}
</style>
