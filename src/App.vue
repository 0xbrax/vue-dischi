<template>
  <div id="app">
    <TopBar :linkedTracksList="linkedTracksList" @genreSelected="getGenreSelected" @artistSelected="getArtistSelected" />
    <TracksList @linkedTracksList="getLinkedTracksList" :genreSelected="linkedGenre" :artistSelected="linkedArtist" />
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
      linkedArtist: 'Seleziona artista',
      linkedGenre: 'Seleziona genere'
    }
  },
  methods: {
    getLinkedTracksList(tracksList) {
      this.linkedTracksList = tracksList;
    },
    getArtistSelected(artist) {
      this.linkedArtist = artist;
    },
    getGenreSelected(genre) {
      this.linkedGenre = genre;
    }
  }
}
</script>

<style lang="scss">
  @import './styles/bootstrap-overwrite.scss';
  @import '~bootstrap/scss/bootstrap.scss';

  @import './styles/general.scss';
</style>
