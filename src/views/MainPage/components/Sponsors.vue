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
              <div class="sponsors__content">
                <div v-html="item.detail"></div>
                <a v-if="item.link" :href="item.link" class="sponsors__link" target="_blank">
                  <span>Пристыковаться</span>
                </a>
              </div>
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
    logo: '/images/logos/tinkoff.svg',
    title: 'Тинькофф',
    'tag-icon': 'universe',
    theme: 'blue',
    detail: 'Космическая выгода для всех участников TrafficJam 2023! Не просто красивые карты, могут экономить и зарабатывать для вас!',
    col: 'col-12 col-lg-6',
    'tag-name': 'Вселенная',
    link: 'https://rafinad.io/offers/?term=%D1%82%D0%B8%D0%BD%D1%8C%D0%BA%D0%BE%D1%84%D1%84&page=1&page_size=10&sortField=publish_dt&sortDir=desc'
  },
  {
    logo: '/images/logos/placeholder-logo-invert.svg',
    title: '',
    'tag-icon': 'universe',
    theme: 'blue',
    detail: 'Скоро сюда прибудет гость межгалактического альянса. Ожидаем.',
    col: 'col-12 col-lg-6',
    'tag-name': 'Вселенная',
    link: ''
  },
  {
    logo: '/images/logos/placeholder-logo-invert.svg',
    title: '',
    'tag-icon': 'planet',
    theme: 'black',
    detail: 'Скоро сюда прибудет гость межгалактического альянса. Ожидаем.',
    col: 'col-12 col-md-6 col-xl-5',
    'tag-name': 'Планета',
    link: ''
  },
  {
    logo: '/images/logos/gazprom.png',
    title: 'Газпромбанк',
    'tag-icon': 'planet',
    theme: 'black',
    detail: 'Один из крупнейших универсальных финансовых институтов России, предоставляющий широкий спектр продуктов и услуг корпоративным и частным клиентам, финансовым институтам, институциональным и частным инвесторам.',
    col: 'col-12 col-md-6 col-xl-5',
    'tag-name': 'Планета',
    link: 'https://rafinad.io/offers/?term=%D0%B3%D0%B0%D0%B7%D0%BF%D1%80%D0%BE%D0%BC%D0%B1%D0%B0%D0%BD%D0%BA&page=1&page_size=10&sortField=publish_dt&sortDir=desc'
  },
  {
    logo: '/images/logos/rosbank.png',
    title: 'Росбанк',
    'tag-icon': 'star',
    theme: 'black',
    detail: '30 лет мы не стоим на месте и постоянно улучшаем качество наших продуктов, один из которых — кредитная карта #120наВСЁ Плюс. Желаем участникам конкурса успехов в продвижении и космического апрува.',
    col: 'col-12 col-md-6 col-xl-4',
    'tag-name': 'Звезда',
    link: 'https://rafinad.io/offers/?term=%D1%80%D0%BE%D1%81%D0%B1%D0%B0%D0%BD%D0%BA&page=1&page_size=10&sortField=publish_dt&sortDir=desc'
  },
  {
    logo: '/images/logos/placeholder-logo-invert.svg',
    title: '',
    'tag-icon': 'star',
    theme: 'black',
    detail: 'Скоро сюда прибудет гость межгалактического альянса. Ожидаем.',
    col: 'col-12 col-md-6 col-xl-4',
    'tag-name': 'Звезда',
    link: ''
  }
]
</script>

<style lang="scss">
.sponsors {
  &__link {
    text-decoration: none;
    color: currentColor;
    display: block;
    width: max-content;
    margin-top: 48px;
    font-size: 16px;
    font-weight: 500;
    margin-left: auto;
    position: relative;
    padding-bottom: 2px;

    
    &:before,
    &:after {
      content: '';
      height: 1px;
      position: absolute;
      width: 100%;
      bottom: 0;
      display: block;
      left: 0;
      background: currentColor;
      border-radius: 2px;
      transition: width 0.2s ease-in;
      opacity: 0.3;
    }

    &:after {
      width: 0%;
      background: currentColor;
      left: 50%;
      opacity: 1;
      transform: translateX(-50%);
    }

    &:hover {
      &:after {
        width: 100%;
      }
    }
  }

  &__content {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    flex-grow: 1;
  }
}
</style>