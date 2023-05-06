<template>
  <div class="card">
    <div class="card-hover">
      <span class="card-hover__item"></span>
      <!-- <span class="card-hover__item"></span>
      <span class="card-hover__item"></span> -->
    </div>
    <div class="card__content">
      123123132
    </div>
  </div>
</template>

<script setup>
</script>

<style lang="scss">
.card-hover {
  position: absolute;
  width: 100%;
  height: 100%;
  background: white;
  clip-path: path('M0 320V24C0 10.7452 10.7452 0 24 0H189C201.15 0 211 9.84974 211 22V22C211 34.1503 220.85 44 233 44H376C389.255 44 400 54.7452 400 68V320C400 333.255 389.255 344 376 344H24C10.7452 344 0 333.255 0 320Z');
  filter: blur(5px);
}
.card {
  // temp
  width: 400px;
  height: 350px;
  margin: 50px;
  position: relative;
  // outline: 1px solid #fff;

  // /temp

  &__content {
    position: absolute;
    top: 6px;
    left: 6px;
    height: calc(100% - 12px);
    width: calc(100% - 12px);
    padding-top: calc(44px + 20px);
    padding-left: 32px;
    padding-right: 32px;
    background: #6285FE;
    clip-path: path('M0 320V24C0 10.7452 10.7452 0 24 0H189C201.15 0 211 9.84974 211 22V22C211 34.1503 220.85 44 233 44H376C389.255 44 400 54.7452 400 68V320C400 333.255 389.255 344 376 344H24C10.7452 344 0 333.255 0 320Z');
  }

  // &:before {
  //   content: '';
  //   position: absolute;
  //   top: 0;
  //   left: 0;
  //   width: 100%;
  //   height: 100%;
  //   background: red;
  //   clip-path: path('M0 320V24C0 10.7452 10.7452 0 24 0H189C201.15 0 211 9.84974 211 22V22C211 34.1503 220.85 44 233 44H376C389.255 44 400 54.7452 400 68V320C400 333.255 389.255 344 376 344H24C10.7452 344 0 333.255 0 320Z');
  //   width: 100%;
  //   height: 100%;
  // }
}
</style>
