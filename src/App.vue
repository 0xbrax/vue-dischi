<template>
  <div id="app">
    <TopBar :linkedTracksList="linkedTracksList" />
    <TracksList @linkedTracksList="getLinkedTracksList" />
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
  },
  data() {
    return {
      linkedTracksList: []
    }
  },
  methods: {
    getLinkedTracksList(tracksList) {
      console.log(tracksList)
      this.linkedTracksList = tracksList;
    }
  }
}
</script>

<style lang="scss">
  @import './styles/bootstrap-overwrite.scss';
  @import '~bootstrap/scss/bootstrap.scss';

  @import './styles/general.scss';
</style>
