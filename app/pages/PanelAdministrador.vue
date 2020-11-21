<template>
  <v-container>
    <div class="title">Listado de cotizaciones</div>

    <div v-for="i in 20" :key="i">
      <v-card class="pa-3 mb-3">
        <v-card-title> Cotización #{{ i }}</v-card-title>
        <v-card-content>
          Cotización realizada por Pedro a las 5/10/2020
        </v-card-content>
        <div class="my-4 text-right">
          <v-btn to="verDatosCliente" color="primary">
            Ver datos del cliente
          </v-btn>
          <v-btn to="verCotizacion" color="primary"> Ver cotización </v-btn>
          <v-btn color="primary"> Eliminar </v-btn>
        </div>
      </v-card>
    </div>
  </v-container>
</template>
<script>
export default {
  data() {
    return {}
  },
}
</script>
