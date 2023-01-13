<script setup>
import MovieCard from './MovieCard.vue';

const props = defineProps({
    name: String,
    data: Array,
})

</script>


<template>

    <section class="moviesection">
        <h1 class="moviesection__title">
            {{ name }}
        </h1>

        <ul class="row">
            <movie-card :movie="movie" v-for="movie in data" :key="movie.id" />
        </ul>

    </section>
</template>



<style lang="scss" scoped>
.moviesection{
    width: 100%;
    padding: 5rem 0 2rem 2rem;

    &__title{
        background-image: linear-gradient(45deg, #f3ec78, #af4261);
        background-clip: text;
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
    }
    &__list{
        width: 100%;
        padding: 25px;
    }
}

.row{
    margin-top: 1rem;
    width: 100%;
    display: flex;
    flex-wrap: nowrap;
    overflow-x: scroll;
    overflow-y: hidden;

    &::-webkit-scrollbar{
        display: none;
    }
}
</style>