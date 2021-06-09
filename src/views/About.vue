<template>
  <div class="about">
    <h1 class="pink-text">About page</h1>
    <div>
      <button class="btn btn-secondary" @click="navigateToHome()">
        Navigate to Home
      </button>
    </div>
    <br/>
  </div>
</template>

<script>
import { updateStitcherApp } from '@/helpers/updateStitcherApp'

export default {
  name: 'About',
  methods: {
    navigateToHome() {
      // create the message to inform stitcher app
      const msg = {
        action: 'update route',
        route: '/'
      }
      
      // call global helper method to update stitcher app about the route change
      this.$router.push('/')
      updateStitcherApp(msg)
    }
  }
}
</script>

<style scoped>
h1 {
  font-weight: bold;
}
</style>
