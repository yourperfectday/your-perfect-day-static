<template>
  <div class="information">
    <logo/>
    <navigation/>
    <div class="iioc">
      INFORMATION ABOUT IIOC GOES HERE
    </div>
  </div>
</template>

<script>
  import Logo from '~/components/Logo.vue'
  import Navigation from '~/components/Navigation.vue'

  export default {
    name: 'IIOC',
    components: {
      Logo,
      Navigation
    }
  }
</script>

<style>

</style>
