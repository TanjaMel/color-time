<script setup>
import { ref, onUnmounted, computed } from 'vue'

const selectedMinutes = ref(1)
const selectedSeconds = ref(0)

const duration = ref(0) // общее время в секундах
const remaining = ref(0) // оставшееся время
const isRunning = ref(false)
const isPaused = ref(false)
const currentColor = ref('green')
let timerInterval = null

const radius = 90
const circumference = 2 * Math.PI * radius

const offset = computed(() => {
  if (duration.value === 0) return circumference
  const percent = remaining.value / duration.value
  return circumference * (1 - percent)
})

function playBeep() {
  const audio = new Audio('/beep.mp3')
  audio.play().catch(() => {})
}

function runTimer() {
  clearInterval(timerInterval)
  timerInterval = setInterval(() => {
    if (isPaused.value) return

    remaining.value--

    const halfway = Math.floor(duration.value / 2)
    if (remaining.value === halfway) currentColor.value = 'yellow'
    if (remaining.value === 10) {
      playBeep()
      currentColor.value = 'red'
    }

    if (remaining.value <= 0) {
      clearInterval(timerInterval)
      isRunning.value = false
      isPaused.value = false
      currentColor.value = 'red'
      remaining.value = 0
    }
  }, 1000)
}

function startTimer() {
  // Если на паузе — продолжить
  if (isPaused.value) {
    isPaused.value = false
    isRunning.value = true
    runTimer()
    return
  }

  // Если уже запущен — ничего делать
  if (isRunning.value) return

  // Стартуем новый таймер
  duration.value = selectedMinutes.value * 60 + selectedSeconds.value
  if (duration.value < 10) return

  remaining.value = duration.value
  currentColor.value = 'green'
  isRunning.value = true
  runTimer()
}

function pauseTimer() {
  if (!isRunning.value) return
  isPaused.value = true
  isRunning.value = false
}

function resetTimer() {
  clearInterval(timerInterval)
  isRunning.value = false
  isPaused.value = false
  remaining.value = 0
  currentColor.value = 'green'
}

const minuteOptions = Array.from({ length: 60 }, (_, i) => i)
const secondOptions = Array.from({ length: 60 }, (_, i) => i)

onUnmounted(() => {
  clearInterval(timerInterval)
})
</script>

<template>
  <v-container class="main-section pa-0" fluid>
    <v-row justify="center">
      <v-col cols="12" md="10" lg="8">
        <v-card
          class="pa-6"
          elevation="8"
          style="border: 2px solid #dcdcdc; border-radius: 24px; background-color: #fdfdfd;"
        >
          <v-row class="d-flex justify-center align-start" no-gutters>

        <!-- Set Time -->
        <v-col cols="12" class="text-center mb-2" style="max-width: 150px;">
          <v-row class="mt-2" dense>
            <v-col cols="6">
              <v-select
                v-model="selectedMinutes"
                :items="minuteOptions"
                label="Minutes"
                density="comfortable"
                hide-details
                :disabled="isRunning"
              />
            </v-col>
            <v-col cols="6">
              <v-select
                v-model="selectedSeconds"
                :items="secondOptions"
                label="Seconds"
                density="comfortable"
                hide-details
                :disabled="isRunning"
              />
            </v-col>
          </v-row>
        </v-col>

            <!-- Buttons -->
            <v-col cols="12" class="mt-4" style="max-width: 320px;">
              <div class="d-flex justify-center" style="gap: 16px;">
                <v-btn
                  color="#0395ff"
                  @click="startTimer"
                  :disabled="isRunning && !isPaused"
                  class="px-4 py-2"
                  style="font-size: 0.8rem; min-width: 60px;"
                  density="comfortable"
                >
                  {{ isPaused ? 'Continue' : 'Start' }}
                </v-btn>

                <v-btn
                  color="#0395ff"
                  @click="pauseTimer"
                  :disabled="!isRunning"
                  class="px-4 py-2"
                  style="font-size: 0.8rem; min-width: 60px;"
                  density="comfortable"
                >
                  Pause
                </v-btn>

                <v-btn
                  color="#0395ff"
                  @click="resetTimer"
                  :disabled="!isRunning && remaining === 0"
                  class="px-4 py-2"
                  style="font-size: 0.8rem; min-width: 60px;"
                  density="comfortable"
                >
                  Reset
                </v-btn>
              </div>
            </v-col>

      <!-- Левая колонка: Set Time, кнопки, светофор -->
      <v-col cols="12" md="6" class="d-flex flex-column align-center">
        <!-- Traffic Light -->
        <v-col cols="12" class="d-flex justify-center mt-6">
          <div class="traffic-body">
            <div :class="['light', currentColor === 'green' ? 'on green' : 'green']"></div>
            <div :class="['light', currentColor === 'yellow' ? 'on yellow' : 'yellow']"></div>
            <div :class="['light', currentColor === 'red' ? 'on red' : 'red']"></div>
          </div>
        </v-col>
      </v-col>

      <!-- Правая колонка: Таймер-круг -->
      <v-col cols="12" md="6" class="d-flex justify-center">
        <v-card
          class="pa-6 d-flex flex-column align-center"
          elevation="6"
          style="border: 1px dashed #000000; border-radius: 20px; background-color: #ffffff; max-width: 400px; width: 100%;"
        >
          <div class="timer-wrapper">
            <div class="timer-circle">
              <svg class="progress-ring" width="200" height="200">
                <circle
                  class="progress-ring__circle"
                  stroke="#2196f3"
                  stroke-width="8"
                  fill="white"
                  r="90"
                  cx="100"
                  cy="100"
                  :stroke-dasharray="circumference"
                  :stroke-dashoffset="offset"
                />
              </svg>
              <div class="time-text">{{ remaining }}</div>
            </div>
          </div>
        </v-card>
      </v-col>
          </v-row>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>


<style scoped>
.content-wrapper {
  max-width: 1200px;
  margin: 0 auto;
  padding: 32px 16px;
  padding-bottom: 80px; /* добавили здесь отступ */
}

.main-section {
  background-color: #ffffff;
  color: #2c1e4a;

  padding-top: 40px;
  padding-bottom: 20px;
  object-fit: cover;
  max-width: 1200px;

  min-height: 570px;
  height: auto;
}

.timer-circle {
  position: relative;
  width: 200px;
  height: 200px;
  margin-bottom: 20px;
}

.progress-ring__circle {
  transition: stroke-dashoffset 1s linear;
  transform: rotate(-90deg);
  transform-origin: 50% 50%;
}

.time-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 32px;
  font-weight: bold;
  color: #000;
  user-select: none;
}

.traffic-body {
  height: 360px;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #222;
  padding: 20px;
  border-radius: 24px;
  width: 120px;
  box-shadow: 0 0 12px rgba(0, 0, 0, 0.4);
}

.timer-wrapper {
  height: 360px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.light {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background-color: #555;
  margin: 12px 0;
  transition: background-color 0.5s;
  box-shadow: inset 0 0 8px rgba(0, 0, 0, 0.6);
}

.green.on {
  background-color: #4caf50;
}

.yellow.on {
  background-color: #ffeb3b;
}

.red.on {
  background-color: #f44336;
  animation: blink 1s infinite;
}

@keyframes blink {
  0%, 50%, 100% {
    opacity: 1;
  }
  25%, 75% {
    opacity: 0.4;
  }
}
</style>
