<template>
  <div class="todo-item" v-bind:class="{ 'is-complete': todo.completed }">
    <input type="checkbox" v-on:change="markComplete" />
    <p>{{ todo.title }}</p>
    <button @click="$emit('del-todo', todo.id)" class="del">X</button> 
  </div></template
>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
        this.todo.completed = !this.todo.completed;
    }
  }
});
</script>
<style scope>
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
</style>
