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
  text-align: center;
  width: 100vw;
  height: 100vh;
}
</style>
