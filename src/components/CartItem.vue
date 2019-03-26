<template>
  <tr>
    <td>{{item.title}}</td>
    <td>{{item.price}}</td>
    <td>{{item.quantity}}</td>
    <td>{{total}}</td>
    <td><button @click='addItem'>add</button></td>
    <td><button @click='removeItem'>remove</button></td>
  </tr>
</template>

<script>
  export default {
    name: 'CartItem',

    props: ['item'],

    computed: {
      total() {
        return this.item.price * this.item.quantity;
      }
    },

    methods: {
      addItem() {
        this.$emit('addItem', this.item);
      },

      removeItem() {
        this.$emit('removeItem', this.item);
      }
    }
  }
</script>
