<template>
  <div class="">
    <v-tabs>
      <v-tab>Gestionar recepcionistas</v-tab>
      <v-tab>Gestionar servicios</v-tab>
      <v-tab>Gestionar productos</v-tab>
      <v-spacer />
      <v-tab @click="$router.push({ path: '/' })">Salir</v-tab>

      <v-tab-item> dx </v-tab-item>
      <v-tab-item> dx2 </v-tab-item>
      <v-tab-item> dx 3</v-tab-item>
    </v-tabs>
  </div>
</template>
