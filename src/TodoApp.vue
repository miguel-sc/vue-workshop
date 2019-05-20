<template>
  <div>
    <h1>Vue TodoMVC</h1>
    <section>
      <h4>
        <label>
          <!-- TODO: The v-model attribute allows you to create a two way databinding. Try to bind the value of the input to our showComplete property. -->
          <input type="checkbox" v-model="showComplete">
          Show Completed
        </label>
      </h4>

      <!-- TODO: The TodoList component receives a prop named "todos" and renders all items in that array in a list. You can bind your own properties to subcomponents with <Element :propName="ownPropName" />. It begins with a colon (:), indicating that Vue should interpret the value as an expression, and not a string. Try passing the filteredTodos into the TodoList. -->
      <TodoList :todos="filteredTodos"/>

      <!-- Here, a form is used to contain the submit button (which allows keyboard input to be captured.) Notice the v-on directive being used. The .prevent method works the same as submit, but also prevents the default behavior. -->
      <form v-on:submit.prevent="addTodo">
        <!-- TODO: The v-model attribute allows you to create a two way databinding. Try to bind the value of the input to our text property. -->
        <input type="text" v-model="text" placeholder="Add new!">

        <!-- TODO: You can enable/disable a button by giving the "disabled" prop a boolean value. Try it out with our submitIsDisabled property. -->
        <button :disabled="submitIsDisabled">Add Todo</button>
      </form>
    </section>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
  components: {
    TodoList
  },
  /**
   * The data method is called by the component, and the values returned become the data model for that component.
   */
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

  /**
   * Computed properties are like data, except instead of a specific value, they are a function. The function is called and then the component can use the value that is returned, like a normal property. Vue components can access their own properties through the "this" special keyword.
   */
  computed: {
    /**
     * TODO: Returns a list of todos with the completed ones removed, when the showComplete is false.
     */
    filteredTodos() {
      //return this.todos;
      return this.todos.filter(todo =>
        this.showComplete ? true : !todo.complete
      );
    },

    /**
     * TODO: A boolean indicating if the submit button should be disabled, based on the content of the input box.
     * Disable the button if the text is empty.
     */
    submitIsDisabled() {
      return this.text == "";
    }
  },

  /**
   * The methods property of a Vue app contains functions, which are usually called from the template, though they can be called from elsewhere in the script, too.
   * If you look in the template, you will find a form which calls this "addTodo()" method.
   * Methods are the preferred way of doing an action that changes the data model.
   */
  methods: {
    /**
     * TODO: addTodo() takes whatever is in the text input box, and makes it into a list element. Vue components can access their own properties through the "this" special keyword.
     */
    addTodo() {
      this.todos.push({
        name: this.text,
        complete: false
      });
      this.text = ``;
    }
  }
};
</script>
