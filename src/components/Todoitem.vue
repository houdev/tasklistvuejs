<template>
    
        <tr>
        <td v-if="!todo.showEdit">
          <v-checkbox v-on:click.native="completed"></v-checkbox>
        </td>
        <td>
          <p 
          v-bind:class="{'is-completed':todo.completed}"
          v-if="!todo.showEdit" 
          class="title blue--text text--darken-4"
          >
              {{todo.title}}
          </p>
        </td>
        <td v-if="todo.showEdit">
         <v-text-field v-model="todo.title"></v-text-field>
        </td>
        <td v-if="todo.showEdit">
         <v-btn fab color="success"  @click="save">
            <v-icon>
              mdi-note-plus
            </v-icon>
          </v-btn>
        </td>
        <td v-if="!todo.showEdit">
          <v-btn fab color="primary"  @click="showEdit">
            <v-icon>
              mdi-pencil
            </v-icon>
          </v-btn>
        </td>
        <td>
          <v-btn fab color="error" @click="$emit('del-it' , todo.id)">
           <v-icon>mdi-delete</v-icon>
          </v-btn>
        </td>
      </tr>
 
</template>

<script>

export default {

    name:'Todoitem',
    props: ["todo"],
    methods:{
        completed(){
            this.todo.completed = !this.todo.completed;
        },
        showEdit(){
            this.todo.showEdit = true;
        },
        save(){
            this.todo.showEdit = false;
         },
    }
}

</script>

<style scoped>

p{
    display: inline;
    font-size: 18px;
    margin-left: 10px;
    margin-right: 10px;
}
.is-completed{
    text-decoration: line-through;
}

.edit-btn{
    padding: 5px;
    margin: 3px;
    background:teal;
    color:white;
    border: none;
}

.delete-btn{
    padding: 5px;
    margin: 3px;
    background: tomato;
    color:white;
  
    border: none;
}
.save-btn{
    padding: 5px;
    margin: 3px;
    background:mediumseagreen;
    color:white;
    border: none;
}

</style>