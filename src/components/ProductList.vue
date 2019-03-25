<template>
  <table>
    <thead>
      <th>Produto</th>
      <th>Preço</th>
    </thead>
    <tbody>
      <ProductListItem
        v-for="product in products"
        :product="product"
        :key="product.id"
        @productSelect="productSelect"
      />
    </tbody>
  </table>
</template>

<script>
  import ProductListItem from './ProductListItem';

  export default {
    name: 'ProductList',

    components: {
      ProductListItem
    },

    props: ['products'],

    methods: {
      productSelect(product) {
        this.$emit('productSelect', product);
      }
    }
  }
</script>

<style>
  table, th, tr, td {
    border: 1px solid black;
    border-collapse: collapse;
  }

  th, td {
    padding: 5px;
  }

  th {
    background-color: #333;
    color: #ddd;
  }
</style>
