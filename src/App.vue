<script setup>
import { onMounted, ref } from 'vue';
import axios from 'axios'
import NavBar from './components/NavBar.vue'
import MovieSection from './components/MovieSection.vue'
import SingleMoviePage from './components/SingleMoviePage.vue';
import FooterSection from './components/FooterSection.vue'

const trending = ref([])
const moviesData = ref([])
const tvShowsData = ref([])

// A P I's
onMounted(async () => {
  const res = await axios.get('https://api.themoviedb.org/3/movie/popular?api_key=73c8539c563f213bb796cf581b7044ed&language=en-US&page=1')
  .then(response => {
    moviesData.value = response.data.results
  })
  .catch(err => console.log(err))
})

axios.get('https://api.themoviedb.org/3/trending/all/day?api_key=73c8539c563f213bb796cf581b7044ed&language=en-US&page=1')
  .then((response) => {
    console.log(response)
    trending.value = response.data.results
  })
  .catch((err) => console.log(err))


axios.get('https://api.themoviedb.org/3/tv/popular?api_key=73c8539c563f213bb796cf581b7044ed&language=en-US&page=1')
  .then((response) => tvShowsData.value = response.data.results)
  .catch((err) => console.log(err))

  // https:/h/api.themoviedb.org/3/genre/movie/list?api_key=73c8539c563f213bb796cf581b7044ed&language=en-US'
</script>

<template>

  <div class="navbar">
    <nav-bar />
  </div>

  <!-- MOVIES SECTIONS -->
  <movie-section name="Trending" :data="trending" />
  <movie-section name="Popular Movies" :data="moviesData" />
  <movie-section name="Popular Tv Shows" :data="tvShowsData" />

  <single-movie-page />

  <!-- FOOTER SECTION -->
  <!-- <footer-section /> -->
</template>

<style lang="scss">
// COLORS
$bg-color: #181818;

body{
  background: $bg-color;
  scroll-behavior: smooth;
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Open Sans';
}

.navbar{
  top: 0;
}

</style>
