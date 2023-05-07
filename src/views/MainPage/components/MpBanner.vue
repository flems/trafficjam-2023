<template>
  <div class="banner">
    <div class="banner-planet">
      <img src="/images/main-page/earth.png" alt="">
    </div>
    <div class="container">
      <div class="banner-announce banner__announce">
        <p class="banner-announce__date">
          <img src="/images/icons/calendar.svg" alt="">
          <span>Июнь-октябрь</span>
        </p>
        <banner-title />
        

        <p class="banner-announce__text">Лей на офферы Rafinad — забирай призы!</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import BannerTitle from './BannerTitle.vue';
</script>

<style lang="scss">


.banner {
  padding-top: 170px;

  &__announce {
    max-width: 410px;
    position: relative;
    z-index: 2;
  }
}

.banner-planet {
  position: absolute;
  z-index: 1;
  top: 256px;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: center;

  img {
    max-width: 100%;
    display: block;
  }

  &:before {
    content: '';
    display: block;
    position: absolute;
    top: 150px;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(180deg, #000210 0%, rgba(0, 2, 16, 0) 100%), linear-gradient(180deg, #000210 0%, rgba(0, 2, 16, 0) 100%), linear-gradient(180deg, #000210 0%, rgba(0, 2, 16, 0) 100%);
    transform: rotate(-180deg);
  }
}

.banner-announce {
  &__title {
    width: 100%;
  }

  &__date {
    color: #fdfdfd;
    font-size: 16px;
    margin-bottom: 10px;
    display: flex;
    align-items: center;

    img {
      margin-right: 12px;
      width: 24px;
      height: 24px;
    }
  }

  &__text {
    font-weight: 500;
    font-size: 24px;
    line-height: 1.40;
    text-transform: uppercase;
    color: #FCFDFD;
    margin-top: 24px;
  }
}


</style>