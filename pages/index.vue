<template>
  <section class="container">
    <logo/>
    <navigation/>
    <home/>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Navigation from '~/components/Navigation.vue'
import Home from '~/components/Home.vue'

export default {
  components: {
    Logo,
    Navigation,
    Home
  }
}
</script>

<style>
.container {
  background: url('~/assets/default.jpeg') center no-repeat;
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
