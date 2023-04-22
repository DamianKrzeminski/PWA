<template>
    <div>
      <div class="products-block">
        <h1>Products</h1>
        <div class="product-list">
          <div class="product-item">
            <span class="product-detail">Name</span>
            <span class="product-detail">Count</span>
            <span class="product-detail">Category</span>
            <span class="product-detail product-detail-end">Cost</span>
          </div>
          <div class="product-item">
            <span class="product-detail">{{ camera.name }}</span>
            <span class="product-detail">{{ camera.count }}</span>
            <span class="product-detail">{{ camera.category }}</span>
            <span class="product-detail product-detail-end">{{ camera.cost }}</span>
          </div>
          <div class="product-item">
            <span class="product-detail">{{ Lenovo.name }}</span>
            <span class="product-detail">{{ Lenovo.count }}</span>
            <span class="product-detail">{{ Lenovo.category }}</span>
            <span class="product-detail product-detail-end">{{ Lenovo.cost }}</span>
          </div>
          <div class="product-item">
            <span class="product-detail">{{ camera2.name }}</span>
            <span class="product-detail">{{ camera2.count }}</span>
            <span class="product-detail">{{ camera2.category }}</span>
            <span class="product-detail product-detail-end">{{ camera2.cost }}</span>
          </div>
          <div class="product-item">
            <span class="product-detail">{{ Acer.name }}</span>
            <span class="product-detail">{{ Acer.count }}</span>
            <span class="product-detail">{{ Acer.category }}</span>
            <span class="product-detail product-detail-end">{{ Acer.cost }}</span>
          </div>
          <div class="product-item">
            <span class="product-detail">{{ SteelSeries.name }}</span>
            <span class="product-detail">{{ SteelSeries.count }}</span>
            <span class="product-detail">{{ SteelSeries.category }}</span>
            <span class="product-detail product-detail-end">{{ SteelSeries.cost }}</span>
          </div>
        </div>
      </div>
    </div>
  
  </template>
  
  <script>
  import Product from '../components/models/product' 
  export default {
    name: 'Products',
    data(){
    return {
      camera: null,
      Lenovo: null,
      camera2: null,
      Acer: null,
      SteelSeries: null
    }
  },
  created() {
    this.camera = this.product('Nikon', '53', 'Cameras', '2500zł')
    this.Lenovo = this.product('Lenovo', '23', 'Laptops', '9500zł')
    this.camera2 = this.product('Fujitsu', '153', 'Cameras', '22500zł')
    this.Acer = this.product('Laptop', '13', 'Laptops', '3500zł')
    this.SteelSeries = this.product('SteelSeries', '253', 'Mouse', '500zł')
  },
  methods: {
    product(name, count, category, cost){
      return new Product(name, count, category, cost);
    }
  },
  components: { Product }
  }
  </script>
  
  <style scoped>

.products-block{
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 50%;
  margin-left: 10px;
}
  .product-list{
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  .product-item{
    display: flex;
    justify-content: space-between;
    width: 100%;
    border-bottom: 3px solid rgb(101, 101, 172);
  }

  .product-detail{
    display: flex;
    align-items: center;
    width: 15%;
    min-height: 25px;
  }

  .product-detail-end{
    justify-content: flex-end;
  }
  </style>