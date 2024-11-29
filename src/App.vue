<script setup>
import { ref, computed } from 'vue';

const numero1 = ref(null);
const numero2 = ref(null);
const operador = ref('soma');

const operadores = {
  soma:'+',
  subtracao: '-',
  divisao: '/',
  multiplicacao: '*',
};

const resultado = computed(() => {
  if (isNaN(numero1.value) || isNaN(numero2.value)) return 'Valores inválidos';
  if (numero1.value === null || numero2.value === null) return 'Digite os valores';
  switch (operador.value){
    case 'soma':
      return numero1.value + numero2.value;
    case 'subtracao':
      return numero1.value - numero2.value;
    case 'divisao':
      return numero2.value !==0 ? (numero1.value/numero2.value).toFixed(2) : 'Erro (divisão por zero)';
    case 'multiplicacao':
      return (numero1.value * numero2.value).toFixed(2);
    default:
      return 'Operação inválida';
  }
})

</script>

<template>
<div class="container mt-5 justify-content-center align-items-center" style="height: 100vh;">
  <header class="p-4 mb-4 mt-4 bg-light rounded-3 text-center shadow">
    <h1 class="display-6">Calculadora Aritmética</h1>
  </header>
  <form>
    <div class="row g-3 align-items-center justify-content-center">
      <div class="col-md-3 col-12 text-center">
        <input v-model="numero1" type="number" placeholder="Digite um número" class="form-control text-center">
      </div>
      <div class="col-md-2 col-12 text-center">
        <select v-model="operador"  class="form-select text-center">
          <option v-for="(simbolo, operacao) in operadores" :key="operacao" :value="operacao">{{ simbolo }}</option>
        </select>
      </div>
      <div class="col-md-3 col-12 text-center">
        <input type="number" v-model="numero2" placeholder="Digite um número" class="form-control text-center">
      </div>
      <div class="col-md-1 col-12 text-center">
        <span class="fs-4"> = </span>
      </div>
      <div class="col-md-3 col-12 text-center">
        <span class="form-control text-center bg-light fs-5"> {{resultado}} </span>
      </div>
    </div>
  </form>
</div>
</template>

<style scoped>

</style>
