<template>
    <div class="header-wrapper">
      <v-app-bar
        app
        color="#E2F1E6"
        :style="{ transform: headerTransform }"
        class="sticky-header"
        :rounded="rounded"
        :elevation="elevation"
      >
        <v-toolbar-title class="font-title headline">
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
    name: 'Header',
    data() {
      return {
        lastScroll: 0,
        headerVisible: true
      };
    },
    props: {
      rounded: {
        type: Boolean,
        default: true
      },
      elevation: {
        type: Number,
        default: 10
      }
    },
    computed: {
      headerTransform() {
        return this.headerVisible ? 'translateY(0)' : 'translateY(-100%)';
      }
    },
    mounted() {
      window.addEventListener('scroll', this.handleScroll);
    },
    beforeDestroy() {
      window.removeEventListener('scroll', this.handleScroll);
    },
    methods: {
      handleScroll() {
        const currentScroll = window.pageYOffset || document.documentElement.scrollTop;
        if (currentScroll > this.lastScroll && currentScroll > 100) {
          this.headerVisible = false;
        } else {
          this.headerVisible = true;
        }
        this.lastScroll = currentScroll;
      },
      makePhoneCall() {
        // Logic to make a phone call
        console.log('Making a phone call...');
      },
      sendEmail() {
        // Logic to compose a new email
        console.log('Composing a new email...');
      },
      openGoogleMaps() {
        // Logic to open Google Maps
        console.log('Opening Google Maps...');
      },
      switchLanguage() {
        // Logic to switch language
        console.log('Switching language...');
      }
    }
  }
  </script>
  
  <style scoped>
  .header-wrapper {
    padding: 10px 10px 0; /* 10px top, 10px left, 0 right */
  }
  
  .sticky-header {
    position: sticky !important;
    top: 0;
    transition: transform 0.5s ease-in-out; /* Slower transition with ease-in-out easing */
    border-radius: 20px; /* Adjusted border radius */
  }
  
  .font-title {
    font-family: "Bilbo", cursive;
    font-weight: 400;
    font-size: 45px; /* Increased font size */
  }
  
  .headline {
    margin-left: 15px; /* Add margin to the left of the title */
    padding-top: 10px; /* Add padding to the top of the title */
    display: flex;
    align-items: center; /* Vertically center content */
  }
  </style>
  

  