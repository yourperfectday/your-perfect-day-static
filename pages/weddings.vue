<template>
  <section class="container weddings">
    <logo/>
    <navigation/>
    <div class="weddings">
      <h1>Weddings</h1>
      <p>
        Your love is like no other so your ceremony shouldn’t be like any other.
      </p>
      <p>
        Your wedding ceremony should fit you as a couple, celebrate your love and bring your lives together
        formally in a personal and meaningful way. Aileen will work with you to craft your perfect wedding
        ceremony. Whether you are looking for a non-religious or multi-faith ceremony, it will be carried out
        to the highest standards with warm professionalism.
      </p>
      <p>
        Our wedding ceremonies normally include your story as a couple, blessings (such as hand-fasting or
        candle lighting), readings and your pronouncement but can easily be changed to suit each couple.
        Aileen will work with you both to create your perfect ceremony that fulfils your wishes.
      </p>
    </div>
  </section>
</template>

<script>
  import Logo from '~/components/Logo.vue'
  import Navigation from '~/components/Navigation.vue'

  export default {
    name: 'Aileen',
    components: {
      Logo,
      Navigation
    }
  }
</script>

<style>

</style>
