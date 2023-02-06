<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <div class="justify-center items-center sm:w-1/5 mx-auto">
    <div class="bg-white text-center w-9/12 mx-auto">
      <div class="p-4">
        <p class="font-medium">Yapear a</p>

        <div class="flex items-center border-b border-gray-300 py-2 mt-10">
          <input v-model="nombres"
            class="capi text-center bg-transparent border-none w-full text-fuchsia-800 text-2xl sm:text-sm capitalize mr-3 py-1 px-2 leading-tight focus:outline-none font-medium"
            type="text" placeholder="Nombres completos" aria-label="Full name" />
        </div>

        <div class="flex text-5xl mb-6 text-fuchsia-800 mt-10">
          <input v-model="monto"
            class="appearance-none text-center bg-transparent border-none w-full text-fuchsia-800 mr-3 py-1 px-2 leading-tight focus:outline-none font-medium"
            type="text" placeholder="0" aria-label="0" />
        </div>
      </div>

      <div class="flex items-center border-b border-gray-300 py-2">
        <input v-model="mensaje"
          class="appearance-none text-center bg-transparent border-none w-full text-gray-700 sm:text-xs mr-3 py-1 px-2 leading-tight focus:outline-none font-medium"
          type="text" placeholder="Agregar mensaje" aria-label="Full name" />
      </div>

      <!-- <div class="p-1">
        <button class="bg-[#10cbb4] hover:bg-[#0ea290] rounded m-4 text-center w-full py-1 text-white mt-5 mx-auto">
          Yapear
        </button>
      </div> -->
    </div>
  </div>

  <br>
  <hr>

  <div class="justify-center items-center h-full sm:w-1/5 mx-auto bg-[#742384]">
    <div class="bg-gradient-to-t from-[#742384] to-purple-900">
      <img src="/src/assets/icons/cruzar.png" alt="cerrar" class="w-4 float-left mt-8 ml-5">
      <img src="/src/assets/images/yape.png" alt="logo" class="-mt-10" />
    </div>
 
    <div class="border-top mx-auto mt-0 w-9/12"></div>

    <div class="bg-white text-center w-9/12 mt-0 mx-auto">
      <div class="p-4">
        <h1 class="text-fuchsia-800 text-2xl font-medium mt-2 mb-6">
          ¡Yapeaste!
        </h1>
        <p class="text-5xl mb-6 text-fuchsia-800">
          <span class="text-2xl font-semibold text-[#6d186f52] align-top">S/</span>{{monto}}
        </p>
        <p class="capitalize text-xl font-medium mb-2">{{ nombres }}</p>
        <span class="text-gray-600 font-normal text-sm">{{ fechaActual }}</span>
      </div>
      <p v-if="mensaje" class="mt-6 border-t border-b pt-3 pb-3 text-sm">{{mensaje}}</p>
      <br />
    </div>
    <div class="border-bottom mx-auto w-9/12 rotate-180"></div>
    <div class="flex justify-center mt-6">
      <div class="mr-7">
        <button class="bg-[#9465aa69] py-4 px-4 rounded-xl text-white ml-2">
          <img src="/src/assets/icons/compartir.png" alt="compartir" class="w-5" />
        </button>
        <p class="text-white text-xs mt-2 ml-1 font-medium">Compartir</p>
      </div>
      <div class="">
        <button class="bg-[#10cbb4] py-4 px-4 rounded-xl text-white ml-2">
          <img src="/src/assets/icons/nuevo.png" alt="nuevo yapeo" class="w-5" />
        </button>
        <p class="text-white text-xs mt-2 font-medium">Nuevo Yapeo</p>
      </div>
    </div>
    <br>
  </div>
</template>

<script>


export default {
  name: 'AppComponent',
  data: () => ({
    monto: "",
    nombres: "",
    fechaActual: "",
    mensaje: "",
  }),
  mounted() {
    var fecha = new Date();
    var dia = ("0" + fecha.getDate()).slice(-2);
    var meses = ["Ene", "Feb", "Mar", "Abr", "May", "Jun", "Jul", "Ago", "Sep", "Oct", "Nov", "Dic"];
    var mesAbreviado = meses[fecha.getMonth()];
    var anio = fecha.getFullYear();
    var hora = ("0" + fecha.getHours()).slice(-2);
    var minutos = ("0" + fecha.getMinutes()).slice(-2);
    var segundos = ("0" + fecha.getSeconds()).slice(-2);
    this.fechaActual = dia + " " + mesAbreviado + "." + " " + anio + " " + hora + ":" + minutos + ":" + segundos;
  },

};
</script>

<style>


 .border-top {
        position: relative;
        padding: 8px 8px 32px 8px;
    }

    .border-top:after {
        background: linear-gradient(-50deg, #ffffff 16px, transparent 0),
            linear-gradient(50deg, #ffffff 16px, transparent 0);
        background-position: left-bottom;
        background-repeat: repeat-x;
        background-size: 8px 32px;
        content: "";
        display: block;
        position: absolute;
        bottom: 0px;
        left: 0px;
        width: 100%;
        height: 32px;
    }

    .border-bottom {
        position: relative;
        padding: 8px 8px 32px 8px;
    }

    .border-bottom:after {
        background: linear-gradient(-50deg, #ffffff 16px, transparent 0),
            linear-gradient(50deg, #ffffff 16px, transparent 0);
        background-repeat: repeat-x;
        background-size: 8px 32px;
        content: "";
        display: block;
        position: absolute;
        bottom: 0px;
        left: 0px;
        width: 100%;
        height: 15px;
    }
</style>
