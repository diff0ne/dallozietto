<template>
    <v-footer app class="footer">
      <div class="footer-content">
        <span class="copyright">&copy; {{ new Date().getFullYear() }} Dallo Zietto. All rights reserved.</span>
        <span class="contact-info">Contact us: <a href="mailto:info@dallozietto.com" class="contact-link">info@dallozietto.com</a> | +123456789</span>
      </div>
    </v-footer>
  </template>
  
  <script>
  export default {
    name: "Footer",
  };
  </script>
  
  <style scoped>
  .footer {
    background-color: #E2F1E6;
    font-family: "Arial", sans-serif;
    position: fixed;
    bottom: 0;
    width: 100%;
    padding: 10px 30px;
  }
  
  .footer-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .copyright {
    color: #182524;
    font-size: 12px;
    font-weight: 400;
  }
  
  .contact-info {
    color: #182524;
    font-size: 12px;
    font-weight: 400;
  }
  
  .contact-link {
    color: #182524;
    text-decoration: none;
    font-weight: 500;
  }
  
  .contact-link:hover {
    text-decoration: underline;
  }
  </style>
  