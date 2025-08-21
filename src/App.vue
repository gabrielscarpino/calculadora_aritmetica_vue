<script setup>
import { reactive, computed, watch } from 'vue'
import Cabecalho from './components/Cabecalho.vue';
import Corpo from './components/Corpo.vue';

const estado = reactive({
  num1: '',
  num2: '',
  operacao: '',
  erro: '', // continuará existindo, mas não será manipulado no computed
})

// Computed apenas calcula o resultado
const resultado = computed(() => {
  const { num1, num2, operacao } = estado

  switch (operacao) {
    case 'somar':
      return num1 + num2
    case 'subtrair':
      return num1 - num2
    case 'dividir':
      if (num2 === 0) {
        return null // não retorna string, delega erro
      }
      return num1 / num2
    case 'multiplicar':
      return num1 * num2
    default:
      return 0
  }
})

// Watcher para tratar erros separadamente
watch(
  () => ({ num1: estado.num1, num2: estado.num2, operacao: estado.operacao }),
  ({ num2, operacao }) => {
    if (operacao === 'dividir' && num2 === 0) {
      estado.erro = 'Não é possível dividir por 0'
    } else {
      estado.erro = ''
    }
  },
  { deep: true }
)
</script>

<template>
  <div class="container">
    <Cabecalho />
    <Corpo :calcular-resultado="resultado ?? estado.erro" :estado="estado" />
  </div>
</template>