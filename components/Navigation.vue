<template>
  <div class="navigation">
    <social/>
    <links/>
  </div>
</template>

<script>
import Social from './Social.vue';
import Links from './Links.vue';

export default {
  name: 'Navigation',
  components: {
    Social,
    Links
  }
}
</script>

<style scoped lang="scss">
  .navigation {
    align-items: center;
    display: flex;
    flex-flow: row-reverse;
    height: 70px;
    top: 0;
    position: fixed;
    width: 100%;
    z-index: 20;
  }
</style>

