<template>
    <div v-if="!dats">Loading...</div>
    <div class="container card d-flex  p-3 text-center" style="width: 12rem;" v-else>

        <div class="day card-title py-2"><i class="fa-regular fa-calendar-days"></i> <span class="mx-2"> {{ fecha }}</span>
        </div>
        <div class="card-body ">
            <div class="temp card-title"><i class="fa-solid fa-temperature-high"></i> {{ dats.main.temp }}°C<span
                    class="mx-2"></span></div>
            <div class="humidity card-title"><i class="fa-solid fa-droplet"></i> <span class="mx-2">{{
        dats.main.humidity }}%</span></div>
            <div class="icono card-title"><img :src="URLIconValue" alt="Icono"></div>
            <div class="description">{{ dats.weather[0].description }}</div>
        </div>
    </div>

</template>


<script setup>
import { computed } from 'vue';

const props = defineProps({
    datos: Object
})


const dats = computed(() => props.datos)


const URLIconValue = computed(() => {
    const IconoCode = dats.value.weather[0].icon
    const URLIcon = `https://openweathermap.org/img/wn/${IconoCode}@2x.png`
    return URLIcon
})

const fecha = computed(() => {
    const date = new Date(dats.value.dt * 1000)
    const dia = date.getDate()
    const mes = date.getMonth()
    const formatedDay = `${dia}/${mes + 1}`
    return formatedDay
})

</script>


<style scoped>
.card {
    background-color: rgb(40, 40, 40);
    color: white;
    box-shadow: 4px 4px 8px black;
}

.day {
    border-bottom: 1px solid;
}
</style>