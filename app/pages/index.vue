<template>
  <div class="valentine-page">
    <EnvelopeIntro v-if="!showContent" @opened="showContent = true" />
    
    <transition name="fade">
      <div v-if="showContent" class="main-content">
        <ParticleBackground />
        <FloatingHearts />
        <HeroSection />
        <CountdownTimer />
        <LoveQuotes />
        <LoveGallery />
        <MessageSection />
        <FooterSection />
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const showContent = ref(false)

useHead({
  title: 'Happy Valentine\'s Day 💖',
  meta: [
    { name: 'description', content: 'Pesan spesial Valentine untukmu dari seseorang yang mencintaimu' },
    { name: 'theme-color', content: '#ff6b9d' }
  ]
})
</script>

<style scoped>
.valentine-page {
  min-height: 100vh;
  position: relative;
}

.main-content {
  min-height: 100vh;
}

.fade-enter-active {
  transition: opacity 1s ease;
}

.fade-enter-from {
  opacity: 0;
}
</style>
