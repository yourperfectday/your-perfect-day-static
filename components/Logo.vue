<template>
  <!--<div class="logos">-->
    <!--<a class="logo" href="/" />-->
  <div class="logo-container">
    <a class="logo" href="/"/>
  </div>
  <!--</div>-->
</template>

<script>
export default {
  name: 'Logo'
}
</script>

<style scoped>
  .logo-container {
    height: 70px;
    order: 3;
    flex-grow: 1;
  }

  .logo {
    background: url('~/assets/logo.png') 0 center;
    background-size: 100%;
    height: 100%;
    width: 140px;
    display: block;
    z-index: 200;
  }

  @media (max-width: 480px) {
    .logo {
      width: 105px;
    }

    .logo-container {
      height: 52.5px;
    }
  }

  /*<!--.logo {-->*/
  /*<!--!*display: block;*!-->*/

  /*<!--!*background-size: 100%;*!-->*/
  /*<!--!*height: 70px;*!-->*/
  /*<!--!*width: 140px;*!-->*/
  /*<!--!*margin: 0 10px;*!-->*/

  /*<!--@media (max-width: 480px) {-->*/
  /*<!--height: 52.5px;-->*/
  /*<!--!*top: 17.5px;*!-->*/
  /*<!--width: 105px;-->*/
  /*<!--}-->*/
  /*<!--}-->*/

</style>
