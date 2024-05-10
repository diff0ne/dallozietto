<template>
    <v-footer app class="footer">
      <span class="footer-text">&copy; {{ new Date().getFullYear() }} Dallo Zietto. All rights reserved.</span>
      <v-spacer></v-spacer>
      <span class="footer-text">Contact us: info@dallozietto.com | +123456789</span>
    </v-footer>
  </template>
  
  <script>
  export default {
    name: "Footer",
  };
  </script>
  
  <style scoped>
  .footer {
    background-color: #E2F1E6; /* Background color */
    font-family: "Arial", sans-serif; /* Common font stack */
    position: fixed;
    bottom: 0;
    width: 100%;
    padding: 10px 20px;
  }
  
  .footer-text {
    color: #182524; /* Text color */
    font-size: 12px; /* Adjusted font size */
    font-weight: 400; /* Increased font weight */
  }
  </style>
  