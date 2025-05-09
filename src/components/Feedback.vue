<template>
  <section ref="sectionRef" class="feedback-section fade-in">
    <div class="container">
      <h2 class="title">Histórias de Sucesso</h2>
      <div class="feedback-grid">
        <div
          class="feedback-card"
          v-for="(item, index) in visibleFeedbacks"
          :key="index"
        >
          <p class="feedback-text">"{{ item.text }}"</p>
          <p class="feedback-author">— {{ item.author }}</p>
        </div>
      </div>
      <div class="controls">
        <button @click="prevPage">←</button>
        <button @click="nextPage">→</button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue';

const feedbacks = ref([
  { text: 'A dieta é incrível, super prática e fácil de seguir! Já vejo resultados e me sinto mais confiante.', author: 'Mariana, 28 anos' },
  { text: 'Adorei o acompanhamento próximo, me senti acolhida em cada etapa do processo.', author: 'Fernanda, 35 anos' },
  { text: 'Finalmente encontrei um plano alimentar que respeita minha rotina e meus gostos!', author: 'Ana, 42 anos' },
  { text: 'O plano foi totalmente adaptado ao meu dia a dia, nunca consegui seguir uma dieta tão bem.', author: 'Paula, 31 anos' },
  { text: 'Recebo muito apoio e incentivo, estou amando!', author: 'Juliana, 26 anos' },
  { text: 'O app facilita demais acompanhar tudo e manter o foco.', author: 'Renata, 38 anos' },
  { text: 'Acompanhamento perfeito para quem não tem tempo para consultas presenciais.', author: 'Lívia, 29 anos' },
  { text: 'Me sinto muito mais saudável e com energia depois do acompanhamento.', author: 'Beatriz, 40 anos' },
  { text: 'As orientações sobre sono e rotina fizeram toda a diferença pra mim.', author: 'Camila, 33 anos' },
  { text: 'Senti minha autoestima melhorar muito, recomendo demais!', author: 'Patrícia, 45 anos' },
]);

const currentPage = ref(0);
const perPage = ref(3);
const sectionRef = ref(null);

const visibleFeedbacks = computed(() => {
  const start = currentPage.value * perPage.value;
  const end = start + perPage.value;
  
  if (end <= feedbacks.value.length) {
    return feedbacks.value.slice(start, end);
  } else {
    const firstPart = feedbacks.value.slice(start, feedbacks.value.length);
    const secondPart = feedbacks.value.slice(0, end - feedbacks.value.length);
    return firstPart.concat(secondPart);
  }
});

const prevPage = () => {
  const totalPages = Math.ceil(feedbacks.value.length / perPage.value);
  currentPage.value = (currentPage.value - 1 + totalPages) % totalPages;
};

const nextPage = () => {
  const totalPages = Math.ceil(feedbacks.value.length / perPage.value);
  currentPage.value = (currentPage.value + 1) % totalPages;
};

const updatePerPage = () => {
  const width = window.innerWidth;
  if (width < 640) {
    perPage.value = 1;
  } else if (width < 960) {
    perPage.value = 2;
  } else {
    perPage.value = 3;
  }
};

onMounted(() => {
  updatePerPage();
  window.addEventListener('resize', updatePerPage);

  if (sectionRef.value) {
    setTimeout(() => {
      sectionRef.value.classList.add('visible');
    }, 200);
  }
});
</script>


<style scoped lang="scss">
.feedback-section {
  padding: 60px 20px;
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.6s ease;

  &.visible {
    opacity: 1;
    transform: translateY(0);
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
    text-align: center;
  }

  .title {
    font-size: 2.5rem;
    color: $color-primary-dark;
    margin-bottom: 40px;
  }

  .feedback-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    justify-items: center;
  }

  .feedback-card {
    background: #fff;
    padding: 20px;
    border-radius: 12px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    color: $color-primary-dark;
    max-width: 300px;

    .feedback-text {
      font-style: italic;
      margin-bottom: 15px;
    }

    .feedback-author {
      font-weight: bold;
      color: $color-primary-soft;
    }
  }

  .controls {
    margin-top: 20px;

    button {
      border: 1px solid $color-primary-dark;
      color: $color-primary-dark;
      padding: 8px;
      margin: 0 5px;
      border-radius: 50px;
      cursor: pointer;
      transition: background-color 0.3s ease;

      &:hover {
        background-color: $color-primary-soft;
        border: 1px solid $color-background-white;
        color: $color-background-white;
      }
    }
  }
}
</style>
