<template>
  <div v-if="!isOpened" class="envelope-intro" @click="openEnvelope">
    <div class="intro-background">
      <div v-for="n in 40" :key="n" class="bg-element" :style="getElementStyle(n)">
        {{ getEmoji(n) }}
      </div>
    </div>

    <div class="envelope-wrapper">
      <div class="envelope-container" :class="{ opening: isAnimating }">
        <!-- Shadow -->
        <div class="envelope-shadow"></div>

        <!-- Envelope Body -->
        <div class="envelope">
          <!-- Back Layer -->
          <div class="envelope-back">
            <div class="envelope-pattern"></div>
          </div>

          <!-- Letter that slides out -->
          <div class="letter" :class="{ 'slide-out': isAnimating }">
            <div class="letter-inner">
              <div class="letter-decoration top-left">❀</div>
              <div class="letter-decoration top-right">❀</div>
              <div class="letter-heart">💖</div>
              <p class="letter-title script-font">For You</p>
              <p class="letter-subtitle">with love</p>
              <div class="letter-decoration bottom-left">❀</div>
              <div class="letter-decoration bottom-right">❀</div>
            </div>
          </div>

          <!-- Front -->
          <div class="envelope-front">
            <div class="envelope-front-inner"></div>
            <div class="envelope-stripe"></div>
          </div>

          <!-- Flap -->
          <div class="envelope-flap" :class="{ 'flap-open': isAnimating }">
            <div class="flap-inner"></div>
          </div>

          <!-- Heart Seal -->
          <div class="heart-seal" :class="{ 'seal-break': isAnimating }">
            <span class="seal-heart">💝</span>
            <div class="seal-shine"></div>
          </div>
        </div>
      </div>

      <!-- Open Me Text -->
      <div class="open-me-container" :class="{ hide: isAnimating }">
        <div class="open-me-badge">
          <span class="sparkle-left">✨</span>
          <span class="open-me-text script-font">Open Me</span>
          <span class="sparkle-right">✨</span>
        </div>
        <div class="tap-hint">
          <span class="hand-icon">👆</span>
          <span>Tap to open</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['opened'])

const isOpened = ref(false)
const isAnimating = ref(false)

const emojis = ['💕', '💖', '💗', '✨', '⭐', '🌸', '💐', '🌹', '💝', '❤️']

const getEmoji = (n) => emojis[n % emojis.length]

const openEnvelope = () => {
  if (isAnimating.value) return
  isAnimating.value = true

  setTimeout(() => {
    isOpened.value = true
    emit('opened')
  }, 2200)
}

const getElementStyle = (n) => ({
  left: `${Math.random() * 100}%`,
  top: `${Math.random() * 100}%`,
  animationDelay: `${Math.random() * 6}s`,
  animationDuration: `${6 + Math.random() * 4}s`,
  fontSize: `${14 + Math.random() * 20}px`,
  opacity: 0.2 + Math.random() * 0.2,
})
</script>

<style scoped>
.envelope-intro {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1000;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #ffeef5 0%, #ffe4ec 30%, #ffd6e7 60%, #ffcce0 100%);
  cursor: pointer;
  overflow: hidden;
}

.intro-background {
  position: absolute;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.bg-element {
  position: absolute;
  animation: floatAround ease-in-out infinite;
}

@keyframes floatAround {

  0%,
  100% {
    transform: translateY(0) translateX(0) rotate(0deg) scale(1);
  }

  25% {
    transform: translateY(-20px) translateX(10px) rotate(5deg) scale(1.1);
  }

  50% {
    transform: translateY(-30px) translateX(-5px) rotate(-3deg) scale(1);
  }

  75% {
    transform: translateY(-15px) translateX(-10px) rotate(3deg) scale(1.05);
  }
}

.envelope-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 40px;
  z-index: 10;
}

.envelope-container {
  position: relative;
  perspective: 1500px;
}

