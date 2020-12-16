<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
// import your componentw that you want to render
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";

import axios from "axios";

export default {
  name: "Home",
  components: {
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(() => (this.todos = this.todos.filter((todo) => todo.id !== id)))
        .catch((err) => console.log(err));
    },
    addTodo(newTodo) {
      //destructuring our value from newTodo
      const { title, completed } = newTodo;
      //make a post request to jsonplaceholder
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed,
        }) //our newTodo will be res.data so we need to added to our array
        .then((res) => (this.todos = [...this.todos, res.data]))
        .catch((err) => console.log(err));
    },
  },
  // created() is working the same as componentDidMount in react
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=3")
      .then((res) => (this.todos = res.data))
      .catch((err) => console.log(err));
  },
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

.btn {
  display: inline-block;
  border: none;
  background: rgb(64, 199, 147);
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  filter: brightness(120%);
}
</style>
