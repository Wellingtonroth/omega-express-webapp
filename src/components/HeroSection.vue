<template>
  <section class="hero-section">
    <div class="background-image"></div>

    <div class="hero-content">
      <span class="crn">CRN10 - 7189</span>
      <h1 class="nutritionist-name">Nutricionista<br />
        <strong>Vanessa Mattos</strong>
      </h1>
      <p class="description">Emagrecimento, Performance e Qualidade de Vida</p>
      <CTAButton :text="'Comece a Consultoria Agora!'" />
    </div>
  </section>
</template>

<script setup>
import CTAButton from '../shared/CTAButton.vue';
</script>

<style lang="scss" scoped>
.hero-section {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 38px;
  background-color: $color-background-white;
  overflow: hidden;
  text-align: center;
  min-height: 600px;

  .background-image {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: url('../assets/vanessa-mattos-omega.jpg');
    background-size: cover;
    background-position: center;
    opacity: 0.3; 
    z-index: 1;
  }

  .hero-content {
    z-index: 2;
    position: relative;

    .crn {
      font-size: 14px;
      color: $color-primary-dark;
    }

    .nutritionist-name {
      font-size: 40px;
      margin-bottom: 16px;
      margin-top: 22px;
      color: $color-primary-dark;
    }

    .description {
      font-size: 18px;
      margin-bottom: 20px;
      color: $color-primary-dark;
      font-weight: 500;
    }
  }
}
</style>
