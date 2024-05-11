<template>
  <div class="background">
    <Nuxt />
    <div class="container">
      <img src="../static/nuvens.svg" alt="" srcset="" class="img-nuvem">
      <img src="../static/nuvens.svg" alt="" srcset="" class="img-nuvem-one">
      <img src="../static/nuvens.svg" alt="" srcset="" class="img-nuvem-buttom">
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({

})
</script>

<style lang="scss" scoped>
.background {
  background: linear-gradient(to bottom, #87CEEB, #FFFFFF);
  background-color: #87CEEB;
  height: 100vh;
  width: 100%;

  .container {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    z-index: 1;
    position: fixed;
    height: 100%;

  }

  .img-nuvem {
    grid-area: 2 / 1 / span 4 / span 2;
  }

  .img-nuvem-one {
    grid-row: 6 / span 7;
    grid-column: 3 / span 5;

  }

  .img-nuvem-buttom {
    grid-area: 9 / 12;
  }

  /* Estilos responsivos para telas menores */
  @media (max-width: 768px) {

    .img-nuvem {
      grid-area: 1 / 8 / span 4 / span 2;
    }

    .img-nuvem-one {
      grid-row: 6 / span 7;
      grid-column: 2 / span 3;
    }

    .img-nuvem-buttom {
      grid-area: 9 / 12;
    }
  }
}
</style>