<template>
  <section class="countdown-section">
    <div class="countdown-container love-card">
      <h2 class="script-font">💕 Countdown to Valentine's Day 💕</h2>
      <p class="countdown-subtitle">14 Februari 2026</p>
      
      <div class="countdown-display">
        <div class="time-block">
          <span class="time-value">{{ days }}</span>
          <span class="time-label">Hari</span>
        </div>
        <div class="time-separator">:</div>
        <div class="time-block">
          <span class="time-value">{{ hours }}</span>
          <span class="time-label">Jam</span>
        </div>
        <div class="time-separator">:</div>
        <div class="time-block">
          <span class="time-value">{{ minutes }}</span>
          <span class="time-label">Menit</span>
        </div>
        <div class="time-separator">:</div>
        <div class="time-block">
          <span class="time-value">{{ seconds }}</span>
          <span class="time-label">Detik</span>
        </div>
      </div>
      
      <p v-if="isValentinesDay" class="celebration-text script-font">🎉 Selamat Hari Valentine! 🎉</p>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue'

const days = ref('00')
const hours = ref('00')
const minutes = ref('00')
const seconds = ref('00')
const isValentinesDay = ref(false)

let interval = null

const updateCountdown = () => {
  const valentinesDay = new Date('2026-02-14T00:00:00')
  const now = new Date()
  const diff = valentinesDay - now
  
  if (diff <= 0) {
    isValentinesDay.value = true
    days.value = '00'
    hours.value = '00'
    minutes.value = '00'
    seconds.value = '00'
    return
  }
  
  const d = Math.floor(diff / (1000 * 60 * 60 * 24))
  const h = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
  const m = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60))
  const s = Math.floor((diff % (1000 * 60)) / 1000)
  
  days.value = String(d).padStart(2, '0')
  hours.value = String(h).padStart(2, '0')
  minutes.value = String(m).padStart(2, '0')
  seconds.value = String(s).padStart(2, '0')
}

onMounted(() => {
  updateCountdown()
  interval = setInterval(updateCountdown, 1000)
})

onUnmounted(() => {
  if (interval) clearInterval(interval)
})
</script>

<style scoped>
.countdown-section {
  padding: 60px 20px;
  position: relative;
  z-index: 1;
}

.countdown-container {
  max-width: 700px;
  margin: 0 auto;
  text-align: center;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.95) 0%, rgba(255, 245, 248, 0.95) 100%);
}

.countdown-container h2 {
  font-size: 2.2rem;
  color: #c44569;
  margin-bottom: 8px;
}

.countdown-subtitle {
  color: #888;
  font-size: 1rem;
  margin-bottom: 30px;
}

.countdown-display {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
}

.time-block {
  background: linear-gradient(135deg, #ff6b9d 0%, #c44569 100%);
  padding: 20px 24px;
  border-radius: 16px;
  min-width: 90px;
  box-shadow: 0 10px 30px rgba(255, 107, 157, 0.3);
}

.time-value {
  display: block;
  font-size: 2.5rem;
  font-weight: 700;
  color: white;
  line-height: 1;
}

.time-label {
  display: block;
  font-size: 0.85rem;
  color: rgba(255, 255, 255, 0.9);
  margin-top: 8px;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.time-separator {
  font-size: 2.5rem;
  font-weight: bold;
  color: #c44569;
}

.celebration-text {
  margin-top: 30px;
  font-size: 2rem;
  color: #c44569;
  animation: pulse 1s infinite;
}

@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.05); }
}

@media (max-width: 768px) {
  .countdown-section {
    padding: 40px 16px;
  }
  
  .countdown-container h2 {
    font-size: 1.6rem;
  }
  
  .countdown-display {
    gap: 8px;
  }
  
  .time-block {
    padding: 16px 18px;
    min-width: 70px;
  }
  
  .time-value {
    font-size: 1.8rem;
  }
  
  .time-separator {
    font-size: 1.8rem;
  }
}
</style>
