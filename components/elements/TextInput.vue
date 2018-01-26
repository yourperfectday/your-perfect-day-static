<template>
  <div class="container">
  <input
    type="text"
    :disabled="disabled"
    v-model="propValue" />
  <div>{{validated}}</div>

  </div>
</template>

<script>
export default {
  name: 'TextInput',
  props: {
    disabled: {
      type: Boolean,
      default: false
    },
    value: {
      type: String,
      default: ''
    },
    maxLength: {
      type: Number,
      default: 100
    },
    minLength: {
      type: Number,
      default: 5
    },
    regexCheck: {
      type: String,
      required: false
    }
  },
  data() {
    return {
      propValue: this.value
    }
  },
  computed: {
    validated() {
      return this.satisfiesLengthRequirements() && this.satisfiesRegex()
    }
  },
  methods: {
    satisfiesLengthRequirements() {
      return this.propValue.length >= this.minLength && this.propValue.length <= this.maxLength
    },
    satisfiesRegex() {
      return this.regexCheck ? false : true
    }
  }
}
</script>

<style lang="scss">

</style>
