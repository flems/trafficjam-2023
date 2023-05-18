<template>
  <div class="main-page">
    <section class="main-page__section">
      <banner />
    </section>
    <section class="main-page__section" id="about">
      <mechanics />
    </section>
    <section class="main-page__section main-page__section--sponsors" id="sponsors">
      <sponsors />
      <div class="main-page__sponsors-bg"></div>
    </section>
    <section class="main-page__section" id="prizes">
      <prizes />
    </section>
    <section class="main-page__section">
      <main-rating />
    </section>

    <div class="main-page-stars main-page-stars--sponsors"></div>
    <div class="main-page-stars main-page-stars--prizes"></div>
    <div class="main-page-stars main-page-stars--rating"></div>
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

  &__sponsors-bg {
    position: absolute;
    width: 110%;
    top: -50%;
    left: 50%;
    transform: translateX(-50%);
    pointer-events: none;

    @media (max-width: 1440px) {
      width: 105%;
      top: -30%;
    }

    &:after {
      content: '';
      width: 100%;
      padding-top: 112%;
      position: absolute;
      background-image: url(/images/main-page/bg.svg);
      background-repeat: no-repeat;
      background-size: contain;
      background-position: 50% 50%;
      position: absolute;
      top: 0;
      left: 0;
    }
  }
}
.main-page-stars {
  width: 100%;
  position: absolute;
  max-width: 1880px;
  top: 0;
  // z-index: -1;

  &:after {
    content: '';
    display: block;
    top: 0;
    left: 0;
    width: 100%;
    padding-top: 50%;
    background-image: url('/images/main-page/stars-2.png');
    background-repeat: no-repeat;
    background-size: contain;
    background-position: 50% 50%;
    z-index: -1;
  }

  &--sponsors {
    top: 30%;
    left: 50%;
    transform: translateX(-100%);
  }

  &--prizes {
    top: 47%;
    left: 44%;
  }

  &--rating {
    top: 70%;
    left: 50%;
    transform: translateX(-100%);
  }
}
</style>
