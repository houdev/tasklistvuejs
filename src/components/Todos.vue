<template>
    <div id="Todos">
        <div v-bind:key="todo.id" v-for="todo in todos">

           <Todoitem v-bind:todo="todo" v-on:del-it="$emit('del-it', todo.id)" />

        </div>
    </div>
</template>

<script>
import Todoitem from './Todoitem.vue'

export default {
    name:"Todos",
    components: {
        Todoitem
    },
    props:["todos"]
    
}
</script>
