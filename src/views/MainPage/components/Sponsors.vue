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
    logo: '/images/logos/placeholder-logo-invert.svg',
    title: '',
    'tag-icon': 'universe',
    theme: 'blue',
    detail: 'Скоро сюда прибудет гость межгалактического альянса. Ожидаем.',
    col: 'col-12 col-md-6',
    'tag-name': 'Вселенная'
  },
  {
    logo: '/images/logos/placeholder-logo-invert.svg',
    title: '',
    'tag-icon': 'universe',
    theme: 'blue',
    detail: 'Скоро сюда прибудет гость межгалактического альянса. Ожидаем.',
    col: 'col-12 col-md-6',
    'tag-name': 'Вселенная'
  },
  {
    logo: '/images/logos/gazprom.png',
    title: 'Газпромбанк',
    'tag-icon': 'planet',
    theme: 'black',
    detail: 'Один из крупнейших универсальных финансовых институтов России, предоставляющий широкий спектр продуктов и услуг корпоративным и частным клиентам, финансовым институтам, институциональным и частным инвесторам.',
    col: 'col-12 col-md-6',
    'tag-name': 'Планета'
  },
  {
    logo: '/images/logos/placeholder-logo-invert.svg',
    title: '',
    'tag-icon': 'planet',
    theme: 'black',
    detail: 'Скоро сюда прибудет гость межгалактического альянса. Ожидаем.',
    col: 'col-12 col-md-6',
    'tag-name': 'Планета'
  },
  {
    logo: '/images/logos/rosbank.png',
    title: 'Росбанк',
    'tag-icon': 'star',
    theme: 'black',
    detail: '30 лет мы не стоим на месте и постоянно улучшаем качество наших продуктов, один из которых — кредитная карта #120наВСЁ Плюс. Желаем участникам конкурса успехов в продвижении и космического апрува.',
    col: 'col-12 col-md-6',
    'tag-name': 'Звезда'
  },
  {
    logo: '/images/logos/placeholder-logo-invert.svg',
    title: '',
    'tag-icon': 'star',
    theme: 'black',
    detail: 'Скоро сюда прибудет гость межгалактического альянса. Ожидаем.',
    col: 'col-12 col-md-6',
    'tag-name': 'Звезда'
  }
]
</script>

<style lang="scss">
    
</style>