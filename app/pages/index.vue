<template>
  <v-sheet class="text-center">
    <div class="text-h4 my-12">Bienvenidos al sistema de cotización</div>

    <div class="text-center my-5 my-12">
      <v-btn x-large to="/inicioSesion" color="primary">
        Ya tengo cuenta
      </v-btn>
      <v-btn x-large to="/registerMyself" color="primary"> Registrarme </v-btn>
    </div>
    <div class="my-5 py-12">
      Con nuestro sistema de cotización podrás obtener de forma expedita y los
      costos de tu idea
    </div>
  </v-sheet>
</template>

<script>
export default {
  components: {},
}
</script>
