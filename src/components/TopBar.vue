<template>
    <nav>
        <div class="container d-flex justify-content-between align-items-center">
            <img src="@/assets/img/logo-small.svg" alt="Spotify">
            <select class="form-select">
                <option selected>Open this select menu</option>
                <option v-for="(genre, genreIndex) in getTracksGenre" :key="genreIndex" value="1">{{genre}}</option>

            </select>
        </div>

        <div>{{getTracksGenre}}</div>
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
            tracksGenre: []
        }
    },
    computed: {
        getTracksGenre() {
            if (!this.linkedTracksList.length == 0) {
                for (let i; i < this.linkedTracksList.length; i++) {
                    if (!this.tracksGenre.includes(this.linkedTracksList[i].genre)) {
                        this.tracksGenre.push(this.linkedTracksList[i].genre);
                        console.log(this.tracksGenre)
                        return this.tracksGerne
                    } else {
                        return false
                    }
                }
                console.log(this.linkedTracksList)
                console.log(this.linkedTracksList[0].genre)
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