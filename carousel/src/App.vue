<template>
  <div id="app">
    <h1>Distrelec Task - Carousel</h1>
    <div class="wrapper" ref="productWrapper">
      <ul class="products">
      <Product 
      v-for="product in products" 
      :key="product.code" 
      :name="product.name" 
      :currency="product.price.currency" 
      :price="product.price.formattedValue" 
      :image="product.productImageUrl"
      :alt="product.productImageAltText"
      :url="product.url"/>
      </ul>
    </div>
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
      products: JSON.carouselData
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

ul, li{
  padding: 0;
  margin: 0;
}

.wrapper{
  width: 90%;
  margin: 0 auto;
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
