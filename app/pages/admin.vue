<template>
  <div class="">
    <div class="text-h1">Panel super-admin</div>
    <v-tabs>
      <v-tab>Listado global de cotizaciones</v-tab>
      <v-tab>Todos los usuarios</v-tab>
      <v-tab>Crear Recepcionista</v-tab>
      <v-tab>Productos / Servicios</v-tab>
      <v-spacer />
      <v-tab @click="$router.push({ path: '/' })">Salir</v-tab>

      <v-tab-item> <CompCotizacionList /></v-tab-item>
      <v-tab-item> <CompUserList /></v-tab-item>
      <v-tab-item> <CompCrearUsuario role="admin" /></v-tab-item>
      <v-tab-item> <CompProser /></v-tab-item>
    </v-tabs>
  </div>
</template>

<script>
import CompUserList from './CompUserList'
import CompCrearUsuario from './CompCrearUsuario'
import CompProser from './CompProser'
import CompCotizacionList from './CompCotizacionList'
export default {
  components: {
    CompProser,
    CompCotizacionList,
    CompUserList,
    CompCrearUsuario,
  },
}
</script>
