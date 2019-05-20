<template>
  <ul>
    <!-- The v-for attribute that we see here repeats whatever tag it is on (in this case, a LI) one time for each element of the referenced list, which in this case is our list. Each repetition, the property has a different value.  -->
    <li v-for="(todo, index) in todos" :key="index" class="todo-list-item">
      <label>
        <input type="checkbox" v-model="todo.complete">
        <!-- TODO: You can insert text with the double curly braces syntax {{}}. Try to insert the name of the todo item into this label. -->
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

<!-- TODO: Write a css class todo-list-item that adds a margin of 10px to every item of the todolist. You can add the class to the correct element in the template by setting the class attribute of that element. -->
<style scoped>
.todo-list-item {
  margin: 10px;
}
</style>