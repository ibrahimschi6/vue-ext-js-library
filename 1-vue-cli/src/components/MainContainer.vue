<template>
<div class="container">
  {{text}}
</div>
  
</template>

<script>
export default{
  data(){
    return{
      text:"lorem ipsum"
    }
  }
  
}

</script>

<style>
.container{
    display: flex ;
    justify-content: center;
    align-items: center;
    margin-right: 5px;
}
</style>