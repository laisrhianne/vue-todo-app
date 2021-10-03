<script setup>
import { ref } from 'vue'

import Todo from '../components/Todo.vue'

const title = ref('')
const done = ref(true)
const todos = ref([])

function handleAddTodo (event) {
  event.preventDefault()
  todos.value.push({title: title.value, done: false})
}

function handleDeleteTodo (event) {
  const index = todos.value.findIndex((todo) => todo.title = event.title)
  todos.value.splice(index, 1)
}

</script>

<template>
  <header>
    <h1>Todo App</h1>
  </header>

  <form class="form" @submit="handleAddTodo">
    <input id="title" type="text" v-model="title" >
    <div id="submit" @click="handleAddTodo">
      <font-awesome-icon icon="plus"/>
    </div>
  </form>

  <li class="todos" v-for="(todo, index) in todos" v-bind:key="index">
    <Todo :title="todo.title" :done="todo.done" @deleteTodo="handleDeleteTodo"/>
  </li>
</template>

<style scoped>
form.form {
  height: 35px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  vertical-align: middle;
  margin: 30px 0;
}

input#title {
  height: 35px;
  width: 25%;
  font-family: sans-serif;
  font-size: 16px;
  vertical-align: middle;
  padding: 1px 2px;
  box-sizing: border-box;
}

div#submit {
  height: 35px;
  width: 5%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #4188ce;
  vertical-align: middle;
  font-size: 16px;

  text-align: center;
  color: #FFF;
  cursor: pointer;

  box-sizing: border-box;
  border: 1px solid #000;
  border-radius: 0 5px 5px 0;
  padding: 1px 2px;
}

div#submit:active {
  opacity: 0.7;
  box-shadow: 0 0 5px -1px rgba(0,0,0,0.6);
}

li.todos {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  margin-top: 10px;
}
</style>
