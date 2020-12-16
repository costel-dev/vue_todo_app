<template>
  <div>
    <form @submit.prevent="addTodo">
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="Add Todo..."
      />
      <input type="submit" value="Submit" class="btn" />
    </form>
    <div v-bind:class="{ 'show-alert': showAlert }">
      <span class="alert-message">Please add todo...</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
      showAlert: true,
    };
  },
  methods: {
    addTodo() {
      const newTodo = {
        title: this.title,
        completed: false,
      };
      // send it to parent
      if (this.title === "") {
        this.showAlert = false;
      } else {
        this.showAlert = true;
        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  height: 40px;
}

input[type="text"] {
  flex: 10;
  padding: 5px;
  outline: none;
}

input[type="submit"] {
  flex: 2;
  outline: none;
}

.show-alert {
  display: none;
}
.alert-message {
  color: red;
}
</style>
