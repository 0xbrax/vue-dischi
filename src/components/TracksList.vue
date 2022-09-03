<template>
    <section class="d-flex justify-content-center align-items-center">
        <div class="container">
            <div class="row g-5 justify-content-center">
                <div class="col-2" v-for="(track, trackIndex) in getFilteredTracksList" :key="trackIndex">
                    <TrackSingle class="track-card p-3" :track="track" />
                </div>
            </div>
        </div>

        <NowLoading v-if="isNowLoading == true" />
    </section>
</template>

<script>
import axios from 'axios'
import TrackSingle from '../elements/TrackSingle.vue'
import NowLoading from '../elements/NowLoading.vue'

export default {
    name: 'TracksList',
    components: {
        TrackSingle,
        NowLoading
    },
    props: {
        artistSelected: String,
        genreSelected: String
    },
    data() {
        return {
            tracksList: [],
            isNowLoading: true
        }
    },
    methods: {
        getTracksLIst() {
            let that = this;

            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(function(response) {
                //console.log(response);

                that.tracksList = response.data.response;
                that.isNowLoading = false;

                //console.log(that.tracksList)
                that.$emit('linkedTracksList', that.tracksList)
            })
            .catch(error => {
                console.log(error);
                that.isNowLoading = false;
            });
        }
    },
    mounted() {
        this.getTracksLIst();
    },
    computed: {
        getFilteredTracksList() {
            if (this.genreSelected == 'Seleziona genere' && this.artistSelected == 'Seleziona artista') {
                return this.tracksList
            } else if (this.genreSelected !== 'Seleziona genere' && this.artistSelected !== 'Seleziona artista') {
                const filteredGenArtList = this.tracksList.filter((track => {
                    if (track.genre.includes(this.genreSelected) && track.author.includes(this.artistSelected)) {
                        return true
                    } else {
                        return false
                    }
                }));
                return filteredGenArtList
            } else if (this.genreSelected !== 'Seleziona genere') {
                const filteredGenresList = this.tracksList.filter((track => {
                    if (track.genre.includes(this.genreSelected) && this.artistSelected == 'Seleziona artista') {
                        return true
                    } else {
                        return false
                    }
                }));
                return filteredGenresList
            } else if (this.artistSelected !== 'Seleziona artista') {
                const filteredArtistsList = this.tracksList.filter((track => {
                    if (track.author.includes(this.artistSelected) && this.genreSelected == 'Seleziona genere') {
                        return true
                    } else {
                        return false
                    }
                }));
                return filteredArtistsList
            } else {
                return this.tracksList
            }
        }
    }
}
</script>

<style scoped lang="scss">
    section {
        height: calc(100vh - 80px);
        background-color: #1e2d3b;
    }

    .track-card {
        height: 100%;
        background-color: #2e3a46;
    }
</style>