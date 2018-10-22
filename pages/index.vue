<template>
  <section class="container">
    <navigation :isHomepage="isHomepage"/>
    <home/>
    <foot/>
  </section>
</template>

<script>
import Navigation from '~/components/Navigation.vue'
import Foot from '~/components/Foot.vue'
import Home from '~/components/Home.vue'
import ContactWidget from '~/components/ContactWidget.vue'

export default {
  name: 'Index',
  components: {
    Navigation,
    Foot,
    Home,
    ContactWidget
  },
  data() {
    return {
      isHomepage: false
    }
  }
}
</script>

<style>
.container {
  background: url('~/assets/images/default.jpg') center center;
  background-size: cover;
  text-align: center;
  width: 100vw;
  height: 100vh;
}
</style>
