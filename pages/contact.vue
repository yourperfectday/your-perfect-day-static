<template>
  <section class="container">
    <navigation/>

    <form v-if="!successfullySubmit" id="contact-form" class="contact-form">
      <h1 class="contact-intro">Thank you for getting in touch!<br>We endeavour to respond to all queries within 24 hours. We look
        forward to giving you your perfect day!</h1>

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
          message="Send Message"
          @click="submit"/>
      </div>

      <div
        v-if="isLoading"
        class="loading"/>

    </form>

    <div
      v-if="successfullySubmit">Your message has been sent. We will be in touch soon!</div>

  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Navigation from '~/components/Navigation.vue'
import axios from '~/node_modules/axios'
import CustomButton from '~/components/elements/CustomButton.vue'

export default {
  name: 'Contact',
  components: {
    Logo,
    Navigation,
    CustomButton
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
  @import "../assets/style/constants";

.container {
  .contact-intro {
    color: $primary;
    font-family: Segan;
    text-align: center;
    font-size: 16px;
    line-height: 1.3;
    font-weight: normal;
    margin-bottom: 40px;
  }
  .contact-form {
    box-sizing: border-box;
    max-width: 480px;
    width: 100%;
    padding: 30px;
    margin-top: 70px;
    /*position: absolute;*/
    /*top: 0;*/

    .contact-container {
      .label, .input, button {
        width: 100%;
        display: block;
      }

      .label,
      .input {
        font-size: 14px;
      }

      input, button {
        height: 40px;
      }

      .input {
        box-sizing: border-box;
        border: 1px solid $primary;
        padding: 7px;
      }

      .label {
        color: $primary;
        font-family: sans-serif;
        margin: 10px 0 5px;
      }

      &.message {
        .input {
          resize: none;
        }
      }

      &.submit {
        margin-top: 20px;
      }
    }

    .loading {
      background: rgba(255, 255, 255, 0.6) url('~/assets/loading.svg') no-repeat center;
      height: 100%;
      left: 0;
      position: absolute;
      top: 0;
      width: 100%;
    }
  }
}
</style>
