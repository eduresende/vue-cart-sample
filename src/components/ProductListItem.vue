<template>
  <tr>
    <td>{{product.title}}</td>
    <td>{{product.price}}</td>
  </tr>
</template>

<script>
  export default {
    name: 'ProductListItem',
    props: ['product']
  }
</script>
