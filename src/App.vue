<template>
  <div id="app">
    <TopBar :linkedTracksList="linkedTracksList" @genreSelected="getGenreSelected" />
    <TracksList @linkedTracksList="getLinkedTracksList" :genreSelected="linkedGenre" />
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
      linkedTracksList: [],
      linkedGenre: ''
    }
  },
  methods: {
    getLinkedTracksList(tracksList) {
      this.linkedTracksList = tracksList;
    },
    getGenreSelected(genre) {
      this.linkedGenre = genre;
      console.log('App vue linked genre: ' + this.linkedGenre)
    }
  }
}
</script>

<style lang="scss">
  @import './styles/bootstrap-overwrite.scss';
  @import '~bootstrap/scss/bootstrap.scss';

  @import './styles/general.scss';
</style>
