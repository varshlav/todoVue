<template>
  <div id="app">
    <div>
      <input id="add" v-model="task"> <button @click="addTodo">Add Task </button>
    </div>
   Following is the List - 
    
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
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
        total : 3
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
