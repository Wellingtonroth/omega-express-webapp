<template>
  <section class="omega-express-section fade-in">
    <div class="container">
      <h2 class="title" id="omega-express">Ômega Express</h2>
      <div class="omega-boxes">
        <div class="omega-box">
          <img class="omega-icon" src="/assets/dieta.svg" alt="Dieta dos sonhos" />
          <div>
            <h3>A dieta dos sonhos</h3>
            <p>Você preenche um formulário detalhado para que eu conheça sua rotina e preferências. Assim, elaboro um plano alimentar totalmente individualizado, gostoso e prático — nada de dieta de gaveta!</p>
            <p>A cada 30 dias, avaliamos juntos seu progresso e ajustamos estratégias para garantir resultados contínuos.</p>
          </div>
        </div>
        <div class="omega-box">
          <img class="omega-icon" src="/assets/estrategia.svg" alt="Estratégias de aceleração de resultados" />
          <div>
            <h3>Estratégias de aceleração de resultados</h3>
            <p>Além da alimentação, você recebe orientações sobre sono, rotina e organização para acelerar seus resultados.</p>
            <p>Todo mês, acompanhamos sua evolução com fotos e medidas.</p>
          </div>
        </div>
        <div class="omega-box">
          <img class="omega-icon" src="/assets/aplicativo-movel.svg" alt="Aplicativo móvel" />
          <div>
            <h3>Contato próximo + aplicativo exclusivo</h3>
            <p>Suporte semanal pelo WhatsApp para dúvidas e conquistas. Use o app exclusivo para registrar refeições de forma prática e variada.</p>
            <p>Tudo 100% online, sem necessidade de vídeo ou deslocamento. Seu plano chega em até 3 dias úteis após o formulário.</p>
          </div>
        </div>
      </div>
      <p class="final-call">
        Vamos começar a construir a autoestima e o corpo que você sempre sonhou!
      </p>
    </div>
  </section>
</template>

<script setup>
import { onMounted } from 'vue';

onMounted(() => {
  const section = document.querySelector('.omega-express-section');
  setTimeout(() => {
    section.classList.add('visible');
  }, 200);
});
</script>

<style lang="scss" scoped>
.omega-express-section {
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
  }

  .title {
    font-size: 2.5rem;
    color: $color-primary-dark;
    text-align: center;
    margin-bottom: 30px;
  }

  .omega-boxes {
    display: flex;
    flex-direction: column;
    gap: 28px;
    margin-bottom: 32px;
  }

  .omega-box {
    background: #fff;
    border-radius: 14px;
    box-shadow: 0 2px 12px rgba(22, 33, 62, 0.2);
    padding: 28px 26px;
    border: 1px solid $color-primary-soft;
    border-left: 4px solid $color-primary-soft;
    transition: box-shadow 0.2s;
    display: flex;
    align-items: flex-start;

    h3 {
      color: $color-primary-dark;
      font-size: 1.22rem;
      margin-bottom: 10px;
      font-weight: 700;
      letter-spacing: 0.2px;
    }

    p {
      color: $color-primary-dark;
      font-size: 0.875rem;
      margin-bottom: 8px;
      line-height: 1.6;
      font-weight: 400;
    }
  }

  .final-call {
    font-weight: bold;
    color: $color-primary-dark;
    text-align: center;
    margin-top: 30px;
    font-size: 1.3rem;
  }

  @media (max-width: 700px) {
    .omega-boxes { gap: 16px; }
    .omega-box { padding: 18px 10px; }
  }
}

.omega-icon {
  width: 48px;
  height: 48px;
  margin-right: 18px;
  flex-shrink: 0;
  display: block;
}
</style>
