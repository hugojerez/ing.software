<template>
  <div class="">
    <div class="text-h1">Panel super-admin</div>
    <v-tabs>
      <v-tab> Producto</v-tab>
      <v-tab>Servicios</v-tab>

      <v-tab>Gestionar Recepcionista</v-tab>
      <v-spacer />
      <v-tab @click="$router.push({ path: '/' })">Salir</v-tab>

      <v-tab-item><CompServicio /> </v-tab-item>
      <v-tab-item> <CompProser /></v-tab-item>
      <v-tab-item>
        <v-text-field
          v-model="loqueseestabuscando"
          placeholder="Buscar"
          prepend-icon="mdi-magnify"
        ></v-text-field>
        <v-dialog scrollable max-width="300px">
          <template v-slot:activator="{ on, attrs }">
            <div class="text-right">
              <v-btn x-large color="primary" dark v-bind="attrs" v-on="on">
                Agregar recepcionista
              </v-btn>
            </div>
          </template>
          <v-card class="my-4 pa-5">
            <div class="text-h4">Agregar</div>

            <CompCrearUsuario role="admin" />
          </v-card>
        </v-dialog>

        <v-divider></v-divider>
        <div class="text-h4">Gestionar</div>
        <CompUserList />
      </v-tab-item>
      <v-tab-item> </v-tab-item>
    </v-tabs>
  </div>
</template>

<script>
import CompUserList from './CompUserList'
import CompCrearUsuario from './CompCrearUsuario'
import CompProser from './CompProser'
import CompServicio from './CompServicio'
export default {
  components: {
    CompProser,
    CompServicio,
    CompUserList,
    CompCrearUsuario,
  },
  data: () => {
    return {
      loqueseestabuscando: '',
    }
  },
  watch: {
    loqueseestabuscando: {
      handler(valorActual, valorAntiguo) {
        this.buscar(valorActual)
      },
    },
  },
  methods: {
    buscar(textoABuscar) {},
  },
}
</script>
