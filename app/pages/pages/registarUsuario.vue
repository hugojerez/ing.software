<template>
  <div>
    <v-text-field
      v-for="(input, index) in inputs"
      :key="index"
      v-model="model[input.label]"
      v-bind="input"
    />
    <div class="text-right">
      <v-btn x-large @click="registar"> Guardar </v-btn>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputs: [
        { label: 'Nombre' },
        { label: 'Apellido' },
        { label: 'email' },
        { label: 'tel' },
        { label: 'contra', type: 'password' },
        { label: 'contra2', type: 'password' },
        { label: 'Rut' },
      ],
      model: {},
    }
  },
  mounted() {},
  methods: {
    registar() {
      const myHeaders = new Headers()
      myHeaders.append('Content-Type', 'application/x-www-form-urlencoded')
      myHeaders.append('Cookie', 'PHPSESSID=2nnuh2en233a7biaca1n2ba4vv')

      const urlencoded = new URLSearchParams()
      for (const a in this.model) {
        urlencoded.append(a, this.model[a])
      }

      const requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: urlencoded,
        redirect: 'follow',
      }

      fetch('http://3.236.254.244/registrarAdministrador.php', requestOptions)
        .then((response) => response.text())
        .then((result) => console.log(result))
        .catch((error) => console.log('error', error))
    },
  },
}
</script>
