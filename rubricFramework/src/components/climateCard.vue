<script setup>
import { ref } from 'vue'
import { climateData } from '../data/climateData.js'

const openId = ref(false)
const toggle = (stateId) => {
  if (openId.value === stateId) {
    // clicked the one that’s already open → close it
    openId.value = false
  } else {
    // clicked a different one → open that one
    openId.value = stateId
  }
}

</script>

<template>
    <article v-for="climateData in climateData" :key="climateData.id">
        <div class="cardContainer" @click="toggle(climateData.id)" v-if="openId === climateData.id">
            <div class="contentContainer">
                <h3>{{ climateData.title }}</h3>
                <img :src="climateData.img" alt="">
                <p v-for="description in climateData.description" :key="description">{{ description }}</p>
            </div>
                <p><strong>+</strong></p>
        </div>
        <div class="cardContainer" @click="toggle(climateData.id)" v-else>
            <div class="contentContainer">
                <h3>{{ climateData.title }}</h3>
            </div>
            <p><strong>-</strong></p>
        </div>
    </article>
</template>

<style scoped>
.cardContainer{
    border: 1px solid black;
    margin: 10px;
    padding: 10px;
    gap: 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
p{
    margin-bottom: 1rem;
}
</style>