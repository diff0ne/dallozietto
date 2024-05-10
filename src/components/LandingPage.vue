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
          description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam efficitur, justo eu sollicitudin sodales, risus libero porta nisi, id vehicula neque libero at elit.",
          dimension: "400 sqft",
          maxCapacity: 2,
          services: ["Free Wi-Fi", "Air Conditioning", "Room Service"],
        },
        {
          name: "Cozy Apartment",
          location: "San Francisco",
          image: "https://via.placeholder.com/400x250",
          description: "Sed et purus in purus accumsan placerat. Proin nec congue risus. Donec eget odio ullamcorper, facilisis mi nec, tempor enim.",
          dimension: "600 sqft",
          maxCapacity: 4,
          services: ["Free Parking", "Kitchenette", "Balcony"],
        },
        {
          name: "Beach House",
          location: "Miami",
          image: "https://via.placeholder.com/400x250",
          description: "Fusce vel justo eget tortor fermentum convallis. Curabitur vitae tempor est, eget fringilla elit. Vestibulum posuere interdum tortor, a semper libero volutpat eu.",
          dimension: "800 sqft",
          maxCapacity: 6,
          services: ["Private Beach Access", "Swimming Pool", "Outdoor Grill"],
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
