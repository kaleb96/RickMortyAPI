<script setup>
    import BreakingBadCard from './BreakingBadCard.vue';

</script>

<template>
    <Suspense>
      <template #default>
        <BreakingBadCard/>
      </template>
      <template #fallback>
        <div class="cards">
          <n-spin size="large"/>
        </div>
      </template>
    </Suspense>
</template>

<style scoped>

  .cards {
    height: 700px;
    background-color: rgb(27, 26, 26);
    display: flex;
    justify-content: center;
    align-items: center;
  }


</style>