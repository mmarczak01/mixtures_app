<template>
  <div id="app">
    <div class="container">

      <!-- header -->
      <app-header />

      <!-- header -->   
      <app-menu />   
      
      <!-- router view -->
      <slide-fade-animation class="animate__fast">
        <router-view />
      </slide-fade-animation>

    </div>
  </div>
</template>

<script>
import './styles/global.scss'
import 'animate.css/animate.min.css'
import AppHeader from './components/AppHeader'
import AppMenu from './components/AppMenu'
import { RouterView } from 'vue-router';
import SlideFadeAnimation from './components/shared/SlideFadeAnimation';

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMenu,
    RouterView,
    SlideFadeAnimation
  }
}
</script>

<style lang="scss">
.container {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
  padding: 2rem;
}
</style>
