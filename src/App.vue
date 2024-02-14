<script setup>
  import RickMortySuspense from './components/Suspense.vue';
  import RickMortyCards from './components/RickMortyCards.vue';
  import Hero from './components/Hero.vue';
  import { ref } from 'vue';

  const isRickAndMorty = ref(true);

</script>

<template>
  <main>
    <Hero 
      :isRickAndMorty="isRickAndMorty" 
      @selectShow="isRickAndMorty = !isRickAndMorty"
    />
      <Component :is="isRickAndMorty ? RickMortySuspense : RickMortyCards"></Component>
  </main>
</template>
