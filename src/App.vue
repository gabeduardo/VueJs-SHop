<template>
  <div id="app">
    <h1>My Shop</h1>
    <p class="animated fadeInRight">Vue shop test of animation</p>
    <font-awesome-icon icon="shopping-cart"></font-awesome-icon>
    <price value="4.52"></price>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import Price from "./components/Price.vue";
export default {
  name: "app",
  components: {
    FontAwesomeIcon,
    Price
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
