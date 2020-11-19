<template>
  <div>
    <div v-for="todo in todos" v-bind:key="todo.id">
      <TodoItem :todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>

<script>
//import your components in order to render them
import TodoItem from "./TodoItem";

export default {
  name: "Todos",
  //add your imported file as a component
  components: {
    TodoItem,
  },
  props: ["todos"],
};
</script>

<style scoped></style>
