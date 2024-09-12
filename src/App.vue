<script setup>
import { ref, computed } from 'vue';

const numero1 = ref(0);
const numero2 = ref(0);
const operacao = ref('soma');

const calculo = computed(() => {
  let n1 = parseFloat(numero1.value);
  let n2 = parseFloat(numero2.value);
  let resultado;

  switch (operacao.value) {
    case 'soma':
      resultado = n1 + n2;
      break;
    case 'subtracao':
      resultado = n1 - n2;
      break;
    case 'multiplicacao':
      resultado = n1 * n2;
      break;
    case 'divisao':
      resultado = n2 !== 0 ? n1 / n2 : 'Erro: Divisão por zero';
      break;
    default:
      resultado = 0;
  }
  return resultado;
});

</script>

<template>
  <header>
    <h1>CALCULADORA</h1>
  </header>
  <section>
    <input v-model="numero1" type="number" required placeholder="Digite um numero">
    <input v-model="numero2" type="number" required placeholder="Digite um numero">

    <select v-model="operacao">
      <option value="soma">Soma</option>
      <option value="subtracao">Subtração</option>
      <option value="multiplicacao">Multiplicação</option>
      <option value="divisao">Divisão</option>
    </select>

    <p>Resultado: {{ calculo }}</p>
  </section>

</template>

<style scoped>
</style>