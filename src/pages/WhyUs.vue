<script setup>
import {useRoute} from 'vue-router';

const route = useRoute()
</script>

<template>
  <v-container class="why-us-section py-16" fluid id="why-us">
    <div class="content-wrapper">
      <h2 class="text-center mb-12 why-us-title">Why Choose Us</h2>

      <v-row class="text-center" justify="center">
        <!-- Колонка 1 -->
        <v-col cols="12" md="4">
          <v-img src="@/assets/puzzle-piece.png" alt="Playful design" max-width="100" class="mx-auto mb-4" />
          <h3 class="why-us-heading">Gamified Experience</h3>
          <p class="why-us-subtitle">Makes time fun and engaging – like solving a puzzle!</p>
        </v-col>


        <!-- Колонка 2 -->
        <v-col cols="12" md="4">
          <v-img src="@/assets/witness.png" alt="Visual timer" max-width="100" class="mx-auto mb-4" />
          <h3 class="why-us-heading">Visual Timer</h3>
          <p class="why-us-subtitle">Time you can see – helps children grasp time intuitively.</p>
        </v-col>

        <!-- Колонка 3 -->
        <v-col cols="12" md="4">
          <v-img src="@/assets/self-regulation.png" alt="Self-regulation" max-width="100" class="mx-auto mb-4" />
          <h3 class="why-us-heading">Self-Regulation</h3>
          <p class="why-us-subtitle">Supports development of independence and responsibility.</p>
        </v-col>
      </v-row>
    </div>
  </v-container>
</template>


<style scoped>
.content-wrapper {
  max-width: 1200px;
  margin: 0 auto;
  padding: 32px 16px;
}

.why-us-section {
  background-color: #ffffff;
  color: #2c1e4a;
  width: 100%;
  font-family: 'Red Hat Display', sans-serif;
}

.why-us-title {
  font-size: 32px;
  font-weight: bold;
}

.why-us-heading {
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 8px;
}

.why-us-subtitle {
  font-size: 16px;
  color: #4e4e4e;
}
</style>
