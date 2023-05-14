<template>
<div class="timer">
  <p class="timer__title">До старта конкурса:</p>
  <div class="timer__container">
    <span class="timer__number">12</span>
    :
    <span class="timer__number">24</span>
    :
    <span class="timer__number">58</span>
  </div>
  <button class="banner__button">Пристыковаться</button>
</div>
</template>

<script setup>
</script>

<style lang="scss" scoped>
.banner__button {
  display: none;

  @media (max-width: 767px) {
    display: block;
    position: absolute;
    bottom: 113px;
  }
}
.timer {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-weight: 700;
  font-size: 20px;
  line-height: 1.4;
  font-family: 'Unbounded', sans-serif;

  &__title {
    color: #FDFDFD;
    margin-bottom: 4px;
    line-height: 1.25;
    font-weight: 400;
    font-size: 16px;
    font-family: 'Graphik LCG', sans-serif;
  }

  &__container {
    padding: 10px 40px;
    border: 2px solid #6B6B6B;
    border-radius: 16px;
    background: rgba(0, 2, 16, 0.1);
    backdrop-filter: blur(6px);
    display: flex;
    gap: 10px;
  }

  &__number {
    flex-shrink: 0;
    padding: 0 10px;
  }
}
</style>