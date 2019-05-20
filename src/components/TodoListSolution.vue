<template>
  <ul>
    <li v-for="(todo, index) in todos" :key="index" class="todo-list-item">
      <label>
        <input type="checkbox" v-model="todo.complete">
        {{ todo.name }}
      </label>
    </li>
  </ul>
</template>

<script>
export default {
  name: "TodoList",
  props: {
    todos: Array
  }
};
</script>

<style scoped>
.todo-list-item {
  margin: 10px;
}
</style>