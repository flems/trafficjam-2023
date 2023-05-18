<template>
  <div class="mp-prizes">
    <div class="container">
      <h2>Джемовые призы</h2>
      <div class="mp-prizes__list">
        <div
          class="mp-prizes__item"
          :class="`mp-prizes__item--${index + 1}`"
          v-for="(item, index) in prizes"
          :key="index"
        >
          <template v-if="!item.isParent">
              <card-default
                :interactive="false"
                :tag-name="item.tagName"
                :tag-width="item.tagWidth"
                :theme="item.theme"
                full-height
                class="prizes-card"
                :class="[
                  `prizes-card--size-${item.size}`,
                  `prizes-card--index-${index + 1}`,
                ]"
                :active="item.active"
              >
              <template v-slot:default>
                <div class="prizes-card__content">
                  <p class="prizes-card__title" v-html="item.title"></p>
                  <div class="prizes-card__image" :style="`background-image: url(${item.image})`"></div>
                </div>
              </template>
            </card-default>
          </template>
          <template v-else>
            <div class="mp-prizes__sub-list">
              <div
                class="mp-prizes__sub-item"
                :class="`mp-prizes__sub-item--${subIndex + 1}`"
                v-for="(subItem, subIndex) in item.items"
                :key="subIndex"
              >
                <card-default
                  :interactive="false"
                  :tag-name="subItem.tagName"
                  :tag-width="subItem.tagWidth"
                  :theme="subItem.theme"
                  full-height
                  class="prizes-card"
                  :class="[
                  `prizes-card--size-${subItem.size}`,
                  `prizes-card--subindex-${subIndex + 1}`,
                ]"
                >
                  <template v-slot:default>
                    <div class="prizes-card__content">
                      <p class="prizes-card__title" v-html="subItem.title"></p>
                      <div class="prizes-card__image" :style="`background-image: url(${subItem.image})`"></div>
                    </div>
                  </template>
                </card-default>
              </div>
            </div>
          </template>
          
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>
import CardDefault from '@/components/CardDefault/Card.vue'

const prizes = [
  {
    tagName: '1 место',
    tagWidth: '85px',
    title: '1&nbsp;000&nbsp;000 рублей',
    theme: 'blue',
    image: '/images/main-page/prizes/1.png',
    size: 'xl',
    active: true
  },
  {
    tagName: '2 место',
    tagWidth: '85px',
    theme: 'blue',
    title: '600&nbsp;000 рублей',
    image: '/images/main-page/prizes/2.png',
    size: 'l'
  },
  {
    tagName: '3 место',
    tagWidth: '85px',
    theme: 'blue',
    title: '400&nbsp;000 рублей',
    image: '/images/main-page/prizes/3.png',
    size: 'l'
  },
  {
    isParent: true,
    items: [
      {
        tagName: '4',
        tagWidth: '50px',
        theme: 'black',
        title: '300&nbsp;000 рублей',
        image: '/images/main-page/prizes/4.png',
        size: 'm'
      },
      {
        tagName: '5',
        tagWidth: '50px',
        theme: 'black',
        title: 'Apple MacBook Air 13.6"',
        image: '/images/main-page/prizes/5.png',
        size: 'm'
      },
      {
        tagName: '6',
        tagWidth: '50px',
        theme: 'black',
        title: 'Apple iPad Pro 12.9 M2 (2022)',
        image: '/images/main-page/prizes/6.png',
        size: 'm'
      },
    ]
  },
  {
    tagName: '7',
    tagWidth: '50px',
    theme: 'black',
    title: 'iPhone&nbsp;14 Pro Max 512Gb eSim',
    image: '/images/main-page/prizes/7.png',
    size: 's'
  },
  {
    tagName: '8',
    tagWidth: '50px',
    theme: 'black',
    title: 'Samsung Galaxy S23 Ultra 8/256Gb',
    image: '/images/main-page/prizes/8.png',
    size: 's'
  },
  {
    tagName: '9',
    tagWidth: '50px',
    theme: 'black',
    title: 'Apple<br>Watch<br>Ultra GPS',
    image: '/images/main-page/prizes/9.png',
    size: 's'
  },
  {
    tagName: '10',
    tagWidth: '50px',
    theme: 'black',
    title: 'Sony Playstation&nbsp;5',
    image: '/images/main-page/prizes/10.png',
    size: 's'
  }
]
</script>

<style lang="scss">
.mp-prizes {
  &__list {
    display: grid;
    grid-gap: 20px;
    grid-template-rows: repeat(3, 1fr);
    grid-template-columns: repeat(12, 1fr);
  }

  &__item {
    grid-column: span 2;

    @media (max-width: 999px) {
      grid-column: span 3;
    }

    @media (max-width: 767px) {
      grid-column: span 6;
    }

    @media (max-width: 479px) {
      grid-column: span 12;
    }

    &--1 {
      grid-row-start: 1;
      grid-row-end: 3;
      grid-column-start: 1;
      grid-column-end: 5;

      @media (max-width: 999px) {
        grid-column-end: 7;
      }

      @media (max-width: 767px) {
        grid-column-end: 13;
      }
    }

    &--2, &--3 {
      grid-column: span 4;

      @media (max-width: 999px) {
        grid-column: span 6;
      }

      @media (max-width: 767px) {
        grid-column: span 12;
      }
    }

    &--4 {
      grid-column: span 8;

      @media (max-width: 999px) {
        grid-column: span 12;
      }
    }

    &--5 {
      grid-column-start: 5;
      grid-column-end: 7;

      @media (max-width: 999px) {
        grid-column-start: 1;
        grid-column: span 3;
      }

      @media (max-width: 767px) {
        grid-column: span 6;
      }

      @media (max-width: 479px) {
        grid-column: span 12;
      }
    }
  }

  &__sub-list {
    height: 100%;
    display: grid;
    grid-gap: 20px;
    grid-template-rows: 1fr;
    grid-template-columns: repeat(12, 1fr);
  }

  &__sub-item {
    grid-column: span 4;

    @media (max-width: 767px) {
      grid-column: span 6;
    }

    @media (max-width: 479px) {
      grid-column: span 12;
    }

    &--1 {
      @media (max-width: 767px) {
        grid-column: span 12;
      }
    }
  }
}

