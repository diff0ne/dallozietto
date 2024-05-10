<template>
  <div class="main-content">
    <div class="propic-container">
      <img class="propic" src="@/assets/propic.png" alt="Propic" />
    </div>
    <div class="introduction">
      <div class="divider"></div>
      <!-- Add a divider element here -->

      <h2 class="display-2 text-center bilbo-regular">La mia casa</h2>
      <p class="text-center w-auto">
        Benvenuti nella mia villa nel verde! Mi chiamano lo Zietto e sono un
        appassionato della natura e della campagna. Qui, tra gli alberi e il
        canto degli uccelli, ho creato un rifugio accogliente per chi cerca pace
        e tranquillità.
        <br />Siate i benvenuti a condividere con me questo angolo di paradiso.
      </p>
    </div>
    <v-carousel cycle hide-delimiter-background class="small-carousel">
      <v-carousel-item v-for="(image, index) in carouselImages" :key="index">
        <div class="carousel-item">
          <img :src="image" class="carousel-image" />
        </div>
      </v-carousel-item>
    </v-carousel>
    <div class="divider pt-15"></div>
    <!-- Add a divider element here -->
    <h2 class="display-2 text-center bilbo-regular">Le mie stanze</h2>

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
  data() {
    return {
      carouselImages: ["src/assets/overView/image2.jpg", "src/assets/overView/image3.jpg"],
    };
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
  padding: 30px;
  text-align: center;
}

.small-carousel {
  width: 90%; /* Adjust the width of the carousel */
  margin: auto; /* Center the carousel horizontally */
}

.carousel-item {
  display: flex; /* Use flexbox for vertical centering */
  justify-content: center; /* Center horizontally */
  align-items: center; /* Center vertically */
  height: 100%; /* Ensure the carousel item takes full height */
}

.carousel-image {
  max-width: 100%; /* Set the width of carousel images to fit within the container */
  max-height: 100%; /* Set the height of carousel images to fit within the container */
}

.divider {
  width: 50%;
  margin: auto;
  border-bottom: 2px solid #182524; /* Add a decorative border */
  margin-bottom: 20px; /* Add some spacing */
}
</style>