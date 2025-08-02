<script setup>

import './assets/styles/main.css'

</script>


<template>
  <v-app class="main-bg">
    <router-view />
  </v-app>
</template>

<style>
.main-bg {
  background-color: #ffffff;
  color: #000000;
  min-height: 100vh;
}
</style>
