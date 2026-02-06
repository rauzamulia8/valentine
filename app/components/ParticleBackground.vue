<template>
  <div class="particle-container">
    <div v-for="n in 50" :key="n" class="particle" :style="getParticleStyle(n)">
      {{ getEmoji(n) }}
    </div>
  </div>
</template>

<script setup>
const emojis = ['💕', '💖', '💗', '💓', '💝', '✨', '⭐', '🌹', '🌸', '💐']

const getEmoji = (n) => emojis[n % emojis.length]

const getParticleStyle = (n) => ({
  left: `${Math.random() * 100}%`,
  animationDelay: `${Math.random() * 15}s`,
  animationDuration: `${10 + Math.random() * 20}s`,
  fontSize: `${12 + Math.random() * 24}px`,
  opacity: 0.3 + Math.random() * 0.4,
})
</script>

<style scoped>
.particle-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 0;
  overflow: hidden;
}

.particle {
  position: absolute;
  top: -50px;
  animation: fall linear infinite;
}

@keyframes fall {
  0% {
    transform: translateY(-10vh) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: 0.6;
  }
  90% {
    opacity: 0.6;
  }
  100% {
    transform: translateY(110vh) rotate(720deg);
    opacity: 0;
  }
}
</style>
