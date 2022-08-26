<template>
    <div>
        <div class="img-wrapper">
            <img :src="track.poster" :alt="`${track.author} - ${track.title}`">
        </div>

        <div>{{track.title}}</div>
        <div>{{track.author}}</div>
        <div>{{track.year}}</div>
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
        overflow: hidden;
    }

    img {
        object-fit: contain;
    }
</style>