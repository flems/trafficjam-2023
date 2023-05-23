<template>
<div class="prizes">
  <ui-card class="prizes__desktop">
    <div class="prizes__container">
      <step
        class="prizes__step"
        name="1"
        icon="rocket"
        score="40&nbsp;000"
        :progress="progress.first"
        key="first"
      />
      <step
        class="prizes__step"
        name="2"
        icon="box"
        active-icon="box-opened"
        score="200&nbsp;000"
        :progress="progress.second"
        key="second"
      />
      <step
        class="prizes__step"
        name="3"
        icon="box"
        active-icon="box-opened"
        score="600&nbsp;000"
        :progress="progress.third"
        key="third"
      />
      <step
        class="prizes__step"
        name="4"
        theme="blue"
        icon="box"
        active-icon="box-opened"
        score="1&nbsp;200&nbsp;000"
        :progress="progress.fourth"
        key="fourth"
      />
      <step
        class="prizes__step prizes__step--last"
        last
        name="top"
        icon="box"
        active-icon="box-opened"
        theme="blue"
        :progress="progress.fifth"
        key="fifth"
        text
      />
    </div>
  </ui-card>
  <ui-card class="prizes__tablet">
    <div class="prizes__container">
      <step
        class="prizes__step"
        name="1"
        icon="rocket"
        score="40&nbsp;000"
        :progress="progress.first"
        key="first"
      />
      <step
        class="prizes__step"
        name="2"
        icon="box"
        active-icon="box-opened"
        score="200&nbsp;000"
        :progress="progress.second"
        key="second"
      />
      
      <step
        class="prizes__step prizes__step--last"
        last
        name="3"
        icon="box"
        active-icon="box-opened"
        theme="black"
        :progress="progress.third"
        key="third"
      />
    </div>
  </ui-card>
  <ui-card class="prizes__tablet">
    <div class="prizes__container">
      <step
        class="prizes__step"
        name="3"
        theme="black"
        icon="box"
        active-icon="box-opened"
        score="600&nbsp;000"
        :progress="progress.third"
        key="third"
      />
      <step
        class="prizes__step"
        name="4"
        icon="box"
        theme="blue"
        active-icon="box-opened"
        score="1&nbsp;200&nbsp;000"
        :progress="progress.fourth"
        key="fourth"
      />
      <step
        class="prizes__step prizes__step--last"
        last
        name="top"
        icon="box"
        active-icon="box-opened"
        theme="blue"
        :progress="progress.fifth"
        key="fifth"
        text
        highlighted-text
      />
    </div>
  </ui-card>
  
</div>
</template>

<script setup>
import Step from './Step.vue'
import { ref, watch } from 'vue'
import UiCard from '@/components/UiCard'

const props = defineProps({
  progressData: Object,
  default: () => ({
    first: '0',
    second: '0',
    third: '0',
    fourth: '0'
  })
})

watch(() => props.progressData, (newprogressData) => {
  changreProgress(newprogressData)
})

const progress = ref({
  first: '0',
  second: '0',
  third: '0',
  fourth: '0',
  fifth: '0'
})

const timeoutIds = ref([])

const changreProgress = data => {
  const delay = 200
  if (data.first === '0') {
    timeoutIds.value.forEach(item => clearTimeout(item))
    progress.value = {
      first: '0',
      second: '0',
      third: '0',
      fourth: '0',
      fifth: '0'
    }
    return
  }
  let count = 0
  for (const key in data) {
    if (count === 0 ) count = 0.5
    const timeoutId = setTimeout(() => progress.value[key] = data[key], delay*count)
    timeoutIds.value.push(timeoutId)
    count++
  }

}
</script>

<style lang="scss">
.prizes {
  $parent: &;

  &__container {
    position: relative;
    display: flex;
    gap: 4px;
  }

  &__step {
    flex-grow: 1;
    width: calc(90%/4);
    flex-shrink: 0;

    &--last {
      width: max-content;
    }
  }

  &__desktop {
    @media (max-width: 999px) {
      display: none;
    }
  }

  &__tablet {
    display: none;

    #{$parent}__step {
      width: calc(85%/2);

      &--last {
        width: max-content;
      }
    }

    & + & {
      margin-top: 20px;
    }

    @media (max-width: 999px) {
      display: block;
    }
  }
}


</style>