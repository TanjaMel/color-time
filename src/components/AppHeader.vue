<script setup>

const scrollTo = (id) => {
  const element = document.getElementById(id);
  if (element) {
    element.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    });
  }
};
</script>
<template>
  <v-app-bar app flat class="header-section py-2">
    <v-container class="d-flex justify-space-between align-center">
      <!-- Логотип и название -->
      <div class="d-flex align-center">
        <img src="@/assets/logo.png" alt="Logo" height="80" class="mr-2" />
      </div>

      <!-- Навигация -->
          <div class="d-flex">
            <v-btn @click="scrollTo('why-us')" variant="plain">
              Why Us
            </v-btn>
            <v-btn @click="scrollTo('about-us')" variant="plain">
              About The App
            </v-btn>
            <v-btn @click="scrollTo('contact-us')" variant="plain">
              Contact
            </v-btn>
          </div>
    </v-container>
  </v-app-bar>
</template>

<style scoped>
.header-section {
  background-color: #ffffff;
  background-image: url('@/assets/logo1.png'); /* путь к изображению */
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  width: 100%;

  padding-top: 40px;
  padding-bottom: 20px;
  color: #ffffff;
}
</style>
