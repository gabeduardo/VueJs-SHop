<template>
  <div id="app">
    <h1>My Shop</h1>
    <navbar :cart="cart" :cartQty="cartQty" :cartTotal="cartTotal"></navbar>

    <price-slider :sliderStatus="sliderStatus" :maximum.sync="maximum"></price-slider>
    <product-list :maximum="maximum" :products="products" @add="addItem"></product-list>
  </div>
</template>

<script>
import ProductList from "./components/ProductList.vue";
import Navbar from "./components/Navbar.vue";
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
    ProductList,
    PriceSlider,
    Navbar
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

