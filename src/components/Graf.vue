<template>
  <div>
    
    <div class="columns">
      <div class="column">
        <h3>Bar Chart</h3>
        
        <bar-chart
        v-if: loaded
        :data="chartdata"
        ></bar-chart>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import {Line, Bar } from 'vue-chartjs'

export default {
  
  extends: Line, Bar,
  data() {
    return {
      baseUrl: process.env.VUE_APP_BASE_URL,
      loaded: false,
      chartdata: [],
      showError: false,
     
      // chartData: {
      //     '2017-05-13' : 2,
      //     '2017-05-14' : 5,
      //     '2017-05-15' : 4,
      //     '2017-05-17' : 3,
      //     '2017-05-18' : 9,
      //     '2017-05-19' : 7,
      // }
    };
  },

  mounted(){
      this.renderChart(this. chartdata)
    },

  created() {
    axios
        .get(this.baseUrl + "testData.json")
        .then(response => {
         this.chartdata = response.data[1]
         
        
         this.loaded = true
        })
        .catch(err => {
          this.errorMessage = err.response.data.error
          this.showError = true
        })
  
  },
  
};
</script>
