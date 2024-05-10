<template>
  <div class="main-content">
    <div class="propic-container">
      <img class="propic" src="@/assets/propic.png" alt="Propic" />
    </div>
    <div class="introduction">
      <h2 class="display-2 text-center bilbo-regular">Mi presento</h2>
      <p class="text-center w-auto">
        Benvenuti a casa mia! Sono lo Zietto, un avvocato che ama la natura e ha
        deciso di condividere questo angolo di pace con voi. Esplorate i nostri
        spazi verdi, respirate aria fresca e lasciatevi coccolare dalla
        tranquillità della campagna.
        <br />Spero che il vostro soggiorno sia rigenerante e pieno di bellezza
        naturale.
      </p>
    </div>
    <div class="featured-rooms">
      <v-container fluid>
        <v-row justify="center">
          <v-col
            cols="12"
            sm="6"
            md="4"
            v-for="(room, index) in featuredRooms"
            :key="index"
          >
            <RoomCard :room="room" />
          </v-col>
        </v-row>
      </v-container>
    </div>
  </div>
</template>

<script>
import RoomCard from "@/components/RoomCard.vue";
export default {
  name: "MainContent",
  components: {
    RoomCard,
  },
  props: {
    featuredRooms: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.main-content {
  position: relative;
}

.propic-container {
  height: 35vh; /* Set the container height to half the viewport height */
  background-color: #182524; /* Same color as before */
  background-size: cover; /* Ensure the background covers the container */
  background-position: center; /* Center the background */
  width: 100%;
}

.propic {
  display: block;
  margin: auto;
  height: 100%; /* Set the image height to fill the container */
  width: auto;
}

.introduction {
  padding: 40px;
  text-align: center;
  margin-bottom: 40px;
}

.featured-rooms {
}
</style>
