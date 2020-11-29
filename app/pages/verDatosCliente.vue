<template>
  <v-container>
    <div class="text-h4">Ver datos del cliente</div>
    <v-btn to="PanelAdministrador" color="primary" class="my-5">
      Volver atrás</v-btn
    >
    <v-btn to="verCotizacion" color="primary"> Ver cotización </v-btn>
    <v-simple-table>
      <template v-slot:default>
        <tbody>
          <tr>
            <td>Nombre</td>
            <td>{{ cotizacion.nombre }}</td>
          </tr>
          <tr>
            <td>Apellidos</td>
            <td>{{ cotizacion.apellido }}</td>
          </tr>
          <tr>
            <td>Direccion</td>
            <td>{{ cotizacion.direccion }}</td>
          </tr>

          <tr>
            <td>Rut</td>
            <td>{{ cotizacion.rut }}</td>
          </tr>

          <tr>
            <td>Correo</td>
            <td>{{ cotizacion.correo }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
    <v-btn to="PanelAdministrador" color="primary" class="my-5">
      Volver atrás</v-btn
    >
  </v-container>
</template>
<script>
import { elementos } from './Cotizador.vue'
export default {
  data() {
    return {
      elegido: [],
      cotizacion: {},
    }
  },
  async mounted() {
    const id = this.$route.query.id
    const mydata = await this.$axios.$get('https://roje.cl/api/tests/' + id)
    this.cotizacion = mydata
    for (const elemento of elementos) {
      if (mydata.model[elemento.text]) {
        this.elegido.push(elemento)
      }
    }
  },
}
</script>
