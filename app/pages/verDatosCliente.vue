<template>
  <v-container>
    <div class="text-h4">Ver datos del cliente</div>
    <v-btn to="PanelAdministrador" color="primary" class="my-5">
      Volver atrás</v-btn
    >
    <v-btn to="verCotizacion" color="primary"> Ver cotización </v-btn>

    <v-simple-table>
      <template v-slot:default>
        <tbody>
          <tr>
            <td>Nombre</td>
            <td>JUAN PEDRO</td>
          </tr>
          <tr>
            <td>Apellidos</td>
            <td>RAULENCIO GUTIREREZ</td>
          </tr>
          <tr>
            <td>Direccion</td>
            <td>
              Avenida Alfalba, Sepeta, Región Metropolitana, Santiago, Chile
            </td>
          </tr>
          <tr>
            <td>Teléfono</td>
            <td>+569828323233</td>
          </tr>

          <tr>
            <td>Correo</td>
            <td>juanpabloraul@gmail.com</td>
          </tr>
          <tr>
            <td>RUT</td>
            <td>12.432.543-3</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
    <v-btn to="PanelAdministrador" color="primary" class="my-5">
      Volver atrás</v-btn
    >
  </v-container>
</template>
