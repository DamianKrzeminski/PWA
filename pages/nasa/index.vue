<template>
    <div>
        <div class="search-box">
            <h1>Nasa - {{ lookingForItem }} </h1>
            <div class="searcher">
                <input type="text" v-model="lookingForItem" placeholder="search...">
                <button @click="$event = find()">Search</button>
            </div>
        </div>

        <div class="loader" v-if="loader">
            <svg xmlns="http://www.w3.org/2000/svg" width="75" height="27" viewBox="0 0 75 27">
                <g fill-rule="evenodd">
                    <polygon points="6.1 14.9 7.7 19.4 12.3 19.5 8.5 22.2 10 26.7 6.1 24 2.3 26.7 3.7 22.2 0 19.5 4.6 19.4"/>
                    <polygon points="20.4 4.1 21.8 8.5 26.6 8.5 22.8 11.4 24.3 15.8 20.4 13.1 16.6 15.8 18 11.4 14.3 8.5 18.9 8.5"/>
                    <polygon points="37.9 0 39.3 4.5 44 4.5 40.2 7.3 41.6 11.8 37.9 9 34 11.8 35.4 7.3 31.7 4.5 36.3 4.5"/>
                    <polygon points="54.9 4.1 56.3 8.5 61 8.5 57.2 11.4 58.6 15.8 54.9 13.1 51 15.8 52.4 11.4 48.6 8.5 53.4 8.5"/>
                    <polygon points="68.9 15.2 70.3 19.7 75 19.8 71.2 22.5 72.7 27 68.9 24.3 65 27 66.4 22.5 62.7 19.8 67.3 19.7"/>
                </g>
            </svg>
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
            loader: false,
            dataArr: [],
            lookingForItem: "sun"
        }
    },
    methods:{
        find(){
            this.fetchData(this.lookingForItem);
        },
        async fetchData(search){
            this.loader = true;
            await axios.get('https://images-api.nasa.gov/search?q=' + search)
            .then(res => {
                this.dataArr = res.data.collection.items;
                this.loader = false;
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

.loader svg {
  width: 100vw;
  height: 108px;
}
.loader svg polygon {
  fill: #ccc;
  color: #ccc;
  animation: change 2.4s infinite;
}
.loader svg polygon:nth-child(1) {
  animation-delay: 0.4s;
}
.loader svg polygon:nth-child(2) {
  animation-delay: 0.8s;
}
.loader svg polygon:nth-child(3) {
  animation-delay: 1.2s;
}
.loader svg polygon:nth-child(4) {
  animation-delay: 1.6s;
}
.loader svg polygon:nth-child(5) {
  animation-delay: 2s;
}
@keyframes change {
  0% {
    fill: #ccc;
    color: #ccc;
  }
  30% {
    fill: #da3d18;
    color: #da3d18;
  }
  100% {
    fill: #ccc;
    color: #ccc;
  }
}
</style>