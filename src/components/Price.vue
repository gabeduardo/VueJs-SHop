<template>
  <span>{{this.prefix + Number.parseFloat(this.value).toFixed(this.precision)}}</span>
</template>

<script>
export default {
  props: {
    value: Number,
    prefix: {
      type: String,
      default: "$"
    },
    precision: {
      type: Number,
      default: 2
    }
  }
};
</script>

   

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
