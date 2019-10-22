<template>
  <div id="app">
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
import ProductList from "./components/ProductList.vue";
import Navbar from "./components/Navbar.vue";
import PriceSlider from "./components/PriceSlider.vue";

export default {
  name: "app",
  data: function() {
    return {
      maximum: 99,
      products: null,
      sliderStatus: true,
      cart: []
    };
  },
  methods: {
    toggleSliderStatus: function() {
      this.sliderStatus = !this.sliderStatus;
    },
    addItem: function(product) {
      var whichProduct;
      var existing = this.cart.filter(function(item, index) {
        if (item.product.id == Number(product.id)) {
          //para obtener el id del producto que hizo match

          whichProduct = index;
          return true;
        } else {
          return false;
        }
      });

      if (existing.length) {
        this.cart[whichProduct].qty++;
      } else {
        this.cart.push({ product: product, qty: 1 });
      }
    },
    deleteItem: function(id) {
      if (this.cart[id].qty > 1) {
        this.cart[id].qty--;
      } else {
        this.cart.splice(id, 1);
      }
    }
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
  },

  computed: {
    cartQty: function() {
      let qty = 0;
      for (let key in this.cart) {
        qty = qty + this.cart[key].qty;
      }
      return qty;
    },
    cartTotal: function() {
      let sum = 0;
      for (let key in this.cart) {
        sum = sum + this.cart[key].product.price * this.cart[key].qty;
      }
      return sum;
    }
  }
};
</script>

