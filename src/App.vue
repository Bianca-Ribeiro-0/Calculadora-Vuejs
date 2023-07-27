<script setup>
import { ref } from 'vue';

//criando constantes dos numeros e definindo elas como 0
const num1 = ref(0);
const num2 = ref(0);
const selectedOperation = ref('adicao');

//criando funções das operações aritmeticas
function soma() {
  return num1.value + num2.value;
}

function subtrai() {
  return num1.value - num2.value;
}

function divide() {
  if (num2.value === 0) {
    return "Erro: Divisão por zero";
  }
  return num1.value / num2.value;
}

function multiplicao() {
  return num1.value * num2.value;
}

//relacionando as funções com o select
function resultado() {
  switch (selectedOperation.value) { 
    case 'adicao':
      return soma();
    case 'subtracao':
      return subtrai();
    case 'divisao':
      return divide();
    case 'multiplicacao':
      return multiplicao();
    default:
      return '';
  }
}
</script>

<template>
  <div class="container">
    <header class="p-5 bg-light rounded-3">
      <h1>Calculadora com Vue</h1>
    </header>
    <form class="p-5">
      <div class="form-row">
        <div class="col">
          <input class="form-control" required type="number" placeholder="Digite um número" v-model="num1">
        </div>
        <div class="col mt-4">
          <input class="form-control" required type="number" placeholder="Digite um número" v-model="num2">
        </div>
        <div class="col-md-2">
          <select class="form-control mt-4" v-model="selectedOperation">
            <option value="adicao">Adição</option>
            <option value="subtracao">Subtração</option>
            <option value="divisao">Divisão</option>
            <option value="multiplicacao">Multiplicação</option>
          </select>
        </div>
      </div>
    </form>
    <div class="p-5">
      <p>{{ resultado() }}</p>
    </div>
  </div>
</template>

<style scoped>
</style>
