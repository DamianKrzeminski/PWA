<template>
    <img :src="image" class="img" />
  </template>
  <script>
  export default {
    name: 'SmallImage',
    props: {
      image: {
          type: String,
          default: () => 'Pusty string'
      }
    }
  }
  </script>
  <style scoped>
  .img {
    width: 150px;
    height: 150px;
    border: 2px solid black;
  }
  </style>