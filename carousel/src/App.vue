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
          :url="product.url"
        />
      </ul>
      <div class="actions">
        <button class="action prev">Previous</button>
        <button class="action next">Next</button>
      </div>
    </div>
  </div>
</template>

<script>
import Product from "./components/Product";
import JSON from "./assets/data.json";

export default {
  name: "app",
  components: {
    Product
  },
  data() {
    return {
      products: JSON.carouselData
    };
  },
  mounted() {
    this.slider();
  },
  methods: {
    slider() {
      // Get items, slider wrapper, slider items and actions
      const slider = document.querySelector(".products");
      const sliderItems = document.querySelectorAll(".product");
      const nextBtn = document.querySelector(".next");
      const prevBtn = document.querySelector(".prev");

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

      slider.style.transform =
        "translateX(" + -sliderItemSize * slideCount + "px)";

      // Grab buttons
      nextBtn.addEventListener("click", () => {
        slider.style.transition = "ease-in-out .25s all";
        slideCount++;
        slider.style.transform =
          "translateX(" + -sliderItemSize * slideCount + "px)";
      });

      prevBtn.addEventListener("click", () => {
        slider.style.transition = "ease-in-out .25s all";
        slideCount--;
        slider.style.transform =
          "translateX(" + -sliderItemSize * slideCount + "px)";
      });

      slider.addEventListener("transitionend", () => {
        if (slideCount == sliderItems.length) {
          slider.style.transition = "none";
          slideCount = sliderItems.length - slideCount;
          slider.style.transform =
            "translateX(" + -sliderItemSize * slideCount + "px)";
        }
      });
    }
  }
};
</script>

<style lang="scss">
/* Variables */
$red: #df1417;
$blue: #009fb4;
$screen__s: 640px;
$screen__m: 768px;

* {
  box-sizing: border-box;
}

img {
  max-width: 100%;
}

ul,
li {
  padding: 0;
  margin: 0;
}

a,
a:link,
a:active,
a:visited {
  color: $blue;
  text-decoration: none;
  font-weight: 700;
  transition: ease-in-out all 0.25s;
}

a:hover,
a:focus {
  color: darken($blue, 10%);
  transition: ease-in-out all 0.25s;
}

.wrapper {
  width: 90%;
  margin: 0 auto;
  overflow: hidden;
  position: relative;
}

#app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica,
    Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #1e1e1d;
  margin-top: 60px;
}

/* Buttons, prev and next */
.actions {
  display: flex;
  justify-content: flex-end;
  margin-top: 15px;
  .action {
    font-size: 0;
    background-color: transparent;
    border:0;
    outline :0;
    cursor: pointer;
    color: $red;
    &::before {
      content: ">";
      font-size: 30px;
    }
    &.prev {
      margin-right: 5px;
      &::before {
        content: "<";
      }
    }
  }
}

/* Product wrapper */
.products {
  display: flex;
  flex-wrap: nowrap;
  width: 100%;
}

/* Products*/
.product {
  display: inline-block;
  padding: 10px;
  min-width: 100%;
  transition: ease-in-out 0.25s all;
  font-weight: 700;
  img {
    margin: auto;
  }

  &__name,
  &__price {
    display: block;
  }

  &__price,
  &__action,
  &__name {
    margin-top: 15px;
  }

  &__action {
    display: inline-block;
    padding: 10px 15px;
    border: 2px solid #1e1e1d;
    border-radius: 4px;
    font-size: inherit;
    font-weight: 400;
    cursor: pointer;
    position: relative;
    z-index: 1;
    &::before {
      content: "";
      position: absolute;
      background: #1e1e1d;
      right: 0;
      left: 0;
      top: 0;
      bottom: 0;
      z-index: -1;
      transform: scaleX(0);
      transform-origin: left;
      transition: ease-in-out 0.25s all;
    }
  }

  &__name {
    min-height: 45px;
  }

  &:hover {
    transition: ease-in-out 0.25s all;
    transform: translateY(-3px);
    .product__action {
      color: #fff;
      &::before {
        transform: scaleX(1);
        transition: ease-in-out 0.25s all;
      }
    }
  }

  @media screen and (min-width: $screen__s) {
    min-width: 50%;
  }
  @media screen and (min-width: $screen__m) {
    min-width: (100% / 3);
  }
}
</style>
