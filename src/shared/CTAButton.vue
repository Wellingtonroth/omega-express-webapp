<template>
  <button class="cta-button" @click="redirectToWhatsApp">
    {{ text }}
  </button>
</template>

<script setup>
defineProps({
  text: String,
});

const redirectToWhatsApp = () => {
  const phoneNumber = '48984847235';
  const message = 'Olá, quero mais informações sobre Ômega Express';
  const url = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(message)}`;
  window.open(url, '_blank');
};
</script>

<style scoped lang="scss">
.cta-button {
  background: $color-secondary-dark;
  color: $color-background-white;
  padding: 12px 24px;
  border: 1px solid $color-secondary-dark;
  border-radius: 30px;
  font-weight: 500;
  cursor: pointer;
  font-size: 1rem;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s;

  &:hover {
    transform: translateY(-2px);
  }
}
</style>