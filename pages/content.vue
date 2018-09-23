<template>
  <div class="content-page">
    <h1 class="content-header">Baby Naming Ceremonies</h1>
    <div class="content-image">
      <img src="~/assets/images/mobile/baby.jpg"/>
    </div>
    <div class="content-text">
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
  export default {
    name: 'content',
    props: {
      associatedImage: {
        type: Object,
        required: true
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
