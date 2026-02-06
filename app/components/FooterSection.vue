<template>
  <footer class="footer">
    <div class="footer-content">
      <p class="footer-text script-font">Made with 💖 just for you</p>
      <p class="footer-year">© {{ currentYear }}</p>
    </div>
  </footer>
</template>

<script setup>
const currentYear = new Date().getFullYear()
</script>

<style scoped>
.footer {
  padding: 40px 20px;
  text-align: center;
  position: relative;
  z-index: 1;
  background: linear-gradient(180deg, transparent 0%, rgba(255, 192, 203, 0.2) 100%);
}

.footer-content {
  max-width: 600px;
  margin: 0 auto;
}

.footer-text {
  font-size: 1.5rem;
  color: #c44569;
  margin-bottom: 8px;
}

.footer-year {
  color: #888;
  font-size: 0.9rem;
}
</style>
