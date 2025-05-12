<template>
  <section class="counter-section">
    <div class="counters">
      <div class="counter-wrapper">
        <div class="counter-title">Planos Nutricionais</div>
        <span class="counter-value">+{{ counterPlans }}</span>
      </div>
      <div class="counter-wrapper">
        <div class="counter-title">Clientes Atendidos</div>
        <span class="counter-value">+{{ counterClients }}</span>
      </div>
      <div class="counter-wrapper">
        <div class="counter-title">Transformações</div>
        <span class="counter-value">+{{ counterTransformations }}</span>
      </div>
    </div>
    <CTAButton :text="'Comece a Consultoria Agora!'" />
  </section>
</template>

<script setup>
import { ref } from 'vue';
import CTAButton from '../shared/CTAButton.vue';

const counterPlans = ref(1000);
const counterClients = ref(1000);
const counterTransformations = ref(1000);
</script>

<style lang="scss" scoped>
.counter-section {
  border: 2px solid #47403d;
  padding: 20px;
  align-items: center;
  justify-content: center;
  display: flex;
  flex-direction: column;

  .counters {
    display: flex;
    gap: 20px;
    margin-bottom: 30px;

    .counter-wrapper {
      padding: 15px 15px 10px 15px;
      border-radius: 4px 4px 4px 4px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      border: 2px solid #47403d;
      width: 244px;


      .counter-title {
        font-size: 20px;
      }

      .counter-value {
        font-size: 32px;
        font-weight: 600;
      }
    }
  }
}

</style>
