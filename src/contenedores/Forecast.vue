<template>
    <div class="container pb-5">
        <h1 class="pb-3 text-white">Próximos días</h1>

        <div class="container d-flex flex-wrap gap-3">
            <ForecastCard :datos="item" v-for="item in filteredDatelist"/>
        </div>
    </div>

</template>


<script setup>
import ForecastCard from '@/components/ForecastCard.vue';
import { onMounted, ref } from 'vue';

const props = defineProps({
    city: String,
})
onMounted(() => {
    fetchForecast()
})

let filteredDatelist = ref()

async function fetchForecast() {

    const ciudad = props.city
    const url = `https://api.openweathermap.org/data/2.5/forecast?q=${ciudad}&appid=0368e50aa4107bff3123ec74654cda2c&lang=es&units=metric`
    const response = await fetch(url)
    const data = await response.json()

    const list = data.list

    filteredDatelist.value = list.filter(element => {
        const date = new Date(element.dt * 1000)
        const hora = date.getHours()

        if (hora === 12) {
            return element
        }

    })
}

</script>


<style scoped></style>