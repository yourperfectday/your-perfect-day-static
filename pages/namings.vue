<template>
  <div class="information">
    <logo/>
    <navigation/>
    <div class="namings">
      <h1>Baby Namings</h1>
      <p>
        Baby naming ceremonies are a wonderful way of officially welcoming your new arrival and
        celebrating this wonderful new addition to your family.
      </p>
      <p>
        Aileen will work with you to provide a non-religious ceremony to welcome your child and mark their
        new place in the world. A new life is the best reason for celebration and Aileen will create and
        deliver a personal ceremony to reflect this.
      </p>
      <p>
        A typical baby naming ceremony will include a blessing (such as a candle ceremony or a tree planting
        – there are many options), readings, parents’ blessing, guardians’ promises and official welcome to
        the baby. But Aileen can work with you to create the perfect fit for you and your new little one.
      </p>
    </div>
  </div>
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
