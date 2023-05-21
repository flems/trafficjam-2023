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
    logo: '/images/logos/gazprom.png',
    title: 'Газпромбанк',
    'tag-icon': 'planet',
    theme: 'black',
    detail: 'Один из крупнейших универсальных финансовых институтов России, предоставляющий широкий спектр продуктов и услуг корпоративным и частным клиентам, финансовым институтам, институциональным и частным инвесторам.',
    col: 'col-12 col-md-6',
    'tag-name': 'Планета'
  },
  // {
  //   logo: '/images/logos/placeholder-logo.png',
  //   title: '',
  //   'tag-icon': 'planet',
  //   theme: 'black',
  //   detail: '',
  //   col: 'col-12 col-md-6',
  //   'tag-name': 'Планета'
  // },
  {
    logo: '/images/logos/rosbank.png',
    title: 'Росбанк',
    'tag-icon': 'star',
    theme: 'black',
    detail: '30 лет мы не стоим на месте и постоянно улучшаем качество наших продуктов, один из которых — кредитная карта #120наВСЁ Плюс. Желаем участникам конкурса успехов в продвижении и космического апрува.',
    col: 'col-12 col-md-6',
    'tag-name': 'Звезда'
  },
  // {
  //   logo: '/images/logos/safepal.svg',
  //   title: 'Название компании',
  //   'tag-icon': 'planet',
  //   theme: 'black',
  //   detail: 'Ты гарантированно <b>получаешь приз</b>, достигнув чек-поинта, <b>больше трафика – круче приз</b>, поэтому неважно когда Ты подключился в игру и кто сегодня в ТОПе! После прохождения всех уровней. Ты попадаешь в ТОП, где среди первых 10 участников будет разыгран призовой фонд в 2,5 млн рублей!',
  //   col: 'col-12 col-md-6 col-xl-5',
  //   'tag-name': 'Планета'
  // },
  // {
  //   logo: '/images/logos/safepal.svg',
  //   title: 'Название компании',
  //   'tag-icon': 'star',
  //   theme: 'black',
  //   detail: 'Ты гарантированно <b>получаешь приз</b>, достигнув чек-поинта, <b>больше трафика – круче приз</b>, поэтому неважно когда Ты подключился в игру и кто сегодня в ТОПе! После прохождения всех уровней. Ты попадаешь в ТОП, где среди первых 10 участников будет разыгран призовой фонд в 2,5 млн рублей!',
  //   col: 'col-12 col-md-6 col-xl-4',
  //   'tag-name': 'Звезда'
  // }
]
</script>

<style lang="scss">
    
</style>