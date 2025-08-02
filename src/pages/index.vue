<script setup>
import AppHeader from "@/components/AppHeader.vue"
import TrafficLightTimer from '@/components/TrafficLightTimer.vue'
import { useRouter } from 'vue-router'

const router = useRouter()

function goToTimer() {
  router.push('/timer')
}
</script>

<template>
  <AppHeader />
  <TrafficLightTimer />

</template>


<style scoped>
.content-wrapper {
  max-width: 1200px;
  margin: 0 auto;
  padding: 32px 16px;
  padding-bottom: 80px; /* добавили здесь отступ */
}

.hero-section {
  background-color: #ffffff;
  color: #2c1e4a;
  background-image: url("@/assets/contactFormBG.png");
  max-width: 1200px;
  background-position: center;
  background-repeat: no-repeat;
  padding-top: 40px;
  padding-bottom: 20px;
  object-fit: cover;

  min-height: 450px;
  height: auto;
}



.hero-title {
  font-size: 48px;
  font-weight: 700;
  color: #000000;
}

.hero-subtitle {
  font-size: 20px;
  color: #3d3d3d;
  margin-top: 16px;
}

.hero-image {
  max-width: 100%;
  height: auto;
}
</style>
