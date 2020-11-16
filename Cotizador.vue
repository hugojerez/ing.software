 <template>
  <v-container>
    <div class="display-1 mt-10">
      ¿Cómo será tu evento?
    </div>
    <div class="lead mb-10">
      Te enseñamos nuestras tarifas
    </div>
    <v-snackbar
      color="success"
      :value="true"
      bottom
      multi-line
      center
      :timeout="-1"
    >
      <div>
        Calculado
      </div>
      <div class="title">
        <AnimatedNumber
          :duration="400"
          :format-value="(a)=>('$ '+Number(Math.round(a)).toLocaleString('es-ES'))"
          :value="total()"
        />
      </div>
      <template v-slot:action="{ attrs }">
        <v-btn
          href="https://api.whatsapp.com/send?phone=56933142154"
          target="_blank"
          outlined
          v-bind="attrs"
          class="subtitle-1 text-none"
          @click="snackbar = false"
        >
          <v-icon>
            mdi-whatsapp
          </v-icon>
          ¡Hablemos!
        </v-btn>
      </template>
    </v-snackbar>
    <div class="text-center">
      <span v-for="precio in precios " :key="precio.text">
        <v-card
          max-width="300"
          :color="((typeof(model[precio.name])==='string' && model[precio.name]===precio.text) || model[precio.name]>0) && '#135c13'"
          dark
          class="rounded-xl d-inline-block ma-3"
        >
          <v-card-title>
            <v-icon class="mr-1" v-text="precio.icon" />
            {{ precio.title }}
          </v-card-title>

          <v-card-text class="text-right overline mb-n3 py-0 mt-n5">
            $ {{ Number(precio.value).toLocaleString('es-ES') }}
          </v-card-text>

          <v-card-text style="height:120px;overflow:hidden">
            {{ precio.text }}
          </v-card-text>
          <div style="height:90px;overflow:hidden">

            <v-card-text v-if="precio.type==='multiple'">
              <Form
                v-model="model"
                :fields="[
                  {name:precio.name,rules:'',type:'integer',value:0,options:{max:precio.max||9000}}
                ]"
              />
            </v-card-text>
            <v-card-text v-else-if="precio.type==='radiobutton'">
              <Form
                v-model="model"
                :fields="[
                  {name:precio.name,rules:'',type:'radiobutton',options:{
                    values:[
                      {key:precio.text,value:'Seleccionar'}
                    ]
                  }}
                ]"
              />
            </v-card-text>
            <v-card-text v-else>
              <Form
                v-model="model"
                :fields="[
                  {name:precio.name,rules:'',type:'checkbox',placeholder:'Seleccionar'}
                ]"
              />
            </v-card-text>
          </div>

        </v-card>
      </span>
    </div>
    <div class="" style="height:250px" />
  </v-container>
</template>

<script>
import AnimatedNumber from 'animated-number-vue'

export default {
  layout: 'panel',

  components: { AnimatedNumber },
  data () {
    return {
      model: {
      },
      precios: [

        { quantity: 0, icon: 'mdi-video', name: 'STREAMING', title: 'Streaming ', text: 'LANDING PAGE + STREAMING CHAT Y ENCUESTA (CAPACIDAD 2000) ', value: 350000, type: 'multiple' },
        { quantity: 0, icon: 'mdi-video', name: 'STREAMING_2', title: 'Streaming ', text: 'LANDING PAGE + STREAMING CHAT Y ENCUESTA  (ILIMITADO)', value: 450000, type: 'multiple' },
        { quantity: 0, icon: 'mdi-account-multiple', name: 'MEETING', title: 'Meeting room /salas ', text: 'SALAS DE VIDEOCONFERENCIA CON LANDING PAGE, MÁS DE 4 SALAS, CONTACTACTESE AL WHATSAPP ', value: 90000, type: 'multiple' },
        { quantity: 0, icon: 'mdi-face-agent', name: 'VIDEO', title: 'Video call center ', text: 'VALOR POR OPERADOR CON SISTEMA DE AGENDAMIENTO Y ENCOLAMIENTO  ', value: 120000, type: 'multiple' },
        { quantity: 0, icon: 'mdi-download', name: 'DESCARGADOC', title: 'Descarga de documentos ', text: 'DENTRO DEL LANDING SE PEDEN REALIZAR DESCARGA DE DOCUMENTOS EN PDF O REDIRECCIONAR A UN SITIO ESPECIFICO DE DESCARGA DE DOCUMENTOS  ', value: 50000 },
        { quantity: 0, icon: 'mdi-image', name: 'DESCARGAIMAGE', title: 'Descarga de imágenes ', text: 'DENTRO DEL LANDING SE PEDEN REALIZAR DESCARGA DE DOCUMENTOS EN JPG O REDIRECCIONAR A UN SITIO ESPECIFICO DE DESCARGA DE IMAGENES CAPACIDAD 5 GIGAS ', value: 50000 },
        { quantity: 0, icon: 'mdi-login-variant', name: 'ACCESO', title: 'Acceso', text: 'ACCESO AL EVENTO SIN RESTRICCIONES  ', value: 30000, type: 'multiple' },
        { quantity: 0, icon: 'mdi-login-variant', name: 'ACCESO_2', title: 'Acceso', text: 'ACCESSO AL EVENTO CON RESTRICCIONES DE INGRESO / BASE DE DATOS PROPORCIONADA POR EL CLIENTE   ', value: 75000, type: 'multiple' },
        { quantity: 0, icon: 'mdi-radiobox-marked', name: 'GRABACIONES', title: 'Grabaciones ', text: 'CAPACIDAD DE 5GB PARA GRABACIONES EN LA NUBE DE ROJE  ', value: 20000 },
        { quantity: 0, icon: 'mdi-lifebuoy', max: 3, name: 'SOPORTE', title: 'Personal soporte ', text: 'TODOS LOS EVENTOS CONTEMPLAN SOPORTE INFORMATICO Y PLATAFORMA  ', value: 45000, type: 'multiple' },
        { quantity: 0, icon: 'mdi-twitter', name: 'RRSS', title: 'RRSS', text: 'VISUALIZACION DEL IFRAME DE LOS COMENTARIOS DE RRSS / EL ADMINISTRADOR DE LA CUENTA DEBE PROPORCIONAR CODIGO HTML ', value: 20000 }

      ]
    }
  },
  methods: {

    total () {
      let total = Number(0)
      for (const item in this.model) {
        const value = this.model[item]
        if (typeof value === 'string') {
          total += this.precios.find(a => (a.text === value)).value
        } else if (value > 0) {
          total += this.precios.find(a => (a.name === item)).value * value
        }
      }
      return total
    }
  }
}
</script>

<style>

</style>
