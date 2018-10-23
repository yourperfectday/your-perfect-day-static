<template>
  <section class="content-container" :class="[pageName]">
    <navigation/>
    <div class="content-page">
      <h1 class="content-header">{{heading}}</h1>
      <img class="content-image -landscape" :src="imageSource"/>
      <div class="content-text">
        <slot></slot>
      </div>
    </div>
  </section>
</template>

<script>
  import Logo from './Logo.vue'
  import Navigation from './Navigation.vue'

  export default {
    name: 'Content',
    components: {
      Logo,
      Navigation
    },
    computed: {
      imageSource() {
        return `/${this.pageName}.jpg`
      }
    },
    props: {
      heading: {
        type: String,
        required: true
      },
      pageName: {
        type: String,
        default: 'content'
      }
    }
  }
</script>

<style lang="scss" scoped>
  .content-page {
    background-color: white;
    width: 100%;
    max-width: 1024px;
    margin: 70px auto 0;
    padding: 30px;
    box-sizing: border-box;

    @media (max-width: 480px) {
      padding: 20px;
    }

    .content-header {
      text-transform: uppercase;
      font-family: Segan;
      font-size: 30px;
      letter-spacing: 5px;
      text-align: center;
      margin-bottom: 30px;

      @media (max-width: 480px) {
        font-size: 22px;
        letter-spacing: 2px;
        margin-bottom: 15px;
      }

      @media (min-width: 768px) {
        margin-left: 330px;
      }
    }

    .content-image {
      float: left;
      margin-right: 30px;
      margin-bottom: 30px;
      width: 300px;
      max-width: 50%;

      @media (max-width: 480px) {
        margin-right: 15px;
        margin-bottom: 15px;
      }

      &.-portrait {
        display: none;
        width: 100%;
      }
    }

    .content-text {
      font-family: Segan;
      line-height: 1.7;
      font-size: 16px;

      @media (max-width: 480px) {
        font-size: 14px;
      }
    }

    @media (orientation: portrait) {
      .content-image {
        &.-portrait {
          /*display: block;*/
        }

        &.-landscape {
          /*display: none;*/
        }
      }
    }

    /*.content-header {*/
      /*align-self: flex-start;*/
      /*width: 100%;*/
      /*text-align: center;*/
      /*font-size: 32px;*/
    /*}*/

    /*.content-image,*/
    /*.content-text {*/
      /*box-sizing: border-box;*/
      /*min-height: calc(100% - 100px);*/
    /*}*/

    /*.content-image {*/
      /*padding: 10px;*/
      /*width: 30%;*/

      /*img {*/
        /*max-width: 100%;*/
      /*}*/
    /*}*/

    /*.content-text {*/
      /*font-size: 16px;*/
      /*line-height: 1.5;*/
      /*padding: 10px;*/
      /*width: 70%;*/
    /*}*/
  }
</style>
