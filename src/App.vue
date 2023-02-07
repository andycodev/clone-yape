<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <div class="justify-center h-screen items-center sm:w-1/5 mx-auto  bg-gray-50">
    <div class="bg-gray-50 text-center w-9/12 mx-auto">
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

      <div class="p-1">
        <button v-if="!generate"
          class="bg-[#10cbb4] rounded m-4 text-center w-full py-3 text-white mt-5 mx-auto font-medium"
          @click="generateVoucher()" :disabled="monto === '' || monto === '0' || nombres === ''"
          :class="[(monto === '' || monto < 0.10 || nombres === '') ? 'bg-gray-300' : '']">
          Yapear
        </button>

        <button v-else class="bg-[#10cbb4] rounded m-4 text-center w-full py-3 text-white mt-3 mx-auto font-medium"
          @click="clearVoucher()" :disabled="monto === '' || monto === '0' || nombres === ''"
          :class="[(monto === '' || monto < 0.10 || nombres === '') ? 'bg-gray-300' : '']">
          Nuevo yapeo
        </button>
      </div>

      <div v-if="generate && monto != 0"
        class="bg-teal-100 text-left border-t-4 border-teal-500 rounded-b text-teal-900 px-4 py-3 shadow-md"
        role="alert">
        <div class="flex">
          <div class="py-1"><svg class="fill-current h-6 w-6 text-teal-500 mr-4" xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 20 20">
              <path
                d="M2.93 17.07A10 10 0 1 1 17.07 2.93 10 10 0 0 1 2.93 17.07zm12.73-1.41A8 8 0 1 0 4.34 4.34a8 8 0 0 0 11.32 11.32zM9 11V9h2v6H9v-4zm0-6h2v2H9V5z" />
            </svg></div>
          <div>
            <p class="font-bold sm:text-xs">Voucher generado con éxito!.</p>
            <p class="text-sm sm:text-xs">Po favor, deslice hacia abajo para visualizar el voucher 😎.</p>
          </div>
        </div>
      </div>

      <div v-if="generate && monto != 0"
        class="items-center bg-fuchsia-800 mt-2 rounded text-white text-sm font-normal px-4 py-3 text-left"
        role="alert">
        <p class="font-semibold sm:text-xs">Importante</p>
        <p class="font-normal sm:text-xs">Puede editar los valores, sin necesidad de generar un nuevo yapeo.</p>
      </div>

    </div>
  </div>

  <hr>

  <div class="justify-center items-center h-screen sm:w-1/5 mx-auto bg-[#742384]">
    <!-- <div class="bg-gradient-to-t from-[#742384] to-purple-900"> -->
    <!-- <img src="/src/assets/icons/cruzar.png" alt="cerrar" class="w-4 float-left mt-8 ml-5 bg-yellow-300">
      <img src="/src/assets/images/yape.png" alt="logo" class="-mt-16 bg-gray-400" /> -->
    <!-- </div> -->
    <div class="grid grid-cols-12 justify-center mx-auto text-center bg-gradient-to-t from-[#742384] to-purple-900">
      <div class="col-span-1 float-left">
        <img src="/src/assets/icons/cruzar.png" alt="cerrar" class="w-3 float-left mt-8 ml-5">
      </div>
      <div class="col-span-12 text-center mx-auto mt-16">
        <img src="/src/assets/images/yape.png" alt="logo" class="-mt-16" />
      </div>
    </div>

    <div class="border-top mx-auto mt-0 w-9/12"></div>

    <div class="bg-white text-center w-9/12 mt-0 mx-auto">
      <div class="p-4">
        <h1 class="text-fuchsia-800 text-2xl font-medium mt-2 mb-6">
          ¡Yapeaste!
        </h1>
        <p class="text-5xl mb-6 text-fuchsia-800">
          <span class="text-2xl font-semibold text-[#6d186f52] align-top">S/</span>{{ monto }}
        </p>
        <p class="capitalize text-xl font-medium mb-2">{{ nombres }}</p>
        <span class="text-gray-600 font-normal text-sm">{{ fechaActual }}</span>
      </div>
      <p v-if="mensaje" class="mt-6 border-t border-b pt-3 pb-3 text-sm">{{ mensaje }}</p>
      <br />
    </div>
    <div class="border-bottom mx-auto w-9/12 rotate-180"></div>
    <div class="flex justify-center mt-4">
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
    generate: false,
  }),
  mounted() {
    this.getDateAndHour();
  },

  methods: {
    getDateAndHour() {
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

    generateVoucher() {
      this.generate = !this.generate;
      this.getDateAndHour();
    },

    clearVoucher() {
      this.generate = !this.generate;
      this.nombres = "";
      this.monto = "";
      this.mensaje = "";
    },
  },



  computed: {
    visualizeButton: function () {
      return this.monto.length >= 1 ? true : false;
    },
  }

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
