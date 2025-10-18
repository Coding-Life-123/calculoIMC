
<template>
  <div class="main-div">
    <h1>CALCULADORA IMC</h1>
    <main>
      <div class="cuestionario">
        <div class="input-cont">
          <h2>Nombre:</h2>
          <input class="inputs" type="text" placeholder="ingrese su nombre" v-model="nombre">
        </div>
        <div class="input-cont">
          <h2>Peso:</h2>
          <input class="inputs" type="number" placeholder="ingrese su peso en kg" v-model="peso">
        </div>      
        <div class="input-cont">
          <h2>Altura:</h2>
          <input class="inputs" type="number" placeholder="ingrese su altura en metros" v-model="altura">
        </div>
        <button @click="calcular()">Calcular</button>
        <p v-text="resultado" v-bind:style="imc < 18.5 ? 'color:yellow;' : ''" ></p>
      </div>
      <div class="image">
        <img v-show="imc > 0 && imc < 18.5" src="/delgada.jpg" alt="persona delgada">
        <img  src="/normal.jpg" alt="persona normal">
        <img v-show="imc >= 25 && imc < 30" src="/sobrepeso.jpg" alt="persona sobrepeso">
        <img v-show="imc >= 30" src="/gordo.jpg" alt="persona gorda">
      </div>
    </main>
  </div>
</template>

<script setup>
  import { ref } from 'vue';
  //v-show="imc >= 18.5 && imc < 25"
  const nombre = ref('')
  const altura = ref('')
  const peso = ref('')
  const imc = ref(0)
  
  function calcular(){
    console.log(nombre.value);
    console.log(altura.value);
    console.log(peso.value);

    imc.value = peso.value / (altura.value * altura.value)
    console.log(imc.value)
  }
</script>

<style>
  *{
    margin: 0px;
    padding: 0px;
  }

  .main-div{
    width:100vw;
    display:flex;
    flex-direction: column;
  }

  h1{
    margin: 0 auto;
    margin-top: 20vh;
  }
  
  main{
    display: flex;
    margin: 20px auto;
    gap: 20px;
    border: 2px solid black;
    padding: 20px;
    border-radius: 10px;
  }

  .cuestionario{
    width: fit-content;
    height: 100%;
    
    padding: 10px;
    display: flex;
    flex-direction: column;
    row-gap: 20px;
    margin: auto;
  }

  h2{
    margin: 0px;
  }

  .inputs{
    height: 20px;
    width: 200px;
    border: none;
    background-color: rgb(100, 100, 100);
    color: white; 
  }

  div .image{
    width: fit-content !important; 
    display: flex;
  }

  img{
    width: fit-content;
  }
</style>