<template>
  <section class="faq-section">
    <div class="container">
      <h2 class="title" id="faq">Perguntas Frequentes</h2>

      <div class="faq-item" v-for="(item, index) in faqs" :key="index">
        <div class="faq-question" @click="toggle(index)">
          <span>{{ item.question }}</span>
          <span>{{ activeIndex === index ? '-' : '+' }}</span>
        </div>
        <transition>
          <div
            class="faq-answer"
            v-show="activeIndex === index"
            ref="answers"
          >
            <p>{{ item.answer }}</p>
          </div>
        </transition>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const faqs = ref([
  {
    question: 'Preciso fazer chamada de vídeo para a consulta?',
    answer: 'Não, a consultoria é para quem preza por praticidade! Todo o acompanhamento é feito através de formulários, mensagens no WhatsApp e pelo aplicativo.',
  },
  {
    question: 'Em quanto tempo recebo meu plano?',
    answer: 'Seu plano alimentar, estratégias e metas serão enviados em até 3 dias úteis após o envio do formulário.',
  },
  {
    question: 'Posso tirar dúvidas durante o acompanhamento?',
    answer: 'Sim! Temos um plantão de dúvidas semanal pelo WhatsApp, toda quinta-feira.',
  },
  {
    question: 'Como funciona o aplicativo?',
    answer: 'Durante o acompanhamento você terá acesso ao aplicativo, onde terá na palma da sua mão, acesso ao plano alimentar, receitas, orientações. E também poderá registrar suas refeições no diário alimentar, recebendo o feedback da nutri!',
  },
]);

const activeIndex = ref(null);

const toggle = (index) => {
  console.log(index);
  activeIndex.value = activeIndex.value === index ? null : index;
}
</script>

<style lang="scss" scoped>
.faq-section {
  padding: 60px 20px;
  background: #fff;

  .container {
    max-width: 900px;
    margin: 0 auto;
  }

  .title {
    font-size: 2.5rem;
    color: $color-primary-dark;
    text-align: center;
    margin-bottom: 30px;
  }

  .faq-item {
    background-color: $color-background-white;
    border: 1px solid $color-primary-soft;
    border-radius: 8px;
    margin-bottom: 15px;
    overflow: hidden;
    transition: all 1s linear;

    .faq-question {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 15px 20px;
      cursor: pointer;
      font-weight: bold;
      color: $color-primary-dark;
      background: #fff;

      &:hover {
        background-color: $color-primary-soft;
        color: $color-background-white;
      }
    }

    .faq-answer {
      padding: 15px 20px;
      background-color: $color-background-light;
      color: $color-primary-dark;
      font-size: 1rem;
      line-height: 1.5;
      overflow: hidden;
    }
  }
}
</style>
