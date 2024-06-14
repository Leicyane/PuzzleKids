<template>
    <div class="card" v-if="data && data.imgcaminho">
      <div @click="redirectPage(data.pageRouter)" class="containerImgGame">
        <img :src="data.imgcaminho" alt="Imagem do Jogo" />
      </div>
      <span>{{ data.name }}</span>
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
      redirectPage(router: any){
          this.$router.push(router)
      }
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
    cursor: pointer;
    span{
        margin-top:1rem;
    }

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