.prizes-card {
  $parent: &;
  min-height: 200px;

  &__title {
    font-family: 'Unbounded', sans-serif;
    font-weight: 500;
    text-transform: uppercase;
    line-height: 1.4;
    color: #FDFDFD;
    max-width: calc(100% - 50px - 8px);
  }

  &__image {
    width: 100%;
    background-repeat: no-repeat;
    background-size: contain;
    background-position: 50% 50%;
    display: block;
    z-index: -1;

    @media (max-width: 1000px) {
      background-size: contain !important;
      background-position: 50% 50% !important;
    }

    &:after {
      width: 100%;
      display: block;
      content: '';
      padding-top: 78%;
    }
  }

  #{$parent}__content {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 10;
    overflow: hidden;
    display: flex;
    flex-direction: column;
  }
  
  &--size-xl {
    #{$parent}__content {
      border-bottom: 2px solid #cdd8ff;
      border-radius: 20px;
    }

    #{$parent}__title {
      max-width: calc(100% - 85px - 8px);
      font-size: 32px;
      color: #000210;
      padding: 32px;
      flex-grow: 1;

      @media (max-width: 1399px) {
        padding: 32px 24px;
      }

      @media (max-width: 999px) {
        font-size: 24px;
      }
    }

    #{$parent}__image {
      margin-top: -20px;
    }
  }
  
  &--size-l {
    #{$parent}__content {
      border-bottom: 2px solid #cdd8ff;
      border-radius: 20px;
    }

    #{$parent}__title {
      max-width: calc(100% - 85px - 8px);
      font-size: 24px;
      color: #000210;
      padding: 32px;

      @media (max-width: 1279px) {
        font-size: 20px;
        padding: 24px;
      }
    }

    #{$parent}__image {
      width: 100%;
      position: absolute;
      top: 50px;
      right: 10px;
      height: 83%;
      background-position: 100% 0;
    }
  }

  &--size-m {
    #{$parent}__image {
      width: 100%;
      position: absolute;
      bottom: -2px;
      right: 0;
      height: calc(100% - 60px);
      background-position: 100% 0;
      border-bottom-right-radius: 20px;
      border-right: 2px solid #6B6B6B;
    }

    #{$parent}__content {
      border-bottom: 2px solid #6B6B6B;
      border-radius: 20px;
    }

    #{$parent}__title {
      font-size: 16px;
      padding: 24px 20px;

      @media (max-width: 1279px) {
        font-size: 14px;
      }

      @media (max-width: 767px) {
        padding: 24px 12px;
        font-size: 16px;
      }

      @media (max-width: 479px) {
        padding: 24px;
      }
    }
  }

  &--subindex-1 {
    #{$parent}__image {
      background-size: 78% auto;
      background-position: 100% 0;
    }
  }

  &--subindex-2 {
    #{$parent}__image {
      background-size: 90% auto;
      background-position: 280% -310%;

      @media (max-width: 1399px) {
        background-size: auto 80%;
        background-position: 130% 100%;
      }

      @media (max-width: 479px) {
        background-position: 230% 0;
      }
    }
  }

  &--subindex-3 {
    #{$parent}__image {
      background-position: 89% 20px;
    }
  }
  
  &--size-s {
    #{$parent}__content {
      padding-top: 68px;
      justify-content: flex-end;
      border-bottom: 2px solid #6B6B6B;
      border-radius: 20px;
    }

    #{$parent}__title {
      max-width: 100%;
      padding: 20px;
      font-size: 16px;

      @media (max-width: 1279px) {
        font-size: 16px;
        padding: 14px;
      }
    }

    #{$parent}__image {
      width: 100%;
      position: absolute;
      bottom: -2px;
      right: 0;
      height: calc(100% - 60px);
      background-position: 100% 0;
      border-bottom-right-radius: 20px;
      border-right: 2px solid #6B6B6B;
      z-index: -1;
    }
  }

  &--index-5 {
    #{$parent}__image {
      background-size: 60% auto;
      background-position: 130% 0%;
    }
  }

  &--index-6 {
    #{$parent}__image {
      background-size: 87% auto;
      background-position: 330% 0%;
    }
  }

  &--index-7 {
    #{$parent}__image {
      background-size: 66% auto;
      background-position: 150% 0%;
    }
  }

  &--index-8 {
    #{$parent}__image {
      background-size: 57% auto;
      background-position: 130% 0%;
    }
  }
  
}
</style>