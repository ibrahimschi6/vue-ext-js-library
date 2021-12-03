<template>
  <div id="container">
    <div id="row">
       <div class="col-md-8 col-offset-md text-center">
          <h3 class="mt-5">Todo List </h3>
          <hr/>
          <div id="row">   
            <div class="col-md-6 offset-md-3 d-flex flex-row ">
              <input type="text" v-model="todoText" >
              <button @click="addTodo()" class="btn btn-primary btn-small" > Add </button>
            </div> 
          </div>
          <hr>
            <div class="todo-container">
              <Todo v-for="todo in todoList" :key="todo.id" :todo="todo" @deleteTodo="deleteTodo($event)"/>
            </div>
       </div>
    
    </div>
    <button @click="fetchData()" class="btn btn-primary btn-small" > Fetch Data </button>
  </div>
</template>

<script>
import Todo from "@/components/Todo"
import axios from "axios"

export default {
  name: 'App',  
  components: {
    Todo
  },
  data(){    
    return {
      todoText:"",
      todoList:[]
    }
  
  },
  created(){
      
      axios.get("https://vuejs-api-project-default-rtdb.europe-west1.firebasedatabase.app/todo.json")
      .then(response =>{
        
        for (let key in  response.data) {
          //console.log(response.data[key]) 
          let todo = {
            id :key,
            text: response.data[key].text
          }
          this.todoList.push(todo)
        }
      })
      .catch()
    },
  methods:{
    addTodo(){
      axios.post("https://vuejs-api-project-default-rtdb.europe-west1.firebasedatabase.app/todo.json",{text:this.todoText})
      .then(response =>{
         let todo = {
            id :response.data.name,
            text: this.todoText
          }
          this.todoList.push(todo)
      })
      .catch(e=>{
        console.log(e)
      })
    },
    deleteTodo(todoId){
      axios.delete("https://vuejs-api-project-default-rtdb.europe-west1.firebasedatabase.app/todo/"+todoId+".json")
      .then(response =>{
        
        let index = this.todoList.findIndex(i=>{
            return i.id ==todoId
          })

        console.log(index+" "+response)
        
        this.todoList.splice(index,1)
 
      })
      .catch(e=>{
        console.log(e)
      })
    }    
  }

}
</script>

<style>

</style>
