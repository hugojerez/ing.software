<template>
  <v-app>
    <v-main>
      <v-img
        src="https://wallpaperaccess.com/full/1393269.jpg"
        height="150"
        gradient="rgba(0,0,0,0.4) , rgba(0,0,0,0.4) "
        color=""
        dark
        class=""
      >
        <div class="container">
          <div class="display-2">Cotizador Roje</div>
          <div class="text-h4">
            Sistema de cotización de servicios audiovisuales
          </div>
        </div>
      </v-img>
      <v-container>
        <nuxt />
        <v-divider class="py-5" />
        <div class="text-center">
          Cotizador

          <img
            style="width: 100px"
            src="https://i.imgur.com/vTUOVe0.png"
            alt=""
          />
          <div class="">Ingeniería de Software 2020 - UDP</div>
        </div>
      </v-container>
    </v-main>
    <v-navigation-drawer v-model="rightDrawer" :right="right" temporary fixed>
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light> mdi-repeat </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire',
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js',
    }
  },
}
</script>
