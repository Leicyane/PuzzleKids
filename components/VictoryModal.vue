<template>
    <div id="vitoria">
      <div id="container">
        <h1>Parabéns!</h1>
        <p>Você encontrou todos os pares com</p>
        <h2><span>{{ errors }}</span> ERROS</h2>
        <ButtonDefault @click.native="$emit('restart')" title="Jogar de novo"/>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'VictoryModal',
    props: {
      errors: Number,
    },
  };
  </script>
  
  <style scoped>
  #vitoria {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.8);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
  }
  #container {
    background: white;
    padding: 37px;
    border-radius: 10px;
    text-align: center;
    color: black;
    width: 24%;
    gap: 1rem;
    display: grid;

  }
  </style>
  