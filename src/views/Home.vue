<template>
  <site-template @usuarioLogado="userLogado">
    <span slot="ladoEsquerdo">
      <div class="row valign-wrapper">
        <div class="col s3">
          <img src="https://materializecss.com/images/yuna.jpg" alt="" class="circle responsive-img">
        </div>
        <div class="col s9">
          <h5>{{ usuario.name }}</h5>
          <span class="black-text">
            {{ usuario.email }}
          </span>
        </div>
      </div>
    </span>
    <span slot="ladoDireito">
      <publicar-conteudo />
      <card-conteudo
      perfil="https://materializecss.com/images/yuna.jpg"
      nome="Jacks Bruno"
      data="29/10/19 19:16">
        <card-detalhes 
          img="https://materializecss.com/images/sample-1.jpg"
          txt="I am a very simple card. I am good at containing small bits of information.
          I am convenient because I require little markup to use effectively."
          titulo="Linda Paisagem" />
      </card-conteudo>
    </span>
  </site-template>
</template>

<script>
import SiteTemplate from '@/template/SiteTemplate'
import CardConteudo from '@/components/cards/CardConteudo'
import CardDetalhes from '@/components/cards/CardDetalhes'
import PublicarConteudo from '@/components/PublicarConteudo'

export default {
  components: { SiteTemplate, CardConteudo, PublicarConteudo, CardDetalhes },

  data(){
    return{
      usuario: '',
      pensamento: ''
    }
  },

  methods: {
    userLogado(e){
      this.usuario = e
    }
  }
}
</script>
