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
              Agregar producto
            </v-btn>
          </div>
        </template>
        <v-card class="pa-4">
          <div class="text-h4">Agregar producto</div>

          <v-textarea v-model="put.title" label="Nombre del producto" />
          <v-text-field v-model="put.value" label="Precio del producto">
          </v-text-field>

          <v-btn type="primary" color="primary" @click="poner()">
            Agregar
          </v-btn>
        </v-card>
      </v-dialog>
    </div>

    <div v-for="(elemento, index) in elementos" :key="index" class="">
      <v-row>
        <v-col>
          <v-text-field disabled label="tipo" value="PRODUCTOS" />
        </v-col>

        <v-col>
          <v-text-field disabled label="elemento" :value="elemento.title" />
        </v-col>

        <v-col>
          <v-text-field disabled label="precio" :value="elemento.value">
          </v-text-field>
        </v-col>
      </v-row>
      <v-dialog scrollable max-width="300px">
        <template v-slot:activator="{ on, attrs }">
          <v-btn color="primary" class="my-4" dark v-bind="attrs" v-on="on">
            Modificar servicio
          </v-btn>
        </template>
        <v-card class="pa-4">
          <div class="text-h4">Modificar producto</div>

          <v-textarea :value="elemento.title" label="Nombre del servicio" />
          <v-text-field :value="elemento.value" label="Precio del servicio">
          </v-text-field>

          <v-btn type="primary" color="primary"> Agregar </v-btn>
        </v-card>
      </v-dialog>
      <v-btn color="primary " class="ma-2">Eliminar</v-btn>
      <v-divider />
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return { elementos: [], put: {} }
  },
  methods: {
    poner() {
      this.elementos.push({
        title: this.put.title,
        value: this.put.value,
      })
    },
  },
}
</script>
