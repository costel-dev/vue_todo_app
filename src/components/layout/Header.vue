<template>
  <header class="header">
    <h1>
      Todo
      <a href="https://vuejs.org/" target="_blank" rel="noopener noreferrer"
        ><img src="../../assets/logo.png" alt="vue logo"
      /></a>
      List
    </h1>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped>
.header {
  background: #333;
  color: #fff;
  text-align: center;
  padding: 10px;
}

.header img {
  width: 40px;
  height: auto;
}

.header a {
  color: #fff;
  padding-right: 5px;
  text-decoration: none;
}

.header a:hover {
  color: rgb(64, 199, 147);
}
</style>
