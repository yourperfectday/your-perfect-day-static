<template>
  <div class="links-container" :class="{ active: isNavActive }" @click="toggleNav">
    <div class="hamburger-container" >
      <div class="hamburger"/>
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
    height: 20px;

    @media (max-width: 767px) {
      order: -1;
    }

    .hamburger-container {
      cursor: pointer;
      position: relative;
      width: 20px;
      height: 100%;
      display: none;
      z-index: 50;
      margin: 0 10px;

      @media (max-width: 767px) {
        display: inline-block;
      }

      .hamburger {
        top: 50%;
        display: block;
        margin-top: -2px;

        &,
        &:before,
        &:after {
          left: 0;
          position: absolute;
          width: 20px;
          height: 3px;
          transition-timing-function: ease;
          transition-duration: .15s;
          transition-property: transform;
          border-radius: 4px;
          background-color: $primary;
        }

        &:before,
        &:after {
          content: '';
          display: block;
        }

        &:before {
          top: -8px;
        }

        &:after {
          bottom: -8px;
        }
      }

      &.active {

      }
    }

    .links {
      list-style: none;
      margin: 0;

      .link-item {
        a {
          color: $primary;
          font-family: Segan;
          font-weight: bold;
          font-size: 30px;
          text-decoration: none;
          transition: color 0.1s linear;

          @media (min-width: 768px) {
            font-size: 14px;
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

    &:hover {
      .hamburger-container {
        .hamburger {
          &,
          &:before,
          &:after {
            background-color: $secondary;
          }
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

      .hamburger {
        transform: rotate(765deg);

        &:before {
          top: 0;
          opacity: 0;
        }

        &:after {
          bottom: 0;
          transform: rotate(90deg);
        }
      }
    }
  }
</style>
