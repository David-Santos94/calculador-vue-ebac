<script setup>
import { ref, computed } from 'vue';

const num1 = ref(0);
const num2 = ref(0);
const operation = ref('add');

const result = computed(() => {
  switch (operation.value) {
    case 'add':
      return num1.value + num2.value;
    case 'subtract':
      return num1.value - num2.value;
    case 'multiply':
      return num1.value * num2.value;
    case 'divide':
      return num2.value !== 0 ? num1.value / num2.value : 'Erro: Divisão por zero';
    default:
      return 0;
  }
});
</script>

<template>
  <div id="app">
    <h1>Calculadora Aritmética</h1>
    <div class="calculator">
      <input type="number" v-model.number="num1" placeholder="Digite o primeiro número" />
      <select v-model="operation">
        <option value="add">+ somar</option>
        <option value="subtract">- subtrair</option>
        <option value="multiply">* multiplicar</option>
        <option value="divide">/ dividir</option>
      </select>
      <input type="number" v-model.number="num2" placeholder="Digite o segundo número" />
      <div class="result">
        Resultado: <strong>{{ result }}</strong>
      </div>
    </div>
  </div>
</template>

<style scoped>
body, #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 100vh;
  background-color: #f5f5f5;
}

#app {
  text-align: center;
}

.calculator {
  background-color: #fff;
  width: 60%;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

input {
  width: 150px;
  padding: 5px;
  margin: 0 10px;
  text-align: end;
}

select {
  padding: 5px;
  width: 100px;
}

.result {
  margin-top: 20px;
  font-size: 20px;
}
</style>
