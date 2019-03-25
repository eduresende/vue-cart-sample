<template>
  <div v-if='product'>
    <strong>{{ product.title }}</strong>
    ( {{ product.price }} )
  </div>
</template>

<script>
  export default {
    name: 'SelectedProduct',
    props: ['product'],
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