.envelope-shadow {
  position: absolute;
  bottom: -30px;
  left: 50%;
  transform: translateX(-50%);
  width: 280px;
  height: 30px;
  background: radial-gradient(ellipse at center, rgba(196, 69, 105, 0.25) 0%, transparent 70%);
  filter: blur(10px);
}

.envelope {
  position: relative;
  width: 320px;
  height: 220px;
  transform-style: preserve-3d;
  animation: envelopeFloat 3s ease-in-out infinite;
}

@keyframes envelopeFloat {

  0%,
  100% {
    transform: translateY(0);
  }

  50% {
    transform: translateY(-10px);
  }
}

.envelope-back {
  position: absolute;
  width: 100%;
  height: 100%;
  background: linear-gradient(145deg, #fff 0%, #fef9fb 50%, #fdf2f6 100%);
  border-radius: 12px;
  box-shadow:
    0 25px 80px rgba(196, 69, 105, 0.25),
    0 5px 20px rgba(196, 69, 105, 0.15),
    inset 0 1px 0 rgba(255, 255, 255, 0.9);
  overflow: hidden;
}

.envelope-pattern {
  position: absolute;
  width: 100%;
  height: 100%;
  background:
    repeating-linear-gradient(45deg,
      transparent,
      transparent 20px,
      rgba(255, 192, 203, 0.1) 20px,
      rgba(255, 192, 203, 0.1) 22px);
}

.envelope-front {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 65%;
  background: linear-gradient(180deg, #fff5f8 0%, #ffecf1 50%, #ffe4ec 100%);
  border-radius: 0 0 12px 12px;
  z-index: 3;
  overflow: hidden;
  box-shadow: 0 -2px 10px rgba(255, 192, 203, 0.3);
}

.envelope-front-inner {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 60%;
  background: linear-gradient(135deg,
      transparent 0%,
      transparent 48%,
      rgba(255, 182, 193, 0.4) 48%,
      rgba(255, 182, 193, 0.4) 52%,
      transparent 52%);
}

.envelope-stripe {
  position: absolute;
  bottom: 25%;
  left: 50%;
  transform: translateX(-50%);
  width: 60%;
  height: 3px;
  background: linear-gradient(90deg, transparent, rgba(255, 107, 157, 0.3), transparent);
  border-radius: 2px;
}

.envelope-flap {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 55%;
  background: linear-gradient(180deg, #fff 0%, #fff9fb 50%, #fff5f8 100%);
  clip-path: polygon(0 0, 50% 100%, 100% 0);
  transform-origin: top center;
  transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1);
  z-index: 4;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.08);
}

.flap-inner {
  position: absolute;
  width: 100%;
  height: 100%;
  background: linear-gradient(180deg,
      rgba(255, 240, 245, 0.5) 0%,
      transparent 100%);
}

.envelope-flap.flap-open {
  transform: rotateX(180deg);
}

/* Letter */
.letter {
  position: absolute;
  top: 15%;
  left: 8%;
  width: 84%;
  height: 75%;
  background: linear-gradient(145deg, #ffffff 0%, #fffbfc 50%, #fff8fa 100%);
  border-radius: 8px;
  box-shadow:
    0 4px 15px rgba(0, 0, 0, 0.08),
    inset 0 1px 0 rgba(255, 255, 255, 0.9);
  z-index: 2;
  transition: transform 1s cubic-bezier(0.25, 0.46, 0.45, 0.94) 0.4s;
  overflow: hidden;
}

.letter.slide-out {
  transform: translateY(-160px) scale(1.05);
}

.letter-inner {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 24px;
  position: relative;
  background:
    radial-gradient(circle at 0% 0%, rgba(255, 182, 193, 0.1) 0%, transparent 50%),
    radial-gradient(circle at 100% 100%, rgba(255, 182, 193, 0.1) 0%, transparent 50%);
}

.letter-decoration {
  position: absolute;
  font-size: 18px;
  color: #ffb6c1;
  opacity: 0.6;
}

.letter-decoration.top-left {
  top: 12px;
  left: 12px;
}

.letter-decoration.top-right {
  top: 12px;
  right: 12px;
}

.letter-decoration.bottom-left {
  bottom: 12px;
  left: 12px;
}

.letter-decoration.bottom-right {
  bottom: 12px;
  right: 12px;
}

.letter-heart {
  font-size: 50px;
  margin-bottom: 12px;
  animation: heartPulse 1.5s ease-in-out infinite;
  filter: drop-shadow(0 4px 15px rgba(255, 107, 157, 0.4));
}

@keyframes heartPulse {

  0%,
  100% {
    transform: scale(1);
  }

  50% {
    transform: scale(1.15);
  }
}

.letter-title {
  font-size: 2.2rem;
  color: #c44569;
  margin-bottom: 4px;
  text-shadow: 0 2px 10px rgba(196, 69, 105, 0.2);
}

.letter-subtitle {
  font-size: 0.95rem;
  color: #e88fa3;
  font-style: italic;
  letter-spacing: 2px;
}

/* Heart Seal */
.heart-seal {
  position: absolute;
  top: 42%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 70px;
  height: 70px;
  background: linear-gradient(145deg, #e74c3c 0%, #c0392b 50%, #a93226 100%);
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 6;
  box-shadow:
    0 8px 25px rgba(231, 76, 60, 0.5),
    inset 0 2px 4px rgba(255, 255, 255, 0.3),
    inset 0 -2px 4px rgba(0, 0, 0, 0.2);
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  overflow: hidden;
}

.heart-seal.seal-break {
  transform: translate(-50%, -50%) scale(0) rotate(180deg);
  opacity: 0;
}

.seal-heart {
  font-size: 32px;
  filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.2));
}

.seal-shine {
  position: absolute;
  top: -50%;
  left: -50%;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.4) 0%, transparent 50%);
  border-radius: 50%;
}

