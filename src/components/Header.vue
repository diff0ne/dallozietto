<template>
    <v-app-bar
      :elevation="20"
      app
      color="#E2F1E6"
      class="sticky-header"
    >
      <v-toolbar-title>
        <span class="font-weight-regular font-title">Benvenuto!</span>
      </v-toolbar-title>
      <template v-slot:append>
        <v-btn icon="mdi-phone-classic"></v-btn>
        <v-btn icon="mdi-email-fast"></v-btn>
        <v-btn icon="mdi-google-maps"></v-btn>
        <v-btn icon="mdi-translate-variant"></v-btn>
      </template>
    </v-app-bar>
  </template>
  
  <script>
  export default {
    name: 'Header'
  }
  </script>
  
  <style scoped>
  .sticky-header {
    position: fixed !important;
    top: 10px !important;
    border-radius: 10px;
    z-index: 1000;
  }
  </style>
  