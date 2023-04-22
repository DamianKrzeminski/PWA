<template>
    <div class="box">
        <bigImage :image="bigimg.img" :alt="bigimg.alt"/>
        <div class="smallbox">
            <smallImage :image="smallimg1.img" :alt="smallimg1.alt"/>
            <smallImage :image="smallimg2.img" :alt="smallimg2.alt"/>
            <smallImage :image="smallimg3.img" :alt="smallimg3.alt"/>
            <smallImage :image="smallimg4.img" :alt="smallimg4.alt"/>
        </div>
    </div>
</template>

<script>
import bigImage from '../components/gallery/bigImage.vue'
import smallImage from '../components/gallery/smallImages.vue'
import Image from '../components/models/image'
export default {
  name: 'Gallery',
  data(){
    return {
      bigimg: null,
      smallimg1: null,
      smallimg2: null,
      smallimg3: null,
      smallimg4: null
    }
  },
  created() {
    this.bigimg = this.image("https://img.freepik.com/darmowe-zdjecie/zolty-zonkil-narcyz-kwitnacy-w-ogrodzie_127675-2729.jpg?w=826&t=st=1679759619~exp=1679760219~hmac=16bc530ed103e815ea90b0515168ca251845e2dcf4822f3f3cba293d01b28582", "bigimg")
    this.smallimg1 = this.image("https://img.freepik.com/darmowe-psd/wiosna-kwiatowy-tlo-podium_23-2150154136.jpg?w=740&t=st=1679759809~exp=1679760409~hmac=397d6d3bda0afec08cd704055ac0eec8f2a8c5f758b1327d1a0b2b34b0e29d06", "smallimg1")
    this.smallimg2 = this.image("https://img.freepik.com/darmowe-zdjecie/zolty-zonkil-narcyz-kwitnacy-w-ogrodzie_127675-2729.jpg?w=826&t=st=1679759619~exp=1679760219~hmac=16bc530ed103e815ea90b0515168ca251845e2dcf4822f3f3cba293d01b28582", "smallimg2")
    this.smallimg3 = this.image("https://img.freepik.com/darmowe-psd/wiosna-kwiatowy-tlo-podium_23-2150154136.jpg?w=740&t=st=1679759809~exp=1679760409~hmac=397d6d3bda0afec08cd704055ac0eec8f2a8c5f758b1327d1a0b2b34b0e29d06", "smallimg3")
    this.smallimg4 = this.image("https://img.freepik.com/darmowe-psd/wiosna-kwiatowy-tlo-podium_23-2150154136.jpg?w=740&t=st=1679759809~exp=1679760409~hmac=397d6d3bda0afec08cd704055ac0eec8f2a8c5f758b1327d1a0b2b34b0e29d06", "smallimg4")
  },
  methods: {
    image(img, alt){
      return new Image(img, alt);
    }
  },
  components: { bigImage, smallImage, Image },
}
</script>
<style scoped>
.box{
    display: flex;
    flex-direction: column;
}

.smallbox{
    display: flex;
    flex-direction: row;
}
</style>