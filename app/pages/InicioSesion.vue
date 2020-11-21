<template>
  <v-container>
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
      ]"
    ></v-select>
    <div class="text-right">
      <v-btn v-if="model.tipo === 'usuario'" to="Cotizador" color="primary"
        >Acceder como usuario</v-btn
      >
      <v-btn v-else to="PanelAdministrador" color="primary"
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
}
</script>