/* Open Me Container */
.open-me-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;
  transition: opacity 0.4s ease, transform 0.4s ease;
}

.open-me-container.hide {
  opacity: 0;
  transform: translateY(20px);
}

.open-me-badge {
  display: flex;
  align-items: center;
  gap: 12px;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.95) 0%, rgba(255, 245, 248, 0.95) 100%);
  padding: 16px 32px;
  border-radius: 50px;
  box-shadow:
    0 10px 40px rgba(196, 69, 105, 0.2),
    0 2px 10px rgba(196, 69, 105, 0.1);
  border: 2px solid rgba(255, 182, 193, 0.5);
}

.open-me-text {
  font-size: 2rem;
  color: #c44569;
  text-shadow: 0 2px 10px rgba(196, 69, 105, 0.2);
}

.sparkle-left,
.sparkle-right {
  font-size: 1.2rem;
  animation: sparkleRotate 2s ease-in-out infinite;
}

.sparkle-right {
  animation-delay: 0.5s;
}

@keyframes sparkleRotate {

  0%,
  100% {
    transform: rotate(0deg) scale(1);
  }

  50% {
    transform: rotate(15deg) scale(1.2);
  }
}

.tap-hint {
  display: flex;
  align-items: center;
  gap: 8px;
  color: #c44569;
  font-size: 0.95rem;
  opacity: 0.8;
  animation: tapBounce 1.5s ease-in-out infinite;
}

.hand-icon {
  font-size: 1.3rem;
}

@keyframes tapBounce {

  0%,
  100% {
    transform: translateY(0);
  }

  50% {
    transform: translateY(-5px);
  }
}

/* Mobile adjustments */
@media (max-width: 768px) {
  .envelope {
    width: 280px;
    height: 190px;
  }

  .heart-seal {
    width: 60px;
    height: 60px;
  }

  .seal-heart {
    font-size: 26px;
  }

  .letter-heart {
    font-size: 40px;
  }

  .letter-title {
    font-size: 1.8rem;
  }

  .open-me-text {
    font-size: 1.6rem;
  }

  .open-me-badge {
    padding: 12px 24px;
  }

  .letter.slide-out {
    transform: translateY(-130px) scale(1.05);
  }
}
</style>
