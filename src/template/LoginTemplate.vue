<template>
  <div>
    <nav-bar />
    <div class="container">
      <div class="row">
        <div class="col s8">
          <card-menu>
            <slot name="ladoEsquerdo" />
          </card-menu>
        </div>
        <div class="col s4">
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
