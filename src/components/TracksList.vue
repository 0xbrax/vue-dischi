<template>
    <div>
        <div v-for="(track, trackIndex) in tracksList" :key="trackIndex">
            <TrackSingle />
        </div>
    </div>
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

<style>

</style>