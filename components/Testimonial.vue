<template>
  <div class="testimonial">
    <div class="quote">{{quote}}</div>
    <div class="names">{{name}}</div>
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
        type: String,
        required: true
      }
    }
  }
</script>

<style lang="scss" scoped>
  .testimonial {
    .quote,
    .names {
      font-size: 12px;
      font-family: Segan;
      margin: 5px 50px;
    }

    .quote {
      font-style: italic;
      line-height: 1.3;

      &:after,
      &:before {
        content: '"';
      }
    }

    .names {
      &:before {
        content: "- ";
      }
    }
  }
</style>
