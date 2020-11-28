<template>
  <v-container>
    <div class="display-3">Ingresa tus datos</div>
    <div class="text-h4">
      Estimado usuario para poder contactarlo necesitamos que rellene los
      siguientes campos
    </div>
    <v-divider class="my-5" />

    <div style="max-width: 500px" class="">
      <v-text-field v-model="model.nombre" label="Nombres" />
      <v-text-field v-model="model.apellido" label="Apellidos" />
      <v-text-field v-model="model.direccion" label="Dirección" />
      <v-text-field v-model="model.correo" label="Correo electrónico" />
      <v-text-field v-model="model.password" type="password" label="Clave" />
      <div class="text-right">
        <v-btn to="cotizacionFinalizada" color="primary"> Continuar </v-btn>
      </div>
    </div>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      model: {},
    }
  },
  methods: {
    send() {
      window.$nuxt.$axios
        .$post('https://roje.cl/api/tests', { type: 'userdata', ...model })
        .then(({ data }) => {
          if (data.length) {
          }
        })
    },
  },
}
</script>
