<template>
  <div class="mechanics">
    <div class="container">
      <h2>механика конкурса</h2>
      <div class="row">
        <div class="col-12 col-lg-6 col-xl-4">
          <ui-card interactive full-height class="mechanics__card" @mouseleave="onMouseleave" @mouseenter="onMouseenter('sugar')">
              <h3 class="mechanics__title">Зарабатывай Сахарки</h3>
              <p>За каждые заработанные <b>100 рублей</b> начисляется <b>10 сахарков</b>. По спонсорским офферам начисляется 20, 30 и даже 40 сахарков в зависимости от спонсора!</p>
          </ui-card>
        </div>
        <div class="col-12 col-lg-6 col-xl-4">
          <ui-card interactive full-height class="mechanics__card" @mouseleave="onMouseleave" @mouseenter="onMouseenter('prizes')">
              <h3 class="mechanics__title">Получай призы</h3>
              <p>Ты <b>гарантированно получаешь кешбэк</b>, достигая чек-поинта. <b>Больше трафика — круче приз</b>, неважно когда ты подключился в игру и кто сегодня в ТОПе!</p>
          </ui-card>
        </div>
        <div class="col-12 col-lg-6 col-xl-4">
          <ui-card interactive full-height class="mechanics__card" @mouseleave="onMouseleave" @mouseenter="onMouseenter('top')">
              <h3 class="mechanics__title">Попадай в топ</h3>
              <p>Начиная с <b>3-го уровня ты начинаешь бороться за место ТОПе</b>, где среди лучших 10 участников будет распределен призовой фонд <b>в __ рублей.</b></p>
          </ui-card>
        </div>
        <div class="col-12">
          <ui-card>
            <prizes :progress-data="progress" />
          </ui-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import UiCard from "@/components/UiCard"
import Prizes from "./components/Prizes.vue"
import { ref } from 'vue'

const progress = ref({
  first: '0',
  second: '0',
  third: '0',
  fourth: '0',
  fifth: '0'
})

const onMouseenter = card => {
  if (card === 'sugar') {
    progress.value = {
      first: '85',
      second: '0',
      third: '0',
      fourth: '0',
      fifth: '0'
    }
  }
  if (card === 'prizes') {
    progress.value = {
      first: '100',
      second: '100',
      third: '100',
      fourth: '5',
      fifth: '0'
    }
  }
  if (card === 'top') {
      progress.value = {
        first: '100',
        second: '100',
        third: '100',
        fourth: '100',
        fifth: '100'
      }
  }
}

const onMouseleave = () => {
  progress.value = {
    first: '0',
    second: '0',
    third: '0',
    fourth: '0'
  }
}
</script>

<style lang="scss">
.mechanics {
  &__title {
    @media (max-width: 1550px) {
      min-height: calc(2em * 1.4);
    }
  }

  &__card {
  }
}
</style>