<template>
  <v-container>
    <div class="display-3">Cotizador</div>
    <div class="text-h4">
      A continuación seleccione los servicios a los cuales está interesado
      contratar
    </div>
    <v-divider class="my-5" />
    <div v-for="elemento in elementos" :key="elemento.text" class="">
      <v-row no-gutters>
        <v-col cols="auto" class="pr-4">
          <v-checkbox v-model="model[elemento.text]" />
        </v-col>
        <v-col>
          <div class="text-h5">
            {{ elemento.title }}
          </div>
          {{ elemento.text }}
        </v-col>
      </v-row>
    </div>
    <div class="text-right">
      <v-btn color="primary" x-large @click="submit"> Continuar </v-btn>
    </div>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      model: {},
      elementos: [
        {
          quantity: 0,
          icon: 'mdi-video',
          name: 'STREAMING',
          title: 'Streaming ',
          text: 'LANDING PAGE + STREAMING CHAT Y ENCUESTA (CAPACIDAD 2000) ',
          value: 350000,
          type: 'multiple',
        },
        {
          quantity: 0,
          icon: 'mdi-video',
          name: 'STREAMING_2',
          title: 'Streaming ',
          text: 'LANDING PAGE + STREAMING CHAT Y ENCUESTA  (ILIMITADO)',
          value: 450000,
          type: 'multiple',
        },
        {
          quantity: 0,
          icon: 'mdi-account-multiple',
          name: 'MEETING',
          title: 'Meeting room /salas ',
          text:
            'SALAS DE VIDEOCONFERENCIA CON LANDING PAGE, MÁS DE 4 SALAS, CONTACTACTESE AL WHATSAPP ',
          value: 90000,
          type: 'multiple',
        },
        {
          quantity: 0,
          icon: 'mdi-face-agent',
          name: 'VIDEO',
          title: 'Video call center ',
          text:
            'VALOR POR OPERADOR CON SISTEMA DE AGENDAMIENTO Y ENCOLAMIENTO  ',
          value: 120000,
          type: 'multiple',
        },
        {
          quantity: 0,
          icon: 'mdi-download',
          name: 'DESCARGADOC',
          title: 'Descarga de documentos ',
          text:
            'DENTRO DEL LANDING SE PEDEN REALIZAR DESCARGA DE DOCUMENTOS EN PDF O REDIRECCIONAR A UN SITIO ESPECIFICO DE DESCARGA DE DOCUMENTOS  ',
          value: 50000,
        },
        {
          quantity: 0,
          icon: 'mdi-image',
          name: 'DESCARGAIMAGE',
          title: 'Descarga de imágenes ',
          text:
            'DENTRO DEL LANDING SE PEDEN REALIZAR DESCARGA DE DOCUMENTOS EN JPG O REDIRECCIONAR A UN SITIO ESPECIFICO DE DESCARGA DE IMAGENES CAPACIDAD 5 GIGAS ',
          value: 50000,
        },
        {
          quantity: 0,
          icon: 'mdi-login-variant',
          name: 'ACCESO',
          title: 'Acceso',
          text: 'ACCESO AL EVENTO SIN RESTRICCIONES  ',
          value: 30000,
          type: 'multiple',
        },
        {
          quantity: 0,
          icon: 'mdi-login-variant',
          name: 'ACCESO_2',
          title: 'Acceso',
          text:
            'ACCESSO AL EVENTO CON RESTRICCIONES DE INGRESO / BASE DE DATOS PROPORCIONADA POR EL CLIENTE   ',
          value: 75000,
          type: 'multiple',
        },
        {
          quantity: 0,
          icon: 'mdi-radiobox-marked',
          name: 'GRABACIONES',
          title: 'Grabaciones ',
          text: 'CAPACIDAD DE 5GB PARA GRABACIONES EN LA NUBE DE ROJE  ',
          value: 20000,
        },
        {
          quantity: 0,
          icon: 'mdi-lifebuoy',
          max: 3,
          name: 'SOPORTE',
          title: 'Personal soporte ',
          text:
            'TODOS LOS EVENTOS CONTEMPLAN SOPORTE INFORMATICO Y PLATAFORMA  ',
          value: 45000,
          type: 'multiple',
        },
        {
          quantity: 0,
          icon: 'mdi-twitter',
          name: 'RRSS',
          title: 'RRSS',
          text:
            'VISUALIZACION DEL IFRAME DE LOS COMENTARIOS DE RRSS / EL ADMINISTRADOR DE LA CUENTA DEBE PROPORCIONAR CODIGO HTML ',
          value: 20000,
        },
      ],
    }
  },
  methods: {
    submit() {
      this.$router.push({ path: '/datosUsuarios' })
      window.$nuxt.$axios.$post('https://roje.cl/api/tests', {
        type: 'send_cotizacion',
        user: localStorage.user,
        model: this.model,
      })
    },
  },
}
</script>
