<template>
  <div id="app">
    <h1>Distrelec Task - Carousel</h1>
    <Product/>
    <Product/>
    <Product/>
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
*{
  box-sizing: border-box;
}

img{
  max-width: 100%;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
