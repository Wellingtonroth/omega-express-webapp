<template>
  <section class="services-section">
    <h2 class="title">Escolha Seu Plano</h2>
    <p class="subtitle">
      Vamos construir a autoestima e o corpo que você sempre sonhou, com um acompanhamento próximo, prático e 
      totalmente individualizado!
    </p>
    <div class="plans">
      <div
        class="plan-card"
        :key="plan.name"
        :class="{ recommended: plan.recommended }"
        v-for="plan in plans"
      >
        <div v-if="plan.recommended" class="badge">
          Recomendado
        </div>
        <h3>{{ plan.name }}</h3>
        <ul>
          <li v-for="feature in plan.features" :key="feature">
            <span class="icon">✅</span> {{ feature }}
          </li>
        </ul>
        <div class="price-box">
          <div
            v-for="(option, idx) in plan.price"
            :key="option.label"
            class="price-option"
            :class="{ main: idx === 0 }"
          >
            <span class="icon" v-if="option.label.includes('PIX')">💵</span>
            <span class="icon" v-else>💳</span>
            <span class="amount">{{ option.amount }}</span>
            <span class="label">{{ option.label }}</span>
          </div>
        </div>
      </div>
    </div>
    <CTAButton :text="'Iniciar a Consultoria'" />
  </section>
</template>

<script setup>
import { ref } from 'vue';
import CTAButton from '../shared/CTAButton.vue';

const plans = ref([
  {
    name: 'Plano Bimestral',
    features: [
      '2 formulários, dietas e planos de ação.',
      '60 dias de suporte com a Nutri.',
      'Plantão de dúvidas semanal pelo WhatsApp.',
      'App exclusivo para registrar refeições.',
      'Envio em até 3 dias úteis após o formulário.',
      '100% Online'
    ],
    price: [
      {
        amount: '2x R$240',
        label: 'no crédito',
        or: 'ou',
      },
      {
        amount: 'R$450',
        label: 'no PIX',
      }
    ],
    recommended: false
  },
  {
    name: 'Plano Trimestral',
    features: [
      '3 formulários, 3 dietas, plano de ação e orientações.',
      '90 dias de suporte com a Nutri.',
      'Plantão de dúvidas semanal pelo WhatsApp.',
      'App exclusivo para registrar refeições.',
      'Envio em até 3 dias úteis após o formulário.',
      '100% Online'
    ],
    price: [
      {
        amount: '3x R$210',
        label: 'no crédito',
        or: 'ou',
      },
      {
        amount: 'R$600',
        label: 'no PIX',
      }
    ],
    recommended: true
  }
]);
</script>

<style scoped lang="scss">
.services-section {
  margin: 0 auto;
  padding: 40px 20px 40px 20px;
  text-align: center;
  background: #fff;
}

.title {
  font-size: 2.8rem;
  color: #16213e;
  margin-bottom: 10px;
  font-weight: 700;
}

.subtitle {
  font-size: 1.2rem;
  color: #3a4a5e;
  margin-bottom: 50px;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}

.plans {
  display: flex;
  flex-wrap: wrap;
  gap: 32px;
  justify-content: center;
  margin-bottom: 32px;
}

.plan-card {
  background: $color-background-white;
  border-radius: 18px;
  box-shadow: 0 2px 16px rgba(22, 33, 62, 15%);
  padding: 36px 28px 28px 28px;
  width: 340px;
  position: relative;
  text-align: left;
  transition: transform 0.2s, box-shadow 0.2s;
  border: 2px solid transparent;

  h3 {
    font-size: 2rem;
    color: #16213e;
    margin-bottom: 18px;
    font-weight: 600;
    text-align: center;
  }

  ul {
    list-style: none;
    padding: 0;
    margin-bottom: 22px;
    
    li {
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 1.08rem;
      margin-bottom: 8px;

      .icon {
        color: #4ecb71;
        font-size: 1.1em;
        margin-bottom: 8px;
      }
    }
  }

  .price-box {
    border-radius: 0 0 18px 18px;
    padding: 16px 10px 10px 10px;
    margin: 0 -28px -28px -28px;
    display: flex;
    flex-direction: column;
    align-items: center;
    font-size: 1.1rem;
    font-weight: 500;
    color: #7a8a2a;
    position: relative;

    .price-option {
      display: flex;
      align-items: center;
      gap: 6px;
      font-size: 1.2rem;
      font-weight: 700;
      margin-bottom: 2px;

      &.main {
        font-size: 1.4rem;
        color: #b5c44a;
        .amount {
          font-size: 1.5em;
          font-weight: 800;
        }
      }

      .icon {
        font-size: 1.3em;
        margin-bottom: 10px;
      }

      .amount {
        font-weight: 800;
      }

      .label {
        font-size: 1em;
        font-weight: 500;
        color: #7a8a2a;
      }
    }

    .divider {
      font-size: 1rem;
      color: #b5c44a;
      margin: 2px 0 0 0;
      font-weight: 600;
    }
  }
}

.plan-card.recommended {
  border: 2px solid #4ecb71;
  background: #f4fff8;
  box-shadow: 0 6px 32px rgba(78, 203, 113, 0.13);
  transform: scale(1.04);
  z-index: 1;

  .badge {
    position: absolute;
    top: -18px;
    right: 18px;
    background: #4ecb71;
    color: #fff;
    padding: 6px 18px;
    border-radius: 12px;
    font-size: 1rem;
    font-weight: bold;
    box-shadow: 0 2px 8px rgba(78, 203, 113, 0.12);
    letter-spacing: 0.5px;
  }
}

@media (max-width: 900px) {
  .plans {
    flex-direction: column-reverse;
    align-items: center;
    gap: 24px;
  }

  .plan-card {
    width: 100%;
    max-width: 400px;
  }
}

@media (max-width: 600px) {
  .service-info {
    flex-direction: column;
    gap: 10px;

    .service-badge {
      width: 100%;
      justify-content: center;
    }
  }
}
</style>
