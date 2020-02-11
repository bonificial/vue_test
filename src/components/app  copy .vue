<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from "./components/layout/header";
import Todos from "./components/Todos";
import axios from 'axios';
import AddTodo from "./components/Addtodo";
export default {
  name: "App",
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      msg: "Hello World there",
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(  this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err=>console.log(err));
    
    },
    addTodo(newTodo) {
      const {title,completed} = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {title,completed})
      .then(res=>this.todos = [...this.todos, newTodo])
      .catch(err=>console.log(err));
     
    }
  },
  created(){
axios.get("https://jsonplaceholder.typicode.com/todos?_limit=8")
.then(res=> this.todos = res.data)
.catch(e=> console.log(e))
    }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
