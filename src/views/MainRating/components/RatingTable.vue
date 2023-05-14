<template>
  <div class="rating-table" v-if="data && data.length">
    <table class="rating-table__table">
      <thead class="rating-table__head">
        <th class="rating-table__cell rating-table__cell--head"></th>
        <th class="rating-table__cell rating-table__cell--head">Место</th>
        <th class="rating-table__cell rating-table__cell--head">UID</th>
        <th class="rating-table__cell rating-table__cell--head">Прогресс</th>
        <th class="rating-table__cell rating-table__cell--head">Уровень</th>
      </thead>
      <tbody>
        <tr
          v-for="(item, index) in data"
          :key="index"
        >
          <td class="rating-table__cell">
            <span
              class="rating-table__trend"
              :class="{ 'rating-table__trend--down': item.prev_position < item.id }"
              v-if="item.prev_position !== item.id"
            ></span>
          </td>
          <td class="rating-table__cell">
            <span v-html="item.id"></span>
          </td>
          <td class="rating-table__cell">
            <span v-html="item.sugar_id"></span>
          </td>
          <td class="rating-table__cell">
            <span v-html="`${item.percentage}%`"></span>
          </td>
          <td class="rating-table__cell">
            <progress-bar :data="item" />
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import ProgressBar from './ProgressBar.vue'

defineProps({
  data: {
    type: Array,
    default: () => []
  }
})
</script>

<style lang="scss">
.rating-table {
  &__trend {
    background-repeat: no-repeat;
    background-size: contain;
    background-position: 50% 50%;
    width: 50px;
    height: 50px;
    display: block;
    background-image: url(/images/main-page/trend-up.png);
    margin: 0 auto;
    
    &--down {
      background-image: url(/images/main-page/trend-down.png);
    }
  }

  &__table {
    width: 100%;
  }

  &__head {
    border-top: 0;
    position: relative;
    
    &:after {
      content: '';
      width: 100%;
      position: absolute;
      height: 100%;
      display: block;
      top: 0;
      left: -2px;
      left: 0;
      border: 2px solid #6B6B6B;
      border-radius: 16px;
      z-index: 1;
    }
  }

  &__cell {
    width: 5%;
    text-align: left;
    padding: 14px 8px;
    color: #FDFDFD;
    font-weight: 500;
    vertical-align: middle;

    &:first-child {
      padding-left: 40px;
    }

    &:last-child {
      width: 80%;
      padding-right: 40px;
    }

    &--head {
      font-weight: 600;
      font-size: 14px;
      line-height: 1.2;
      letter-spacing: -0.01em;
      color: #6B6B6B;
      padding: 32px 8px 20px;
      min-width: 80px;
    }
  }
}
</style>