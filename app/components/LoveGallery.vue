<template>
  <section class="gallery-section">
    <h2 class="section-title script-font">💫 Momen Indah Kita 💫</h2>
    
    <div class="gallery-grid">
      <div v-for="(item, index) in memories" :key="index" 
           class="memory-card" 
           :style="{ animationDelay: `${index * 0.1}s` }">
        <div class="memory-icon">{{ item.icon }}</div>
        <div class="memory-content">
          <h3>{{ item.title }}</h3>
          <p>{{ item.description }}</p>
        </div>
        <div class="memory-glow"></div>
      </div>
    </div>
  </section>
</template>

<script setup>
const memories = [
  { icon: '☕', title: 'Kopi Pertama', description: 'Saat pertama kali kita ngobrol berjam-jam di cafe' },
  { icon: '🌅', title: 'Sunset Berdua', description: 'Menonton matahari terbenam dengan tangan bergandengan' },
  { icon: '🎬', title: 'Movie Night', description: 'Tertawa dan menangis bersama menonton film favorit' },
  { icon: '🌧️', title: 'Hujan-hujanan', description: 'Berlari bersama di bawah hujan yang tak terduga' },
  { icon: '🍕', title: 'Makan Malam', description: 'Berbagi slice pizza terakhir untukmu' },
  { icon: '🌙', title: 'Malam Berbintang', description: 'Menghitung bintang dan membuat harapan bersama' },
]
</script>

<style scoped>
.gallery-section {
  padding: 80px 20px;
  position: relative;
  z-index: 1;
}

.section-title {
  text-align: center;
  font-size: clamp(2rem, 5vw, 3rem);
  color: #c44569;
  margin-bottom: 60px;
}

.gallery-grid {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 24px;
}

.memory-card {
  position: relative;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.9) 0%, rgba(255, 245, 248, 0.9) 100%);
  backdrop-filter: blur(10px);
  border-radius: 24px;
  padding: 32px;
  display: flex;
  align-items: center;
  gap: 20px;
  border: 2px solid rgba(255, 192, 203, 0.5);
  box-shadow: 0 10px 40px rgba(196, 69, 105, 0.1);
  overflow: hidden;
  animation: fadeInUp 0.8s ease-out both;
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

.memory-card:hover {
  transform: translateY(-8px) scale(1.02);
  box-shadow: 0 20px 60px rgba(196, 69, 105, 0.25);
  border-color: #ff6b9d;
}

.memory-card:hover .memory-glow {
  opacity: 1;
}

.memory-glow {
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle, rgba(255, 107, 157, 0.15) 0%, transparent 70%);
  opacity: 0;
  transition: opacity 0.4s;
  pointer-events: none;
}

.memory-icon {
  font-size: 48px;
  min-width: 80px;
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #ff6b9d 0%, #c44569 100%);
  border-radius: 20px;
  box-shadow: 0 8px 25px rgba(255, 107, 157, 0.35);
}

.memory-content h3 {
  font-size: 1.3rem;
  color: #c44569;
  margin-bottom: 8px;
}

.memory-content p {
  color: #666;
  line-height: 1.6;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(40px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 768px) {
  .gallery-section {
    padding: 60px 16px;
  }
  
  .gallery-grid {
    grid-template-columns: 1fr;
  }
  
  .memory-card {
    padding: 24px;
  }
  
  .memory-icon {
    font-size: 36px;
    min-width: 64px;
    height: 64px;
  }
}
</style>
