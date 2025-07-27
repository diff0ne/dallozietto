<template>
  <v-container>
    <v-card class="elevation-1">
      <v-card-title class="headline">Servizi Disponibili</v-card-title>
      <v-card-text>
        <ul class="services-list">
          <li><strong>WiFi:</strong> Connessione internet WiFi gratuita disponibile in tutto il B&B.</li>
          <li><strong>Cucina Attrezzata:</strong> Cucina completamente attrezzata a disposizione degli ospiti per preparare i pasti.</li>
          <li><strong>Televisione:</strong> TV a schermo piatto con canali via cavo disponibile in ogni camera.</li>
          <li><strong>Lavanderia Self Service:</strong> Servizio di lavanderia self-service disponibile per gli ospiti.</li>
          <li><strong>Uso Barbecue:</strong> Area barbecue disponibile per l'uso degli ospiti.</li>
        </ul>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'Services', // Component name for registration and debugging
}
</script>

<style scoped>
/* Use Poppins font consistent with other components */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500&display=swap');

.services-list {
  padding-left: 1.5rem;
  padding-right: 1.5rem;
  font-family: 'Poppins', sans-serif;
  font-weight: 300;
  font-size: 1rem;
  color: #182524;
  line-height: 1.5;
}
</style>
