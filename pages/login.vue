<template>
    <div class="containerLogin">
        <div class="card">
            <h1>Bem Vindo!</h1>
            <h4 class="legenda"  v-if="!login">Registre-se, ou faça o <span @click="logarUser" class="link-login">login</span> </h4> 
            <h4 class="legenda"  v-else>Insira suas credencias, ou <span @click="logarUser" class="link-login">registre-se</span> </h4> 
            <FormLogin v-if="!login" > 

                <InputText title="Username" idInput="text" v-model="credentialUser.username" />
                <InputText title="Idade" idInput="number" v-model="credentialUser.age"/>
                <InputText title="Senha" idInput="text" v-model="credentialUser.password"/>
                <ButtonDefault title="Cadastrar" />
            </FormLogin>
            <FormLogin v-if="login" > 
                <InputText title="Username" idInput="text" v-model="user.username" />
                <InputText title="Senha" idInput="password" v-model=" user.password" />
               
                <ButtonDefault title="Login" @click.native="logar" />
            </FormLogin>
        </div>
    </div>
</template>

<script>
export default {
 data(){
    return{
        login: true,
        credentialUser:{
            username:"",
            age:"",
            password:"",
        },
        user:{
            username: "",
            password:"",
        }

        
    }
 },
 methods:{
    logarUser(){
        this.login = !this.login
        console.log('login recebe', this.login)
    },
    logar(){
        localStorage.setItem('nome', this.user.username);
        this.$router.push('/games')
    }
 }
}
</script>
<style lang="scss" scoped>
.containerLogin{
    width: 100%;
    height: 100vh;
    position: absolute;
    z-index: 2;
    display: grid;

.card{
    background: white;
    border-radius: 1rem;
    width: 30%;
    height: auto;
    margin: auto;
    padding: 1.4rem;
    gap: 1rem;
    display: flex;
    flex-direction: column;
    h1{
        margin: 0;
    }
    .legenda{
        font-weight: 400;
    }
    .link-login{
        font-weight: 300;
        color: blue;
        cursor: pointer;
    }
    
}

}
</style>
