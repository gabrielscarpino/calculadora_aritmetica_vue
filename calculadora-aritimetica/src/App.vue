<script setup>
import { reactive } from 'vue'
import Cabecalho from './components/Cabecalho.vue';
import Corpo from './components/Corpo.vue';

const estado = reactive({
    num1: '',
    num2: '',
    operacao: '',
    erro: '',
  })

  function calcularResultado() {
    estado.erro = ''
    const { num1, num2, operacao } = estado

    switch (operacao) {
      case 'somar':
        return num1 + num2;
      case 'subtrair':
        return num1 - num2;
      case 'dividir':
        if (num2 === 0) {
          return 'Não é possível dividir por 0'
        }
        return num1 / num2;
      case 'multiplicar':
        return num1 * num2;
    }
  }

</script>

<template>
  <div class="container">

    <Cabecalho />
    <Corpo :calcular-resultado="calcularResultado()" :estado="estado"/>

  </div>
</template>

<style scoped>

</style>
