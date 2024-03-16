<template>
    <template v-if="!props.data.main">
        <h1 class="d-flex espera justify-content-center m-0">***</h1>
    </template>

    <template v-else>
            <div class="container">
                <Current :info="props.data" />
            </div>
        </template>
</template>

<script setup>
import { ref } from 'vue';
import Current from '../components/Current.vue'

const props = defineProps({
    data: Object,
})

const estado = ref(true)


</script>

<style scoped>
.espera {
    color: white
}
</style>