<template>
  <div class="mechanics">
    <div class="container">
      <h2>Механика конкурса</h2>
      <div class="row">
        <div class="col-12 col-md-4">
          <ui-card interactive full-height class="mechanics__card" @mouseleave="onMouseleave" @mouseenter="onMouseenter('sugar')">
              <h3 class="mechanics__title">Зарабатывай Сахарки</h3>
              <p>За&nbsp;каждые заработанные <b>100 рублей</b> начисляется <b>10 сахарков</b>. По&nbsp;спонсорским офферам начисляется 20, 30 и&nbsp;даже 40 сахарков в&nbsp;зависимости от&nbsp;спонсора!</p>
              <prizes-card
                class="mechanics__card-prizes"
                :initial="[
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
                ]"
              />
          </ui-card>
        </div>
        <div class="col-12 col-md-4">
          <ui-card interactive full-height class="mechanics__card" @mouseleave="onMouseleave" @mouseenter="onMouseenter('prizes')">
              <h3 class="mechanics__title">Получай кешбэк</h3>
              <p>Ты <b>гарантированно получаешь кешбэк</b>, достигая чек-пойнта. <b>Больше трафика&nbsp;&mdash; круче кешбэк</b>, неважно когда ты подключился в&nbsp;игру и&nbsp;кто сегодня в&nbsp;ТОПе!</p>
              <prizes-card
                class="mechanics__card-prizes"
                :data="[
                  {
                    progress: '100',
                    name: '3',
                    icon: 'box',
                    score: '600&nbsp;000',
                    theme: 'black',
                    'active-icon': 'box-opened'
                  },
                  {
                    progress: '5',
                    name: '4',
                    icon: 'box',
                    score: '1&nbsp;200&nbsp;000',
                    theme: 'blue',
                    'active-icon': 'box-opened'
                  },
                  {
                    progress: '0',
                    name: 'top',
                    icon: 'box',
                    last: true,
                    theme: 'blue',
                    text: true,
                    'active-icon': 'box-opened'
                  },
                ]"
                :initial="[
                  {
                    progress: '0',
                    name: '1',
                    icon: 'box',
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
                ]"
              />
          </ui-card>
        </div>
        <div class="col-12 col-md-4">
          <ui-card interactive full-height class="mechanics__card" @mouseleave="onMouseleave" @mouseenter="onMouseenter('top')">
              <h3 class="mechanics__title">Попадай в&nbsp;топ</h3>
              <p>Начиная с&nbsp;<b>4-го уровня ты начинаешь бороться за место в&nbsp;ТОПе</b>, где среди лучших 10 участников будет распределен призовой фонд <b>более&nbsp;3&nbsp;000&nbsp;000 рублей.</b></p>
              <prizes-card
                class="mechanics__card-prizes"
                :data="[
                  {
                    progress: '100',
                    name: '3',
                    icon: 'box',
                    score: '600&nbsp;000',
                    theme: 'black',
                    'active-icon': 'box-opened'
                  },
                  {
                    progress: '100',
                    name: '4',
                    icon: 'box',
                    score: '1&nbsp;200&nbsp;000',
                    theme: 'blue',
                    'active-icon': 'box-opened'
                  },
                  {
                    progress: '100',
                    name: 'top',
                    icon: 'box',
                    last: true,
                    theme: 'blue',
                    text: true,
                    'active-icon': 'box-opened'
                  },
                ]"
                :initial="[
                  {
                    progress: '0',
                    name: '1',
                    icon: 'box',
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
                ]"
              />
          </ui-card>
        </div>
        <div class="col-12 mechanics__hidden-mobile">
          <prizes :progress-data="progress" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import UiCard from '@/components/UiCard'
import Prizes from './components/Prizes.vue'
import PrizesCard from './components/PrizesCard.vue'

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
    // min-height: calc(2em * 1.4);

    @media (max-width: 767px) {
      min-height: auto;
    }
  }

  &__hidden-mobile {
    @media (max-width: 767px) {
      display: none;
    }
  }

  &__card {
    @media (max-width: 767px) {
      pointer-events: none;
    }
  }

  &__card-prizes {
    display: none;

    @media (max-width: 767px) {
      display: flex;
      margin-top: 32px;
    }
  }
}
</style>