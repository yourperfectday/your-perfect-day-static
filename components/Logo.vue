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
    background: url('~/assets/logo.png') no-repeat center;
    background-size: contain;
    height: 100px;
    width: 100px;
    margin: 0 10px;
  }
</style>
