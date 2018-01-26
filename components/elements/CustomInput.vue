<template>
  <div class="container">
  <input
    type="text"
    :disabled="disabled"
    @blur="focusGone"
    v-model="propValue" />
  <div>{{validated}}</div>

  </div>
</template>

<script>
export default {
  name: 'CustomInput',
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
    validationType: {
      type: String,
      required: false
    }
  },
  created() {
    this.regex = this.getValidationRegex()
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
    focusGone() {
      alert('lost focus!')
    },
    satisfiesLengthRequirements() {
      return this.propValue.length >= this.minLength && this.propValue.length <= this.maxLength
    },
    satisfiesRegex() {
      return this.validationRegex ? false : true
    },
    getValidationRegex() {
      switch(this.validationType) {
        case 'email':
          return new RegExp('')
        case 'phone':
          return new RegExp('')
        default:
          return new RegExp('')
      }
    }
  }
}
</script>

<style lang="scss">

</style>
