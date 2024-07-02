<template>
  <div class="page">
    <page-title>About</page-title>
    <p>This app was built with Vue.js</p>
    <img 
      class="animate__animated"
      :class="{'animate__jackInTheBox': isLogoAnimated}" 
      src="@/assets/image.png"
      @click="animateLogo"
      @animationend="isLogoAnimated = false">
  </div>
</template>
  
<script>
import PageTitle from '../components/shared/PageTitle';
export default {
  name: 'AboutPage',
  data: () => ({
    isLogoAnimated: true
  }),
  methods: {
    animateLogo () {
      this.isLogoAnimated = false;
      this.$nextTick(() => {
        this.isLogoAnimated = true;
      });
    }
  },
  components: { PageTitle }
}
</script>