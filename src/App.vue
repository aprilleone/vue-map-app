<template>
  <div id="app">
    <h1>Basic Map App</h1>
    
    <BaseMap/>
  </div>
</template>

<script>

import BaseMap from './components/BaseMap.vue'

export default {
  name: 'App',
  components: {
    BaseMap
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
