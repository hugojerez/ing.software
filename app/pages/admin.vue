<template>
  <div class="">
    <div class="text-h1">Panel super-admin</div>
    <v-tabs>
      <v-tab>Productos / Servicios</v-tab>
      <v-tab>Agregar Recepcionista</v-tab>
      <v-spacer />
      <v-tab @click="$router.push({ path: '/' })">Salir</v-tab>

      <v-tab-item> <CompProser /></v-tab-item>
      <v-tab-item> <CompCrearUsuario role="admin" /></v-tab-item>
    </v-tabs>
  </div>
</template>

<script>
import CompCrearUsuario from './CompCrearUsuario'
import CompProser from './CompProser'
export default {
  components: {
    CompProser,
    CompCrearUsuario,
  },
}
</script>
