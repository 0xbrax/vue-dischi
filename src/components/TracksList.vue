<template>
    <section class="d-flex d-flex justify-content-center align-items-center">
        <div class="container">
            <div class="row">

                    <div class="col-2" v-for="(track, trackIndex) in tracksList" :key="trackIndex">
                        <TrackSingle :track="track" />
                    </div>

            </div>
        </div>
    </section>
</template>

<script>
import axios from 'axios'
import TrackSingle from '../elements/TrackSingle.vue'

export default {
    name: 'TracksList',
    components: {
        TrackSingle
    },
    data() {
        return {
            tracksList: []
        }
    },
    methods: {
        getTracksLIst() {
            let that = this;

            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(function(response) {
                console.log(response);

                that.tracksList = response.data.response;
            })
        }
    },
    mounted() {
        this.getTracksLIst();
    }
}
</script>

<style scoped lang="scss">
    section {
        height: calc(100vh - 80px);
    }
</style>