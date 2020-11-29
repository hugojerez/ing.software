<template>
  <v-container>
    <div class="title">Creación de cuenta</div>

    <v-text-field v-model="model.email" label="Usuario" name="email" />
    <v-text-field v-model="model.name" label="Nombres" name="name" />
    <v-text-field v-model="model.lastname" label="Apellidos" name="lastname" />
    <v-text-field v-model="model.rut" label="Rut" name="rut" />
    <v-text-field v-model="model.telefono" label="Teléfono" name="telefono" />

    <v-text-field
      v-model="model.password"
      label="Contraseña"
      type="password"
      name="password"
    />
    <v-btn @click="register">Registar</v-btn>
  </v-container>
</template>
<script>
export default {
  props: {
    role: { type: String, default: '' },
  },
  data() {
    return {
      model: {},
    }
  },
  mounted() {},
  methods: {
    async register(id) {
      if (this.model.email && this.model.password) {
        const existe = await window.$nuxt.$axios
          .$get('https://roje.cl/api/tests?email=' + this.model.email)
          .then((a) => a.total)
        if (existe) {
          alert('El Usuario ya existe')
          return
        }
        await window.$nuxt.$axios.$post('https://roje.cl/api/tests/', {
          type: 'userEntity',
          name: this.model.name,
          lastname: this.model.lastname,
          telefono: this.model.telefono,
          rut: this.model.rut,
          email: this.model.email,
          role: this.role,
          password: this.model.password,
        })
        alert('Usuario creado')
      }
    },
  },
}
</script>
