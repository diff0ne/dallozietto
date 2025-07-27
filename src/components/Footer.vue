<template>
  <v-footer app class="footer">
    <div class="footer-content">
      <!-- Left: Copyright text -->
      <span class="copyright">&copy; {{ new Date().getFullYear() }} Villa Amabel. Tutti i diritti riservati.</span>

      <!-- Right: Contact info and location -->
      <div class="contact-wrapper">
        <div class="contact-info">
          <v-icon
            class="contact-icon"
            @click="openEmail"
            title="Email"
          >mdi-email</v-icon>
          <a href="mailto:avv.gabrieledifede@libero.it" class="contact-link email-text">
            avv.gabrieledifede@libero.it
          </a>

          <span class="spacer"></span>

          <v-icon
            class="contact-icon"
            @click="openPhone"
            title="Telefono"
          >mdi-phone</v-icon>
          <a href="tel:+393337326617" class="contact-link phone-text">+39 333 732 6617</a>
        </div>

        <div class="location" @click="openNavigator" title="Indirizzo">
          <v-icon class="contact-icon">mdi-map-marker</v-icon>
          <span class="location-text">Viganò, Via della Bandagera 8, Lecco</span>
        </div>
      </div>
    </div>
  </v-footer>
</template>

<script>
export default {
  name: "Footer",
  methods: {
    // Opens Google Maps with the address destination
    openNavigator() {
      const address = encodeURIComponent("Viganò, Via della Bandagera 8, Lecco");
      const url = `https://www.google.com/maps/dir/?api=1&destination=${address}`;
      window.open(url, "_blank");
    },
    // Opens default email client
    openEmail() {
      window.location.href = "mailto:avv.gabrieledifede@libero.it";
    },
    // Initiates phone call
    openPhone() {
      window.location.href = "tel:+393337326617";
    },
  },
};
</script>

<style scoped>
.footer {
  background-color: #E6E5D1;
  font-family: 'Poppins', sans-serif;
  position: fixed;
  bottom: 0;
  width: 100%;
  padding: 10px 30px;
  box-sizing: border-box;
}

.footer-content {
  display: flex;
  justify-content: space-between; /* Left and right aligned */
  align-items: center;
  gap: 40px;
  white-space: nowrap;
  flex-wrap: nowrap;
}

.copyright {
  color: #182524;
  font-size: 12px;
  font-weight: 400;
  cursor: default;
  white-space: nowrap;
}

.contact-wrapper {
  display: flex;
  align-items: center;
  gap: 20px;
  white-space: nowrap;
}

.contact-info {
  display: flex;
  align-items: center;
  gap: 15px;
}

.location {
  cursor: pointer;
  font-weight: 500;
  display: flex;
  align-items: center;
  gap: 8px;
  white-space: nowrap;
  color: #182524;
  font-size: 12px;
  font-weight: 400;
}

.contact-link {
  font-size: 12px;
  color: #182524;
  text-decoration: none;
  font-weight: 500;
}

.contact-link:hover {
  text-decoration: underline;
}

.contact-icon {
  cursor: pointer;
  color: #182524;
  font-size: 18px;
}

/* Responsive: hide contact info on smaller screens, keep only copyright */
@media (max-width: 1024px) {
  .contact-wrapper {
    display: none;
  }

  .copyright {
    font-size: 10px;
  }
}
</style>
