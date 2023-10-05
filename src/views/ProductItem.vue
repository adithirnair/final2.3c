<template>
    <li>
      <h3>{{ product.name }}</h3>
      <p>Price: ${{ product.price }}</p>
      <p v-if="product.inStock">In Stock</p>
      <p v-else>Out of Stock</p>
    </li>
  </template>
  
  <script>
  export default {
    props: {
      product: Object, // Assuming that 'product' is an object with properties like 'name', 'price', and 'inStock'
    },
  };
  </script>
  