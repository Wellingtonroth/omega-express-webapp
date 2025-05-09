<template>
  <section class="counters">
    <div class="counter-wrapper">
      <div>Planos Nutricionais</div>
      <span>{{ counterPlans }}</span>
    </div>
    <div class="counter-wrapper">
      <div>Clientes Atendidos</div>
      <span>{{ counterClients }}</span>
    </div>
    <div class="counter-wrapper">
      <div>Transformações</div>
      <span>{{ counterTransformations }}</span>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const counterPlans = ref(1000);
const counterClients = ref(1000);
const counterTransformations = ref(1000);
</script>

<style lang="scss" scoped>
.counters {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 20px;
  background-color: #47403d;
  padding: 20px;
  color: #fff;

  .counter-wrapper {
    background-color: rgb(197 197 197 / 34%);
    padding: 15px 15px 10px 15px;
    border-radius: 4px 4px 4px 4px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
}
</style>
