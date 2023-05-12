<template>
  <div class="user-progress" v-if="data">
      <div class="user-progress__level">
        <number size="m" :active="!checkPercentage(1)">1</number>
        <span class="progress-bar">
          <span
            class="progress-bar__progress"
            :class="{ 'progress-bar__progress--0':  checkPercentage(1) }"
            :style="`width: ${getWidth(1)}`"
          ></span>
        </span>
      </div>
      <div class="user-progress__level">
        <number size="m" :active="!checkPercentage(2)">2</number>
        <span class="progress-bar">
          <span
            class="progress-bar__progress"
            :class="{ 'progress-bar__progress--0':  checkPercentage(2) }"
            :style="`width: ${getWidth(2)}`"
          ></span>
        </span>
      </div>
      <div class="user-progress__level">
        <number size="m" :active="!checkPercentage(3)">3</number>
        <span class="progress-bar">
          <span
            class="progress-bar__progress"
            :class="{ 'progress-bar__progress--0':  checkPercentage(3) }"
            :style="`width: ${getWidth(3)}`"
          ></span>
        </span>
      </div>
      <div class="user-progress__level">
        <number size="m" :active="!checkPercentage(4)">4</number>
        <span class="progress-bar">
          <span
            class="progress-bar__progress"
            :class="{ 'progress-bar__progress--0':  checkPercentage(4) }"
            :style="`width: ${getWidth(4)}`"
          ></span>
        </span>
      </div>
      <div class="user-progress__level user-progress__level--last">
        <number
          size="m"
          :active="+data.lvl === 4 && +data.percentage === 100"
        >top</number>
      </div>
  </div>
</template>

<script setup>
import Number from '@/components/Number'

const props = defineProps({
  data: Object
})

const checkPercentage = lvl => {
  return (lvl === props.data.lvl && +props.data.percentage === 0) || +props.data.lvl < lvl
}

const getWidth = lvl => {
  if (+props.data.lvl > lvl) return '100%'
  if (+props.data.lvl === lvl) return `${props.data.percentage}%`
  return 0
}
</script>

<style lang="scss">
.user-progress {
  display: flex;

  &__level {
    display: flex;
    align-items: center;
    flex-grow: 1;

    &--last {
      flex-grow: 0;
      flex-shrink: 0;

      .number__text {
        font-size: 10px;
      }
    }
  }
}

.progress-bar {
  background: #000210;
  
  height: 10px;
  width: 100%;
  border-radius: 16px;
  position: relative;
  
  &:before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border-radius: 16px;
    border: 2px solid rgba(252, 253, 253, 0.1);
  }

  &__progress {
    position: absolute;
    width: 0%;
    height: 100%;
    border-radius: 16px;
    border: 2px solid #FCFDFD;
    box-shadow: 0px 0px 7px #FFFFFF, 0px 0px 20px #0085FF, 0px 0px 20px #0085FF, inset 0px 0px 7px #FFFFFF, inset 0px 0px 20px #00E0FF, inset 0px 0px 20px #00E0FF;
    transition: width 0.2s ease-out, opacity 0.1s linear 0.1s;

    &--0 {
      opacity: 0;
    }
  }
}
</style>
