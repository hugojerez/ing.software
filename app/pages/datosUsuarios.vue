<template>
  <v-container> Cargando... </v-container>
</template>
<script>
export default {
  data() {
    return {
      model: {
        nombre: 'Minera',
        apellido: 'El tajo',
        rut: '70.567.567-3',
        direccion: 'Calama',
        correo: 'mineraeltajo@gmail.com',
        password: '232323',
      },
    }
  },
  mounted() {
    this.send()
  },
  methods: {
    send() {
      window.$nuxt.$axios
        .$patch('https://roje.cl/api/tests/' + localStorage.last, {
          ...this.model,
          userEmail: localStorage.myUser,
        })
        .then(() => {
          this.$router.push({ path: 'cotizacionFinalizada' })
        })
    },
  },
}
</script>
