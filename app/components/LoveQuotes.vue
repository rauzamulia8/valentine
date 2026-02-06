<template>
  <section class="quotes-section">
    <div class="quotes-container">
      <div class="quote-card" :class="{ 'fade-in': isVisible }">
        <div class="quote-marks">"</div>
        <p class="quote-text">{{ currentQuote.text }}</p>
        <span class="quote-author">— {{ currentQuote.author }}</span>
      </div>
      
      <div class="quote-navigation">
        <button @click="prevQuote" class="nav-btn">
          <span>←</span>
        </button>
        <div class="quote-dots">
          <span v-for="(_, index) in quotes" :key="index" 
                class="dot" 
                :class="{ active: index === currentIndex }"
                @click="goToQuote(index)">
          </span>
        </div>
        <button @click="nextQuote" class="nav-btn">
          <span>→</span>
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

const quotes = [
  { text: "Aku memilihmu. Dan aku akan terus memilihmu. Setiap hari, tanpa jeda, tanpa ragu, aku memilihmu.", author: "Untukmu" },
  { text: "Dalam semesta yang luas ini, keajaiban terbesar adalah menemukan dirimu.", author: "Cintaku" },
  { text: "Bersama denganmu, bahkan hari biasa terasa luar biasa.", author: "Hati ini" },
  { text: "Kau bukan hanya cintaku, tapi juga rumah tempat hatiku pulang.", author: "Jiwaku" },
  { text: "Setiap detak jantungku mengeja namamu.", author: "Seluruh diriku" },
]

const currentIndex = ref(0)
const isVisible = ref(true)
let autoPlayInterval = null

const currentQuote = computed(() => quotes[currentIndex.value])

const changeQuote = (newIndex) => {
  isVisible.value = false
  setTimeout(() => {
    currentIndex.value = newIndex
    isVisible.value = true
  }, 300)
}

const nextQuote = () => {
  const newIndex = (currentIndex.value + 1) % quotes.length
  changeQuote(newIndex)
}

const prevQuote = () => {
  const newIndex = currentIndex.value === 0 ? quotes.length - 1 : currentIndex.value - 1
  changeQuote(newIndex)
}

const goToQuote = (index) => {
  if (index !== currentIndex.value) {
    changeQuote(index)
  }
}

onMounted(() => {
  autoPlayInterval = setInterval(nextQuote, 5000)
})

onUnmounted(() => {
  if (autoPlayInterval) clearInterval(autoPlayInterval)
})
</script>

<style scoped>
.quotes-section {
  padding: 80px 20px;
  position: relative;
  z-index: 1;
  background: linear-gradient(180deg, transparent 0%, rgba(255, 107, 157, 0.05) 50%, transparent 100%);
}

.quotes-container {
  max-width: 800px;
  margin: 0 auto;
}

.quote-card {
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.95) 0%, rgba(255, 245, 248, 0.95) 100%);
  backdrop-filter: blur(20px);
  border-radius: 32px;
  padding: 60px 50px;
  text-align: center;
  box-shadow: 0 25px 80px rgba(196, 69, 105, 0.2);
  border: 2px solid rgba(255, 192, 203, 0.6);
  position: relative;
  overflow: hidden;
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.quote-card.fade-in {
  opacity: 1;
  transform: translateY(0);
}

.quote-card:not(.fade-in) {
  opacity: 0;
  transform: translateY(20px);
}

.quote-marks {
  font-family: 'Dancing Script', cursive;
  font-size: 120px;
  color: rgba(255, 107, 157, 0.2);
  position: absolute;
  top: 10px;
  left: 30px;
  line-height: 1;
}

.quote-text {
  font-size: 1.5rem;
  line-height: 1.8;
  color: #444;
  font-style: italic;
  margin-bottom: 24px;
  position: relative;
  z-index: 1;
}

.quote-author {
  font-family: 'Dancing Script', cursive;
  font-size: 1.4rem;
  color: #c44569;
}

.quote-navigation {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 24px;
  margin-top: 32px;
}

.nav-btn {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  border: 2px solid #ff6b9d;
  background: white;
  color: #ff6b9d;
  font-size: 1.2rem;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
}

.nav-btn:hover {
  background: linear-gradient(135deg, #ff6b9d 0%, #c44569 100%);
  color: white;
  transform: scale(1.1);
  box-shadow: 0 8px 25px rgba(255, 107, 157, 0.4);
}

.quote-dots {
  display: flex;
  gap: 10px;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: rgba(255, 107, 157, 0.3);
  cursor: pointer;
  transition: all 0.3s ease;
}

.dot:hover {
  background: rgba(255, 107, 157, 0.6);
}

.dot.active {
  background: linear-gradient(135deg, #ff6b9d 0%, #c44569 100%);
  width: 32px;
  border-radius: 6px;
}

@media (max-width: 768px) {
  .quotes-section {
    padding: 60px 16px;
  }
  
  .quote-card {
    padding: 40px 24px;
    border-radius: 24px;
  }
  
  .quote-marks {
    font-size: 80px;
    top: 5px;
    left: 15px;
  }
  
  .quote-text {
    font-size: 1.2rem;
  }
  
  .nav-btn {
    width: 44px;
    height: 44px;
  }
}
</style>
