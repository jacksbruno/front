<template>
  <span>
    <div v-if="img" class="card-image">
      <img :src="img">
      <span class="card-title">{{ titulo }}</span>
    </div>
    <div class="card-content" v-if="txt">
      <p>{{ txt }}</p>
    </div>
  </span>
</template>

<script>
export default {
  props: ['img', 'titulo', 'txt']
}
</script>
