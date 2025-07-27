<template>
  <v-container>
    <v-card class="elevation-1">
      <v-card-title class="headline">Regolamento</v-card-title>
      <v-card-text>
        <!-- Display list of rules with title and description -->
        <ol class="rule-list">
          <li v-for="(rule, index) in rules" :key="index">
            <strong>{{ rule.title }}</strong>
            <p>{{ rule.description }}</p>
          </li>
        </ol>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: "Rules",
  data() {
    return {
      // Array of rules with title and description
      rules: [
        {
          title: "Pulizia e Manutenzione",
          description:
            "Al fine di mantenere un ambiente pulito e confortevole per tutti gli ospiti, si prega di rispettare le norme di igiene e di utilizzare gli spazi comuni con cura. Il personale del B&B si occuperà regolarmente della pulizia delle aree comuni e delle camere.",
        },
        {
          title: "Silenzio e Rispetto della Quiete",
          description:
            "Per garantire un ambiente tranquillo e rilassante, si prega di rispettare il silenzio negli spazi comuni e di evitare rumori molesti nelle ore notturne.",
        },
        {
          title: "Vietato Fumare",
          description:
            "È severamente vietato fumare all'interno delle camere e delle aree comuni del B&B. È disponibile una zona fumatori esterna designata.",
        },
        {
          title: "Animali Domestici",
          description:
            "Gli animali domestici non sono ammessi, a meno che non sia stato concordato diversamente in anticipo con la direzione del B&B.",
        },
        {
          title: "Responsabilità degli Ospiti",
          description:
            "Gli ospiti sono responsabili per eventuali danni causati alle strutture o al loro contenuto durante il soggiorno. Eventuali danni saranno addebitati al momento del check-out.",
        },
        {
          title: "Accesso WiFi",
          description:
            "È disponibile una connessione WiFi gratuita per gli ospiti. Le credenziali di accesso saranno fornite al momento del check-in.",
        },
        {
          title: "Politica di Cancellazione",
          description:
            "Si prega di consultare le politiche di cancellazione al momento della prenotazione. Eventuali modifiche o cancellazioni devono essere comunicate entro i termini stabiliti.",
        },
        {
          title: "Emergenze e Sicurezza",
          description:
            "In caso di emergenza, contattare immediatamente il personale del B&B. Si prega di prendere visione delle informazioni relative alla sicurezza fornite all'arrivo.",
        },
      ],
    };
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500&display=swap');

.v-card-text {
  /* Use consistent font styling */
  font-family: 'Poppins', sans-serif;
  color: #182524;
  font-weight: 300;
  font-size: 1rem;
  line-height: 1.5;
  padding-left: 1rem;
  padding-right: 1rem;
}

.rule-list {
  padding-left: 1.5em;
  margin-bottom: 1.2em;
}

.rule-list li {
  margin-bottom: 1.5em; /* Space between each rule */
}

.rule-list strong {
  display: block; /* Title on separate line */
  margin-bottom: 0.25em;
}

.rule-list p {
  margin: 0; /* Remove default paragraph margin */
}
</style>
