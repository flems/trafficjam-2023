<template>
<div class="banner-title">
    <img class="banner-announce__title" src="/images/main-page/banner-block.svg" alt="">
    <svg class="svg">
    <clipPath id="my-clip-path" clipPathUnits="objectBoundingBox"><path d="M0.585,1 H0.059 C0.027,1,0.002,0.967,0.002,0.923 V0.125 C0.002,0.104,0.008,0.084,0.018,0.069 L0.049,0.026 C0.059,0.011,0.074,0.003,0.089,0.003 H0.945 C0.976,0.003,1,0.038,1,0.083 V0.346 C1,0.39,0.976,0.426,0.945,0.426 H0.819 C0.803,0.426,0.788,0.435,0.776,0.451 L0.712,0.542 C0.701,0.558,0.694,0.58,0.694,0.602 V0.849 C0.694,0.87,0.688,0.89,0.678,0.905 L0.625,0.979 C0.615,0.994,0.6,1,0.585,1"></path></clipPath>
    </svg>

    <div class="clipped"></div>
</div>
</template>

<script setup>
</script>

<style lang="scss" scoped>
.banner-title {
  position: relative;
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
}
</style>