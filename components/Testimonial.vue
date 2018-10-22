<template>
  <div class="testimonial">
    <div class="quote">{{quote}}</div>
    <div class="names" v-if="name">{{name}}</div>
  </div>
</template>

<script>
  export default {
    name: 'Testimonial',
    props: {
      quote: {
        type: String,
        required: true
      },
      name: {
        type: String
      }
    }
  }
</script>

<style lang="scss" scoped>
  .testimonial {
    .quote,
    .names {
      font-size: 15px;
      font-family: Segan;
      margin: 10px auto;
      max-width: 750px;
    }

    .quote {
      font-style: italic;
      line-height: 1.5;

      &:before {
        content: '“';
      }

      &:after {
        content: '”'
      }
    }

    .names {
      &:before {
        content: "- ";
      }
    }
  }
</style>
