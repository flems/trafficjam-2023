<template>
  <div
    class="prizes-step"
    :class="{
      'prizes-step--active': progress !== '0',
      'prizes-step--last': last
    }"
  >
    <div class="prizes-step__icon">
      <ui-icon :name="progress !== '0' && activeIcon ? activeIcon : icon" />
    </div>
    <div class="prizes-step__container">
      <div class="prizes-step__number">
        <number
          :theme="theme"
          :active="progress !== '0'"
          :text="text"
          :highlighted-text="highlightedText"
        >{{ name }}</number>
      </div>
      <div class="prizes-step__progress" v-if="!last">
        <div
          class="prizes-step__bar"
          :class="`prizes-step__bar--progress-${progress}`"
        ></div>
        <div class="prizes-step__score">
          <span v-html="score"></span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import Number from '@/components/Number'
import UiIcon from '@/components/UiIcon'

defineProps({
  icon: String,
  activeIcon: String,
  name: String,
  score: String,
  theme: {
    type: String,
    default: 'black',
    validator: prop => ['black', 'blue'].includes(prop)
  },
  last: Boolean,
  text: Boolean,
  progress: {
    type: String,
    default: '0',
    validator: prop => ['0', '5', '85', '100'].includes(prop)
  },
  highlightedText: {
    type: Boolean,
    default: false
  }
})
</script>

<style lang="scss">
$transition: 0.1s linear;
$transitionWidth: 0.25s linear 0s;

.prizes-step {
  $parent: &;

  &__container {
    display: flex;
    align-items: flex-start;

    @media (max-width: 1279px) {
      align-items: flex-end;
    }
  }

  &__icon {

    height: 40px;
    width: max-content;
    margin-bottom: 12px;
    margin-left: 32px;

    @media (max-width: 1279px) {
      margin-left: 24px;
    }

    @media (max-width: 767px) {
      margin-left: 14px;
    }

    svg {
      width: auto;
      height: 100%;
      stroke: #6B6B6B;
      transition: all $transition;
      
      path {
        stroke: inherit;
      }
    }
  }

  &__number {
    flex-shrink: 0;
  }

  &__progress {
    flex-grow: 1;
    position: relative;
    margin-top: 44px;

    @media (max-width: 1279px) {
      margin-top: 0;
    }
  }

  &__bar {
    background: #000210;
    border: 2px solid rgba(252, 253, 253, 0.1);
    height: 16px;
    width: 100%;
    border-radius: 18px;
    position: relative;

    &:after {
      content: '';
      position: absolute;
      width: 0%;
      height: 100%;
      border-radius: 16px;
      border: 2px solid #FCFDFD;
      box-shadow: 0px 0px 7px #FFFFFF, 0px 0px 20px #0085FF, 0px 0px 20px #0085FF, inset 0px 0px 7px #FFFFFF, inset 0px 0px 20px #00E0FF, inset 0px 0px 20px #00E0FF;
      transition: width $transitionWidth, opacity 0.1s linear 0.1s;
    }

    &--progress-0,
    &--progress-5 {
      &:after {
        opacity: 0;
      }
    }

    &--progress-85 {
      &:after {
        width: 85%;
      }
    }
    
    &--progress-100 {
      &:after {
        width: 100%;
      }
    }
  }

  &__score {
    font-family: 'Unbounded', sans-serif;
    font-weight: 500;
    font-size: 16px;
    line-height: 1.4;
    margin-top: 16px;
    padding-left: 6px;
    padding-right: 6px;
    display: flex;
    justify-content: center;
    align-content: center;

    @media (max-width: 1279px) {
      margin-top: 10px;
      font-size: 14px;
    }

    @media (max-width: 767px) {
      font-size: 10px;
    }

    &:after {
      content: '';
      display: block;
      width: 24px;
      height: 28px;
      flex-shrink: 0;
      background-image: url("data:image/svg+xml,%3Csvg width='25' height='28' viewBox='0 0 25 28' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M11.9357 0.154705C12.2847 -0.0515682 12.7134 -0.0515682 13.0608 0.154705L23.8798 6.54739C23.8977 6.5567 23.9154 6.56653 23.9329 6.57688L23.9374 6.57995C24.2849 6.78623 24.5 7.16645 24.5 7.57745V20.4233C24.5 20.8343 24.2849 21.2145 23.9374 21.4208L13.6289 27.512L13.0928 27.8272L13.0817 27.8341L13.0618 27.8461C12.7128 28.0523 12.2841 28.0508 11.9352 27.8445L1.06409 21.4208C0.715105 21.2145 0.5 20.8343 0.5 20.4218V7.57592C0.50024 7.51009 0.505915 7.44505 0.516729 7.38139C0.57281 7.04757 0.77127 6.75164 1.0631 6.57841L11.9357 0.154705ZM13.6291 24.843L13.6276 14.6664L22.2423 9.57726V19.7554L13.6291 24.843Z' fill='%23FDFDFD'/%3E%3C/svg%3E%0A");
      background-size: contain;
      background-repeat: no-repeat;
      background-position: 50% 50%;
      margin-left: 16px;
      margin-top: -0.2em;

      @media (max-width: 1279px) {
        margin-left: 8px;
        width: 22px;
        height: 26px;
      }

      @media (max-width: 767px) {
        width: 16px;
        height: 18px;
      }
    }
  }

  &--active {
    #{$parent}__icon {
      .ui-icon {
        filter: drop-shadow(0px 0px 7px #FFFFFF) drop-shadow(0px 0px 20px rgba(0, 133, 255, 1));
        stroke: #a3f3ff;
      }
    }
  }
}
</style>