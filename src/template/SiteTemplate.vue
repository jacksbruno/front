<template>
  <div>
    <nav-bar>
      <ul id="nav-mobile" class="right hide-on-med-and-down">
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/login">Entrar</router-link></li>
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
  components: { NavBar, Rodape, CardMenu }
}
</script>

<style lang="scss">

</style>
