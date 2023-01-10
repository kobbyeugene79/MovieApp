<script setup>
import { ref } from 'vue'
import searchIcon from '../assets/Icons/search_black_24dp.svg'

const navList = ref([
  {id: 1, title: 'Home', activeLink: false},
  {id: 2, title: 'Movies', activeLink: true},
  {id: 3, title: 'TV Shows', activeLink: false},
  {id: 4, title: 'About Me', activeLink: false},
])

const toggleActiveLink = (link) => {
  link.activeLink = !link.activeLink
}

</script>

<template>
  <div class="navBar">

    <div class="navBar__logo">
      <h2 class="navBar__logo--name">KayBee Movies</h2>
    </div>

    <!-- <ul class="navBar__menu">
      <li 
        v-for="link in navList" 
        @click="toggleActiveLink(link)"
        class="navBar__menu--list"
        :key="link.id" 
        >
        {{link.title}}
      </li>
    </ul> -->

    <div class="navBar__search">
      <input class="navBar__search--input" type="text" name="search" id="search" placeholder="Search Here...">
      <div class="navBar__search--div"><img :src="searchIcon" alt="search icon" class="navBar__search--icon"></div>
    </div>

  </div>
</template>

<style lang="scss" scoped>
$nav-bg-color: #000;
$white-color: #ffffff;
$blue-color: #007acc;
$crimson-color: #751e2f;

.navBar{
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 1.15rem 3rem;
  z-index: 1;
  background: $nav-bg-color;
  cursor: pointer;

  &__logo{
    
    &--name{
      color: $white-color;
      font-weight: 600;

      // background-image: linear-gradient(45deg, #09009f, #00ff95 80%);
      // -webkit-background-clip: text;
      // -webkit-text-fill-color: transparent;
    }
  }

  &__menu{
    list-style-type: none;
    display: flex;
    justify-content: space-between;

    &--list{
      color: $white-color;
      padding: 0 0.77rem;
      transition: .3s ease-out;
    }
  }

  &__search{
    position: relative;
    width: 15rem;
    background: $white-color;
    border-radius: 2rem;
    align-items: center;
    justify-content: space-between;
    box-shadow: 2px 2px 4px rgba($color: #252526, $alpha: 0.3);

    &--input{
    align-items: center;
    margin-left: 00.5rem;
    width: 85%;
    height: 1.9rem;
    padding-left: 0.5rem;
    padding-right: 0.5rem;
    border-radius: 2rem;
    border: none;
    font-weight: 500;
    background: transparent;
    outline: none;
    
      &::placeholder{
        margin-left: 1rem;
        transition: .2s;
      }
    }

    &:focus &--input::placeholder{
      transform: translateX(5px);
    }

    &--div{
      display: inline;
    }

    &--icon{
      position: absolute;
      top: 3px;
      right: 0;
      margin-right: 0.7rem;
      cursor: pointer;
    }
  }
}


.active{
  top: -0.5rem;
  position: relative;
  color: $crimson-color;
  font-weight: 700;

  &::after{
    position: absolute;
    content: '';
    width: 0.5rem;
    height: 0.5rem;
    border-radius: 50%;
    background: $crimson-color;
    bottom: -1rem;
    left: 50%;
  }
}
</style>
