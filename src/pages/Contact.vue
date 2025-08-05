<script setup>
import { ref } from 'vue'

const valid = ref(false)
const firstname = ref('')
const lastname = ref('')
const email = ref('')
const message = ref('')

const nameRules = [
  value => !!value || 'Name is required.',
  value => (value?.length <= 10) || 'Name must be less than 10 characters.'
]

const emailRules = [
  value => !!value || 'E-mail is required.',
  value => /.+@.+\..+/.test(value) || 'E-mail must be valid.'
]

const submitForm = () => {
  if (valid.value) {
    // Тут можно отправить данные или показать сообщение об успехе
    alert('Message sent successfully!')

    // Очистим поля
    firstname.value = ''
    lastname.value = ''
    email.value = ''
    message.value = ''
    valid.value = false
  }
}
</script>

<template>
  <v-container class="about-section pa-0" fluid id="contact-us">
    <div class="content-wrapper">

      <v-col cols="12" md="4" class="text-start  mt-12">
        <h2 class="about-title">CONTACT US</h2>
        <v-form v-model="valid" @submit.prevent="submitForm">
          <v-container>
            <v-row>
              <v-col cols="12" md="6">
                <v-text-field
                  v-model="firstname"
                  :counter="10"
                  :rules="nameRules"
                  label="First name"
                  required
                />
              </v-col>

              <v-col cols="12" md="6">
                <v-text-field
                  v-model="lastname"
                  :counter="10"
                  :rules="nameRules"
                  label="Last name"
                  required
                />
              </v-col>

              <v-col cols="12">
                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="E-mail"
                  required
                />
              </v-col>

              <v-col cols="12">
                <v-textarea
                  v-model="message"
                  label="Your message"
                  auto-grow
                  rows="3"
                  placeholder="Write your message here..."
                />
              </v-col>

              <v-col cols="12" class="text-center">
                <v-btn
                  color="primary"
                  large
                  class="send-btn"
                  :disabled="!valid"
                  @click="submitForm"
                >
                  Send Message
                </v-btn>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-col>
    </div>
  </v-container>
</template>

<style scoped>
.content-wrapper {
  max-width: 1200px;
  margin: 0 auto;
  padding: 32px 16px;
  padding-bottom: 80px; /* добавили здесь отступ */
}

.about-section {
  background-color: #ffffff;
  color: #2c1e4a;
  background-image: url("@/assets/contactFormBG.png");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  padding-top: 40px;
  padding-bottom: 20px;
  object-fit: cover;
  max-width: 1200px;

  min-height: 570px;
  height: auto;
}


.about-title {
  font-size: 32px;
  font-weight: 700;
  margin-bottom: 32px;
  text-align: center;
}

.send-btn {
  background-color: #0395ff;
  color: #0395ff;
  padding: 12px 32px;
  border-radius: 8px;

}

.send-btn:hover {
  background-color: #0395ff;
}
</style>
