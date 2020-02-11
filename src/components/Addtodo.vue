<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add Item" />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
    name:"AddTodo",
    data(){
        return{
title:''
            }
            },
            methods:{
addTodo(e){
    e.preventDefault();
    
    const newToDo = {
 
title:this.title,
completed:false
        }
        this.$emit('add-todo',newToDo);
        this.title = "";
        }
                }
})
</script>
<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
}
</style>