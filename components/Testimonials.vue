<template>
  <div class="testimonials-container">
    <transition name="slide" mode="out-in">
      <testimonial
        :key="activeIndex"
        :name="testimonials[activeIndex].name"
        :quote="testimonials[activeIndex].quote"/>
    </transition>
  </div>
</template>

<script>
  import Testimonial from '~/components/Testimonial.vue'

  export default {
    name: 'Testimonials',
    components: {
      Testimonial
    },
    data() {
      return {
        testimonials: [
          {
            quote: 'Everyone, from our guests to photographer, commented on how wonderful our ceremony was, and this was all down to the hard work and dedication Aileen put in'
          },
          {
            quote: 'Our ceremony was my favourite part of our wedding day and Aileen did an amazing job as our celebrant! From the very beginning she listened to what we wanted and understood the tone we hoped to strike.'
          },
          {
            quote: 'When we first met Aileen she understood exactly what we wanted as a couple and struck the perfect balance of romance and humour with our \'love story\'. She listened to our ideas and incorporated them all beautifully.'
          },
          {
            quote: 'Leading up to the wedding, I felt we were in good hands. Aileen was organised and professional and checked in with us regularly to ensure we were prepared and happy. On the day she was fantastic!'
          },
          {
            quote: 'The ceremony is the most important part to any wedding day and thankfully we were in the safe hands of Aileen who ensured our day ran seamlessly.'
          },
          {
            quote: 'Aileen did our daughter\'s naming ceremony. She worked with us in planning the event, perfectly incorporated everything we wanted and delivered a beautiful speech and service. Cannot recommend Your Perfect Day highly enough!'
          },
          {
            quote: 'On the day Aileen\'s calm, professional and vibrant persona eased any jitters and set the tone for the most perfect day. I would highly recommend Aileen to any couple getting married.'
          }
        ],
        activeIndex: 0,
        testimonialDisplayTime: 7000
      }
    },
    created() {
      this.activeIndex = Math.floor(Math.random() * this.testimonials.length)
    },
    mounted() {
      setInterval(() => {
        this.activeIndex = (this.activeIndex + 1) % this.testimonials.length
      }, this.testimonialDisplayTime)
    }
  }
</script>

<style lang="scss">
  .testimonials-container {
    width: 100%;
  }

  .slide-leave-active,
  .slide-enter-active {
    transition: all .25s;
  }

  .slide-leave-to /* .fade-leave-active below version 2.1.8 */ {
    transition-delay: 0.3s;
    transform: translateX(-100%);
    opacity: 0;
  }

  .slide-enter /* .fade-leave-active below version 2.1.8 */ {
    transform: translateX(100%);
    opacity: 0;
  }
</style>
