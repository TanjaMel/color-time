<script setup>
import {useRoute} from 'vue-router';

const route = useRoute()
</script>
<template>
  <v-app-bar app flat class="header-section py-2">
    <v-container class="d-flex justify-space-between align-center">
      <!-- Логотип и название -->
      <div class="d-flex align-center">
        <img src="@/assets/logo.png" alt="Logo" height="80" class="mr-2" />
      </div>

      <!-- Навигация -->
      <router-link to="/whyus">
        <v-btn variant="plain">Why Us</v-btn>
      </router-link>

      <router-link to="/contact">
        <v-btn variant="plain">Contact</v-btn>
      </router-link>
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
