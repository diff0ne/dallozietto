<template>
  <div>
    <v-app-bar
      app
      color="#E6E5D1"
      :style="{
        transform: headerTransform,
        zIndex: headerZIndex,
        marginTop: headerMarginTop,
        marginLeft: headerMarginLeft,
        marginRight: headerMarginRight,
        paddingRight: '24px'
      }"
      class="sticky-header"
      :rounded="rounded"
      :elevation="elevation"
    >
      <v-toolbar-title class="font-title headline" @click="scrollTop">
        Benvenuto da Amabel
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <span class="info-label">Informazioni:</span>

      <v-btn icon @click="makePhoneCall" aria-label="Chiama">
        <v-icon>mdi-phone</v-icon>
      </v-btn>

      <v-btn icon @click="sendEmail" aria-label="Invia email">
        <v-icon>mdi-email</v-icon>
      </v-btn>

      <v-btn icon @click="openGoogleMaps" aria-label="Apri mappa">
        <v-icon>mdi-map-marker</v-icon>
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
      headerZIndex: 1000,
      headerMarginTop: "10px",
      headerMarginLeft: "10px",
      headerMarginRight: "10px",
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
      this.headerVisible = currentScroll > this.lastScroll && currentScroll > 100;
      this.lastScroll = currentScroll;
    },
    makePhoneCall() {
      window.location.href = "tel:+393337326617";
    },
    sendEmail() {
      window.location.href = "mailto:avv.gabrieledifede@libero.it";
    },
    openGoogleMaps() {
      window.open(
        "https://www.google.com/maps?q=Viganò,+via+della+Bandagera+8,+Lecco",
        "_blank"
      );
    },
    scrollTop() {
      window.scrollTo({
        top: 0,
        behavior: "smooth",
      });
    },
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300&display=swap');

.sticky-header {
  position: fixed !important;
  top: 0;
  left: 0;
  right: 0;
  transition: transform 0.5s ease-in-out;
  border-radius: 20px 0 0 20px;
  font-family: 'Poppins', sans-serif;
  font-weight: 300;
  color: #182524;
}

.font-title {
  font-family: "Bilbo";
  font-weight: 400;
  font-size: 80px;
  cursor: pointer;
}

.headline {
  width: fit-content !important;
  margin-left: 15px;
  padding: 20px 15px;
  line-height: 1;
  font-size: 30px;
}

.info-label {
  font-family: 'Poppins', sans-serif;
  font-weight: 300;
  font-size: 14px;
  margin-right: 10px;
  color: #182524;
}
</style>
