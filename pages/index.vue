<template>
  <section class="container">
    <navigation isHomepage="false"/>
    <home/>
  </section>
</template>

<script>
import Navigation from '~/components/Navigation.vue'
import Home from '~/components/Home.vue'
import ContactWidget from '~/components/ContactWidget.vue'

export default {
  components: {
    Navigation,
    Home,
    ContactWidget
  }
}
</script>

<style>
.container {
  -webkit-background-size: cover;
  background-size: cover;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  width: 100vw;
  height: 100vh;
}
</style>
