<template>
  <div class="todo-item">
    <input type="checkbox" v-model="todo.completed" />
    <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
    <button @click="removeTodo">Delete</button>
  </div>
</template>

<script setup>
defineProps({
  todo: Object,
  removeTodo: Function,
});
</script>

<style lang="scss" scoped>
.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  background-color: #f9f9f9;
  margin-bottom: 8px;
  border-radius: 4px;

  span {
    flex: 1;
    margin-left: 10px;
  }

  .completed {
    text-decoration: line-through;
    color: #777;
  }

  button {
    background: none;
    border: none;
    color: red;
    cursor: pointer;
  }
}
</style>
