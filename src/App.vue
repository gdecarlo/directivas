<script setup>

import { ref,computed,onUnmounted, onMounted } from 'vue'


console.log('Primer log')

const tipoDeCuenta = ref(0)
const tipoCuentaSeleccionada = ref(1)
const tiposDeCuentas = ref([
  {id: 1, nombre: 'Caja de ahorro'},
  {id: 2, nombre: 'Cuenta corriente'},
  {id: 3, nombre: 'Cuenta sueldo'}
])



const nombres = ref([
  {id: 1, nombre: 'Juan'},
  {id: 2, nombre: 'Pedro'},
  {id: 3, nombre: 'Maria'}
])

onMounted(()=>{
  //buscamos datos
  // Promise.all([])
  //asignamos a una propiedad
})

onUnmounted(()=>{
  console.log('Se desmontó el componente')
})

const informacionTipoCuenta = computed(()=>{
  const tipoDeCuenta = tiposDeCuentas.value.find(tipo => tipo.id === tipoCuentaSeleccionada.value)
  return tipoDeCuenta !== undefined ? tipoDeCuenta.nombre : 'No se ha seleccionado un tipo de cuenta'
})

const otraComputada = computed(()=> informacionTipoCuenta.value.toUpperCase())
</script>

<template>
  <h2>ID Tipo de cuenta del select {{ tipoCuentaSeleccionada }}</h2>
  <h2>Nombre Tipo de cuenta del select {{ informacionTipoCuenta }}</h2>
  <h3>{{ otraComputada }}</h3>
  Caja de ahorro
<input type="radio" :value="1" v-model="tipoDeCuenta">
Cuenta corriente
<input type="radio" :value="2" v-model="tipoDeCuenta">
<h1>{{ tipoDeCuenta }}</h1>
<div v-if="tipoDeCuenta === 1">
  Ha seleccionado caja de ahorro
</div>
<div v-if="tipoDeCuenta === 2">
  Ha seleccionado cuenta corriente
</div>
<select v-model="tipoCuentaSeleccionada">
  <option :value="0">Todos</option>
  <option v-for="tipo in tiposDeCuentas" :value="tipo.id" >{{ tipo.nombre }}</option>
</select>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
