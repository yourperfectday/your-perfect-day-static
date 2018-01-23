<template>
  <div class="your-perfect-day">
    <ul id="services" class="services">
      <service
        v-for="(service, index) in services"
        :key="index"
        :name="service.name"
        :path="service.path"
        :image="service.image"
        :index="index">
      </service>
    </ul>
  </div>
</template>

<script>
  import Service from '~/components/Service.vue'

  export default {
    name: 'Home',
    components: {
      Service
    },
    data () {
      return {
        services: [
          { name: 'Weddings', path: '/weddings', image: 'assets/wedding.jpg' },
          { name: 'Namings', path: '/baby-namings', image: 'assets/baby.jpg' },
          { name: 'Renewals', path: '/vow-renewals', image: 'assets/vows.jpg' }
        ]
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .your-perfect-day {
    align-items: center;
    display: flex;
    flex-flow: column;
    justify-content: center;
    height: 100%;

    &:after {
      content: '';
      position: absolute;
      height: 100%;
      width: 100%;
      background: rgba(255, 255, 255, 0.2);
      z-index: 5;
      left: 0;
      top: 0;
    }

    .services {
      display: flex;
      flex-flow: row;
      flex-wrap: wrap;
      justify-content: center;
      padding: 0;
      margin: 0;
    }
  }
</style>
