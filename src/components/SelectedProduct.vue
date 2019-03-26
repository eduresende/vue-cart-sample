<template>
  <div v-if='product'>
    <strong>{{ product.title }}</strong>
    ( {{ product.price }} )
    <button @click='addItem'>Add</button>
  </div>
</template>

<script>
  export default {
    name: 'SelectedProduct',
    props: ['product'],

    methods: {
      addItem() {
        this.$emit('addItem', this.product);
      }
    }
  }
</script>

<style scoped>
  div {
    border: 1px solid #ccc;
    width: 300px;
    margin-top: 15px;
    padding: 10px;
  }
</style>
