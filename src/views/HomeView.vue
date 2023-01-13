<script setup>
import { onMounted, ref } from 'vue';
import axios from 'axios'

const trendingData = ref([])
const moviesData = ref([])
const tvShowsData = ref([])
const genresData = ref([])

// A P I's
/* POPULAR <<<</>>>> MOVIES */
onMounted(async () => {
  const res = await axios.get('https://api.themoviedb.org/3/movie/popular?api_key=73c8539c563f213bb796cf581b7044ed&language=en-US&page=1')
  .then(response => {
    moviesData.value = response.data.results
  })
  .catch(err => console.log(err))
})

/* TRENDING <<<</>>>> ALL */
axios.get('https://api.themoviedb.org/3/trending/all/day?api_key=73c8539c563f213bb796cf581b7044ed&language=en-US&page=1')
  .then((response) => {
    console.log(response)
    trendingData.value = response.data.results
  })
  .catch((err) => console.log(err))

/* POPULAR <<<</>>>> TV_SHOWS */
axios.get('https://api.themoviedb.org/3/tv/popular?api_key=73c8539c563f213bb796cf581b7044ed&language=en-US&page=1')
  .then((response) => tvShowsData.value = response.data.results)
  .catch((err) => console.log(err))

/* GET <<<</>>>> GENRES */
axios.get('https://api.themoviedb.org/3/genre/movie/list?api_key=73c8539c563f213bb796cf581b7044ed&language=en-US')
  .then((response) => genresData.value = response.data.genres)
  .catch((err) => console.log(err))



</script>

<template>
    
  <!-- MOVIES SECTIONS -->
  <movie-section name="Trending" :genres="genresData" :data="trendingData" />
  <movie-section name="Popular Movies" :genres="genresData" :data="moviesData" />
  <movie-section name="Popular Tv Shows" :genres="genresData" :data="tvShowsData" />


</template>

<style lang="scss" scoped>

</style>