<template>
  <div class="containerPage">
      <div class="main">
          <div class="div1">
            <div class="containerLeft">
              <h1 class="title">Jogos Educativos</h1>
              <span class="messageWelcome">O Escola Games é uma plataforma educativa gratuita que oferece jogos e livros infantis para crianças
                  pequenas e os anos iniciais do Ensino Fundamental. O site é desenvolvido com o acompanhamento de
                  profissionais da área da pedagogia para garantir que os jogos cumpram seu objetivo de ensinar
                  enquanto divertem.</span>
                  <button class="btn-inicial" @click="redirectPage">
                      Iniciar 
                  </button>
            </div>
          </div>
          <div class="containerImg">

              <img src="../assets/arteIndex.png" alt="" srcset="">
          </div>

      </div>
  </div>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data() {
      return {
          
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

  .main {
      overflow: hidden;
      width: 100%;
      height: 100%;
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      grid-template-rows: 1fr;
      grid-column-gap: 0px;
      grid-row-gap: 0px;
      margin-top: auto;
      position: absolute;
      justify-content: center;


      .div1 {
          grid-area: 1 / 1 / 2 / 2;
          padding: 0 2rem;

      .containerLeft{
          display: flex;
          flex-direction: column;
          justify-content: center;
          height: 80%;
          width: 70%;
          gap: 1.5rem;
          .title{
          color: #FFFFFF;
      }
          .messageWelcome {
              color: #063B60;
              font-weight: 500;
              margin-top: 1rem;
          }
          .btn-inicial{
              background-color: #FFB703;
              border: none;
              height: 2.5rem;
              color: #FFFFFF;

              &:hover{
                  background-color:#002ead;
                  transition: 0.7s;
                  cursor: pointer;
              }
          }
      }
     
          
      }

      .containerImg {
          grid-area: 1 / 2 / 2 / 3;
          display: flex;
          align-items: flex-start;
          width: 100%;
          height: 100%;
          padding: 0 10%;
          img {
              width: 80%;
              margin-left: auto;
              object-fit: cover;
          }
      }


  }



}
</style>