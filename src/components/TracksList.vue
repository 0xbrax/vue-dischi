<template>
    <section class="d-flex justify-content-between align-items-center">
        <div class="container">
            <div class="row g-5">
                    <div class="col-2" v-for="(track, trackIndex) in tracksList" :key="trackIndex">
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
                console.log(response);

                that.tracksList = response.data.response;
                that.isNowLoading = false;
            })
            .catch(error => {
                console.log(error);
                that.isNowLoading = false;
            });
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
        background-color: #1e2d3b;
    }

    .track-card {
        height: 100%;
        background-color: #2e3a46;
    }
</style>