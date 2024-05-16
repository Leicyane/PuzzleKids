<template>
    <div class="card" v-if="data && data.imgcaminho">
      <div class="containerImgGame">
        <img :src="data.imgcaminho" alt="Imagem do Jogo" />
      </div>
      <span>{{ data.id }}</span>
    </div>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    props: {
        title: String,
        data: Object 
    },
  data() {
      return {

      }
  },

  methods:{
      // redirectPage(){
      //     this.$router.push('/login')
      // }
  }
})
</script>
<style lang="scss" scoped>
.card{
    width: 18%;
    background: white;
    height: 18rem;
    border-radius: 1rem;
    padding: 1rem;
    text-align: center;

    .containerImgGame{
        background-color: wheat;
        height: 85%;
        width: 100%;
        border-radius: 1rem;
        img{
            object-fit: cover;
            width: 100%;
            height: 100%;
        }
     
    }
}
</style>