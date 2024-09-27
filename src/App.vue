<script setup>
import { reactive } from 'vue';

const estado = reactive({
  operacao: 'soma',
  valor1: 0,
  valor2: 0,
  resultado: ''
})

function soma(valor1, valor2){
  return valor1 + valor2;
}

function subtracao(valor1, valor2){
  return valor1 - valor2;
}

function multiplicacao(valor1, valor2){
  return valor1 * valor2;
}

function divisao(valor1, valor2){
  return valor1 / valor2;
}

function calculaOperacao(){
  switch(estado.operacao){
    case '+':
      estado.resultado = soma(estado.valor1, estado.valor2);
      console.log("teste soma");
      break;
    case '-':
      estado.resultado = subtracao(estado.valor1, estado.valor2);
      console.log("teste subt");
      break;
    case '*':
      estado.resultado = multiplicacao(estado.valor1, estado.valor2);
      console.log("teste mult");
      break;
    case '/':
      estado.resultado = divisao(estado.valor1, estado.valor2);
      console.log("teste div");
      break;
  }
}

</script>

<template>
  <div class="container">
    <header>
      <h1 class="m-3 p-3 text-center">Calculator - Vue.js</h1>
    </header> 
  </div>

  <div class="container">
    <div class="row mt-5 pt-3 pb-5 text-center border">
      <h3 class="pb-3">Digite os valores:</h3>
      <div class="col-5">
        <input @keyup="calculaOperacao()" type="text" class="form-control" placeholder="Primeiro valor" :value="estado.valor1" @input="event => estado.valor1 = event.target.value"/>
      </div>

      <div class="col-2 text-center">
        <span> {{estado.operacao}} </span>
      </div>

      <div class="col-5">
        <input type="text" class="form-control" placeholder="Segundo valor" :value="estado.valor2" @input="event => estado.valor2 = event.target.value" />
      </div>      
    </div>
    <div class="row mt-5 text-center pb-5 border">
      <div class="col-12">
        <h3 class="m-3 pb-3">Escolha a operação:</h3>
        <select @change="evento => estado.operacao = evento.target.value" class="col-8 text-center">
          <option value="+">Soma +</option>
          <option value="-">Subtração -</option>
          <option value="*">Multiplicação x</option>
          <option value="/">Divisão /</option>
        </select>
      </div>
    </div>
    <div class="row mt-5 text-center pb-5 border">
      <div class="col-12">
        <h3 class="m-3 pb-3">Resultado:</h3>
        <div class="col-6 m-auto">
          <input disabled type="text" value="estado.resultado" class="form-control text-center resultado" placeholder="Resultado" />
        </div>
      </div>
    </div>
  </div>

  <footer class="text-center p-1 m-1 fixed-bottom">
    <p class="m-1">© 2024 - Developed by <a href="https://github.com/frohlichramon01" class=""><i class="bi bi-github"></i> frohlichramon01</a></p>
  </footer>
</template>

<style scoped>
span {
  font-size: 30px;
  font-weight: bold;
}

input, select{
  text-align: center;
  font-size: 24px;
  font-weight: bold;
}

.resultado{
  text-align: end;
}

footer{
  background-color: darkgrey;
  display: flex;
  justify-content: center;
}

a {
  text-decoration: none;
  color: black;

  &:hover{
    text-decoration: underline;
  }
}
</style>
