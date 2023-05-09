<template>
  <div class="card" @click="onClick" :class="{ [`card--theme-${theme}`]: theme }">

    <div class="card__top">
      <span class="card__label"></span>
      <span class="card__tag">
        <img :src ="tagIcon" class="card__tag-icon" v-if="tagIcon" />
        Вселенная
      </span>
    </div>
    <div class="card__logo">
      <img :src="logo" alt="">
    </div>
    <div class="card__container">
      <div class="card__content">
        <p class="card__title" v-html="title"></p>
        <slot name="content" />
      </div>
    </div>
    <div class="card__utils">
      <!-- тени и заплатки -->
      <span class="card__top-shadow"></span>
      <span class="card__label-shadow-top"></span>
      <span class="card__label-shadow-left"></span>
      <span class="card__label-shadow-right"></span>
      <span class="card__label-shadow-bottom"></span>
      <span class="card__container-shadow"></span>
      <span class="card__patch"><span></span></span>
    </div>
  </div>
</template>

<script setup>
import { gsap } from 'gsap'

defineProps({
  logo: {
    type: String
  },
  title: {
    type: String
  },
  theme: {
    type: String,
    default: 'blue',
    validator: prop => ['black', 'blue'].includes(prop)
  },
  tagIcon: {
    type: String
  }
})

const onClick = e => {
  const card = e.currentTarget
  const logo = card.querySelector('.card__logo')
  const content = card.querySelector('.card__content')
  const logoAnumDur = 0.5
  const tl = gsap.timeline()

  tl.to(logo, {left: 32, duration: logoAnumDur})
  tl.to(logo, {top: 20, duration: logoAnumDur}, 0)
  tl.to(logo, {xPercent: 0, duration: logoAnumDur}, 0)
  tl.to(logo, {yPercent: 0, duration: logoAnumDur}, 0)
  tl.to(logo, {width: 85, duration: logoAnumDur}, 0)
  tl.to(content, {opacity: 1, duration: 0.1}, 0.2)
}
</script>

<style lang="scss">
$tagWidth: 178px;
$tagHeight: 38px;
$tagSpaceX: 8px;
$tagSpaceY: 10px;
$labelHeight: $tagHeight + $tagSpaceY;

$borderRadius: 16px; // если меняется, нужно править положение для card__patch
$borderWidth: 2px; // есть ошибки в расчетах у одного из бордеров, видно при изменении значения бордера
$boxShadowLight: 0px 0px 7px #FFFFFF, 0px 0px 20px #00E0FF, 0px 0px 20px #00E0FF;
$boxShadowDark: 0px 0px 7px #FFFFFF, 0px 0px 20px #0085FF, 0px 0px 20px #0085FF;
$boxShadowLightInset: inset 0px 0px 7px #FFFFFF, inset 0px 0px 20px #00E0FF, inset 0px 0px 20px #00E0FF;
$boxShadowHeight: 20px; 
$transition: 0.2s ease-in;

.card {
  --bgCard: #6285FE;
  --contenTextColor: #000210;
  --contentHighlightTextColor: #fcfdfd;
  --titleTextColor: #000210;
  --borderColor: #cdd8ff;
  --tagColorText: #000210;
  
  &--theme-black {
    --bgCard: #000210;
    --titleTextColor: #fcfdfd;
    --contenTextColor: #fcfdfd;
    --contentHighlightTextColor: #6285FE;
    --borderColor: #6B6B6B;
    --tagColorText: #fdfdfd;
  }
}

