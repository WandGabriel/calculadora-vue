<script setup>
    const props = defineProps(['operacaoAritmetica','primeiroValor','segundoValor','resultado', 'editaPrimeiroValor','editaSegundoValor','calcular','limparDadosInseridos'])
</script>

<template>
<form @submit.prevent>
    <div class="text-center">
      <div class="col-md-3 w-50 text-center">
        <label>Primeiro número: </label>            
          <input :value="props.primeiroValor" @change="editaPrimeiroValor" required class="form-control" type="number">      
          <label>Segundo número: </label>    
          <input :value="props.segundoValor" @change="editaSegundoValor" required class="form-control" type="number">
          <div class="col m-4">
            <select @change="props.operacaoAritmetica" @click="calcular" :v-model="limparDadosInseridos" class="form-control text-center btn btn-warning">
              <option value=""></option>
              <option value="somar">Somar</option>
              <option value="subtrair">Subtrair</option>
              <option value="multiplicar">Multipicar</option>
              <option value="dividir">Dividir</option>
            </select>
          </div>
          <label>Resultado Final: </label>
          <br />
            <h2>{{ props.resultado }}</h2>
      </div>    
      <div class="row">
      </div>
    </div>
  </form>
</template>