<template>
  <tr @click='onClick'>
    <td>{{product.title}}</td>
    <td>{{product.price}}</td>
  </tr>
</template>

<script>
  export default {
    name: 'ProductListItem',

    props: ['product'],

    methods: {
      onClick() {
        this.$emit('productSelect', this.product);
      }
    }
  }
</script>

<style scoped>
  tr {
    cursor: pointer;
  }

  tr:hover {
    background-color: #ddd;
  }
</style>
