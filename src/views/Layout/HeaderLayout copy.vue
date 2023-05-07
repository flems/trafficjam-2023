<template>
  <header class="header">
    <div class="header__container container">
      <div class="header__login"></div>
        <div class="header__logo">
          <span class="header__logo-border-left"></span>
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
  --headerHeight: 32px;
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
    padding: 16px 40px;
    background: var(--headerBg);
    // border-bottom-left-radius: 30px;
    // border-bottom-right-radius: 30px;
    // border: var(--borderWidth) solid var(--borderColor);
    // border-top: none;
    position: relative;

    img {
      position: relative;
      z-index: 2;
    }

    &:after {
      content: '';
      bottom: -5px;
      position: absolute;
      left: 40px;
      width: calc(100% - 40px);
      border-bottom: var(--borderWidth) solid var(--borderColor);
      display: block;
    }

  }

  &__logo-border-left {
    position: absolute;
    top: calc(var(--headerHeight) - var(--borderWidth));
    left: 8px;
    width: 122px;
    height: 40px;
    transform: translateX(-70%);
    overflow: hidden;

    &:before {
      content: '';
      position: absolute;
      width: 100%;
      height: 100%;
      left: 0;
      top: 0;
      display: block;
      background: var(--headerBg);
    }

    &:after {
      content: '';
      --mask: radial-gradient(109.17px at 50% calc(100% + 88px),#0000 calc(99% - 2px),#000 calc(101% - 2px) 99%,#0000 101%) calc(50% - 80px) calc(50% - 31px + 0.5px)/240px 62px repeat-x, radial-gradient(109.17px at 50% -90px,#0000 calc(99% - 2px),#000 calc(101% - 2px) 99%,#0000 101%) -3% calc(50% + 31px)/240px 62px no-repeat;
      -webkit-mask: var(--mask);
      mask: var(--mask);
      position: absolute;
      top: 0;
      left: 0;
      width: 160px;
      height: 40px;
      background: var(--borderColor);


    }
  }

  &__menu {
    display: flex;
    justify-content: flex-end;
  }
}
</style>
