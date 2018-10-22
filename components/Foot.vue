<template>
  <div class="footer">
    <testimonials/>
  </div>
</template>

<script>
  import Testimonials from '~/components/Testimonials.vue'

  export default {
    name: 'Foot',
    components: {
      Testimonials
    }
  }
</script>

<style scoped lang="scss">
  .footer {
    background-color: rgba(255,255,255,0.9);
    height: 100px;
    left: 0;
    bottom: 0;
    position: fixed;
    width: 100%;
    z-index: 20;
    display: flex;
    align-items: center;
    justify-content: center;

    @media (max-width: 767px) {
      display: none;
    }
  }
</style>

