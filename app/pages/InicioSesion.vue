<template>
  <v-container style="max-width: 600px" class="mx-auto">
    <div class="title">Inicio de sesión</div>
    <v-text-field
      v-model="model.user"
      label="Nombre de usuario"
      name="nombre de usuario"
    />
    <v-text-field
      v-model="model.password"
      label="Contraseña"
      type="password"
      name="clave"
    />
    <v-select
      v-model="model.tipo"
      label="Tipo de usuario"
      :items="[
        { value: 'usuario', text: 'Soy un usuario' },
        { value: 'recepcionista', text: 'Soy un recepcionista' },
        { value: 'admin', text: 'Soy un administrador' },
      ]"
    ></v-select>
    <div class="text-right">
      <v-btn v-if="model.tipo === 'usuario'" color="primary" @click="login()"
        >Acceder como usuario</v-btn
      >
      <v-btn v-else-if="model.tipo === 'admin'" color="primary" @click="login()"
        >Acceder como usuario</v-btn
      >

      <v-btn v-else color="primary" @click="login()"
        >Acceder como recepcionista</v-btn
      >
    </div>
  </v-container>
</template>
<script>
export default {
  data() {
    return { model: { usuario: 'usuario' } }
  },
  methods: {
    login() {
      const tipo = this.model.tipo
      window.$nuxt.$axios
        .$get('https://roje.cl/api/tests?email=' + this.model.user)
        .then(({ data }) => {
          if (data.length) {
            if (data[0].clave === this.model.clave) {
              localStorage.myUser = data[0].email
              if (tipo === 'admin') {
                this.$router.push({ path: 'Admin' })
              } else if (tipo === 'usuario') {
                this.$router.push({ path: 'Cotizador' })
              } else {
                this.$router.push({ path: 'PanelAdministrador' })
              }
              alert('login exitoso')
            } else {
              alert('contraseña inválida')
            }
          } else {
            alert('El usuario no existe')
          }
        })
    },
  },
}
</script>
