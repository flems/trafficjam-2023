<template>
  <div class="main-page">
    <banner />
    <div class="container">

    </div>

    <!-- 
    
    <number />


    <card
      logo="/images/logos/safepal.svg"
      title="Название компании"
      tag-icon="/images/icons/universe.svg"
    >
      <template v-slot:content>
        <p>Ты гарантированно <b>получаешь приз</b>, достигнув чек-поинта, <b>больше трафика – круче приз</b>, поэтому неважно когда Ты подключился в игру и кто сегодня в ТОПе! После прохождения всех уровней. Ты попадаешь в ТОП, где среди первых 10 участников будет разыгран призовой фонд в 2,5 млн рублей!</p>
      </template>
    </card>

    <br><br>

    <img src="/images/icons/universe.png" alt="">

    <card
      logo="/images/logos/safepal.svg"
      title="Название компании"
      tag-icon="/images/icons/star.svg"
      theme="black"
    >
      <template v-slot:content>
        <p>Ты гарантированно <b>получаешь приз</b>, достигнув чек-поинта, <b>больше трафика – круче приз</b>, поэтому неважно когда Ты подключился в игру и кто сегодня в ТОПе! После прохождения всех уровней. Ты попадаешь в ТОП, где среди первых 10 участников будет разыгран призовой фонд в 2,5 млн рублей!</p>
      </template>
    </card> -->
  </div>
</template>

<script setup>
import Banner from "@/views/MainBanner/MainBanner.vue";
import Card from "@/components/Card"
import Number from '@/components/Number'

</script>

<style scoped>
.main-page {
  /* padding: 50px; */
  background-image: url(/images/main-page/stars.png) 0 0;
  height: 3600px;
  background-size: auto auto;
  background-position: 50% 0px;
  background-repeat: repeat no-repeat;
  position: relative;
  overflow: hidden;
}
</style>
