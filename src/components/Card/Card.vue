<template>
  <div class="card">
    <div class="card__top">
      <span class="card__top-shadow"></span>
      <span class="card__label-shadow"></span>
      <span class="card__top-label">
        <slot name="label" />
      </span>
    </div>
    <span class="card__patch"></span>
    <div class="card__content">
      <slot name="content" />
    </div>
  </div>
</template>

<script setup>
</script>

<style lang="scss">
$borderRadius: 20px;
$labelWidth: 200px;
$labelHeight: 44px;
$borderWidth: 2px;
$borderColor: #FCFDFD;
$boxShadowLight: 0px 0px 7px #FFFFFF, 0px 0px 20px #00E0FF, 0px 0px 20px #00E0FF;
$boxShadowDark: 0px 0px 7px #FFFFFF, 0px 0px 20px #0085FF, 0px 0px 20px #0085FF;
$boxShadowLightInset: inset 0px 0px 7px #FFFFFF, inset 0px 0px 20px #00E0FF, inset 0px 0px 20px #00E0FF;
$boxShadowHeight: 20px; 
$cardBg: #6285FE;
$transition: 0.2s ease-in;

.card {
  width: 640px;
  height: 300px;
  margin: 50px;
  display: flex;
  flex-direction: column;
  position: relative;
  min-width: $labelWidth + $borderRadius * 2;
  cursor: pointer;

  // супер костыльная заплатка
  &__patch {
    &:before {
      content: '';
      width: $labelWidth;
      height: 20px;
      display: block;
      position: absolute;
      left: 2px;
      top: 29px;
      background: $cardBg;
      border-radius: 9px;
      pointer-events: none;
      z-index: 4;
    }
    &:after {
      content: '';
      width: 20px;
      height: 20px;
      display: block;
      position: absolute;
      left: 191px;
      top: 36px;
      background: $cardBg;
      border-radius: 50%;
      pointer-events: none;
      z-index: 4;
    }
  }
  // /супер костыльная заплатка

  &__top {
    height: $labelHeight + $boxShadowHeight;
    margin-bottom: -($boxShadowHeight + $borderWidth);
    position: relative;
    z-index: 5;

    &:after {
      content: '';
      position: absolute;
      width: calc((100% - #{$labelWidth} - #{$borderWidth}) - $boxShadowHeight);
      height: calc(#{$labelHeight}/2 - #{$borderWidth});
      bottom: calc(#{$boxShadowHeight} + #{$borderWidth}/2);
      left: $labelWidth - $borderWidth;
      border: $borderWidth solid $borderColor;
      border-bottom-left-radius: $borderRadius;
      border-top: none;
      border-right: none;
      z-index: 1;
      pointer-events: none;
    }

    &:before {
      content: '';
      position: absolute;
      width: calc((100% - #{$labelWidth} - #{$borderWidth})/2);
      height: calc(#{$labelHeight}/2 - #{$borderWidth});
      bottom: calc(#{$borderWidth}/2);
      left: calc((100% - #{$labelWidth} - #{$borderWidth})/2 + #{$labelWidth});
      border: $borderWidth solid $borderColor;
      border-top-right-radius: $borderRadius;
      border-bottom: none;
      border-left: none;
      z-index: 2;
      pointer-events: none;
    }
  }

  &__top-label {
    display: block;
    width: $labelWidth;
    height: $labelHeight + $boxShadowHeight;
    position: relative;
    border-left: $borderWidth solid $borderColor;
    border-top-left-radius: $borderRadius;
    border-top-right-radius: $borderRadius;
    background: $cardBg;
    padding: 18px 32px 0;
    overflow: hidden;

    &:before {
      content: '';
      position: absolute;
      width: calc(100% - #{$borderWidth});
      height: calc(#{$labelHeight}/2 - #{$borderWidth});
      top: 0;
      left: -$borderWidth;
      border: $borderWidth solid $borderColor;
      // background: green;
      border-top-left-radius: $borderRadius;
      border-top-right-radius: $borderRadius;
      border-bottom: none;
      z-index: 2;
      pointer-events: none;
      // border-left: none;
    }
  }

  &__content {
    flex-grow: 1;
    border: $borderWidth solid $borderColor;
    background: $cardBg;
    border-top: none;
    border-bottom-left-radius: $borderRadius;
    border-bottom-right-radius: $borderRadius;
    border-top-right-radius: $borderRadius;
    position: relative;
    overflow: hidden;
    z-index: 3;
    transition: box-shadow $transition;
    padding: 20px 32px;

    &:after {
      content: '';
      position: absolute;
      width: 100%;
      height: 200%;
      bottom: 0;
      left: 0;
      transition: box-shadow $transition;
    }
  }
}

// inset shadow
.card {
  $parent: &;

  &__top-shadow {
    position: absolute;
    bottom: 0;
    left: 0;
    width: calc(100% - #{$boxShadowHeight}/2);
    height: calc(100% - #{$boxShadowHeight}/2);
    overflow: hidden;
    pointer-events: none;
    
    &:after {
      opacity: 0;
      transition: opacity $transition;

      content: '';
      position: absolute;
      width: 200%;
      height: 200%;
      bottom: calc(#{$boxShadowHeight} + #{$borderWidth}/2);
      left: $labelWidth - $borderWidth;
      border-bottom-left-radius: $borderRadius;
      border-top: none;
      border-right: none;
      box-shadow: $boxShadowLight;
      z-index: 1;
    }
  }

  #{$parent}__top-label {
    &:after {
      content: '';
      position: absolute;
      top: $borderWidth;
      border-radius: $borderRadius - 4px;
      left: 0;
      width: 200%;
      height: 200%;
      box-shadow: $boxShadowLightInset;
      opacity: 0;
      transition: opacity $transition;
    }
  }
}

// box-shadow
.card {
  $parent: &;

  &:after {
    content: '';
    display: block;
    position: absolute;
    width: 50px;
    height: 100%;
    z-index: -1;
    background: red;
    border-top-left-radius: $borderRadius;
    border-bottom-left-radius: $borderRadius;
    box-shadow: $boxShadowDark;
    opacity: 0;
    transition: opacity $transition;
  }

  &__label-shadow {
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    position: absolute;
    z-index: -1;

    &:before {
      content: '';
      display: block;
      position: absolute;
      border-top-left-radius: $borderRadius;
      border-top-right-radius: $borderRadius;
      top: 0;
      left: 0;
      width: $labelWidth;
      height: 30px;
      background: red;
      box-shadow: $boxShadowDark;
      opacity: 0;
      transition: opacity $transition;
    }
  }
}

// hover
.card {
  $parent: &;

  &:hover {
    #{$parent}__top-shadow:after {
      opacity: 1;
    }

    &:after {
      opacity: 1;
    }

    #{$parent}__label-shadow:before {
      opacity: 1;
    }

    #{$parent}__content:after {
      box-shadow: $boxShadowLightInset;
    }

    #{$parent}__content {
      box-shadow: $boxShadowDark;
    }

    #{$parent}__top-label:after {
      opacity: 1;
    }
  }
}
</style>