.card {
  width: 640px;
  max-width: 100%;
  min-width: 280px;
  min-height: 285px;
  // height: 300px;
  display: flex;
  flex-direction: column;
  position: relative;
  cursor: pointer;

  &__tag-icon {
    width: 16px;
    height: 16px;
    flex-shrink: 0;
    margin-right: 10px;
  }

  &__title {
    font-weight: 500;
    font-size: 20px;
    line-height: 1.40;
    font-family: 'Unbounded', sans-serif;
    margin-bottom: 12px;
    color: var(--titleTextColor);
  }

  &__content {
    font-style: normal;
    font-weight: 400;
    font-size: 18px;
    line-height: 1.25;
    font-family: 'Graphik LCG', sans-serif;
    color: var(--contenTextColor);

    b {
      color: var(--contentHighlightTextColor);
      font-weight: 600;
    }
  }

  &__logo {
    position: absolute;
    z-index: 12;
    position: absolute;
    z-index: 12;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 190px;
    max-width: 90%;

    img {
      width: 100%;
      display: block;
    }
  }

  &__content {
    opacity: 0;
    transition: opacity $transition;
  }

  &__tag {
    height: $tagHeight;
    width: $tagWidth;
    border-radius: $borderRadius;
    background: var(--bgCard);
    right: 0;
    top: 0;
    position: absolute;
    border: $borderWidth solid var(--borderColor);
    transition: box-shadow $transition, border-color $transition;
    font-weight: 700;
    font-size: 12px;
    line-height: 1;
    font-family: 'Graphik LCG', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    color: var(--tagColorText);
  }

  &__top {
    height: $labelHeight + $boxShadowHeight;
    margin-bottom: -($boxShadowHeight + $borderWidth);
    position: relative;
    z-index: 5;
    flex-shrink: 0;

    &:after {
      content: '';
      position: absolute;
      width: calc(100% - ((100% - (#{$tagWidth} + #{$tagSpaceX}) + #{$borderRadius} + #{$borderWidth})));
      height: calc(#{$labelHeight}/2 - #{$borderWidth});
      bottom: calc(#{$boxShadowHeight});
      left: calc(100% - (#{$tagWidth} + #{$tagSpaceX} + #{$borderWidth}));
      border: $borderWidth solid var(--borderColor);
      transition: border-color $transition;
      border-bottom-left-radius: $borderRadius;
      border-top: none;
      border-right: none;
      z-index: 1;
      pointer-events: none;
    }

    &:before {
      content: '';
      position: absolute;
      width: calc(100% - ((100% - (#{$tagWidth} + #{$tagSpaceX}) + #{$borderRadius} + #{$borderWidth})));
      height: calc(#{$labelHeight}/2 - #{$borderWidth});
      bottom: 0;
      right: 0;
      border: $borderWidth solid var(--borderColor);
      transition: border-color $transition;
      border-top-right-radius: $borderRadius;
      border-bottom: none;
      border-left: none;
      z-index: 2;
      pointer-events: none;
    }
  }

  &__label {
    display: block;
    width: calc(100% - (#{$tagWidth} + #{$tagSpaceX}));
    height: $labelHeight;
    position: relative;
    border-left: $borderWidth solid var(--borderColor);
    transition: box-shadow $transition, border-color $transition;
    border-top-left-radius: $borderRadius;
    border-top-right-radius: $borderRadius;
    background: var(--bgCard);
    padding: 18px 32px 0;
    overflow: hidden;

    &:before {
      content: '';
      position: absolute;
      width: calc(100% + #{$borderWidth});
      height: calc(#{$labelHeight}/2 + #{$borderWidth});
      top: 0;
      left: -$borderWidth;
      border: $borderWidth solid var(--borderColor);
      transition: border-color $transition;
      border-top-left-radius: $borderRadius;
      border-top-right-radius: $borderRadius;
      border-bottom: none;
      z-index: 2;
      pointer-events: none;
    }
  }

  &__container {
    flex-grow: 1;
    border: $borderWidth solid var(--borderColor);
    background: var(--bgCard);
    border-top: none;
    border-bottom-left-radius: $borderRadius;
    border-bottom-right-radius: $borderRadius;
    border-top-right-radius: $borderRadius;
    position: relative;
    overflow: hidden;
    z-index: 3;
    transition: box-shadow $transition, border-color $transition;
    padding: 20px 32px 42px;
  }

  &__utils {
    pointer-events: none;
  }
}

// inset shadow
.card {
  &__container-shadow {
    position: absolute;
    top: $labelHeight;
    left: $borderWidth;
    width: calc(100% - #{$borderWidth}*2);
    height: calc(100% - #{$labelHeight});
    z-index: 10;
    overflow: hidden;
    border-bottom-left-radius: $borderRadius;
    border-bottom-right-radius: $borderRadius;
    border-top-right-radius: $borderRadius;
    pointer-events: none;

    &:before {
      content: '';
      position: absolute;
      width: 100%;
      height: 200%;
      bottom: 0;
      left: 0;
      box-shadow: $boxShadowLightInset;
      border-bottom-left-radius: $borderRadius;
      border-bottom-right-radius: $borderRadius;
      
      transition: opacity $transition;
      opacity: 0;
    }
  }

  &__label-shadow-top {
    display: block;
    width: calc(100% - (#{$tagWidth} + #{$tagSpaceX} + #{$borderWidth}*2));
    height: calc(#{$labelHeight}/2);
    position: absolute;
    top: calc(#{$borderWidth}/2);
    left: $borderWidth;
    z-index: 10;
    border-top-left-radius: $borderRadius;
    border-top-right-radius: $borderRadius;
    overflow: hidden;

    &:before {
      content: '';
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 200%;
      box-shadow: $boxShadowLightInset;

      transition: opacity $transition;
      opacity: 0;
    }
  }

  &__label-shadow-left {
    position: absolute;
    width: calc(100% - (#{$tagWidth} + #{$tagSpaceX} + #{$borderWidth}*2));
    height: calc(#{$labelHeight}/2 - #{$borderWidth}/2);
    display: block;
    top: calc(#{$borderWidth}/2 + #{$labelHeight}/2);
    left: $borderWidth;
    overflow: hidden;
    z-index: 10;

    &:before {
      content: '';
      height: 400%;
      width: 200%;
      position: absolute;
      top: -$boxShadowHeight;
      left: 0;
      box-shadow: $boxShadowLightInset;

      transition: opacity $transition;
      opacity: 0;
    }
  }

  &__label-shadow-right {
    position: absolute;
    width: calc((100% - (100% - #{$tagWidth}) + #{$tagSpaceX} + #{$borderWidth}) - #{$tagWidth}/2 + #{$boxShadowHeight});
    height: calc(#{$labelHeight}/2 + #{$boxShadowHeight});
    display: block;
    bottom: calc(100% - (#{$borderWidth}/2 + #{$labelHeight} + #{$boxShadowHeight}));
    right: $tagWidth + $tagSpaceX + $borderWidth*2 + $boxShadowHeight;
    transform: translateX(100%);
    border-bottom-left-radius: $borderRadius;
    overflow: hidden;
    z-index: 10;
    
    &:before {
      content: '';
      position: absolute;
      bottom: calc(#{$boxShadowHeight} + #{$borderWidth}*2 - #{$borderWidth}/2);
      left: calc(#{$boxShadowHeight} + #{$borderWidth});
      width: 200%;
      height: 200%;
      display: block;
      box-shadow: $boxShadowLight;
      border-bottom-left-radius: $borderRadius;

      transition: opacity $transition;
      opacity: 0;
    }
  }

  &__label-shadow-bottom {
    position: absolute;
    width: calc(#{$tagWidth}/2);
    height: calc(100% - #{$labelHeight} - #{$borderWidth}/2);
    display: block;
    top: calc(#{$labelHeight} - #{$borderWidth});
    right: $borderWidth;
    overflow: hidden;
    z-index: 10;
    border-bottom-right-radius: $borderRadius;
    
    &:before {
      content: '';
      position: absolute;
      top: 0;
      right: calc(#{-$borderWidth}/2);
      width: 200%;
      height: 200%;
      display: block;
      border-top-right-radius: $borderRadius;
      box-shadow: $boxShadowLightInset;

      transition: opacity $transition;
      opacity: 0;
    }
  }
}

// outer shadow
.card {
  &__label {

    &:after {
      content: '';
      display: block;
      position: absolute;
      top: 100%;
      left: 0;
      width: 100%;
      height: 40px;
      opacity: 0;
      transition: opacity $transition;
    }
  }
}

// костыли
.card {
  &__patch {
    &:before {
      content: "";
      width: 20px;
      height: 20px;
      display: block;
      position: absolute;
      left: calc(100% - 177px - 8px);
      transform: translate(-90%, -42%);
      top: 46px;
      background: var(--bgCard);
      pointer-events: none;
      z-index: 5;
      border-radius: 10px;
    }

    &:after {
      content: '';
      width: calc(100% - #{$tagWidth} - #{$tagSpaceX} - #{$borderWidth}*2);
      height: 20px;
      position: absolute;
      top: #{$labelHeight};
      left: $borderWidth;
      z-index: 6;
      background: var(--bgCard);
    }

    span {
      position: absolute;
      width: 30px;
      height: 30px;
      display: block;
      position: absolute;
      left: calc(100% - 177px - 8px);
      transform: translate(-31%, 8%) rotate(31deg);
      top: 46px;
      background: var(--bgCard);
      pointer-events: none;
      z-index: 5;
      filter: blur(1px);
    }
  }
}

// hover
.card {
  $parent: &;

  &:hover {
    --borderColor: #fcfdfd;

    #{$parent}__label-shadow-bottom:before,
    #{$parent}__label-shadow-right:before,
    #{$parent}__label-shadow-left:before,
    #{$parent}__label-shadow-top:before,
    #{$parent}__container-shadow:before,
    #{$parent}__label:after {
        opacity: 1;
    }

    #{$parent}__tag {
      box-shadow: $boxShadowDark, $boxShadowLightInset;
      backdrop-filter: blur(5.5px);
    }

    #{$parent}__container,
    #{$parent}__label {
      box-shadow: $boxShadowDark;
    }
  }
}
</style>
