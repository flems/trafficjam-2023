<template>
  <div class="banner">
    <space-objects class="banner__space-objects"/>

    <div class="container">
      <div class="banner-announce banner__announce">
        <p class="banner-announce__date">
          <img src="/images/icons/calendar.svg" alt="">
          <span>Июнь-октябрь</span>
        </p>
        <div class="banner-announce banner__announce-wrapper">
          <banner-title />
          <p class="banner-announce__text">Лей на офферы Rafinad — забирай призы!</p>
        </div>
      </div>
      <div class="banner__actions">
        <a href="https://rafinad.io/login/" target="_blank" class="banner__button">Пристыковаться</a>
        <a href="https://rafinad.io/sugar/progress/" target="_blank" class="banner__link">
          <span>Узнать подробнее</span>
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import BannerTitle from './components/Title.vue';
import SpaceObjects from './components/SpaceObjects.vue';
</script>

<style lang="scss">
.banner {
  padding-top: 170px;
  position: relative;

  @media (max-width: 1279px) {
    padding-top: 100px;
  }

  @media (max-width: 767px) {
    padding-bottom: calc(14% + 270px);
  }

  @media (max-width: 479px) {
    padding-bottom: 90%;
  }

  &__space-objects {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    z-index: 2;

    @media (max-width: 767px) {
      z-index: 3;
      pointer-events: none;
      top: 200px;
    }

    @media (max-width: 479px) {
      z-index: 2;
      pointer-events: none;
      top: 20px;
    }
  }

  &__announce {
    pointer-events: none;
    max-width: 410px;
    position: relative;
    z-index: 2;

    @media (max-width: 1279px) {
      max-width: 324px;
    }

    @media (max-width: 999px) {
      max-width: 290px;
    }

    @media (max-width: 767px) {
      max-width: 100%;
    }
  }

  &__announce-wrapper {
    @media (max-width: 767px) {
      display: flex;
      align-items: flex-start;
    }

    @media (max-width: 479px) {
      display: block;
    }
  }

  &__actions {
    position: relative;
    z-index: 5;
    margin-top: 80px;
    pointer-events: none;
    display: flex;
    flex-wrap: wrap;

    @media (max-width: 1279px) {
      margin-top: 40px;
    }

    @media (max-width: 767px) {
      display: none;
    }
  }

  &__button {
    font-family: 'Unbounded', sans-serif;
    font-weight: 700;
    font-size: 20px;
    line-height: 1.4;
    text-align: center;
    text-transform: uppercase;
    text-decoration: none;
    color: #FCFDFD;
    padding: 10px 40px;
    background: #6285FE;
    border: 2px solid #CDD8FF;
    border-radius: 16px;
    cursor: pointer;
    pointer-events: all;
    transition: all 0.2s ease-in;

    @media (max-width: 359px) {
      padding-left: 24px;
      padding-right: 24px;
    }

    &:hover {
      border-color: #FCFDFD;
      box-shadow: 0px 0px 7px #FFFFFF, 0px 0px 20px #0085FF, 0px 0px 20px #0085FF, inset 0px 0px 7px #FFFFFF, inset 0px 0px 20px #00E0FF, inset 0px 0px 20px #00E0FF;
    }
  }

  &__link {
    margin-left: 24px;
    text-decoration: none;
    color: #FDFDFD;
    font-size: 16px;
    display: flex;
    align-items: center;
    pointer-events: all;

    @media (max-width: 999px) {
      display: none;
    }

    span {
      transition: box-shadow 0.2s ease-in;
    }

    &:hover {
      span {
        box-shadow: inset 0 -1px 0 0 currentColor;
      }
    }

    &:before {
      content: '';
      background-image: url("data:image/svg+xml,%3Csvg width='30' height='32' viewBox='0 0 30 32' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M4.74919 0L3.82031 0.628848L6.15648 4.0195C-0.194728 8.61024 -1.89315 17.4299 2.28992 24.0124L3.25119 23.3606C2.05794 21.4533 1.37537 19.3722 1.20682 17.1141V17.1009L1.4121 13.6203V13.6202C1.4121 13.6153 1.4121 13.612 1.41376 13.6071C1.87103 11.2497 2.87904 9.14879 4.4361 7.30924L4.44611 7.29931L7.18974 4.85264C7.19141 4.85099 7.19474 4.84768 7.19808 4.84602C8.72343 3.72773 10.4073 3.06272 12.2498 2.84931C12.2537 2.84931 12.2566 2.84828 12.2602 2.84703L12.2631 2.84601C13.9887 2.34642 15.7444 2.29844 17.5334 2.70043C19.3475 2.97173 20.9663 3.64998 22.3898 4.73684C22.3932 4.74015 22.3965 4.7418 22.4015 4.74346C23.8651 5.51435 25.0767 6.57805 26.0397 7.93124L27.0944 7.2166C26.9559 7.02967 26.8124 6.84439 26.6638 6.66242C22.0494 1.02465 13.9604 -0.485696 7.59193 3.10077C7.42177 3.19668 7.2543 3.29536 7.08953 3.39671L4.74919 0ZM26.6904 8.9131C27.8903 10.8254 28.5779 12.9131 28.7464 15.1778V15.1911L28.5412 18.6717C28.5412 18.6766 28.5412 18.6799 28.5395 18.6849C28.0822 21.0422 27.0742 23.1432 25.5172 24.9827L25.5072 24.9926L22.7635 27.4393C22.7625 27.4403 22.761 27.4418 22.7591 27.4433L22.7573 27.4446L22.7552 27.4459C21.2298 28.5642 19.5459 29.2292 17.7035 29.4426C17.6985 29.4426 17.6952 29.4443 17.6901 29.4459C15.9645 29.9455 14.2089 29.9935 12.4198 29.5915C10.6058 29.3202 8.98697 28.642 7.56341 27.5551C7.56008 27.5518 7.55674 27.5501 7.55173 27.5485C6.08145 26.7743 4.86484 25.704 3.90023 24.3425L2.95898 24.9794C3.08248 25.1432 3.20765 25.3053 3.33782 25.4641C7.95226 31.1019 16.0413 32.6122 22.4097 29.0257C22.6459 28.8927 22.8769 28.7543 23.1027 28.6109L25.4378 32L26.3667 31.3711L24.0264 27.9745C30.2042 23.3683 31.84 14.7032 27.7568 8.19184L26.6904 8.9131ZM16.8323 16.0009C16.8323 16.9548 16.0522 17.728 15.09 17.728C14.1277 17.728 13.3477 16.9548 13.3477 16.0009C13.3477 15.0471 14.1277 14.2739 15.09 14.2739C16.0522 14.2739 16.8323 15.0471 16.8323 16.0009Z' fill='%23FDFDFD'/%3E%3C/svg%3E%0A");
      background-size: contain;
      background-repeat: no-repeat;
      background-position: 50% 50%;
      display: block;
      width: 30px;
      height: 30px;
      margin-right: 16px;
    }
  }
}

.banner-announce {
  .banner-title {
    width: 100%;
    display: block;

    @media (max-width: 767px) {
      max-width: 290px;
      flex-shrink: 0;
      width: 66%;
    }

    @media (max-width: 479px) {
      width: 100%;
      max-width: none;
    }
  }

  &__date {
    color: #fdfdfd;
    font-size: 16px;
    margin-bottom: 10px;
    display: flex;
    align-items: center;

    img {
      margin-right: 12px;
      width: 24px;
      height: 24px;
    }
  }

  &__text {
    font-weight: 500;
    font-size: 24px;
    line-height: 1.40;
    text-transform: uppercase;
    color: #FCFDFD;
    margin-top: 24px;

    @media (max-width: 999px) {
      font-size: 16px;
    }

    @media (max-width: 767px) {
      margin-top: 0;
      padding-left: 16px;
      font-size: 14px;
      max-width: 200px;
    }

    @media (max-width: 479px) {
      margin-top: 10px;
      padding-left: 0;
      max-width: 121px;
    }
  }
}


</style>