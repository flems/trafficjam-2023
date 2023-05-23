<template>
<nav class="header-nav">
  <ul class="header-nav__list">
    <li
      class="header-nav__item"
      v-for="(item, index) in data"
      :key="index"
    >
      <a :href="item.link" @click.prevent="onClick(item.link)" class="header-nav__link">
        <span v-html="item.name"></span>
      </a>
    </li>
  </ul>
</nav>
</template>

<script setup>
import { gsap } from 'gsap'

const emits = defineEmits(['close'])

const onClick = hash => {
  const block = document.querySelector(hash)
  block.scrollIntoView({ behavior: 'smooth', block: 'start' });
  emits('close')
}

const data = [
  {
    name: 'О конкурсе',
    link: '#about'
  },
  {
    name: 'Спонсоры',
    link: '#sponsors'
  },
  {
    name: 'Призы',
    link: '#prizes'
  }
]
</script>

<style lang="scss">
.header-nav {
  border: 2px solid #6B6B6B;
  background-color: #000210E5;
  width: 190px;
  border-radius: 24px;
  padding: 80px 40px 40px;

  &__list {
    margin: 0;
    padding: 0;
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  &__link {
    color: #FDFDFD;
    font-size: 18px;
    text-decoration: none;
    transition: box-shadow 0.2s ease-in;

    &:hover {
      box-shadow: 0 1px 0 0 #FDFDFD;
    }
  }
}
</style>