<template>
  <header class="header">
    <div class="header__container container">
      <div class="header__left"></div>
        <div class="header__logo">
          <div class="header__logo-borders">
            <span class="header__logo-border-top-left"></span>
            <span class="header__logo-border-bottom-left"></span>
          </div>
          <div class="header__logo-borders header__logo-borders--right">
            <span class="header__logo-border-top-left"></span>
            <span class="header__logo-border-bottom-left"></span>
          </div>
          <a href="https://rafinad.io/" target="_blank">
            <img src="/images/logo.svg" alt="Rafinad">
          </a>
        </div>
        <div class="header__right">
          <div class="header__menu" v-click-outside="closeMenu">
            <div class="header__menu-patch"></div>
            <div class="header__logo-borders">
              <span class="header__logo-border-top-left"></span>
              <span class="header__logo-border-bottom-left"></span>
            </div>
            <div class="header__logo-borders header__logo-borders--right">
              <span class="header__logo-border-top-left"></span>
              <span class="header__logo-border-bottom-left"></span>
            </div>
            
            <button class="header__burger" @click="toggleMenu">
              <ui-icon
                width="28"
                height="28"
                :name="isMenuOpened ? 'close' : 'burger'" />
            </button>

            <header-nav
              class="header__nav"
              :class="{ 'header__nav--opened' : isMenuOpened}"
              @close="closeMenu"
            />
          </div>
        </div>
    </div>
  </header>
</template>

<script setup>
import HeaderNav from '@/components/HeaderNav'
import UiIcon from '@/components/UiIcon'
import { ref } from 'vue'

const isMenuOpened = ref(false)

const toggleMenu = () => {
  isMenuOpened.value = !isMenuOpened.value
}

const closeMenu = () => {
  isMenuOpened.value = false
}
</script>

<style lang="scss">
.header {
  --borderColor: #6B6B6B;
  --borderWidth: 2px;
  --headerHeight: 38px;
  --headerBg: #000210;
  --borderRadius: 20px
}

.header {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 3;

  &__burger {
    background: none;
    border: none;
    padding: 0;
    cursor: pointer;

    svg {
      pointer-events: none;
    }
  }

  &__container {
    display: flex;

    @media (max-width: 999px) {
      justify-content: space-between;
      padding: 0;
    }
  }

  &__nav {
    position: absolute;
    top: 0;
    right: -2px;
    z-index: -1;
    transform: translateY(-100%);
    transition: transform 0.3s ease-out;

    @media (max-width: 1279px) {
      right: 0;
    }
    
    .header-nav__link {
      opacity: 0;
      transition: opacity 0.2s ease-out 0.25s;
    }

    &--opened {
      transform: translateY(0);

      .header-nav__link {
        opacity: 1;
      }
    }
  }

  &:before {
    content: '';
    width: 100%;
    height: var(--headerHeight);
    top: 0;
    pointer-events: none;
    z-index: 0;
    left: 0;
    position: absolute;
    background: var(--headerBg);
    border-bottom: var(--borderWidth) solid var(--borderColor);
  }

  &__left,
  &__right {
    width: 50%;
  }

  &__left {
    @media (max-width: 990px) {
      display: none;
    }
  }

  &__logo {
    flex-shrink: 0;
    padding: 16px 80px 16px;
    background: var(--headerBg);
    position: relative;
    height: 56px;

    @media (max-width: 767px) {
      padding-left: 36px;
      padding-right: 36px;
    }

    img {
      position: relative;
      z-index: 2;
      height: 28px;
      width: auto;

      @media (max-width: 767px) {
        height: 24px;
      }
    }

    &:after {
      content: '';
      bottom: 0;
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      width: calc(100% - 88px);
      border-bottom: var(--borderWidth) solid var(--borderColor);
      display: block;
    }

  }

  &__logo-borders {
    position: absolute;
    width: 44px;
    height: 22px;
    z-index: 10;
    top: calc(var(--headerHeight) - var(--borderWidth));
    left: 0;

    &--right {
      right: 0;
      left: auto;
      transform: scale(-1, 1);
    }
  }

  &__logo-border-top-left {
    position: absolute;
    top: 0;
    left: 0;
    display: block;
    height: 50%;
    width: 50%;
    overflow: hidden;

    &:before {
      content: "";
      width: 81px;
      height: 90px;
      border-radius: 50%;
      border: var(--borderWidth) solid var(--borderColor);
      display: block;
      position: absolute;
      top: 0px;
      right: -18px;
    }
  }
  
  &__logo-border-bottom-left {
    position: absolute;
    bottom: 0;
    right: 0;
    display: block;
    height: calc(50% + var(--borderWidth)*2);
    width: 50%;
    overflow: hidden;

    &:before {
      content: "";
      width: 80px;
      height: 90px;
      border-radius: 50%;
      border: var(--borderWidth) solid var(--borderColor);
      display: block;
      position: absolute;
      bottom: 2px;
      left: -15px;
    }
  }

  &__right {
    display: flex;
    justify-content: flex-end;
  }

  &__menu-patch {
    position: absolute;
    bottom: 18px;
    left: 50%;
    transform: translateX(-50%);
    width: 95%;
    height: 4px;
    background: #000210;
    pointer-events: none;

    &:after,
    &:before {
      content: '';
      background: #000210;
      display: block;
      position: absolute;
      width: 40%;
      height: 18px;
      top: 100%;
    }

    &:after {
      left: 0;
      transform: translateX(40%);
      border-bottom-left-radius: 100%;
    }

    &:before {
      right: 0;
      transform: translateX(-40%);
      border-bottom-right-radius: 100%;
    }
  }

  &__menu {
    padding: 16px 40px 0;
    position: relative;

    @media (max-width: 999px) {
      padding-left: 37px;
      padding-right: 37px;
    }

    &:after {
      content: '';
      bottom: 0;
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      width: calc(100% - 88px);
      border-bottom: var(--borderWidth) solid var(--borderColor);
      display: block;
    }
  }
}
</style>
