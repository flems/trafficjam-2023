<template>
  <div class="number"
    :class="[
      {
        'number--active': active,
        'number--text': text,
        'number--highlighted-text': highlightedText,
      },
      `number--theme-${theme}`,
      `number--size-${size}`
    ]"
  >
    <span class="number__text">
      <slot />
    </span>
  </div>
</template>

<script setup>
defineProps({
  active: {
    type: Boolean,
    default: false
  },
  theme: {
    type: String,
    default: 'black',
    validator: prop => ['black', 'blue'].includes(prop)
  },
  size: {
    type: String,
    default: 'l',
    validator: prop => ['l', 'm'].includes(prop)
  },
  text: {
    type: Boolean,
    default: false
  },
  highlightedText: {
    type: Boolean,
    default: false
  }
})
</script>

<style lang="scss">
.number {
  $parent: &;
  width: max-content;
  position: relative;
  // padding: 16px;

  &--active {
    #{$parent}__text {
      &:after {
        background: rgba(0, 2, 16, 0.5);
        border: 2px solid #FFFFFF;
        backdrop-filter: blur(5.5px);
        box-shadow: 0px 0px 7px #FFFFFF,
                    0px 0px 20px #0085FF,
                    0px 0px 20px #0085FF,
                    inset 0px 0px 7px #FFFFFF,
                    inset 0px 0px 20px #00E0FF,
                    inset 0px 0px 20px #00E0FF;
      }
    }
  }

  &__text {
    color: #fff;
    font-weight: 500;
    line-height: 140%;
    font-family: 'Unbounded', sans-serif;
    display: block;
    position: relative;
    text-align: center;
    white-space: nowrap;
    position: relative;
    text-transform: uppercase;
    z-index: 2;

    &:after {
      content: '';
      width: 100%;
      height: 100%;
      position: absolute;
      top: 0px;
      // border-radius: 16px;
      left: 0px;
      transform: rotate(45deg);
      background: #2F2F2F;
      border: 2px solid rgba(255, 255, 255, 0.1);
      z-index: -1;
      transition: all 0.2s linear;
    }
  }

  &--size-m {
    padding: 12px;

    @media (max-width: 479px) {
      padding: 8px;
    }

    #{$parent}__text {
      width: 30px;
      height: 30px;
      font-size: 16px;
      line-height: 30px;
      
      &:after {
        border-radius: 4px;
      }
    }
  }

  &--size-l {
    padding: 16px;

    @media (max-width: 1279px) {
      padding: 12px;
    }

    @media (max-width: 479px) {
      padding: 8px;
    }

    #{$parent}__text {
      width: 70px;
      height: 70px;
      font-size: 24px;
      line-height: 70px;

      @media (max-width: 1279px) {
        width: 56px;
        height: 56px;
        line-height: 56px;
      }

      @media (max-width: 767px) {
        width: 40px;
        height: 40px;
        line-height: 40px;
        font-size: 18px;
      }

      @media (max-width: 479px) {
        width: 26px;
        height: 26px;
        line-height: 26px;
        font-size: 12px;
      }
      
      &:after {
        border-radius: 16px;

        @media (max-width: 767px) {
          border-radius: 12px;
        }

        @media (max-width: 479px) {
          border-radius: 4px;
        }
      }
    }

    &#{$parent}--text {
      #{$parent}__text {
        @media (max-width: 1279px) {
          font-size: 16px;
        }

        @media (max-width: 767px) {
          font-size: 12px;
        }

        @media (max-width: 479px) {
          font-size: 9px;
        }
      }
    }
  }

  &--theme-blue {
    &.number--active {
      #{$parent}__text {
        &:after {
          background: #6285FE;
        }
      }
    }
  }

  &--highlighted-text {
    &#{$parent}--active {
      #{$parent}__text {
        color: #6285FE;
        text-shadow: -2px 1px 0 white, -1px 1px 0 white, 1px -1px 0 white, -1px -1px 0 white, 0px 1px 0 white, 0px -1px 0 white, -1px 0px 0 white, 1px 0px 0 white, 2px 2px 0 white, -2px 2px 0 white, 2px -2px 0 white, -2px -2px 0 white, 0px 2px 0 white, 0px -2px 0 white, -2px 0px 0 white, 2px 0px 0 white, 1px 2px 0 white, -1px 2px 0 white, 1px -2px 0 white, -1px -2px 0 white, 2px 1px 0 white, -2px 1px 0 white, 2px -1px 0 white, -2px -1px 0 white, 0px 0px 7px #FFFFFF, 0px 0px 20px #0085FF, 0px 0px 20px #0085FF;
        font-weight: 400;  
      }
    }
  }
}
</style>