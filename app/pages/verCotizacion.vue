<template>
  <v-container>
    <div class="text-h4">Ver cotización</div>
    <v-btn to="PanelAdministrador" color="primary" class="my-5">
      Volver atrás</v-btn
    >
    <v-btn to="verDatosCliente" color="primary"> Ver datos del cliente </v-btn>
    <div class="title">Información de la solicitud de cotización</div>
    <v-simple-table>
      <template v-slot:default>
        <tbody>
          <tr>
            <td>Fecha</td>
            <td>03 Noviember del 2020 a las 3:00 pm</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
    <div class="title">Cotización</div>
    <v-sheet>
      <v-simple-table>
        <template v-slot:default>
          <thead>
            <tr>
              <th class="font-weight-bold text-uppercase text--primary text-h5">
                Descripción
              </th>
              <th class="font-weight-bold text-uppercase text--primary text-h5">
                Cantidad
              </th>
              <th class="font-weight-bold text-uppercase text--primary text-h5">
                Precio
              </th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>SISTEMA DE AGENDAMIENTO Y ENCOLAMIENTO</td>
              <td>1</td>
              <td>$4.543.543</td>
            </tr>
            <tr>
              <td>
                SALAS DE VIDEOCONFERENCIA CON LANDING PAGE, MÁS DE 4 SALAS,
                CONTACTACTESE AL WHATSAPP
              </td>
              <td>1</td>
              <td>$6.344.743</td>
            </tr>
            <tr>
              <td>SISTEMA DE AGENDAMIENTO Y ENCOLAMIENTO</td>
              <td>1</td>
              <td>$4.543.543</td>
            </tr>
            <tr>
              <td>
                SALAS DE VIDEOCONFERENCIA CON LANDING PAGE, MÁS DE 4 SALAS,
                CONTACTACTESE AL WHATSAPP
              </td>
              <td>1</td>
              <td>$6.344.743</td>
            </tr>
            <tr>
              <td>SISTEMA DE AGENDAMIENTO Y ENCOLAMIENTO</td>
              <td>1</td>
              <td>$4.543.543</td>
            </tr>
            <tr>
              <td></td>
              <td class="font-weight-bold">SUBTOTAL</td>
              <td class="font-weight-bold">$26.344.743</td>
            </tr>
            <tr>
              <td></td>
              <td class="font-weight-bold">IVA 19%</td>
              <td class="font-weight-bold">$6.344.743</td>
            </tr>
            <tr>
              <td></td>
              <td class="font-weight-bold">TOTAL</td>
              <td class="font-weight-bold">$26.344.743</td>
            </tr>
          </tbody>
        </template>
      </v-simple-table>
    </v-sheet>
    <v-btn to="PanelAdministrador" color="primary" class="my-5">
      Volver atrás</v-btn
    >
  </v-container>
</template>
