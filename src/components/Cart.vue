<template>
  <div>
    <table>
      <thead>
        <th>Produto</th>
        <th>Preço</th>
        <th>Quantidade</th>
        <th>Total</th>
        <th colspan=2>Opções</th>
      </thead>
      <tbody>
        <CartItem
          v-for="item in items"
          :item="item"
          :key="item.id"
          @addItem='addItem'
          @removeItem='removeItem'
        />
      </tbody>
    </table>
    <br>
    Total: <strong>{{total}}</strong>
  </div>
</template>

<script>
  import CartItem from './CartItem';
  import lodash from 'lodash';

  export default {
    name: 'Cart',

    props: ['items'],

    components: {
      CartItem
    },

    computed: {
      total() {
        var total = 0;

        lodash.forEach(this.items, (item) => {
          total += (item.price * item.quantity);
        });

        return total;
      }
    },

    methods: {
      addItem(item) {
        this.$emit('addItem', item);
      },

      removeItem(item) {
        this.$emit('removeItem', item);
      }
    }
  }
</script>

<style scoped>
  table {
    margin-top: 15px;
  }
</style>
