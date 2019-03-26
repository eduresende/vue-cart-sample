<template>
  <div id='app'>
    <SearchBar @termChange='termChange' />
    <ProductList :products='products' @productSelect='productSelect'/>
    <SelectedProduct :product='selectedProduct' @addItem='addItem'/>
    <Cart :items='cartItems' @addItem='addItem' @removeItem='removeItem' />
  </div>
</template>

<script>
  import lodash from 'lodash';

  import ProductList from './components/ProductList';
  import SearchBar from './components/SearchBar';
  import SelectedProduct from './components/SelectedProduct';
  import Cart from './components/Cart'

  export default {
    name: 'App',

    components: {
      ProductList,
      SearchBar,
      SelectedProduct,
      Cart
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

        selectedProduct: null,

        cartItems: []
      }
    },

    methods: {
      termChange: function(term) {
        this.term = term;
      },

      productSelect(product) {
        this.selectedProduct = product;
      },

      addItem(item) {
        var newCartItems = [];
        var added = false;

        lodash.forEach(this.cartItems, (cartItem) => {
          if (cartItem.id == item.id) {
            cartItem.quantity++;
            added = true;
          }
          newCartItems.push(cartItem);
        });

        if (!added) {
          newCartItems.push({ id: item.id, title: item.title, price: item.price, quantity: 1 });
        }

        this.cartItems = newCartItems;
      },

      removeItem(item) {
        var newCartItems = [];

        lodash.forEach(this.cartItems, (cartItem) => {
          if (cartItem.id == item.id) {
            cartItem.quantity--;
          }

          if (cartItem.quantity > 0) {
            newCartItems.push(cartItem);
          }
        });

        this.cartItems = newCartItems;
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
