<template>
    <nav>
        <div class="container d-flex justify-content-between align-items-center">
            <img src="@/assets/img/logo-small.svg" alt="Spotify">
            <select @change="$emit('genreSelected', valueGenre)" v-model="valueGenre" class="form-select">
                <option selected>Seleziona genere</option>
                <option v-for="(genre, genreIndex) in getTracksGenre()" :key="genreIndex" :value="genre">{{genre}}</option>
            </select>
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
            tracksGenre: [],
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