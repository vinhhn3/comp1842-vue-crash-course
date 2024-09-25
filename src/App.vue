<template>
  <div class="todo-app">
    <h1>Todo List</h1>
    <form @submit.prevent="addTodo">
      <input v-model="newTodo" type="text" placeholder="Add a new todo" />
      <button type="submit">Add</button>
    </form>

    <div class="todo-list">
      <TodoItem
        v-for="(todo, index) in todos"
        :key="index"
        :todo="todo"
        :removeTodo="() => removeTodo(index)"
      />
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import TodoItem from "./components/TodoItem.vue";

// Reactive state
const newTodo = ref("");
const todos = ref([
  { text: "Learn Vue.js", completed: false },
  { text: "Build a Todo App", completed: false },
]);

// Add a new todo
const addTodo = () => {
  if (newTodo.value.trim()) {
    todos.value.push({
      text: newTodo.value,
      completed: false,
    });
    newTodo.value = "";
  }
};

// Remove a todo by index
const removeTodo = (index) => {
  todos.value.splice(index, 1);
};
</script>

<style lang="scss">
.todo-app {
  max-width: 400px;
  margin: 100px auto;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: #ffffff;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

form {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;

  input {
    flex: 1;
    padding: 10px;
    margin-right: 10px;
    border-radius: 5px;
    border: 1px solid #ddd;
  }

  button {
    padding: 10px 15px;
    background-color: #42b883;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;

    &:hover {
      background-color: #38a06f;
    }
  }
}

.todo-list {
  margin-top: 20px;
}
</style>
