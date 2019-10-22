<template>
  <transition-group
    name="fade"
    tag="div"
    enter-active-class="animated fadeInRight"
    leave-active-class="animated slideOutRight"
    @beforeEnter="beforeEnter"
    @enter="enter"
    @leave="leave"
  >
    <!-- eslint-disable -->
    <div
      class="row d-flex mb-3 align-items-center"
      v-for="(item, index) in products"
      :key="item.id"
      :data-index="index"
      v-if="item.price <= Number(maximum)"
    >
      <div class="col-1 m-auto">
        <button class="btn btn-info" @click="$emit('add', item)">+</button>
      </div>

      <div class="col-sm-4">
        <img class="img-fluid d-block" :src="item.image" :alt="item.name" />
      </div>
      <div class="col">
        <h3 class="text-info">{{ item.name }}</h3>
        <p class="mb-0">{{ item.description }}</p>

        <!-- agregando filtro -->
        <div class="h5 float-right">
          <price :value="Number(item.price)"></price>
        </div>
      </div>
    </div>
  </transition-group>
</template>

<script>
import Price from "./Price.vue";
export default {
  name: "product-list",
  components: { Price },
  props: ["products", "maximum"],
  computed: {
    filteredProducts: function() {
      // if (this.products !== null) {
      //   return this.products.filter(product => product.price <= this.maximum);
      // }
      return this.products;
    }
  },

  methods: {
    beforeEnter: function(el) {
      el.className = "d-none";
    },

    enter: function(el) {
      var delay = el.dataset.index * 100;
      setTimeout(function() {
        el.className =
          "row d-flex mb-3 align-items-center animated fadeInRight";
      }, delay);
    },

    leave: function(el) {
      var delay = el.dataset.index * 100;
      setTimeout(function() {
        el.className =
          "row d-flex mb-3 align-items-center animated fadeOutRight";
      }, delay);
    }
  }
};
</script>

