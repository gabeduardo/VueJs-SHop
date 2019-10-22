<template>
  <div id="app">
    <h1>My Shop</h1>
    <font-awesome-icon icon="shopping-cart"></font-awesome-icon>
    <price-slider :sliderStatus="sliderStatus" :maximum.sync="maximum"></price-slider>
    <product-list :maximum="maximum" :products="products" @add="addItem"></product-list>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

import ProductList from "./components/ProductList.vue";
import PriceSlider from "./components/PriceSlider.vue";

export default {
  name: "app",
  data: function() {
    return {
      maximum: 99,
      products: null,
      sliderStatus: true
    };
  },

  components: {
    FontAwesomeIcon,

    ProductList,
    PriceSlider
  },

  mounted: function() {
    fetch("http://localhost:3000/products")
      .then(response => response.json())
      .then(data => {
        this.products = data;
      });
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
