<template>
  <login-template>
    <span slot="ladoEsquerdo">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcTse7Gh1Mxyq7u0JtX_QrKBsx4cSAgt1r85L_4rOXJShjmAkdWS" alt="Imagem de Login" class="responsive-img">
    </span>
    <span slot="ladoDireito">
      <!-- Login em conta já existente -->
      <span v-if="!cadastrar">
        <h2>Login</h2>
        <input type="email" placeholder="E-mail" v-model="email">
        <input type="password" placeholder="Senha" v-model="password">
        <div class="botoes">
          <button class="btn waves-effect waves-ligth col s6" @click="login">Entrar</button>
          <button class="btn waves-effect waves-ligth orange col s6"
          @click="cadastrar = !cadastrar">Cadastre-se</button>
        </div>
      </span>

      <!-- Cadastrar nova conta -->
      <span v-else>
        <h2>Cadastrar</h2>
        <input type="text" placeholder="Nome">
        <input type="email" placeholder="E-mail">
        <input type="password" placeholder="Senha">
        <input type="password" placeholder="Repetir Senha">
        <div class="botoes">
          <button class="btn waves-effect waves-ligth col s6">Cadastrar</button>
          <button class="btn waves-effect waves-ligth orange col s6"
          @click="cadastrar = !cadastrar">Voltar</button>
        </div>
      </span>
    </span>
  </login-template>
</template>
<script>
import axios from 'axios'
import LoginTemplate from '@/template/LoginTemplate'

export default {
  components: { LoginTemplate },

  data(){
    return{
      cadastrar: false,
      email: '',
      password: ''
    }
  },

  created(){
    let user = localStorage.getItem('usuario')
    if(user) this.$router.push('/')
  },

  methods: {
    login(){
      let dados = {
        email: this.email,
        password: this.password
      }
      axios.post('http://127.0.0.1:8000/api/login', dados).then(res => {
        console.log(res)
        if(res.data.token){
          /* Armazena informações do usuário no localStorage */
          localStorage.setItem('usuario', JSON.stringify(res.data))
          this.$router.push('/')
        }else if(res.data.status == false){
          /* Verifica se Login existe */
          M.toast({html: 'Usuário ou Senha incorretos!', displayLength: 5000})
        }else{
          /* Verifica erros de validação */
          if(res.data.email) M.toast({html: res.data.email, displayLength: 5000})
          if(res.data.password) M.toast({html: res.data.password, displayLength: 5000})
        }
      }).catch(err => {
        console.log(err)
        M.toast({html: 'Erro de conecção, verifique sua internet ou tente de novo mais tarde.', displayLength: 6000})
      })
    }
  }
}
</script>

<style lang="scss">
  img{
    width: 100%;
    height: 100%;
  }
  .botoes{
    margin-top: 20px;
  }
</style>
