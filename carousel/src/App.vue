<template>
  <div id="app">
    <h1>Distrelec Task - Carousel</h1>
    <Product/>
  </div>
</template>

<script>

import Product from "./components/Product";

export default {
  name: 'app',
  components: {
    Product
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
