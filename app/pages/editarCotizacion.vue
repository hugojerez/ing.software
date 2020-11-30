<template>
  <v-container>
    <div class="text-h4">Editar cotización</div>
    <v-btn to="PanelAdministrador" color="primary" class="my-5">
      Volver atrás</v-btn
    >
    <div class="title">Información de la solicitud de cotización</div>

    <v-simple-table>
      <template v-slot:default>
        <tbody>
          <tr>
            <td>Nombre</td>
            <td><v-text-field :value="cotizacion.nombre" /></td>
          </tr>
          <tr>
            <td>Apellidos</td>
            <td><v-text-field :value="cotizacion.apellido" /></td>
          </tr>
          <tr>
            <td>Direccion</td>
            <td><v-text-field :value="cotizacion.direccion" /></td>
          </tr>

          <tr>
            <td>Rut</td>
            <td><v-text-field :value="cotizacion.rut" /></td>
          </tr>

          <tr>
            <td>Correo</td>
            <td><v-text-field :value="cotizacion.correo" /></td>
          </tr>
          <tr>
            <td>Fecha</td>
            <td><v-text-field :value="cotizacion.createdAt" /></td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
    <div class="title">Cotización</div>
    <v-sheet>
      <v-simple-table>
        <template v-slot:default>
          <thead>
            <tr>
              <th class="font-weight-bold text-uppercase text--primary text-h5">
                Descripción
              </th>
              <th class="font-weight-bold text-uppercase text--primary text-h5">
                Cantidad
              </th>
              <th class="font-weight-bold text-uppercase text--primary text-h5">
                Precio
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="elemento in elegido" :key="elemento.name">
              <td><v-text-field :value="elemento.title" /></td>

              <td>1</td>
              <td>${{ Number(elemento.value).toLocaleString('es') }}</td>
              <td>
                <v-btn color="blue" dark> Editar</v-btn>
                <v-btn color="red" dark> Eliminar</v-btn>
              </td>
            </tr>
            <tr>
              <td></td>
              <td class="font-weight-bold">SUBTOTAL</td>
              <td class="font-weight-bold">
                ${{
                  Number(
                    elegido.map((a) => a.value).reduce((a, b) => a + b, 0)
                  ).toLocaleString('es')
                }}
              </td>
            </tr>
            <tr>
              <td></td>
              <td class="font-weight-bold">IVA 19%</td>
              <td class="font-weight-bold">
                ${{
                  Number(
                    0.19 *
                      elegido.map((a) => a.value).reduce((a, b) => a + b, 0)
                  ).toLocaleString('es')
                }}
              </td>
            </tr>
            <tr>
              <td></td>
              <td class="font-weight-bold">TOTAL</td>
              <td class="font-weight-bold">
                $
                {{
                  Number(
                    1.19 *
                      elegido.map((a) => a.value).reduce((a, b) => a + b, 0)
                  ).toLocaleString('es')
                }}
              </td>
            </tr>
          </tbody>
        </template>
      </v-simple-table>
    </v-sheet>
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
