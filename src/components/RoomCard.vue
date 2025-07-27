<template>
  <v-card @click="openDialog" class="room-card" elevation="1">
    <v-img :src="imageSrc" class="padded-image"></v-img>
    <v-card-title>{{ capitalizeFirstLetter(room.name) }}</v-card-title>
    <v-card-text class="subtitle-2">
      <p><strong>Numero Ospiti:</strong> {{ room.maxCapacity }}</p>
      <div class="divider"></div>
      <p class="truncate">{{ room.description }}</p>
    </v-card-text>
    <v-card-actions>
      <v-btn text color="primary" @click.stop="openDialog">Vedi Dettagli</v-btn>
    </v-card-actions>

    <v-dialog v-model="dialog" max-width="900">
      <v-card>
        <v-card-title>{{ capitalizeFirstLetter(room.name) }}</v-card-title>

        <v-carousel
          cycle
          hide-delimiter-background
          show-arrows
          class="dialog-carousel"
          height="350"
        >
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
          <h3>Descrizione</h3>
          <p v-html="formattedDescription"></p>
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
  computed: {
    formattedDescription() {
      if (!this.room.description) return "";
      return this.room.description.replace(/\. +/g, '.<br>').replace(/\.$/, '.');
    },
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
        this.carouselImages = [this.imageSrc];
      }
    },
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300&display=swap');

.room-card {
  font-family: 'Poppins', sans-serif;
  font-weight: 300;
  font-size: 1rem;
  line-height: 1.6;
  color: #182524;
}

.padded-image {
  margin: 16px;
  padding: 2px;
  border-radius: 4px;
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
  max-width: 780px;
  margin: auto;
  position: relative;
}

.carousel-item {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.carousel-image {
  max-width: 85%;
  max-height: 330px;
  height: auto;
  object-fit: contain;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);
  transition: box-shadow 0.3s, transform 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  border-radius: 6px;
}

.carousel-image:hover {
  transform: scale(1.05);
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.4);
}

.v-carousel__controls__item {
  color: #182524 !important;
  font-size: 28px !important;
  opacity: 0.9 !important;
  transition: opacity 0.3s ease;
}

.v-carousel__controls__item:hover {
  opacity: 1 !important;
  cursor: pointer;
}

.characteristic-label {
  font-weight: 700;
  margin-right: 6px;
}

.dialog-characteristics {
  padding: 0px 16px !important;
  font-size: 0.95rem;
  margin-bottom: 2px;
}

.characteristic {
  margin-bottom: 6px;
}

.dialog-description {
  padding: 0px 16px !important;
  font-size: 0.95rem;
  line-height: 1.4;
  color: #182524;
  margin-top: 0;
}

.dialog-description h3 {
  margin-bottom: 6px;
  font-weight: 700;
  font-size: 1.1rem;
}
</style>
