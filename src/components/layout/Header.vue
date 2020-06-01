<template>
  <header class="header container-fluid">
    <h1>Todo List</h1>
    <div id="nav">
      <router-link to="/">Home</router-link>|
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style scoped>
.header {
  background: rgb(127, 140, 141);
  background: linear-gradient(
    90deg,
    rgba(127, 140, 141, 1) 49%,
    rgba(70, 70, 70, 1) 100%
  );
  color: white;
  text-align: center;
  padding: 10px;
}
.header a {
  color: white;
  padding-right: 5px;
  text-decoration: none;
}
#nav a.router-link-exact-active {
  color: white;
}
#nav a {
  font-weight: bold;
  color: smokewhite;
}
</style>