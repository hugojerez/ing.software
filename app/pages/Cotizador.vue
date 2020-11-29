<template>
  <div class="">
    <div class="text-h1">Panel cliente</div>

    <v-tabs>
      <v-tab>Consultar servicios</v-tab>
      <v-tab>Consultar productos</v-tab>
      <v-tab>Ver el estado de las cotizaciones</v-tab>
      <v-spacer />
      <v-tab @click="$router.push({ path: '/' })">Salir</v-tab>

      <v-tab-item> <CompCotizador /></v-tab-item>
      <v-tab-item> <CompCotizador /></v-tab-item>
      <v-tab-item>
        <CompCotizacionList mode="user" :filter="filter"
      /></v-tab-item>
    </v-tabs>
  </div>
</template>

<script>
import CompCotizacionList from './CompCotizacionList'
import CompCotizador, { elementos } from './CompCotizador'

export { elementos }
export default {
  components: { CompCotizacionList, CompCotizador },
  data() {
    return { filter: '' }
  },
  mounted() {
    this.filter = localStorage.myUser
  },
}
</script>
