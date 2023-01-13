<script setup>
import { computed } from 'vue';

const props = defineProps({
    movie: Object,
    genres: Array
})

const posterPath = computed(() => {
    return "https://image.tmdb.org/t/p/w500" + props.movie.poster_path
})

const vote = computed(() => {
    return parseFloat(props.movie.vote_average).toFixed(1)
})

</script>

<template>
    <div class="movie">
        <div class="movie__poster">
            <img :src="posterPath" alt="not found" class="movie__poster--img">
        </div>

        <span class="movie__rating">{{ vote }}</span>

        <h2 class="movie__title">{{ movie.title }} {{ movie.name }}</h2>

        <span class="movie__genres" v-for="genra in movie.genre_ids" :key="genra.id">{{ genra }}</span>

    </div>
</template>

<style lang="scss" scoped>

.movie {
    display: inline-block;
    position: relative;
    border-radius: 20px;
    box-shadow: rgba(44, 44, 44, 0.021) 0px 4px 16px;
    cursor: pointer;

    &__title{
        padding: 1rem;
        font-size: 1.2em;
        position: absolute;
        color: #ffff;
        left: 0;
        bottom: 0;
        transform: translateY(-20px);
        opacity: 0;
        transition: .3s;
    }

    &:hover &__title{
        opacity: 1;
        transform: translateY(0);
    }

    &__rating{
        position: absolute;
        top: 0;
        right: 1rem;
        background: #FFD700;
        font-size: small;
        border-bottom-right-radius: 7px;
        border-bottom-left-radius: 7px;
        padding: 0.5rem 0.3rem 0.2rem;
        box-shadow: 0 2px 4px rgb(48, 48, 48);
    }

    //movie__poster--img
    &__poster{
        position: relative;
        height: 100%;
        width: 15rem;
        border-radius: 20px;
        padding-right: 1rem;

        &--img{
            width: 100%;
            height: 100%;
            border-radius: 10px;
        }

    }

    &:hover &__poster::before{
        position: absolute;
        content: '';
        bottom: 0;
        left: 0;
        border-radius: 10px;
        width: 100%;
        height: 50%;
        background: linear-gradient(transparent, rgba($color: #000000, $alpha: 0.9));
    }

    &__genres{
        // display: flex;
        // flex-wrap: wrap;
        position: absolute;
    }
}
</style>