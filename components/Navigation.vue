<template>
  <div class="navigation">
    <logo v-if="!isHomepage"/>
    <social/>
    <links/>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Social from './Social.vue';
import Links from './Links.vue';

export default {
  name: 'Navigation',
  props: {
    isHomepage: {
      type: Boolean,
      default: false
    }
  },
  components: {
    Social,
    Links,
    Logo
  }
}
</script>

<style scoped lang="scss">
  .navigation {
    background-color: rgba(255,255,255,1);
    align-items: center;
    display: flex;
    flex-flow: row-reverse;
    height: 70px;
    left: 0;
    top: 0;
    position: fixed;
    width: 100%;
    z-index: 20;


  }
</style>

