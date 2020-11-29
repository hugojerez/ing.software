<template>
  <div class="">
    <div class="text-h1">Panel super-admin</div>
    <v-tabs>
      <v-tab> Producto</v-tab>
      <v-tab>Servicios</v-tab>
      <v-tab>Agregar Recepcionista</v-tab>
      <v-tab>Gestionar Recepcionista</v-tab>
      <v-spacer />
      <v-tab @click="$router.push({ path: '/' })">Salir</v-tab>

      <v-tab-item><CompServicio /> </v-tab-item>
      <v-tab-item> <CompProser /></v-tab-item>
      <v-tab-item> <CompCrearUsuario role="admin" /></v-tab-item>
      <v-tab-item>
        <CompUserList />
      </v-tab-item>
    </v-tabs>
  </div>
</template>

<script>
import CompUserList from './CompUserList'
import CompCrearUsuario from './CompCrearUsuario'
import CompProser from './CompProser'
import CompServicio from './CompServicio'
export default {
  components: {
    CompProser,
    CompServicio,
    CompUserList,
    CompCrearUsuario,
  },
}
</script>
