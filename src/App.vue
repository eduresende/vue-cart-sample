<template>
  <div id='app'>
    <ProductList :products='allProducts' />
  </div>
</template>

<script>
  import ProductList from './components/ProductList';

  export default {
    name: 'App',

    components: {
      ProductList
    },

    data() {
      return {
        allProducts: [
          { id: 1, title: 'Lapis', price: 1, },
          { id: 2, title: 'Caneta', price: 3, },
          { id: 3, title: 'Cola', price: 5, },
          { id: 4, title: 'Caderno', price: 10, },
          { id: 5, title: 'Tesoura', price: 15, },
          { id: 6, title: 'Livro', price: 100, },
          { id: 7, title: 'Mochila', price: 200, },
          { id: 8, title: 'Notebook', price: 1000 },
        ]
      }
    }
  }
</script>
