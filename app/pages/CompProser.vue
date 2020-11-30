<template>
  <div class="">
    <v-text-field
      placeholder="Buscar"
      prepend-icon="mdi-magnify"
    ></v-text-field>
    <div class="text-right">
      <v-dialog scrollable max-width="300px">
        <template v-slot:activator="{ on, attrs }">
          <div class="text-right">
            <v-btn
              x-large
              color="primary"
              class="my-4"
              dark
              v-bind="attrs"
              v-on="on"
            >
              Agregar servicio
            </v-btn>
          </div>
        </template>
        <v-card class="pa-4">
          <div class="text-h4">Agregar servicio</div>

          <v-textarea label="Nombre del servicio" />
          <v-text-field label="Precio del servicio"> </v-text-field>

          <v-btn type="primary" color="primary"> Agregar </v-btn>
        </v-card>
      </v-dialog>
    </div>
    <div v-for="elemento in elementos" :key="elemento.name" class="">
      <v-row>
        <v-col>
          <v-text-field disabled label="tipo" value="SERVICIO" />
        </v-col>

        <v-col>
          <v-text-field disabled label="elemento" :value="elemento.title" />
        </v-col>

        <v-col>
          <v-text-field disabled label="precio" :value="elemento.value">
          </v-text-field>
        </v-col>
      </v-row>
      <v-btn color="primary " class="ma-2">Modificar</v-btn>
      <v-btn color="primary " class="ma-2">Eliminar</v-btn>
      <v-divider />
    </div>
  </div>
</template>
<script>
import { elementos } from './CompCotizador'

export default {
  data() {
    return { elementos }
  },
}
</script>
