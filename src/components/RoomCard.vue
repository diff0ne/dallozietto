<template>
  <!-- Room Card Component -->
  <v-card @click="openDialog" class="room-card" elevation="1">
    <!-- Room Image -->
    <v-img :src="imageSrc"></v-img>
    <!-- Room Title -->
    <v-card-title>{{ capitalizeFirstLetter(room.name) }}</v-card-title>
    <!-- Room Details -->
    <v-card-text class="subtitle-2">
      <p>Numero Ospiti: {{ room.maxCapacity }}</p>
      <div class="divider"></div>
      <p class="truncate">{{ room.description }}</p>
    </v-card-text>
    <!-- Button to Open Dialog -->
    <v-card-actions>
      <v-btn text color="primary" @click="openDialog">Vedi Dettagli</v-btn>
    </v-card-actions>

    <!-- Dialog Component for Room Details -->
    <v-dialog v-model="dialog" max-width="700">
      <v-card>
        <!-- Dialog Title -->
        <v-card-title>{{ capitalizeFirstLetter(room.name) }}</v-card-title>

        <!-- Carousel of Room Pictures -->
        <v-carousel
          cycle
          hide-delimiter-background
          class="dialog-carousel small-carousel"
        >
          <!-- Loop through Carousel Images -->
          <v-carousel-item v-for="(image, index) in carouselImages" :key="index">
            <div class="carousel-item">
              <!-- Image within Carousel -->
              <img :src="image" class="carousel-image" />
            </div>
          </v-carousel-item>
        </v-carousel>

        <!-- Room Characteristics -->
        <v-card-text class="dialog-characteristics">
          <div class="characteristic">
            <span class="characteristic-label">People Allowed:</span>
            <span>{{ room.maxCapacity }}</span>
          </div>
          <div class="characteristic">
            <span class="characteristic-label">Dimension:</span>
            <span>{{ room.dimension }}</span>
          </div>
          <div class="characteristic">
            <span class="characteristic-label">Services:</span>
            <span>{{ room.services.join(", ") }}</span>
          </div>
        </v-card-text>

        <!-- Room Description -->
        <v-card-text class="dialog-description">
          <p>{{ room.description }}</p>
        </v-card-text>

        <!-- Dialog Actions -->
        <v-card-actions>
          <v-btn text @click="closeDialog">Close</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-card>
</template>

<script>
export default {
  name: "RoomCard",
  props: {
    // Room Object Prop
    room: {
      type: Object,
      required: true,
    },
    // Image Source Prop
    imageSrc: {
      type: String,
      required: true,
    },
    // Carousel Images Prop
    carouselImages: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      // Dialog State
      dialog: false,
    };
  },
  methods: {
    // Method to Open Dialog
    openDialog() {
      this.dialog = true;
    },
    // Method to Close Dialog
    closeDialog() {
      this.dialog = false;
    },
    // Method to Capitalize First Letter of a String
    capitalizeFirstLetter(text) {
      return text.charAt(0).toUpperCase() + text.slice(1);
    },
  },
};
</script>

<style scoped>
/* Component Styles */
.room-card {
  margin: 32px;
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
</style>
