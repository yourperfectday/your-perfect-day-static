<template>
  <form id="contact-form" class="contact-form">
    <div class="close">x</div>
    <div class="name contact-container">
      <label class="label"
          for="name">Name*:</label>
      <input type="text"
          v-model="formData.name"
          id="name"
          name="name"/>
    </div>
    <div class="email contact-container">
      <label class="label"
          for="email">Email*:</label>
      <input type="text"
          v-model="formData.email"
          id="email"
          name="email" />
    </div>
    <div class="description contact-container">
      <label class="label"
          for="description">Message*:</label>
      <textarea id="description"
          v-model="formData.description"
          name="description"
          resize="none"
          rows="5"/>
    </div>
    <div class="submit contact-container">
      <button name="submit"
          @click.prevent="submit">Send</button>
    </div>
  </form>
</template>

<script>
  import axios from '~/node_modules/axios'

  export default {
    name: 'ContactWidget',
    props: [],
    data() {
      return {
        formData: {
          name: null,
          email: null,
          description: null
        }
      }
    },
    methods: {
      submit() {
        console.log(JSON.stringify(this.formData))
        axios.post(
            'https://o430f22hp6.execute-api.us-east-1.amazonaws.com/prod/helloWorldNodeJs', this.formData)
          .then((response) => {
            console.log(JSON.stringify(response))
          })
          .catch((error) => {
            console.log(JSON.stringify(error))
          });
      }
    }
  }
</script>

<style lang="scss" scoped="true">
.contact-form {
  border-radius: 5px;
  position: fixed;
  bottom: 10px;
  right: 10px;

  display: flex;
  flex-flow: column;
  align-items: left;
  background-color: white;
  padding: 20px;
  z-index: 100;

  .close {
    position: absolute;
    top: 0;
    right: 0;

    &:hover {
      cursor: pointer;
    }
  }

  .contact-container {
    display: flex;
    flex-flow: column;
    align-items: left;
    margin: 5px 0;

    textarea {
      resize: none;
    }
  }
}
</style>
