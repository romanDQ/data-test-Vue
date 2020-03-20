<template>
  <div class>
    <table class="w3-table-all">
      <tr v-for-key="currency in info" class="currency"></tr>
      <tr>
        <th>{{info.USD.description}}:</th>
        <th>{{info.GBP.description}}:</th>
        <th>{{info.EUR.description}}:</th>
      </tr>
      <tr>
        <th>{{info.USD.rate_float}}</th>
        <th>{{info.GBP.rate_float}}</th>
        <th>{{info.EUR.rate_float}}</th>
      </tr>
    </table>
  </div>
</template>

<script>


import axios from "axios";
export default {
  data() {
    return {
      info: null
      // money
    };
  },

  filters: {
    currencydecimal(value) {
      return value.toFixed(2);
    }
  },
  mounted() {
    axios
      .get("https://api.coindesk.com/v1/bpi/currentprice.json")
      .then(response => {
        this.info = response.data.bpi;
      });
  }
};
</script>

<style scoped>
.table {
  display: block;
  width: 50%;
  padding: 15px;
  text-align: center;
  margin-right: auto;
  margin-left: auto;

  color: #313131;
  font-size: 20px;
  appearance: none;
  border: none;
  background: none;
}
</style>