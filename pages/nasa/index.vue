<template>
    <div>
        <h1>Nasa</h1>
        <div class="img-nasa-box">
            <img class="image-nasa" :src="value.links[0].href" v-for="(value, index) in dataArr" :key="index"/>
        </div>
    </div>
</template>

<script>
import axios from "axios";
export default {
    name: "index",
    created(){
        this.fetchData()
    },
    data(){
        return{
            dataArr: []
        }
    },
    methods:{
        async fetchData(){
            await axios.get('https://images-api.nasa.gov/search?q=sun')
            .then(res => {
                this.dataArr = res.data.collection.items;
            })
            .catch(error => {
                console.log(error)
            })
        }
    }
}
</script>

<style>
.img-nasa-box{
    display: flex;
    flex-wrap: wrap;
    width: 100vw;
    justify-content: center;
}

.image-nasa{
    width: 100px;
    height: 100px;
    object-fit: cover;
    padding: 5px;
}
</style>