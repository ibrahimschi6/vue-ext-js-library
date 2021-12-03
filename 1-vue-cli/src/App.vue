<template>
<div>
  <myCom/>
  <div class="cart">
    <h3>Chart Items</h3>
  <ul>
    <li v-for="item in chartItems" :key="item.id">{{ item.title }}</li>
    <p v-if="chartItems.length == 0">Your Chart is empty. Shop now !!</p>
  </ul>
  </div>
  <hr/>
 <myProduct @addToChartEvent="chartItems.push($event)" :product2="product" v-for="product in productList" :key="product.id"/>
</div>
  
</template>

<script>
import MainContainer from "@/components/MainContainer"
import Product from './components/Product.vue'
export default{
  components :{
    myCom : MainContainer,
    myProduct : Product    
  },
  data(){
    return{
      text:"lorem ipsum",      
            productList:[
                {
                    id:1,
                    title:"MacBook Pro",
                    price: 1300,
                    count: 0,
                    description : "Product Details"
                },
                {
                    id:2,
                    title:"iPhone",
                    price: 800,
                    count: 20,
                    description : "Product Details 2"
                },
                {
                    id:3,
                    title:"Keyboard",
                    price: 10,
                    count: 100,
                    description : "Product Details 3"
                }

            ], chartItems:[]

    }
  }
  
}

</script>

<style>
.chart{
  margin-bottom: 50px;
  text-align: left;
}
</style>