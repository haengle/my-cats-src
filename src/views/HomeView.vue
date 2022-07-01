<script setup>
import { myCats } from '../data/cats';
import CardVue from '../components/Card.vue';
</script>

<template>
<header>
    <h1>My cats</h1>
    <a href="/match" class="button">Match Game</a>
  </header>
  <main>
    <section class="cardList">
      <template v-for="cat in myCats" :key="cat.id">
        <CardVue 
        :name="cat.name" 
        :year="cat.yearBorn" 
        :month="cat.monthBorn" 
        :color="cat.color" 
        :image="cat.image"
        :fact="cat.funFact"
        :image-ratio="cat.imageRatio" />
      </template>
    </section>
  </main>
</template>

<style scoped>
  .cardList {
    display: grid;
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  @media screen and (min-width: 768px) {
    .cardList {
      grid-template-columns: 1fr 1fr 1fr;
    }
  }
</style>