<template>
  <div class="container">
    <div class="row justify-content-center align-item-center text-center">
      <div class="col-12 col-md-10 col-lg-8">
        <!-- Navigation Bar -->
        <NavBar/>

        <!-- App Information Component -->
        <AppInfo/>

        <!-- Route renderer -->
        <router-view/>


        <!-- Current Route info -->
        <h3>
          Current child route is: <span class="pink-text">{{route}}</span>
        </h3>
        
      </div>
    </div>
  </div>
</template>

<script>
import AppInfo from '@/components/AppInfo'
import NavBar from '@/components/NavBar'

export default {
  name: 'App',
  components: {
    NavBar,
    AppInfo
  },
  computed: {
    route() {
      return this.$route.fullPath // return the fullpath of the current child app route
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

.pink-text {
  color: #FF4083;
}
</style>
