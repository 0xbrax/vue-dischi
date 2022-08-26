<template>
  <div id="app">
    <TopBar />
    <TracksList />
  </div>
</template>

<script>
import TopBar from './components/TopBar.vue'
import TracksList from './components/TracksList.vue'

export default {
  name: 'App',
  components: {
    TopBar,
    TracksList
  }
}
</script>

<style lang="scss">
  @import '~bootstrap/scss/bootstrap.scss';
  @import './styles/general.scss';
</style>
