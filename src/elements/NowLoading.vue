<template>
    <div class="loader d-flex justify-content-center align-items-center text-white text-uppercase fw-bold fs-4">
        Caricamento
    </div>
</template>

<script>
export default {
    name: 'NowLoading'
}
</script>

<style lang="scss">
    .loader {
        position: fixed;
        top: 0;
        left: 0;
        background-color: #1e2d3b;
        height: 100vh;
        width: 100%;
    }
</style>