<template>
  <section class="container">
    <logo/>
    <navigation/>

    <form v-if="!successfullySubmit" id="contact-form" class="contact-form">
      <h1 class="contact-intro">Your perfect day is just a click away.<br>Fill out the form below and Aileen will be in touch shortly.</h1>

      <div class="name contact-container">
        <label class="label"
               for="name">Name*</label>
        <input type="text"
               class="input"
               v-model="formData.name"
               id="name"
               name="name" />
      </div>

      <div class="email contact-container">
        <label class="label"
               for="email">Email*</label>
        <input type="email"
               class="input"
               v-model="formData.email"
               id="email"
               name="email" />
      </div>

      <div class="phone contact-container">
        <label class="label"
               for="phone">Phone</label>
        <input type="tel"
               class="input"
               v-model="formData.phone"
               id="phone"
               name="phone" />
      </div>

      <div class="message contact-container">
        <label class="label"
               for="message">Message*</label>
        <textarea id="message"
                  class="input"
                  v-model="formData.message"
                  name="message"
                  resize="none"
                  rows="5"/>
      </div>

      <div class="submit contact-container">
        <custom-button
          :isEnabled="canSubmit"
          message="Send"
          @click="submit"/>
      </div>

    </form>

    <div
      v-if="isLoading"
      class="loading"/>

    <div
      v-if="successfullySubmit">Thank you for your message. Aileen will be in touch with you shortly.</div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Navigation from '~/components/Navigation.vue'
import axios from '~/node_modules/axios'
import CustomButton from '~/components/elements/CustomButton.vue'
import CustomInput from '~/components/elements/CustomInput.vue'

export default {
  name: 'Contact',
  components: {
    Logo,
    Navigation,
    CustomButton,
    CustomInput
  },
  props: [],
  data() {
    return {
      successfullySubmit: false,
      isLoading: false,
      formData: {
        name: '',
        email: '',
        phone: '',
        message: ''
      }
    }
  },
  methods: {
    nameIsValid() {
      return this.formData.name.length > 0 && this.formData.name.length < 100
    },
    emailIsValid() {
      let emailRegex = /^(([^<>()[\]\\.,;:\s@\"]+(\.[^<>()[\]\\.,;:\s@\"]+)*)|(\".+\"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return emailRegex.test(this.formData.email);
    },
    phoneIsValid() {
      return this.formData.phone.length > 0 ? false : true
    },
    messageIsValid() {
      return this.formData.message.length > 0 && this.formData.message.length < 500
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
  },
  computed: {
    canSubmit: function() {
      return this.nameIsValid() && this.emailIsValid() && this.messageIsValid()
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

      &.message {
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
