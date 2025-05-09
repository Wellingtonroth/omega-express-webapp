<script setup>
import { ref } from 'vue'
import Header from './components/Header.vue';
import HeroSection from './components/HeroSection.vue';
import OmegaExpress from './components/OmegaExpress.vue';
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
    <Services />
    <Feedback />
    <FAQ />
    <Footer />
  </div>
</template>

<style scoped lang="scss">
.main {
  height: 100%;
  width: 100%;
  background-color: $color-background-white;
}
</style>
