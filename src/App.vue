<template>
  <div id="app">
    <BarChartComponent/>
    <TableComponent />
  </div>
</template>

<script>
import TableComponent from './components/TableComponent.vue';
import BarChartComponent from './components/BarChartComponent.vue'

export default {
  name: 'App',
  components: {
    TableComponent,
    BarChartComponent
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
</style>
