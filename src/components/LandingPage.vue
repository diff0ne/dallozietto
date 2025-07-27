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
      featuredRooms: [
        {
          name: "iris",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam efficitur, justo eu sollicitudin sodales, risus libero porta nisi, id vehicula neque libero at elit.",
          dimension: "400 sqft",
          maxCapacity: 2,
          services: ["Free Wi-Fi", "Air Conditioning", "Room Service"],
        },
        {
          name: "rosa",
          description:
            "Sed et purus in purus accumsan placerat. Proin nec congue risus. Donec eget odio ullamcorper, facilisis mi nec, tempor enim.",
          dimension: "600 sqft",
          maxCapacity: 4,
          services: ["Free Parking", "Kitchenette", "Balcony"],
        },
        {
          name: "aquilegia",
          description:
            "Sed et purus in purus accumsan placerat. Proin nec congue risus. Donec eget odio ullamcorper, facilisis mi nec, tempor enim.",
          dimension: "600 sqft",
          maxCapacity: 4,
          services: ["Free Parking", "Kitchenette", "Balcony"],
        },
        {
          name: "ortensia",
          location: "San Francisco",
          description:
            "Sed et purus in purus accumsan placerat. Proin nec congue risus. Donec eget odio ullamcorper, facilisis mi nec, tempor enim.",
          dimension: "600 sqft",
          maxCapacity: 4,
          services: ["Free Parking", "Kitchenette", "Balcony"],
        },
      ],
    };
  },
};
</script>

<style scoped>
/* Adjust the width of the main content */
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
