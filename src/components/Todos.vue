<template>
    <div id="Todos">

        <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">Mark it Done</th>
          <th class="text-left">Title</th>
          <th class="text-left">Edit</th>
          <th class="text-left">Delete</th>
        </tr>
      </thead>
        <tbody>
            

            <Todoitem v-bind:key="todo.id" v-for="todo in todos" v-bind:todo="todo" v-on:del-it="$emit('del-it', todo.id)"  />

           
        </tbody>
        </template>
  </v-simple-table>
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
