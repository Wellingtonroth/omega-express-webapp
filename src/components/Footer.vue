<template>
  <footer class="footer">
    <div class="footer-content">
      <div class="footer-section">
        <h4>Nutricionista Vanessa Mattos</h4>
        <p>Endereço: Rua Araci Vaz Callado, 727 - Canto, Florianópolis - SC, 88070-750</p>
        <p class="contact">Contato: (48) 98484-7235</p>
      </div>
      <div class="footer-section">
        <a :href="whatsappUrl" target="_blank" class="social-icon">
          <img src="/assets/whatsapp.svg" alt="WhatsApp" />
        </a>
        <a href="https://www.instagram.com/nutrivanessamattos/" target="_blank" class="social-icon">
          <img src="/assets/instagram.svg" alt="Instagram" />
        </a>
      </div>
    </div>
    <div class="footer-copyright">
      <p>&copy; {{ currentYear }} Nutricionista Vanessa Mattos. Todos os direitos reservados.</p>
    </div>
  </footer>
</template>

<script setup>
import { computed } from 'vue';
import "@fortawesome/fontawesome-free/css/all.css";

const phoneNumber = import.meta.env.VITE_PHONE;
const message = 'Estou interessado(a) em saber mais sobre seus serviços.';
const whatsappUrl = computed(() => {
  return `https://wa.me/${phoneNumber}?text=${encodeURIComponent(message)}`;
});
const currentYear = new Date().getFullYear();
</script>

<style scoped lang="scss">
.footer {
  padding: 44px;
  text-align: center;
}

.footer-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: fit-content;
  margin: auto;
}

.footer-section {
  margin-bottom: 10px;

  h4 {
    margin-bottom: 10px;
    font-size: 24px;
  }

  p {
    margin: 0;
    text-align: left;
    margin-bottom: 10px;
  }
}

.social-icon {
  font-size: 30px;
  margin: 0 10px;
  transition: color 0.3s ease;
  padding: 8px;
  border-radius: 50%;
  color: #000;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.social-icon img {
  width: 30px;
  height: 30px;
  display: block;
}

.footer-copyright {
  margin-top: 20px;
  font-size: 14px;
}
</style>