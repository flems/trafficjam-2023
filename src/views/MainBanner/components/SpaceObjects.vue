<template>
<div class="space-objects">
  <div class="space-objects__container">
    <div class="space-objects__austronaut austronaut">
      <div class="austronaut__timer-line">
        <div class="austronaut__timer">
          <timer />
        </div>
      </div>
    </div>
    <div class="space-objects__ship"></div>
  </div>
</div>
</template>

<script setup>
import Timer from './Timer.vue';
</script>

<style lang="scss" scoped>
.space-objects {
  position: absolute;

  &__container {
    max-width: 1920px;
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
  }

  &__austronaut {
    position: absolute;
    left: 36%;
    top: 206px;
    width: 30%;
  }

  &__ship {
    width: 265px;
    position: absolute;
    right: 5%;
    top: 156px;

    &:before {
      content: '';
      padding-top: 50%;
      width: 100%;
      display: block;
      background-image: url('/images/main-page/spaceship.png');
      background-repeat: no-repeat;
      background-size: contain;
      background-position: 50% 50%;
    }
  }
}

.austronaut {
  max-width: 480px;

  &:before {
    content: '';
    padding-top: 100%;
    width: 100%;
    display: block;
    background-image: url('/images/main-page/austronaut.png');
    background-repeat: no-repeat;
    background-size: contain;
    background-position: 50% 50%;
  }

  &__timer-line {
    width: 210px;
    position: absolute;
    top: 46%;
    left: 86%;

    &:before {
      content: '';
      padding-top: 90%;
      width: 100%;
      display: block;
      background-image: url('/images/main-page/timer-line.svg');
      background-repeat: no-repeat;
      background-size: contain;
      background-position: 50% 50%;
    }
  }

  &__timer {
    position: absolute;
    left: 92%;
    transform: translateX(-50%);
  }
}

</style>