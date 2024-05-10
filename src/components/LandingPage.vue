<template>
  <v-app>
    <!-- Header Section -->
    <Header />
    <!-- Main Content Section -->
    <MainContent :featuredRooms="featuredRooms" />

    <!-- Footer Section -->
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
      featuredRooms: [
        {
          name: "Luxury Suite",
          location: "New York City",
          image: "https://via.placeholder.com/400x250",
        },
        {
          name: "Luxury Suite",
          location: "New York City",
          image: "https://via.placeholder.com/400x250",
        },
        {
          name: "Luxury Suite",
          location: "New York City",
          image: "https://via.placeholder.com/400x250",
        },
        {
          name: "Luxury Suite",
          location: "New York City",
          image: "https://via.placeholder.com/400x250",
        },
        {
          name: "Luxury Suite",
          location: "New York City",
          image: "https://via.placeholder.com/400x250",
        },
        {
          name: "Luxury Suite",
          location: "New York City",
          image: "https://via.placeholder.com/400x250",
        },
        {
          name: "Luxury Suite",
          location: "New York City",
          image: "https://via.placeholder.com/400x250",
        },
        {
          name: "Cozy Apartment",
          location: "San Francisco",
          image: "https://via.placeholder.com/400x250",
        },
        {
          name: "Beach House",
          location: "Miami",
          image: "https://via.placeholder.com/400x250",
        },
      ],
    };
  },
};
</script>

<!-- Styles -->
<style scoped>
/* Define styles here */
</style>
