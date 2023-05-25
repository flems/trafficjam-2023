<template>
<div class="timer" v-if="day && hour && tmin">
  <p class="timer__title">
    <span v-if="!isCompetitionStarted">До старта конкурса:</span>
    <span v-else>До окончания конкурса:</span>
  </p>
  <div class="timer__container">
    
    <span class="timer__number">
      <span v-html="day"></span>&nbsp;д
    </span>
    <template v-if="hour">
      :
      <span class="timer__number" v-if="hour">
        <span v-html="hour"></span>&nbsp;ч
      </span>
    </template>

    <template v-if="tmin">
      :
      <span class="timer__number">
        <span v-html="tmin"></span>&nbsp;м
      </span>
    </template>
    
  </div>
  <button class="banner__button">Пристыковаться</button>
</div>
</template>

<script setup>
import { onMounted, ref, computed, onUnmounted } from 'vue'


const timer = ref(null)
const timeend1 = new Date(2023, 5, 1, 12, 0, 0, 0)
const timeend2 = new Date(2023, 9, 31, 23, 59, 59, 0)
const tmin = ref(null)
const tsec = ref(null)

const isCompetitionStarted = computed(() => {
  return getCurrentDate() >= timeend1
})

const timeend = computed(() => {
  return isCompetitionStarted.value ? timeend2 : timeend1
})

const getCurrentDate = () => {
  const currentDate = new Date()
  currentDate.setTime(new Date().getTime() + new Date().getTimezoneOffset()*60*1000 + 3*60*60*1000)
  currentDate.setDate(new Date().getUTCDate())
  return currentDate
}

const hour = computed(() => {
  let thour = Math.floor((timeend.value - getCurrentDate()) / 1000 / 60 / 60) % 24
  if (thour < 0) thour = 0
  if (thour < 10) {
    thour = '0' + thour
  }
  return thour
})

const day = computed(() => {
  let today = Math.floor((timeend.value - getCurrentDate()) / 1000 / 60 / 60 / 24)
  if (today < 0) today = 0
  if (today < 10) {
      today = '0' + today
  }
  return today
})

const upd = () => {
  tsec.value = Math.floor((timeend.value - getCurrentDate()) / 1000) % 60
  if (tsec.value < 0) tsec.value = 0
  if (tsec.value < 10) {
      tsec.value = '0' + tsec.value
  }

  tmin.value = Math.floor((timeend.value - getCurrentDate()) / 1000 / 60) % 60
  if (tmin.value < 0) tmin.value = 0
  if (tmin.value < 10) {
      tmin.value = '0' + tmin.value
  }
}

const startTimer = () => {
  timer.value = setInterval(upd, 1000)
}

const stopTimer = () => {
  clearTimeout(timer.value)
}

onMounted(() => {
  upd()
  startTimer()
})

onUnmounted(() => {
  stopTimer()
})
</script>

<style lang="scss" scoped>
.banner__button {
  display: none;

  @media (max-width: 767px) {
    display: block;
    position: absolute;
    bottom: 113px;
  }
}
.timer {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-weight: 700;
  font-size: 20px;
  line-height: 1.4;
  font-family: 'Unbounded', sans-serif;

  &__title {
    color: #FDFDFD;
    margin-bottom: 4px;
    line-height: 1.25;
    font-weight: 400;
    font-size: 16px;
    font-family: 'Graphik LCG', sans-serif;
  }

  &__container {
    padding: 10px 40px;
    border: 2px solid #6B6B6B;
    border-radius: 16px;
    background: rgba(0, 2, 16, 0.1);
    backdrop-filter: blur(6px);
    display: flex;
    gap: 10px;

    @media (max-width: 479px) {
      padding-left: 24px;
      padding-right: 24px;
    }
  }

  &__number {
    flex-shrink: 0;
    padding: 0 10px;
  }
}
</style>