<template>
  <div id="nav">
    <router-link @click="updateParentRoute('/')" to="/">Home</router-link> |
    <router-link @click="updateParentRoute('/about')" to="/about">About</router-link>
  </div>
  <router-view/>
  <p>
    This application aims to show you how route syncing can be done across the parent & child app
  </p>
  <h3>
    Current child route is: {{route}}
  </h3>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      stitcherAppDomain: process.env.VUE_APP_STITCHER_DOMAIN
    }
  },
  computed: {
    route() {
      return this.$route.fullPath
    }
  },
  methods: {
    updateParentRoute(url) {
      if (url !== this.route) {
        const msg = {
          action: 'update route',
          route: url
        }
        try {
          window.parent.postMessage(msg, this.stitcherAppDomain);
        } catch(e) {
          console.error('error posting message to stitcher app', e);
        }
      }
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

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
