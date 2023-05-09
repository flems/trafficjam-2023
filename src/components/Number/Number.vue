<template>
  <div class="number"
    :class="[
      { 'number--active': active },
      `number--theme-${theme}`
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
  }
})
</script>

<style lang="scss">
.number {
  $parent: &;
  width: max-content;
  position: relative;
  padding: 16px;

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

  &--theme-blue {
    &.number--active {
      #{$parent}__text {
        &:after {
          background: #6285FE;
        }
      }
    }
  }

  &__text {
    color: #fff;
    font-weight: 500;
    font-size: 24px;
    line-height: 140%;
    font-family: 'Unbounded', sans-serif;
    display: block;
    width: 70px;
    height: 70px;
    position: relative;
    line-height: 70px;
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
      border-radius: 16px;
      left: 0px;
      transform: rotate(45deg);
      background: #2F2F2F;
      border: 2px solid rgba(255, 255, 255, 0.1);
      z-index: -1;
      transition: all 0.2s linear;
    }
  }
}
</style>