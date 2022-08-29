<template>
    <nav>
        <div class="container d-flex justify-content-between align-items-center">
            <img src="@/assets/img/logo-small.svg" alt="Spotify">
            <div class="d-flex justify-content-end align-items-center">
                <select @change="$emit('artistSelected', valueArtist)" v-model="valueArtist" class="form-select me-5">
                    <option selected>Seleziona artista</option>
                    <option v-for="(artist, artistIndex) in getTracksArtist()" :key="artistIndex" :value="artist">{{artist}}</option>
                </select>
                <select @change="$emit('genreSelected', valueGenre)" v-model="valueGenre" class="form-select">
                    <option selected>Seleziona genere</option>
                    <option v-for="(genre, genreIndex) in getTracksGenre()" :key="genreIndex" :value="genre">{{genre}}</option>
                </select>
            </div>
        </div>

    </nav>
</template>

<script>
export default {
    name: 'TopBar',
    props: {
        linkedTracksList: Array
    },
    data() {
        return {
            tracksArtist: [],
            tracksGenre: [],
            valueArtist: 'Seleziona artista',
            valueGenre: 'Seleziona genere'
        }
    },
    methods: {
        getTracksGenre() {
            if (this.linkedTracksList.length !== 0) {
                for (let i = 0; i < this.linkedTracksList.length; i++) {
                    if (!this.tracksGenre.includes(this.linkedTracksList[i].genre)) {
                        this.tracksGenre.push(this.linkedTracksList[i].genre);
                    }
                }
                return this.tracksGenre
            } else {
                return false
            }
        },
        getTracksArtist() {
            if (this.linkedTracksList.length !== 0) {
                for (let i = 0; i < this.linkedTracksList.length; i++) {
                    if (!this.tracksArtist.includes(this.linkedTracksList[i].author)) {
                        this.tracksArtist.push(this.linkedTracksList[i].author);
                    }
                }
                return this.tracksArtist
            } else {
                return false
            }
        }
    }
}
</script>

<style scoped lang="scss">
    nav {
        height: 80px;
        background-color: #2e3a46;
        .container {
            height: 100%;
        }
        select {
            width: 200px;
        }
    }

    img {
        height: 60px;
    }
</style>