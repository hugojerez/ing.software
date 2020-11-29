<template>
  <div class="">
    <v-text-field
      placeholder="Buscar"
      prepend-icon="mdi-magnify"
    ></v-text-field>
    <div class="text-right">
      <v-btn color="primary " class="ma-2" x-large>Agregar</v-btn>
    </div>

    <div v-for="(elemento, index) in 0" :key="index" class="">
      <v-row>
        <v-col>
          <v-text-field disabled label="tipo" value="PRODUCTOS" />
        </v-col>

        <v-col>
          <v-text-field disabled label="elemento" value=" " />
        </v-col>

        <v-col>
          <v-text-field disabled label="precio" value=" "> </v-text-field>
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
