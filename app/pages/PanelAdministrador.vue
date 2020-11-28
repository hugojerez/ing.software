<template>
  <v-container>
    <div class="title">Listado de cotizaciones</div>

    <div v-for="i in data" :key="i._id">
      <v-card class="pa-3 mb-3">
        <v-card-title>
          Cotización ({{ Object.values(i.model || {}).length }} elementos
          cotizados)</v-card-title
        >
        <v-card-content>
          Cotización realizada a las
          {{ new Date(i.createdAt).toLocaleString() }}
        </v-card-content>
        <div class="my-4 text-right">
          <v-btn to="verDatosCliente" color="primary">
            Ver datos del cliente
          </v-btn>
          <v-btn to="verCotizacion" color="primary"> Editar cotización </v-btn>
          <v-btn to="verCotizacion" color="primary"> Ver cotización </v-btn>
          <v-btn color="primary" @click="remove(i._id)"> Eliminar </v-btn>
        </div>
      </v-card>
    </div>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      data: [],
    }
  },
  mounted() {
    this.reloadCotizaciones()
  },
  methods: {
    async remove(id) {
      await window.$nuxt.$axios.$delete('https://roje.cl/api/tests/' + id)
      this.reloadCotizaciones()
    },
    async reloadCotizaciones() {
      this.data = await window.$nuxt.$axios
        .$get('https://roje.cl/api/tests?type=send_cotizacion')
        .then((a) => a.data)
    },
  },
}
</script>
