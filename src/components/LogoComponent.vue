<template>
    <div>
        <img src="../assets/logo-white.png">
    </div>
</template>

<script>
export default {
    name: 'LogoComponent',
    props: {
        img: String
    }
}
</script>

<style scoped>
    img {
        max-width: 100%;
        max-height: 100%;
        display: block;
        margin: auto;
    }
</style>