<template>
  <div id="app">
    <Header />
    <br />
    <addtodo v-on:new-todo="addTodo" />
    <br />
    <Todos v-bind:todos="todos" v-on:del-it="deleteit"/>
  </div>
</template>

<script>

import Todos from './components/Todos.vue';
import Header from './components/layout/Header.vue';
import Addtodo from './components/Addtodo.vue';

export default {
  name: 'App',
  components: {
    Todos,
    Header,
    Addtodo
  },
  data (){
    return {
      todos:[
        {
          id:1,
          title: 'Learn Vue.js',
          completed: false,
          showEdit: false,
        },
        {
          id:2,
          title: 'Master Vue.js',
          completed: false,
          showEdit: false,
        },
        {
          id:3,
          title: 'Build An App',
          completed: false,
          showEdit: false,
        }
      ]
    }
  },
  methods:{
    deleteit(id){
      this.todos = this.todos.filter(todo => todo.id !== id );
    },
    addTodo(newtodo){
      this.todos.push(newtodo);
    },
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
  margin-top: 0px;
}
</style>
