<template>
  <div class="">
    <div v-for="(elemento, index) in 20" :key="index" class="">
      <v-row>
        <v-col>
          <v-text-field label="tipo" value="PRODUCTOS" />
        </v-col>

        <v-col>
          <v-text-field label="elemento" value=" " />
        </v-col>

        <v-col>
          <v-text-field label="precio" value=" "> </v-text-field>
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
