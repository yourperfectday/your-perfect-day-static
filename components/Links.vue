<template>
  <div class="links-container" :class="{ active: isNavActive }">
    <div class="links-hamburger" @click="toggleNav">
      <span class="top"></span>
      <span class="mid"></span>
      <span class="bottom"></span>
    </div>
    <ul class="links">
      <li v-for="(link, index) in links" :key="index" class="link-item">
        <a :href="link.link">{{ link.name }}</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Links',
  data () {
    return {
      isNavActive: false,
      links: [
        { name: 'About Aileen', link: '/aileen' },
        { name: 'About The IIOC', link: 'https://www.iioc.ie/' },
        { name: 'Contact', link: '/contact' }
      ]
    }
  },
  methods: {
    toggleNav: function () {
      this.isNavActive = !this.isNavActive
    }
  }
}
</script>

<style scoped lang="scss">
  @import "../assets/style/constants";

  .links-container {
    @media (max-width: 767px) {
      order: -1;
    }

    .links-hamburger {
      cursor: pointer;
      display: none;
      margin: 0 10px;
      width: 30px;
      height: 30px;
      position: relative;
      z-index: 50;

      &:hover {
        span {
          background: $secondary;
        }
      }

      span {
        display: block;
        position: absolute;
        height: 4.5px;
        width: 100%;
        background: $primary;
        border-radius: 4.5px;
        opacity: 1;
        left: 0;
        transform: rotate(0deg);
        transition: .25s ease-in-out;
      }

      .top {
        top: 0px;
        transform-origin: left center;
      }

      .mid {
        top: 9px;
        transform-origin: left center;
      }

      .bottom {
        top: 19px;
        transform-origin: left center;
      }

      @media (max-width: 767px) {
        display: block;
      }
    }

    .links {
      list-style: none;

      .link-item {
        a {
          color: $primary;
          font-family: Segan;
          font-weight: bold;
          font-size: 30px;
          text-decoration: none;
          transition: color 0.1s linear;

          @media (min-width: 768px) {
            font-size: 16px;
            line-height: 24px;
          }

          &:hover {
            color: $secondary;
          }
        }
      }

      @media (min-width: 768px) {
        .link-item {
          display: inline-block;
          padding: 0 10px;
        }
      }

      @media (max-width: 767px) {
        display: flex;
        visibility: hidden;
        opacity: 0;
        flex-flow: column;
        justify-content: center;
        align-items: center;
        position: fixed;
        width: 100%;
        height: 100%;
        top: 0;
        left: 0;
        padding: 0;
        margin: 0;
        background-color: rgba(255, 255, 255, 0.9);
        transition: all 0.1s ease-in;

        .link-item {
          display: inline-block;
          font-size: 24px;
          margin: 10px auto;
          line-height: 40px;
        }
      }
    }

    &.active {
      .links {
        @media (max-width: 767px) {
          visibility: visible;
          opacity: 1;
        }
      }

      .links-hamburger {
        .top {
          transform: rotate(45deg);
          top: -1.5px;
          left: 4px;
        }

        .mid {
          width: 0;
          opacity: 0;
        }

        .bottom {
          transform: rotate(-45deg);
          top: 19.5px;
          left: 4px;
        }
      }
    }
  }
</style>
