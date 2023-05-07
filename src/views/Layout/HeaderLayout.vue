<template>
  <header class="header">
    <div class="header__container container">
      <div class="header__login"></div>
        <div class="header__logo">
          <div class="header__logo-borders">
            <span class="header__logo-border-top-left"></span>
            <span class="header__logo-border-bottom-left"></span>
          </div>
          <div class="header__logo-borders header__logo-borders--right">
            <span class="header__logo-border-top-left"></span>
            <span class="header__logo-border-bottom-left"></span>
          </div>
          <img src="/images/logo.svg" alt="Rafinad">
        </div>
        <div class="header__menu">
          <img src="/images/icons/menu.svg" alt="">
        </div>
    </div>
  </header>
</template>

<script setup>

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
  position: relative;

  &__container {
    display: flex;
  }

  &:before {
    content: '';
    width: 100%;
    height: var(--headerHeight);
    top: 0;
    pointer-events: none;
    z-index: -1;
    left: 0;
    position: absolute;
    background: var(--headerBg);
    border-bottom: var(--borderWidth) solid var(--borderColor);
  }

  &__login,
  &__menu {
    width: 50%;
  }

  &__logo {
    flex-shrink: 0;
    padding: 16px 80px 16px;
    background: var(--headerBg);
    position: relative;
    height: 56px;

    img {
      position: relative;
      z-index: 2;
      height: 28px;
      width: auto;
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

  &__logo-border-top-left,
  &__logo-border-bottom-left {
    overflow: hidden;
  }

  &__logo-border-top-left {
    position: absolute;
    top: 0;
    left: 0;
    display: block;
    height: 50%;
    width: 50%;

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

  &__menu {
    display: flex;
    justify-content: flex-end;
  }
}
</style>
