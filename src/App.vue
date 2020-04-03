<template>
  <div id="app">
    <header class="header">
      <h1>TodoList</h1>
    </header>
    <div class="todocontent">
      <div class="addtodo">
        <input type="text" id="add" v-model="task"/> 
        <button type="submit" @click="addTodo" class="btn">Add Task </button>
      </div>
        
      <h3> Following is the List - </h3>
      <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    </div>
  </div>
</template>

<script>
import Todos from './components/Todos.vue'

export default {
  name: 'App',
  components: {
    Todos
  },
  data(){
    return {
      task: '',
      todos: [
        {id: 1,
        title: 'Buy Groceries',
        completed: false
        },
        {id: 2,
        title: 'Wash Clothes',
        completed: true
        },
        {id: 3,
        title: 'Complete Assignment',
        completed: false
        }],
        total : 4
    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id); 
    },
    addTodo(){
      this.todos.push({
      id: this.total++,
      title: this.task,
      completed: false
    });
    this.task = "";
  }
  }
}
</script>

<style>

*{
  box-sizing :border-box;
  margin:0;
  padding:0;
}
body{
  font-family: Arial, Helvetica, sans-serif;
  line-height:1.4;
}
#app{
  width:800px;
  margin: 10px auto;
  border: 1px solid #000;
}
.header{
  background:#333;
  color:#fff;
  text-align:center;
  padding:10px;
}
.header a{
  color:#fff;
  padding-right:5px;
  }

   .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
    border: 1px solid #555;
    border-top-right-radius: 5px;
    border-bottom-right-radius: 5px
  }
  .btn:hover {
    background: #666;
  }
 
  .addtodo {
    display: flex;
     padding:10px;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
    border-top-left-radius: 5px;
    border: 1px solid #737171;
    border-bottom-left-radius: 5px;
    font-size:14px;
  }
  input[type="submit"] {
    flex: 2;
  }
  .todocontent h3{
   padding:10px;

  }
</style>
