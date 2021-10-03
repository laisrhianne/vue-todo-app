<script>
export default {
  props: {
    title: String,
    done: Boolean,
    handleDelete: function () {}
  }
}
</script>

<template>
  <div class="todo">
    <div class="todo-container">
      <input id="todo-check" type="checkbox" label="Teste" v-model="done">
      <p id="todo-title" v-bind:class="{ done }">{{title}}</p>
    </div>
    <font-awesome-icon id="delete-todo" icon="trash" @click="handleDelete" />
  </div>
</template>


<style>
div.todo {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;

  border: 1px solid #4188ce;
  border-radius: 5px;
  width: 50%;
  padding: 10px;
}

div.todo-container {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
}

#todo-title {
  margin: 0 10px;
}

.done {
  text-decoration: line-through;
}

#delete-todo {
  color: red;
  width: 20px;
  height: 20px;
  
  cursor: pointer;
}


#delete-todo:active {
  opacity: 0.7;
}

</style>