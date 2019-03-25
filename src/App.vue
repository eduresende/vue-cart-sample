<template>
  <div id='app'>
    <SearchBar @termChange='termChange' />
    <ProductList :products='products' @productSelect='productSelect'/>
    <SelectedProduct :product='selectedProduct' />
  </div>
</template>

<script>
  import lodash from 'lodash';

  import ProductList from './components/ProductList';
  import SearchBar from './components/SearchBar';
  import SelectedProduct from './components/SelectedProduct';

  export default {
    name: 'App',

    components: {
      ProductList,
      SearchBar,
      SelectedProduct
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
        ],

        term: '',

        selectedProduct: 'Produto selecionado',
      }
    },

    methods: {
      termChange: function(term) {
        this.term = term;
      },

      productSelect(product) {
        this.selectedProduct = product;
      }
    },

    computed: {
      products() {
        if (!this.term) {
          return this.allProducts;
        } else {
          var selected = [];
          const termRegex = new RegExp(this.term, 'i');

          lodash.forEach(this.allProducts, (product) => {
            if (product.title.match(termRegex)) {
              selected.push(product);
            }
          });

          return selected;
        }
      }
    }
  }
</script>

<style scoped>
  #app {
    margin: 20px;
    font-family: sans-serif;
    font-size: 14px;
  }
</style>
