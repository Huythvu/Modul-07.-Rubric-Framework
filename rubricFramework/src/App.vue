<script setup>
import TheHeader from './components/TheHeader.vue'
import TheFooter from './components/TheFooter.vue'
import ClimateCard from './components/climateCard.vue'
</script>

<template>
  <div class="layout">
    <TheHeader />
    <main>
      <ClimateCard />
    </main>
    <TheFooter />
  </div>
</template>

<style scoped>
.layout{
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  justify-content: space-between;
}
</style>
