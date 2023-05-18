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
  // const parallaxItems = [austronaut.value, ship.value, timerLine.value]

  // container.value.addEventListener('mousemove', e => {
  //   parallax(e, parallaxItems)
  // })
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
    width: 100%;
    height: auto;
    filter: blur(10px);
    transform: translateX(-50%);
    max-width: 1120px;
  }
  
  &__img {
    width: 100%;
    max-width: 1120px;
    display: block;
    position: relative;
    z-index: 2;
    animation: spin 660s linear infinite
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
    left: 50%;
    transform: translateX(-50%);

    @media (max-width: 1279px) {
      width: 112%;
    }

    @media (max-width: 999px) {
      top: 240px;
    }

    @media (max-width: 767px) {
      min-width: 768px;
      top: 180px;
    }

    @media (max-width: 479px) {
      top: 55%;
    }
  }

  &__austronaut {
    position: absolute;
    left: 40%;
    top: 206px;
    width: 34%;
    z-index: 12;

    @media (max-width: 1439px) {
      left: 35%;
    }

    @media (max-width: 1279px) {
      top: 136px;
    }

    @media (max-width: 999px) {
      top: 130px;
      width: 37%;
      left: 32%;
    }

    @media (max-width: 767px) {
      top: 64px;
      width: 63%;
      left: 50%;
      transform: translateX(-50%);
    }

    @media (max-width: 479px) {
      top: 40%;
      left: 0;
      transform: none;
    }
  }

  &__ship {
    max-width: 265px;
    position: absolute;
    right: 15%;
    top: 156px;
    width: 20%;
    z-index: 6;
    animation: ship 1s ease-out 0.1s;

    @media (max-width: 1440px) {
      right: 5%;
    }

    @media (max-width: 999px) {
      top: 106px;
    }

    @media (max-width: 767px) {
      width: 25%;
      top: 10%;
      right: 10px;
    }

    @media (max-width: 479px) {
      top: 80px;
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

    @media (max-width: 479px) {
      position: absolute;
      top: 81%;
      right: -225%;
      width: 640%;
      z-index: -1;
      transform: rotate(-41deg);
      filter: blur(34px);
    }

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

  @media (max-width: 1439px) {
    max-width: 406px;
  }

  @media (max-width: 1279px) {
    max-width: 340px;
  }

  @media (max-width: 999px) {
    max-width: 284px;
  }

  @media (max-width: 479px) {
    max-width: 100%;
    width: 100%;
  }

  &__men {
    padding-top: 100%;
    width: 100%;
    display: block;
    background-image: url('/images/main-page/austronaut.png');
    background-repeat: no-repeat;
    background-size: contain;
    background-position: 50% 50%;
    animation: levitate-animation 2s ease-in-out infinite alternate;
    transform-origin: center;
    transform: translate3d(0, 0, 0);

    @media (max-width: 479px) {
      margin-left: auto;
      padding: 0;
      margin-right: 20px;
      width: 64%;
      padding-top: 100%;
      background-position: 0 0;
      min-width: 230px;
    }
  }

  &__timer-line {
    max-width: 290px;
    position: absolute;
    top: 46%;
    left: 86%;
    width: 51%;
    
    @media (max-width: 1439px) {
      width: 70%;
    }
    
    @media (max-width: 1279px) {
      width: 60%;
      max-width: 245px;
    }
    
    @media (max-width: 999px) {
      max-width: 130px;
      width: 80%;
    }
    
    @media (max-width: 767px) {
      left: auto;
      right: 9.5%;
      width: 48%;
    }
    
    @media (max-width: 479px) {
      left: auto;
      right: 0;
      width: 100%;
      max-width: none;
      top: 26%;
    }

    &:before {
      content: '';
      padding-top: 90%;
      width: 100%;
      display: block;
      background-image: url('/images/main-page/timer-line.svg');
      background-repeat: no-repeat;
      background-size: contain;
      background-position: 50% 50%;

      @media (max-width: 999px) {
        padding-top: 130%;
        background-image: url('/images/main-page/timer-line-tablet.svg');
      }
      
      @media (max-width: 767px) {
        padding-top: 170%;
        background-image: url('/images/main-page/timer-line-480.svg');
      }

      @media (max-width: 479px) {
        width: 49%;
        padding-top: 59%;
        margin-left: auto;
        margin-right: 20px;
        background-image: url('/images/main-page/timer-line-360.svg');
      }
    }
  }

  &__timer {
    position: absolute;
    left: 92%;
    top: 100%;
    transform: translateX(-50%);

    @media (max-width: 767px) {
      left: 24px;
      top: 97%;
    }

    @media (max-width: 479px) {
      left: 0;
      top: 94%;
      transform: none;
      width: 100%;
    }
  }
}

@keyframes spin {
  to {
    -webkit-transform: rotate(1turn);
    transform: rotate(1turn)
  }
}

@keyframes ship {
  from {
    right: 33%;
  }
}

@media (max-width: 999px) {
  @keyframes ship {
    from {
      right: 33%;
      top: 216px;
    }
  }
}

@keyframes levitate-animation {
  0% {
    transform: translate3d(0, 0, 0);
  }
  100% {
    transform: translate3d(0px, -10px, 0);
  }
}
</style>