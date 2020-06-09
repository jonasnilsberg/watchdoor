<template>
    <div>
        <h1>{{ h1 }}</h1>
    </div>
</template>

<script>
export default {
    name: "HeaderComponent",
    props: {
        h1: String,
    }
}
</script>

<style scoped>

h1 {
    font-family: 'Montserrat', sans-serif;
    font-weight: bold;
    font-size: 32px;
    line-height: 39px;
    text-align: center;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: black;
    margin: 0 0 0.3em 0;
}

</style>