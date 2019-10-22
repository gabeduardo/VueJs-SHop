<template>
  <transition
    name="custom"
    enter-active-class="animated fadeInDown"
    leave-active-class="animated slideOutRight"
  >
    <div v-if="sliderStatus">
      <div class="align-items-center" :class="sliderState">
        <label for="formMax" class="font-weight-bol mr-2">max</label>
        <input
          type="text"
          id="formMax"
          class="form-control mx-2 text-center"
          style="width: 60px;"
          v-model="maxAmount"
          @change="$emit('update:maximum',maxAmount )"
        />
        <input
          type="range"
          class="custom-range"
          min="0"
          max="200"
          v-model="maxAmount"
          style="width:30%;"
          @input="$emit('update:maximum',maxAmount )"
        />
      </div>
    </div>
  </transition>
</template>


<script>
export default {
  name: "price-slider",
  props: ["sliderStatus"],
  data: function() {
    return {
      maxAmount: 99
    };
  },

  computed: {
    sliderState: function() {
      return this.sliderStatus ? "d-flex" : "d-none";
    }
  }
};
</script>

<style scoped>
</style>