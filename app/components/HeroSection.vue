<template>
  <section class="hero">
    <div class="hero-glow"></div>
    <div class="hero-content">
      <div class="heart-container">
        <div class="heart-icon">💖</div>
        <div class="heart-rings">
          <span class="ring ring-1"></span>
          <span class="ring ring-2"></span>
          <span class="ring ring-3"></span>
        </div>
      </div>
      <h1 class="hero-title script-font">
        <span class="title-line">Happy</span>
        <span class="title-line title-main">Valentine's Day</span>
      </h1>
      <p class="hero-subtitle">✨ Untuk seseorang yang sangat spesial di hatiku ✨</p>
      <div class="hero-message love-card">
        <div class="message-glow"></div>
        <p class="love-text">
          Setiap hari bersamamu terasa seperti Valentine. 
          Kau adalah alasan senyumku, kebahagiaan dalam hidupku, 
          dan cinta yang tak pernah pudar dalam hatiku.
        </p>
        <span class="signature script-font">~ With all my love 💕</span>
      </div>
      <button class="btn-valentine glow-btn" @click="scrollToMessage">
        💌 Baca Pesan Spesial
      </button>
    </div>
    
    <div class="decorative-elements">
      <span class="sparkle sparkle-1">✨</span>
      <span class="sparkle sparkle-2">⭐</span>
      <span class="sparkle sparkle-3">✨</span>
      <span class="sparkle sparkle-4">💫</span>
      <span class="sparkle sparkle-5">🌟</span>
    </div>
  </section>
</template>

<script setup>
const scrollToMessage = () => {
  const messageSection = document.getElementById('special-message')
  if (messageSection) {
    messageSection.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 40px 20px;
  position: relative;
  z-index: 1;
}

.hero-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 600px;
  height: 600px;
  background: radial-gradient(circle, rgba(255, 107, 157, 0.3) 0%, transparent 70%);
  filter: blur(60px);
  pointer-events: none;
}

.hero-content {
  text-align: center;
  max-width: 700px;
  animation: fadeInUp 1s ease-out;
  position: relative;
  z-index: 2;
}

.heart-container {
  position: relative;
  display: inline-block;
  margin-bottom: 20px;
}

.heart-icon {
  font-size: 80px;
  animation: heartBeat 2s infinite;
  position: relative;
  z-index: 2;
  filter: drop-shadow(0 0 30px rgba(255, 107, 157, 0.8));
}

.heart-rings {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 100%;
  height: 100%;
}

.ring {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border: 2px solid rgba(255, 107, 157, 0.5);
  border-radius: 50%;
  animation: ringPulse 3s ease-out infinite;
}

.ring-1 { width: 120px; height: 120px; animation-delay: 0s; }
.ring-2 { width: 160px; height: 160px; animation-delay: 0.5s; }
.ring-3 { width: 200px; height: 200px; animation-delay: 1s; }

@keyframes ringPulse {
  0% { transform: translate(-50%, -50%) scale(0.8); opacity: 0.8; }
  100% { transform: translate(-50%, -50%) scale(1.5); opacity: 0; }
}

.hero-title {
  font-size: clamp(2.5rem, 8vw, 4.5rem);
  margin-bottom: 16px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0;
}

.title-line {
  display: block;
  background: linear-gradient(135deg, #ff6b9d 0%, #c44569 50%, #e74c3c 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-shadow: 0 0 60px rgba(255, 107, 157, 0.5);
}

.title-main {
  font-size: 1.3em;
  background: linear-gradient(135deg, #ff6b9d 0%, #e91e63 30%, #c44569 60%, #ff6b9d 100%);
  background-size: 200% auto;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: shimmer 3s linear infinite;
}

@keyframes shimmer {
  0% { background-position: 0% center; }
  100% { background-position: 200% center; }
}

.hero-subtitle {
  font-size: 1.3rem;
  color: #666;
  margin-bottom: 40px;
  font-weight: 400;
}

.hero-message {
  margin-bottom: 40px;
  text-align: center;
  position: relative;
  overflow: hidden;
}

.message-glow {
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle at 30% 30%, rgba(255, 107, 157, 0.1) 0%, transparent 50%);
  pointer-events: none;
}

.love-text {
  font-size: 1.15rem;
  line-height: 1.8;
  color: #444;
  margin-bottom: 20px;
  position: relative;
  z-index: 1;
}

.signature {
  font-size: 1.5rem;
  color: #c44569;
}

.glow-btn {
  animation: glow 2s ease-in-out infinite alternate;
}

@keyframes glow {
  from {
    box-shadow: 0 10px 30px rgba(255, 107, 157, 0.4), 0 0 20px rgba(255, 107, 157, 0.2);
  }
  to {
    box-shadow: 0 10px 40px rgba(255, 107, 157, 0.6), 0 0 40px rgba(255, 107, 157, 0.4);
  }
}

.decorative-elements {
  position: absolute;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.sparkle {
  position: absolute;
  font-size: 24px;
  animation: sparkle 2s infinite;
}

.sparkle-1 { top: 15%; left: 10%; animation-delay: 0s; }
.sparkle-2 { top: 25%; right: 15%; animation-delay: 0.4s; }
.sparkle-3 { bottom: 25%; left: 15%; animation-delay: 0.8s; }
.sparkle-4 { top: 35%; left: 5%; animation-delay: 1.2s; }
.sparkle-5 { bottom: 35%; right: 8%; animation-delay: 1.6s; }

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes heartBeat {
  0% { transform: scale(1); }
  14% { transform: scale(1.3); }
  28% { transform: scale(1); }
  42% { transform: scale(1.3); }
  70% { transform: scale(1); }
}

@keyframes sparkle {
  0%, 100% { opacity: 0; transform: scale(0) rotate(0deg); }
  50% { opacity: 1; transform: scale(1) rotate(180deg); }
}

@media (max-width: 768px) {
  .hero {
    padding: 60px 16px;
  }
  
  .hero-glow {
    width: 300px;
    height: 300px;
  }
  
  .heart-icon {
    font-size: 60px;
  }
  
  .ring-1 { width: 90px; height: 90px; }
  .ring-2 { width: 120px; height: 120px; }
  .ring-3 { width: 150px; height: 150px; }
  
  .hero-subtitle {
    font-size: 1.1rem;
  }
  
  .love-text {
    font-size: 1rem;
  }
}
</style>
