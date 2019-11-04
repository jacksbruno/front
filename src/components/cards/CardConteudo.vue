<template>
<div class="row">
  <div class="card">
    <div class="card-content">
      <div class="row valign-wrapper">
        <div class="col s1">
          <img :src="perfil" alt="" class="circle responsive-img">
        </div>
        <div class="col s11">
          <strong>{{ nome }}</strong> - <small>{{ data }}</small>
        </div>
      </div>
    </div>
    <slot />
    <div class="card-action">
      <p>
        <i class="material-icons">chat</i>
        <i class="material-icons">favorite_border</i>
      </p>
    </div>
  </div>
</div>
</template>

<script>
export default {
  props: ['perfil', 'nome', 'data']
}
</script>

<style lang="scss">

</style>