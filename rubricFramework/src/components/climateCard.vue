<script setup>
import { ref } from 'vue'
import { climateData } from '../data/climateData.js'

let openId = ref(false)
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
        <div class="cardContainer" v-if="openId === climateData.id">
            <div class="contentTitle hover" @click="toggle(climateData.id)">
                <h3>{{ climateData.title }}</h3>
                <span class="material-symbols-outlined">remove</span>
            </div>
            <div class="contentText">
                <img :src="climateData.img" alt="">
                <p v-for="description in climateData.description" :key="description">{{ description }}</p>
            </div>
        </div>
        <div class="cardContainer" v-else>
            <div class="contentTitle hover" @click="toggle(climateData.id)">
                <h3>{{ climateData.title }}</h3>
                <span class="material-symbols-outlined">add</span>
            </div>
        </div>
    </article>
</template>

<style scoped>
article{
    display: flex;
    justify-content: center;
}
.cardContainer{
    width: 40vw;
    border: 1px solid black;
    margin: 10px;

    display: flex;
    flex-direction: column;
    justify-content: space-between;
}
.hover{
    padding: 10px;
}
.hover:hover{
    cursor: pointer;
    background-color: lightgreen;
}
.contentTitle{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.contentText{
    display: flex;
    flex-direction: column;
    padding: 10px;
}

p{
    margin-bottom: 1rem;
}

</style>