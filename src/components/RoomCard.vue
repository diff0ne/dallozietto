<template>
  <v-card @click="openDialog" class="room-card" elevation="1">
    <v-img :src="imageSrc" class="padded-image"></v-img>
    <v-card-title>{{ capitalizeFirstLetter(room.name) }}</v-card-title>
    <v-card-text class="subtitle-2">
      <p>Numero Ospiti: {{ room.maxCapacity }}</p>
      <div class="divider"></div>
      <p class="truncate">{{ room.description }}</p>
    </v-card-text>
    <v-card-actions>
      <v-btn text color="primary" @click.stop="openDialog">Vedi Dettagli</v-btn>
    </v-card-actions>

    <v-dialog v-model="dialog" max-width="700">
      <v-card>
        <v-card-title>{{ capitalizeFirstLetter(room.name) }}</v-card-title>

        <v-carousel cycle hide-delimiter-background class="dialog-carousel small-carousel">
          <v-carousel-item
            v-for="(image, index) in carouselImages"
            :key="index"
          >
            <div class="carousel-item">
              <img :src="image" class="carousel-image padded-image" />
            </div>
          </v-carousel-item>
        </v-carousel>

        <v-card-text class="dialog-characteristics">
          <div class="characteristic">
            <span class="characteristic-label">Numero Ospiti:</span>
            <span>{{ room.maxCapacity }}</span>
          </div>
          <div class="characteristic">
            <span class="characteristic-label">Dimensione:</span>
            <span>{{ room.dimension }}</span>
          </div>
          <div class="characteristic">
            <span class="characteristic-label">Servizi:</span>
            <span>{{ room.services.join(", ") }}</span>
          </div>
        </v-card-text>

        <v-card-text class="dialog-description">
          <p>{{ room.description }}</p>
        </v-card-text>

        <v-card-actions>
          <v-btn text @click="closeDialog">Chiudi</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-card>
</template>

<script>
export default {
  name: "RoomCard",
  props: {
    room: {
      type: Object,
      required: true,
    },
    imageSrc: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      dialog: false,
      carouselImages: [],
    };
  },
  methods: {
    openDialog() {
      this.dialog = true;
      this.loadImages(this.room.name);
    },
    closeDialog() {
      this.dialog = false;
    },
    capitalizeFirstLetter(text) {
      if (!text) return "";
      return text.charAt(0).toUpperCase() + text.slice(1);
    },
    loadImages(roomName) {
      const images = import.meta.glob("/src/assets/*/*.{jpg,jpeg,png}", { eager: true });

      this.carouselImages = Object.entries(images)
        .filter(([path]) => path.toLowerCase().includes(`/assets/${roomName.toLowerCase()}/`))
        .map(([, module]) => module.default);

      if (this.carouselImages.length === 0) {
        // fallback a immagine singola o placeholder se non ci sono immagini
        this.carouselImages = [this.imageSrc];
      }
    },
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300&display=swap');

.room-card {
  margin: 32px;
  font-family: 'Poppins', sans-serif;
  font-weight: 300;
  font-size: 1rem;
  line-height: 1.6;
  color: #182524;
}

.padded-image {
  padding: 8px;
}

.divider {
  height: 1px;
  width: 100%;
  background-color: #ccc;
  margin: 8px 0;
}

.truncate {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
  overflow: hidden;
}

.dialog-carousel {
  height: 200px;
}

.dialog-characteristics {
  padding-top: 20px;
}

.characteristic {
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}

.characteristic-label {
  font-weight: bold;
}

.small-carousel {
  height: 100px;
}

.carousel-item {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 80%;
}

.carousel-image {
  max-width: 100%;
  max-height: 100%;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);
  transition: box-shadow 0.3s, transform 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}

.carousel-image:hover {
  transform: scale(1.1);
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.4);
}
</style>
