<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/Cabecalho.vue';
  import Principal from './components/Principal.vue';
  import Rodape from './components/Rodape.vue';

  const estado = reactive({
    primeiroValor: 0,
    segundoValor: 0,
    operacao: 'adicao',
    resultado: 0
  });

  function valorUm(e){
    estado.primeiroValor = e.target.value;
    getResultado();
  };

  function valorDois(e){
    estado.segundoValor = e.target.value;
    getResultado();
  };

  function operacao(e){
    estado.operacao = e.target.value;
    getResultado();
  };
  
  function getResultado(){
    switch (estado.operacao) {
      case 'adicao':
        estado.resultado = Number(estado.primeiroValor) + Number(estado.segundoValor);
        break;
      case 'subtracao':
        estado.resultado = estado.primeiroValor - estado.segundoValor;
        break;
      case 'multiplicacao':
        estado.resultado = estado.primeiroValor * estado.segundoValor;
        break;
      case 'divisao':
        estado.resultado = Number(estado.primeiroValor / estado.segundoValor).toFixed(2);
        break;
      case 'potenciacao':
        estado.resultado = Number(Math.pow(estado.primeiroValor, estado.segundoValor)).toFixed(2);
        break;
      default:
        estado.resultado = 0;
    }
  };
</script>

<template>
    <Cabecalho />
    <div class="container">
      <Principal :primeiro-valor="estado.primeiroValor" :valor-um="valorUm" :segundo-valor="estado.segundoValor" :valor-dois="valorDois" :operacao="estado.operacao" :calcular="operacao" :resultado="estado.resultado" />
    </div>
    <footer class="footer">
      <Rodape />
    </footer>
</template>

<style>
  
  /*
    Tirei o scoped para aplicar o CSS de forma global.
    Li que a boa prática seria criar o style scope em cada component,
    mas como tenho pouco tempo para estudar e desenvolver no curso
    resolvi fazer globalmente.
  */

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: sans-serif;
  }

  body {
    position: relative;
  }

  input {
    border: 1px solid #079992;
    border-radius: 8px;
    margin: 8px;
    outline: none;
    text-align: center;
    height: 100px;
    width: 160px;
    font-size: 48px;
    padding-left: 12px;
    color: #079992;
    cursor: pointer;
  }

  input::placeholder {
    font-size: 24px;
    color: #079992;
    padding-left: 8px;
  }

  input::-webkit-scrollbar {
    border-radius: 8px;
  }

  select {
    border: none;
    outline: none;
    font-size: 36px;
    color: #079992;
    cursor: pointer;
  }

  span {
    display: block;
  }

  .titulo_resultado {
    color: #dee2e6;
  }

  .valor_resultado {
    font-size: 48px;
    color: #dee2e6;
  }

  h1, .footer span {
    color: #079992;
  }

  .container {
    max-width: 780px;
    width: 100%;
    margin: 80px auto 0;
    height: calc(100vh - 200px);
    display: flex;
    align-items: center;
  }

  .header {
    text-align: center;
    position: absolute;
    top: 5%;
    left: 50%;
    transform: translate(-50%, -50%);
    margin-top: 0;
  }

  main {
    display: block;
    width: 60%;
    margin: 0 auto;
    text-align: center;
    border-radius: 16px;
  }

  .main_header{
    border: 1px solid #38ada9;
    border-top-left-radius: 16px;
    border-top-right-radius: 16px;
    background-color: #38ada9;
    color: #dee2e6;
  }

  .main_body {
    padding: 16px 0;
    border: 1px solid #38ada9;
  }

  .main_footer {
    border: 1px solid #38ada9;
    font-size: 20px;
    font-weight: bold;
    border-bottom-left-radius: 16px;
    border-bottom-right-radius: 16px;
    background-color: #38ada9;
  }

  .footer {
    text-align: center;
    position: absolute;
    bottom: 5%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  button {
    margin-top: 8px;
    border-color: #079992;
    border-radius: 4px;
    outline: none;
    padding: 4px 8px;
    color: #079992;
    font-weight: bold;
    background-color: #fff;
    cursor: pointer;
  }

  @media (max-width: 680px) {
    input, select {
      display: block;
      margin: 0 auto;
    }
  }
</style>