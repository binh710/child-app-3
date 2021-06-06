<template>
  <div id="nav">
    <router-link @click="updateParentRoute('/')" to="/">Home</router-link> |
    <router-link @click="updateParentRoute('/about')" to="/about">About</router-link>
  </div>
</template>

<script>
export default {
  name: 'NavBar',
}
</script>

<style scoped>
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>

