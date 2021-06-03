<template>
  <div id="contact-container" class="page text-left">
    <Header title="CONTACT" />
    <div id="contact-form-container" class="mx-auto my-4">
      <div class="alert alert-success d-none" role="alert">
        Email successfully sent
      </div>
      <div class="alert alert-warning d-none" role="alert">
        Email failed to send
      </div>
      <div class="text-start mx-sm-5 mx-3 my-5">
        <p>
          Contact me using the form below. Or, email me directly at
          <a
            id="email-link"
            class="text-decoration-underline"
            href="mailto: ethanweiner20@gmail.com"
            >ethanweiner20@gmail.com</a
          >.
        </p>
      </div>

      <form class="contact-form mx-sm-5 mx-3" @submit.prevent="sendEmail">
        <label for="user_name" class="form-label">Your Name</label>
        <input
          type="text"
          name="user_name"
          class="form-control"
          id="user_name"
        />
        <label for="user_email" class="form-label mt-2">Your Email</label>
        <input
          type="email"
          name="user_email"
          class="form-control"
          id="user_email"
        />
        <label for="message" class="form-label mt-2">Message</label>
        <textarea name="message" id="message" class="form-control"></textarea>
        <div class="d-grid mt-4">
          <input type="submit" value="Send" class="btn-lg" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import { onMounted } from '@vue/runtime-core'
import Header from '../components/Header'
import emailjs from 'emailjs-com'

export default {
  name: 'Contact',
  components: {
    Header
  },
  methods: {
    // sendEmail
    // Sends an email to "ethwanweiner20@gmail.com" from the user specified in the form
    sendEmail: (e) => {
      const form = e.target
      emailjs
        .sendForm('gmail', 'contact_form', form, 'user_itr1mqJ0gtSIu5Bw1eok5')
        .then(
          (result) => {
            document.querySelector('.alert-success').classList.remove('d-none')

            setTimeout(() => {
              document.querySelector('.alert-success').classList.add('d-none')
            }, 5000)
            form.reset()
          },
          (error) => {
            document.querySelector('.alert-warning').classList.remove('d-none')

            setTimeout(() => {
              document.querySelector('.alert-warning').classList.add('d-none')
            }, 5000)
          }
        )
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/styles.scss';

#contact-form-container {
  max-width: 800px;
}

#email-link {
  color: lighten($main-color, 10);
  &:hover {
    color: lighten($main-color, 25);
  }
}

form {
  text-align: left;
  font-size: 25px;
  input[type='text'],
  input[type='email'],
  textarea {
    color: white !important;
    background: transparent !important;
    font-size: 25px;
  }
  textarea {
    height: 275px;
    font-size: 20px !important;
  }
  input[type='submit'] {
    color: white;
    border: none;
    background-color: $main-color;
    transition: background-color 1s ease, transform 1s ease;
    &:hover {
      background-color: lighten($main-color, 10);
      transition: background-color 1s ease transform 1s ease;
      transform: scaleY(1.2);
    }
  }
}
</style>
