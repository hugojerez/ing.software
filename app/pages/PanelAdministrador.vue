<template>
  <div class="">
    <div class="text-h1">Panel recepcionista</div>
    <v-tabs>
      <v-tab>Gestionar cotizaciones</v-tab>
      <v-spacer />
      <v-tab @click="$router.push({ path: '/' })">Salir</v-tab>

      <v-tab-item>
        <v-text-field
          placeholder="Buscar"
          prepend-icon="mdi-magnify"
        ></v-text-field>
        <CompCotizacionList
      /></v-tab-item>
      <v-tab-item>
        <v-text-field
          placeholder="Buscar"
          prepend-icon="mdi-magnify"
        ></v-text-field
        ><CompUserList
      /></v-tab-item>
      <v-tab-item> <CompCrearUsuario role="user" /></v-tab-item>
    </v-tabs>
  </div>
</template>

<script>
import CompUserList from './CompUserList'
import CompCrearUsuario from './CompCrearUsuario'
import CompCotizacionList from './CompCotizacionList'
export default {
  components: { CompCotizacionList, CompUserList, CompCrearUsuario },
}
</script>
