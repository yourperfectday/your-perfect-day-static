<template>
  <section class="container aileen">
    <logo/>
    <navigation/>
    <div class="aileen">
      <h1>About Aileen</h1>
      <p>
        An IIOC (Irish Institute of Celebrants) qualified celebrant, I am an experienced public speaker and
        writer. I would describe myself as warm and professional (with a healthy dose of Irish humour!).
        I will work with you to create and deliver your perfect ceremony. My goal is to provide you with a
        ceremony that reflects your love, values and your two individual personalities. Or, in the case of
        baby naming ceremonies, the personality of your new little person! And I will deliver that ceremony
        with solemnity, joy and a touch of humour.
      </p>
      <p>
        I look forward to giving you your perfect day.
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
