<template>
  <div class="floating-hearts">
    <span v-for="n in 10" :key="n" class="heart">💕</span>
  </div>
</template>

<style scoped>
.floating-hearts {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 0;
  overflow: hidden;
}

.heart {
  position: absolute;
  opacity: 0.3;
  animation: float 6s ease-in-out infinite;
}

.heart:nth-child(1) { left: 5%; top: 10%; animation-delay: 0s; font-size: 24px; }
.heart:nth-child(2) { left: 15%; top: 30%; animation-delay: 1s; font-size: 32px; }
.heart:nth-child(3) { left: 25%; top: 50%; animation-delay: 2s; font-size: 20px; }
.heart:nth-child(4) { left: 35%; top: 70%; animation-delay: 0.5s; font-size: 28px; }
.heart:nth-child(5) { left: 45%; top: 20%; animation-delay: 1.5s; font-size: 36px; }
.heart:nth-child(6) { left: 55%; top: 40%; animation-delay: 2.5s; font-size: 22px; }
.heart:nth-child(7) { left: 65%; top: 60%; animation-delay: 0.8s; font-size: 30px; }
.heart:nth-child(8) { left: 75%; top: 80%; animation-delay: 1.8s; font-size: 26px; }
.heart:nth-child(9) { left: 85%; top: 15%; animation-delay: 2.2s; font-size: 34px; }
.heart:nth-child(10) { left: 92%; top: 45%; animation-delay: 0.3s; font-size: 28px; }

@keyframes float {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-20px) rotate(5deg); }
}
</style>
