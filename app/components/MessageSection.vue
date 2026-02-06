<template>
  <section id="special-message" class="message-section">
    <div class="message-container">
      <h2 class="section-title script-font">💕 Pesan Spesial Untukmu 💕</h2>
      
      <div class="message-cards">
        <div class="message-card love-card">
          <div class="card-icon">💐</div>
          <h3>Kau Segalanya</h3>
          <p>Seperti bunga yang mekar di musim semi, kehadiranmu mewarnai hidupku dengan keindahan yang tak terlukiskan.</p>
        </div>
        
        <div class="message-card love-card">
          <div class="card-icon">💎</div>
          <h3>Berharga</h3>
          <p>Lebih berharga dari berlian, lebih indah dari semua keajaiban dunia - itulah dirimu di mataku.</p>
        </div>
        
        <div class="message-card love-card">
          <div class="card-icon">🌟</div>
          <h3>Bintangku</h3>
          <p>Dalam gelap malam, kau adalah bintang yang menerangi jalanku. Selalu bersinar, selalu menuntun.</p>
        </div>
      </div>
      
      <div class="promise-box love-card">
        <h3 class="script-font">Janjiku Untukmu</h3>
        <ul class="promise-list">
          <li>💝 Selalu ada di sisimu dalam suka dan duka</li>
          <li>💝 Mencintaimu setiap hari, tanpa syarat</li>
          <li>💝 Menjaga senyummu tetap mekar</li>
          <li>💝 Membuatmu bahagia selamanya</li>
        </ul>
      </div>
    </div>
  </section>
</template>

<style scoped>
.message-section {
  padding: 80px 20px;
  position: relative;
  z-index: 1;
}

.message-container {
  max-width: 1200px;
  margin: 0 auto;
}

.section-title {
  text-align: center;
  font-size: clamp(2rem, 5vw, 3rem);
  color: #c44569;
  margin-bottom: 60px;
}

.message-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
  margin-bottom: 60px;
}

.message-card {
  text-align: center;
  animation: fadeInUp 0.8s ease-out;
}

.message-card:nth-child(1) { animation-delay: 0.1s; }
.message-card:nth-child(2) { animation-delay: 0.2s; }
.message-card:nth-child(3) { animation-delay: 0.3s; }

.card-icon {
  font-size: 50px;
  margin-bottom: 20px;
}

.message-card h3 {
  font-size: 1.5rem;
  color: #c44569;
  margin-bottom: 16px;
}

.message-card p {
  color: #555;
  line-height: 1.7;
}

.promise-box {
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
  background: linear-gradient(135deg, rgba(255, 107, 157, 0.1) 0%, rgba(196, 69, 105, 0.1) 100%);
}

.promise-box h3 {
  font-size: 2rem;
  color: #c44569;
  margin-bottom: 24px;
}

.promise-list {
  list-style: none;
  text-align: left;
}

.promise-list li {
  padding: 12px 0;
  font-size: 1.1rem;
  color: #444;
  border-bottom: 1px dashed rgba(196, 69, 105, 0.3);
}

.promise-list li:last-child {
  border-bottom: none;
}

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

@media (max-width: 768px) {
  .message-section {
    padding: 60px 16px;
  }
  
  .section-title {
    margin-bottom: 40px;
  }
  
  .message-cards {
    gap: 20px;
    margin-bottom: 40px;
  }
  
  .card-icon {
    font-size: 40px;
  }
}
</style>
