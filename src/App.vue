<template>
  <div id="app">
    <TracksList />
  </div>
</template>

<script>
import TracksList from './components/TracksList.vue'

export default {
  name: 'App',
  components: {
    TracksList
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
