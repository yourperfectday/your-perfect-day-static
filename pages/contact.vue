<template>
  <section class="container">
    <logo/>
    <navigation/>
    <form v-if="!successfullySubmit" id="contact-form" class="contact-form">
      <h1 class="contact-intro">Your perfect day is just a click away. Fill out the form below and Aileen will be in touch shortly.</h1>
      <div class="name contact-container">
        <label class="label"
               for="name">Name*</label>
        <input type="text"
               class="input"
               v-model="formData.name"
               id="name"
               name="name"/>
      </div>
      <div class="email contact-container">
        <label class="label"
               for="email">Email*</label>
        <input type="text"
               class="input"
               v-model="formData.email"
               id="email"
               name="email" />
      </div>
      <div class="phone contact-container">
        <label class="label"
               for="phone">Phone</label>
        <input type="text"
               class="input"
               v-model="formData.phone"
               id="phone"
               name="phone" />
      </div>
      <div class="description contact-container">
        <label class="label"
               for="description">Message*</label>
        <textarea id="description"
                  class="input"
                  v-model="formData.description"
                  name="description"
                  resize="none"
                  rows="5"/>
      </div>
      <div class="submit contact-container">
        <custom-button
          :isEnabled="isValidField(formData.name) && isValidField(formData.email) && isValidField(formData.phone) && isValidField(formData.description)"
          message="Send"
          @click="submit"/>
      </div>
    </form>

    <div
      v-if="isLoading"
      class="loading"/>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Navigation from '~/components/Navigation.vue'
import axios from '~/node_modules/axios'
import CustomButton from '~/components/elements/CustomButton.vue'
import TextInput from '~/components/elements/TextInput.vue'

export default {
  name: 'Contact',
  components: {
    Logo,
    Navigation,
    CustomButton,
    TextInput
  },
  props: [],
  data() {
    return {
      successfullySubmit: false,
      isLoading: false,
      formData: {
        name: null,
        email: null,
        phone: null,
        description: null
      }
    }
  },
  methods: {
    isValidField(field) {
      return field && field.length > 0
    },
    submit() {
      this.isLoading = true
      axios.post(
        'https://o430f22hp6.execute-api.us-east-1.amazonaws.com/prod/helloWorldNodeJs', this.formData)
        .then((response) => {
          this.isLoading = false
          this.successfullySubmit = true
        })
        .catch((error) => {
          this.isLoading = false
          console.log(JSON.stringify(error))
        });
    }
  }
}
</script>

<style lang="scss">
.container {
  margin-top: 100px;
  position: relative;

  .contact-intro {
    color: $primary;
    font-family: sans-serif;
    text-align: center;
    font-size: 18px;
    font-weight: normal;
    margin: 30px;
  }
  .contact-form {
    margin: 150px auto 50px;
    width: 400px;
    max-width: calc(100% - 30px);

    .contact-container {
      .label,
      .input {
        display: block;
        width: 100%;
      }

      .label {
        color: $primary;
        font-family: sans-serif;
        font-size: 14px;
        margin: 10px 0 5px;
      }

      &.description {
        .input {
          resize: none;
        }
      }

      &.submit {
        margin-top: 20px;
        text-align: center;
      }
    }
  }

  .loading {
    background: url('~/assets/loading.svg') no-repeat center;
    height: 100%;
    left: 0;
    position: absolute;
    top: 0;
    width: 100%;
  };
}
</style>
