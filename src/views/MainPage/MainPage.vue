<template>
  <div class="main-page">
    <section class="main-page__section">
      <banner />
    </section>
    <section class="main-page__section">
      <mechanics />
    </section>
    <section class="main-page__section">
      <sponsors />
    </section>
    <section class="main-page__section main-page__section--prizes">
      <prizes />
    </section>
    <section class="main-page__section main-page__section--rating">
      <main-rating />
    </section>
  </div>
</template>

<script setup>
import Banner from '@/views/MainBanner/MainBanner.vue'
import Mechanics from '@/views/MainMechanics/MainMechanics.vue'
import Sponsors from './components/Sponsors.vue'
import Prizes from './components/Prizes.vue'
import MainRating from '@/views/MainRating/MainRating.vue'
</script>

<style lang="scss" scoped>
.main-page {
  background-image: url('/images/main-page/stars.png');
  background-size: auto auto;
  background-position: 50% 0px;
  background-repeat: repeat no-repeat;
  position: relative;
  overflow: hidden;

  &__section {
    position: relative;
    z-index: 2;

    & + & {
      margin-top: 180px;

      @media (max-width: 1279px) {
        margin-top: 140px;
      }

      @media (max-width: 999px) {
        margin-top: 100px;
      }

      @media (max-width: 767px) {
        margin-top: 80px;
      }
    }
  }
}
</style>
