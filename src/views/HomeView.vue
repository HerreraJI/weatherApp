<template>
    <div class="wrapper">
        <Navbar />
        <Hero />    
        <Footer />  
        <SubFooter />  
    </div>
</template>


<script setup>
import Navbar from "@/contenedores/Navbar.vue";
import Hero from "../contenedores/Hero.vue";
import Footer from "@/contenedores/Footer.vue";
import SubFooter from "@/contenedores/SubFooter.vue";

</script>

<style scoped>
.wrapper {
    background: rgb(175, 199, 228);
    background: linear-gradient(0deg, rgba(175, 199, 228, 0.5) 0%, rgba(92, 118, 159, 1) 52%, rgba(27, 35, 143, 1) 100%);
}
</style>