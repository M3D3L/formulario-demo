<template>
  <body class="flex flex-col justify-center w-full h-screen text-white bg-center bg-cover">
    <div class="flex justify-center">
      <img class="absolute w-24 h-16 md:h-32 md:w-36 md:top-10 top-5" src="../assets/img/logo.png" alt="">
    </div>
    <div class="w-full h-3/5">
    <!--cstm-gradient class compuesto de tailwind favor de mirar abajo-->
      <div class="flex flex-col w-full h-full mx-auto my-auto xl:w-1/2 lg:w-3/4 md:w-4/5 md:flex-row">
        <div class="relative flex flex-col justify-center w-full h-full py-4 rounded-l-lg rounded-r-lg md:rounded-r-none md:w-1/2 cstm-gradient md:overflow-y-hidden md:py-0">
          <span class="flex justify-center w-full space-x-4 md:absolute md:top-10">
            <base-circle placeholder="01" color="bg-gradient-to-b from-blue-500 via-blue-400 to-blue-300 border border-white"></base-circle>
            <base-circle placeholder="02"></base-circle>
            <base-circle placeholder="03"></base-circle>
            <base-circle placeholder="04"></base-circle>
          </span>
          <span class="w-full md:absolute md:top-32">
            <h1 class="text-xl font-bold text-center">
              Información Personal
            </h1>
          </span>

          <h2 class="flex justify-center w-full text-center md:absolute md:top-56">
            Ingrese sus datos personales para agendar <br> una cita.
          </h2>
          <h3 class="flex justify-center w-full text-center md:absolute md:top-96 md:mt-24">
            5555-555-555 <br>
            info@ejemplo.com
          </h3>
        </div>
        <div class="z-0 w-full px-8 bg-white bg-opacity-25 rounded-l-lg rounded-r-lg md:overflow-y-hidden md:h-full md:w-1/2 md:rounded-l-none filter backdrop-blur-3xl backdrop-filter">
          <form class="space-y-6" @submit.prevent="submitFunction">
            <base-input :v-model="nombreCompleto" class="mt-6 md:mt-10"  type="text" placeholder="Nombre Completo"></base-input>
            <base-input :v-model="curp" type="text" placeholder="CURP"></base-input>
            <base-input :v-model="dirección" type="address" placeholder="Dirección"></base-input>
            <base-input v-model="email" type="email" placeholder="Correo electrónico"></base-input>
            <base-input v-model="contraseña" type="password" placeholder="Contraseña"></base-input>
            <base-input v-model="confirmarContraseña" type="password" placeholder="Confirmar contraseña"></base-input>
            <base-input v-model="tipoDeConsulta" type="text" placeholder="Tipo de consulta"></base-input>
          </form>
          <span class="flex mt-2">
            <input @click="aceptoAviso=!aceptoAviso" class="mt-2 cursor-pointer " type="checkbox"   >
            <p class="ml-2 font-bold">
              Acepto aviso de privacidad
            </p>
          </span>
          <span class="flex justify-center w-full py-4">
            <button class="w-32 h-8 font-bold text-white rounded-lg cstm-gradient md:mb-2" @click="submitForm">
            Siguiente
          </button>
          </span>

        </div>
      </div>
    </div>
    <div class="absolute flex justify-end w-full top-5 h-42 md:top-96 md:mt-96">
      <span class="w-12 h-12 mb-8 mr-8 rounded-full cursor-pointer md:h-24 md:w-24 bg-500 cstm-gradient">
        <svg class="h-12 mx-auto md:mt-2 " viewBox="0 0 16 16">
          <path d="M8 2A4 4 0 0 0 4 6H5A3 3 0 0 1 8 3 3 3 0 0 1 11 6 3 3 0 0 1 8 9H7V12H8V10A4 4 0 0 0 12 6 4 4 0 0 0 8 2M7 13V14H8V13H7" fill="white"/>
        </svg>
        <p class="text-center text-white ">
          Ayuda
        </p>
      </span>
    </div>
  </body>
</template>

<script>
import BaseCircle from '../components/BaseCircle.vue'
import BaseInput from '../components/BaseInput.vue'
export default {
  components: {
    BaseCircle,
    BaseInput },
    data(){
      return{
        nombreCompleto: '',
        curp: '',
        dirección: '',
        email: '',
        contraseña: '',
        confirmarContraseña: '',
        tipoDeConsulta: '',
        aceptoAviso: false,
      }
    },
    methods:{
      submitForm (event) {
        if (this.aceptoAviso !== false) {
        this.$axios.post('https://imoneymexico.com:58000/stores/get/all/', {
          nombreCompleto: this.nombreCompleto,
          curp: this.curp,
          dirección: this.dirección,
          email: this.email,
          contraseña: this.contraseña,
          confirmarContraseña: this.confirmarContraseña,
          tipoDeConsulta: this.tipoDeConsulta
        }).then(response => {
          console.log(response);
        }).catch(error => {
          console.log(error);
        })
        }else alert('Acepta el aviso para continuar')
      }
    }
    }
</script>

<style>
  body {
  background-image: url('../assets/img/bg.jpg');
  }
  /*Css class compuesto de tailwind*/
  .cstm-gradient {
    @apply bg-gradient-to-b from-blue-500 to-blue-400;
  }
</style>
