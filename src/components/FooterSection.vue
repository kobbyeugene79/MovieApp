<script setup>
import { ref } from "@vue/reactivity";

const types = ref([
    'Movies',
    'Tv Shows',
    'Trending',
    'Top Rated'
])

</script>

<template>
    <footer>
        <ul class="footer__types">
            <li v-for="type, index in types" :key="index">{{ type }}</li>
        </ul>
    </footer>
</template>

<style lang="scss" scoped>

</style>