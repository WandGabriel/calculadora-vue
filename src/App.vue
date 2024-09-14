<script setup>
import { reactive } from 'vue';
import Formulario from './components/Formulario.vue';
import Cabecalho from './components/Cabecalho.vue';

const limparDadosInseridos = () => {
  estado.primeiroValor = '';
  estado.segundoValor = '';
}

const calcular = () => {  
    switch (estado.operacaoAritmetica) {
      case 'somar':
        estado.resultado = parseFloat(estado.primeiroValor) + parseFloat(estado.segundoValor);
        limparDadosInseridos();
        break;
      case 'subtrair':
        estado.resultado = parseFloat(estado.primeiroValor) - parseFloat(estado.segundoValor);
        limparDadosInseridos();
        break;
      case 'multiplicar':
        estado.resultado = parseFloat(estado.primeiroValor) * parseFloat(estado.segundoValor).toFixed(2);
        limparDadosInseridos();
        break;
      case 'dividir':
        if(estado.segundoValor != 0){
          estado.resultado = parseFloat(estado.primeiroValor) / parseFloat(estado.segundoValor).toFixed(2);
        } else {
          estado.resultado = 'Divisão por zero não é permitida'
        }
        limparDadosInseridos();
        break;
      default:
        return estado.resultado = 'Operação inválida';
    }

}

const estado = reactive({
  operacaoAritmetica: 'somar',
  resultado: '',
  primeiroValor: '',
  segundoValor: '',
})

</script>

<template>
  <div class="container w-50">
      <Cabecalho />
      <Formulario :operacao-aritmetica="evento => estado.operacaoAritmetica = evento.target.value" 
        :primeiro-valor="estado.primeiroValor"
        :segundo-valor="estado.segundoValor"
        :resultado="estado.resultado"
        :edita-primeiro-valor="evento => estado.primeiroValor = evento.target.value"
        :edita-segundo-valor="evento => estado.segundoValor = evento.target.value"
        :calcular="calcular"/>
  </div>
  <br />
</template>

<style scoped>

</style>
