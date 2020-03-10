<template>
    <div class="todoitem" v-bind:class="{'is-completed':todo.completed}">

        <input type="checkbox" v-if="!todo.showEdit" v-on:click="completed">
        <p v-if="!todo.showEdit">{{todo.title}}</p>
        <input type="text" name="edit" v-if="todo.showEdit" v-model="todo.title" >
        <input type="button" class="save-btn" value="save" v-if="todo.showEdit" @click="save">
        <input type="button" class="edit-btn" value="Edit" v-if="!todo.showEdit" @click="showEdit">
        <input type="button" class="delete-btn" value="Delete" @click="$emit('del-it' , todo.id)">
      
    </div>
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