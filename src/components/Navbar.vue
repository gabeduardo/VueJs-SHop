<template>
  <nav class="navbar navbar-light fixed-top">
    <div class="navbar-text ml-auto d-flex">
      <button class="btn btn-sm btn-outline-success" @click="$parent.$emit('toggle')">
        Range of
        <font-awesome-icon icon="dollar-sign"></font-awesome-icon>
      </button>
      <div class="ml-2">
        <button
          class="btn btn-success btn-sm dropdown-toggle"
          id="cartDropdown"
          data-toggle="dropdown"
        >
          <b>Cart:</b>
          <span class="badge badge-pill badge-light">{{cartQty}}</span>
          <!-- <i class="fas fa-shopping-cart mx-2">{{cartTotal}}</i> -->
          <price :value="Number(cartTotal)"></price>
        </button>

        <!-- modal que muestra el carrito -->

        <div class="dropdown-menu dropdown-menu-right text-right">
          <!-- uso como key el item para no tener el mismo key de los elementos de abajo -->
          <div v-for="(item,index) in cart" :key="index">
            <div class="dropwdown-item-text text-nowrap text-right">
              <span class="badge badge-pill badge-warning align-text-top mr-1">{{item.qty}}</span>
              {{item.product.name}}
              <b>
                <price :value="Number(item.qty * item.product.price)"></price>
              </b>

              <a
                href="#"
                @click.stop="$parent.$emit('delete', index)"
                class="badge badge-danger text-white"
              >-</a>
            </div>
          </div>
          <router-link
            class="btn btn-sm btn-outline-info text-dark float-right mr-4"
            to="/checkout"
          >Checkout</router-link>
        </div>
      </div>
    </div>
  </nav>
</template>
  

<script>
import Price from "./Price.vue";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
// import VueRouter from "vue-router";
export default {
  name: "navbar",
  props: ["cart", "cartQty", "cartTotal"],
  components: {
    FontAwesomeIcon,

    Price
  }
};
</script>

<style scoped>
</style>