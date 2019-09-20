<template>
  <div id="app">
    <h1>Distrelec Task - Carousel</h1>
    <div class="wrapper">
      <p>This carousel was made using Vue. I decided to make this in Vue as I have never really used Vue before and thought it would be a good excercise to grasp the basics. The products are pulled in using the data from the JSON file.</p>
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
      <button class="action prev">Previous</button>
      <button class="action next">Next</button>
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
  },
  mounted(){
    this.slider();
  },
  methods: {
    slider(){
      
      // Get items, slider wrapper, slider items and actions
      const slider = document.querySelector('.products');
      const sliderItems = document.querySelectorAll('.product');
      const nextBtn = document.querySelector('.next');
      const prevBtn = document.querySelector('.prev');

      // Counter to keep track of slide selected.
      let slideCount = 1;

      // Get width of image so the slider can slide that amount, also grabs the first image to make sure its hidden.
      const sliderItemSize = sliderItems[0].clientWidth;

      // Clone first product and add to the end. Clone last product, add to start.
      const firstItem = slider.firstChild.cloneNode(true);
      const lastItem = slider.lastChild.cloneNode(true);
      slider.append(firstItem);
      slider.prepend(lastItem);

      // Start slide on 2nd item.

       slider.style.transform = 'translateX(' + (-sliderItemSize * slideCount) + 'px)';
      
      // Grab buttons
      nextBtn.addEventListener('click', ()=>{
        slider.style.transition = 'ease-in-out .25s all';
        slideCount++;
        slider.style.transform = 'translateX(' + (-sliderItemSize * slideCount) + 'px)';
      });

      prevBtn.addEventListener('click', ()=>{
        slider.style.transition = 'ease-in-out .25s all';
        slideCount--;
        slider.style.transform = 'translateX(' + (-sliderItemSize * slideCount) + 'px)';
      });

      slider.addEventListener('transitionend', () => {
        if( slideCount == sliderItems.length){
          console.log('limit hit');
          slider.style.transition = 'none';
          slideCount = sliderItems.length - slideCount;
          slider.style.transform = 'translateX(' + (-sliderItemSize * slideCount) + 'px)';
        }
      });

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
  outline: 3px solid red;
  overflow: hidden;
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
