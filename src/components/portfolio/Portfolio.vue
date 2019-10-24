<template>
<div>
    <h1 class="text-center">My Stocks</h1><br>
    <div class="container" v-show="isSell">
        <div class="col-md-offset-4 col-md-4 text-center">
            <div class="alert alert-success">
                <p><i class="fa fa-check"></i>Stock sold successfully</p>
            </div>
        </div>
    </div><br>
    <div class="container" v-show="checkStock">
        <div class="col-md-offset-3 col-md-6 text-center">
            <div class="alert alert-info">
                <h5>You have <strong>0</strong> stocks, please purchase stocks to trade</h5>
            </div>
            <router-link to="/stocks" class="btn btn-primary" tag="button">Purchase Stocks</router-link>
        </div>
    </div>
    <app-data-stock v-for="stock in stocks" :stock="stock" @issell="changeIsSell"></app-data-stock>
</div>
</template>

<script>
import {mapGetters} from 'vuex';
import Stock from './Stock.vue';

export default {
    data () {
        return {
            isSell: false      
        }
    },
    computed: {
        ...mapGetters({
        stocks: 'stockPortfolio'
        }),
        checkStock() {
            return this.stocks === undefined || this.stocks.length == 0;
        }
    },
    components: {
        'app-data-stock': Stock
    },
    methods: {
        changeIsSell() {
            return this.isSell = true;
        }
    }
}
</script>
