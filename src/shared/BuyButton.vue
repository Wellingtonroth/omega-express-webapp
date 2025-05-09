<template>
  <button class="button" @click="redirectToWhatsApp">
    {{ text }}
  </button>
</template>

<script setup>
defineProps({
  text: String,
});

const redirectToWhatsApp = () => {
  const phoneNumber = '48984847235';
  const message = 'Olá, gostaria de mais informações sobre o Método Ômega';
  const url = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(message)}`;
  window.open(url, '_blank');
};
</script>

<style scoped lang="scss">
.button {
  background: rgb(154, 132, 113);
  color: #fff;
  font-size: 20px;
  padding: 14px 30px;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: background 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
  text-align: center;
  margin-top: 20px;

  &:hover {
    background: rgb(154, 132, 113, 0.7);
    transform: scale(1.05);
    box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
  }
}
</style>
