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
  { text: 'Com a ajuda dela, consegui voltar a me olhar no espelho com amor, fiz as pazes com a comida e estou caminhando para conquistar a minha melhor versão!', author: 'Camila, 26 anos' },
  { text: 'Já voltei a usar algumas blusas que eu adorava que não me serviam mais! Tô bem feliz, e melhor de tudo é que não tenho feito nenhum sacrifício enorme, tá sendo bem tranquilo seguir o plano.', author: 'Suzana, 34 anos' },
  { text: 'Não é uma dieta pronta que a gente logo esquece, é um amadurecimento em relação a alimentação, é aprender a deixar de lado crenças limitantes e atingir objetivos. Foi um investimento que vai se diluir ao longo da vida, então valeu demais a pena e meu único arrependimento é não ter começado o acompanhamento antes.', author: 'Bruna, 29 anos' },
  { text: 'Pela primeira vez na vida, depois de vários profissionais (médicos e nutricionistas, só faltou eu ir em benzedeira), meu intestino está funcionando como o intestino de uma pessoa normal. A Vanessa operou milagres!', author: 'Pricila, 44 anos' },
  { text: 'Tem sido uma ótima experiência, leve. Ela tem um olhar bem humano com seus pacientes, ela entende a pessoa, o que ajuda muito no processo.', author: 'Thais, 36 anos' },
  { text: 'A minha alimentação melhorou muito desde que comecei a fazer acompanhamento com ela e, como consequência, a alimentação da minha família também. O plano alimentar é personalizado (leva em consideração as nossas preferências alimentares) e o acompanhamento é contínuo, começa na consulta e segue de forma on-line.', author: 'Chaiani, 43 anos' },
  { text: 'A Vanessa é mais que uma nutri. É psicóloga, professora, investigadora, incentivadora, coach.... A melhor nutri para uma vida real, não idealizada. ', author: 'Jane, 42 anos' },
  { text: 'Indico para quem deseja realmente aprender a comer e não ficar refém de dietas milagrosas!', author: 'Naiara, 36 anos' },
  { text: 'A Vanessa é uma profissional exemplar, está me ajudando muito no processo de reeducação alimentar e emagrecimento, além da parte nutricional ela trabalha com uma parte comportamental que com certeza foi essencial para uma virada de chave na minha vida.', author: 'Gisieli, 27 anos' },
  { text: 'Já fui em outras nutricionistas mas não me motivei a continuar. Já com a Vanessa foi bem diferente, adaptou o plano conforme minha realidade e rotina, levando em conta todos os fatores que envolvem a alimentação muito além do plano alimentar.', author: 'Tuamy, 30 anos' },
  { text: 'Não existe dieta louca, ou hábitos malucos, nem perda de peso instantânea, e sim uma reeducação alimentar, pois essa é pro resto da vida! E sinto que é isso que vc sempre tenta transparecer e passar, essa essência da importância de fazer as pazes com a alimentação. Essa é sua marca registrada, com certeza!', author: 'Kety, 39 anos' },
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
