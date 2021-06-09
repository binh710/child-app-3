<template>
  <div id="nav">
    <router-link @click="navigateToRoute('/')" to="/">Home</router-link> |
    <router-link @click="navigateToRoute('/about')" to="/about">About</router-link>
  </div>
</template>

<script>
import { updateStitcherApp } from '@/helpers/updateStitcherApp'

export default {
  name: 'NavBar',
  computed: {
    route() {
      return this.$route.fullPath // return the fullpath of the current child app route
    }
  },
  methods: {
    navigateToRoute(url) {
      // simple check for url change
      if (url !== this.route) {
        // create the message to inform stitcher app
        const msg = {
          action: 'update route',
          route: url
        }
        
        // call global helper method to update stitcher app about the route change
        updateStitcherApp(msg)
      }
    }
  }
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

