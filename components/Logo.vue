<template>
  <a class="logo" href="/" />
</template>

<script>
export default {
  name: 'Logo'
}
</script>

<style scoped>
  .logo {
    position: fixed;
    left: 0;
    top: 0;
    z-index: 20;
    background: url('~/assets/logo.png') 0 -36px;
    background-size: 100%;
    height: 70px;
    width: 140px;
    margin: 0 10px;
  }
</style>
