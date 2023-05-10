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
    <section class="main-page__section">
      <prizes />
    </section>

    
  </div>
</template>

<script setup>
import Banner from "@/views/MainBanner/MainBanner.vue"
import Mechanics from "@/views/MainMechanics/MainMechanics.vue"
import Sponsors from "./components/Sponsors.vue"
import Prizes from "./components/Prizes.vue"
</script>

<style lang="scss" scoped>
.main-page {
  /* padding: 50px; */
  background-image: url('/images/main-page/stars.png');
  // height: 3600px;
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
    }
  }
}
</style>
