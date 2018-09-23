<template>
  <section class="content-container" :class="[pageName]">
    <logo/>
    <navigation/>
    <div class="content-page">
      <h1 class="content-header">{{heading}}</h1>
      <div class="content-image">
        <img :src="imageSource"/>
      </div>
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
    background-color: rgba(255, 255, 255, 0.9);
    position: fixed;
    top: 50px;
    bottom: 50px;
    width: calc(100% - 100px);
    left: 50px;
    display: flex;
    font-family: Segan;
    align-items: center;
    flex-wrap: wrap;

    .content-header {
      align-self: flex-start;
      width: 100%;
      text-align: center;
    }

    .content-image,
    .content-text {
      box-sizing: border-box;
      width: 50%;
      min-height: calc(100% - 100px);
    }

    .content-image {
      padding: 10px;
      img {
        max-width: 100%;
      }
    }

    .content-text {
      font-size: 18px;
      line-height: 24px;
      padding: 10px;
    }
  }
</style>
