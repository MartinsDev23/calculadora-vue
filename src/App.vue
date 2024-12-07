<script setup>
import { reactive } from 'vue';


  const estado = reactive ({
    valores: {
      valor1: 0,
      valor2: 0,
    },
    operacao: 'soma',
    resultado: 0
  })

  const calculaResultado = () => {
    const valor1 = Number(estado.valores.valor1);
    const valor2 = Number(estado.valores.valor2);

    switch (estado.operacao) {
      case 'soma':
        estado.resultado = valor1 + valor2;
        break;
      case 'subtrai':
        estado.resultado = valor1 - valor2;
        break;
      case 'multiplica':
        estado.resultado = valor1 * valor2;
        break;
      case 'divide':
        estado.resultado = valor1 / valor2;
        break;
    }  
  }


  
</script>

<template>
  <div class="container col-md-4 text-center mt-5">
    <h1>Calculadora Aritmética</h1>
    <form class="form-control mt-3">
        <input @keyup="evento => estado.valores.valor1 = evento.target.value" class="form-control mt-3 mb-3" type="number" placeholder="Digite um número">
        <select @change="evento => {  estado.operacao = evento.target.value; calculaResultado() }"  class="col-md-12">
            <option value="soma">Somar</option>
            <option value="subtrai">Subtrair</option>
            <option value="multiplica">Multiplicar</option>
            <option value="divide">Dividir</option>
        </select>
        <input @keyup="evento => estado.valores.valor2 = evento.target.value" class="form-control mb-3 mt-3" type="numer" placeholder="Digite um segundo número">
        <span class="form-control">Resultado: {{ estado.resultado }}</span>
    </form>
  </div>
</template>

<style scoped>

</style>
