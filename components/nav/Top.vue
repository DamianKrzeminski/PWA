<template>
    <div class="nav">
        <div class="navElement">
            <NuxtLink to="/"  class="item">Home</NuxtLink>
        </div>
        <div class="navElement">
            <NuxtLink to="/about" class="item">About</NuxtLink>
        </div>
        <div class="navElement">
            <NuxtLink to="/gallery" class="item">Gallery</NuxtLink>
        </div>
        <div class="navElement">
            <NuxtLink to="/list_of_products" class="item">List of Products</NuxtLink>
        </div>
        <div class="navElement">
            <NuxtLink :to="'/products/' + name"  class="item">Products</NuxtLink>
        </div>
    </div>
</template>

<script>
export default{
    name: 'Top',
data(){
    return {
        name: '123'
    }
}
}

</script>
<style scoped>
.nav {
    display: flex;
    flex-direction: row;
    height: 50px;
    background-color: rgb(80, 100, 200);
}

.navElement{
    display: flex;
    width: 10%;
    height: 100%;
}

.item {
    display: flex;
    justify-content: space-around;
    align-items: center;
    height: 100%;
    width: 100%;
    text-decoration: none;
    font-weight: 600;
    color: black;
    font-size: 25px;
}

.item:hover{
    background-color: rgb(82, 82, 160);
}
</style>