<template>
  <div id="app">
    <h1>  My Shop</h1>
    <p class="animated fadeInRight"> Vue shop test of animation </p>
    <font-awesome-icon icon="shopping-cart"> </font-awesome-icon>
  </div>
</template>

<script>

import {FontAwesomeIcon} from "@fortawesome/vue-fontawesome";
export default {
  name: 'app',
  components: {
    FontAwesomeIcon,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
