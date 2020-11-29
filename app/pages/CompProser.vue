<template>
  <div class="">
    <div v-for="elemento in elementos" :key="elemento.name" class="">
      <v-row>
        <v-col>
          <v-text-field label="tipo" value="SERVICIO" />
        </v-col>

        <v-col>
          <v-text-field label="elemento" :value="elemento.title" />
        </v-col>

        <v-col>
          <v-text-field label="precio" :value="elemento.value"> </v-text-field>
        </v-col>
      </v-row>

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
