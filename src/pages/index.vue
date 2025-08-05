<script setup>
import AppHeader from "@/components/AppHeader.vue"
import TrafficLightTimer from '@/components/TrafficLightTimer.vue'

import { useRouter } from 'vue-router'

const router = useRouter()

</script>

<template>
  <v-container id="main">
    <div class="content-wrapper">
      <TrafficLightTimer />
    </div>
  </v-container>
</template>


<style scoped>
.content-wrapper {
  max-width: 1200px;
  margin: 0 auto;
  padding: 32px 16px;
  padding-bottom: 40px;
}

</style>
