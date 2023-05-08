<template>
<div class="space-objects" ref="container">
  <div class="space-objects__container">
    <div class="banner-planet space-objects__planet">
      <img class="banner-planet__blur" src="/images/main-page/earth.png" alt="">
      <img class="banner-planet__img" src="/images/main-page/earth.png" alt="">
    </div>

    <div class="space-objects__austronaut austronaut">
      <div class="austronaut__men" ref="austronaut" data-parallax-value="-2"></div>
      <div class="austronaut__timer-line" data-parallax-value="1">
        <div class="austronaut__timer">
          <timer />
        </div>
      </div>
    </div>
    <div class="space-objects__ship ship" ref="ship" data-parallax-value="1">
      <div class="ship__trail"></div>
    </div>
    <div class="space-objects__trail"></div>
  </div>
</div>
</template>

<script setup>
import Timer from './Timer.vue'
import { onMounted, ref } from 'vue'

const austronaut = ref(null)
const ship = ref(null)
const container = ref(null)
const timerLine = ref(null)
const parallax = (event, items) => {
  items.forEach((item) => {
    if (!item) return
    const position = item.dataset.parallaxValue || 2
    const x = (window.innerWidth - event.pageX * position) / 300;
    const y = (window.innerHeight - event.pageY * position) / 300;

    item.style.transform = `translate3d(${x}px, ${y}px, 0px)`
  });
}

const init = () => {
  const parallaxItems = [austronaut.value, ship.value, timerLine.value]

  container.value.addEventListener('mousemove', e => {
    parallax(e, parallaxItems)
  })
}

onMounted(() => {
  init()
})
</script>

<style lang="scss" scoped>
.banner-planet {
  width: 100%;
  display: flex;
  justify-content: center;
  pointer-events: none;

  &__blur {
    position: absolute;
    top: 0;
    left: 50%;
    width: 90%;
    height: auto;
    filter: blur(10px);
    transform: translateX(-50%);
    max-width: 1120px;
  }
  
  &__img {
    width: 90%;
    max-width: 1120px;
    display: block;
    position: relative;
    z-index: 2;
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
    z-index: 3;
  }
}

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

  &__planet {
    z-index: 9;
    position: absolute;
    top: 256px;
    left: 0;
  }

  &__austronaut {
    position: absolute;
    left: 36%;
    top: 206px;
    width: 34%;
    z-index: 12;
  }

  &__ship {
    max-width: 265px;
    position: absolute;
    right: 15%;
    top: 156px;
    width: 20%;
    z-index: 6;

    @media (max-width: 1440px) {
      right: 5%;
    }
  }

  &__trail {
    position: absolute;
    z-index: 3;
    overflow: hidden;
    top: 60%;
    width: 50%;
    left: 0%;
    
    @media (max-width: 1440px) {
      width: 50%;
    }
    
    &:after {
      content: '';
      width: 100%;
      transform: translateX(-10%);
      padding-top: 63%;
      display: block;
      background-image: url('/images/main-page/ship-trail-2.svg');
      background-repeat: no-repeat;
      background-size: contain;
      background-position: 50% 50%;
    }
  }
}

.ship {
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

  &__trail {
    position: absolute;
    top: 0;
    right: 0;
    width: 250%;
    z-index: -1;

    &:after {
      content: '';
      width: 100%;
      padding-top: 50%;
      display: block;
      background-image: url(/images/main-page/ship-trail.svg);
      background-repeat: no-repeat;
      background-size: contain;
      background-position: 50% 50%;
    }
  }
}

.austronaut {
  max-width: 480px;

  &__men {
    padding-top: 100%;
    width: 100%;
    display: block;
    background-image: url('/images/main-page/austronaut.png');
    background-repeat: no-repeat;
    background-size: contain;
    background-position: 50% 50%;
  }

  &__timer-line {
    max-width: 290px;
    position: absolute;
    top: 46%;
    left: 86%;
    width: 51%;

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