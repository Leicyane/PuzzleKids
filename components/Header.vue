<template>
    <header class="container-header">
        <h2>Jogos Educativos</h2>

        <section class="infoUser">
            <ul>
                <li> {{user}}</li>
                <li> 
                    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@24,400,0,0" />
                    <span class="material-symbols-outlined">joystick</span>
                    level 1
                </li>
        </ul>
        </section>
    </header>
</template>
<script lang="js">
import Vue from 'vue'
export default Vue.extend({
    data() {
      return {
        user: "",
      }
  },
  async created(){
    const nome = await localStorage.getItem('nome');
    this.user  = nome
  },
})
</script>
<style lang="scss" scoped>
.container-header{
    display: flex;
    width: 100%;
    height: 4rem;
    background: #f7f8fb66;
    justify-content: space-between;
    align-items: center;
    padding: 0 2rem;

    .infoUser{

        ul{
            display: flex;
            gap: 1rem;
        } li{
            display: flex;
            align-items: center;
            justify-content: center;
            list-style: none;
           
        }
    }
}
</style>