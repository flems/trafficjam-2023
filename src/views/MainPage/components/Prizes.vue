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
                :class="`prizes-card--size-${item.size}`"
                :active="item.active"
              >
              <template v-slot:default>
                <div class="prizes-card__content">
                  <p class="prizes-card__title" v-html="item.title"></p>
                  <img class="prizes-card__image" :src="item.image" alt="" width="100">
                </div>
              </template>
            </card-default>
          </template>
          <template v-else>
            <div class="mp-prizes__sub-list">
              <div
                class="mp-prizes__sub-item"
                :class="`mp-prizes__sub-item--${index + 1}`"
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
                  :class="`prizes-card--size-${subItem.size}`"
                >
                  <template v-slot:default>
                    <div class="prizes-card__content">
                      <p class="prizes-card__title" v-html="subItem.title"></p>
                      <img class="prizes-card__image" :src="subItem.image" alt="" width="100">
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
    title: '600&nbsp;000 рублей',
    theme: 'blue',
    image: '/images/main-page/prizes/1.png',
    size: 'xl',
    active: true
  },
  {
    tagName: '2 место',
    tagWidth: '85px',
    theme: 'blue',
    title: '300&nbsp;000 рублей',
    image: '/images/main-page/prizes/2.png',
    size: 'l'
  },
  {
    tagName: '3 место',
    tagWidth: '85px',
    theme: 'blue',
    title: '100&nbsp;000 рублей',
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
        title: 'Apple iMac 24-inch',
        image: '',
        size: 'm'
      },
      {
        tagName: '5',
        tagWidth: '50px',
        theme: 'black',
        title: 'Apple MacBook Pro 13',
        image: '',
        size: 'm'
      },
      {
        tagName: '6',
        tagWidth: '50px',
        theme: 'black',
        title: 'apple ipad 256gb',
        image: '',
        size: 'm'
      },
    ]
  },
  {
    tagName: '7',
    tagWidth: '50px',
    theme: 'black',
    title: 'apple iphone 14 pro max 256gb',
    image: '',
    size: 's'
  },
  {
    tagName: '8',
    tagWidth: '50px',
    theme: 'black',
    title: 'Название приза',
    image: '',
    size: 's'
  },
  {
    tagName: '9',
    tagWidth: '50px',
    theme: 'black',
    title: 'Название приза',
    image: '',
    size: 's'
  },
  {
    tagName: '10',
    tagWidth: '50px',
    theme: 'black',
    title: 'Название приза',
    image: '',
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
    grid-template-columns: repeat(6, 1fr);
  }

  &__item {
    &--1 {
      grid-row-start: 1;
      grid-row-end: 3;
      grid-column-start: 1;
      grid-column-end: 3;
    }

    &--2, &--3 {
      grid-column: span 2;
    }

    &--4 {
      grid-column: span 4;
    }

    &--5 {
      grid-column-start: 3;
      grid-column-end: 4;
    }
  }

  &__sub-list {
    height: 100%;
    display: grid;
    grid-gap: 20px;
    grid-template-rows: 1fr;
    grid-template-columns: repeat(3, 1fr);
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
    font-size: 16px;
    padding: 24px;
    max-width: calc(100% - 50px - 8px);
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
    }

    #{$parent}__image {
      width: 100%;
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
    }

    #{$parent}__image {
      width: auto;
      position: absolute;
      bottom: 0;
      right: 0;
      height: 67%;
    }
  }
  
  &--size-s {
    #{$parent}__content {
      padding-top: 68px;
      justify-content: flex-end;
    }

    #{$parent}__title {
      max-width: 100%;
    }
  }
}
</style>