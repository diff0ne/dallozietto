<template>
    <div>
      <v-app-bar
        app
        color="#E2F1E6"
        :style="{ transform: headerTransform, zIndex: headerZIndex, marginTop: headerMarginTop, marginLeft: headerMarginLeft, marginRight: headerMarginRight }"
        class="sticky-header"
        :rounded="rounded"
        :elevation="elevation"
      >
        <v-toolbar-title class="font-title headline" @click="scrollTop">
          Benvenuto!
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn icon @click="makePhoneCall">
          <v-icon>mdi-phone</v-icon>
        </v-btn>
        <v-btn icon @click="sendEmail">
          <v-icon>mdi-email</v-icon>
        </v-btn>
        <v-btn icon @click="openGoogleMaps">
          <v-icon>mdi-map-marker</v-icon>
        </v-btn>
        <v-btn icon @click="switchLanguage">
          <v-icon>mdi-translate</v-icon>
        </v-btn>
      </v-app-bar>
    </div>
  </template>
  
  <script>
  export default {
    name: "Header",
    data() {
      return {
        lastScroll: 0,
        headerVisible: false,
        headerZIndex: 1000, // Set a high z-index value
        headerMarginTop: "10px", // Add top margin
        headerMarginLeft: "10px", // Add left margin
        headerMarginRight: "10px", // Add right margin
      };
    },
    props: {
      rounded: {
        type: Boolean,
        default: true,
      },
      elevation: {
        type: Number,
        default: 10,
      },
    },
    computed: {
      headerTransform() {
        return this.headerVisible ? "translateY(0)" : "translateY(-120%)";
      },
    },
    mounted() {
      window.addEventListener("scroll", this.handleScroll);
    },
    beforeDestroy() {
      window.removeEventListener("scroll", this.handleScroll);
    },
    methods: {
      handleScroll() {
        const currentScroll =
          window.pageYOffset || document.documentElement.scrollTop;
        if (currentScroll > this.lastScroll && currentScroll > 100) {
          this.headerVisible = true; // Show header when scrolling down
        } else {
          this.headerVisible = false;
        }
        this.lastScroll = currentScroll;
      },
      makePhoneCall() {
        // Logic to make a phone call
        console.log("Making a phone call...");
      },
      sendEmail() {
        // Logic to compose a new email
        console.log("Composing a new email...");
      },
      openGoogleMaps() {
        // Logic to open Google Maps
        console.log("Opening Google Maps...");
      },
      switchLanguage() {
        // Logic to switch language
        console.log("Switching language...");
      },
      scrollTop() {
        window.scrollTo({
          top: 0,
          behavior: "smooth", // Smooth scrolling animation
        });
      },
    },
  };
  </script>
  
  <style scoped>
  .sticky-header {
    position: fixed !important;
    top: 0;
    left: 0;
    right: 0;
    transition: transform 0.5s ease-in-out; /* Slower transition with ease-in-out easing */
    border-radius: 20px 0 0 20px; /* Adjusted border radius */
  }
  
  .font-title {
    font-family: "Bilbo", cursive;
    font-weight: 400;
    font-size: 45px; /* Increased font size */
    cursor: pointer; /* Change cursor to pointer on hover */
  }
  
  .headline {
    width: fit-content !important;
    margin-left: 15px; /* Add margin to the left of the title */
    padding: 20px 15px; /* Added padding */
    line-height: 1; /* Ensure the line height is normal */
  }
  </style>
  