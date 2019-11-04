<template>
  <div class="row">
    <div class="input-field col s12">
      <textarea id="textarea1" class="materialize-textarea" v-model="conteudo"></textarea>
      <label for="textarea1">No que você está pensando?</label>
    </div>
    <p>
      <button class="btn col s2 offset-s10 waves-effect waves-ligth" v-if="conteudo">Publicar</button>
    </p>
  </div>
</template>

<script>
export default {
  data(){
    return{
      conteudo: ''
    }
  }
}
</script>
