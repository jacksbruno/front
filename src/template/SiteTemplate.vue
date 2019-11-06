<template>
  <div>
    <nav-bar>
      <ul id="nav-mobile" class="right hide-on-med-and-down">
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/perfil">{{ usuario.name }}</router-link></li>
        <li><a @click="sair">Sair</a></li>
      </ul>
    </nav-bar>
    <div class="container">
      <div class="row">
        <div class="col s4">
          <card-menu>
            <slot name="ladoEsquerdo" />
          </card-menu>
        </div>

        <div class="col s8">
          <slot name="ladoDireito" />
        </div>
      </div>
    </div>
    <Rodape />
  </div>
</template>

<script>
import NavBar from '@/components/NavBar'
import Rodape from '@/components/Rodape'
import CardMenu from '@/components/cards/CardMenu'

export default {
  components: { NavBar, Rodape, CardMenu },

  data(){
    return{
      usuario: ''
    }
  },

  created(){
    let user = localStorage.getItem('usuario')
    if(!user) this.$router.push('/login')
    if(user){
      this.usuario = JSON.parse(user)
      this.$emit('usuarioLogado', this.usuario)
    }
  },

  methods: {
    sair(){
      localStorage.clear()
      this.$router.push('/login')
    }
  }
}
</script>

<style lang="scss">

</style>
