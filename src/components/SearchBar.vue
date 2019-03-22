<template>
  <input @input="onInput">
</template>

<script>
  export default {
    name: 'SearchBar',

    methods: {
      onInput: function (event) {
        this.$emit('termChange', event.target.value);
      }
    }
  };
</script>

<style scoped>
  input {
    border: 1px solid #666;
    margin-bottom: 10px;
    height: 20px;
  }
</style>
