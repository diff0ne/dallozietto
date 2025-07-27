<template>
  <v-app>
    <Header />
    <MainContent :featuredRooms="featuredRooms" />
    <Footer />
  </v-app>
</template>

<script>
import Header from "@/components/Header.vue";
import MainContent from "@/components/MainContent.vue";
import Footer from "@/components/Footer.vue";

export default {
  components: {
    Header,
    MainContent,
    Footer,
  },
  data() {
    return {
      "featuredRooms": [
        {
          "name": "iris",
          "description": "Camera matrimoniale accogliente e luminosa, con ampio letto in legno, lenzuola fresche e vista sul verde dal grande finestrone con grate di sicurezza. Dispone di armadio, scrivania, scarpiera e TV. Ideale per rilassarsi dopo una giornata di visite. Ambiente silenzioso e curato nei dettagli.",
          "dimension": "20 sqm",
          "maxCapacity": 2,
          "services": ["TV", "Scrivania"]
        },
        {
          "name": "rosa",
          "description": "Camera doppia luminosa con due letti singoli in legno, ciascuno dotato di set di asciugamani e biancheria. La finestra con vista sul verde garantisce luce naturale e tranquillità. Completano l’arredo un armadio spazioso e un mobile con specchio, perfetti per soggiorni confortevoli.",
          "dimension": "20 sqm",
          "maxCapacity": 2,
          "services": ["Armadio", "Specchio"]
        },
        {
          "name": "aquilegia",
          "description": "Elegante camera matrimoniale in stile classico, con arredi in legno massiccio e atmosfera calda e rilassante. Dotata di bagno privato con ampia doccia idromassaggio, bidet, grande armadio, scrivania e piccola TV. Ideale per chi cerca comfort e privacy in un ambiente raffinato.",
          "dimension": "25 sqm",
          "maxCapacity": 2,
          "services": ["Bagno privato", "Doccia idromassaggio", "TV", "Scrivania"]
        },
        {
          "name": "ortensia",
          "description": "Camera doppia spaziosa e luminosa, arredata con due letti singoli in legno, ideale per amici o colleghi. Dispone di ampio armadio e scrivania comoda, con spazio extra per bagagli o attività di lavoro/studio. Ambiente semplice e funzionale, perfetto per un soggiorno pratico e confortevole.",
          "dimension": "20 sqm",
          "maxCapacity": 2,
          "services": ["Scrivania", "Armadio", "Spazio extra per bagagli"]
        }
      ]
    }

  },
};
</script>

<style scoped>
.main-content {
  width: 90%;
  margin: auto;
  padding-bottom: 38px;
}

/* Media query for large screens */
@media screen and (min-width: 1200px) {
  .main-content {
    width: 80%;
  }
}
</style>
