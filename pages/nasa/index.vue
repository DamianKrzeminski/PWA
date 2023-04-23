<template>
    <div>
        <div class="search-box">
            <h1>Nasa - {{ lookingForItem }} </h1>
            <div class="searcher">
                <input type="text" v-model="lookingForItem" placeholder="search...">
                <button @click="$event = find()">Search</button>
            </div>
        </div>
        <div class="img-nasa-box">
            <template v-for="(value) in dataArr">
                <template v-for="(link, index) in value.links">
                    <img v-if="index === 0" @click="setModal(link.href)" class="image-nasa" :src="link.href" :data-indec="index"/>
                </template>
            </template>
        </div>
    </div>
</template>

<script>
import axios from "axios";
export default {
    name: "index",
    created(){
        this.fetchData(this.lookingForItem)
    },
    data(){
        return{
            dataArr: [],
            lookingForItem: "sun"
        }
    },
    methods:{
        find(){
            this.fetchData(this.lookingForItem);
        },
        async fetchData(search){
            await axios.get('https://images-api.nasa.gov/search?q=' + search)
            .then(res => {
                this.dataArr = res.data.collection.items;
            })
            .catch(error => {
                console.log(error)
            })
        },
        setModal(value) {
            const data = {
                state: true,
                content: value
            }
            this.$nuxt.$emit('runModal', data);
        },
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

.image-nasa:hover{
    border: 10px solid royalblue;
}

.searcher{
    display: flex;
    justify-content: center;
}

.search-box{
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>