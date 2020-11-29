<template>
  <div class="" style="max-width: 500px; margin: 0 auto">
    <CompCrearUsuario />
    <v-btn class="ma-4" color="primary" @click="$router.push({ path: '/' })"
      >Salir</v-btn
    >
  </div>
</template>
<script>
import CompCrearUsuario from './CompCrearUsuario'
export default {
  components: {
    CompCrearUsuario,
  },
}
</script>
