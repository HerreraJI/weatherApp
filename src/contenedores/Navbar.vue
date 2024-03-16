<template>
  <nav class="navbar bg-body-tertiary sticky-top">
    <div class="container-fluid">
      <a class="navbar-brand" href="#" id="brand">
        <i class="fa-solid fa-bolt" id="icono"></i>ClimApp
      </a>
      <p class="m-0 fw-bold" id="fecha">{{ fechaFormatted }}</p>
      <h1 class="m-0 fs-2"><i class="fa-solid fa-moon" style="color: #484878"></i> <i class="fa-regular fa-sun"
          style="color: #ffdc9a;"></i></h1>
    </div>
  </nav>
</template>


<script setup>
import { ref } from 'vue';


const fechaArr = new Date().toDateString().split(' ')
let diaFormated = null

switch (fechaArr[0]) {

  case 'Mon':
    diaFormated = "Lunes"
    break;

  case 'Tue':
    diaFormated = "Martes"
    break;

  case 'Wed':
    diaFormated = "Miercoles"
    break;

  case 'Thu':
    diaFormated = "Jueves"
    break;

  case 'Fri':
    diaFormated = "Viernes"
    break;

  case 'Sat':
    diaFormated = "Sabado"
    break;

  case 'Sun':
    diaFormated = "Domingo"
    break;

  default:
    diaFormated = "X"
    break;
}

const fechaFormatted = `${diaFormated} ${fechaArr[2]} ${fechaArr[1]} ${fechaArr[3]}`



// const dia = {
//   mon: "Lunes",
//   tue: "Martes",
//   wed: "Miercoles",
//   thu: "Jueves",
//   fri: "Viernes",
//   sat: "Sabado",
//   sun: "Domingo",
// }

</script>

<style scoped>
#icono {
  color: peru
}

#brand {
  font-weight: 700;
  color: #484878
}
@media (max-width:376px){
  h1{
    display: none;
  }
}
</style>