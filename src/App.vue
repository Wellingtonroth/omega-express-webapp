<script setup>
import { ref } from 'vue'
import Header from './components/Header.vue';
import HeroSection from './components/HeroSection.vue';
import OmegaExpress from './components/OmegaExpress.vue';
import Counter from './components/Counter.vue';
import Services from './components/Services.vue';
import Feedback from './components/Feedback.vue';
import FAQ from './components/FAQ.vue';
import Footer from './components/Footer.vue';
</script>

<template>
  <div class="main">
    <Header />
    <HeroSection />
    <OmegaExpress />
    <!-- <Counter /> -->
    <Services />
    <Feedback />
    <FAQ />

    <div class="service-info">
      <div class="service-badge online">
        <span class="icon">🌐</span>
        <span>O Omega Express é 100% Online!</span>
      </div>
      <div class="service-badge presencial">
        <span class="icon">📍</span>
        <a href="https://omega.nutrivanessamattos.com/" target="_blank" rel="noopener noreferrer" class="service-link">
          Planos presenciais também disponíveis!
        </a>
      </div>
    </div>
    
    <Footer />
  </div>
</template>

<style scoped lang="scss">
.main {
  height: 100%;
  width: 100%;
  background-color: $color-background-white;

  .service-info {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 18px;
    margin-bottom: 40px;
    padding-bottom: 30px;
    flex-wrap: wrap;
    background-color: #fff;

    .service-badge {
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 8px 18px;
      border-radius: 24px;
      font-size: 1.1rem;
      font-weight: 600;
      background: #f4fff8;
      color: #223a5e;
  
      .icon {
        font-size: 1.3em;
      }
    }
  
    .online {
      background: $color-accent;
      color: $color-primary-dark;
    }
  
    .presencial {
      background: $color-background-white;
      color: $color-primary-dark;
      border: 1.5px solid $color-accent;

      .service-link {
        text-decoration: none;
        color: $color-primary-dark;
      }
    }
  }
}
</style>
