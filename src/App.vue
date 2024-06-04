<script setup>
import { reactive, computed } from 'vue';

const estado = reactive({
  operacao: 'soma',
  numero1: 0,
  numero2: 0,
})

const soma = () => {
  return estado.numero1 + estado.numero2;
}

const subtracao = () => {
  return estado.numero1 - estado.numero2;
}

const divisao = () => {
  return estado.numero1 / estado.numero2;
}

const multiplicacao = () => {
  return estado.numero1 * estado.numero2;
}

const getOperacao = computed(() => {
  switch (estado.operacao) {
    case 'subtracao':
      return subtracao();
    case 'divisao':
      return divisao();
    case 'multiplicacao':
      return multiplicacao();
    default:
      return soma();
  }
});
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
      <h1>Calculadora Aritmética</h1>
      <br />
      <p>Escolha a operação:</p>
      <select @change="evento => estado.operacao = evento.target.value">
        <option value="soma">+</option>
        <option value="subtracao">-</option>
        <option value="divisao">÷</option>
        <option value="multiplicacao">×</option>
      </select>
      <br />
      <br />
      <p>Insira os números:</p>
      <input type="number" v-model.number="estado.numero1" />
      <input type="number" v-model.number="estado.numero2" />
      <br />
      <br />
      <h5>O resultado é: {{ getOperacao }}</h5>
    </header>
  </div>
</template>

<style scoped>
  .container {
    text-align: center;
  }
</style>