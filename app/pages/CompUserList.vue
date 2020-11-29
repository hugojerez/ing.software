<template>
  <v-container>
    <div class="title">Listado de cuentas</div>

    <div v-for="i in data" :key="i._id">
      <v-card class="pa-3 mb-3">
        <v-card-title>
          <v-icon> mdi-account </v-icon>
          {{ i.email }} ( {{ i.role }} )
        </v-card-title>

        <v-card-content>
          {{ new Date(i.createdAt).toLocaleString() }}
        </v-card-content>
        <div class="my-4 text-right">
          <v-btn color="primary"> Modificar </v-btn>

          <v-btn color="primary" @click="remove(i._id)"> Eliminar </v-btn>
        </div>
      </v-card>
    </div>
  </v-container>
</template>
<script>
export default {
  props: {
    filter: { type: String, default: '' },
  },
  data() {
    return {
      data: [],
    }
  },
  mounted() {
    this.reloadUsers()
  },
  methods: {
    async remove(id) {
      await window.$nuxt.$axios.$delete('https://roje.cl/api/tests/' + id)
      this.reloadUsers()
    },
    async reloadUsers() {
      this.data = await window.$nuxt.$axios
        .$get('https://roje.cl/api/tests?type=userEntity')
        .then((a) => a.data)
    },
  },
}
</script>
