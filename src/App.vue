<script setup>
import { ref } from 'vue';
import NavBar from './components/NavBar.vue'
import FooterSection from './components/FooterSection.vue'


</script>

<template>
  <!-- N A V <><><><><> BAR -->
  <nav-bar />

  <!-- C_UR_R_ENT <?<>?<?><?> PA_GE -->
  <router-view />


  <!-- FOOTER SECTION -->
  <footer-section />
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


</style>
