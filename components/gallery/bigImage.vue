<template>
  <img :src="image" class="img" />
</template>
<script>
export default {
  name: 'BigImage',
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
  width: 600px;
  height: 600px;
  border: 2px solid black;
}
</style>