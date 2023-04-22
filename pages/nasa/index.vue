<template>
    <div>
        <h1>Nasa {{ message }} </h1>
        <input type="text" v-model="message" placeholder="search...">
        <button @click="$event = find()">Search</button>
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
        this.fetchData(this.message)
    },
    data(){
        return{
            dataArr: [],
            message: "sun"
        }
    },
    methods:{
        find(){
            this.fetchData(this.message);
        },
        async fetchData(search){
            await axios.get('https://images-api.nasa.gov/search?q=' + search)
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