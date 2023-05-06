<template>
  <div class="main-page">
    main page

    <banner />
    
    <number />


    <card>
      <template v-slot:label>Safepal</template>
      <template v-slot:content>
        <h2>Название компании</h2>
        <p>Ты гарантированно получаешь приз, достигнув чек-поинта, больше трафика – круче приз, поэтому неважно когда Ты подключился в игру и кто сегодня в ТОПе! После прохождения всех уровней. Ты попадаешь в ТОП, где среди первых 10 участников будет разыгран призовой фонд в 2,5 млн рублей!</p>
      </template>
    </card>
  </div>
</template>

<script setup>
import Banner from "./components/MpBanner.vue";
import Card from "@/components/Card"
import Number from '@/components/Number'

</script>

<style scoped>
.main-page {
  
}
</style>
