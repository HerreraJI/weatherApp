<template>
    <div class="wrapper container-fluid">
        <div class="container d-flex flex-column  justify-content-center" id="contenedor">
            <h1 class="mb-5">¿Cómo está el clima <span>hoy</span>?</h1>
            <form class="container">
                <input v-model="city" placeholder="Ciudad" class="form-control" name="ciudad">
                <button type="submit" class="btn btn-warning my-3" @click.prevent="buscar">Buscar</button>
            </form>
        </div>
        <template v-if="error">
            <p class="error d-flex justify-content-center m-0 pb-3 animate__animated animate__bounce"><i class="fa-solid fa-bolt"></i>{{ errorMessage }}<i
                    class="fa-solid fa-bolt"></i></p>
        </template>

        <template v-if="showdata">
            <Datos :data="datos" />
            <Forecast :city="city"/>
        </template>
    </div>
</template>

<script setup>
import { ref } from 'vue'
import Datos from './Datos.vue'
import Forecast from './Forecast.vue';


let city = ref('');
const datos = ref({})
let error = ref(false)
let showdata = ref(false)
let errorMessage = ref('')

const errorMessageFunction = (errorMe) => {
    errorMessage.value = errorMe
}

const buscar = () => {
    if (!city.value) {
        errorMessageFunction("Debe completar el campo anterior")
        error.value = true
        showdata.value=false

    } else {
        fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city.value}&appid=0368e50aa4107bff3123ec74654cda2c&lang=es&units=metric`)
            .then(resp => resp.json())
            .then(data => {
                if (data.name === undefined) {
                    errorMessageFunction("Ciudad no encontrada")
                    error.value = true
                }
                else {
                    showdata.value = true
                    datos.value = data
                    error.value = false
                }

            })
    }
}


</script>

<style scoped>
#contenedor {
    height: 78vh;
}

.container h1 {
    font-size: 3rem;
    color: white
}

.container h1 span {
    color: purple;
    animation: colores infinite linear 5s;
}

.error {
    color: red;
    font-weight: 700;
}

@keyframes colores {
    0% {
        color: purple
    }

    25% {
        color: green
    }

    50% {
        color: red;
    }

    75% {
        color: yellow
    }
}

@media (min-width: 768px) {
    .container h1 {
        font-size: 4.3rem;
    }
}
</style>