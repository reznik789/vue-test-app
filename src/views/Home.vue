<template>
  <div>
    <AddTodo v-on:add-todo="addTodo" />
    <Todos :todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
import axios from "axios";
export default {
  name: "Home",
  components: {
    Todos,
    AddTodo
  },

  data: function() {
    return {
      todos: []
    };
  },
  methods: {
    deleteTodo: function(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo: function(newTodo) {
      this.todos = [...this.todos, newTodo];
    }
  },
  created: async function() {
    try {
      const res = await axios.get("https://cors-anywhere.herokuapp.com/https://jsonplaceholder.typicode.com/todos");
      this.todos = res.data;
    } catch (e) {
      console.log(e);
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
