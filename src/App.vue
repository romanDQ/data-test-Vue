<template>
  <div id="app">
    <Table />
    <Tabulka class="tabulka"/>
    <Graf/>
  </div>
</template>

<script>
import Table from './components/Table.vue'
import Tabulka from './components/Tabulka.vue'
import Graf from './components/Graf'

export default {
  name: 'App',
  components: {
    Table,
    Tabulka,
    Graf,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.tabulka{
  margin: 30px;
}
</style>
