<template>
    <v-footer app color="#E2F1E6" class="sticky-footer mb-4">
      <span>&copy; {{ new Date().getFullYear() }} Dallo Zietto. All rights reserved.</span>
      <v-spacer></v-spacer>
      <span>Contact us: info@dallozietto.com | +123456789</span>
    </v-footer>
  </template>
  
  <script>
  export default {
    name: 'Footer'
  }
  </script>
  
  <style scoped>
  .sticky-footer {
    bottom: 0;
    width: 100%;
    z-index: 1000;
  }
  </style>
  