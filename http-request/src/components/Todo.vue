<template>

<div id="row">      
              <div class="col-md-9 offset-md-3 border d-flex flex-row justify-content-between align-items-center pa-2 pb-2">      
                <span>{{todo.text}}</span>
                
                  <button class="btn btn-danger btn-small" @click="$emit('deleteTodo',todo.id)" > Delete </button>
              </div>
            </div>
</template>
<script>
export default {
    props:["todo"]
}
</script>