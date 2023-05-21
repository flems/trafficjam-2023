<template>
<div class="prizes-first" ref="container">
  <step
    v-for="(item, index) in stepData"
    :key="index"
    class="prizes-first__step"
    :class="{ 'prizes-first__step--last': item.last }"
    :name="item.name"
    :icon="item.icon"
    :score="item.score"
    :progress="item.progress"
    :last="item.last"
    :theme="item.theme"
    :active-icon="item['active-icon']"
    :text="item.text"
    :highlighted-text="item['highlighted-text']"
  />
</div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import Step from './Step.vue'
import verge from 'verge'

const props = defineProps({
  data: {
    type: Array,
    default: () => [
      {
        progress: '85',
        name: '1',
        icon: 'rocket',
        score: '40&nbsp;000',
        theme: 'black'
      },
      {
        progress: '0',
        name: '2',
        icon: 'box',
        score: '200&nbsp;000',
        theme: 'black',
        'active-icon': 'box-opened'
      },
      {
        progress: '0',
        name: '3',
        icon: 'box',
        score: '600&nbsp;000',
        last: true,
        theme: 'blue',
        'active-icon': 'box-opened',
        text: false,
        'highlighted-text': false
      }
    ]
  },
  initial: {
    type: Array,
    default: () => ([
      {
        progress: '0',
        name: '1',
        icon: 'rocket',
        score: '',
        theme: 'black'
      },
      {
        progress: '0',
        name: '2',
        icon: 'box',
        score: '',
        theme: 'black',
        'active-icon': 'box-opened'
      },
      {
        progress: '0',
        name: '3',
        icon: 'box',
        score: '',
        last: true,
        theme: 'blue',
        'active-icon': 'box-opened',
        text: false,
        'highlighted-text': false
      }
    ])
  }
})

const container = ref(null)
const viewportOffset = -250
const stepData = ref(props.initial)

const isInView = () => {
  if (!container.value) return
  
  if (verge.inY(container.value, viewportOffset)) {
    return true
  }

  return false
}


onMounted(() => {
  window.addEventListener('scroll', () => {
    if (isInView()) {
      stepData.value = props.data
    }
  })
})
</script>

<style lang="scss">
.prizes-first {
  $parent: &;

  position: relative;
  display: flex;
  gap: 4px;

  &__step {
    flex-grow: 1;
    width: calc(80%/2);
    flex-shrink: 0;

    &--last {
      width: max-content;
    }
  }
}
</style>