<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        
        <p>
            <input class="checkbox" type="checkbox" v-on:change="changeStatus"> {{todo.title}}
            <button @click="$emit('delete',todo.id)" class="del"> X </button>
        </p>
    </div>
</template>
<script>
export default {
    name: 'TodoItem',
    props: ["todo"],
    methods: {
        changeStatus(){
            this.todo.completed = !this.todo.completed ;
        }
    }

    
}
</script>
<style scoped>
.todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
  .checkbox{
      margin-right:5px;
  }
</style>