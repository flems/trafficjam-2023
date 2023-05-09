<template>
  <div class="ui-card"
    :class="{
      'ui-card--full-height' : fullHeight,
      'ui-card--interactive': interactive
    }"
  >
    <slot />
  </div>
</template>

<script setup>
defineProps({
  fullHeight: {
    type: Boolean,
    default: false
  },
  interactive: {
    type: Boolean,
    default: false
  }
})
</script>

<style lang="scss">
.ui-card {
  padding: 32px 40px;
  border-radius: 24px;
  border: 2px solid #6B6B6B;
  background: #000210;
  color: #FDFDFD;
  transition: all 0.2s ease-in;

  b {
    font-weight: 600;
    color: #6285FE;
    transition: color 0.2s ease-in;
  }

  &--interactive {
    cursor: pointer;

    &:hover {
      border-color: #CDD8FF;
      background: #6285FE;
      color: #000210;

      b {
        color: #FCFDFD;
      }
    }
  }

  &--full-height {
    height: 100%;
  }

}
</style>