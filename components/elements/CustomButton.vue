<template>
  <button class="button"
    :disabled="!isEnabled"
    @click.prevent="submit">{{message}}</button>
</template>

<script>
export default {
  name: 'CustomButton',
  props: [
    'isEnabled',
    'message'
  ],
  methods: {
    submit() {
      this.$emit('click')
    }
  }
}
</script>

<style lang="scss">
  .button {
    background-color: white;
    border-radius: 3px;
    font-size: 14px;
    padding: 5px;
    border-color: black;

    &:disabled {
      //TODO: something here!
    }
  }
</style>
