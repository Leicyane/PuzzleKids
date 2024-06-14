<template>
    <div class="containerPage">
       <Header />
       <div class="containerGames">
          <MemoryCard />
          
       </div>
    </div>
  </template>
  <script lang="ts">
  import Vue from 'vue'
  export default Vue.extend({
    data() {
        return {}
    },
    methods:{

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