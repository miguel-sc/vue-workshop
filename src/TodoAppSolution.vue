<template>
  <div>
    <h1>Vue Todo App</h1>
    <section>
      <h4>
        <label>
          <input type="checkbox" v-model="showComplete">
          Show Completed
        </label>
      </h4>
      <TodoList :todos="filteredTodos"/>
      <form v-on:submit.prevent="addTodo">
        <input type="text" v-model="text" placeholder="Add new!">
        <button :disabled="submitIsDisabled" type="submit">Add Todo</button>
      </form>
    </section>
  </div>
</template>

<script>
import TodoList from './components/TodoListSolution.vue'

export default {
  components: {
    TodoList
  },
  data: () => ({
    todos: [
      {
        name: "Learn Vue",
        complete: false
      },
      {
        name: "Buy groceries",
        complete: false
      }
    ],
    text: "",
    showComplete: true
  }),
  computed: {
    filteredTodos() {
      return this.todos.filter(todo =>
        this.showComplete ? true : !todo.complete
      );
    },
    submitIsDisabled() {
      return this.text == "";
    }
  },
  methods: {
    addTodo() {
      this.todos.push({
        name: this.text,
        complete: false
      });
      this.text = "";
    }
  }
};
</script>
