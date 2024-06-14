<template>
    <div class="containerPage">
       <Header />
       <div class="containerGames">
          <CardGames title="Quebra-cabeça deslizante" v-for="(item, id) in gamesDisponiveis" :key="id" :data="item"/>
       </div>
    </div>
  </template>
  <script lang="ts">
  import Vue from 'vue'
  export default Vue.extend({
    data() {
        return {
            gamesDisponiveis:[
              { 
                id: 1,
                name: 'Puzzle deslizante numeros',
                imgcaminho: '*/assets/puzzle.png',
                pageRouter: "/puzzle"
              },
              { 
                id: 2,
                name: 'Jogo da memoria',
                imgcaminho: '*/assets/puzzle.png',
                pageRouter: "/memoryCard"
              }

            ]
        }
    },
    methods:{
        redirectPage(){
            this.$router.push('/login')
        }
    }
  })
  </script>
  
  
  <style scoped lang="scss">
  .containerPage {
    width: 100%;
    height: 100vh;
    position: absolute;
    z-index: 2;

    .containerGames{
      display: flex;
      align-items: flex-end;
      gap: 2rem;
      padding: 3rem 2rem;
    }
    
  }
  </style>