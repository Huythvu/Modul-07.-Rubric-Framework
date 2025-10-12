<script setup>
// Import af ref fra Vue og data fra min climateData.js fil
import { ref } from 'vue'
import { climateData } from '../data/climateData.js'

// Variabel til at holde styr på cardets state false alle lukket og hvis et id er valgt er det åbent (id = 2 så er card med id 2 åbent)
let openId = ref(false)
// Her laves der en toggle funktion som skifter state når der klikkes på cardet
// Der tjekkes om openId er lig med stateId (hvilket betyder der er et open card) så sættes openId til false hvilket lukker cardet.
// Og omvendt hvis de ikke matcher så sættes openId til stateId hvilket åbner det valgte card.
const toggle = (stateId) => {
  if (openId.value === stateId) {
    openId.value = false
  } else {
    openId.value = stateId
  }
}

</script>

<template>
    <!-- Vi kører en v-for loop over climateData -->
    <article v-for="data in climateData" :key="data.id">
        <!-- Her bruges der en if statement der tjekker om openId er lig med data.id og viser alt content af cardet hvis opfyldt condition. -->
        <div class="cardContainer" v-if="openId === data.id">
            <!-- Her bruges der en click event til at toggle cardet, vi kigger på hvilken data.id det er og sender det til toggle funktionen -->
            <div class="contentTitle hover" @click="toggle(data.id)">
                <!-- Her vises titlen på cardet gennem reference -->
                <h3>{{ data.title }}</h3>
                <!-- Ikon fra google icons -->
                <span class="material-symbols-outlined">remove</span>
            </div>
            <div class="contentText">
                <!-- Her bruges der forkortelsen : for v-bind der binder data.img til src attributten -->
                <img :src="data.img" alt="">
                <!-- Her bruges en v-for loop fordi min data.description er et array af text-->
                <p v-for="description in data.description" :key="description">{{ description }}</p>
            </div>
        </div>
        <!-- Her bruges der en else statement til at vise det lukkede state af cardet -->
        <div class="cardContainer" v-else>
            <div class="contentTitle hover" @click="toggle(data.id)">
                <h3>{{ data.title }}</h3>
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