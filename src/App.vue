<template>
  <div id="app">
    <!-- <graphChart1 /> -->
    <graphChart2 />
  </div>
</template>

<script>
// import graphChart1 from './components/graphChart1.vue'

import graphChart2 from './components/graphChart2.vue'

export default {
  name: 'App',
  components: {
    // graphChart1,
    graphChart2,
  },
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
