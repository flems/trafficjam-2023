<template>
<div class="banner-title">
  <div class="banner-title__wrapper">
    <img class="banner-title__title" src="/images/main-page/banner-block.svg" alt="">
    <svg class="svg">
      <clipPath id="my-clip-path" clipPathUnits="objectBoundingBox"><path d="M0.585,1 H0.059 C0.027,1,0.002,0.967,0.002,0.923 V0.125 C0.002,0.104,0.008,0.084,0.018,0.069 L0.049,0.026 C0.059,0.011,0.074,0.003,0.089,0.003 H0.945 C0.976,0.003,1,0.038,1,0.083 V0.346 C1,0.39,0.976,0.426,0.945,0.426 H0.819 C0.803,0.426,0.788,0.435,0.776,0.451 L0.712,0.542 C0.701,0.558,0.694,0.58,0.694,0.602 V0.849 C0.694,0.87,0.688,0.89,0.678,0.905 L0.625,0.979 C0.615,0.994,0.6,1,0.585,1"></path></clipPath>
    </svg>
    <div class="clipped"></div>
  </div>
  <div class="banner-title__wrapper banner-title__wrapper--mobile">
    <img class="banner-title__title" src="/images/main-page/banner-block-mobile.svg" alt="">
    <svg class="svg">
      <clipPath id="my-clip-path-mobile" clipPathUnits="objectBoundingBox"><path d="M0,0.21 V0.941 C0,0.973,0.011,1,0.025,1 H0.845 H0.899 C0.906,1,0.912,0.994,0.917,0.983 L0.993,0.803 C0.997,0.791,1,0.776,1,0.761 V0.059 C1,0.027,0.989,0,0.975,0 H0.088 C0.082,0,0.075,0.006,0.071,0.017 L0.007,0.168 C0.003,0.179,0,0.194,0,0.21"></path></clipPath>
    </svg>
    <div class="clipped"></div>
  </div>
    
</div>
</template>

<script setup>
</script>

<style lang="scss" scoped>
.banner-title {
  position: relative;

  &__title {
    width: 100%;
  }

  &__wrapper {
    @media (max-width: 479px) {
      display: none;
    }
    
    &--mobile {
      display: none;

      @media (max-width: 479px) {
        display: block;
      }
    }
  }
}
.svg {
  position: absolute;
  width: 0;
  height: 0;
}
.clipped {
  width: 0;
  height: 0;
  padding-top: 71%;
  padding-right: 100%;
  // background: red;
  backdrop-filter: blur(11px);
  background-size: cover;
  -webkit-clip-path: url(#my-clip-path);
  clip-path: url(#my-clip-path);
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;
  
  @media (max-width: 479px) {
    padding-top: 42%;
    -webkit-clip-path: url(#my-clip-path-mobile);
    clip-path: url(#my-clip-path-mobile);
  }
}
</style>