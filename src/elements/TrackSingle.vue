<template>
    <div class="text-center">
        <div class="img-wrapper">
            <img :src="track.poster" :alt="`${track.author} - ${track.title}`">
        </div>

        <div class="text-white text-uppercase fw-bold mt-1">{{track.title}}</div>
        <div class="text-white-50 mt-2">{{track.author}}</div>
        <div class="text-white-50">{{track.year}}</div>
    </div>
</template>

<script>
export default {
    name: 'TrackSingle',
    props: {
        track: Object
    }
}
</script>

<style scoped lang="scss">
    .img-wrapper {
        width: 100%;
        aspect-ratio: 1 / 1;
        max-height: 150px;
        overflow: hidden;
    }

    img {
        height: 100%;
        object-fit: contain;
    }
</style>