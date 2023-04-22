<template>
    <div>
        <div class="about-content">
          <h1>Damian Krzemiński</h1>
          <h2>43737</h2>
          <button class="btn" @click="showInfo">Send Like</button>
        </div>
    </div>
</template>

<script>
export default {
  name: 'About',
  components: {},
  methods: {
    showInfo: () => {
        console.log('Wysłano Like!')
        alert('Dzięki :)')
    }
  }
}
</script>
<style scoped>

.about-content{
  display: flex;
  flex-direction: column;
  width: 30%;
  margin-left: 5px;
}
.btn{
  width: 100px;
  height: 50px;
  color: black;
  font-size: 16px;
  font-weight: 600;
  background-color: rgb(97, 97, 190);
  border-radius: 15%;
  border: 4px solid rgb(69, 69, 224);
}

.btn:hover{
  background-color: rgb(69, 69, 224);
}
</style>