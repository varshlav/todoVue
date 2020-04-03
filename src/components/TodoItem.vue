<template>
    <div v-bind:class="{'is-complete':todo.completed}">
        
        <p><input type="checkbox" v-on:change="changeStatus"> {{todo.title}}
            <button @click="$emit('delete',todo.id)"> X </button>
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
.is-complete{
    text-decoration: line-through;
}
</style>