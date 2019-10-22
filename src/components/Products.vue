<template>
  <div>
    <h1>My Shop</h1>
    <navbar
      :cart="cart"
      :cartQty="cartQty"
      :cartTotal="cartTotal"
      @toggle="toggleSliderStatus"
      @delete="deleteItem"
    ></navbar>

    <price-slider :sliderStatus="sliderStatus" :maximum.sync="maximum"></price-slider>
    <product-list :maximum="maximum" :products="products" @add="addItem"></product-list>
  </div>
</template>


<script>
import ProductList from ".//ProductList";
import Navbar from "./Navbar.vue";
import PriceSlider from "./PriceSlider.vue";
export default {
  name: "products",
  props: [
    "cart",
    "cartQty",
    "cartTotal",
    "sliderStatus",
    "maximum",
    "products"
  ],

  components: {
    ProductList,
    PriceSlider,
    Navbar
  }
};
</script>