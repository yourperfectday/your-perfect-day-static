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
    background-color: transparent;
    border-radius: 5px;
    cursor: pointer;
    font-size: 14px;
    padding: 5px;
    width: 150px;
  }
</style>
