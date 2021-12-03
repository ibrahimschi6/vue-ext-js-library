<template>

    <div class="product" >
        <strong>Product Name</strong>
        <p>{{ product2.title }}</p>
        <p>Description</p>
        <p>{{ product2.description }}</p>
        <strong>Price: {{product2.price}} Stock: {{product2.count}}</strong>
        <br/>
        <br/>
        <button @click="addToChart(product2)">Add to Chart</button>
    </div>
</template>
<script>
export default {
    props:["product2"],
    methods:{
        addToChart(v){
            this.$emit("addToChartEvent",v)
            }
        }    
    }
</script>
<style>
.product{
    padding:  5px;
    border: 1px dashed;
    margin-bottom: 5px;
}
.product:hover{
    border:2px solid #666
}
</style>