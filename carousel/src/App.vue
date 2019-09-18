<template>
  <div id="app">
    <h1>Distrelec Task - Carousel</h1>
    <Product name="Test" price="30" url="lorem"/>
    <p>{{products.numberOfItems}}</p>
  </div>
</template>

<script>

import Product from "./components/Product";
import JSON from "./assets/data.json";

export default {
  name: 'app',
  components: {
    Product
  },
  data(){
    return{
      products: JSON
    }
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
