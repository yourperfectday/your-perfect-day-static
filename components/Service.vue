<template>
  <li class="service-container">
    <div class="service" :class="{ active: isActive }" @mouseover="enter" @mouseout="exit">
      <div class="service-image" :class="['image-' + index]"></div>
      <a :href="path">{{ name }}</a>
    </div>
  </li>
</template>

<script>
export default {
  name: 'Service',
  props: [
    'path',
    'name',
    'image',
    'index'
  ],
  data () {
    return {
      isActive: false
    }
  },
  methods: {
    enter: function (event) {
      this.isActive = true
    },
    exit: function (event) {
      this.isActive = false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @import "../assets/style/constants";

  .service-container {
    display: inline-block;

    @media (max-width: 1024px) {
      width: 100%;
    }

    .service {
      display: flex;
      margin: 0;
      padding: 0;
      text-decoration: none;
      text-transform: uppercase;
      font-size: 40px;
      font-family: Segan;
      letter-spacing: 5px;
      text-align: center;

      @media (max-width: 480px) {
        font-size: 32px;
      }

      a {
        color: $primary;
        font-weight: bolder;
        padding: 10px 20px;
        position: relative;
        text-decoration: none;
        z-index: 10;
        width: 100%;
        letter-spacing: 10px;
      }

      .service-image {
        background: transparent no-repeat center;
        background-size: cover;
        transition: opacity 0.2s linear;
        height: 100vh;
        left: 0;
        opacity: 0;
        pointer-events: none;
        position: fixed;
        top: 0;
        width: 100vw;
        z-index: 0;
        margin: 0;
        padding: 0;

        &.image-0 {
          background-image: url('~/assets/images/wedding.jpg');

          @media screen and (orientation:portrait) {
            background-image: url('~/assets/images/mobile/wedding.jpg');
          }
        }

        &.image-1 {
          background-image: url('~/assets/images/baby.jpg');

          @media screen and (orientation:portrait) {
            background-image: url('~/assets/images/mobile/baby.jpg');
          }
        }

        &.image-2 {
          background-image: url('~/assets/images/vows.jpg');

          @media screen and (orientation:portrait) {
            background-image: url('~/assets/images/mobile/vows.jpg');
          }
        }
      }

      &.active {
        .service-image {
          display: block;
          opacity: 1;
          background-size: cover;

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
        }

        a:after {
          background-color: $primary;
          content: '';
          display: block;
          position: absolute;
          height: 2px;
          width: 100px;
          bottom: 10px;
          left: calc(50% - 50px);
        }
      }
    }
  }
</style>
