<template>
    <template v-if="!props.info">
        <h1>Loading info...</h1>
    </template>

    <template v-else>
        <div class="wrapper-all container g-0 gap-3 d-flex">
            <div class="name">
                <h1 class="text-decoration-underline">{{props.info.name}} <i class="fa-solid fa-location-dot"></i></h1>
                <H2><span class="text-decoration-underline">Pais</span><span>: </span>{{ props.info.sys.country }}</H2>
                <h3>{{ props.info.weather[0].description }}</h3>
            </div>

            <div class="wrapper container ">
                <div class="main d-flex justify-content-evenly align-items-center">
                    <div class="icono">
                        <img :src="UrlValue" alt="icono" class="">
                    </div>
                    <div class="temperatura ">{{ props.info.main.temp }}<span class="span">°C</span></div>
                </div>
                <div class="otrosDatos d-flex justify-content-between">
                    <div class="presion d-flex flex-column">
                        <div class="titulo"><i class="fa-solid fa-arrow-down px-2"></i>Presion</div>
                        <div class="valor "> {{ props.info.main.pressure }}HPa</div>
                    </div>
                    <div class="humedad">
                        <div class="titulo"><i class="fa-solid fa-droplet px-2"></i>humedad</div>
                        <div class="valor"> {{ props.info.main.humidity }}%</div>
                    </div>

                    <div class="viento">
                        <div class="titulo"><i class="fa-solid fa-wind px-2"></i> Viento</div>
                        <div class="valor"> {{ Math.round(props.info.wind.speed * 3.6) }}km/h</div>
                    </div>
                </div>
            </div>
        </div>
    </template>
</template>


<script setup>
import { computed } from 'vue';

let props = defineProps({
    info: Object,
})

let codeIcono = ''
let UrlIcono


const UrlValue = computed(() => {
    codeIcono = props.info.weather[0].icon
    UrlIcono = `https://openweathermap.org/img/wn/${codeIcono}@2x.png`

    return UrlIcono
})


</script>


<style scoped>

.wrapper-all{
    color: white;
    flex-wrap: wrap;   
    padding-bottom: 2rem 

}
.wrapper-all .name{
    font-size: large;
    ;
}
.wrapper-all .name span{
    font-size: smaller;
}
.wrapper {
    background: rgb(164, 178, 247);
    background: radial-gradient(circle, rgba(164, 178, 247, 1) 0%, rgba(29, 19, 82, 1) 100%);
    color: white;
    width: fit-content;
    border-radius: 5px;
    border: 1px solid rgb(167, 167, 222);
    padding: 1.3rem;

}

.wrapper .otrosDatos .titulo {
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    border-left: 1px solid white;
    padding: 0px 6px;

}

.wrapper .otrosDatos .valor {
    display: flex;
    justify-content: center;
}

.main {
    font-size: 2.6rem;
    /* border: 1px solid white */
}

.main .temperatura .span {
    font-size: 1.5rem;

}


@media (min-width: 760px) {

    .wrapper {
        padding: 2rem
    }

    .main {
        font-size: 4rem;
        justify-content: space-between;
    }

    .main .temperatura .span {
        font-size: 2.6rem;

    }

    .main .icono img {
        width: 8rem;
    }
}
</style>