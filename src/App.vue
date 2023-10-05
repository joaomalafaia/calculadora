<script setup>
  import { reactive } from 'vue';
  const estado = reactive({
    operação: 'default',
    número1: 0,
    número2: 0
  });
  
  function conta() {
    const {operação, número1, número2} = estado

    switch(operação) {
      case 'soma':
        return parseFloat(número1) + parseFloat(número2)
      case 'subtração':
        return parseFloat(número1) - parseFloat(número2)
      case 'multiplicação':
        return parseFloat(número1) * parseFloat(número2)
      case 'divisão':
        return parseFloat(número1) / parseFloat(número2)
    }
  };
</script>

<template>
  <div class="container">
    <header class="header p-5 mt-4 rounded-3">
      <h1>Calculadora</h1>
      <p>
        Insira os números nos campos e selecione a operação aritmética
      </p>
    </header>
    <form>
      <div class="row">
        <div class="col-md-5">
          <input :value="estado.número1" @input="evento => estado.número1 = evento.target.value" required type="number" placeholder="número" class="form-control">
        </div>
        <div class="col-md-2">
          <select @change="evento => estado.operação = evento.target.value" class="form-control">
            <option value="default">Operação</option>
            <option value="soma">&plus;</option>
            <option value="subtração">&minus;</option>
            <option value="multiplicação">&times;</option>
            <option value="divisão">&divide;</option>
          </select>
        </div>
        <div class="col-md-5">
          <input :value="estado.número2" @input="evento => estado.número2 = evento.target.value" required type="number" placeholder="número" class="form-control">
        </div>
      </div>
    </form>
    <h3 class="resposta mt-5">{{ conta() }}</h3>
  </div>
</template>

<style scoped>
  .header {
    text-align: center;
  }
  .resposta {
    text-align: center;
    font-size: 48px;
  }
</style>