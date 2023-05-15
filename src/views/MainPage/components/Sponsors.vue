<template>
  <div class="sponsors">
    <div class="container">
      <h2>Спонсоры проекта</h2>

      <div class="row">
        <div
          :class="item.col"
          v-for="(item, index) in sponsors"
          :key="index"
        >
          <card
            :logo="item.logo"
            :title="item.title"
            :tag-icon="item['tag-icon']"
            :theme="item.theme"
            full-height
            :tag-name="item['tag-name']"
          >
            <template v-slot:content>
              <div v-html="item.detail"></div>
            </template>
          </card>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import Card from "@/components/Card"

const sponsors = [
  {
    logo: '/images/logos/safepal.svg',
    title: 'Название компании',
    'tag-icon': 'universe',
    theme: 'blue',
    detail: 'Ты гарантированно <b>получаешь приз</b>, достигнув чек-поинта, <b>больше трафика – круче приз</b>, поэтому неважно когда Ты подключился в игру и кто сегодня в ТОПе! После прохождения всех уровней. Ты попадаешь в ТОП, где среди первых 10 участников будет разыгран призовой фонд в 2,5 млн рублей!',
    col: 'col-12 col-md-6',
    'tag-name': 'Вселенная'
  },
  {
    logo: '/images/logos/safepal.svg',
    title: 'Название компании',
    'tag-icon': 'universe',
    theme: 'blue',
    detail: 'Ты гарантированно <b>получаешь приз</b>, достигнув чек-поинта, <b>больше трафика – круче приз</b>, поэтому неважно когда Ты подключился в игру и кто сегодня в ТОПе! После прохождения всех уровней. Ты попадаешь в ТОП, где среди первых 10 участников будет разыгран призовой фонд в 2,5 млн рублей!',
    col: 'col-12 col-md-6',
    'tag-name': 'Вселенная'
  },
  {
    logo: '/images/logos/safepal.svg',
    title: 'Название компании',
    'tag-icon': 'planet',
    theme: 'black',
    detail: 'Ты гарантированно <b>получаешь приз</b>, достигнув чек-поинта, <b>больше трафика – круче приз</b>, поэтому неважно когда Ты подключился в игру и кто сегодня в ТОПе! После прохождения всех уровней. Ты попадаешь в ТОП, где среди первых 10 участников будет разыгран призовой фонд в 2,5 млн рублей!',
    col: 'col-12 col-md-6 col-xl-5',
    'tag-name': 'Планета'
  },
  {
    logo: '/images/logos/safepal.svg',
    title: 'Название компании',
    'tag-icon': 'star',
    theme: 'black',
    detail: 'Ты гарантированно <b>получаешь приз</b>, достигнув чек-поинта, <b>больше трафика – круче приз</b>, поэтому неважно когда Ты подключился в игру и кто сегодня в ТОПе! После прохождения всех уровней. Ты попадаешь в ТОП, где среди первых 10 участников будет разыгран призовой фонд в 2,5 млн рублей!',
    col: 'col-12 col-md-6 col-xl-4',
    'tag-name': 'Звезда'
  }
]
</script>

<style lang="scss">
    
</style>