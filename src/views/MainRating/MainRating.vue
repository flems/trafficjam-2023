<template>
  <div class="mp-rating" v-if="data && data.length">
    <div class="container mp-rating__wrapper">
      <h2>ТОП участников</h2>
      <div class="mp-rating__container">

        <rating-table :data="data" />
        <span class="mp-rating__decor mp-rating__decor--top-left rating-decor"></span>
        <span class="mp-rating__decor mp-rating__decor--top-right rating-decor"></span>
        <span class="mp-rating__decor mp-rating__decor--bottom-right rating-decor"></span>
        <span class="mp-rating__decor mp-rating__decor--bottom-left rating-decor"></span>
      </div>
    </div>
  </div>
</template>

<script setup>
import RatingTable from './components/RatingTable.vue'
import { ref, onBeforeMount } from 'vue'

const data = ref([])

const getData = () => {
  fetch('https://rafinad.io/api/v1/bonuspoint/top_data/',
    {
      headers: {
        'Authorization': 'Token 0042287fbcd916971408c84312cdebc668c00b38',
      },
      method: "POST"
    })
    .then(res => {
      data.value = res
    })
    .catch(error => {
      console.error(error);

      data.value = [
        {
            "user_id": 9353,
            "id": 1,
            "sugar_id": "k10307",
            "lvl": 4,
            "percentage": 25,
            "prev_position": 322,
            "count": 5089.27
        },
        {
            "user_id": 9354,
            "id": 2,
            "sugar_id": "k10307",
            "lvl": 4,
            "percentage": 100,
            "prev_position": 3,
            "count": 5089.27
        },
        {
            "user_id": 9355,
            "id": 3,
            "sugar_id": "k10307",
            "lvl": 2,
            "percentage": 63,
            "prev_position": 2,
            "count": 5089.27
        },
        {
            "user_id": 93556,
            "id": 4,
            "sugar_id": "k10307",
            "lvl": 1,
            "percentage": 63,
            "prev_position": 4,
            "count": 5089.27
        },
        {
            "user_id": 93556,
            "id": 5,
            "sugar_id": "k10307",
            "lvl": 1,
            "percentage": 63,
            "prev_position": 2,
            "count": 5089.27
        },
        {
            "user_id": 9354,
            "id": 6,
            "sugar_id": "k10307",
            "lvl": 4,
            "percentage": 100,
            "prev_position": 3,
            "count": 5089.27
        },
        {
            "user_id": 9355,
            "id": 7,
            "sugar_id": "k10307",
            "lvl": 2,
            "percentage": 63,
            "prev_position": 2,
            "count": 5089.27
        },
        {
            "user_id": 93556,
            "id": 8,
            "sugar_id": "k10307",
            "lvl": 1,
            "percentage": 63,
            "prev_position": 4,
            "count": 5089.27
        },
        {
            "user_id": 93556,
            "id": 9,
            "sugar_id": "k10307",
            "lvl": 1,
            "percentage": 63,
            "prev_position": 2,
            "count": 5089.27
        },
        {
            "user_id": 9353,
            "id": 10,
            "sugar_id": "k10307",
            "lvl": 4,
            "percentage": 25,
            "prev_position": 322,
            "count": 5089.27
        },
    ]
    })
}

onBeforeMount(() => {
  getData()
})
</script>

<style lang="scss">
.rating-decor {
  position: relative;
  display: block;
  height: 24px;
  background-image: url("data:image/svg+xml,%3Csvg width='13' height='24' viewBox='0 0 13 24' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1 0V12M1 24V12M1 12H13' stroke='%23FDFDFD' stroke-width='2'/%3E%3C/svg%3E%0A"), url("data:image/svg+xml,%3Csvg width='12' height='24' viewBox='0 0 12 24' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M12 0V12M12 24V12M12 12H-1.19209e-07' stroke='%23FDFDFD' stroke-width='2'/%3E%3C/svg%3E%0A");
  background-repeat: no-repeat, no-repeat;
  background-size: contain, contain;
  background-position: 0% 50%, 100% 50%;

  &:after {
    content: '';
    width: 100%;
    height: 2px;
    width: calc(100% - 12px*2);
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: #6B6B6B;
  }
}

.mp-rating {
  &__wrapper {
    position: relative;

    &:after {
      content: '';
      background-image: url('/images/main-page/bg-2.svg');
      width: 800px;
      height: 400px;
      display: block;
      position: absolute;
      top: -12%;
      left: 60%;
      background-repeat: no-repeat;
      background-position: 50% 50%;
      background-size: contain;
    }
  }

  &__container {
    border-radius: 16px;
    position: relative;
    padding-bottom: 26px;
    background: rgba(0, 2, 16, 0.5);
    margin-bottom: 20px;
    
    &::after {
      content: '';
      border-radius: 16px;
      position: absolute;
      display: block;
      box-shadow: 0px 0px 7px #FFFFFF, 0px 0px 20px #0085FF, 0px 0px 20px #0085FF, inset 0px 0px 7px #FFFFFF, inset 0px 0px 20px #00E0FF, inset 0px 0px 20px #00E0FF;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 3;
      pointer-events: none;
      border: 2px solid #FCFDFD;
    }
  }

  &__decor {
    position: absolute;
    width: calc(((100vw - 100%) / 2) - 22px);

    &--top-left {
      top: 0;
      right: calc(100% + 12px);
    }
    
    &--top-right {
      top: 0;
      left: calc(100% + 12px);
    }

    &--bottom-left {
      bottom: 0;
      right: calc(100% + 12px);
    }

    &--bottom-right {
      bottom: 0;
      left: calc(100% + 12px);
    }
  }
}


</style>