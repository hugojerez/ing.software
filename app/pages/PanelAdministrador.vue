<template>
  <div class="">
    <div class="text-h1">Panel recepcionista</div>
    <v-tabs>
      <v-tab>Listado de cotizaciones</v-tab>
      <v-spacer />
      <v-tab @click="$router.push({ path: '/' })">Salir</v-tab>

      <v-tab-item> <CompCotizacionList /></v-tab-item>
    </v-tabs>
  </div>
</template>

<script>
import CompCotizacionList from './CompCotizacionList'
export default {
  components: { CompCotizacionList },
}
</script>
